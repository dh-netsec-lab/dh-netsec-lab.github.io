
# Suricata IDS Lab – Enterprise Cybersecurity Lab (ECL)

This lab documents the setup, configuration, verification, and alert validation for **Suricata IDS** inside the Enterprise Cybersecurity Lab (ECL). These screenshots demonstrate proper installation, correct interface binding, packet visibility, and alert/log generation for SIEM ingestion.

---

## 1. Suricata Build Information  
This confirms version, architecture, and compiled feature support.

![Suricata Build Info](screenshots/suricata-build-info.png)

---

## 2. Suricata Configuration (YAML)

### HOME_NET Definition  
Ensures Suricata is monitoring your internal network ranges properly.

![Suricata HOME_NET](screenshots/suricata-yaml-homenet.png)

### Interface Assignment  
Validates Suricata is bound to the correct SPAN/data-plane interface (e.g., g1/3).

![Suricata Interface](screenshots/suricata-yaml-interface.png)

---

## 3. Live Traffic Verification (SPAN / Mirror)

Command executed:

```
sudo tcpdump -i g1/3 -nn
```

This verifies Suricata is receiving real-time mirrored network traffic.

![Suricata tcpdump](screenshots/suricata-tcpdump.png)

---

## 4. Suricata Alert Verification (fast.log)

Command executed:

```
sudo tail -f /var/log/suricata/fast.log
```

This confirms Suricata is actively detecting threats and anomalies.

![Suricata Fast Log](screenshots/suricata-fastlog.png)

---

## 5. EVE JSON Event Stream  
The primary structured JSON output for SIEM ingestion (Splunk, Wazuh, ELK).

Command executed:

```
sudo tail -f /var/log/suricata/eve.json
```

![Suricata EVE Events](screenshots/suricata-eve-events.png)

---

# Summary  
This lab verifies the full Suricata pipeline:

- Correct installation  
- Proper interface binding  
- Live packet visibility  
- Alert generation  
- EVE JSON SIEM-ready output  

Suricata is now fully operational within the Enterprise Cybersecurity Lab (Phase 2: Security Visibility & Telemetry).

