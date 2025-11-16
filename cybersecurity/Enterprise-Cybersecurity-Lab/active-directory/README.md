# 🧠 Enterprise Cybersecurity Lab — Active Directory, Certificate Authority & IIS Server

This section documents the **Active Directory (AD), Certificate Services (CA), and IIS Web Server** configuration inside the **Enterprise Cybersecurity Lab (ECL)**.  
The goal is to provide a **production-grade identity, authentication, and web services foundation** for your SOC, firewalls, EDR, Suricata, Zeek, and endpoint tooling.

---

# 📌 1. Active Directory Configuration

### **Domain Information**
| Setting | Value |
|--------|-------|
| **Domain Name** | `ECL.lab` |
| **Primary Domain Controller** | `ECL-DC01` |
| **Windows Server Version** | 2012 R2 Standard |
| **Core Roles Installed** | AD DS, DNS Server, Certificate Authority (AD CS), IIS Web Server |

---

## 📂 1.1 AD DS Overview

### Screenshot: AD Users & Computers (Domain Root)  
`ad-domain-root.png`

### Screenshot: Domain Controllers OU  
`ad-domain-controllers-ou.png`

---

## 📁 1.2 Organizational Unit (OU) Design

### Screenshot: Computers OU  
`ad-computers-ou.png`

### Screenshot: ECL-Groups OU  
`ad-ecl-groups-ou.png`

### Screenshot: ECL-Users OU  
`ad-ecl-users-ou.png`

---

## 👥 1.3 ECL Security Groups  

### Screenshot: Domain Admins Properties  
`ad-domain-admin-properties.png`

### Screenshot: AD Users & Computers (Tree View)  
`ecl-ad-users-and-computers.png`

---

# 🔐 2. Certificate Authority (AD CS)

The CA provides certificates for:
- Domain Clients  
- Domain Controllers  
- Palo Alto Firewalls  
- Fortinet Firewalls  
- IIS Application  
- SSL/TLS Inspection & Decryption Lab  

## 2.1 CA Role Installed

### Screenshot: CA Role Installed  
`dc-ca-role-installed.png`

---

## 2.2 CA Console

### Screenshot: CA MMC Console  
`dc-ca-console.png`

---

# 🌐 3. IIS Web Server Overview

## 3.1 IIS Installed

### Screenshot: IIS Role Installed  
`iss-role-installed.png`

---

## 3.2 Default Web Site

### Screenshot: Default Web Site  
`iis-default-website.png`

---

## 3.3 Software Center (Internal App Distribution Portal)

### Screenshot: IIS Software Center Folder  
`iis-software-center-folder.png`

---

## 3.4 IIS Manager Tools/Features View

### Screenshot: IIS Tools Menu  
`iss-tools-menu.png`

---

# 🛡️ 4. How AD, CA & IIS Tie Into the SOC

Your identity & trust infrastructure supports:

### **🔹 SOC Visibility**
- Users authenticate to the domain → logs sent to Splunk  
- Machines register to AD → tracked by Wazuh EDR  
- Suricata & Zeek capture east-west and north-south traffic tied to hostname & identity  

### **🔹 Firewall Integrations**
- Palo Alto firewalls use **CA-issued certificates** for:
  - SSL Decryption  
  - GlobalProtect  
  - Administrative UI hardening  

- Fortinet firewalls also receive certificates from the same trusted CA  

### **🔹 Secure Internal App Hosting**
- IIS Software Center hosts PowerShell tools, installers, and packages safely  
- Future expansion: Internal PKI-protected apps, dashboards, OCSP, CRL distribution  

---

# 🏁 Final Notes

Your AD + CA + IIS environment is now **fully documented**, **production‑grade**, and tightly integrated into the rest of your Enterprise Cybersecurity Lab.

This README is ready to publish on GitHub.

