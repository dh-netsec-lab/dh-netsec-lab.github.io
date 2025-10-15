# Palo Alto User-ID Lab

## Objective
This lab demonstrates how to configure **User-ID** on a Palo Alto Networks firewall to map user activity to IP addresses using **Agentless User-ID** and **Active Directory (AD)** integration.  
The goal is to enable identity-based security policies for better visibility and control.

---

## Topology
The following diagram represents the User-ID lab environment.

![Topology](./screenshots/topology.png)

**Key Components:**
- **Palo Alto Firewall:** 10.1.0.254 (Trust interface), 192.168.118.188 (Management)
- **Domain Controller (AD):** 10.1.0.207
- **Windows User System:** 10.1.0.153
- **Domain:** 4OUTOF7.com
- **User-ID Service Account:** 4OUTOF7\svc-paloalto

---

## Lab Environment
- **Platform:** VMware Workstation  
- **PAN-OS Version:** 10.x  
- **Windows Server 2022:** Domain Controller, DNS, and AD  
- **Windows 10:** Domain-joined client system  
- **Purpose:** Demonstrate WMI/LDAP-based User-ID mapping.

---

## Step 1: Configure User-ID Settings on the Firewall

1. Navigate to **Device → User Identification → User Mapping**.  
2. Click **Add** and configure:
   - **Server:** 10.1.0.207  
   - **Type:** Active Directory  
   - **Network User:** `4OUTOF7\svc-paloalto`  
   - **Password:** (Service Account Password)
   - **WMI Authentication:** Enabled  
   - **Enable Session Read:** Checked  

3. Commit the configuration.

![User-ID Agentless Config](screenshots/userid-agentless-settings.png)

---

## Step 2: Configure Server Monitoring

1. Navigate to **Device → User Identification → Server Monitoring**.  
2. Add your AD server:
   - **Server Name:** WIN_2022_AD  
   - **Server Address:** 10.1.0.207  
   - **Enable Server:** Checked  

3. Under **Server List**, ensure **Connection Status** shows as *Connected* after commit.

![Server Monitoring](screenshots/server-monitor.png)

---

## Step 3: Create Security Policy Using User-ID

1. Go to **Policies → Security → Add**  
2. Configure the following:
   - **Name:** User-ID_Test  
   - **From:** Trust  
   - **To:** Untrust  
   - **Source User:** Select specific AD users or groups  
   - **Application:** web-browsing, ssl  
   - **Action:** Allow  

![User-ID Security Policy](screenshots/userid-security-policy.png)

---

## Step 4: Verification and Troubleshooting

### CLI Commands
Check user mappings:
```bash
show user ip-user-mapping all
