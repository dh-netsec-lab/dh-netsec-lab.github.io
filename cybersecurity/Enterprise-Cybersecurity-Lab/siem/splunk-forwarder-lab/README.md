# 🧠 Splunk Universal Forwarder Log Ingestion Lab  
*Windows → Splunk Indexer via Universal Forwarder*

![Splunk Badge](https://img.shields.io/badge/Splunk-Universal%20Forwarder-blue?logo=splunk&logoColor=white)
![Windows Badge](https://img.shields.io/badge/Windows%20Server-Domain%20Controller-blue?logo=windows)
![Category Badge](https://img.shields.io/badge/Lab%20Type-SIEM%20Integration-success)

---

## 📚 **Table of Contents**
- [🎯 Objective](#-objective)
- [🧩 Topology Overview](#-topology-overview)
- [⚙️ Lab Steps](#️-lab-steps)
  - [1️⃣ Install the Splunk Universal Forwarder](#1️⃣-install-the-splunk-universal-forwarder)
  - [2️⃣ Configure the Forwarder Outputs](#2️⃣-configure-the-forwarder-outputs)
  - [3️⃣ Verify the Forwarder Service](#3️⃣-verify-the-forwarder-service)
  - [4️⃣ Validate Connectivity to Indexer](#4️⃣-validate-connectivity-to-indexer)
  - [5️⃣ Confirm Active Forwarder on Indexer](#5️⃣-confirm-active-forwarder-on-indexer)
  - [6️⃣ Review Logs in Splunk](#6️⃣-review-logs-in-splunk)
  - [7️⃣ Log File Verification](#7️⃣-log-file-verification)
- [🧾 Verification Summary](#-verification-summary)
- [🧭 Lessons Learned](#-lessons-learned)
- [🔗 Return Links](#-return-links)

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
