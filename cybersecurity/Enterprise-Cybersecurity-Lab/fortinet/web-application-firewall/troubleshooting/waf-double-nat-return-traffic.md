# WAF Connectivity Issue – Double NAT Return Traffic

## Summary

During the deployment of a FortiWeb Web Application Firewall (WAF) within the
Enterprise Cybersecurity Lab (ECL), external access to multiple published web
applications failed after the WAF was placed inline.

Although firewall and WAF policies were permitting traffic, client connections
to the public VIPs consistently timed out. The issue was ultimately traced to
source NAT behavior on the edge router, which was altering return traffic for
public VIP addresses and breaking TCP session state.

---

## Initial Symptoms

After completing the FortiWeb configuration and integrating it behind the
FortiGate VIPs, access to all published applications stopped working.

Attempts to browse to the following public IPs:

- http://203.0.114.100  
- http://203.0.114.101  
- http://203.0.114.102  
- http://203.0.114.103  

consistently resulted in **ERR_CONNECTION_TIMED_OUT** in the browser.

No HTTP error pages were returned, and the connections failed silently without
any visible application-level response.

---

## What Was Verified

The initial focus was to rule out policy-related blocks.

On the FortiGate:
- Firewall logs showed traffic from the public VIPs being allowed.
- No deny actions or security policy drops were observed.

On the FortiWeb:
- Logs confirmed that traffic was reaching the virtual servers.
- Requests were being allowed by WAF policies.
- No WAF enforcement actions were triggered.

At this point, both the NGFW and WAF appeared to be functioning correctly, yet
client connections were still failing.

---

## Packet-Level Observations

Multiple packet captures were taken at different points in the traffic path,
including the FortiGate, FortiWeb, and edge router.

A consistent TCP pattern emerged during testing:

1. The client sent a TCP SYN toward the public VIP.
2. The FortiWeb (via the FortiGate) responded with a SYN-ACK.
3. The client immediately replied with a TCP RST.

The reset was originating from the client, not from the firewall or the WAF.

This behavior indicated that the client was receiving a response but rejecting
it as invalid, suggesting a source address or session-state mismatch rather
than a blocked connection or application failure.

---

## Root Cause

Further review showed that the issue was caused by NAT behavior on the edge
router.

The router was configured to perform source NAT for the entire
203.0.114.0/24 network as part of the outbound internet access configuration.
This NAT rule included the public VIP addresses assigned to the FortiGate.

As a result, return traffic sourced from the FortiGate and FortiWeb VIPs was
being translated again at the router. Instead of receiving responses from the
expected VIP source address, the client saw packets sourced from the router’s
outside interface address (172.29.129.253).

This source address mismatch caused the client to reset the TCP session,
resulting in the observed SYN → SYN-ACK → RST behavior.

---

## Resolution

To resolve the issue, the router NAT configuration was updated to exclude the
FortiGate VIP addresses from source NAT.

The existing NAT access list used for outbound internet traffic was rewritten
to explicitly deny NAT for the following VIPs:

- 203.0.114.100
- 203.0.114.101
- 203.0.114.102
- 203.0.114.103

All other internal networks continued to be NAT’d normally for internet access.

After applying the updated ACL and clearing existing NAT translations, external
access to the published applications through the WAF was immediately restored.
Browser connections completed successfully without client-side resets.

---

## Lessons Learned

When deploying a WAF behind an NGFW using public VIPs, upstream NAT behavior
must be carefully reviewed. Public-facing VIP addresses should not be included
in general outbound NAT rules, as doing so can alter return traffic and break
TCP session state.

This issue reinforced the importance of validating return paths and preserving
source addresses when introducing additional inspection layers into an
application delivery path.

