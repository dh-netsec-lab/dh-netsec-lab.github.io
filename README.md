# 🧠 Enterprise Cybersecurity Lab (ECL)

Welcome to the **Enterprise Cybersecurity Lab (ECL)** — a multi-vendor, enterprise-grade network and security environment designed to demonstrate end-to-end visibility, control, and detection across **Fortinet**, **Palo Alto Networks**, **Windows Server**, **Linux (rsyslog/Suricata/Zeek)**, and **Splunk**.

This lab is part of my continuous learning initiative to integrate **network engineering**, **cybersecurity operations**, and **SIEM visibility** into one evolving environment.

---

## 🚦 Lab Progress Overview

![Phase 1: Complete](https://img.shields.io/badge/Phase%201-Complete-brightgreen)
![Phase 2: In Progress](https://img.shields.io/badge/Phase%202-In%20Progress-yellow)
![Phase 3: Planned](https://img.shields.io/badge/Phase%203-Planned-lightgrey)

| Phase | Title | Focus | Status | Key Deliverables |
|:------|:------|:-------|:--------|:-----------------|
| ✅ **Phase 1** | Network Connectivity Verification | Routing, NAT, Firewalls, LAN/WAN reachability | **Complete** | Edge Router, Fortinet (Bama), Palo Alto (NY), LAN Host screenshots |
| 🔄 **Phase 2** | Security Visibility & Telemetry | Sysmon, Rsyslog, Splunk data pipeline | **In Progress** | Endpoint log collection, SIEM correlation |
| ⏳ **Phase 3** | Identity & Trust Integration | AD, DNS, CA, Certificates, User-ID, HTTPS Decryption | **Planned** | Domain authentication, SSL inspection |
| ⏳ **Phase 4** | Threat Detection & Response | Security policies, Sysmon detections, alerting | **Planned** | Splunk correlation searches, detections |
| ⏳ **Phase 5** | Automation & Hardening | Config automation, IaC, risk controls | **Future** | PowerShell, Ansible, GRC overlays |

---

## 🧩 Phase 1 — Network Connectivity Verification ✅

### 🎯 Objective
Establish baseline **network communication** between all lab components:
- Edge Router → HQ Firewall (Fortinet)
- HQ Firewall → Remote Firewall (Palo Alto)
- Internal LAN Hosts → Internet

### 🧱 Core Components
- **Fortinet (Bama Firewall)** — Internal gateway and NAT for 10.0.1.0/24 LAN  
- **Palo Alto (NY Firewall)** — Remote site VPN and inspection  
- **Edge Router** — Multi-interface routing between LAN/WAN segments  
- **LAN Hosts** — Connectivity validation for ICMP and web traffic  

### 📸 Screenshots
- `bama-fw-nat-rules.png` — Fortinet NAT configuration  
- `ny-fw-security-policies.png` — Palo Alto security rules  
- `lan-host-ping-success.png` — Verified outbound reachability  
- `edge-router-route-table.png` — Static routes and interface summary  

---

## 🧩 Phase 2 — Security Visibility & Telemetry (In Progress)

### 🎯 Objective
Establish **end-to-end log visibility** across Windows, Linux, and network devices using a unified data pipeline.

### 🧠 Key Learning Goals
- Understand how Sysmon + Rsyslog + Splunk work together  
- Validate Windows and Linux endpoint visibility  
- Build Splunk searches for event correlation (4625 failures, 4688 process creations, etc.)  

### 🧩 Architecture
