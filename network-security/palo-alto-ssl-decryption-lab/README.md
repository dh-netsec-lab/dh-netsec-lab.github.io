# 🔐 Palo Alto SSL Decryption Lab

## 🎯 Objective
This lab demonstrates **SSL Forward Proxy** (outbound) and **SSL Inbound Decryption** (server-side) on a Palo Alto Networks firewall.  
It covers certificate creation/import, trust distribution, decryption policy configuration, traffic verification, and troubleshooting.

---

## 🧩 Topology
![Topology](screenshots/topology.png)

| Device | Role | IP Address | Notes |
|:-------|:-----|:-----------|:------|
| PA-FW-01 | Palo Alto NGFW | 10.0.1.254 | Performs SSL Forward Proxy & Inbound Decryption |
| WIN-CLIENT | Windows 10 | 10.0.1.10 | Browser for testing decrypted traffic |
| WIN-SRV-CA | Windows Server 2019 | 10.0.1.100 | Enterprise CA & IIS Web Server |
| Internet | Public Sites | N/A | Used for SSL Forward Proxy verification |

---

## 🏗️ Lab Components
- **PAN-OS Version:** 10.x or later  
- **Windows Server:** Active Directory Certificate Services (Enterprise CA)  
- **Client Browser:** Edge / Chrome (with CA trust installed)  
- **IIS Web Server:** Hosts HTTPS site for inbound decryption  
- **Test Sites:** `https://example.com`, `https://badssl.com`, local `https://iis.4outof7.com`

---

## 🪪 Certificates

### 1. Create / Obtain Root CA
- Generate or issue a **Root CA certificate** on `WIN-SRV-CA`.
- Export the CA certificate (`PA-ForwardTrust-CA.cer`) and import it into the Palo Alto Firewall:
  - **Device → Certificate Management → Certificates → Import**
- Mark it as **Forward Trust Certificate**.

🖼 *Screenshot:* `screenshots/fw-cert-list.png`

---

### 2. Distribute CA to Clients
- Export the same `.cer` file and install into client trust store:
  - `MMC → Certificates (Computer Account) → Trusted Root Certification Authorities`
- Verify it appears under the Trusted Root list.

🖼 *Screenshot:* `screenshots/client-truststore.png`

---

### 3. Server Certificate for Inbound Decryption
- On `WIN-SRV-CA`, issue a server certificate for the IIS web server:
  - **Common Name:** `iis.4outof7.com`
  - **SANs:** `iis.4outof7.com`, IP of server
- Export the `.pfx` (with private key) and import into Palo Alto:
  - Mark as **SSL Forward Untrust Certificate** if needed for inspection of untrusted sites.

🖼 *Screenshot:* `screenshots/iis-server-cert.png`

---

## ⚙️ Firewall Configuration

### 1. Create SSL/TLS Service Profile
- **Device → Certificate Management → SSL/TLS Service Profile**
- Assign the Forward Trust CA certificate.

🖼 *Screenshot:* `screenshots/fw-cert-list.png`

---

### 2. Configure Decryption Policy
1. **Policies → Decryption → Add**
   - **Name:** `SSL_Forward_Proxy`
   - **Source Zone:** Inside
   - **Destination Zone:** Outside
   - **Service:** `service-https`
   - **Action:** `Decrypt`
   - **Decryption Type:** `SSL Forward Proxy`
   - **Certificate:** `PA-ForwardTrust-CA`

🖼 *Screenshot:* `screenshots/decryption-policy-config.png`

---

### 3. Configure Decryption Exceptions
- **Policies → Decryption → Add → Action: No Decrypt**
- Add categories such as:
  - `Financial Services`
  - `Health`
  - `Government`
- Also add pinned sites (e.g., Google, Microsoft, etc.).

🖼 *Screenshot:* `screenshots/decryption-exceptions.png`

---

## 🔍 Verification & Testing

### 1. Browser Validation
- From `WIN-CLIENT`, browse to:
  - `https://example.com` → Should show **secure** lock icon.
  - View the certificate → Issued by `PA-ForwardTrust-CA`.

🖼 *Screenshot:* `screenshots/browser-cert-inspect.png`

---

### 2. CLI Validation
Run:
```bash
openssl s_client -connect example.com:443 -servername example.com -showcerts

