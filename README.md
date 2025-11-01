# 🧠 Enterprise Cybersecurity Lab (ECL)

Welcome to the **Enterprise Cybersecurity Lab (ECL)** — a continuously evolving, multi-vendor environment that brings together **network engineering**, **cybersecurity operations**, and **SIEM visibility** in one integrated ecosystem.  

This lab simulates how a modern enterprise environment functions — combining **Fortinet**, **Palo Alto Networks**, **Windows Server**, **Linux (Rsyslog / Suricata / Zeek)**, and **Splunk** to demonstrate real-world concepts like segmentation, telemetry, detection, and governance.

---

## 🧭 Quick Navigation

| Section | Description |
|:--|:--|
| [🔐 **Cybersecurity**](../../cybersecurity/) | Includes the Enterprise Cybersecurity Lab (ECL) and detection-focused projects |
| [🧱 **Network Security**](../../network-security/) | Vendor-specific labs — [Palo Alto](../../network-security/palo-alto/) & [Fortinet](../../network-security/fortinet/) |
| [🌐 **Networking Labs**](../../networking/) | Routing, VLANs, OSPF/BGP, and infrastructure connectivity |
| [📊 **GRC & DR Initiatives**](../../grc-dr/) | Governance, Risk, Compliance, and Disaster Recovery |
| [🏠 **Return to Portfolio Home**](../../README.md) | Back to main portfolio index |

---

## 🚦 Lab Progress Overview

![Phase 1: Complete](https://img.shields.io/badge/Phase%201-Complete-brightgreen)
![Phase 2: In Progress](https://img.shields.io/badge/Phase%202-In%20Progress-yellow)
![Phase 3: Planned](https://img.shields.io/badge/Phase%203-Planned-lightgrey)
![Phase 4: Planned](https://img.shields.io/badge/Phase%204-Planned-lightgrey)
![Phase 5: Future](https://img.shields.io/badge/Phase%205-Future-lightgrey)
![Phase 6: Future](https://img.shields.io/badge/Phase%206-Future-lightgrey)
![Phase 7: Future](https://img.shields.io/badge/Phase%207-Future-lightgrey)

| Phase | Title | Focus | Status | Key Deliverables |
|:------|:------|:-------|:--------|:-----------------|
| ✅ **Phase 1** | Network Connectivity Verification | Routing, NAT, Firewall reachability | **Complete** | [View Network Validation Screenshots](./phase1-network-connectivity/) |
| 🔄 **Phase 2** | Security Visibility & Telemetry | Sysmon, Rsyslog, Splunk data pipeline | **In Progress** | Endpoint log forwarding, correlation searches |
| ⏳ **Phase 3** | Secure Communication & VPNs | Site-to-Site VPNs, Cross-Vendor Tunnels | **Planned** | Palo ↔ Fortinet VPN with backup tunnels |
| ⏳ **Phase 4** | Identity & Trust Integration | AD, DNS, CA, Certificates, SSL Decryption | **Planned** | Domain authentication, SSL inspection |
| ⏳ **Phase 5** | Security Management Platforms | Panorama, FortiManager, FortiAnalyzer | **Future** | Centralized management & log analytics |
| ⏳ **Phase 6** | Disaster Recovery & Cloud Integration | Cloud failover tunnels, remote log sync | **Future** | AWS/Azure hybrid VPN, DR testing |
| ⏳ **Phase 7** | GRC, Automation & Hardening | Risk Register, Policy controls, IaC | **Future** | GRC baseline, PowerShell / Ansible integration |

---

## 🧱 Core Technologies

| Category | Tool / Platform | Purpose |
|:--|:--|:--|
| **Network Edge** | Cisco / Layer-3 Router | Routing, VLAN segmentation |
| **Firewalls** | Fortinet (Bama) / Palo Alto (NY) | Security zones, NAT, IPS, VPN |
| **Servers** | Windows Server 2022 | AD DS, DNS, CA, IIS |
| **Endpoints** | Windows 10 / 11 Clients | Sysmon telemetry, Splunk UF |
| **Linux Systems** | Ubuntu (Rsyslog / Suricata / Zeek) | Log collection, threat visibility |
| **SIEM / Analytics** | Splunk Enterprise / Universal Forwarder | Data aggregation, detection logic |

---

## 🧠 Lab Purpose

The **Enterprise Cybersecurity Lab** serves as the foundation for a long-term initiative to:

- Build a unified **multi-vendor security architecture**
- Demonstrate **real-world SOC visibility** from endpoint → SIEM  
- Integrate **GRC practices** (risk tracking, mitigation, and reporting)
- Practice **disaster recovery and automation** workflows
- Provide a **portfolio-ready showcase** of engineering and cybersecurity capability

---

## 🧩 Lessons Learned & Troubleshooting (Ongoing)

| Area | Example Challenge | Resolution |
|:--|:--|:--|
| Splunk Forwarder (DC) | Service encryption (AES-GCM) errors | Recreated certs, verified permissions |
| Sysmon Deployment | Missing Event IDs in Splunk | Adjusted Winlogbeat & Rsyslog forwarding paths |
| VPN Cross-Vendor | Tunnel negotiation mismatch | Adjusted Phase-1/Phase-2 proposals and PSKs |
| SSL Decryption | Untrusted CA in browsers | Imported internal CA into client trust store |

---

## 📚 Next Steps

- Finalize **Phase 2 Telemetry Pipeline** (Sysmon → Rsyslog → Splunk)
- Begin **Phase 3 VPN & Secure Communication**
- Document all screenshots into subfolders per phase
- Develop a **GRC mini-template** (risk register + control tracking)
- Expand **DR lab** — AWS or Azure-based failover

---

🧩 *The ECL is an ongoing enterprise simulation — every phase builds on the last, creating a living cybersecurity ecosystem that grows in complexity, integration, and visibility.*
