---
layout: default
title: Test Home
---

<style>
    body {
        font-family: Arial, sans-serif;
        background-color: #f5f7fa;
        margin: 0;
        padding: 0;
        color: #333;
    }
    header {
        background: #0d1117;
        color: #fff;
        padding: 40px 20px;
        text-align: center;
    }
    h1 {
        margin: 0;
        font-size: 2.4rem;
    }
    h2 {
        margin-top: 40px;
        margin-bottom: 10px;
        font-size: 1.6rem;
        color: #0d1117;
    }
    p {
        line-height: 1.6;
    }
    .container {
        width: 90%;
        max-width: 900px;
        margin: auto;
        padding-bottom: 60px;
    }
    .card-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
        gap: 20px;
        margin-top: 20px;
    }
    .card {
        background: white;
        padding: 20px;
        border-radius: 10px;
        box-shadow: 0 2px 8px rgba(0,0,0,0.1);
        border-left: 5px solid #0d6efd;
    }
    .card h3 {
        margin-top: 0;
    }
    a.button {
        display: inline-block;
        padding: 10px 16px;
        margin-top: 10px;
        background: #0d6efd;
        color: white;
        text-decoration: none;
        border-radius: 6px;
    }
    ul li a {
        color: #0d6efd;
    }
    footer {
        text-align: center;
        margin-top: 40px;
        padding: 20px;
        background: #e9ecef;
    }
    .note {
        font-size: 0.9rem;
        color: #555;
    }
</style>

<header>
    <h1>DH NetSec Lab – Professional Portfolio</h1>
    <p>Enterprise Cybersecurity Lab (ECL) · Network Security · SOC & SIEM</p>
</header>

<div class="container">

    <h2>⭐ Featured Labs</h2>

    <div class="card-grid">

        <div class="card">
            <h3>Palo Alto Networks Lab Series</h3>
            <p>Enterprise firewall deployment with Panorama, site-to-site VPN, security profiles, and best practices.</p>
            <a class="button" href="/network-security/palo-alto-labs/">View Palo Alto Labs</a>
        </div>

        <div class="card">
            <h3>Hub-and-Spoke VPN & Centralized DHCP</h3>
            <p>Fortinet + Palo Alto hub-and-spoke IPSec design with centralized DHCP, routing, and verification.</p>
            <a class="button" href="/cybersecurity/Enterprise-Cybersecurity-Lab/siem/vpn-hub-and-spoke-lab/">View VPN Case Study</a>
        </div>

        <div class="card">
            <h3>Identity & Trust Integration</h3>
            <p>Active Directory, DNS, certificates, and foundation for NAC & SSL decryption.</p>
            <a class="button" href="/cybersecurity/Enterprise-Cybersecurity-Lab/identity-trust/">View Identity Labs</a>
        </div>

        <div class="card">
            <h3>SOC / SIEM Pipeline & Threat Detection</h3>
            <p>Suricata, Zeek, Wazuh, Sysmon, and Splunk working together to provide security visibility.</p>
            <a class="button" href="/cybersecurity/Enterprise-Cybersecurity-Lab/siem/">Enter SOC / SIEM Labs</a>
        </div>

    </div>

    <h2>🏢 Enterprise Cybersecurity Lab (ECL)</h2>
    <p>
        The ECL is a multi-site, multi-vendor enterprise lab built to simulate a real-world environment with
        hub-and-spoke VPN, centralized identity, full SOC visibility, and layered defenses. From this environment
        you can drill into each phase: connectivity, telemetry, identity, threat detection, and GRC.
    </p>
    <a class="button" href="/cybersecurity/Enterprise-Cybersecurity-Lab/">Enter ECL Overview</a>

    <h2>🚀 Quick Navigation</h2>
    <ul>
        <li><a href="/cybersecurity/Enterprise-Cybersecurity-Lab/">Enterprise Cybersecurity Lab (ECL Overview)</a></li>
        <li><a href="/cybersecurity/Enterprise-Cybersecurity-Lab/siem/">SOC / SIEM & Threat Detection Labs</a></li>
        <li><a href="/network-security/palo-alto-labs/">Palo Alto Networks Lab Series</a></li>
    </ul>

    <h2>🔐 Network Security</h2>
    <p>
        The Network Security track focuses on firewall architecture, segmentation, VPN design, and secure connectivity.
        Current content is centered on Palo Alto Networks, with Fortinet-focused labs planned as a separate series.
    </p>
    <p class="note">
        Fortinet lab series is in progress and will be added as its own section once published.
    </p>

    <h2>🛡 Cybersecurity / SOC Labs</h2>
    <p>
        The Cybersecurity labs highlight end-to-end visibility: network IDS, endpoint telemetry, log aggregation,
        and SIEM correlation inside the Enterprise Cybersecurity Lab.
    </p>
    <a class="button" href="/cybersecurity/Enterprise-Cybersecurity-Lab/siem/">Explore SOC / SIEM Labs</a>

    <h2>📫 Contact</h2>
    <p>
        Email: <strong>dh-netsec-lab@gmail.com</strong><br>
        LinkedIn: <a href="https://www.linkedin.com/in/derrickhervey" target="_blank">linkedin.com/in/derrickhervey</a>
    </p>

</div>

<footer>
    <p>© 2025 DH NetSec Lab — Professional Portfolio</p>
</footer>
