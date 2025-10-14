# Palo Alto GlobalProtect VPN Lab (VMware Environment)

## Objective
This lab demonstrates the configuration of **Palo Alto GlobalProtect VPN** in a VMware environment.  
The goal is to allow remote users to securely connect to the internal network using GlobalProtect with certificate-based authentication.

---

## Topology
The following topology shows the VMware setup for the GlobalProtect lab.

![GlobalProtect VMware Topology](screenshots/globalprotect-vmware-topology.png)

**Key Components:**
- **Firewall:** 192.168.118.188 (Mgmt), WAN 192.168.1.254, Trust 10.1.0.254, DMZ 10.2.0.254  
- **Domain Controller / CA:** 192.168.118.207  
- **Trust Network:** 10.1.0.0/24  
- **DMZ Network:** 10.2.0.0/24  
- **Untrust Network:** 192.168.1.0/24  
- **GlobalProtect Client (WAN PC):** 192.168.1.29  

---

## Lab Environment
- **Platform:** VMware Workstation  
- **PAN-OS Version:** 10.x  
- **Windows Server 2022:** Domain Controller, DNS, Certificate Authority  
- **Windows 10:** GlobalProtect client system  
- **Purpose:** Demonstrate portal, gateway, certificate, and user authentication setup for GlobalProtect.

---

## Step 1: Import and Assign Certificate

1. Generate a certificate on the Domain Controller’s Certificate Authority with the following **Subject Alternative Names (SANs):**  
   - `192.168.1.254`  
   - `192.168.118.207`  
   - `gp.4outof7.com`  

2. Export the certificate (including the private key) and import it into the Palo Alto firewall.  
3. Mark it as **Trusted Root CA** and **Local** on the firewall.  

![Certificate Import](screenshots/certificate-import.png)

---

## Step 2: Create an Authentication Profile

1. Go to **Device → Authentication Profile**.  
2. Create a profile that uses **Local Database** or **LDAP** (if connected to AD).  
3. Add user(s) allowed to connect via GlobalProtect.

![Authentication Profile](screenshots/auth-profile.png)

---

## Step 3: Configure GlobalProtect Portal

1. Navigate to **Network → GlobalProtect → Portals → Add**.  
2. Under **General**, assign the WAN interface (`ethernet1/1 – 192.168.1.254`).  
3. Under **Authentication**, select the imported certificate and authentication profile.  
4. Add a client configuration with:  
   - Internal Gateway: `192.168.1.254`  
   - IP Pool: `10.10.10.0/24` (example)  
   - DNS: `10.1.0.207` or internal DNS server.

![Portal Configuration](screenshots/portal-config.png)

---

## Step 4: Configure GlobalProtect Gateway

1. Go to **Network → GlobalProtect → Gateways → Add**.  
2. Assign the **same WAN interface** (`ethernet1/1 – 192.168.1.254`).  
3. Under **Authentication**, use the same certificate and authentication profile.  
4. Under **Client Configuration**, define:
   - IP Pool: `10.10.10.0/24`
   - Split Tunnel settings as required
   - DNS and WINS if applicable

![Gateway Configuration](screenshots/gateway-config.png)

---

## Step 5: Security and NAT Policies

1. Create a **Security Policy** allowing GlobalProtect connections:
   - **Name:** `GlobalProtect_VPN`
   - **From:** Untrust  
   - **To:** Trust  
   - **Source:** Any  
   - **Destination:** Firewall WAN IP (192.168.1.254)  
   - **Application:** `ssl`, `web-browsing`, `ipsec-esp`, `ping`  
   - **Action:** Allow  

![Security Policy](screenshots/security-policy.png)

2. Create a **NAT Policy** (if outbound NAT is needed for VPN clients):
   - **From:** VPN Zone  
   - **To:** Untrust  
   - **Source Translation:** Dynamic IP and Port  

![NAT Policy](screenshots/nat-policy.png)

---

## Step 6: Client Connection Test

1. Install the GlobalProtect Client on the WAN PC (`192.168.1.29`).  
2. Launch the client and connect to the portal address `gp.4outof7.com` or `192.168.1.254`.  
3. Log in with your allowed user credentials.  

![GlobalProtect Connection](screenshots/globalprotect-connect.png)

---

## Verification

- In the firewall CLI, verify active users:

