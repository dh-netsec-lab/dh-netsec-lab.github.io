# 🧩 Phase 1 – Network Connectivity Verification  
*Foundation Phase of the Enterprise Cybersecurity Lab (ECL)*  

---

## 🎯 Objective  
Validate core routing, NAT, and Internet reachability across the **Enterprise Cybersecurity Lab (ECL)**.  
Each component demonstrates full traffic flow from internal LAN hosts through multiple firewalls and the edge router to the Internet.

---

## 🧱 Topology Overview  

| Component | Role | Key Function |
|:--|:--|:--|
| **Edge Router** | Cisco Router | Double NAT and default gateway to Internet |
| **Bama_FW** | FortiGate | Outbound NAT and routing to Edge Router |
| **NY_FW** | Palo Alto | DIPP NAT for Trust → Untrust traffic |
| **LAN Host** | Windows / Linux PC | Test connectivity and verify routes |

![Phase 1 Topology](../screenshots/network_topology.png)

---

## 🧩 Verification Steps & Results  

### 1️⃣ Router NAT Translations  
Dynamic NAT mappings translating firewall WAN IPs to public egress IP.  
```bash
show ip nat translations

