# 🔐 Palo Alto Site-to-Site VPN Lab  

![Palo Alto](https://img.shields.io/badge/Palo%20Alto-NGFW-blue?logo=paloaltonetworks&logoColor=white)
![Category](https://img.shields.io/badge/Category-Network%20Security-red)
![Platform](https://img.shields.io/badge/Platform-EVE--NG-lightgrey)
![Version](https://img.shields.io/badge/PAN--OS-10.1.6-yellow)

**Category:** Network Security  
**Tools/Tech:** Palo Alto NGFW (PAN-OS 10.1.6), EVE-NG, IPsec VPN  

---

## 🎯 Objective
Configure and validate a **site-to-site IPsec VPN** tunnel between two Palo Alto firewalls, allowing secure communication between two branch networks.

---

## 🧩 Lab Topology
![VPN Topology](./screenshots/palo-vpn-topology.png)

| Device | Public IP | LAN Network | Tunnel Interface | Role |
|---------|------------|-------------|------------------|------|
| **PaloAlto-1** | 192.168.1.1 | 10.0.1.0/24 | tunnel.1 | HQ |
| **PaloAlto-2** | 192.168.3.1 | 10.0.2.0/24 | tunnel.1 | Branch |

---

## ⚙️ Environment Setup
- Two Palo Alto VM-Series firewalls in **EVE-NG**
- Each firewall configured with three zones:
  - **Trust (LAN)**
  - **Untrust (WAN/Transport)**
  - **VPN (Tunnel)**

---

## 🧭 Configuration Steps

### 1️⃣ IKE Gateway Setup
- Authentication: **Pre-shared key**
- Version: **IKEv2**
- Local/Peer Address: Public IPs of both firewalls
- Pre-shared key: `paloalto123`

---

### 2️⃣ IPsec Tunnel Configuration
- IKE Gateway: `vpn-gw`
- IPsec Crypto Profile: AES-256 / SHA256 / DH Group 14
- Proxy IDs: 10.0.1.0/24 ↔ 10.0.2.0/24

---

### 3️⃣ Tunnel Interface Setup
- Interface: `tunnel.1`
- Zone: **VPN**
- Added to the virtual router for routing
- Assigned to the correct security zone

---

### 4️⃣ Routing Configuration
- HQ Firewall: Route 10.0.2.0/24 via `tunnel.1`
- Branch Firewall: Route 10.0.1.0/24 via `tunnel.1`
- Verify via `show routing route | match 10.0`

---

### 5️⃣ Security Policies
- Allow traffic **Trust → VPN**
- Allow traffic **VPN → Trust**

---

### 6️⃣ Validation Commands
```bash
> show vpn ike-sa gateway <gateway-name>
> show vpn ipsec-sa tunnel <tunnel-name>
> test security-policy-match source 10.0.1.13 destination 10.0.2.13 protocol 6 destination-port 80
> show routing route | match 10.0.2.13
> ping source 10.0.1.13 host 10.0.2.13
