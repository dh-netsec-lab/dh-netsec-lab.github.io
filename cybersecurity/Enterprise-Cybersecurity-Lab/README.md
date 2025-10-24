# ECL - Enterprise Cybersecurity Lab

## Overview
The Enterprise Cybersecurity Lab (ECL) is a multi-site, full-spectrum security lab designed to simulate a real-world enterprise network environment. It integrates multi-vendor firewalls, endpoints, servers, logging infrastructure, and security monitoring tools. The lab allows hands-on practice in network security, SOC operations, incident response, and enterprise-level system administration.

**Virtualization Platforms:** EVE-NG and VMware  
**Firewalls:** FortiGate and Palo Alto Networks  
**Lab Focus:** Full Spectrum Security Engineer (Network + SOC + Detection + Logging)

---

## Lab Purpose
The purpose of the ECL is to provide a **centralized lab environment** where multiple security and network technologies can be practiced together without rebuilding separate labs. Key objectives include:

- Practicing firewall policy creation and management with FortiGate and Palo Alto
- Building VLAN-segmented enterprise networks
- Implementing centralized logging and SIEM workflows (Sysmon → Rsyslog → Splunk)
- Detecting and responding to network and endpoint security events
- Hosting vulnerable applications for testing and red team exercises
- Automating backups and configuration versioning across devices

---

## Network & VLAN Architecture

| Site       | Subnet Range     | VLAN / Role                      |
|------------|----------------|----------------------------------|
| **Bama**   | 10.0.0.0/19     | 10: MGMT, 20: User, 30: Servers (AD/Linux), 40: Monitoring, 50: Remote User, 60: Vulnerable Apps, 70–100: Reserved |
| **New York** | 10.0.32.0/19  | 32: MGMT, 33: User, 34–36: Reserved, 37: Web_Srv_1, 38: Web_Srv_2 |
| **Cali**   | 10.0.64.0/19    | 64: MGMT, 65: Virtual_Server_VIP, 66: Vulnerable Apps, 67–73: Reserved |

**OOB Management Subnet:** 192.168.118.0/24

---
![Network Topology](screenshots/network_topology.png)


## Technology Stack

| Category           | Technology / Tool                  | Role / Purpose |
|-------------------|-----------------------------------|----------------|
| Firewalls          | FortiGate, Palo Alto              | Perimeter & segmentation, policy enforcement, VPN |
| Logging / SIEM     | Splunk, Rsyslog, Sysmon           | Centralized logging, monitoring, detection |
| IDS / IPS          | Suricata                          | Network intrusion detection & alerting |
| Server Infrastructure | Windows Server 2022, Linux VMs | AD domain, DNS/DHCP, monitoring, vulnerable app hosting |
| WAF                | FortiWeb                           | Web application protection & testing |
| Automation & Backup | Linux scripts, Git repo           | Configuration versioning, automated backups |

---

## Skills Demonstrated

- Network architecture & segmentation (VLANs, subnets, routing)
- Firewall policy design (FortiGate & Palo Alto)
- Logging & SIEM pipelines (Sysmon → Rsyslog → Splunk)
- Detection & response (Suricata alerts, Splunk correlation)
- Systems administration (Windows AD, Linux services)
- Automation & backup workflows for enterprise environments

---

## Usage Instructions
1. Navigate to `/diagrams` to see the lab topology and security architecture images.  
2. `/configs` contains sample configuration files for firewalls, Linux, and Windows servers.  
3. `/scripts` contains automation scripts for configuration backup and logging setup.  
4. `/documentation` contains your IP/VLAN tables and lab notes.

---

## Resume / Portfolio Snippet

> Designed and implemented a multi-site enterprise cybersecurity lab integrating FortiGate and Palo Alto firewalls, Splunk SIEM, Suricata IDS, Windows Server AD, Linux servers, and VLAN-segmented networks. Practiced full-spectrum security engineering including SOC workflows, detection, monitoring, and automated configuration management.

---

## Interview Elevator Pitch

> “I built the ECL — a multi-vendor enterprise lab using FortiGate and Palo Alto firewalls, Splunk, Suricata, and Windows/Linux infrastructure.  
> I manage VLAN segmentation, centralized logging, incident detection, and vulnerability testing.  
> This lab lets me practice full-spectrum security engineering and demonstrates my ability to design, implement, and operate enterprise security architectures.”

