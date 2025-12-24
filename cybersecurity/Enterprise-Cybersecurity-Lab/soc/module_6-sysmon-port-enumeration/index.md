# Module 6 — Detecting Port Enumeration with Sysmon EventCode 3

## Overview
This module demonstrates how **Sysmon EventCode 3 (Network Connection)**
can be used to detect suspicious outbound activity and how a SOC analyst
validates that activity in **Splunk**.

The scenario simulates PowerShell-based network activity originating
from an internal host and confirms visibility, context, and triage.

---

## Lab Environment
- Endpoint: **ECL-JUMPBOX-01**
- OS: Windows Server 2022
- Telemetry: Sysmon (EventCode 3)
- SIEM: Splunk

---

## Detection Objective
Identify suspicious outbound network connections by validating:
- Process context (PowerShell)
- Destination IP and port
- Protocol and initiation direction
- Temporal correlation in Splunk

---

## 1. Verify Sysmon Network Telemetry

Confirm Sysmon is generating **EventCode 3** network connection events.

<img src="./screenshots/01-sysmon-eventcode3-telemetry.png" width="900"/>

---

## 2. Observe PowerShell Network Activity

Validate outbound PowerShell-initiated connections including
destination IP and SSH (port 22).

<img src="./screenshots/02-sysmon-powershell-ssh.png" width="900"/>

---

## 3. Detection & Validation in Splunk

Confirm EventCode 3 visibility and validate timing and context
using Splunk search and visualization.

<img src="./screenshots/03-splunk-detection-view.png" width="900"/>

---

## MITRE ATT&CK Mapping
- **T1046 – Network Service Scanning**

---

## Analyst Takeaways
- Sysmon EventCode 3 provides high-fidelity host-level network telemetry
- Process context is critical for triage
- SIEM correlation enables rapid validation of suspicious activity

---

## Conclusion
This module demonstrates reliable detection and investigation of
suspicious network behavior using deterministic endpoint telemetry
and structured SOC workflows.
