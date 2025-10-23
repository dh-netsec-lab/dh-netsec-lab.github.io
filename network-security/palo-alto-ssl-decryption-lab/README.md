# 🔐 Palo Alto SSL Decryption Lab

## 🎯 Objective
This lab demonstrates **SSL Forward Proxy** (outbound) and **SSL Inbound Decryption** (server-side) on a Palo Alto Networks firewall.  
It covers certificate creation/import, trust distribution, decryption policy configuration, traffic verification, and troubleshooting.

---

## 🧩 Topology
![Topology](screenshots/topology.png)

| Device | Role | IP Address | Notes |
|:-------|:-----|:-----------|:------|
| **PA-FW-01** | Palo Alto NGFW | 10.0.1.254 | Performs SSL Forward Proxy & Inbound Decryption |
| **WIN-CLIENT** | Windows 10 | 10.0.1.10 | Browser for testing decrypted traffic |
| **WIN-SRV-CA** | Windows Server 2019 | 10.0.1.100 | Enterprise CA & IIS Web Server |
| **Internet** | Public Sites | N/A | Used for SSL Forward Proxy verification |

---

## 🏗️ Lab Components
- **PAN-OS Version:** 10.x or later  
- **Windows Server:** Active Directory Certificate Services (Enterprise CA)  
- **Client Browser:** Edge / Chrome (with CA trust installed)  
- **IIS Web Server:** Hosts HTTPS site for inbound decryption  
- **Test Sites:** `https://example.com`, `https://badssl.com`, and internal `https://iis.4outof7.com`

---

## 🪪 Certificates

### 1. Create / Obtain Root CA
- Generate or issue a **Root CA certificate** on `WIN-SRV-CA`.
- Export the CA certificate (`PA-ForwardTrust-CA.cer`) and import it into the Palo Alto Firewall:
  - **Device → Certificate Management → Certificates → Import**
- Mark it as **Forward Trust Certificate**.

![Firewall Certificates](screenshots/fw-cert-list.png)

---

### 2. Distribute CA to Clients
- Export the same `.cer` file and install into the client’s trusted root store:
  - `MMC → Certificates (Computer Account) → Trusted Root Certification Authorities`
- Verify it appears in the Trusted Root list.

![Client Trusted Root](screenshots/client-truststore.png)

---

### 3. Server Certificate for Inbound Decryption
- On `WIN-SRV-CA`, issue a server certificate for the IIS web server:
  - **Common Name:** `iis.4outof7.com`
  - **SANs:** `iis.4outof7.com`, internal IP of the server
- Export the `.pfx` (with private key) and import it into the Palo Alto firewall for use in **Inbound SSL Decryption**.

![IIS Server Certificate](screenshots/iis-server-cert.png)

---

### 🔎 Firewall Certificate Inventory
The following screenshot shows all device certificates installed on the Palo Alto firewall for this SSL Decryption lab.

![Firewall Certificates](screenshots/fw-cert-list.png)

| Certificate Name | Purpose | Key/CA | Usage |
|:------------------|:--------|:-------|:------|
| **Trusted_Local_Win_CA** | Root CA issued by Windows Server 2019 CA (`DC=4outof7,DC=com`) | ✅ CA | *Trusted Root CA Certificate* |
| **Cert_For_132_Mgmt** | Forward Trust certificate used by the firewall to dynamically re-sign valid SSL sites | ✅ Key | *Forward Trust Certificate* |
| **Cert_For_Resigning_132** | Intermediate certificate for re-signing traffic in special policy cases (optional use) | ✅ Key | *Forward Trust / Custom Re-signing* |
| **Win_IIS_Server_Cert** | Certificate installed on the IIS server for inbound SSL decryption testing | ✅ Key | *Server Certificate* |
| **Deny_Untrusted_Invalid_Cert** | Palo Alto–issued Forward Untrust Certificate used when a destination site’s certificate is **invalid**, **expired**, or **untrusted** | ✅ CA | *Forward Untrust Certificate* |
| **trusted-certificate / untrusted-certificate** | Default PAN-OS test certificates (not used in this lab) | ✅ Key | — |

📘 **Summary:**  
- **`Trusted_Local_Win_CA`** is your root CA trusted by internal clients.  
- **`Cert_For_132_Mgmt`** is configured as the **Forward Trust Certificate** (used for re-signing trusted websites).  
- **`Deny_Untrusted_Invalid_Cert`** is configured as the **Forward Untrust Certificate** (used when a site’s original certificate fails validation).  
- **`Win_IIS_Server_Cert`** supports **Inbound SSL Decryption** for the IIS server.  

🧠 **Tip:**  
When users browse to a site wi
