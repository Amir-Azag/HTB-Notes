# Opening Moves: The Theory of Password Protection

## The Security Trinity: Authentication, Authorization, and Accountability

In the digital battlefield, security boils down to three foundational principles: **Authentication**, **Authorization**, and **Accountability**. Understanding and mastering these concepts is the key to securing your systems.

---

### 1. Authentication: Prove You Are Who You Claim to Be

Authentication is the gatekeeper of security. It’s about verifying identity before granting access.

#### Types of Authentication:
1. **Knowledge-based (Something You Know):**
   - Passwords, PINs, security questions.
   - Example: Entering a PIN at an ATM.

2. **Possession-based (Something You Have):**
   - Physical tokens, security keys, ID cards.
   - Example: Using a YubiKey for 2FA.

3. **Biometric-based (Something You Are):**
   - Fingerprints, facial recognition, iris scans.
   - Example: Unlocking your phone with Face ID.

#### Multi-Factor Authentication (MFA):
- Combines two or more authentication methods.
- Example: Logging into a bank account using a password (knowledge) and a text message code (possession).

**Key Insight:** The strength of authentication lies in diversity. Relying on just one factor is a security risk.

---

### 2. Authorization: Define What You’re Allowed to Do

Once authenticated, the system determines what resources you can access. Think of it as role-based access control (RBAC).

#### Real-World Example:
- A bank teller can access customer accounts but cannot modify core banking software.

#### Common Strategies:
- **Role-Based Access Control (RBAC):** Assign permissions based on roles (e.g., admin, user).
- **Attribute-Based Access Control (ABAC):** Access is granted based on attributes like location, time, or device type.

---

### 3. Accountability: Keep Track of What Happens

Accountability ensures that actions are logged and traceable. Without accountability, security incidents are harder to diagnose.

#### Essential Components:
- **Audit Logs:** Record every login attempt, file access, and configuration change.
- **Non-Repudiation:** Ensure actions cannot be denied (e.g., using digital signatures).

---

# Common Password Vulnerabilities: The Achilles’ Heel of Security

Passwords are often the weakest link in the security chain. Here’s why:

### 1. Weak Passwords:
- Examples: `123456`, `password`, `qwerty`.
- These are easily guessable and are the first to be cracked in brute-force attacks.

### 2. Password Reuse:
- Studies show 66% of users reuse passwords across multiple accounts.
- Problem: A breach on one platform compromises all linked accounts.

### 3. Post-Breach Inaction:
- 55% of users continue using passwords exposed in breaches.
- This is akin to leaving your front door key under the welcome mat after a burglary.

---

# The Strategic Counter: How to Fortify Passwords

### **1. Use Password Managers**
- Generate and store complex passwords.
- Example tools: LastPass, Bitwarden, Dashlane.

### **2. Enforce Complexity Rules**
- Minimum length (e.g., 12 characters).
- Include uppercase, lowercase, numbers, and special symbols.
- Avoid dictionary words and predictable patterns.

### **3. Adopt Passwordless Solutions**
- Biometric authentication (e.g., Windows Hello).
- Public Key Infrastructure (e.g., FIDO2).

**Pro Tip:** Educate users about phishing to ensure strong passwords aren’t willingly handed over.

---

# The Playbook: Password Storage Mechanics

Passwords must never be stored in plaintext. Instead, use secure hashing algorithms.

---

### Linux Credential Storage
- **Location:** `/etc/shadow`
- **Hash Algorithms:**
  - **MD5 ($1$):** Obsolete, vulnerable to rainbow tables.
  - **SHA-256 ($5$):** Balanced in speed and security.
  - **Yescrypt ($y$):** Modern, resistant to brute-force attacks.

**Security Tip:** Ensure `/etc/shadow` permissions are correctly configured (`root:root`, `640`).

---

### Windows Credential Storage
- **SAM Database:** Located at `%SystemRoot%\system32\config\SAM`.
- **NTDS.dit:** Stores domain credentials.
- **Credential Manager:** Stores cached credentials in `Vault/Credentials`.

**Tools for Forensic Analysis:**
- **reg.exe:** Access Windows registry for SAM file data.
- **secretsdump.py:** Extract NTDS.dit contents remotely.

---

# The Strategic Attack: Cracking Passwords

Password cracking is a combination of brute-force attempts, educated guesses, and exploiting vulnerabilities in hashing algorithms.

---

### Tools of the Trade

1. **John the Ripper (JTR):**
   - Versatile tool for password cracking.
   - Modes: Single, Wordlist, Incremental.
   - Example:
     ```bash
     john --format=<hash_type> <hash_file>
     ```

2. **Hashcat:**
   - GPU-powered password cracker.
   - Supports rule-based attacks.
   - Example:
     ```bash
     hashcat -m <mode> <hash_file> <wordlist>
     ```

3. **Hydra:**
   - Network protocol brute-forcing (SSH, SMB, RDP).
   - Example:
     ```bash
     hydra -L user.list -P pass.list ssh://<IP>
     ```

4. **Rainbow Tables:**
   - Precomputed hash-to-plaintext mappings.
   - Trade-off: Storage space for cracking speed.

---

### Strategic Plays: Optimize Cracking
- Use tailored wordlists like `rockyou.txt`.
- Combine brute-force with mutation rules for efficiency.
- Leverage GPU acceleration with tools like Hashcat.

---

# Credential Storage: Treasure Troves for Hackers

### Linux Secrets
- **Critical Files:**
  - `/etc/passwd`: Contains user account info.
  - `/etc/shadow`: Stores hashed passwords.

**Common Vulnerability:** Misconfigured permissions on `/etc/shadow`.

---

### Windows Secrets
- **Key Files:**
  - SAM Database: Stores local account hashes.
  - NTDS.dit: Domain controller’s master file.

**Tools for Access:**
- **Mimikatz:** Extract credentials from memory.
- **CrackMapExec:** SMB/NTDS dumping.

---

# Network Services: Exploiting Authentication Mechanisms

### Common Authentication Protocols
1. **SMB:** File sharing and directory services.
2. **SSH:** Secure shell for remote access.
3. **RDP:** Graphical remote desktop access.
4. **WinRM:** Remote PowerShell management.

---

### Exploitation Tools
1. **CrackMapExec:**
   - Swiss Army tool for SMB and WinRM.
   - Example:
     ```bash
     crackmapexec smb <IP> -u <user> -p <password>
     ```

2. **Evil-WinRM:**
   - Exploit remote PowerShell endpoints.
   - Example:
     ```bash
     evil-winrm -i <IP> -u <user> -p <password>
     ```

---

# Advanced Moves: Enhancing Password Cracking

### Password Mutations
- Transform weak passwords into strong guesses:
  - Example mutations: `Password2023!`, `P@ssw0rd123`.
- Automate with Hashcat mutation rules.

---

### LSA Secrets Extraction
- Dump sensitive credentials stored in memory:
  ```bash
  crackmapexec smb <IP> --lsa -u <user> -p <password>
