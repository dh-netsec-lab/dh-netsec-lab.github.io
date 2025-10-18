# 🧱 Palo Alto Networks Lab Series

Welcome to my **Palo Alto Networks Lab Series** — a hands-on collection of firewall and network-security configurations built in **VMware** and **EVE-NG** environments.  
Each lab demonstrates real-world enterprise use cases and showcases practical skills in **routing**, **NAT**, **VPN**, and **user identity integration**.

---

## 📚 Lab Index

| 🧩 **Lab Name** | 🧠 **Description** | 🔗 **Link** |
|-----------------|--------------------|-------------|
| **DNAT Lab** | Configure **Destination NAT** to publish an internal web server (e.g., 10.3.0.1) to the internet via the untrust interface. | [View Lab →](./palo-alto-dnat-lab/) |
| **L2 NAT Interface Lab** | Demonstrate **Layer 2 + Layer 3 + VWire** with **SNAT** and VLAN segmentation. | [View Lab →](./palo-alto-l2-nat-interface-lab/) |
| **Site-to-Site VPN Lab** | Build a **site-to-site IPsec VPN** between two Palo Alto firewalls to securely connect remote networks. | [View Lab →](./palo-alto-site-to-site-vpn/) |
| **User-ID Integration Lab** | Integrate Palo Alto with **Active Directory (WMI/LDAP)** for user-based policies and visibility. | [View Lab →](./palo-alto-user-id-lab/) |
| **GlobalProtect VPN Lab** | Configure **GlobalProtect VPN** for secure remote access using certificate authentication. | [View Lab →](./palo-alto-globalprotect-lab/) |


---

## 🧱 Technologies Covered
- Palo Alto Networks **NGFW (PAN-OS 10.x)**
- **NAT (SNAT & DNAT)** rules and verification
- **IPsec VPN** configuration and routing between sites
- **User-ID / LDAP / WMI** authentication integration
- **GlobalProtect VPN** portal and gateway setup
- Security policy design, traffic inspection, and logging

---

## 💡 Usage
Each lab directory contains:
- A detailed **README.md** guide for configuration  
- A **/screenshots/** folder for visual reference  
- **CLI validation** and troubleshooting steps  

Browse each folder to explore configurations or clone this repository for your own lab environment.

---

**Next:** [Start with the DNAT Lab →](./palo-alto-dnat-lab/)
