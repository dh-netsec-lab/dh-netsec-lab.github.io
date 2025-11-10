# 🧠 Splunk Universal Forwarder Log Ingestion Lab
*Windows → Splunk Indexer via Universal Forwarder*

![Splunk Badge](https://img.shields.io/badge/Splunk-Universal%20Forwarder-blue?logo=splunk&logoColor=white)
![Windows Badge](https://img.shields.io/badge/Windows%20Server-Domain%20Controller-blue?logo=windows)
![Category Badge](https://img.shields.io/badge/Lab%20Type-SIEM%20Integration-success)

---

## 🗂️ Lab Index

| Step | Description | Link |
|:--|:--|:--|
| 1 | Install the Splunk Universal Forwarder | [View →](#step1) |
| 2 | Configure the Forwarder Outputs | [View →](#step2) |
| 3 | Verify the Forwarder Service | [View →](#step3) |
| 4 | Validate Connectivity to Indexer | [View →](#step4) |
| 5 | Confirm Active Forwarder on Indexer | [View →](#step5) |
| 6 | Review Logs in Splunk Web | [View →](#step6) |
| 7 | Review Forwarder Log File | [View →](#step7) |
| ✅ | Verification Summary | [View →](#verification) |
| 🧭 | Lessons Learned | [View →](#lessons) |

---

## 🎯 Objective
Install, configure, and verify the **Splunk Universal Forwarder** on a **Windows Server (Domain Controller)** to forward **Windows Event Logs** to a **Splunk Indexer**.

---

## 🧩 Topology Overview

| Role | Hostname | IP | Description |
|------|-----------|----|-------------|
| 🖥️ DC | `ecl-dc01` | `192.168.118.123` | Universal Forwarder |
| 📊 Indexer | `splunk` | `192.168.118.153` | Receives logs on `9997` |

---

<a id="step1"></a>
## Step 1 — Install the Splunk Universal Forwarder
Run the MSI installer on the Domain Controller, accept the license, and create an admin user.

🖼 **Screenshot — Forwarder Installation Success**  
![forwarder-install-success](screenshots/forwarder-install-success.png)

---

<a id="step2"></a>
## Step 2 — Configure the Forwarder Outputs
During setup, specify:  
- **Deployment Server:** *(optional)*  
- **Receiving Indexer:** `192.168.118.153`  
- **Port:** `9997`

🖼 **Screenshot — Forwarder Outputs Configuration**  
![forwarder-outputs-conf](screenshots/forwarder-outputs-conf.png)

---

<a id="step3"></a>
## Step 3 — Verify the Forwarder Service
After installation, confirm the service status:

```powershell
Get-Service splunkforwarder
