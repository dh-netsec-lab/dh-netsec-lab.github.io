# SOC-102 Module 2 — Network Reconnaissance & Scanning Detection (Internal)

## 🎯 Objective
Detect **internal reconnaissance and scanning behavior** by identifying deviations from an established East/West network baseline.

This module builds directly on **SOC-102 Module 1**, shifting from *what is normal* to *how abnormal reconnaissance manifests on the network*.

---

## 🧠 Detection Engineering Focus
Rather than centering on specific tools, this module focuses on **behavioral patterns** that indicate reconnaissance activity, including:

- One-to-many communication from a single internal host
- Bursty, short-lived connections
- Port spread across a single destination or multiple hosts
- Increased connection volume compared to baseline

The goal is to identify **early-stage lateral reconnaissance**, a common post-compromise activity.

---

## 🧩 Reconnaissance vs Baseline (Conceptual Shift)

From Module 1, we established that normal internal traffic:
- Is relatively stable
- Involves predictable host relationships
- Shows consistent request / response behavior

In this module, reconnaissance is identified when a host:
- Rapidly contacts **many internal IPs**
- Attempts **multiple ports** per host
- Generates **incomplete TCP handshakes**
- Exhibits traffic patterns inconsistent with baseline norms

---

## 🛠️ Telemetry Sources Used

Primary:
- **Zeek** — Behavioral network telemetry (conn.log)
- **Splunk** — Aggregation and deviation analysis

Secondary:
- **Suricata** — Flow metadata and scan confirmation

Validation:
- **tcpdump** — Packet-level confirmation (minimal use)

All telemetry is derived from **internal (East/West) traffic only**.

---

## 🔍 Observed Reconnaissance Behaviors

### 1️⃣ Zeek — Port Spread Across Internal Hosts
Zeek connection logs reveal a single internal host initiating repeated short-lived TCP connections to **multiple destination ports** across internal systems.

This behavior deviates from the stable, predictable communication patterns established in Module 1 and is indicative of **internal service enumeration** rather than normal application traffic.

Key indicators include:
- High number of unique destination ports
- Minimal connection duration
- Lack of full session establishment

📸 *Screenshot:* Zeek `conn.log` highlighting internal port spread

---

### 2️⃣ Suricata — SYN-Only Flow States
Suricata flow metadata confirms reconnaissance behavior by identifying:
- TCP SYN packets without completed handshakes
- Elevated connection attempts without data exchange
- Repeated timeout-based flows

Suricata serves as **confirmatory telemetry**, reinforcing the behavioral signal observed in Zeek rather than acting as the primary detection source.

📸 *Screenshot:* Suricata `eve.json` showing SYN-only flows

---

### 3️⃣ tcpdump — Packet-Level Validation
A targeted tcpdump capture validates reconnaissance behavior at the packet level, confirming:
- Repeated TCP SYN packets
- Multiple destination ports contacted in rapid succession
- Lack of sustained bidirectional communication

This capture is used strictly for **ground-truth validation**, not as a primary detection mechanism.

📸 *Screenshot:* tcpdump capture showing internal reconnaissance traffic

---

## 🧠 Detection Opportunities

Based on observed behavior, potential detection logic includes:

- Thresholds on **unique internal destinations** per source
- Thresholds on **unique destination ports**
- Ratios of SYN packets to established sessions
- Temporal clustering of connection attempts
- Deviation from historical baseline patterns

These detections are **behavior-driven**, not signature-dependent.

---

## 🚫 Why This Is Not an Alert-Only Module
This module intentionally avoids:
- Static IDS alerts
- Tool-specific signatures
- Command-based detections

Detection engineering emphasizes **repeatable logic** that remains effective even as attacker tooling changes.

---

## 🔗 Relationship to Future Modules
This reconnaissance detection directly enables future SOC-102 scenarios, including:
- Beaconing and periodic communication detection
- Multi-host correlation
- Early-stage lateral movement analysis

Reconnaissance is often the **earliest detectable signal** after initial access.

---

## 📁 Artifacts
```
screenshots/
├── zeek-connlog-host-sweep.png
├── zeek-connlog-port-spread.png
├── suricata-syn-flows.png
└── tcpdump-internal-recon.png
```

---

## 🏁 Module Outcome
By completing this module, you have:
- Identified internal reconnaissance behaviors
- Distinguished scanning activity from baseline traffic
- Correlated multiple telemetry sources
- Designed detection logic grounded in behavior, not tools

This module represents a transition from **SOC monitoring** to **detection engineering thinking**.

---

← **[Back to Detection Engineering](../)**  
→ **[Next: Beaconing & Periodic Communication Detection](../module_3-beaconing/)**

