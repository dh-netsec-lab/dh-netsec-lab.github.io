#  Detection Engineering (SOC-102)

## Overview
The **Detection Engineering** section of the Enterprise Cybersecurity Lab represents **SOC-102** — the transition from alert triage to **designing, validating, and tuning detections**.

While SOC-101 focuses on *how analysts investigate alerts*, SOC-102 focuses on a deeper question:

> **What should we be detecting, and why?**

This section demonstrates how security telemetry is transformed into **reliable, high-signal detections** using network visibility, behavioral analysis, and correlation logic.

---

##  Purpose
Detection engineering sits at the intersection of:
- Network visibility
- Security analytics
- SOC operations
- Architecture decisions

The goal is to move beyond reactive alerting and toward:
- Earlier detection
- Fewer false positives
- Better coverage of attacker behavior
- Clear understanding of visibility gaps

---

##  SOC-101 vs SOC-102

| SOC-101 (Analyst) | SOC-102 (Detection Engineering) |
|-----------------|--------------------------------|
| Investigate alerts | Design detections |
| Endpoint-heavy | Network-centric |
| “What happened?” | “What should we detect?” |
| Reactive | Proactive |
| Case-based | Signal-based |

SOC-102 builds on SOC-101 but requires a **different mindset**: engineering reliable signals, not just responding to them.

---

##  Core Telemetry & Tooling
Detection engineering scenarios in this section leverage:

- **Zeek** — Behavioral network analysis and protocol metadata  
- **Suricata** — Signature and protocol-level visibility  
- **Splunk** — Detection logic, correlation, and tuning  
- **SPAN / TAP** — Realistic traffic ingestion points  
- **Multiple Hosts** — East/West traffic and lateral visibility  
- **Wazuh** — Contextual enrichment (not primary detection)

These tools are used to **reason about behavior**, not simply generate alerts.

---

##  Detection Engineering Scenarios
Rather than traditional “labs,” SOC-102 is organized into **Detection Engineering Scenarios**, each focused on a specific capability:

- Establishing **network baselines**
- Identifying **protocol abuse**
- Correlating behavior across **multiple hosts**
- Tuning detection logic to reduce noise
- Identifying **visibility gaps** in enterprise environments

Each scenario answers:
1. What telemetry is available?
2. What does *normal* look like?
3. What deviation matters?
4. Why should this alert exist?
5. How is it tuned?

---

##  Skills Demonstrated
By completing SOC-102 detection engineering scenarios, this lab demonstrates:

- Network behavior analysis
- East/West visibility reasoning
- Detection logic design
- False-positive reduction
- Security telemetry correlation
- Architectural awareness of monitoring blind spots

These scenarios build on foundational SOC skills and progress toward detection engineering responsibilities through practical, real-world telemetry analysis.

---

##  What Comes Next
SOC-102 bridges the gap between SOC operations and advanced security practice.

From here, the lab expands into:
- **Threat Hunting** — hypothesis-driven analysis
- **Incident Response** — containment and remediation
- **Risk & Exposure Management** — understanding impact beyond detection

SOC-102 is where the mindset shifts from *responding* to **engineering security outcomes**.

---

← **[Back to Enterprise Cybersecurity Lab](../)**  
→ **[Continue to Detection Engineering Scenarios](./)**  


