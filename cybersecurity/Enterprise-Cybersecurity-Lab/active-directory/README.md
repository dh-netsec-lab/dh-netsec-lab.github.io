# 🧠 Active Directory (AD) Setup – Enterprise Cybersecurity Lab (ECL)

This documentation covers the full **Active Directory build**, including domain structure, users, groups, and how AD integrates into the **SOC stack (Splunk, Wazuh, Suricata, Zeek)** within the ECL.

---

## 🚀 1. Domain Overview

Your Active Directory Domain Services (AD DS) deployment provides identity, authentication, authorization, and directory services for the entire ECL environment.

### **Domain Name:** `ECL.lab`  
### **Primary Domain Controller:** `ECL-DC01`  
### **Windows Server Version:** 2012 R2 Standard  
### **Roles Installed:**
- Active Directory Domain Services (AD DS)
- DNS Server
- Certificate Authority (AD CS)
- IIS (for SSL testing & SOC use cases)

---

## 🏛️ 2. AD Organizational Unit (OU) Structure

A clean and professional OU layout makes the lab look enterprise‑grade and is ideal for GPO, security baselines, and SOC telemetry.

```
ECL.lab
│
├── ECL-Users
│     ├── Admins
│     ├── Standard-Users
│
├── ECL-Groups
│     ├── Security-Groups
│     ├── Service-Accounts
│
├── Computers
│     ├── Servers
│     ├── Workstations
│
└── Domain Controllers
```

### 📸 Screenshots:
- ![](./screenshots/ad-domain-root.png)
- ![](./screenshots/ad-domain-admin-properties.png)
- ![](./screenshots/ecl-ad-users-and-computers.png)
- ![](./screenshots/ad-domain-controllers-ou.png)
- ![](./screenshots/ad-computers-ou.png)
- ![](./screenshots/ad-ecl-groups-ou.png)
- ![](./screenshots/ad-ecl-users-ou.png)

---

## 👥 3. User & Group Configuration

### 🔐 **Administrative Accounts**
- `ECL-Administrator` (Domain Admin)
- `ECL-Splunk-Service` (Splunk AD queries)
- `ECL-Wazuh-Agent` (Optional future integration)

### 👨‍💼 **Standard Users**
- Production‑style usernames (example):  
  - `dhervey`
  - `testuser01`

### 🧩 **Security Groups**
- `ECL-Splunk-Admins`
- `ECL-Workstation-Users`
- `ECL-Server-Admins`

---

## ✔️ 4. Group Policy (GPO) Integration

Policies you may add later in the SOC phase:

### **Recommended GPOs:**
- **Windows Logging Baseline**
- **PowerShell Logging**
- **Sysmon Deployment GPO** (if not manually installed)
- **RDP Restriction / Firewall Rules**
- **Browser Hardening**
- **Audit Policy: Success + Failure**

GPO will directly support:
- Splunk → Windows Event Logs  
- Wazuh → FIM, Sysmon, WinRM logs  
- Zeek/Suricata → Enriched telemetry with usernames  

---

## 🔗 5. How Active Directory Ties Into the SOC

AD plays a **central role** in the Enterprise Cybersecurity Lab:

### **🔎 Splunk Integration**
- DC logs → forwarded via Splunk Universal Forwarder
- Authentication logs (4624/4625)  
- GPO changes (4739)  
- User lockouts (4740)  
- group membership changes  

### **🛡️ Wazuh Integration**
- Windows agent installed on DC  
- File Integrity Monitoring (FIM) for:  
  - `NTDS.dit`
  - SYSVOL  
  - Security logs  
- Detection of brute force, RDP attempts, privilege escalation

### **🌐 Suricata Integration**
- Maps LDAP / Kerberos traffic  
- Detects unusual authentication attempts  
- Detects lateral movement patterns (EternalBlue, DCERPC anomalies)

### **📡 Zeek Integration**
- Kerberos logs  
- NTLM traffic  
- SMB service discovery  
- DNS queries from domain-joined hosts

Together, this forms your full IDS + SIEM + EDR + Identity stack.

---

## 🧪 6. Verification Checklist

### **Domain Controller**
- [x] Promote to DC  
- [x] AD DS Installed  
- [x] DNS Integrated  
- [x] AD CS Installed  
- [x] IIS Configured  

### **SOC Integration**
- [x] Splunk Forwarder Installed  
- [x] Wazuh Agent Installed  
- [x] Event Logs captured  
- [x] FIM Enabled  
- [x] Sysmon Installed  

---

## 📘 7. Future Enhancements

- Add **GPO deployment for Sysmon.xml**
- Configure **LDAP integration for ClearPass**
- Create **SOC Playbooks** for:  
  - Brute force attack  
  - Privilege escalation  
  - Password spray  
  - Malware detection
- Generate dashboards in Splunk:
  - Authentication Statistics  
  - AD Security Events  
  - User Behavior Analytics  

---

## 🏁 Final Notes

This Active Directory environment is now fully production‑grade and integrated into the ECL SOC ecosystem.  
The documentation, screenshots, and explanations reflect professional‑style design decisions suitable for resumes, hiring managers, and portfolio reviews.

