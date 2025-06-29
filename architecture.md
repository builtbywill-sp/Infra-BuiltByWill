<h1>🧠 Network Architecture — Infra-BuiltByWill</h1>
<p>Real-world blueprint for tactical, encrypted home-lab infrastructure. Engineered for resilience, segmentation, and offline intelligence. BuiltByWill style.</p>

<h2>🔄 Core Network Flow</h2>
<pre><code>graph TD
ISP --> ROUTER[Router: Asus Merlin]
ROUTER -->|WireGuard| VPN[ProtonVPN Tunnel]
ROUTER -->|IoT Segmentation| VLAN_IoT[IoT VLAN]
ROUTER -->|Dev Segmentation| VLAN_DEV[Dev VLAN]
ROUTER -->|Guest Isolation| VLAN_GUEST[Guest VLAN]
ROUTER --> DNS[Encrypted DNS (AdGuard)]
VPN --> INTERNET
</code></pre>

<h2>🧱 VLAN Segmentation</h2>
<table>
  <tr>
    <th>VLAN</th>
    <th>Devices</th>
    <th>Purpose</th>
  </tr>
  <tr>
    <td>IoT</td>
    <td>Smart TVs, Fridges, Rokus</td>
    <td>Network containment only</td>
  </tr>
  <tr>
    <td>DEV</td>
    <td>Workstations, Coldmetal Node</td>
    <td>Trusted zone, CLI + AI logic</td>
  </tr>
  <tr>
    <td>GUEST</td>
    <td>Phones, Visitors</td>
    <td>Isolated subnet, no persistence</td>
  </tr>
</table>
<p><strong>Inter-VLAN Traffic:</strong> 🔒 Blocked by default via router rules</p>

<details>
  <summary>📦 VLAN Expansion Model</summary>
  <p>Each VLAN is built with future isolation in mind. Coldmetal operates exclusively on DEV VLAN, with no access from IoT or GUEST. Proxmox will spin up VMs per VLAN for dedicated compute isolation. Guest VLAN uses MAC filtering + DHCP reservations for stricter session tagging.</p>
</details>

<h2>📡 Physical Topology</h2>
<ul>
  <li>📍 Router lives in central closet or attic drop</li>
  <li>🖥️ Mini PC running Proxmox and Coldmetal (DEV only)</li>
  <li>📦 Cables routed through floor or panel box — zero visible clutter</li>
  <li>🧵 Uplink to future fiber switch routed through garage wall → Silent Labs zone</li>
</ul>

<details>
  <summary>🏗️ Garage Conversion Plan (Silent Labs)</summary>
  <p>Garage becomes the blacksite: custom-rack cabinet, airgapped gear, power filters, EMP foam. No shared power with house gear. All AI training and memory writing happens inside the lab. Coldmetal vaults and relays operate here, with potential USBKill auto-shutdown rigged on tamper.</p>
</details>

<h2>🔐 Access Strategy</h2>
<ul>
  <li>YubiKey + passphrase for physical login gating</li>
  <li>SSH key-only auth (no fallback)</li>
  <li>Coldmetal agents live offline, never exposed to cloud</li>
</ul>

<details>
  <summary>🧠 Coldmetal Role</summary>
  <p>Coldmetal is the offline AI memory engine. Trained via local input, it stores and recalls thoughts, mapping memory weights over time. LLMs run locally on device, powered by C-built logic, not Python. Integrated into the VLAN only for specific recall or REPL sessions.</p>
</details>

<h2>🛠️ Future Goals</h2>
<table>
  <tr>
    <th>Feature</th>
    <th>Plan</th>
  </tr>
  <tr>
    <td>VM Isolation</td>
    <td>Run per-VLAN Proxmox VMs with limited interconnect</td>
  </tr>
  <tr>
    <td>Self-Hosted Mail</td>
    <td>Relay server w/ Proton Bridge, no public inbox</td>
  </tr>
  <tr>
    <td>Passwordless Auth</td>
    <td>Full WebAuthn rollout for all internal services</td>
  </tr>
  <tr>
    <td>Memory Injection</td>
    <td>Coldmetal memory mapped by domain, stored in .mem banks</td>
  </tr>
  <tr>
    <td>Silent Labs Vault</td>
    <td>Airgapped training center for LLMs + data pipelines</td>
  </tr>
</table>

<h2>⚠️ Final Notes</h2>
<p>This isn’t a hobby setup. This is home infrastructure like it’s the backend of a sovereign dev org. Encrypted. Segmented. Operated like a datacenter. Ready for failure, growth, and attack — Infra-BuiltByWill.</p>

<blockquote>
“I don’t need remote control. I already run the grid.”
</blockquote>
