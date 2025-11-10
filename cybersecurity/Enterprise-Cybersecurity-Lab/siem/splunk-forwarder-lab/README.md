# 🧠 Splunk Universal Forwarder Log Ingestion Lab  
*Windows → Splunk Indexer via Universal Forwarder*

![Splunk Badge](https://img.shields.io/badge/Splunk-Universal%20Forwarder-blue?logo=splunk&logoColor=white)
![Windows Badge](https://img.shields.io/badge/Windows%20Server-Domain%20Controller-blue?logo=windows)
![Category Badge](https://img.shields.io/badge/Lab%20Type-SIEM%20Integration-success)

---

## 🗂️ Quick Navigation
- [Step 1: Install Splunk Universal Forwarder](#step1)
- [Step 2: Configure Forwarder Outputs](#step2)
- [Step 3: Verify Forwarder Service](#step3)
- [Step 4: Validate Connectivity to Indexer](#step4)
- [Step 5: Confirm Active Forwarder on Indexer](#step5)
- [Step 6: Review Logs in Splunk](#step6)
- [Step 7: Review Forwarder Log File](#step7)
- [Step 8: Verification Summary](#step8)

---

## 🎯 Objective
Demonstrate how to install, configure, and verify the **Splunk Universal Forwarder** on a  
**Windows Server (Domain Controller)** to forward **Windows Event Logs** to a **Splunk Indexer** for centralized visibility.

---

## 🧩 Topology Overview
| Role | Hostname | IP Address | Description |
|:--|:--|:--|:--|
| 🖥️ Windows DC | `ecl-dc01` | `192.168.118.123` | Splunk Universal Forwarder |
| 📊 Splunk Indexer | `splunk` | `192.168.118.153` | Receives forwarded logs on port `9997` |

---

<a name="step1"></a>
## Step 1: Install the Splunk Universal Forwarder
Run the MSI installer on the Domain Controller, accept the license, and create an admin user.

🖼 **Screenshot:** `forwarder-install-success.png`  
Shows successful completion of the Splunk Universal Forwarder installation.  
![Forwarder Install Success](screenshots/forwarder-install-success.png)

---

<a name="step2"></a>
## Step 2: Configure the Forwarder Outputs
During setup, specify:
- **Deployment Server:** *(optional – leave blank)*  
- **Receiving Indexer:** `192.168.118.153`  
- **Port:** `9997`

🖼 **Screenshot:** `forwarder-outputs-conf.png`  
Displays correct indexer IP and port configuration.  
![Forwarder Outputs Config](screenshots/forwarder-outputs-conf.png)

---

<a name="step3"></a>
## Step 3: Verify the Forwarder Service
After installation, confirm the SplunkForwarder service status:

```powershell
Get-Service splunkforwarder
```

🖼 **Screenshot:** `forwarder-service-running.png`  
Service successfully running after installation.  
![Forwarder Service Running](screenshots/forwarder-service-running.png)

🖼 **Screenshot:** `forwarder-service-stopped.png`  
Service shown in stopped state for testing before restart.  
![Forwarder Service Stopped](screenshots/forwarder-service-stopped.png)

---

<a name="step4"></a>
## Step 4: Validate Connectivity to Indexer
Verify that TCP port `9997` is reachable from the Domain Controller to the Splunk Indexer:

```powershell
Test-NetConnection 192.168.118.153 -Port 9997
```

🖼 **Screenshot:** `forwarder-test-netconnection-9997.png`  
Connectivity confirmed between forwarder and indexer on port 9997.  
![Forwarder Test NetConnection 9997](screenshots/forwarder-test-netconnection-9997.png)

---

<a name="step5"></a>
## Step 5: Confirm Active Forwarder on Indexer
On the Splunk Indexer, list forwarders:

```bash
sudo /opt/splunk/bin/splunk list forward-server
```

🖼 **Screenshot:** `indexer-active-forwarders.png`  
Indexer shows an active forwarder connection from the Windows DC.  
![Indexer Active Forwarders](screenshots/indexer-active-forwarders.png)

🖼 **Screenshot:** `indexer-port-9997-listening.png`  
Validates that the indexer is listening for forwarder traffic on port 9997.  
![Indexer Port 9997 Listening](screenshots/indexer-port-9997-listening.png)

---

<a name="step6"></a>
## Step 6: Review Logs in Splunk
In Splunk Web, search for the Windows DC host to verify event ingestion:

```spl
index=main host=ecl-dc01
```

🖼 **Screenshot:** `splunk-search-results.png`  
Displays Windows event logs from `ecl-dc01` successfully indexed in Splunk.  
![Splunk Search Results](screenshots/splunk-search-results.png)

---

<a name="step7"></a>
## Step 7: Review Forwarder Log File
Examine the forwarder’s internal log to validate forwarding activity:

```powershell
Get-Content "C:\Program Files\SplunkUniversalForwarder\var\log\splunk\splunkd.log" -Tail 40 | findstr 9997
```

🖼 **Screenshot:** `forwarder-connection-log.png`  
Shows successful connections to the indexer from the forwarder.  
![Forwarder Connection Log](screenshots/forwarder-connection-log.png)

---

<a name="step8"></a>
## ✅ Verification Summary
| Check | Status | Result |
|:--|:--|:--|
| Forwarder Installed | ✅ | Service operational on Windows DC |
| Port 9997 Reachable | ✅ | Connectivity verified via `Test-NetConnection` |
| Forwarder Active on Indexer | ✅ | Confirmed under `list forward-server` |
| Logs Visible in Splunk | ✅ | Windows events indexed successfully |

---

## 🧭 Lessons Learned
- Splunk Universal Forwarder is lightweight yet essential for Windows event visibility.  
- Verifying connectivity (`9997`) and service status resolves most forwarding issues.  
- Always cross-check in Splunk Web and `splunkd.log` for confirmation.  

---

*Maintained by DH | [Back to Cybersecurity Index](../README.md)*
