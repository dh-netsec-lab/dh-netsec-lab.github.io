# Module 6 — Detecting Port Enumeration with Sysmon EventCode 3

## Overview
This module demonstrates how Sysmon EventCode 3 can be used to detect
network port enumeration activity and how a SOC analyst investigates
that activity using Splunk.

The scenario simulates an internal host performing a network scan using
Nmap, generating high-volume outbound connections captured by Sysmon
and forwarded to Splunk.

## Lab Environment
- Endpoint: ECL-JUMPBOX-01 (Windows Server 2022)
- Telemetry: Sysmon (EventCode 3 – Network Connection)
- SIEM: Splunk
- Attack Tool: Nmap

---

## Detection Objective
Identify suspicious port enumeration behavior by analyzing:
- High-frequency outbound connections
- Repeated destination IPs
- Sequential destination ports
- Scanning-related processes

---
## Walkthrough

### 1. Verify Sysmon Logging
Confirm Sysmon is installed and generating EventCode 3 network events.

📸 [01-sysmon-verification.png](/module_6-sysmon-port-enumeration/screenshots/01-sysmon-verification.png)

---

### 2. Execute Nmap Scan
Run an Nmap scan from the Jumpbox to generate enumeration traffic.

📸 [02-nmap-scan-execution.png](/module_6-sysmon-port-enumeration/screenshots/02-nmap-scan-execution.png)

---

### 3. Observe Sysmon Network Events
Sysmon records each outbound connection attempt, including destination
IP, destination port, and process name.

📸 [03-sysmon-eventcode3-nessus-scan.png](/module_6-sysmon-port-enumeration/screenshots/03-sysmon-eventcode3-nessus-scan.png)

---

### 4. Detect Enumeration in Splunk
Use Splunk to identify high-volume EventCode 3 activity.

📸 [04-sysmon-enumeration-detection.png](/module_6-sysmon-port-enumeration/screenshots/04-sysmon-enumeration-detection.png)

---

### 5. SOC Investigation
Review timing, volume, and affected ports to confirm scanning behavior.

📸 [05-investigation-view-sysmon-eventcode3.png](/module_6-sysmon-port-enumeration/screenshots/05-investigation-view-sysmon-eventcode3.png)



## MITRE ATT&CK Mapping
- T1046 – Network Service Scanning

---

## Analyst Takeaways
- Port scanning produces repetitive, high-volume network events
- Sysmon provides host-level network visibility
- SIEM correlation enables rapid investigation and response

---

## Conclusion
Sysmon EventCode 3 is an effective detection source for identifying
internal reconnaissance and port enumeration activity when paired
with SIEM analytics.

