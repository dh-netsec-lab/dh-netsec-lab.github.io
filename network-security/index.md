# 🛡️ Palo Alto Network Security Labs

Welcome to my **Palo Alto Networks Lab Series** — a hands-on collection of firewall and network-security configurations built in **VMware** and **EVE-NG** environments.  
Each lab demonstrates real-world enterprise use cases and is designed to show practical skills across routing, NAT, VPN, and identity integration.

---

## 📚 Lab Index

| 🧩 **Lab Name** | 🧠 **Description** | 🔗 **Link** |
|-----------------|--------------------|-------------|
| **DNAT Lab** | Configures **Destination NAT** to publish an internal web server (e.g., 10.3.0.1) to the internet via the untrust interface. | [View Lab →](./palo-alto-dnat-lab/palo-alto-dnat-lab.md) |
| **L2 NAT Interface Lab** | Demonstrates **Layer 2 NAT** configuration and traffic flow between VLAN zones using Ethernet switching. | [View Lab →](./palo-alto-l2-nat-interface-lab/palo-alto-l2-nat-interface-lab.md) |
| **Site-to-Site VPN Lab** | Builds an **IPsec VPN** tunnel between two Palo Alto firewalls to securely connect remote networks. | [View Lab →](./palo-alto-site-to-sitevpn/palo-alto-site-to-sitevpn.md) |
| **User-ID Integration Lab** | Integrates Palo Alto with **Active Directory (WMI/LDAP)** for user-based policies and monitoring. | [View Lab →](./palo-alto-userid/palo-alto-userid.md) |
| **GlobalProtect VPN Lab** | Configures **GlobalProtect** to enable secure remote user access with certificate-based authentication. | [View Lab →](./palo-alto-globalprotect-lab/palo-alto-globalprotect-lab.md) |

---

## 🧱 Technologies Covered
- Palo Alto Networks **NGFW (PAN-OS 10.x)**
- **NAT (SNAT & DNAT)** rules and verification
- **IPsec VPN** and routing between firewalls
- **User-ID / LDAP / WMI** integration
- **GlobalProtect VPN** (portal + gateway)
- Security policy, logging, and monitoring

---

## 💡 Usage
Each lab directory contains:
- A `README` or `*.md` guide explaining the full configuration  
- A `/screenshots/` folder for visual references  
- Verified CLI outputs and GUI examples  

Clone or browse individual labs to view step-by-step configurations.

---

## 🌐 Repository
Return to the main project home:  
➡️ [dh-netsec-lab.github.io](https://dh-netsec-lab.github.io/)


