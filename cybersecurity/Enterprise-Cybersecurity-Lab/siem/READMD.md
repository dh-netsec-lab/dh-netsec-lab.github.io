# 🛡️ Phase 2 – Security Visibility & Telemetry (SIEM Pipeline)

Phase 2 establishes full **enterprise telemetry** by integrating endpoint logs, syslogs, network metadata, and security alerts into a unified SIEM pipeline.  
This phase builds the **log ingestion backbone** required for threat detection, SOC analysis, and later phases of the Enterprise Cybersecurity Lab (ECL).

---

## 🔎 Phase 2 Architecture Overview

```
[Windows Sysmon]         [Linux / Firewalls / Devices]
        ↓                              ↓
   Sysmon Logs                    Syslog Messages
        ↓                              ↓
        →→→→→→ [Rsyslog Aggregator] →→→→→→
                        ↓
                Log Normalization
                        ↓
                Splunk Forwarder
                        ↓
              [Splunk Enterprise SIEM]
                        ↓
     ┌────────────────────────────────────────┐
     │ Suricata IDS • Zeek NSM • Wazuh SIEM  │
     │ Add detection, metadata, and alerts    │
     └────────────────────────────────────────┘
```

---

## 📁 Phase 2 File Structure

```
siem/
├── rsyslog-forwarding-lab/
├── splunk-forwarder-lab/
├── suricata-lab/
├── sysmon-lab/
├── zeek-lab/
└── wazuh-lab/
```

---

## 📘 Phase 2 Lab Navigation

| Step | Lab | Purpose | View |
|------|------|---------|-------|
| 1 | **Rsyslog Forwarding Lab** | Central syslog aggregation from network devices | [View Lab →](rsyslog-forwarding-lab/) |
| 2 | **Splunk Forwarder Lab** | Forwards normalized logs to Splunk SIEM | [View Lab →](splunk-forwarder-lab/) |
| 3 | **Suricata IDS Lab** | Network intrusion detection alerts → Splunk | [View Lab →](suricata-lab/) |
| 4 | **Sysmon Endpoint Lab** | Deep Windows host telemetry → Rsyslog/Splunk | [View Lab →](sysmon-lab/) |
| 5 | **Zeek Network Metadata Lab** | Protocol metadata / NSM logs → Splunk | [View Lab →](zeek-lab/) |
| 6 | **Wazuh SIEM Lab** | Host IDS + log correlation → Splunk alerts | [View Lab →](wazuh-lab/) |

---

## 🎯 Phase Summary

Phase 2 completes the **visibility foundation** of the Enterprise Cybersecurity Lab.  
By integrating host telemetry, network metadata, syslogs, IDS alerts, and SIEM indexing, this phase provides:

- End-to-end observability  
- SOC-level detection capability  
- Forensic visibility across all systems  
- A unified log pipeline for advanced analysis  

This telemetry backbone is essential for **Phase 3 (Identity & Trust)** and **Phase 4 (Threat Detection & Response)**.

---

## 🧭 Navigation

- ← [Back to ECL Home](../README.md)  
- → Phase 3: Identity & Trust Integration *(coming soon)*

