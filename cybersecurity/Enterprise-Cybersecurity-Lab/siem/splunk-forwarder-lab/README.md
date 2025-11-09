# 🧠 Splunk Universal Forwarder Log Ingestion Lab  
*Windows → Splunk Indexer via Universal Forwarder*

![Splunk Badge](https://img.shields.io/badge/Splunk-Universal%20Forwarder-blue?logo=splunk&logoColor=white)
![Windows Badge](https://img.shields.io/badge/Windows%20Server-Domain%20Controller-blue?logo=windows)
![Category Badge](https://img.shields.io/badge/Lab%20Type-SIEM%20Integration-success)

---

## 🗂️ Splunk Universal Forwarder Lab Index

Welcome to the **Splunk Universal Forwarder Log Ingestion Lab** — part of the ECL SIEM visibility phase.  
This lab demonstrates Windows → Splunk Indexer integration for centralized event collection and monitoring.

---

| 🧩 Step | Description | 🔗 Link |
|:--|:--|:--|
| 1️⃣ Install the Splunk Universal Forwarder | Run the MSI installer and create admin credentials. | [View Section →](#1️⃣-install-the-splunk-universal-forwarder) |
| 2️⃣ Configure the Forwarder Outputs | Specify deployment server, indexer IP, and port `9997`. | [View Section →](#2️⃣-configure-the-forwarder-outputs) |
| 3️⃣ Verify the Forwarder Service | Confirm the SplunkForwarder service is running. | [View Section →](#3️⃣-verify-the-forwarder-service) |
| 4️⃣ Validate Connectivity | Test TCP port 9997 and confirm communication. | [View Section →](#4️⃣-validate-connectivity-to-indexer) |
| 5️⃣ Confirm Active Forwarder on Indexer | Verify active connections via CLI. | [View Section →](#5️⃣-confirm-active-forwarder-on-indexer) |
| 6️⃣ Review Logs in Splunk | Search for Windows event logs in Splunk Web. | [View Section →](#6️⃣-review-logs-in-splunk) |
| 7️⃣ Review Forwarder Log File | Validate successful forwarding in `splunkd.log`. | [View Section →](#7️⃣-log-file-verification) |
| ✅ Verification Summary | Final checks and validation table. | [View Section →](#-verification-summary) |
| 🧭 Lessons Learned | Key takeaways from this integration. | [View Section →](#-lessons-learned) |


---

## 🎯 **Objective**
Demonstrate how to install, configure, and verify the **Splunk Universal Forwarder** on a **Windows Server (Domain Controller)** to forward **Windows Event Logs** to a **Splunk Indexer** for centralized visibility.

---

## 🧩 **Topology Overview**

| Role | Hostname | IP Address | Description |
|------|-----------|-------------|--------------|
| 🖥️ Windows DC | `ecl-dc01` | `192.168.118.123` | Hosts Splunk Universal Forwarder |
| 📊 Splunk Indexer | `splunk` | `192.168.118.153` | Receives forwarded logs on port `9997` |

---

## ⚙️ **Lab Steps**

### 1️⃣ Install the Splunk Universal Forwarder
Run the MSI installer on the Domain Controller, accept the license, and create an admin user.

🖼 **Screenshot: Forwarder Installation Success**  
![Forwarder Install Success](screenshots/forwarder-install-success.png)

---

### 2️⃣ Configure the Forwarder Outputs
During setup, specify:
- **Deployment Server:** *(optional – leave blank)*
- **Receiving Indexer:** `192.168.118.153`
- **Port:** `9997`

🖼 **Screenshot: Forwarder Outputs Configuration**  
![Forwarder Outputs Config](screenshots/forwarder-outputs-conf.png)

---

### 3️⃣ Verify the Forwarder Service
After installation, confirm the service status:

```powershell
Get-Service splunkforwarder
