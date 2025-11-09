# 🧠 Splunk Universal Forwarder Log Ingestion Lab  
*Windows → Splunk Indexer via Universal Forwarder*

![Splunk Badge](https://img.shields.io/badge/Splunk-Universal%20Forwarder-blue?logo=splunk&logoColor=white)
![Windows Badge](https://img.shields.io/badge/Windows%20Server-Domain%20Controller-blue?logo=windows)
![Category Badge](https://img.shields.io/badge/Lab%20Type-SIEM%20Integration-success)

---

## 🎯 **Objective**
Demonstrate how to install, configure, and verify the **Splunk Universal Forwarder** on a **Windows Server (Domain Controller)** to forward Windows Event Logs to a **Splunk Indexer** for centralized visibility.

---

## 🧩 **Topology Overview**

| Role | Hostname | IP Address | Description |
|------|-----------|-------------|--------------|
| 🖥️ Windows DC | `ecl-dc01` | `192.168.118.123` | Hosts Splunk Universal Forwarder |
| 📊 Splunk Indexer | `splunk` | `192.168.118.153` | Receives forwarded logs on port `9997` |

---

## ⚙️ **Lab Steps**

### 1️⃣ Install the Splunk Universal Forwarder
- Run the MSI installer on your Windows DC.  
- Accept the license agreement.  
- Set admin credentials (`Username: usmdb18`).  

🖼 **Screenshot: Forwarder Installation Success**  
![Forwarder Install Success](screenshots/forwarder-install-success.png)

---

### 2️⃣ Configure the Forwarder Outputs
During setup:
- Leave the **Deployment Server** field blank (optional).  
- Enter **Receiving Indexer:** `192.168.118.153`  
- Use **Port:** `9997`  

🖼 **Screenshot: Forwarder Outputs Configuration**  
![Forwarder Outputs Config](screenshots/forwarder-outputs-conf.png)

---

### 3️⃣ Verify the SplunkForwarder Service
Check the forwarder service on Windows:

```powershell
Get-Service splunkforwarder

