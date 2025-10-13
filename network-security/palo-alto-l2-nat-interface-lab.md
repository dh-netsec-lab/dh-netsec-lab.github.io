# 🔄 Palo Alto Layer 2, VLAN & NAT Policy Lab

## 🎯 Objective
Demonstrate configuration of:
- VLAN and sub-interface segmentation  
- Layer 2 interfaces and VLAN tagging  
- Virtual Wire inspection  
- Tap mode traffic monitoring  
- L3 VLAN interface configuration  
- Source NAT and Security Policies  

## 🧱 Topology Overview
| Interface | Type | Zone | Description |
|------------|------|------|--------------|
| e1/1,e1/2 | Layer 2 VLAN 10 | Inside | Access layer VLAN |
| e1/3,e1/4 | Sub-interfaces | Inside | Routed segmentation |
| e1/5,e1/6 | Virtual Wire | VWire | Inline inspection |
| e1/7 | L3 / Untrust | WAN 172.16.1.2/24 |
| e1/9 | Tap | Tap-Monitor | SPAN mirror |
| e1/11 | L3 / Trust | Inside 10.1.0.1/24 |

## ⚙️ Configuration Summary
```bash
set network interface ethernet e1/7 layer3 ip 172.16.1.2/24
set rulebase nat rules Outbound-SNAT from Trust to Untrust source 10.1.0.0/24 to-interface e1/7 source-translation dynamic-ip-and-port interface-address interface e1/7
set rulebase security rules Allow-Trust-to-Untrust from Trust to Untrust source any destination any application any action allow
commit
