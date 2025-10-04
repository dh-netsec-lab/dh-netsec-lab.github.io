# Palo Alto User-ID Integration with Active Directory

**Category:** Network Security  
**Tools/Tech:** Palo Alto NGFW (PAN-OS 10.1.6), Windows Server 2019 (Active Directory, LDAP)

---

## 🎯 Objective
Integrate a Palo Alto firewall with Microsoft Active Directory to enforce security policies based on user identity.  
This lab demonstrates configuring LDAP integration, creating an authentication profile, and validating user-to-IP mappings.

---

## 🖥 Lab Diagram
(Replace with your own diagram or screenshot)  
![Lab Diagram](../assets/diagrams/palo-uid.png)

---

## ⚙️ Environment Setup
- **Firewall:** Palo Alto VM-100 (PAN-OS 10.1.6)  
- **Domain Controller:** Windows Server 2019 (AD + LDAP)  
- **Service Account:** `svc-palo` created in `OU=ServiceAccounts,DC=4outof7,DC=com`  
- **Network:**  
  - Mgmt: 192.168.118.132  
  - AD/DC: 192.168.118.207  

---

## 📝 Steps
1. **Create Service Account in AD**  
   - Username: `svc-palo`  
   - OU: `ServiceAccounts`  
   - Permissions: Read-only for LDAP bind  

2. **Configure LDAP Server Profile** (PAN-OS GUI)  
   - Name: `AD-LDAP`  
   - Server: `192.168.118.207:389` (StartTLS)  
   - Bind DN: `svc-palo@4outof7.com`  
   - Password: *(account password)*  

3. **Configure Authentication Profile**  
   - Profile: `AD-Auth`  
   - Type: LDAP  
   - Server Profile: `AD-LDAP`  
   - Allow List: `all` or specific AD groups  

4. **Enable User-ID on Internal Zone**  
   - Network → Zones → Enable User-ID  

5. **Validate via CLI**  
   ```bash
   test authentication authentication-profile AD-Auth username svc-palo@4outof7.com password
   show user group list
   show user ip-user-mapping all
