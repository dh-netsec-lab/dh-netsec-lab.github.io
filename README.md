# 🧠 Enterprise Cybersecurity Lab (ECL)

Welcome to the **Enterprise Cybersecurity Lab (ECL)** — a multi-vendor, enterprise-grade security environment designed to integrate **network engineering**, **cybersecurity operations**, and **SIEM visibility** into one evolving ecosystem.  

The lab mirrors how a modern SOC-enabled enterprise operates — combining **Fortinet**, **Palo Alto Networks**, **Windows Server**, **Linux (Rsyslog / Suricata / Zeek)**, and **Splunk** to explore end-to-end visibility, policy enforcement, and detection.

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
| ⏳ **Phase 3** | Secure Communication & VPNs | Site-to-Site VPNs, Cross-Vendor Tunnels | **Planned** | [Palo ↔ Fortinet VPN Lab](../../network-security/palo-alto/palo-fortinet-vpn-lab/) |
| ⏳ **Phase 4** | Identity & Trust Integration | AD, DNS, CA, Certificates, User-ID, SSL Decryption | **Planned** | [Palo Alto SSL Decryption Lab](../../network-security/palo-alto/ssl-decryption-lab/) |
| ⏳ **Phase 5** | Security Management Platforms | Panorama, FortiManager, FortiAnalyzer | **Future** | Centralized management, log correlation |
| ⏳ **Phase 6** | Disaster Recovery & Cloud Integration | AWS / Azure failover tunnels, remote logging | **Future** | Hybrid VPN, S3/Cloud storage integration |
| ⏳ **Phase 7** | GRC, Automation & Hardening | Risk Register, PowerShell / Ansible, Policy controls | **Future** | GRC mini-framework, automated configuration |

---

## 🧱 Core Technologies

| Category | Tool / Platform | Purpose |
|:--|:--|:--|
| **Network Edge** | Cisco / Layer-3 Router | Routing, VLAN segmentation |
| **Firewalls** | Fortinet (Bama) / Palo Alto (NY) | Security zones, NAT, IPS, VPN |
| **Servers** | Windows Server 2022 | AD DS, DNS, CA, IIS |
| **Endpoints** | Windows 10 / 11 Clients | Sysmon visibility, Splunk UF |
| **Linux Systems** | Ubuntu (Rsyslog / Suricata / Zeek) | Log collection, traffic analysis |
| **SIEM / Analytics** | Splunk Enterprise / Universal Forwarder | Data aggregation and threat detection |

---

## 📊 Phase Summaries

### 🧩 Phase 1 — Network Connectivity Verification ✅
Establish baseline **routing, NAT, and reachability** across all lab devices.

**Core Components**
- Fortinet “Bama” Firewall — internal LAN gateway  
- Palo Alto “NY” Firewall — remote VPN and inspection point  
- Edge Router — static routes and WAN connectivity  
- LAN Host — ICMP and web connectivity validation  

**Deliverables**
- [View Phase-1 Screenshots](./phase1-network-connectivity/)  
- Verified routing table, NAT rules, and ping success from LAN hosts

---

### 🧩 Phase 2 — Security Visibility & Telemetry (In Progress)
Deploy and validate **Sysmon + Rsyslog + Splunk** to form a cross-platform visibility pipeline.

**Goals**
- Collect Windows and Linux logs  
- Forward to Splunk for normalization  
- Build searches for authentication failures (4625), process creation (4688), etc.

**Related Labs**
- [Sysmon Deployment on Windows Server & Clients](../../cybersecurity/sysmon-deployment/)
- [Rsyslog to Splunk Forwarding](../../cybersecurity/rsyslog-forwarding/)

---

### 🧩 Phase 3 — Secure Communication & VPNs (Planned)
Demonstrate **multi-vendor VPN interoperability** and redundancy.

**Goals**
- Configure Fortinet ↔ Palo Alto Site-to-Site VPN  
- Create Backup Tunnel for redundancy  
- Validate encrypted communication and routing  

**Related Labs**
- [Palo Alto ↔ Fortinet VPN Lab](../../network-security/palo-alto/palo-fortinet-vpn-lab/)
- [Fortinet VPN Lab](../../network-security/fortinet/vpn-lab/)

---

### 🧩 Phase 4 — Identity & Trust Integration (Planned)
Extend enterprise trust using AD, CA, and SSL inspection.

**Goals**
- Integrate AD / LDAP for authentication  
- Issue internal certificates from CA  
- Implement Palo Alto SSL Decryption and SSH Proxy  

**Related Labs**
- [Palo Alto SSL Decryption Lab](../../network-security/palo-alto/ssl-decryption-lab/)
- [User-ID Integration](../../network-security/palo-alto/user-id-lab/)

---

### 🧩 Phase 5 — Security Management Platforms (Future)
Centralize configuration and visibility with management suites.

**Goals**
- Deploy Panorama for Palo Alto management  
- Integrate FortiManager and FortiAnalyzer  
- Push policies from central console  

---

### 🧩 Phase 6 — Disaster Recovery & Cloud Integration (Future)
Demonstrate resilience through cloud-based failover.

**Goals**
- Extend ECL topology into AWS/Azure  
- Simulate DR failover tunnels  
- Replicate Splunk or Rsyslog data to the cloud  

---

### 🧩 Phase 7 — GRC, Automation & Hardening (Future)
Introduce a governance and automation layer to tie it all together.

**Goals**
- Build a mini-risk register and control map  
- Use PowerShell/Ansible for policy enforcement  
- Document compliance posture (NIST / CIS baseline)  

---

## 🧭 Navigation

| Section | Description |
|:--|:--|
| [🔐 Cybersecurity Labs](../) | View all security-focused projects including ECL |
| [🧱 Network Security](../../network-security/) | Explore vendor-specific firewall labs |
| [🌐 Networking](../../networking/) | View routing and switching foundational labs |
| [🏠 Return to Home](../../README.md) | Back to main portfolio index |

---

## 🧠 Next Steps
- Complete **Phase 2 telemetry pipeline** and verify event ingestion  
- Document Sysmon and Splunk visibility screenshots  
- Begin **Phase 3 cross-vendor VPN implementation**  
- Add GRC template for early documentation tracking  

---

🧩 *This lab evolves continuously to mirror real-world enterprise environments. Each phase builds on the previous, emphasizing integration, visibility, and governance.*
