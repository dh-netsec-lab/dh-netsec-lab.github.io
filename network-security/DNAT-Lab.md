# Palo Alto DNAT Lab

# 🔥 Palo Alto DNAT Lab — Publish an Internal Web Server

![Lab Verified](https://img.shields.io/badge/Status-Working-brightgreen?style=for-the-badge)
![Firewall](https://img.shields.io/badge/Platform-Palo%20Alto%20Networks-blue?style=for-the-badge)

---

## 🧠 Objective
Configure **Destination NAT (DNAT)** on a Palo Alto Firewall to allow external (WAN) users to reach an internal web server in the **DMZ zone** via the firewall’s public IP.

---

## 🧩 Topology
| Device | Interface | IP Address | Zone | Role |
|--------|------------|-------------|------|------|
| **Internet Router** | G0/0 | 172.16.1.1/24 | — | Default Gateway for WAN |
| **Firewall WAN** | ethernet1/7 | 172.16.1.2/24 | UnTrust | Public-facing interface |
| **Firewall DMZ** | ethernet1/3 | 10.3.0.254/24 | DMZ | Internal server gateway |
| **Web Server** | eth0 | 10.3.0.1/24 | DMZ | Hosted HTTP site |
| **WAN Test PC** | eth0 | 172.16.1.10/24 | — | Used for external testing |

---

## ⚙️ Configuration Steps

### 1️⃣ Address Objects
| Name | Type | IP/Mask | Description |
|------|------|----------|--------------|
| `WAN_Public_IP` | IP Netmask | 172.16.1.2/32 | Firewall’s public IP |
| `DMZ_Web_10.3.0.1` | IP Netmask | 10.3.0.1/32 | Internal web server |

```bash
# CLI Example
set address WAN_Public_IP ip-netmask 172.16.1.2/32
set address DMZ_Web_Srv_1 ip-netmask 10.3.0.1/32

| Field                      | Value                     |
| -------------------------- | ------------------------- |
| **Name**                   | DNAT_SIP              |
| **From Zone**              | UnTrust                   |
| **To Zone (post-NAT)**     | UnTrust                       |
| **Destination Address**    | WAN_Public_IP             |
| **Service**                | service-http              |
| **Translated Destination** | DMZ_Web_10.3.0.1 (static) |

📸 Screenshot Placeholder:
![nat-policy](images/nat-policy.png)

| Field           | Value                       |
| --------------- | --------------------------- |
| **Name**        | Allow_DNAT_to_Web           |
| **From Zone**   | UnTrust                     |
| **To Zone**     | DMZ                         |
| **Source**      | any                         |
| **Destination** | WAN_Public_IP (pre-NAT IP)  |
| **Service**     | web-browsing / service-http |
| **Action**      | Allow                       |

set rulebase security rules Allow_DNAT_to_Web from UnTrust
set rulebase security rules Allow_DNAT_to_Web to DMZ
set rulebase security rules Allow_DNAT_to_Web source any
set rulebase security rules Allow_DNAT_to_Web destination WAN_Public_IP
set rulebase security rules Allow_DNAT_to_Web application web-browsing
set rulebase security rules Allow_DNAT_to_Web service service-http
set rulebase security rules Allow_DNAT_to_Web action allow

📸 Screenshot Placeholder:
![security-policy](images/security-policy.png)

ping 172.16.1.2
curl http://172.16.1.2

✅ Expected Result:

HTTP connection successful
Server webpage loads
Traffic logs visible under Monitor → Traffic

📸 Screenshot Placeholder:
![browser-test](images/browser-test.png)

🔍 Verification

CLI checks:
show session all | match 10.3.0.1
show session all
show running nat-policy
show running security-policy
show interface all


🧠 Skills Demonstrated
Layer-3 NAT translation (SNAT + DNAT)
Zone-based security enforcement
Application and service identification
Real-time session troubleshooting
Palo Alto CLI & GUI proficiency

🏁 Outcome
✅ Successfully accessed internal web server (10.3.0.1) via external IP (172.16.1.2).
✅ Confirmed NAT & session visibility in firewall CLI and traffic logs.
✅ Demonstrated a complete inbound web publishing scenario.





