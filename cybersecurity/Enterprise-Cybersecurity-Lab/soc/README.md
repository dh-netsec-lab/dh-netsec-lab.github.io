# Module 6 — Detecting Port Enumeration with Sysmon EventCode 3

## Overview
This module demonstrates how Sysmon EventCode 3 (Network Connection)
can be used to detect suspicious outbound network activity from an
endpoint and how a SOC analyst investigates that activity using Splunk.

The focus of this lab is **endpoint-based telemetry and triage**, aligned
to SOC-101 fundamentals.

---

## Lab Environment
- **Endpoint:** ECL-JUMPBOX-01 (Windows Server 2022)
- **Telemetry Source:** Sysmon (EventCode 3 – Network Connection)
- **SIEM:** Splunk
- **Data Source:** Windows Sysmon Operational Log

---

## Detection Objective
Identify potentially suspicious outbound connections by analyzing:
- Initiating process
- Destination IP and port
- Connection frequency
- Analyst investigation pivots

This module does **not** assume malware or compromise. The goal is to
demonstrate **detection and triage**, not attribution.

---

## 1. Validate Sysmon Network Telemetry
Sysmon EventCode 3 confirms that the endpoint is generating network
connection telemetry, including process name, destination IP, and port.

<img src="./screenshots/01-sysmon-eventcode3-telemetry.png" width="900"/>

**Key fields observed:**
- Image
- DestinationIp
- DestinationPort
- Protocol
- Initiated

---

## 2. Detection in Splunk
The analyst aggregates EventCode 3 activity to identify repeated
outbound connections that may warrant further investigation.

<img src="./screenshots/02-sysmon-eventcode3-detection.png" width="900"/>

This view supports detection logic by highlighting:
- Repeated destination ports
- Common destination IPs
- Processes responsible for the connections

---

## 3. SOC Investigation Pivot
The analyst pivots into process-specific activity to understand
context and intent behind the network connections.

<img src="./screenshots/03-sysmon-eventcode3-investigation.png" width="900"/>

This investigation step ties together:
- Process execution
- Network behavior
- Potential risk context

---

## MITRE ATT&CK Mapping
- **T1046 – Network Service Scanning**

---

## Analyst Takeaways
- Sysmon provides deterministic, high-fidelity endpoint network telemetry
- EventCode 3 enables early detection of reconnaissance activity
- Splunk supports efficient triage and investigation workflows
- Clear scoping prevents over-alerting and false assumptions

---

## Conclusion
Sysmon EventCode 3 is an effective foundational telemetry source for
SOC analysts to detect and investigate suspicious outbound network
activity when paired with SIEM analytics.

This module demonstrates **SOC-101–level detection and triage** using
real endpoint telemetry and defensible investigation steps.
