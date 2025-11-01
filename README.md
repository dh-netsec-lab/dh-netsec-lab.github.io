# 🧠 Enterprise Cybersecurity Lab (ECL)

The **Enterprise Cybersecurity Lab (ECL)** is a continuously evolving, multi-vendor environment that unites **network engineering**, **cybersecurity operations**, and **SIEM visibility** into one integrated enterprise ecosystem.

This lab demonstrates how real organizations combine **Fortinet**, **Palo Alto Networks**, **Windows Server**, **Linux (Rsyslog / Suricata / Zeek)**, and **Splunk** to achieve visibility, control, and resilience.

---

## 🎯 Lab Purpose

The goal of the **ECL** is to simulate an end-to-end enterprise network — from firewalls and domain controllers to SIEM integration and governance controls — while continuously expanding in scope to include:
- ✅ Multi-vendor security controls (Fortinet + Palo Alto)
- ✅ End-to-end log visibility (Sysmon → Rsyslog → Splunk)
- ✅ Identity, Trust, and Encryption (AD, CA, SSL, VPN)
- ✅ Governance & Risk integration (GRC overlays)
- ✅ Cloud continuity and DR simulations (AWS tunnels)

This is a **long-term learning lab**, designed to grow over time as new technologies, controls, and lessons are added.

---

## 🧭 Quick Navigation

| Section | Description |
|:--|:--|
| [🔐 **Cybersecurity**](../../cybersecurity/) | Enterprise Security labs (ECL, Detection Engineering, etc.) |
| [🧱 **Network Security**](../../network-security/) | [Palo Alto](../../network-security/palo-alto/) & [Fortinet](../../network-security/fortinet/) labs |
| [🌐 **Networking Labs**](../../networking/) | Routing, VLANs, OSPF/BGP, and Layer-3 core design |
| [📊 **GRC & DR Initiatives**](../../grc-dr/) | Governance, Risk, Compliance, and Disaster Recovery |
| [🏠 **Return to Portfolio Home**](../../README.md) | Back to main portfolio overview |

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
| ✅ **Phase 1** | Network Connectivity Verification | Routing, NAT, Firewall reachability | **Complete** | [View Connectivity Validation](./phase1-network-connectivity/) |
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
| **Network Edge** | Cisco / L3 Router | Routing, VLAN segmentation |
| **Firewalls** | Fortinet (Bama) / Palo Alto (NY) | Security zones, NAT, IPS, VPN |
| **Servers** | Windows Server 2022 | AD DS, DNS, CA, IIS |
| **Endpoints** | Windows 10 / 11 Clients | Sysmon telemetry, Splunk UF |
| **Linux Systems** | Ubuntu (Rsyslog / Suricata / Zeek) | Log collection, threat visibility |
| **SIEM / Analytics** | Splunk Enterprise / UF | Data aggregation, detection logic |

---

## 🧩 Lessons Learned & Troubleshooting (Ongoing)

| Area | Example Challenge | Resolution |
|:--|:--|:--|
| Splunk Forwarder (DC) | Service encryption (AES-GCM) errors | Recreated certs, verified permissions |
| Sysmon Deployment | Missing Event IDs in Splunk | Adjusted Winlogbeat & Rsyslog forwarding |
| VPN Cross-Vendor | Tunnel negotiation mismatch | Adjusted Phase-1/Phase-2 proposals |
| SSL Decryption | Untrusted CA in browsers | Imported internal CA into client trust store |

---

## 📚 Next Steps

- Finalize **Phase 2 Telemetry Pipeline** (Sysmon → Rsyslog → Splunk)
- Begin **Phase 3 VPN & Secure Communication**
- Document all screenshots into subfolders per phase
- Develop a **GRC mini-template** (risk register + control tracking)
- Expand **DR lab** — AWS or Azure-based failover

---

🧩 *The ECL is an evolving enterprise simulation — each phase adds new layers of visibility, integration, and governance, bridging technical engineering with cybersecurity resilience.*
