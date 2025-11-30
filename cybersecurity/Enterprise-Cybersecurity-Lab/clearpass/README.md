# ClearPass Integration Lab

**Identity, Authentication, and Access Control across the Enterprise
Cybersecurity Lab**

The ClearPass section of the Enterprise Cybersecurity Lab demonstrates
how identity-driven access control is implemented in an enterprise
environment. This includes:

-   RADIUS authentication
-   TACACS+ device administration
-   802.1X endpoint authentication
-   Integration with Active Directory
-   Enforcement policies
-   Logging, analysis, and troubleshooting

ClearPass acts as the central policy engine for authentication,
authorization, and device control across all network equipment in the
lab.

## Key Capabilities Demonstrated

### RADIUS Authentication

Used for 802.1X, Windows 11 testing, and switch-based authentication.

### TACACS+ Device Administration

Used for secure admin access to network devices (Cali, Bama, NY
switches).

### Active Directory Integration

ClearPass queries users, groups, machine accounts, and roles from AD.

### PKI / Certificates

Used for secure 802.1X authentication and future EAP-TLS deployment.

------------------------------------------------------------------------

## ClearPass Services Used in the Lab

  ------------------------------------------------------------------------
  Service            Purpose              Status             Link
  ------------------ -------------------- ------------------ -------------
  RADIUS_TEST        Windows 11 802.1X &  Working            Coming Soon
                     switch                                  
                     authentication                          

  ECL_TACACS         TACACS+ admin login  Working            Coming Soon
                     for switches                            

  RADIUS (Generic)   Backup/fallback      Working            Coming Soon
                     service                                 
  ------------------------------------------------------------------------

------------------------------------------------------------------------

## Configuration Areas

### Authentication Sources

-   Active Directory (ECL.lab)
-   Local User Repository

### Enforcement Profiles

-   TACACS+ Allow
-   TACACS+ Deny
-   RADIUS Basic Allow
-   RADIUS VLAN Assignment (future)

### Device Groups

-   Cisco Switches
-   Firewalls
-   Test endpoints

------------------------------------------------------------------------

## Validation & Testing

  Test                               Result
  ---------------------------------- ---------
  Switch TACACS+ login               Success
  Windows 11 RADIUS authentication   Success
  802.1X EAP testing                 Pending
  Active Directory authentication    Working

------------------------------------------------------------------------

## Troubleshooting Documentation

Common issues documented in the lab:

-   "User not found in Local User Repository"
-   Incorrect NAS-IP-Address
-   Dot1x failures on switchports
-   Enforcement mismatches
-   RADIUS packet analysis

Full troubleshooting guide will be available here: `troubleshooting.md`

------------------------------------------------------------------------

## Navigation

[Back to ECL Home](../index.md)\
[Return to Cybersecurity Portfolio Home](../../README.md)
