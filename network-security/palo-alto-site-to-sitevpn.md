# Palo Alto Site-to-Site VPN Lab

**Category:** Network Security  
**Tools/Tech:** Palo Alto NGFW (PAN-OS 10.1.6), EVE-NG, IPsec VPN

---

## 🎯 Objective
Configure and validate a **site-to-site IPsec VPN** tunnel between two Palo Alto firewalls, allowing secure communication between two branch networks.

---

## 🖥 Lab Diagram
![VPN Diagram](../assets/diagrams/palo-vpn.png)

- **Site PaloAlto-1 :** 10.0.1.0/24 behind PaloAlto-1 
- **Site PaloAlto-2 :** 10.0.2.0/24 behind PaloAlto-2  
- **Public IPs(in the lab):**  
  - PaloAlto-1: 192.168.1.1  
  - PaloAlto-2: 192.168.3.1  

---

## ⚙️ Environment Setup
- **Two Palo Alto VM firewalls** in EVE-NG  
- Each firewall connected to:  
  - Internal LAN  
  - Internet/transport network  

---

## 📝 Steps
1. **IKE Gateway Setup** (both firewalls)  
   - Authentication: Pre-shared key  
   - Local/Peer addresses: Public IPs of each firewall  

2. **IPsec Tunnel Setup**  
   - IKE Gateway: created above  
   - IPsec Crypto Profile: AES-256, SHA256, DH Group 14  

3. **Tunnel Interface Setup**  
   - `tunnel.1` (PaloAlto-1) → Zone: VPN  
   - `tunnel.1` (PaloAlto-2) → Zone: VPN  

4. **Routing**  
   - Static routes:  
     - PaloAlto-1 routes 10.0.2.0/24 via `tunnel.1`  
     - PaloAlto-2 routes 10.0.1.0/24 via `tunnel.1`  

5. **Security Policy**  
   - Allow traffic from LAN → VPN and VPN → LAN  

6. **Validation**  
   - `show vpn ike-sa gateway <gateway-name>` (check IKE Phase 1)  
   - `show vpn ipsec-sa tunnel <tunnel-name>` (check Phase 2)
   -  test security-policy-match source 10.0.1.13 destination 10.0.2.13 protocol 6 destination-port 80
   -  show routing route | match 10.0.1.3
   - Ping between 10.0.1.13 ↔ 10.0.2.13  

---

## ✅ Results
- Tunnel successfully established (IKE + IPsec SAs up).  
- Devices in Site A reached Site B securely.  
- Policies enforced properly over VPN tunnel.  

---

## 📸 Screenshots
(Add: IKE gateway config, IPsec tunnel config, successful SA output)  

Example CLI validation:  
```bash
> show vpn ike-sa
> show vpn ipsec-sa
