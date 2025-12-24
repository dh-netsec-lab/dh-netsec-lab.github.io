# SOC-101 — Module 2
## PowerShell Execution Visibility (Sysmon Event ID 1)

---

## 🎯 Objective
This module demonstrates how a SOC analyst identifies and triages
PowerShell execution using Sysmon Event ID 1 (Process Create) and Splunk.

The focus is on visibility, context, and analyst decision-making rather
than immediate attribution of malicious intent.

---

## 🧠 Why This Matters
PowerShell is:
- Widely used by administrators and enterprise services
- Frequently abused by attackers
- Common in both benign and malicious workflows

SOC analysts must determine:
- Who executed PowerShell
- How it was executed
- Whether the activity is expected or suspicious

---

## 🧪 Lab Scenario
A Windows endpoint generates PowerShell process execution events that are:
- Logged locally by Sysmon
- Forwarded to Splunk
- Investigated by a SOC analyst

Some PowerShell executions originate from legitimate services, reinforcing
the importance of contextual analysis during triage.

---

## 🖥️ Environment
- Endpoint: ECL-JUMPBOX-01
- Operating System: Windows Server 2022
- Telemetry Source: Sysmon
- SIEM: Splunk
- Event Type: Sysmon Event ID 1 (Process Create)

---

## 🔍 Step 1 — Validate Endpoint Telemetry (Sysmon)
The analyst first confirms that Sysmon is recording PowerShell execution
locally on the endpoint.

What is validated:
- Sysmon Event ID 1 is present
- Process creation events are logged
- PowerShell execution is captured with command-line details

📸 Evidence:
screenshots/01-sysmon-eventcode1-powershell-execution.png

---

## 🔎 Step 2 — PowerShell Visibility in Splunk
Next, the analyst verifies that PowerShell execution events are successfully
ingested into Splunk.

What is validated:
- Sysmon Operational logs are searchable
- PowerShell-related events are visible
- Host attribution is correct

📸 Evidence:
screenshots/02-splunk-powershell-visibility.png

---

## 🧠 Step 3 — Analyst Command-Line Review
The analyst reviews command-line arguments and execution context to
determine whether the activity is expected.

What is analyzed:
- Executing user
- Command-line arguments
- Service vs interactive execution
- Parent process context

In this lab, PowerShell executions initiated by the Splunk Universal
Forwarder service are identified and classified as legitimate operational
activity.

📸 Evidence:
screenshots/03-splunk-powershell-commandline-analysis.png

---

## 📌 Key Analyst Takeaways
- PowerShell execution alone is not inherently malicious
- Context determines severity
- Service-initiated PowerShell is common in enterprise environments
- Command-line visibility is critical for effective triage

---

## 🧩 MITRE ATT&CK Mapping
- T1059.001 — Command and Scripting Interpreter: PowerShell

---

## ✅ Conclusion
This module demonstrates how SOC analysts:
- Establish baseline PowerShell visibility
- Validate endpoint telemetry ingestion
- Perform command-line–level triage
- Distinguish benign activity from potentially suspicious behavior

These skills form a foundational detection capability for identifying
more advanced PowerShell-based attacks in later SOC modules.

---

## 📂 Directory Structure
module_2-powershell-execution-visibility/
├─ README.md
├─ index.md
└─ screenshots/
   ├─ 01-sysmon-eventcode1-powershell-execution.png
   ├─ 02-splunk-powershell-visibility.png
   └─ 03-splunk-powershell-commandline-analysis.png

---

➡️ Next Module:
SOC-101 — Module 3: Encoded and Obfuscated PowerShell (planned)

