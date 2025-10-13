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
