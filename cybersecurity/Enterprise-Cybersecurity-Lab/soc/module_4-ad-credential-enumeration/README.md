# 🔴 SOC-101 Module 4 — Active Directory Credential Enumeration (Final)

## 🎯 Objective
This module demonstrates how a Security Operations Center (SOC) detects, investigates, and validates **Active Directory (AD) credential enumeration** activity — a critical precursor to credential theft, lateral movement, and domain compromise.

The focus of this module is **detection and analyst decision-making**, not exploitation.

---

##  Threat Scenario
After gaining initial access, attackers commonly perform **Active Directory enumeration** to:
- Identify valid domain users
- Discover service accounts
- Assess authentication weaknesses
- Prepare for credential abuse (Kerberoasting, AS-REP roasting, brute force)

In this lab, a simulated attacker executes common AD enumeration techniques from a **non-privileged workstation**, while the SOC monitors enterprise telemetry.

---

##  Attack Simulation (What Was Done)
The following enumeration techniques were executed against the domain:

- **Kerbrute** — Kerberos-based user enumeration
- **AS-REP Roasting** — Identifying users without Kerberos pre-authentication
- **Enum4Linux** — SMB-based user enumeration
- **LDAP Anonymous Enumeration** — Directory queries without authentication

These techniques intentionally generate **authentication anomalies and reconnaissance patterns** observable by SOC tooling.

---

##  Telemetry Sources Observed

| Layer | Tooling | Purpose |
|-----|--------|--------|
| Network | Suricata | DNS and reconnaissance traffic |
| Network | Zeek | DNS queries and directory resolution |
| Host | Windows Security Logs | Authentication activity |
| Endpoint / SIEM | Wazuh | Centralized auth event visibility |

---

##  Detection & Investigation

### 1️⃣ Network Reconnaissance Visibility
Suricata and Zeek revealed **abnormal DNS and directory resolution activity** consistent with reconnaissance behavior.

**Evidence:**

![Suricata DNS Evidence](screenshots/suricata-dns.png)

![Zeek DNS Evidence](screenshots/zeek-dns.png)

---

### 2️⃣ Authentication Anomalies
Windows Security Event Logs captured abnormal authentication behavior:

- **EventCode 4625** — Failed logon attempts  
- **EventCode 4768** — Kerberos authentication ticket requests  

**Evidence:**

![Windows Authentication Evidence](screenshots/windows-detection-4625-4768.png)

---

### 3️⃣ Endpoint & SIEM Correlation
Wazuh aggregated Windows authentication events and correlated them across time and source host.

**Evidence:**

![Wazuh Authentication Events](screenshots/wazuh-auth-events.PNG)

---

##  Expected vs Malicious Behavior

| Behavior | SOC Assessment |
|-------|----------------|
| Normal user logons during business hours | ✅ Expected |
| Occasional authentication failures | ✅ Expected |
| Repeated Kerberos auth attempts from workstation | 🚨 Suspicious |
| Enumeration across multiple protocols | 🚨 Malicious |
| Recon activity without admin context | 🚨 High Risk |

---

##  SOC Analyst Investigation Flow
1. Alert triggered — authentication anomalies observed  
2. Source validation — activity traced to non-privileged workstation  
3. Telemetry correlation — network and authentication logs aligned  
4. Behavior analysis — enumeration patterns confirmed  
5. Risk assessment — credential harvesting suspected  
6. SOC decision — incident escalation and containment recommended  

---

##  SOC Analyst Verdict
> “Multiple authentication and directory enumeration techniques were observed originating from a non-privileged workstation. The activity is consistent with Active Directory credential enumeration and represents a high-risk precursor to credential abuse.”

**Severity:** High

**Recommended Actions:**
- Isolate the source host
- Reset potentially exposed credentials
- Investigate for lateral movement attempts

---

##  MITRE ATT&CK Mapping

| Technique | ID | Description |
|--------|----|------------|
| Account Discovery | T1087 | User and group enumeration |
| Brute Force | T1110 | High-volume authentication attempts |
| Kerberos Pre-Auth Abuse | T1558.004 | AS-REP roasting behavior |
| Credential Access | TA0006 | Enumeration leading to credential theft |
| Valid Accounts | T1078 | Abuse of legitimate credentials |

---

##  Additional Enumeration Artifacts

![Kerbrute Enumeration](screenshots/kerbrute-user-enum.png)

![AS-REP Enumeration](screenshots/asrep-enum.png)

![Enum4Linux Users](screenshots/enum4linux-users.png)

![LDAP Enumeration](screenshots/ldapsearch-enum.png)

---

##  Module Outcome
This module demonstrates:
- Enterprise-grade AD visibility  
- Detection of credential enumeration activity  
- SOC investigation methodology  
- Analyst decision-making and escalation  

✅ **SOC-101 Module 4 Complete**
