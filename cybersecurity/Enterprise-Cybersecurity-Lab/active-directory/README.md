# 🧩 Active Directory & Core Infrastructure – Enterprise Cybersecurity Lab (ECL)

This document provides full documentation of the **Active Directory (AD)**, **Certificate Authority (CA)**, and **IIS Web Services** used inside the Enterprise Cybersecurity Lab (ECL).  
It includes architecture, screenshots, verification steps, and how AD integrates into the SOC ecosystem (Splunk, Wazuh, Suricata/Zeek, and identity‑based security controls).

---

# 🏛️ 1. Active Directory Overview

### **Domain Information**
- **Domain Name:** `ECL.lab`  
- **Primary Domain Controller:** `ECL-DC01`  
- **Windows Server OS:** 2012 R2 Standard  
- **Server Roles Installed:**  
  - Active Directory Domain Services (AD DS)  
  - DNS  
  - Certificate Authority (AD CS)  
  - IIS Web Server (used internally for Software Center / file distribution)

### **Functional Goal**
The AD domain provides:
- Central identity management for all lab users  
- Computer account lifecycle control  
- Authentication backend for firewalls, SIEM, and NAC integrations  
- Certificate issuance for Palo Alto / Fortinet / Win endpoints  
- Internal software delivery via IIS  

---

# 🗂️ 2. Organizational Unit (OU) Structure

The OU structure was built following a clean, enterprise‑ready model.

### Screenshots  
- `ad-domain-root.png`  
- `ad-domain-controllers-ou.png`  
- `ad-computers-ou.png`  
- `ad-ecl-users-ou.png`  
- `ad-ecl-groups-ou.png`  

---

# 👥 3. Users & Groups

Users and groups aligned to security best practices:

### Users  
- Domain Admin  
- Standard user accounts  
- Service accounts for integration  

### Groups  
- ECL_Admins  
- ECL_Security  
- ECL_Users  
- Firewall_Auth (used for Panorama/Palo auth)  
- SIEM_Readers  

### Screenshots  
- `ad-domain-admin-properties.png`  
- `ecl-ad-users-and-computers.png`

---

# 🌐 4. DNS Configuration

DNS runs on the Domain Controller.

- Internal zone: `ECL.lab`  
- A/PTR records created automatically for joined devices  
- Supports reverse DNS for firewall/User-ID lookups  
- Ensures Splunk, Wazuh, Suricata, Sysmon machines resolve correctly

### Screenshot  
- `dc-dns-console.png`

---

# 🔐 5. Certificate Authority (AD CS)

The Domain Controller acts as the **Enterprise Root Certificate Authority**.

### Purpose in the ECL
- Issues certificates for:
  - Palo Alto firewalls  
  - Fortinet firewalls  
  - Windows OS / Sysmon  
  - Suricata/Zeek (Trust Store)  
  - Internal IIS web sites  
- Enables SSL Decryption labs  
- Supports internal HTTPS services  

### Screenshots  
- `dc-ca-role-installed.png`  
- `dc-ca-console.png`

---

# 🌐 6. IIS Web Server (Internal Software Center)

IIS is used for:
- Hosting an internal **Software Center**  
- Distribution of Sysmon config  
- Hosting documentation or scripts  
- Supporting future ECL endpoints (Zero Trust, NAC, automation)

### Screenshots  
- `dc-iis-role-installed.png`  
- `dc-iis-console.png`  
- `dc-iis-default-site.png`  
- `dc-iis-software-center.png`

---

# 🧩 7. How Active Directory Integrates With the SOC

Active Directory directly supports multiple SOC components:

### **Wazuh**
- DC sends Windows Event Logs → Wazuh Agent  
- Wazuh performs:
  - File integrity monitoring  
  - Logon/logoff analysis  
  - Process monitoring  
  - Service changes / privilege escalations  

### **Splunk**
- DC also forwards logs to Splunk for:
  - Authentication dashboards  
  - Sysmon analysis  
  - Lateral movement detections  

### **Suricata / Zeek**
- AD workstation traffic is monitored by IDS/NSM  
- User identity (from AD) + network events = full visibility  

### **Palo Alto / Fortinet**
- Trusted CA issues firewall certificates  
- Firewalls authenticate admins via AD groups  
- VPN & SSL Decryption rely on AD-issued certificates  

### **ClearPass NAC (future integration)**
- AD provides:
  - Identity source  
  - Group-based policies  
  - Machine authentication  

This creates a fully integrated enterprise‑grade SOC and Zero Trust identity model.

---

# 🖼️ 8. Screenshot Index (for GitHub README linking)

```
/active-directory/screenshots/
│
├── ad-domain-root.png
├── ad-domain-controllers-ou.png
├── ad-computers-ou.png
├── ad-ecl-users-ou.png
├── ad-ecl-groups-ou.png
├── ad-domain-admin-properties.png
├── ecl-ad-users-and-computers.png
├── dc-dns-console.png
├── dc-ca-role-installed.png
├── dc-ca-console.png
├── dc-iis-role-installed.png
├── dc-iis-console.png
├── dc-iis-default-site.png
└── dc-iis-software-center.png
```

---

# 🏁 Final Notes

This AD environment is now:

✔ Enterprise‑ready  
✔ Cleanly structured  
✔ Fully integrated into the SOC pipeline  
✔ Documented with professional, portfolio‑quality screenshots  

This README replaces the previous file and is now the **official AD documentation** for the Enterprise Cybersecurity Lab.

