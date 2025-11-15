
# 📘 Active Directory Setup — Enterprise Cybersecurity Lab (ECL)

This section documents the **Active Directory (AD) environment** used throughout the Enterprise Cybersecurity Lab.  
The AD domain provides centralized **identity, authentication, DNS, and organizational structure** for all security integrations in the lab.

---

## 🏷️ Domain Information

| Item | Value |
|------|--------|
| **Domain Name** | `ecl.lab` |
| **Domain Controller** | `ECL-DC01` |
| **OS Version** | Windows Server 2012 R2 Standard |
| **DNS Role** | Active Directory–Integrated DNS |
| **Time Source** | Local DC (default) |

---

## 🗂️ Organizational Unit (OU) Structure

A clean and intentionally designed OU structure is critical for future GPOs, workstation segmentation, role isolation, and SIEM/NAC integrations.

### OU Structure Implemented
- **ECL-Computers**
  - Firewalls  
  - Servers  
  - Workstations
- **ECL-Groups**
- **ECL-Users**
  - Admins  
  - Service Accounts  
  - Test_Users  

Screenshots:
- `ad-domain-root.png`
- `ad-computers-ou.png`
- `ad-ecl-groups-ou.png`
- `ad-ecl-users-ou.png`

---

## 👤 User & Group Management

The following core accounts/groups support lab authentication, administration, and logging:

### Users
- **DerrickHervey** (Lab primary user)
- **ECL Admin** (Domain administrative account)
- **Service Accounts** (for Splunk, Wazuh, ClearPass)

### Groups
- Domain Users  
- Admins  
- Service Accounts  
- Test Users  

Screenshots:
- `ad-domain-admin-properties.png`  
- `ecl-ad-users-and-computers.png`

---

## 🖥️ Domain Controllers & Role Verification

The lab currently uses **one primary DC**:

- **ECL-DC01**
  - Domain Controller  
  - Global Catalog  
  - DNS Server  
  - Time Authority  

Screenshot:
- `ad-domain-controllers-ou.png`

---

## 🌐 DNS Configuration

Active Directory uses **AD-integrated DNS**, enabling automatic SRV record creation, workstation registration, and hostname lookup.

Configured zones:

- **Forward Lookup Zones**
  - `ecl.lab`
  - `_msdcs.ecl.lab`

Screenshot:
- `dns-forward-lookup-zone.png`

---

## 🔗 How Active Directory Ties Into the SOC (Very Important Section)

Active Directory is **one of the most attacked, monitored, and critical components** in any enterprise security program.  
In the ECL SOC, AD acts as the *identity backbone* and provides **event sources, authentication telemetry, and security controls** that feed your SIEM and detection systems.

### 🔍 1. Authentication Logs → Splunk + Wazuh  
Windows event logs from the Domain Controller provide:

- Logon successes & failures  
- Kerberos ticket activity  
- Account lockouts  
- Lateral movement indicators  
- Privilege escalation attempts  

These logs feed:
- **Splunk** (correlation, dashboards)  
- **Wazuh** (MITRE ATT&CK alerts, agent-based monitoring)

### 🧭 2. DNS Logs → Network Threat Detection  
DNS logs support:
- Suricata / Zeek correlation  
- Suspicious domain lookups  
- C2 domain identification  
- Hostname-to-IP mapping for incident response  

### 🔐 3. AD as a Target for Attack Simulations  
During attack simulations, you will observe attempts to:

- Enumerate the domain  
- Perform pass-the-hash or pass-the-ticket  
- Create rogue users  
- Abuse service accounts  
- Query AD for sensitive objects  

This allows realistic SOC workflows:
- Detect  
- Triage  
- Investigate  
- Remediate  

### 🛡️ 4. Policy Enforcement via GPO  
GPOs allow:

- Security hardening  
- USB blocking  
- Logging policies  
- Firewall rules  
- Sysmon deployment  
- Wazuh agent deployment  

This ensures **consistent security controls across the enterprise**.

### 🔧 5. NAC / ClearPass Integration  
AD provides:
- User identity  
- Group membership  
- Authentication source  

ClearPass will use AD to make decisions such as:
- Which VLAN a device belongs to  
- Whether the device is compliant  
- Whether access should be allowed or quarantined  

---

## 📁 Screenshot Directory

```
/cybersecurity/Enterprise-Cybersecurity-Lab/active-directory/screenshots/
```

---

## ✅ Status

AD configuration is fully functional and integrated into:

- Wazuh EDR  
- Splunk SIEM  
- Suricata / Zeek NIDS  
- Firewall authentication  
- Future ClearPass NAC  
- Future GPO security baselines

