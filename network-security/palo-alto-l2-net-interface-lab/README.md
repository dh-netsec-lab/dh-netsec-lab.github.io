# 🧱 Palo Alto Layer 2, VLAN & NAT Interface Lab

## 🎯 Objective
The goal of this lab is to configure and validate **Layer 2 VLANs, Virtual Wires, and NAT Policies** on a Palo Alto Firewall to demonstrate switching, routing, and traffic translation in a mixed Layer 2 / Layer 3 environment.

---

## 🧩 Topology
![Topology](screenshots/topology.png)

**Interface Summary**

| Interface | Type | Zone | Purpose |
|------------|------|------|----------|
| e1/1, e1/2 | Layer 2 / VLAN 10 | Inside | Access Layer (Switching) |
| e1/3, e1/4 | L3 Subinterfaces | Inside | Routed Segments |
| e1/5, e1/6 | Virtual Wire | VWire | Inline Inspection |
| e1/7 | L3 Untrust | WAN | 172.16.1.2/24 |
| e1/9 | Tap | Tap-Monitor | SPAN Mirror |
| e1/11 | L3 Trust | Inside | 10.1.0.1/24 |

---

## ⚙️ Configuration Steps

---

### 1️⃣ Configure Layer 2 and VLAN Interfaces
Create VLAN objects and assign Layer 2 interfaces.

**Example:**
