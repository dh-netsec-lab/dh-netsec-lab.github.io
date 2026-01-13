# Web Application Firewall (FortiWeb) – Enterprise Cybersecurity Lab

## Overview
This lab documents the deployment and troubleshooting of a Web Application
Firewall (FortiWeb) protecting internet-facing web applications within the
Enterprise Cybersecurity Lab (ECL).

The WAF is deployed behind an NGFW VIP layer and provides Layer 7 inspection,
policy enforcement, and application security controls.

## Architecture

Edge Router → FortiGate VIPs → FortiWeb → Backend Web Applications

This WAF deployment operates within the broader ECL topology and focuses
specifically on application-layer protection and traffic flow validation.

## Validation and Security Posture

This deployment validates correct in-line placement and basic operation of a
Web Application Firewall in front of multiple intentionally vulnerable web
applications within the Enterprise Cybersecurity Lab.

Traffic flow was validated through multiple public VIPs, including applications
listening on standard and non-standard ports. The WAF is operating with a
base/default rule set and is not tuned for application-specific behavior.

At this stage, the WAF provides baseline protection against generic and automated
attacks. The backend applications remain intentionally vulnerable, and advanced
attack techniques, logic-based flaws, and WAF bypass scenarios are considered
out of scope for this lab.

This lab establishes a functional WAF baseline. Future labs will focus on rule
tuning, attack detection, and response validation.



## Troubleshooting
A real-world NAT and return-traffic failure was encountered and resolved
during this deployment.

See:
- [WAF Double-NAT Return Traffic Case Study](troubleshooting/waf-double-nat-return-traffic.md)

