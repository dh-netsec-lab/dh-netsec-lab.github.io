# 🧩 **Enterprise Active Directory Setup – ECL.lab**

This document provides a full overview of the **Active Directory Domain Services (AD DS)** configuration in the **Enterprise Cybersecurity Lab (ECL)**.  
It includes domain structure, OU design, users/groups, DNS configuration, and the enterprise Certificate Authority (ADCS) that anchors the lab’s identity & trust infrastructure.

---

 **Domain Overview**

| Key Component | Value |
|---------------|-------|
| **Domain Name** | `ECL.lab` |
| **Primary Domain Controller** | `ECL-DC01` |
| **Windows Version** | Windows Server 2012 R2 Standard |
| **Roles Installed** | AD DS, DNS, ADCS (Enterprise Root CA), IIS |

---

# 🗂️ **Organizational Unit (OU) Structure**

## **AD Domain Root**
![AD Domain Root](screenshots/ad-domain-root.png)

---

## **ECL-Computers OU**
![ECL Computers OU](screenshots/ad-computers-ou.png)

---

## **ECL-Groups OU**
![ECL Groups OU](screenshots/ad-ecl-groups-ou.png)

---

## **ECL-Users OU**
![ECL Users OU](screenshots/ad-ecl-users-ou.png)

---

#  **Domain Admin Properties**
![Domain Admin Properties](screenshots/ad-domain-admin-properties.png)

---

# 🖥️ **Active Directory Users and Computers View**
![ADUC Full View](screenshots/ecl-ad-users-and-computers.png)

---

# 🏢 **Domain Controllers OU**
![Domain Controllers OU](screenshots/ad-domain-controllers-ou.png)

---

# 🌐 **DNS Configuration**
![DNS Forward Lookup Zone](screenshots/dns-forward-lookup-zone.png)

---

# 🔐 **Public Key Infrastructure – ADCS (Certificate Authority)**

Your domain controller is also an **Enterprise Root CA**, powering:

- SSL decryption for Palo Alto  
- Internal HTTPS services (IIS)  
- Machine certificate issuance  
- ClearPass identities  
- Wazuh secure enrollment  
- TLS inspection for Suricata/Zeek  
- Future SOC authentication workflows  

## **ADCS Role Installed**
![ADCS Role Installed](screenshots/dc-ca-role-installed.png)

---

## **Certificate Authority Console**
![CA Console](screenshots/dc-ca-console.png)

---

# 🌐 **IIS Web Server Role (Installed)**
*(Add screenshot when available)*

---

# 🏁 **Summary**

Your AD environment is now:

✔️ Fully documented  
✔️ Portfolio-ready  
✔️ Designed to match real enterprise architecture  
✔️ Integrated with CA, DNS, SOC tooling, and authentication workflows  
✔️ Following hiring-manager-friendly structure

