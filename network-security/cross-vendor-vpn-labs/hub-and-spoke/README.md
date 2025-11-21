# 🏢 Enterprise Cybersecurity Lab  
## 🔐 Hub-and-Spoke VPN + Centralized DHCP Case Study  
### (Bama Hub – NY Spoke – Cali Spoke)

This lab demonstrates a production-grade **hub-and-spoke VPN architecture** between three sites (Bama, NY, and Cali) using **Fortinet + Palo Alto firewalls**, with **centralized DHCP services** routed securely across IPSec tunnels.

---

# 🖼️ Topology Diagram (ASCII)

```
                         ┌───────────────────────────────┐
                         │     Bama Hub – Fortinet        │
                         │   --------------------------    │
                         │   Role: Central Hub             │
                         │   Networks:                     │
                         │      • 10.0.2.0/24 (Users)      │
                         │      • 10.0.3.0/24 (Servers/DC) │
                         └───────────────────────────────┘
                                      /        \
                                     /          \
                                    /            \
                                   /              \
                                  /                \
                                 /                  \
                                /                    \
                               /                      \
              ┌────────────────────────┐     ┌────────────────────────┐
              │   NY Spoke – Palo Alto │     │ Cali Spoke – Fortinet  │
              │  --------------------- │     │ ----------------------- │
              │  Role: Spoke           │     │ Role: Spoke            │
              │  Network:              │     │ Network:               │
              │    • 10.0.33.0/24      │     │   • 10.0.64.0/24       │
              └────────────────────────┘     └────────────────────────┘
```

---

# 📸 Screenshot Evidence

(Your screenshots section here)

---

# 🧪 Connectivity Verification

(Your connectivity tests here)

---

# 🛠 Troubleshooting Notes

(Your notes here)

---

# 🎓 Lessons Learned

(Your lessons here)

---

# 💼 Skills Demonstrated

(Your summary here)

