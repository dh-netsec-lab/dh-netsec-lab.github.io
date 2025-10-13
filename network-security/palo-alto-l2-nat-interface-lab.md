# 🔄 Palo Alto Layer 2, VLAN & NAT Policy Lab

![Palo Alto](https://img.shields.io/badge/Palo%20Alto-Firewall-orange)
![Type](https://img.shields.io/badge/Lab-L2%20Interfaces%20%7C%20NAT-blue)
![Status](https://img.shields.io/badge/Status-Complete-green)

---

## 🎯 Objective
Showcase configuration and validation of:
- Layer-2 VLANs  
- VLAN subinterfaces (L3)  
- Virtual Wire and Tap modes  
- Source NAT and Security Policies  
- Traffic verification using Monitor → Traffic

---

## 🧱 Topology Overview
| Interface | Type | Zone | Purpose |
|------------|------|------|----------|
| e1/1,e1/2 | L2 / VLAN 10 | Inside | Access layer |
| e1/3,e1/4 | L3 sub-interfaces | Inside | Routed segments |
| e1/5,e1/6 | Virtual Wire | VWire | Inline inspection |
| e1/7 | L3 Untrust | WAN | 172.16.1.2/24 |
| e1/9 | Tap | Tap-Monitor | SPAN mirror |
| e1/11 | L3 Trust | Inside | 10.1.0.1/24 |

---

## ⚙️ Key Configuration (Summary)


---

## 🧪 Validation Steps
1. Verify NAT and policy logs in **Monitor → Traffic**  
2. Observe mirrored packets on the Tap interface  
3. Confirm intra-VLAN and inter-zone policies  
4. Test outbound Internet access via SNAT

---

## 📸 Suggested Screenshots
- Interfaces (L2, VLAN, VWire, Tap)  
- NAT and Security Policy tabs  
- Monitor → Traffic showing translations

---

**Back to Labs:** [⬅ Network-Security Index](./index.md)
