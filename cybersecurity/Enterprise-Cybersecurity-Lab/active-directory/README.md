# Active Directory Setup (ECL Lab)

## Overview
This document provides detailed documentation of the Active Directory (AD), Certificate Authority (CA), and IIS Web Server configuration in the Enterprise Cybersecurity Lab (ECL). It includes architecture, roles, screenshots, and how AD integrates with SOC tooling such as Splunk, Wazuh, Suricata, and Zeek.

---

## AD Domain Configuration

**Domain Name:** ECL.lab  
**Primary Domain Controller:** ECL-DC01  
**Windows Server Version:** Windows Server 2012 R2 Standard  
**Roles Installed:**  
- Active Directory Domain Services (AD DS)  
- DNS Server  
- Certificate Authority (AD CS)  
- IIS Web Server (for Software Center hosting)

---

## AD Organizational Structure

### Domain Root  
[ad-domain-root.png](./screenshots/ad-domain-root.png)

### Domain Controllers OU  
[ad-domain-controllers-ou.png](./screenshots/ad-domain-controllers-ou.png)

### Computers OU  
[ad-computers-ou.png](./screenshots/ad-computers-ou.png)

### ECL Groups OU  
[ad-ecl-groups-ou.png](./screenshots/ad-ecl-groups-ou.png)

### ECL Users OU  
[ad-ecl-users-ou.png](./screenshots/ad-ecl-users-ou.png)

### Domain Admins Properties  
[ad-domain-admin-properties.png](./screenshots/ad-domain-admin-properties.png)

### AD Users & Computers (Tree View)  
[ecl-ad-users-and-computers.png](./screenshots/ecl-ad-users-and-computers.png)

---

## Certificate Authority (CA)

The Domain Controller also functions as the **Enterprise Root Certificate Authority**.  
The CA issues certificates for:  
- Workstations  
- Servers  
- Splunk  
- Palo Alto & Fortinet firewalls  
- Future ClearPass integrations  
- SSL inspection labs  
- Secure RADIUS/EAP authentication

### CA Role Installed  
[dc-ca-role-installed.png](./screenshots/dc-ca-role-installed.png)

### CA Console  
[dc-ca-console.png](./screenshots/dc-ca-console.png)

---

## IIS Web Server

IIS is installed on the domain controller to support internal application delivery, such as the **Software Center** repository for agents and tools.

### IIS Role Installed  
[iss-role-installed.png](./screenshots/iss-role-installed.png)

### Default Web Site  
[iis-default-website.png](./screenshots/iis-default-website.png)

### Software Center Folder  
[iis-software-center-folder.png](./screenshots/iis-software-center-folder.png)

### IIS Tools Menu  
[iss-tools-menu.png](./screenshots/iss-tools-menu.png)

---

## How AD Integrates Into the SOC

Active Directory is the backbone of identity in the ECL SOC:

### 🔐 Identity & Access  
- AD accounts are used for workstation authentication  
- Domain Admin credentials protect privileged SOC functions  
- Multi‑tier OU structure models enterprise identity design  

### 🧩 SOC Telemetry  
- DC logs flow to Wazuh (File Integrity Monitoring, Authentication, Syscheck)  
- Sysmon logs → forwarded into Splunk  
- DNS logs → monitored via Zeek  
- Certificate issuance audited via Windows Event Logs  

### 🛡️ Zero Trust Foundations  
- CA enables mutual‑TLS, SSL inspection, and endpoint cert enrollment  
- GPOs enforce consistent workstation policy  
- IIS hosts trusted internal tools  

---

## Final Notes

This documentation reflects a realistic enterprise-grade AD environment fully integrated into the ECL SOC.  
It demonstrates identity management, certificate trust, auditing, server roles, and secure application hosting.

