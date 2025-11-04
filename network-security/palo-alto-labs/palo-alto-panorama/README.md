---

## 🧩 Phase 2 — Template Stack & VPN Validation ✅

### 🎯 Objective
Establish a centralized configuration and control framework in **Panorama** for multiple Palo Alto firewalls, integrating global settings, site-specific templates, and VPN communication between FW188 (HQ) and FW189 (Branch).

This phase focuses on:
- Building and applying **Template & Template Stacks**
- Deploying **Site-to-Site VPN** configurations via Panorama
- Validating successful **commit**, **push**, and **tunnel establishment**

---

### 🧱 Template Hierarchy & Global Configuration

| Screenshot | Description |
|:------------|:-------------|
| ![Template Hierarchy](screenshots/template-hierarchy.png) | Global and site-specific templates created for centralized management. |
| ![FW188 Stack](screenshots/template-stack-fw188.png) | Template stack for FW188 combining Global Template and site configuration. |
| ![FW189 Stack](screenshots/template-stack-fw189.png) | Template stack for FW189 combining Global Template and site configuration. |
| ![Syslog Profile](screenshots/syslog-profile-global.png) | Global syslog server profile applied to all managed devices. |

---

### 🌐 Network & Routing Configuration

| Screenshot | Description |
|:------------|:-------------|
| ![FW188 Interfaces](screenshots/fw188-interfaces.png) | FW188 interface and zone configuration via Panorama. |
| ![FW189 Interfaces](screenshots/fw189-interfaces.png) | FW189 interface and zone configuration via Panorama. |
| ![FW188 VR](screenshots/firewall188-virtual-router.png) | Virtual Router configuration for FW188 including static and default routes. |
| ![FW189 VR](screenshots/firewall189-virtual-router.png) | Virtual Router configuration for FW189 with VPN route entries. |

---

### 🔐 VPN Connectivity Validation

| Screenshot | Description |
|:------------|:-------------|
| ![IKE SA](screenshots/show-vpn-ike-sa.png) | IKE SA established between FW188 ↔ FW189 confirming Phase 1 success. |
| ![IPSec SA](screenshots/show-vpn-ipsec-sa.png) | IPSec tunnel established, traffic encryption confirmed for Phase 2. |

---

### ✅ Commit & Device Sync Verification

| Screenshot | Description |
|:------------|:-------------|
| ![Commit Success](screenshots/commit-success.png) | Successful commit and push operation from Panorama. |
| ![Device Summary](screenshots/panorama-managed-devices-summary-sync-status.png) | Both firewalls connected and in-sync with Panorama. |

---

### 🧠 Lessons Learned
- Using **template variables** simplifies interface and IP reuse between multiple firewalls.
- The **Global Template** is ideal for shared services (DNS, NTP, Syslog, Panorama).
- VPN configs (IKE/IPSec, routes, zones) belong in the **site-specific templates** to avoid overlapping objects.
- A successful **Phase 1 (IKE)** and **Phase 2 (IPSec)** verify both communication and encryption readiness.

---

### 🧩 Verification Commands
```bash
> show devices all
> show config pushed-summary
> show vpn ike-sa
> show vpn ipsec-sa

