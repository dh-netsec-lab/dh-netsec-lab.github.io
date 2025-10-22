# 🛡️ Palo Alto Threat Prevention Lab

## 🎯 Objective
This lab demonstrates how to implement and verify **Palo Alto Networks Threat Prevention** features — including **Antivirus, Anti-Spyware, Vulnerability Protection, URL Filtering, File Blocking, and WildFire Analysis** — to detect and prevent malicious activity in real time.

The configuration also showcases the use of a **Security Profile Group** applied to a security policy to streamline enforcement.

---

## 🧩 Topology

![Topology](screenshots/palo-threat-prevention-topology.png)

> **Description:**  
> Outbound web and file traffic from the LAN (`10.0.1.0/24`) passes through the Palo Alto firewall’s **Trust (Inside)** zone, where the `Threat_Prevention_Group` security profiles inspect and filter malicious or restricted content before it reaches the **Untrust (Outside)** interface.

| Component | Role | IP / Network |
|------------|------|---------------|
| **Firewall (Trust / Inside)** | LAN Interface | `10.0.1.254/24` |
| **Firewall (Untrust / Outside)** | Internet Interface | `192.168.1.254/24` |
| **Firewall (Management)** | Management Interface | `192.168.118.132` |
| **Active Directory / DNS Server** | Domain Controller, internal test host | `10.0.1.100` |
| **LAN Network** | User subnet | `10.0.1.0/24` |
| **Security Profile Group** | Threat Prevention Bundle | `Threat_Prevention_Group` |

---

## ⚙️ Step 1: Verify Dynamic Updates
1. Navigate to **Device → Dynamic Updates**.  
2. Ensure the following are **downloaded and installed**:
   - Applications and Threats  
   - Antivirus  
   - WildFire  
   - URL Filtering Database  
3. Click **Check Now**, then **Download** and **Install** the latest versions.

🖼 *Screenshot:* `screenshots/dynamic-updates.png`

---

## ⚙️ Step 2: Create or Verify Security Profiles
1. Go to **Objects → Security Profiles**.  
2. Verify or clone the following profiles:
   - **Antivirus:** `AV-Default`
   - **Anti-Spyware:** `Spyware-Default`
   - **Vulnerability Protection:** `Vuln-Default`
   - **URL Filtering:** `URL-Filter`
   - **File Blocking:** `File-Block`
   - **WildFire Analysis:** `WildFire-Analysis`
3. Customize as needed (e.g., block high-risk categories or file types).

🖼 *Screenshot:* `screenshots/security-profiles.png`

---

## ⚙️ Step 3: Create the Threat Prevention Group
1. Go to **Objects → Security Profile Groups → Add**.  
2. Name: `Threat_Prevention_Group`  
3. Add the profiles listed above.

🖼 *Screenshot:* `screenshots/threat-prevention-group.png`

---

## ⚙️ Step 4: Apply the Group to Security Policies
1. Go to **Policies → Security**.  
2. Edit the following policies and attach the group:
   - `Inside_To_Outside`
   - `LAN_To_VPN`
   - `VPN_To_LAN`
3. Under the **Actions** tab → **Profile Setting**, select `Group Profile` → `Threat_Prevention_Group`.

🖼 *Screenshot:* `screenshots/security-policy-threat-prevention.png`

---

## 🧪 Step 5: Testing and Validation

### **1️⃣ Antivirus Test**
- From a LAN host (`10.0.1.100`), attempt to download the **EICAR test file**:  
  [https://secure.eicar.org/eicar.com](https://secure.eicar.org/eicar.com)  
- The firewall should block the download, generating a **Threat Log** entry.

🖼 *Screenshot:* `screenshots/eicar-block.png`

---

### **2️⃣ URL Filtering Test**
- From a LAN host, try visiting a **Gambling** or **Adult** website.  
- The browser should display a **block page**.  
- Confirm entries under **Monitor → URL Filtering**.

🖼 *Screenshot:* `screenshots/url-filter-block.png`

---

### **3️⃣ WildFire and File Blocking Test**
- Attempt to upload a suspicious or compressed file.  
- The file should be submitted to **WildFire** for analysis (if enabled).  
- Confirm entries under **Monitor → WildFire Submissions**.

🖼 *Screenshot:* `screenshots/wildfire-submission.png`

---

## ✅ Step 6: Verification & Monitoring

### **CLI Validation**
```bash
show running security-policy
show threat id all
show wildfire status

