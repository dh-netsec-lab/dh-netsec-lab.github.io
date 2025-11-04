## 🍀 Phase 2 – Template Stack & VPN Validation ✅

### 🎯 Objective
Establish a centralized configuration and control framework in **Panorama** for multiple Palo Alto firewalls, integrating global and site-specific templates for scalable management.

This phase focuses on:

- Building and applying **Template & Template Stacks**
- Deploying **Site-to-Site VPN** configurations via Panorama
- Validating successful **commit**, **push**, and **tunnel establishment**

---

### 🧱 Configuration Overview
| Component | Description |
|------------|-------------|
| **Panorama Templates** | Centralized configuration objects (DNS, NTP, Syslog, Panorama Servers, etc.) applied globally |
| **Device Templates** | Site-specific configurations (zones, interfaces, routes, VPN profiles) for each firewall |
| **Template Stacks** | Combined global + site templates applied to the managed firewalls |
| **Managed Devices** | FW188 and FW189 (Panorama-managed Palo Alto VM-Series Firewalls) |

---

### 🧩 Implementation Steps
1. **Create Global Template**
   - Add DNS, NTP, Syslog, and Panorama Server profiles.  
   - Confirm sync status ✔️ in **Panorama > Managed Devices**.

2. **Create Site-Specific Templates**
   - Configure **Zones**, **Interfaces**, **Virtual Routers**, and **VPN profiles** for FW188 and FW189.  
   - Include static and default routes.

3. **Build Template Stacks**
   - Combine the **Global Template** with each site-specific template.  
   - Verify **template hierarchy** is correct.

4. **Push Configuration to Firewalls**
   - Commit changes to Panorama.  
   - Push configuration to FW188 and FW189.  
   - Verify **commit-success** in logs.

5. **Validate VPN Establishment**
   - Use CLI:  
     ```
     show vpn ike-sa
     show vpn ipsec-sa
     ```
   - Confirm both IKE and IPSec SAs are up ✅.

---

### 🖼️ Screenshots
| Screenshot | Description |
|-------------|-------------|
| `commit-success.png` | Panorama commit confirmation |
| `fw188-interfaces.png` | FW188 interface configuration |
| `fw189-interfaces.png` | FW189 interface configuration |
| `firewall188-virtual-router.png` | FW188 routing overview |
| `firewall189-virtual-router.png` | FW189 routing overview |
| `show-vpn-ike-sa.png` | Phase 1 IKE SA validation |
| `show-vpn-ipsec-sa.png` | Phase 2 IPSec SA validation |
| `syslog-profile-global.png` | Global Syslog profile settings |
| `panorama-managed-devices-summary-sync-status.png` | Device sync status |
| `template-hierarchy.png` | Global vs Site Template hierarchy |
| `template-stack-fw188.png` | FW188 Template Stack |
| `template-stack-fw189.png` | FW189 Template Stack |

---

### ✅ Verification Checklist
- [x] Global Template created and applied  
- [x] Site Templates created for FW188 and FW189  
- [x] Template Stacks built and linked  
- [x] Configuration committed and pushed successfully  
- [x] IKE and IPSec SAs established  
- [x] Syslog messages forwarded to Rsyslog/Splunk

---

### 🔗 Return to Lab Index
[← Back to Network-Security Portfolio Index](../index.md)
