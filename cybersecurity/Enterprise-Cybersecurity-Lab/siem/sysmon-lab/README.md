
# 🛡️ Sysmon Visibility Lab  
**Enterprise Cybersecurity Lab – Phase 2: Security Visibility & Telemetry**

This lab implements **Windows Sysmon** to provide deep endpoint telemetry and forward all Sysmon logs to your **Rsyslog collector**, which then forwards logs to **Splunk**.

```
Windows → Sysmon → Rsyslog → Splunk
```

---

## 📘 Table of Contents
- Overview
- Lab Topology
- Objectives
- Requirements
- Sysmon Installation
- Sysmon Configuration XML
- Forwarding Sysmon Logs to Rsyslog
- Rsyslog → Splunk Configuration
- Splunk Verification Queries
- Screenshots
- Navigation

---

## 🔎 Overview
Sysmon enhances Windows logging by capturing:
- Process creation  
- Network connections  
- DNS queries (Event ID 22)  
- Registry modifications  
- File creation timestamps  
- WMI events  

This lab shows how to install Sysmon, apply a config file, forward Sysmon logs to Rsyslog, and confirm visibility in Splunk.

---

## 🖥️ Lab Topology

```
+---------------------------+
| Windows 10/11 / Server    |
|  Sysmon Installed         |
+-------------+-------------+
              |
              v
+---------------------------+
|         Rsyslog           |
| Ubuntu 22.04 Collector    |
+-------------+-------------+
              |
              v
+---------------------------+
|          Splunk           |
+---------------------------+
```

---

## 🎯 Objectives
- Install Sysmon  
- Apply Sysmon XML configuration  
- Forward Sysmon logs to Rsyslog  
- Forward from Rsyslog to Splunk  
- Validate data ingestion in Splunk  

---

## 📦 Requirements
- Windows 10/11 or Server 2019/2022  
- Sysmon + configuration XML  
- Rsyslog server (already built in Phase 2)  
- Splunk indexer (port 9997 open)  

---

## ⚙️ Sysmon Installation

### 1️⃣ Download Sysmon
```powershell
Invoke-WebRequest -Uri "https://live.sysinternals.com/Sysmon64.exe" -OutFile "C:\Tools\Sysmon64.exe"
```

### 2️⃣ Install with configuration
```powershell
sysmon64.exe -accepteula -i sysmon-config.xml
```

Verify:
```powershell
Get-WinEvent -LogName "Microsoft-Windows-Sysmon/Operational" -MaxEvents 10
```

---

## 📄 Sysmon Configuration XML (Basic)

Create a file named **sysmon-config.xml**:

```xml
<Sysmon schemaversion="4.82">
  <EventFiltering>
    <ProcessCreate onmatch="include" />
    <NetworkConnect onmatch="include" />
    <DnsQuery onmatch="include" />
    <FileCreateTime onmatch="include" />
    <ProcessAccess onmatch="include" />
  </EventFiltering>
</Sysmon>
```

---

## 📤 Forwarding Sysmon Logs to Rsyslog
Use **nxlog** on Windows for clean forwarding.

Example `nxlog.conf`:

```
<Input sysmon>
  Module im_msvistalog
  Query <QueryList><Query Id="0"><Select Path="Microsoft-Windows-Sysmon/Operational">*</Select></Query></QueryList>
</Input>

<Output out>
  Module om_udp
  Host 10.0.4.42
  Port 514
</Output>

<Route r1>
  Path sysmon => out
</Route>
```

Restart nxlog after saving.

---

## 🔁 Rsyslog → Splunk Configuration

Create file:
```
/etc/rsyslog.d/60-sysmon.conf
```

Add:

```
module(load="imudp")
input(type="imudp" port="514")

if $programname == "Sysmon" then {
    action(type="omfwd" target="192.168.118.153" port="9997" protocol="tcp")
    stop
}
```

Restart Rsyslog:

```bash
sudo systemctl restart rsyslog
```

---

## 📊 Splunk Verification Queries

### Process Creation
```
index=sysmon EventCode=1 | table _time Computer Image CommandLine
```

### Network Connections
```
index=sysmon EventCode=3 | table _time Computer SourceIp DestinationIp DestinationPort
```

### DNS Queries
```
index=sysmon EventCode=22 | table _time QueryName Image ProcessId
```

---

## 📸 Screenshots

Recommended screenshots:
- sysmon-installed.png  
- sysmon-events-eventviewer.png  
- nxlog-running.png  
- rsyslog-receiving.png  
- splunk-sysmon-events.png  

Store them under:

```
/sysmon-lab/screenshots/
```

---

## 🔗 Navigation
**↩️ Back to SIEM Folder**  
`../`

**↩️ Back to Portfolio Home**  
`../../README.md`

---

This completes the Sysmon → Rsyslog → Splunk lab module.
