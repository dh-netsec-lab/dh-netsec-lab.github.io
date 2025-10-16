# Palo Alto User-ID Agentless Configuration Lab

## Objective
This lab demonstrates the configuration and troubleshooting of **Palo Alto’s User-ID Agentless setup** using Windows Server 2022 as the domain controller.  
The goal is to enable user identification on the firewall without installing the User-ID agent, leveraging WMI and LDAP queries directly from the firewall.

---

## Topology

![Topology](/network-security/palo-alto-user-id-lab/screenshot/topology.png)

**Components**
- **Firewall (PA-VM)**  
  - Mgmt: `192.168.118.188`  
  - Untrust: `192.168.1.254/24`  
  - Trust: `10.1.0.254/24`
- **Domain Controller / AD**  
  - Hostname: `WIN_2022_AD`  
  - IP: `10.1.0.207`  
  - Domain: `4OUTOF7.com`
- **Client Systems**  
  - Domain-joined Windows 10 host(s)

---

## Lab Overview

| Component | Purpose |
|------------|----------|
| **Windows Server 2022** | Domain Controller, DNS, and LDAP Authentication |
| **Palo Alto Firewall** | Agentless User-ID Integration |
| **User-ID Service Account** | Service account with necessary WMI and DCOM privileges |
| **Verification** | Map IP addresses to domain users in the firewall |

---

## Step 1: Create the User-ID Service Account

1. In **Active Directory Users and Computers**, create a user:  
   **Name:** `svc-paloalto`  
   **Password:** Strong non-expiring password  
2. Add this account to the following local groups on the Domain Controller:  
   - Distributed COM Users  
   - Event Log Readers  
   - Remote Management Users  
3. Delegate “Read all properties” and “Read logon information” in AD Users & Computers.

![User-ID Configuration](/network-security/palo-alto-user-id-lab/screenshot/service-account.png)

---

## Step 2: Enable Agentless User-ID on the Firewall

1. Navigate to **Device → User Identification → User Mapping**.  
2. Enable **User-ID** and **Server Monitoring**.  
3. Add the Domain Controller as a monitored server:  
   - **Name:** `Windows_AD`  
   - **Server:** `10.1.0.207`  
   - **Type:** `Active Directory (WMI)`  
   - **User:** `4OUTOF7\svc-paloalto`  
   - **Enable Server Monitoring**

![Server Monitor](/network-security/palo-alto-user-id-lab/screenshot/server-monitor.png)

---

## Step 3: Verify Connectivity and Permissions

Run the following CLI commands on the firewall:

```bash
> show user server-monitor state all
> show user user-id-agent statistics
> show user ip-user-mapping all
> show user user-id-agent state all
