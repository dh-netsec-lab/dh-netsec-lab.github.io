# 🛡️ Wazuh Lab – Host Intrusion Detection & Alert Forwarding to Splunk

This lab demonstrates how Wazuh Manager and a Wazuh Agent were deployed inside the Enterprise Cybersecurity Lab (ECL) to forward security alerts into **Splunk Enterprise**, completing the SIEM ingestion pipeline.

---

## 🧩 Architecture Overview

Wazuh Agent → Wazuh Manager → alerts.json → Splunk Enterprise (index=ossec)

---

## 📁 File Structure

wazuh-lab/
├── screenshots/
│   ├── wazuh-active-agents.png
│   ├── wazuh-agent-info.png
│   ├── wazuh-agent-log.png
│   ├── wazuh-agent-status.png
│   ├── wazuh-manager-status.png
│   ├── wazuh-to-splunk-alerts.png
└── README.md

---

# ✅ Verification Steps & Screenshots

## ✔️ 1. Active Agents
![Active Agents](screenshots/wazuh-active-agents.png)

## ✔️ 2. Agent Info
![Agent Info](screenshots/wazuh-agent-info.png)

## ✔️ 3. Agent Log Output
![Agent Log Output](screenshots/wazuh-agent-log.png)

## ✔️ 4. Agent Status
![Agent Status](screenshots/wazuh-agent-status.png)

## ✔️ 5. Wazuh Manager Status
![Wazuh Manager Status](screenshots/wazuh-manager-status.png)

## ✔️ 6. Wazuh → Splunk Alert Forwarding (Success)
![Wazuh to Splunk Alerts](screenshots/wazuh-to-splunk-alerts.png)

---

# 🎉 Lab Complete

You now have a working Host-IDS → SIEM pipeline.
