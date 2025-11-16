# 🧠 Active Directory & Core Windows Services Setup

This document details the full **Active Directory**, **Certificate Authority**, and **IIS Web Server** configuration used in the **Enterprise Cybersecurity Lab (ECL)**.

---

## 📁 Domain Overview

- **Domain Name:** `ECL.lab`
- **Primary Domain Controller:** `ECL-DC01`
- **Windows Server Version:** *2012 R2 Standard*
- **Core Roles Installed:**
  - Active Directory Domain Services (AD DS)
  - DNS Server
  - Active Directory Certificate Services (AD CS)
  - Web Server (IIS)

---

# 🏛️ Active Directory Structure

## 1. Domain Root  
![AD Domain Root](./screenshots/ad-domain-root.png)

## 2. Domain Controllers OU  
![Domain Controllers OU](./screenshots/ad-domain-controllers-ou.png)

## 3. Computers OU  
![Computers OU](./screenshots/ad-computers-ou.png)

## 4. ECL-Groups OU  
![ECL Groups OU](./screenshots/ad-ecl-groups-ou.png)

## 5. ECL-Users OU  
![ECL Users OU](./screenshots/ad-ecl-users-ou.png)

## 6. Domain Admin Properties  
![Domain Admin Properties](./screenshots/ad-domain-admin-properties.png)

## 7. AD Users & Computers (Tree View)  
![AD Users & Computers Tree](./screenshots/ecl-ad-users-and-computers.png)

---

# 🔐 Certificate Authority (AD CS)

The CA provides certificates for:
- Internal servers  
- Workstations  
- Firewall integrations (Palo Alto & Fortinet)  
- Future secure services: SSL inspection, NPS, ClearPass, etc.

## CA Role Installed  
![CA Role Installed](./screenshots/dc-ca-role-installed.png)

## CA Console  
![CA Console](./screenshots/dc-ca-console.png)

---

# 🌐 IIS Web Server (Installed on DC)

Used for internal services such as:
- Software distribution  
- Hosting internal landing/testing pages  
- Certificate enrollment pages  

## IIS Role Installed  
![IIS Role Installed](./screenshots/iis-role-installed.png)

## Default Web Site  
![IIS Default Website](./screenshots/iis-default-website.png)

## IIS Software Center Folder  
![Software Center](./screenshots/iis-software-center-folder.png)

## IIS Tools Menu  
![IIS Tools Menu](./screenshots/iis-tools-menu.png)

---

# 🔄 DNS Configuration

## Forward Lookup Zone  
![DNS Forward Lookup Zone](./screenshots/dns-forward-lookup-zone.png)

---

# 🏁 Final Notes

This Active Directory environment forms the backbone of the **ECL SOC ecosystem**, supporting:

- Identity management  
- Certificate deployment  
- Log forwarding and visibility  
- Secure authentication for servers and firewalls  
- Future integrations (ClearPass, Suricata, Zeek, Wazuh, Splunk)

This layout reflects a **professional, enterprise‑grade AD deployment**, appropriate for engineering work and portfolio documentation — while remaining neutral for current employer visibility.

---

*Last updated: November 2025*
