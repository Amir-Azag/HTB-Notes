# Pivoting, Tunneling, and Port Forwarding

## Introduction to Pivoting, Tunneling, and Port Forwarding

### Overview
During a **red team engagement**, penetration test, or Active Directory assessment, you might gain access to credentials, SSH keys, hashes, or access tokens. However, these may not provide direct access to other hosts. In such cases, you can use a **pivot host** to move to other targets in previously unreachable network segments.

Key actions when landing on a host for the first time:
1. Check privilege level.
2. Analyze network connections.
3. Look for VPNs or remote access software.
4. Identify multiple network adapters (for access to different segments).

### Definitions
- **Pivoting**: Moving to other networks through a compromised host to discover and target more systems.
- **Tunneling**: Encapsulating network traffic into another protocol to route it securely through the network.
- **Lateral Movement**: Expanding access horizontally across hosts and services to escalate privileges.

---

## Common Terms
- **Pivot Host**: The compromised host used for network access.
- **Proxy**: A server routing traffic on behalf of another device.
- **Foothold**: Initial access point to a system.
- **Beach Head System**: The first point of compromise in a network.
- **Jump Host**: A system used to connect to a separate network.

---

## Examples of Key Techniques

### Lateral Movement
- Expanding access to hosts, applications, and services within the same network.
- Often involves privilege escalation and domain resource access.
- **Example**:
  - Gain initial access to a target environment using local admin credentials.
  - Perform a network scan and find three more Windows hosts.
  - Use the same credentials to compromise another device, expanding domain access.

---

### Pivoting
- Utilizing multiple hosts to cross network boundaries, often to target isolated environments.
- Focuses on targeted movement deeper into a network.
- **Example**:
  - Compromise a dual-homed engineering workstation with access to both enterprise and operational networks.
  - Use this system to bridge network segments and access sensitive resources.

---

### Tunneling
- Obfuscating traffic by encapsulating it within another protocol to avoid detection.
- Often used for:
  - **Command & Control (C2)**: Masking traffic between an attacker’s server and the victim system.
  - **Data Exfiltration**: Sneaking data out of a target network.
  - **Payload Delivery**: Delivering malicious files or instructions.
- **Example**:
  - Craft HTTP/HTTPS traffic to appear as legitimate GET and POST requests.
  - Malformed packets redirect to a legitimate website to mislead defenders.

---

## Key Takeaways
- **Lateral Movement**: Broadens access across hosts and services in a network.
- **Pivoting**: Focuses on accessing deeper, isolated environments.
- **Tunneling**: Hides malicious activity to maintain persistence and evade detection.

---

## Related Techniques and Tools
### Networking Concepts Behind Pivoting
1. **Dynamic Port Forwarding with SSH**:
   - Use SOCKS5 proxy to route traffic through a compromised system.
2. **Remote/Reverse Port Forwarding**:
   - Open connections back to the attacker's system using SSH or Meterpreter.
3. **DNS Tunneling**:
   - Use tools like `dnscat2` to tunnel traffic over DNS.

### Tools for Advanced Pivoting
- **Socat**:
  - Redirect reverse or bind shells through compromised hosts.
- **SSHuttle**:
  - Simplifies network access by tunneling through SSH.
- **Chisel**:
  - Lightweight SOCKS5 tunneling for proxying connections.
- **Rpivot**:
  - HTTP/S-based pivoting for web server environments.

---

## Practical Use Cases
1. **Gaining Access to Isolated Networks**:
   - Use compromised dual-homed hosts to traverse network boundaries.
2. **Hiding C2 Traffic**:
   - Obfuscate malicious communications using HTTPS or SSH tunneling.
3. **Data Exfiltration**:
   - Tunnel sensitive files through HTTP or DNS without detection.

---