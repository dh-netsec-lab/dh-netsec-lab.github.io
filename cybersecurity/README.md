# 🔐 Cybersecurity Labs

This section focuses on **enterprise-grade security visibility, detection, and response** — integrating multiple vendors, operating systems, and SIEM solutions into one continuous learning platform.

---

## 🧩 Featured Project — Enterprise Cybersecurity Lab (ECL)

The **[Enterprise Cybersecurity Lab (ECL)](./ecl/)** is the flagship environment that demonstrates:
- Multi-vendor firewall integration (Fortinet + Palo Alto)
- Windows Server 2022 with AD, DNS, IIS, and CA services  
- Linux-based telemetry nodes (Rsyslog, Suricata, Zeek)  
- Splunk Enterprise SIEM visibility  
- Sysmon endpoint logging and event correlation  

ECL serves as a **realistic enterprise simulation** — evolving through defined phases that mirror how organizations mature their cybersecurity posture over time.

| Phase | Title | Focus | Status |
|:------|:------|:------|:------|
| ✅ **Phase 1** | Network Connectivity Verification | Routing, NAT, and firewall reachability | ✅ Complete |
| 🔄 **Phase 2** | Security Visibility & Telemetry | Sysmon + Rsyslog + Splunk data pipeline | ⚙️ In Progress |
| ⏳ **Phase 3** | Identity & Trust Integration | AD, DNS, Certificates, SSL Decryption | 📅 Planned |
| ⏳ **Phase 4** | Threat Detection & Response | SOC correlation and detections | 📅 Planned |
| ⏳ **Phase 5** | Automation & GRC Overlays | PowerShell, Ansible, risk controls | 🌐 Future |

> 📁 [View the ECL Lab Folder →](./ecl/)

---

## 🧠 Supporting Security Labs (Planned)

Additional standalone cybersecurity projects will be organized here as independent modules complementing the ECL ecosystem.

| Lab | Description | Status |
|:--|:--|:--|
| SOC Detection & Correlation | Custom correlation searches in Splunk (e.g., Event ID 4688, 4625) | ⏳ Planned |
| Log Ingestion Pipeline | Syslog, Winlogbeat, Rsyslog architecture comparison | ⏳ Planned |
| MITRE ATT&CK Integration | Mapping detections and TTP visibility | ⏳ Planned |
| GRC & Risk Register | Risk tracking and control alignment (linked to ECL phases) | 🚧 In Progress |

---

## 🧭 Learning Focus

These labs emphasize:
- End-to-end telemetry and log flow
- SIEM-based threat detection
- Secure Windows/Linux integration
- Data correlation and response strategies
- Continuous improvement through GRC alignment

---

## 📈 Road Ahead

- Expand Phase 2 telemetry with Sysmon and Rsyslog
- Add GRC documentation for Phase 1–2  
- Begin Splunk correlation dashboard design  
- Develop SOC detection & incident response use cases  

---

*Maintained by DH | [Back to Portfolio Home](../README.md)*  

