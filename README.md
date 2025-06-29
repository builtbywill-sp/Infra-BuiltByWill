 <h1>🔐🛰️ Infra-BuiltByWill</h1>
  <p>Encrypted. Segmented. Untouchable.<br>
  No leaks. No noise. NSA-tier lockdown — BuiltByWill style.</p>

  <h2>💻 Core Setup</h2>
  <table>
    <tr>
      <th>Layer</th>
      <th>Tech</th>
      <th>Purpose</th>
    </tr>
    <tr>
      <td>Router</td>
      <td>Asus Merlin + WireGuard</td>
      <td>VPN from the source, optional kill switch, router-wide encryption</td>
    </tr>
    <tr>
      <td>DNS</td>
      <td>AdGuard DNS (Encrypted) + LocalBlocklists</td>
      <td>Blocks trackers + malware at DNS level with encryption</td>
    </tr>
    <tr>
      <td>VPN</td>
      <td>ProtonVPN (WireGuard)</td>
      <td>Encrypt outbound traffic and tunnel through secure nodes</td>
    </tr>
    <tr>
      <td>Isolation</td>
      <td>IoT VLANs + Dev VLAN + Guest VLAN</td>
      <td>Network segmentation to keep devices quarantined</td>
    </tr>
  </table>

  <h2>🔑 Access & Security</h2>
  <table>
    <tr>
      <th>Tool</th>
      <th>Use</th>
      <th>Status</th>
    </tr>
    <tr>
      <td>Pass + YubiKey</td>
      <td>Vaulted passwords with physical 2FA</td>
      <td>✅ Implemented</td>
    </tr>
    <tr>
      <td>SSH Key Auth</td>
      <td>No password fallback on CLI</td>
      <td>🧪 Researching</td>
    </tr>
    <tr>
      <td>FIDO2 / WebAuthn</td>
      <td>Passwordless login for secure services</td>
      <td>🔍 Evaluating</td>
    </tr>
    <tr>
      <td>LocalBackups</td>
      <td>Nightly rsync to encrypted drive</td>
      <td>🕓 Next Phase</td>
    </tr>
    <tr>
      <td>Coldmetal Memory</td>
      <td>Offline memory file system for AI continuity</td>
      <td>✅ Linked</td>
    </tr>
  </table>

  <h2>📡 Network Hardening</h2>
  <table>
    <tr>
      <th>Layer</th>
      <th>Hardened Setting</th>
      <th>Status</th>
    </tr>
    <tr>
      <td>Router WAN</td>
      <td>Remote admin disabled</td>
      <td>✅ Enforced</td>
    </tr>
    <tr>
      <td>UPNP + WPS</td>
      <td>Disabled / closed ports</td>
      <td>✅ Locked</td>
    </tr>
    <tr>
      <td>Router Login</td>
      <td>Brute-force lockout or 2FA</td>
      <td>🔍 Planning</td>
    </tr>
    <tr>
      <td>VLAN Firewalls</td>
      <td>No inter-VLAN communication</td>
      <td>🧱 Conceptual</td>
    </tr>
  </table>

  <details>
    <summary>📦 VPN Configuration (Proton + WireGuard)</summary>
    <p>Export the .conf file from ProtonVPN dashboard. Upload to Asus router via VPN Fusion or WireGuard config UI. Set to auto-connect on boot. Use kill switch mode.</p>
    <pre><code>[Interface]
PrivateKey = ...
Address = 10.2.0.2/32
DNS = 10.2.0.1

[Peer]
PublicKey = ...
AllowedIPs = 0.0.0.0/0
Endpoint = ...
    </code></pre>
  </details>

  <details>
    <summary>🛡️ DNS Encryption (Local vs Device-Level)</summary>
    <p>DNS can be encrypted:</p>
    <ul>
      <li>At the router (AdGuard, DoH/DoT config)</li>
      <li>Or at the device level (Proton, AdGuard app)</li>
    </ul>
    <p>Redundancy ensures fallback encryption. Router DNS should default to <code>dns.adguard-dns.com</code> or <code>dns.cloudflare.com</code> (DoH).</p>
  </details>

  <h2>📁 Future Expansions</h2>
  <table>
    <tr>
      <th>Upgrade</th>
      <th>Target</th>
      <th>Status</th>
    </tr>
    <tr>
      <td>Proxmox server</td>
      <td>Run VMs segmented by VLANs</td>
      <td>🚧 Planning</td>
    </tr>
    <tr>
      <td>Dedicated Coldmetal node</td>
      <td>Hardware LLM execution</td>
      <td>🧪 Early phase</td>
    </tr>
    <tr>
      <td>Encrypted relay email</td>
      <td>Custom SMTP + Proton bridge</td>
      <td>🔐 Researching</td>
    </tr>
    <tr>
      <td>Cert Studies</td>
      <td>Security+ / Network+ (Tactical upskill)</td>
      <td>📚 Ongoing</td>
    </tr>
    <tr>
      <td>USBKill / powercut</td>
      <td>Auto power-down on tamper</td>
      <td>🧠 Conceptual</td>
    </tr>
  </table>
