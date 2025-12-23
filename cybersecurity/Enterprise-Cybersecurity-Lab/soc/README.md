# SOC-101 — Threat Detection & Triage Fundamentals

Welcome to the **SOC-101** section of the *Enterprise Cybersecurity Lab (ECL)*.

This directory demonstrates **foundational Security Operations Center (SOC) capabilities**:
how suspicious activity is detected, validated, and triaged using **endpoint telemetry**
and a SIEM before escalation to advanced detection engineering, threat hunting,
or incident response functions.

This section is **intentionally scoped** to prioritize clarity, explainability,
and strong detection fundamentals.

---

## 🎯 Purpose of SOC-101

SOC-101 focuses on demonstrating the ability to:

- Generate realistic attacker activity in a controlled environment
- Detect suspicious endpoint behavior
- Analyze telemetry using a SIEM
- Perform structured alert triage and investigation
- Understand how detections inform response decisions

These workflows align with **Tier 1–2 SOC analyst and SOC engineer responsibilities**
in real enterprise environments.

---

## 🧩 Telemetry Scope (SOC-101)

SOC-101 intentionally emphasizes **deterministic endpoint telemetry**, which provides
high-confidence, explainable detections suitable for foundational SOC work.

### Primary Telemetry Sources
- **Endpoint telemetry:** Sysmon and Windows Event Logs  
- **SIEM & analysis:** Splunk  
- **Identity context:** Active Directory (contextual use only)  
- **Attack simulation:** Kali Linux  

This telemetry stack allows detections to be traced cleanly from
**attacker action → log generation → alert → investigation**.

---

### Additional Detection Capabilities in the ECL

The Enterprise Cybersecurity Lab includes additional security capabilities
that are **integrated elsewhere** and introduced in later phases, including:

- Network detection and visibility (Zeek, Suricata)
- Firewall and NAC telemetry
- Vulnerability scanning and risk context
- Threat hunting and hypothesis-driven analysis

These capabilities are deliberately separated to reflect
how security teams operate across specialized disciplines.

---

## 🔍 SOC-101 Detection Modules

Each SOC-101 module demonstrates **one attacker behavior**, the telemetry it generates,
and the investigation process used to validate the alert.

### ▶️ Module 1 — Endpoint Network Reconnaissance (Sysmon)

Detect endpoint-initiated network reconnaissance using **Sysmon EventCode 3**
and analyze suspicious outbound connection patterns in Splunk.

🔗 **[Open Module 1 — Sysmon Network Reconnaissance](./module_6-sysmon-port-enumeration/README.md)**

<!-- Additional SOC-101 modules will be added incrementally once validated -->

---

## 🛡️ Incident Triage Context

SOC-101 supports **initial incident triage**, not full incident response
program design.

A high-level SOC triage workflow is documented here:

🔗 **[SOC Incident Triage Workflow](./incident-response.md)**

---

## 🧭 How SOC-101 Fits Into the ECL

SOC-101 represents the **foundational detection layer** of the
Enterprise Cybersecurity Lab.

Other security disciplines are intentionally organized as peer sections
within the ECL, including:

- Detection Engineering (advanced and network-based detection)
- Vulnerability Management (exposure and risk context)
- Threat Hunting (hypothesis-driven analysis)
- Security Engineering and Architecture

This separation mirrors real enterprise security team structures
and progression paths.

---

## 🔗 Navigation

- ← **[Back to Enterprise Cybersecurity Lab](../README.md)**
- ← **[Back to Portfolio Home](../../README.md)**
