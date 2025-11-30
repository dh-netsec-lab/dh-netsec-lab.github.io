# ClearPass Integration Lab
<b>Identity, Authentication, and Access Control across the Enterprise Cybersecurity Lab</b>

The ClearPass section of the Enterprise Cybersecurity Lab demonstrates how identity-driven access control is implemented in an enterprise environment. This includes:

- RADIUS authentication  
- TACACS+ device administration  
- 802.1X endpoint authentication  
- Integration with Active Directory  
- Enforcement policies  
- Logging, analysis, and troubleshooting  

ClearPass acts as the central policy engine for authentication, authorization, and device control across all network equipment in the lab.

<hr>

<h2>Key Capabilities Demonstrated</h2>

<h3>RADIUS Authentication</h3>
Used for 802.1X, Windows 11 testing, and switch-based authentication.

<h3>TACACS+ Device Administration</h3>
Used for secure admin access to network devices (Cali, Bama, NY switches).

<h3>Active Directory Integration</h3>
ClearPass queries users, groups, machine accounts, and roles from AD.

<h3>PKI / Certificates</h3>
Used for secure 802.1X authentication and future EAP-TLS deployment.

<hr>

<h2>ClearPass Services Used in the Lab</h2>

<table>
  <thead>
    <tr>
      <th>Service</th>
      <th>Purpose</th>
      <th>Status</th>
      <th>Link</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>RADIUS_TEST</td>
      <td>Windows 11 802.1X & switch authentication</td>
      <td>Working</td>
      <td>Coming Soon</td>
    </tr>
    <tr>
      <td>ECL_TACACS</td>
      <td>TACACS+ admin login for switches</td>
      <td>Working</td>
      <td>Coming Soon</td>
    </tr>
    <tr>
      <td>RADIUS Generic</td>
      <td>Backup / fallback service</td>
      <td>Working</td>
      <td>Coming Soon</td>
    </tr>
  </tbody>
</table>

<hr>

<h2>Configuration Areas</h2>

<h3>Authentication Sources</h3>
<ul>
  <li>Active Directory (ECL.lab)</li>
  <li>Local User Repository</li>
</ul>

<h3>Enforcement Profiles</h3>
<ul>
  <li>TACACS+ Allow</li>
  <li>TACACS+ Deny</li>
  <li>RADIUS Basic Allow</li>
  <li>RADIUS VLAN Assignment (future)</li>
</ul>

<h3>Device Groups</h3>
<ul>
  <li>Cisco Switches</li>
  <li>Firewalls</li>
  <li>Test endpoints</li>
</ul>

<hr>

<h2>Validation & Testing</h2>

<table>
  <thead>
    <tr>
      <th>Test</th>
      <th>Result</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Switch TACACS+ login</td>
      <td>Success</td>
    </tr>
    <tr>
      <td>Windows 11 RADIUS authentication</td>
      <td>Success</td>
    </tr>
    <tr>
      <td>802.1X EAP testing</td>
      <td>Pending</td>
    </tr>
    <tr>
      <td>Active Directory authentication</td>
      <td>Working</td>
    </tr>
  </tbody>
</table>

<h2>Validation & Testing</h2>
<table>...</table>

<!-- INSERT THE 802.1X BLOCK HERE -->

<h2>Troubleshooting Documentation</h2>
...


<hr>

<h2>Troubleshooting Documentation</h2>

Common issues documented in the lab include:

<ul>
  <li>"User not found in Local User Repository"</li>
  <li>Incorrect NAS-IP-Address</li>
  <li>Dot1x failures on switchports</li>
  <li>Enforcement mismatches</li>
  <li>RADIUS packet analysis</li>
</ul>

The full troubleshooting guide will be available in:  
<code>troubleshooting.md</code>

<hr>

<h2>Navigation</h2>

<p><a href="../index.md">Back to ECL Home</a></p>
<p><a href="../../README.md">Return to Cybersecurity Portfolio Home</a></p>
