# Wazuh SIEM Lab

## 1. Wazuh Agent Enrollment

Shows that the Linux host is enrolled and communicating.

![Active Agents](screenshots/wazuh-active-agents.png)

## 2. Agent Info

Displays agent metadata, IP, status, and last connection.

![Agent Info](screenshots/wazuh-agent-info.png)

## 3. Wazuh Manager Status

Validation that the manager services are active.

![Manager Status](screenshots/wazuh-manager-status.png)

## 4. Wazuh Logtest Validation

Demonstrates decoding and rule triggering using wazuh-logtest.

![Logtest](screenshots/wazuh-logtest.png)

## 5. Splunk Forwarded Events

Shows Wazuh alerts arriving successfully in Splunk.

![Splunk Events](screenshots/wazuh-splunk-events.png)

## 6. Architecture Diagram (Text-Based)

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

## Summary

This lab demonstrates full Wazuh agent enrollment, alert generation,
rule matching, and forwarding to Splunk for SOC investigation workflows.
