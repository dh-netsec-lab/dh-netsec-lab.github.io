# 🔐 Palo Alto Site-to-Site VPN Lab  

![Palo Alto](https://img.shields.io/badge/Palo%20Alto-NGFW-blue?logo=paloaltonetworks&logoColor=white)
![Category](https://img.shields.io/badge/Category-Network%20Security-red)
![Platform](https://img.shields.io/badge/Platform-EVE--NG-lightgrey)
![Version](https://img.shields.io/badge/PAN--OS-10.1.6-yellow)

**Category:** Network Security  
**Tools/Tech:** Palo Alto NGFW (PAN-OS 10.1.6), EVE-NG, IPsec VPN  

---

## 🎯 Objective
Establish a **site-to-site IPsec VPN tunnel** between two Palo Alto firewalls, enabling secure routed communication between two branch networks.

---

## 🧩 Lab Topology
![Topology](./screenshots/palo-vpn-topology.png)

| Device | Public IP | LAN Network | Tunnel Interface | Role |
|---------|------------|--------------|------------------|------|
| **PaloAlto-1** | 192.168.1.1 | 10.0.1.0/24 | tunnel.1 | HQ |
| **PaloAlto-2** | 192.168.3.1 | 10.0.2.0/24 | tunnel.1 | Branch |

---

## ⚙️ Environment Setup
- Two Palo Alto VM-Series firewalls running in **EVE-NG**  
- Each device has:
  - **LAN Zone** (Trust)
  - **Transport Zone** (Untrust)
  - **Tunnel Zone** (VPN)

---

## 🧭 Configuration Steps

### 1️⃣ IKE Gateway
- Authentication – Pre-shared key  
- Version – IKEv2  
- Peer IPs: 192.168.1.1 ↔ 192.168.3.1  

### 2️⃣ IPsec Tunnel
- IKE Gateway: `vpn-gw`  
- IPsec Crypto Profile: AES-256 / SHA256 / DH Group 14  
- Proxy IDs: 10.0.1.0/24 ↔ 10.0.2.0/24  

### 3️⃣ Tunnel Interface
- Interface: `tunnel.1`  
- Zone: VPN  
- Added to virtual router  

### 4️⃣ Routing
- HQ: Static route 10.0.2.0/24 → `tunnel.1`  
- Branch: Static route 10.0.1.0/24 → `tunnel.1`  

### 5️⃣ Security Policies
- Allow Trust → VPN  
- Allow VPN → Trust  

### 6️⃣ Validation
```bash
> show vpn ike-sa
> show vpn ipsec-sa
> test security-policy-match source 10.0.1.13 destination 10.0.2.13 protocol 6 destination-port 80
> show routing route | match 10.0.1.13
> ping source 10.0.1.13 host 10.0.2.13

