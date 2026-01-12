# Web Application Firewall (FortiWeb) – Enterprise Cybersecurity Lab

## Overview
This lab documents the deployment and troubleshooting of a Web Application
Firewall (FortiWeb) protecting internet-facing web applications within the
Enterprise Cybersecurity Lab (ECL).

The WAF is deployed behind an NGFW VIP layer and provides Layer 7 inspection,
policy enforcement, and application security controls.

## Architecture
Edge Router → FortiGate VIPs → FortiWeb → Backend Web Applications

## Troubleshooting
A real-world NAT and return-traffic failure was encountered and resolved
during this deployment.

See:
- [WAF Double-NAT Return Traffic Case Study](troubleshooting/waf-double-nat-return-traffic.md)

