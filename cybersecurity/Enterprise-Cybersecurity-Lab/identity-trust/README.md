# 🔐 Identity & Trust (Phase 3)
### Active Directory • DNS • Group Policy • PKI • ClearPass

Phase 3 establishes centralized **identity, authentication, authorization, and trust services** for the Enterprise Cybersecurity Lab.  
This includes **Active Directory**, **DNS**, **Certificate Services**, **PKI**, and upcoming **ClearPass NAC** integration.

---

## 🧭 Phase 3 Overview

Identity and Trust services form the foundation of every enterprise security program:

- Centralized user and computer authentication  
- Secure certificate issuance and trust chains  
- Directory-based access control  
- Role-based authorization  
- Network Access Control (NAC)  
- Integration with firewalls, VPNs, and security platforms  

This phase strengthens the integrity and authenticity of all systems in the ECL environment.

---

## 🗂️ Phase 3 Folder Structure

```
identity-trust/
├── active-directory/
│     └── README.md
└── clearpass/                ← coming soon
      └── README.md (planned)
```

---

## ✔️ Completed in Phase 3

### **✓ Active Directory Deployment**
- Domain Controller installation  
- Domain `ecl.lab` deployment  
- Users, Groups, and OU structure  
- Administrative groups  
- Group Policy Management  
- Computer & server enrollment  

### **✓ DNS & Domain Integration**
- Forward & reverse lookup zones  
- Internal name resolution  
- DNS delegation for lab subnets  

### **✓ Certificate Authority / PKI**
- AD CS installed  
- Root CA setup  
- SSL Decryption trust chain for Palo Alto & Fortinet  
- Client CA enrollment  
- Certificate template configuration  

### **✓ AD Lab Documentation Added**
➡️ [Open Active Directory Lab →](./active-directory/)

---

## 🚧 In Progress

### **ClearPass Integration**
ClearPass will provide:
- RADIUS / TACACS  
- 802.1X Authentication  
- Machine authentication  
- Profiling & role assignment  
- Enforcement Policies  
- Integration with AD, Firewalls, & Switches  

➡️ *ClearPass lab folder will be added soon.*

---

## 🧩 Identity & Trust Architecture Diagram (Coming Soon)

A diagram will illustrate:
- Domain Controllers  
- ClearPass Cluster  
- Certificate Authority  
- Identity flows  
- Authentication paths  
- Firewall / VPN integration  
- Trust relationships  

---

## 📁 Phase 3 Labs

| Lab | Description | Status | Open |
|------|-------------|--------|-------|
| **Active Directory Lab** | Domain build, OUs, Users, DNS, PKI | ✔️ Completed | [Open →](./active-directory/) |
| **ClearPass NAC Lab** | 802.1X, RADIUS/TACACS, profiling, role enforcement | 🚧 Planned | Coming Soon |
| **PKI Integration** | Trust chains for SSL decryption | ✔️ Completed | Included in AD Lab |

---

## 🔙 Navigation

- ← Back to **Enterprise Cybersecurity Lab Home**  
- → Forward to **Phase 4 – Threat Detection & Response**

