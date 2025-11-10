# 🧠 Splunk Universal Forwarder Log Ingestion Lab  
*Windows → Splunk Indexer via Universal Forwarder*

![Splunk Badge](https://img.shields.io/badge/Splunk-Universal%20Forwarder-blue?logo=splunk&logoColor=white)
![Windows Badge](https://img.shields.io/badge/Windows%20Server-Domain%20Controller-blue?logo=windows)
![Category Badge](https://img.shields.io/badge/Lab%20Type-SIEM%20Integration-success)

---

## 🗂️ Lab Index

| Step | Description | Link |
|:--|:--|:--|
| 1️⃣ | Install the Splunk Universal Forwarder | [View Section →](#step1) |
| 2️⃣ | Configure the Forwarder Outputs | [View Section →](#step2) |
| 3️⃣ | Verify the Forwarder Service | [View Section →](#step3) |
| 4️⃣ | Validate Connectivity to Indexer | [View Section →](#step4) |
| 5️⃣ | Confirm Active Forwarder on Indexer | [View Section →](#step5) |
| 6️⃣ | Review Logs in Splunk Web | [View Section →](#step6) |
| 7️⃣ | Review Forwarder Log File | [View Section →](#step7) |
| ✅ | Verification Summary | [View Section →](#verification) |
| 🧭 | Lessons Learned | [View Section →](#lessons) |

---

## 🎯 Objectives  
Demonstrate how to install, configure, and verify a **Windows Server Domain Controller** forwarding **Windows Event Logs** to a **Splunk Indexer** using the **Splunk Universal Forwarder**.

---

## 🧩 Topology Overview  

| Role | Hostname | IP Address | Description |
|------|-----------|-------------|--------------|
| 🖥️ Windows DC | `ecl-dc01` | `192.168.118.123` | Splunk Universal Forwarder |
| 📊 Splunk Indexer | `splunk` | `192.168.118.153` | Receives forwarded logs on port `9997` |

---

## Step 1: Install the Splunk Universal Forwarder  
<a name="step1"></a>

Run the MSI installer on the Domain Controller, accept the license, and configure admin credentials.

🖼 **Screenshot:**   
![Forwarder Install Success](screenshots/forwarder-install-success.png)

---

## Step 2: Configure the Forwarder Outputs  
<a name="step2"></a>

During setup, specify:  
- **Deployment Server:** *(optional – leave blank)*  
- **Receiving Indexer:** `192.168.118.153`  
- **Port:** `9997`

🖼 **Screenshot:** `forwarder-outputs-conf.png`  
![Forwarder Outputs Config](screenshots/forwarder-outputs-conf.png)

---

## Step 3: Verify the Forwarder Service  
<a name="step3"></a>

After installation, confirm the SplunkForwarder service status:

```powershell
Get-Service splunkforwarder
```

🖼 **Screenshot:** `forwarder-service-running.png`  
![Forwarder Service Running](screenshots/forwarder-service-running.png)

🖼 **Screenshot:** `forwarder-service-stopped.png`  
![Forwarder Service Stopped](screenshots/forwarder-service-stopped.png)

---

## Step 4: Validate Connectivity to Indexer  
<a name="step4"></a>

Verify that TCP port 9997 is reachable from the Domain Controller to the Splunk Indexer:

```powershell
Test-NetConnection 192.168.118.153 -Port 9997
```

🖼 **Screenshot:** `forwarder-test-netconnection-9997.png`  
![Forwarder Test-NetConnection 9997](screenshots/forwarder-test-netconnection-9997.png)

---

## Step 5: Confirm Active Forwarder on Indexer  
<a name="step5"></a>

Check the Indexer to confirm active forwarder registration:

```bash
sudo /opt/splunk/bin/splunk list forward-server
sudo netstat -tulnp | grep 9997
```

🖼 **Screenshot:** `indexer-active-forwarders.png`  
![Indexer Active Forwarders](screenshots/indexer-active-forwarders.png)

🖼 **Screenshot:** `indexer-port-9997-listening.png`  
![Indexer Port 9997 Listening](screenshots/indexer-port-9997-listening.png)

---

## Step 6: Review Logs in Splunk Web  
<a name="step6"></a>

Use Splunk Web to verify that logs are arriving from the Domain Controller:

```bash
index=win_events host=ecl-dc01
```

🖼 **Screenshot:** `splunk-search-results.png`  
![Splunk Search Results](screenshots/splunk-search-results.png)

---

## Step 7: Review Forwarder Log File  
<a name="step7"></a>

Inspect the Forwarder’s internal log to ensure forwarding to 192.168.118.153:9997 is confirmed:

```powershell
Get-Content "C:\Program Files\SplunkUniversalForwarder\var\log\splunk\splunkd.log" -Tail 50 | findstr 9997
```

🖼 **Screenshot:** `forwarder-connection-log.png`  
![Forwarder Connection Log](screenshots/forwarder-connection-log.png)

---

## ✅ Verification Summary  
<a name="verification"></a>

| Check | Expected | Result |
|:--|:--|:--|
| Forwarder Service | Running | ✅ |
| Port 9997 | Open & reachable | ✅ |
| Active Forwarder | Listed on Indexer | ✅ |
| Events in Splunk | Visible under `index=win_events` | ✅ |
| Forwarder Logs | `splunkd.log` shows connection success | ✅ |

---

## 🧭 Lessons Learned  
<a name="lessons"></a>

- A clean reinstall can resolve broken forwarder connections.  
- Always verify port 9997 reachability before Splunk troubleshooting.  
- Review `splunkd.log` to confirm data transmission state.  
- Visual confirmation in Splunk Web closes the verification loop.

---

*Return to:* [Cybersecurity Labs](../../README.md) • [Enterprise Cybersecurity Lab](../README.md)
