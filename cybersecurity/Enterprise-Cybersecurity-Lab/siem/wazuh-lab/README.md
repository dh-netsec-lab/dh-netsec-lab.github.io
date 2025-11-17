# Wazuh SIEM Lab

This lab demonstrates how Wazuh provides endpoint visibility, alerting,
and log-forwarding into Splunk as part of the Enterprise Cybersecurity Lab (ECL).
The screenshots below verify correct agent enrollment, event decoding,
manager health, and successful Splunk integration.

---

## 1. Wazuh Agent Enrollment  
Shows that the Linux host is enrolled and communicating.

![Active Agents](screenshots/wazuh-active-agents.png)

---

## 2. Agent Info  
Displays agent metadata, IP, status, and last connection.

![Agent Info](screenshots/wazuh-agent-info.png)

---

## 3. Wazuh Manager Status  
Validation that the manager services are active.

![Manager Status](screenshots/wazuh-manager-status.png)

---

## 4. Wazuh Logtest Validation

Demonstrates decoding and rule triggering using wazuh-logtest.

![Logtest](screenshots/wazuh-agent-log.png)

## 5. Splunk Forwarded Events

Shows Wazuh alerts arriving successfully in Splunk.

![Splunk Events](screenshots/wazuh-to-splunk-alerts.png)

---

## 6. Architecture Diagram (Text-Based)

```
        [Linux Hosts / Endpoints]
                 |
            Wazuh Agent
                 |
        --------------------
        |   Wazuh Manager  |
        --------------------
                 |
        Forwarded Alerts
                 |
               Splunk
```

---

## Summary  
This lab verifies end-to-end Wazuh operation:  
✔ Agent enrollment  
✔ Rule matching & alert generation  
✔ Wazuh Manager health  
✔ Successful log forwarding into Splunk  

These components form the foundation of SOC-style detection and analysis within your ECL.
