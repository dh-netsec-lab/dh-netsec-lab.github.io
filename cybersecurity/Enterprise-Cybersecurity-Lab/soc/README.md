# **Phase 4 — Threat Detection & Response**

Welcome to **Phase 4** of the *Enterprise Cybersecurity Lab (ECL)*.  
This phase demonstrates **SOC visibility**, **threat detection**, and **risk-informed response**
using network, endpoint, identity, firewall, and vulnerability telemetry to model real-world
SOC investigation workflows.

---

## ⚡ Phase 4 Objectives

- Generate realistic attacker activity  
- Detect reconnaissance, enumeration, and suspicious behavior  
- Analyze network and endpoint telemetry in Splunk  
- Correlate detections with asset risk and vulnerability context  
- Support informed response and prioritization decisions  

---

# 🔍 Threat Detection Lab Modules

Below are the structured lab modules for Phase 4. Each module includes
attack simulation, telemetry validation, screenshots, and analysis workflows.

---

## ▶️ **Module 1 — ICMP Baseline Visibility**

Establish a clean baseline using ICMP traffic and verify Suricata and Zeek
capture and log expected behavior.

🔗 **[Open Module 1 — ICMP Baseline](./module_1-icmp-baseline/README.md)**

---

## ▶️ **Module 2 — Nmap Host Discovery Scan**

Detect ICMP, ARP, and TCP-based host discovery scanning from an attacker system.

🔗 **[Open Module 2 — Nmap Host Discovery](./module_2-nmap-host-discovery/README.md)**

---

## ▶️ **Module 3 — Nmap Port Scanning**

Detect SYN, CONNECT, FIN, XMAS, and NULL scans using Suricata, Zeek, and Splunk.

🔗 **[Open Module 3 — Nmap Port Scanning](./module_3-nmap-port-scanning/README.md)**

---

## ▶️ **Module 4 — Active Directory Credential Enumeration**

Detect LDAP, SMB, NTLM, and Active Directory credential probing activity.

🔗 **[Open Module 4 — AD Credential Enumeration](./module_4-ad-credential-enumeration/README.md)**

---

## ▶️ **Module 6 — Sysmon Port Enumeration Detection**

Detect endpoint-level port enumeration using Sysmon EventCode 3 and analyze
suspicious outbound connection patterns in Splunk.

🔗 **[Open Module 6 — Sysmon Port Enumeration](./module_6-sysmon-port-enumeration/README.md)**

---

## ▶️ **Module 7 — Vulnerability Management with Nessus**

Establish vulnerability context for enterprise assets and demonstrate how
attack surface and configuration weaknesses inform detection priority
and response decisions.

🔗 **[Open Module 7 — Vulnerability Management](./module_7-vulnerability-management/README.md)**

---

## 🔭 Phase 4 Telemetry Coverage

Phase 4 integrates multiple security telemetry sources to support
threat detection and response workflows, including:

- **Network-based detection:** Suricata and Zeek  
- **Endpoint-based detection:** Sysmon and Windows event logs  
- **Identity telemetry:** Active Directory authentication events  
- **Firewall telemetry:** Palo Alto and Fortinet threat and traffic logs  
- **Vulnerability context:** Nessus vulnerability assessment data  

Each telemetry source is analyzed within the context of the associated
lab modules to demonstrate realistic SOC investigation and decision-making.

---

## 🔗 Navigation

- ← **[Back to SOC Overview](../README.md)**  
- ← **[Back to Portfolio Home](../../README.md)**  
