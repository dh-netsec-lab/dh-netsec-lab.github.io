# 🧱 Palo Alto Site-to-Site VPN with Overlapping Subnets

This lab demonstrates how to configure a **site-to-site VPN** between two sites that share **identical internal subnets**.  
By using **NAT translation**, each site maps its internal network to a unique subnet for VPN traffic — solving overlapping IP challenges commonly found in M&A or multi-tenant environments.

---

## 🧩 Topology

![Topology](screenshots/topology.png)

| Component | IP/Subnet | Description |
|------------|------------|-------------|
| **Site A LANs** | 10.1.1.0/24 and 10.2.2.0/24 | Local subnets |
| **Site B LAN** | 10.2.2.0/24 | Overlapping subnet with Site A |
| **Mapped Subnet (Site A)** | 10.4.4.0/24 | Used for traffic sent to Site B |
| **Mapped Subnet (Site B)** | 10.3.3.0/24 | Used for traffic sent to Site A |
| **WAN Router** | 203.0.113.0/24 ↔ 198.51.100.0/24 | Simulated public WAN connection |
| **Management** | Site A: 172.29.129.140 <br> Site B: 172.29.129.141 | For firewall GUI/CLI access |

---

## ⚙️ Configuration Steps

### 🔹 Step 1: IKE Gateway Configuration
Configure an IKEv2 gateway on both firewalls.

| Setting | Site A | Site B |
|----------|---------|--------|
| IKE Version | IKEv2 | IKEv2 |
| Peer IP | 198.51.100.254 | 203.0.113.254 |
| Authentication | Pre-shared key | Pre-shared key |
| IKE Crypto Profile | AES-256 / SHA256 / DH Group 14 | AES-256 / SHA256 / DH Group 14 |

**Screenshot:**  
![IKE Gateway - Site A](screenshots/ike-gateway-siteA.png)  
![IKE Gateway - Site B](screenshots/ike-gateway-siteB.png)

---

### 🔹 Step 2: IPSec Tunnel
Create an IPSec tunnel using the configured IKE Gateway.

| Setting | Value |
|----------|--------|
| Tunnel Interface | `tunnel.1` |
| IKE Gateway | As configured above |
| Auto Key IKE | Enabled |
| Proxy IDs | Not manually configured (see note below) |

> ⚠️ **Note on Proxy IDs**  
> Manual Proxy IDs were **not used** in this lab because both peers are **Palo Alto firewalls** using Auto-Key IKEv2.  
> The firewalls automatically negotiated matching Proxy IDs based on the translated subnets (10.4.4.0/24 ↔ 10.3.3.0/24).

**Screenshot:**  
![IPSec Tunnel - Site A](screenshots/ipsec-tunnel-siteA.png)  
![IPSec Tunnel - Site B](screenshots/ipsec-tunnel-siteB.png)

---

### 🔹 Step 3: NAT Configuration

| Site | Source NAT | Destination NAT |
|------|-------------|-----------------|
| **Site A** | 10.1.1.0/24 → 10.4.4.0/24 | 10.3.3.0/24 → 10.2.2.0/24 |
| **Site B** | 10.2.2.0/24 → 10.3.3.0/24 | 10.4.4.0/24 → 10.2.2.0/24 |

**Screenshot:**  
![NAT Policy - Site A](screenshots/nat-policy-siteA.png)  
![NAT Policy - Site B](screenshots/nat-policy-siteB.png)

---

### 🔹 Step 4: Security Policies

Add security rules to allow VPN traffic between the translated subnets.

| Source Zone | Destination Zone | Action |
|--------------|------------------|---------|
| Trust | VPN | Allow |
| VPN | Trust | Allow |

**Screenshot:**  
![Security Policies](screenshots/security-policies.png)

---

### 🔹 Step 5: Routing Configuration

Add static routes for the translated subnets.

| Site | Destination | Next Hop |
|------|--------------|-----------|
| Site A | 10.3.3.0/24 | `tunnel.1` |
| Site B | 10.4.4.0/24 | `tunnel.1` |

**Screenshot:**  
![Virtual Router Routes](screenshots/virtual-router-routes.png)

---

## 🔍 Verification and Monitoring

### 🔸 Verify IKE SA
**Path:** `Network → IPSec Tunnels → Tunnel Info (IKE SA)`  
![IKE SA Active](screenshots/monitor-ike-sa.png)

---

### 🔸 Verify IPsec SA
**Path:** `Network → IPSec Tunnels → Tunnel Info (IPSec SA)`  
![IPSec SA Active](screenshots/monitor-ipsec-sa.png)

---

### 🔸 Verify Traffic Logs
**Path:** `Monitor → Logs → Traffic`  
Filter: `( interface eq tunnel.1 )`  
![Traffic Log Verification](screenshots/traffic-log-verification.png)

---

### 🔸 Ping Verification
From Site A:

|
