# Module 4 – AD Credential Enumeration Detection Lab

This module focuses on detecting **Active Directory credential enumeration** using Suricata, Zeek, and Splunk.  
Screenshots must be placed in the `screenshots/` directory inside this module.

---

## 📁 Folder Structure
```
module_4-ad-credential-enumeration/
│
├── README.md
└── screenshots/
      ├── ad-enum-suricata-alert.png
      ├── ad-enum-zeek-connlog.png
      ├── ad-enum-zeek-kerberos.png
      ├── ad-enum-splunk-search.png
      └── ad-enum-splunk-dashboard.png
```

---

## 📸 Screenshots (Click to View)

### 1. Suricata Alert – Credential Enumeration  
[![Suricata Alert](./screenshots/ad-enum-suricata-alert.png)](./screenshots/ad-enum-suricata-alert.png)

### 2. Zeek conn.log – LDAP / Kerberos Enumeration  
[![Zeek Connlog](./screenshots/ad-enum-zeek-connlog.png)](./screenshots/ad-enum-zeek-connlog.png)

### 3. Zeek kerberos.log – Suspicious Requests  
[![Zeek Kerberos](./screenshots/ad-enum-zeek-kerberos.png)](./screenshots/ad-enum-zeek-kerberos.png)

### 4. Splunk Search – AD Enumeration Query  
[![Splunk Search](./screenshots/ad-enum-splunk-search.png)](./screenshots/ad-enum-splunk-search.png)

### 5. Splunk Dashboard Panel – Enumeration Activity  
[![Splunk Dashboard](./screenshots/ad-enum-splunk-dashboard.png)](./screenshots/ad-enum-splunk-dashboard.png)

---

## 🧪 Detection Summary

Credential enumeration is a common precursor to lateral movement and privilege escalation.  
This module demonstrates:

### ✔ Suricata  
- Detecting LDAP bind attempts  
- Kerberos anomalies  
- Excessive authentication attempts  

### ✔ Zeek  
- Logging LDAP/Kerberos activity  
- Identifying enumeration-style queries  
- Detecting unusual authentication patterns  

### ✔ Splunk  
- Correlating Suricata + Zeek logs  
- Highlighting enumeration behavior  
- Providing a workflow for SOC triage  

---

## 📝 Notes
- Replace screenshot filenames with your real ones after upload  
- Ensure the folder is named exactly:  
  `module_4-ad-credential-enumeration`

---

## 🔗 Navigation
[← Back to Phase 4 Overview](../README.md)

