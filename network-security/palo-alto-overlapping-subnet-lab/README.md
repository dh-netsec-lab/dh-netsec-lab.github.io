# 🌐 Palo Alto Overlapping Subnet VPN Lab

![Palo Alto](https://img.shields.io/badge/Palo%20Alto-NGFW-blue?logo=paloaltonetworks&logoColor=white)
![Category](https://img.shields.io/badge/Category-Network%20Security-red)
![Platform](https://img.shields.io/badge/Platform-EVE--NG-lightgrey)
![Version](https://img.shields.io/badge/PAN--OS-10.1.6-yellow)

---

## 🎯 Objective
Configure and validate a **Site-to-Site IPsec VPN** where both locations use the **same internal subnet (10.2.2.0/24)**.  
Implement **bi-directional NAT** to translate overlapping subnets (10.4.4.0/24 and 10.3.3.0/24) to enable secure communication between the two sites.

This lab simulates a **real-world overlapping subnet scenario** — common in mergers, acquisitions, and multi-tenant designs.

---

## 🧩 Topology
![Topology](screenshots/overlap-topology.png)

| Site | Firewall | Internal Subnet | Mapped (Translated) Subnet | Public IP | Tunnel Interface |
|------|------------|-----------------|-----------------------------|------------|------------------|
| **Site-A (HQ)** | PaloAlto-1 | 10.2.2.0/24 | 10.4.4.0/24 | 203.0.113.254 | tunnel.1 |
| **Site-B (Branch)** | PaloAlto-2 | 10.2.2.0/24 | 10.3.3.0/24 | 198.51.100.254 | tunnel.1 |

📍 *Site-A pings 10.3.3.0/24 (mapped subnet on Site-B)*  
📍 *Site-B pings 10.4.4.0/24 (mapped subnet on Site-A)*

---

## ⚙️ Configuration Steps

---

### 1️⃣ Create the IKE Gateway
**IKE Gateway Settings:**
- Version: **IKEv2**
- Authentication: **Pre-shared key**
- Local IPs:  
  - Site-A: `203.0.113.254`  
  - Site-B: `198.51.100.254`
- Peer IP: Opposite firewall public IP  
- Pre-shared key: `paloalto123`

📸 **Screenshot:**  
![IKE Gateway](screenshots/ike-gateway.png)

---

### 2️⃣ Configure the IPsec Tunnel
**IPsec Tunnel Settings:**
- IKE Gateway: `vpn-gw`
- IPsec Crypto Profile: AES-256 / SHA256 / DH Group 14
- Proxy IDs:
  - Site-A: Local `10.4.4.0/24` → Remote `10.3.3.0/24`
  - Site-B: Local `10.3.3.0/24` → Remote `10.4.4.0/24`

📸 **Screenshot:**  
![IPsec Tunnel](screenshots/ipsec-tunnel.png)

---

### 3️⃣ NAT Configuration

#### 🔹 Site-A Firewall
**Source NAT (SNAT):**
- Source: `10.2.2.0/24`
- Translated Source: `10.4.4.0/24`
- Destination: `10.2.2.0/24` (remote pre-NAT)
- To Zone: **VPN**

**Destination NAT (DNAT):**
- Destination: `10.3.3.0/24`
- Translated Destination: `10.2.2.0/24`

📸 **Screenshot:**  
![SiteA NAT Policy](screenshots/nat-policy-hq.png)

---

#### 🔹 Site-B Firewall
**Source NAT (SNAT):**
- Source: `10.2.2.0/24`
- Translated Source: `10.3.3.0/24`
- Destination: `10.2.2.0/24`
- To Zone: **VPN**

**Destination NAT (DNAT):**
- Destination: `10.4.4.0/24`
- Translated Destination: `10.2.2.0/24`

📸 **Screenshot:**  
![SiteB NAT Policy](screenshots/nat-policy-branch.png)

---

### 4️⃣ Proxy IDs
Each firewall uses **translated subnets** for its Proxy ID configuration.

| Firewall | Local | Remote |
|-----------|--------|---------|
| Site-A | 10.4.4.0/24 | 10.3.3.0/24 |
| Site-B | 10.3.3.0/24 | 10.4.4.0/24 |

📸 **Screenshot:**  
![Proxy ID](screenshots/proxy-id.png)

---

### 5️⃣ Static Routes
Add static routes so each site knows to reach the mapped subnet through the tunnel.

```bash
set network virtual-router default routing-table ip static-route vpn-branch destination 10.3.3.0/24 interface tunnel.1
set network virtual-router default routing-table ip static-route vpn-hq destination 10.4.4.0/24 interface tunnel.1

