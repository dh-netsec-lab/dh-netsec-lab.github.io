# Palo Alto Site-to-Site VPN Lab

## Objective
Configure and validate a site-to-site IPsec VPN between two Palo Alto firewalls to enable secure communication between separate private networks over an untrusted WAN.

This lab demonstrates how Palo Alto firewalls establish encrypted tunnels and route traffic between remote sites.

---

## Topology
![Topology](screenshots/palo-vpn-topology.png)

---

## Network Overview

| Site | Firewall | Public IP | LAN Subnet | Tunnel Interface |
|-------|------------|------------|-------------|------------------|
| HQ | PaloAlto-1 | 192.168.1.1 | 10.0.1.0/24 | tunnel.1 |
| Branch | PaloAlto-2 | 192.168.3.1 | 10.0.2.0/24 | tunnel.1 |

---

## Traffic Flow

- Traffic from the HQ LAN (10.0.1.0/24) is routed to the tunnel interface  
- Traffic is encrypted and sent across the WAN  
- The Branch firewall decrypts the traffic and forwards it to the remote LAN (10.0.2.0/24)  
- Return traffic follows the same path in reverse  

---

## Configuration Steps

### 1. Configure IKE Crypto Profile

Create an IKE Crypto Profile to define Phase 1 negotiation settings.

Settings used:
- Encryption: AES-256-CBC  
- Authentication: SHA256  
- DH Group: Group 14  
- Key Lifetime: 8 hours  

This profile is used by the IKE Gateway during tunnel establishment.

Screenshot:  
![IKE Crypto Profile](screenshots/palo-vpn-ike-crypto.png)

---

### 2. Configure IKE Gateway

Configure the IKE gateway using:
- IKE Version: IKEv2  
- Authentication: Pre-shared key  
- Local IP: firewall public IP  
- Peer IP: remote firewall public IP  
- IKE Crypto Profile: (created above)  

This establishes Phase 1 (IKE SA).

Screenshot:  
![IKE Gateway](screenshots/palo-vpn-ike.png)

---

### 3. Configure IPSec Crypto Profile

Create an IPSec Crypto Profile to define Phase 2 encryption settings.

Settings used:
- Encryption: AES-256-CBC  
- Authentication: SHA256  
- DH Group: Group 14  
- Lifetime: 1 hour  

This profile is used to secure data traffic inside the tunnel.

Screenshot:  
![IPSec Crypto Profile](screenshots/palo-vpn-ipsec.png)

---

### 4. Configure IPSec Tunnel

Create the IPSec tunnel using:
- IKE Gateway: vpn-gw  
- IPSec Crypto Profile: IPSec_Crypto_To_147  
- Tunnel Interface: tunnel.1  

Proxy IDs:
- Local: 10.0.1.0/24  
- Remote: 10.0.2.0/24  

This defines Phase 2 (IPSec SA).

Screenshot:  
![IPSec Tunnel](screenshots/palo-vpn-ipsec.png)

---

### 5. Configure Tunnel Interface

Assign the tunnel interface to:
- Virtual Router: default  
- Security Zone: VPN  

This interface carries encrypted VPN traffic.

Screenshot:  
![Tunnel Interface](screenshots/palo-vpn-tunnel-interface.png)

---

### 6. Configure Routing

Add static routes for remote networks:

| Site | Destination | Next Hop |
|------|--------------|-----------|
| HQ | 10.0.2.0/24 | tunnel.1 |
| Branch | 10.0.1.0/24 | tunnel.1 |

These routes ensure traffic is directed into the VPN tunnel.

Screenshot:  
![Routing Table](screenshots/palo-vpn-route.png)

---

### 7. Configure Security Policies

Allow traffic between zones:

- Trust → VPN  
- VPN → Trust  

These policies permit bidirectional communication across the tunnel.

Screenshot:  
![Security Policies](screenshots/palo-vpn-policy.png)

---

## Verification

### VPN Status

Run:
```
show vpn ike-sa
show vpn ipsec-sa
```

Confirm:
- IKE Security Association is established  
- IPSec Security Association is active  
- Tunnel is up and passing traffic  

---

### Routing and Policy Validation

Run:
```
show routing route | match 10.0
test security-policy-match source 10.0.1.13 destination 10.0.2.13 protocol 6 destination-port 80
```

Confirm:
- Routes exist for remote networks  
- Security policies allow traffic  

---

### Connectivity Test

Run:
```
ping source 10.0.1.13 host 10.0.2.13
```

Confirm successful communication between sites.

---

## Key Takeaways

- Phase 1 (IKE) establishes the secure tunnel  
- Phase 2 (IPSec) encrypts traffic inside the tunnel  
- Tunnel interfaces integrate VPN traffic into routing and policy  
- Proper alignment of routing and security policy is required for connectivity  

---

## Summary

This lab demonstrates how Palo Alto firewalls establish and validate a site-to-site VPN using IKE and IPSec.

By combining crypto profiles, tunnel interfaces, routing, and security policies, remote networks can securely communicate across an untrusted WAN.

---

## Navigation

| Previous | Back to Index | Next |
|----------|--------------|------|
| [L2 NAT Interface Lab](../palo-alto-l2-nat-interface-lab/) | [Palo Alto Lab Index](../) | [Overlapping Subnets VPN Lab →](../palo-alto-overlapping-subnet-lab/) |
