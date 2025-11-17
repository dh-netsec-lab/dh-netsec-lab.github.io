# 🛡️ Wazuh SIEM Integration Lab

**Enterprise Cybersecurity Lab --- Phase 2: Security Visibility &
Telemetry**

Wazuh provides host-based intrusion detection (HIDS), file integrity
monitoring (FIM), log collection, rootcheck scanning, and threat
detection.\
This lab demonstrates a full deployment of **Wazuh Manager + Wazuh
Agent**, with alerts successfully forwarded into **Splunk** for
centralized SIEM visibility.

------------------------------------------------------------------------

## 📌 **Lab Objectives**

-   Deploy Wazuh Manager on Linux\
-   Enroll and validate the Wazuh Agent\
-   Verify FIM, syscheck, and rootcheck telemetry\
-   Enable alert forwarding into Splunk\
-   Confirm events appear in Splunk under the `ossec` index\
-   Capture SOC-style validation evidence

------------------------------------------------------------------------

## 📡 **Architecture Overview**

    [Wazuh Agent] → [Wazuh Manager] → alerts.json → [Splunk Enterprise] → index=ossec

------------------------------------------------------------------------

## 📁 **File Structure**

    wazuh-lab/
    │
    ├── screenshots/
    │   ├── wazuh-active-agents.png
    │   ├── wazuh-agent-info.png
    │   ├── wazuh-agent-log.png
    │   ├── wazuh-agent-status.png
    │   ├── wazuh-manager-status.png
    │   └── wazuh-to-splunk-alerts.png
    │
    └── README.md

------------------------------------------------------------------------

## 🏗️ **1. Wazuh Agent Enrollment**

### ✔️ Active Agents

Shows that the Linux host is enrolled and communicating.

📸 *Screenshot:*\
screenshots/wazuh-active-agents.png

------------------------------------------------------------------------

### ✔️ Agent Info

Displays agent metadata, IP, status, and last connection.

📸 *Screenshot:*\
screenshots/wazuh-agent-info.png

------------------------------------------------------------------------

### ✔️ Agent Log Output

Confirms the agent has connected and sent initial telemetry.

📸 *Screenshot:*\
screenshots/wazuh-agent-log.png

------------------------------------------------------------------------

### ✔️ Agent Status

Shows running modules: syscollector, syscheck, logcollector,
wazuh-modulesd, etc.

📸 *Screenshot:*\
screenshots/wazuh-agent-status.png

------------------------------------------------------------------------

## 🛠️ **2. Wazuh Manager Verification**

Wazuh Manager is running with all core daemons active.

📸 *Screenshot:*\
screenshots/wazuh-manager-status.png

------------------------------------------------------------------------

## 🔄 **3. Splunk Integration (File Monitoring)**

Splunk monitors Wazuh's alert output file:

    /var/ossec/logs/alerts/alerts.json

Example inputs.conf:

    [monitor:///var/ossec/logs/alerts/alerts.json]
    index = ossec
    sourcetype = wazuh-alerts
    disabled = false

------------------------------------------------------------------------

## 📊 **4. Validation --- Wazuh Alerts in Splunk**

All alerts appear in Splunk under:

    index=ossec sourcetype=wazuh-alerts

📸 *Screenshot:*\
screenshots/wazuh-to-splunk-alerts.png

------------------------------------------------------------------------

## 🚀 **5. SOC Verification Workflow**

Example test: Invalid SSH Login Attempt

1.  Trigger:

        ssh invaliduser@localhost

2.  Wazuh detects rule 5710\

3.  Splunk receives alert with MITRE metadata

------------------------------------------------------------------------

## 🧭 Navigation

🔙 [Back to SIEM Labs](../)\
🔝 [Back to Portfolio Home](../../../)

------------------------------------------------------------------------

## ✅ Lab Status: **Completed**
