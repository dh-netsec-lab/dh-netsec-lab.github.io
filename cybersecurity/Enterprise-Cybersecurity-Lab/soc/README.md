# **Phase 4 -- Threat Detection & Response**

Welcome to **Phase 4** of the *Enterprise Cybersecurity Lab (ECL)*.  
This phase focuses on demonstrating **SOC visibility**, **threat detection**, and **attack simulation** using Suricata, Zeek, Rsyslog, Splunk, and Windows/Linux telemetry.

---

## ⚡ Phase 4 Objectives

- Generate realistic attacker activity  
- Detect reconnaissance, enumeration, and suspicious traffic  
- Validate Suricata & Zeek alerts  
- Forward logs through Rsyslog → Splunk  
- Build actionable detection dashboards  
- Correlate firewall, endpoint, and IDS telemetry  

---

# 🔍 Threat Detection Lab Modules

Below are the structured lab modules for Phase 4. Each module includes screenshots, attack execution steps, IDS/SIEM visibility, and analysis workflows.

---

## ▶️ **Module 1 — ICMP Baseline Visibility**

Establish a clean baseline using ICMP traffic (ping) and verify Suricata + Zeek capture SPAN traffic correctly.

🔗 **[Open Module 1 — ICMP Baseline](./module_1-icmp-baseline/README.md)**

---

## ▶️ **Module 2 — Nmap Host Discovery Scan**

Detect ICMP, ARP, and TCP-based host discovery scanning from a Kali attacker.

🔗 **[Open Module 2 — Nmap Host Discovery](./module_2-nmap-host-discovery/README.md)**

---

## ▶️ **Module 3 — Nmap Port Scanning**

Detect SYN, CONNECT, FIN, XMAS, and NULL port scans using Suricata, Zeek, and Splunk.

🔗 **[Open Module 3 — Nmap Port Scanning](./module_3-nmap-port-scanning/README.md)**

---

## ▶️ **Module 4 — Active Directory Credential Enumeration**

Detect LDAP, SMB, NTLM, and AD-related credential probing activity.

🔗 **[Open Module 4 — AD Credential Enumeration](./module_4-ad-credential-enumeration/README.md)**

---

## ▶️ **Module 5 — Command & Control Beaconing**

Simulate beacon-style periodic outbound traffic and analyze with Suricata, Zeek, and Splunk.

🔗 **[Open Module 5 — C2 Beaconing](./module_5-c2-beaconing/README.md)**

---

# 🔭 Upcoming Deep-Dive Threat Labs

These will be added as data is collected.

### Suricata Alert Validation  
- ICMP alerting  
- TCP/UDP scan detection  
- Suspicious protocol signatures  

### Zeek Log Analysis  
- Conn.log deep dives  
- Notice logs  
- Weird events  
- DNS/HTTP enumeration patterns  

### Sysmon Threat Events  
- Process creation anomalies  
- Suspicious PowerShell  
- Persistence behaviors  

### Authentication & Credential Threats  
- AD brute-force detection  
- Kerberos anomalies  

### Firewall Threat Visibility  
- Palo Alto threat logs  
- Fortinet UTM events  
- Policy-denied traffic correlation  

---

# 🔗 Navigation

- ← **[Back to SOC Overview](../README.md)**  
- ← **[Back to Portfolio Home](../../README.md)**
