# 🔐 Cybersecurity Labs

This section focuses on **enterprise-grade security visibility, detection, and response** — integrating multiple vendors, operating systems, and SIEM solutions into one continuous learning platform.

---

## 🧩 Featured Project — Enterprise Cybersecurity Lab (ECL)

The **[Enterprise Cybersecurity Lab (ECL)](./Enterprise-Cybersecurity-Lab/)** is the flagship environment that demonstrates:
- Multi-vendor firewall integration (Fortinet + Palo Alto)
- Windows Server 2022 with AD, DNS, IIS, and CA services  
- Linux-based telemetry nodes (Rsyslog, Suricata, Zeek)  
- Splunk Enterprise SIEM visibility  
- Sysmon endpoint logging and event correlation  

ECL serves as a **realistic enterprise simulation** — evolving through defined phases that mirror how organizations mature their cybersecurity posture over time.

| Phase | Title | Focus | Status |
|:------|:------|:------|:------|
| ✅ **Phase 1** | Network Connectivity Verification | Routing, NAT, and firewall reachability | ✅ Complete |
| ✅ **Phase 2** | Security Visibility & Telemetry | Sysmon + Rsyslog + Splunk data pipeline | ✅ Complete |
| 🧩 **Phase 3** | Identity & Trust Integration | AD, DNS, Certificates, SSL Decryption | 📅 Planned |
| 🧠 **Phase 4** | Threat Detection & Response | SOC correlation and detections | 📅 Planned |
| 🧾 **Phase 5** | Automation & GRC Overlays | PowerShell, Ansible, risk controls | 🌐 Future |


![Progress](https://progress-bar.dev/40/?title=Phase+2+of+5+Completed)


> 📁 [View the ECL Lab Folder →](./Enterprise-Cybersecurity-Lab/)

---

## 🧠 Supporting Security Labs

Additional standalone cybersecurity projects will be organized here as independent modules that complement the ECL ecosystem.

| Lab | Description | Status | Link |
|:--|:--|:--|:--|
| 🪟 Splunk Universal Forwarder | Windows → Splunk Indexer log ingestion | ✅ Complete | [View Lab →](./Enterprise-Cybersecurity-Lab/siem/splunk-forwarder-lab/)
| 🧰 Sysmon Integration | Endpoint visibility with granular event collection | 🔄 In Progress | *(Coming Soon)* |
| 🧾 Rsyslog → Splunk | Linux log forwarding pipeline | 🔄 In Progress | *(Coming Soon)* |
| 🧱 SOC Detection & Correlation | Splunk searches for Event ID 4625, 4688, 4698 | 🧠 Planned | *(Coming Soon)* |
| 📋 GRC & Risk Register | Risk tracking, mitigation, and control mapping | 🚧 In Progress | *(Coming Soon)* |

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
- Add GRC documentation for Phases 1–2  
- Develop Splunk correlation dashboards  
- Implement SOC playbooks and incident response examples  

---

*Maintained by DH | [Back to Portfolio Home](../README.md)*  
