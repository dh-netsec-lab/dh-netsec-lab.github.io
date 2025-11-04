# 🧠 Palo Alto Panorama Centralized Management Lab

### 🌐 Part of the *Enterprise Cybersecurity Lab (ECL)* Series

This lab demonstrates **centralized management of multiple Palo Alto Networks firewalls** using **Panorama**, focusing on scalable configuration deployment, policy control, and VPN management across distributed sites.

The Panorama lab is structured into multiple phases that align with real enterprise workflows—from initial onboarding to full policy and logging integration.

---

## 📘 Table of Contents
- [Phase 1 – Template Creation & Onboarding](#phase1)
- [Phase 2 – Template Stack & VPN Validation](#phase2)
- [Phase 3 – Device Groups & Policy Push](#phase3)
- [Phase 4 – Log Forwarding & SIEM Integration](#phase4)


---

### 🧩 **Lab Overview**

| Component | Description |
|------------|-------------|
| **Platform** | Panorama 10.x managing VM-Series firewalls (**FW188**, **FW189**) |
| **Managed Devices** | Two firewalls onboarded into Panorama representing separate enterprise sites |
| **Management Network** | **192.168.118.0/24** – shared between Panorama and managed firewalls |
| **Configuration Layers** | Templates → Template Stacks → Device Groups |
| **Objective** | Demonstrate hierarchical configuration, centralized policy control, and VPN deployment from Panorama |
| **Outcome** | Achieved centralized firewall management, consistent policy enforcement, and verified VPN & Internet connectivity |

---

### 🧭 **Lab Phases**

| Phase | Focus | Deliverable |
|--------|--------|-------------|
| **Phase 1** | Create and apply Global + Site-Specific Templates | Managed device onboarding, DNS/NTP/Syslog configuration |
| **Phase 2** | Build Template Stacks and deploy Site-to-Site VPN | Validated IKE/IPSec SAs and successful commit/push |
| **Phase 3** | Configure Device Groups and Security/NAT policies | Centralized policy deployment to FW188/FW189 |
| **Phase 4** *(up next)* | Log Forwarding & SIEM Integration | Forward logs to Rsyslog/Splunk for enterprise visibility |

---

> 💡 *Each phase below includes configuration steps, verification commands, and screenshots demonstrating successful Panorama management operations.*
