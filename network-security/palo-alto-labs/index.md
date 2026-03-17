# Palo Alto Network Lab Series

## Overview
This section of the Network Security Portfolio demonstrates hands-on configuration, deployment, and operational management of Palo Alto Networks firewalls.

The labs are designed to reflect real-world enterprise scenarios, progressing from foundational firewall functions to advanced capabilities such as VPN deployment, identity-based security, SSL decryption, and centralized management using Panorama.

---

## Lab Index

| Lab | Objective | Access |
|:--|:--|:--|
| **Destination NAT (DNAT) – Publishing Internal Services** | Configure destination NAT to securely expose an internal web server to external networks through the untrust interface. | [View Lab →](./palo-alto-dnat-lab/) |
| **Layer 2 / Layer 3 NAT with Virtual Wire (VWire)** | Demonstrate Layer 2, Layer 3, and Virtual Wire deployment with source NAT and VLAN segmentation. | [View Lab →](./palo-alto-l2-nat-interface-lab/) |
| **Site-to-Site IPsec VPN Deployment** | Build a site-to-site IPsec VPN between two Palo Alto firewalls to securely connect remote networks. | [View Lab →](./palo-alto-site-to-site-vpn/) |
| **Overlapping Subnets VPN with NAT** | Build a site-to-site VPN between identical subnets using NAT translation to resolve overlapping address space. | [View Lab →](./palo-alto-overlapping-subnet-lab/) |
| **User-ID Integration with Active Directory** | Integrate Palo Alto with Active Directory using WMI and LDAP for identity-based policy enforcement and visibility. | [View Lab →](./palo-alto-user-id-lab/) |
| **GlobalProtect Remote Access VPN** | Configure GlobalProtect for secure remote access using certificate-based authentication. | [View Lab →](./palo-alto-globalprotect-lab/) |
| **SSL Decryption (Inbound and Outbound)** | Inspect encrypted HTTPS traffic using SSL Forward Proxy and inbound decryption while managing certificates correctly. | [View Lab →](./palo-alto-ssl-decryption-lab/) |
| **Panorama Centralized Management** | Centralize firewall management using Panorama templates, template stacks, and policy deployment workflows. | [View Lab →](./palo-alto-panorama/) |

---

## Key Capabilities Demonstrated
- Network Address Translation (NAT)
- Site-to-Site and Remote Access VPNs
- Identity-Based Security (User-ID)
- SSL/TLS Traffic Inspection
- Segmentation and Zone-Based Policy
- Centralized Firewall Management with Panorama

---

## Return
[Back to Network Security Portfolio](../index.md)
