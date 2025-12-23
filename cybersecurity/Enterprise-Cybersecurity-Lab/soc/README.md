### Telemetry Scope (SOC-101)

SOC-101 intentionally focuses on deterministic endpoint telemetry to
build strong detection and triage fundamentals.

Other detection and security capabilities exist elsewhere in the ECL
and are introduced in later phases, including:

- Network detection (Zeek, Suricata)
- Firewall and NAC telemetry
- Vulnerability scanning and risk context
- Threat hunting and hypothesis-driven analysis


---

## 🧩 Telemetry Scope (Intentional)

SOC-101 focuses on **deterministic endpoint telemetry**, which provides
high-confidence, explainable detections.

### Primary Telemetry Sources
- **Endpoint telemetry:** Sysmon & Windows Event Logs
- **SIEM & analysis:** Splunk
- **Identity context:** Active Directory (contextual only)
- **Attack simulation:** Kali Linux

### Explicitly Out of Scope for SOC-101
The following technologies are integrated elsewhere in the ECL
but are **not used in this section by design**:

- Network detection (Zeek, Suricata)
- Firewalls and NAC platforms
- Vulnerability scanning and risk management
- Threat hunting and hypothesis-driven analysis

These capabilities are introduced in **later ECL phases**.

---

## 🔍 SOC-101 Detection Modules

Each module demonstrates **one attacker behavior**, the **telemetry it generates**,
and the **investigation workflow** used to validate it.

### ▶️ Module 1 — Endpoint Network Reconnaissance (Sysmon)
Detect endpoint-initiated network reconnaissance using Sysmon EventCode 3
and analyze suspicious outbound connections in Splunk.

🔗 [Open Module 1 — Sysmon Network Reconnaissance](./module_1-sysmon-network-recon/README.md)

<!-- Future SOC-101 modules will be added incrementally once validated -->

---

## 🛡️ Incident Triage Context

SOC-101 supports **initial incident triage**, not full incident response
program design.

A high-level triage workflow is documented here:

🔗 [SOC Incident Triage Workflow](./incident-response.md)

---

## 🧭 How This Fits Into the ECL

SOC-101 represents the **foundational detection layer** of the Enterprise Cybersecurity Lab.

Additional detection disciplines are intentionally separated:

- **Detection Engineering:** Advanced network and multi-signal detections
- **Vulnerability Management:** Exposure and risk context
- **Threat Hunting:** Hypothesis-driven analysis

This separation reflects how security teams operate in real enterprise environments.

---

## 🔗 Navigation

- ← [Back to Enterprise Cybersecurity Lab](../README.md)
- ← [Back to Portfolio Home](../../README.md)
