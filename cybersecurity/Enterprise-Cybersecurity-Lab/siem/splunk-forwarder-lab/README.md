# 🧠 Splunk Universal Forwarder Log Ingestion Lab  
*Windows → Splunk Indexer via Universal Forwarder*

![Splunk Badge](https://img.shields.io/badge/Splunk-Universal%20Forwarder-blue?logo=splunk&logoColor=white)
![Windows Badge](https://img.shields.io/badge/Windows%20Server-Domain%20Controller-blue?logo=windows)
![Category Badge](https://img.shields.io/badge/Lab%20Type-SIEM%20Integration-success)

---

## 🗂️ Lab Index

| Step | Description | Link |
|:--|:--|:--|
| 1️⃣ | Install the Splunk Universal Forwarder | [View Section →](#1️⃣-install-the-splunk-universal-forwarder) |
| 2️⃣ | Configure the Forwarder Outputs | [View Section →](#2️⃣-configure-the-forwarder-outputs) |
| 3️⃣ | Verify the Forwarder Service | [View Section →](#3️⃣-verify-the-forwarder-service) |
| 4️⃣ | Validate Connectivity to Indexer | [View Section →](#4️⃣-validate-connectivity-to-indexer) |
| 5️⃣ | Confirm Active Forwarder on Indexer | [View Section →](#5️⃣-confirm-active-forwarder-on-indexer) |
| 6️⃣ | Review Logs in Splunk Web | [View Section →](#6️⃣-review-logs-in-splunk-web) |
| 7️⃣ | Review Forwarder Log File | [View Section →](#7️⃣-review-forwarder-log-file) |
| ✅ | Verification Summary | [View Section →](#✅-verification-summary) |
| 🧭 | Lessons Learned | [View Section →](#🧭-lessons-learned) |

> 💡 *Click any link above to jump directly to that section.*

---

## 🎯 Objectives  
This lab demonstrates how to configure and verify a **Windows Server Domain Controller** to forward **Windows Security Events** to a Splunk Indexer using the **Splunk Universal Forwarder**.

---

## 🧩 Topology Overview  

| Role | Hostname | IP Address | Description |
|------|-----------|-------------|--------------|
| 🖥️ Windows DC | `ecl-dc01` | `192.168.118.123` | Splunk Universal Forwarder |
| 📊 Splunk Indexer | `splunk` | `192.168.118.153` | Receives forwarded logs on port `9997` |

---

## 1️⃣ Install the Splunk Universal Forwarder  

Run the MSI installer on the Domain Controller, accept the license, and configure admin credentials.  

🖼 **Screenshot:** `forwarder-install-success.png`  
![Forwarder Install Success](screenshots/forwarder-install-success.png)

---

## 2️⃣ Configure the Forwarder Outputs  

During setup, specify:  
- **Deployment Server:** *(optional – leave blank)*  
- **Receiving Indexer:** `192.168.118.153`  
- **Port:** `9997`  

🖼 **Screenshot:** `forwarder-outputs-conf.png`  
![Forwarder Outputs Config](screenshots/forwarder-outputs-conf.png)

---

## 3️⃣ Verify the Forwarder Service  

After installation, confirm the service status:  

```powershell
Get-Service splunkforwarder
