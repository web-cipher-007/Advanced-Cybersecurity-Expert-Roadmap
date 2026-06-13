# Complete Red Teaming Roadmap

---

## 🛠️ Phase 1: Core Active Directory (AD) & Windows Internals
*Before launching attacks, you must understand how Windows enterprises manage authentication and identity.*

### Core Concepts to Master
*   **Authentication Protocols**: Learn exactly how **Kerberos** (Tickets, SPNs, AS-REQ, TGS/TGT) and **NTLM** (NetNTLMv1/v2, hashes) work.
*   **AD Objects & Architecture**: Understand Domains, Forests, Trees, Trust Relationships, Group Policy Objects (GPOs), Organizational Units (OUs), and Access Control Lists (ACLs).
*   **AD Certificate Services (ADCS)**: Understand how enterprises handle internal PKI (Public Key Infrastructure) and certificates.

### Primary Attack Vectors
*   **Credential Theft & Harvesting**: LLMNR/NBT-NS Poisoning (using Responder), SAM/LSA database dumping, and extracting cleartext credentials from LSASS memory.
*   **Kerberos Exploitation**: **Kerberoasting** (targeting service accounts) and **AS-REP Roasting** (targeting accounts without pre-authentication required).
*   **Lateral Movement**: Pass-the-Hash (PtH), Pass-the-Ticket (PtT), and Overpass-the-Hash using tools like **Impacket**.
*   **Domain Dominance**: Creating Golden and Silver Tickets, and exploiting Active Directory object misconfigurations (GenericAll, WriteDacl) via **BloodHound**.

### Best Free Training Resources
*   **Video Course**: *Practical Ethical Hacking (Active Directory Section)* by TCM Security on YouTube.
*   **Reference Libraries**: **The Hacker Recipes** and **HackTricks (Windows / AD section)**.

---

## 🖥️ Phase 2: Building Your Hands-On Range (Self-Hosted Lab)
*You cannot master network exploitation by reading books. You must build and break an enterprise network locally.*

### The Lab Assignment: Game of Active Directory (GOAD)
*   **What it is**: A free, open-source vulnerable laboratory consisting of multiple domains, forests, and built-in misconfigurations.
*   **Setup Requirements**: A computer with at least 16GB RAM (32GB preferred) and a multi-core CPU. 
*   **Deployment**: Install **VirtualBox** and **Vagrant** on your machine. Clone the GOAD GitHub repository and run the setup scripts to automatically spin up your Windows Server instances.

### Your Objective inside GOAD
*   Map the network from a standard unprivileged user workstation using **BloodHound**.
*   Execute a complete attack chain: From initial low-level user compromise, to lateral movement across domains, to extracting the `NTDS.dit` database to achieve Full Domain Controller Administrator rights.

---

## 🔀 Phase 3: Modern Network Pivoting & Post-Exploitation
*In a real red team engagement, you cannot access internal servers directly from the internet. You must pivot through compromised systems.*

### Core Concepts to Master
*   **Pivoting Architecture**: SOCKS Proxies, Port Forwarding (Remote and Local), and Routing Tunnels.
*   **Firewall & Egress Evasion**: Learning how to wrap malicious traffic inside allowed protocols like HTTP, HTTPS, or DNS to bypass network restrictions.

### Tooling to Master
*   **Ligolo-ng**: The gold standard tool for modern red teamers. It establishes a multi-platform tunnel that lets you route tools directly through an interface like a standard VPN.
*   **Chisel**: An excellent fast TCP/UDP tunnel over an HTTP connection secured via SSH.

### Best Free Training Resources
*   **Lab Environment**: Complete the free **Wreath Network** on TryHackMe. It focuses completely on pivoting, routing, and breaking through multi-layered internal corporate networks.

---

## 📡 Phase 4: Command and Control (C2) Infrastructure Setup
*Red teamers do not use interactive standard reverse shells (like Netcat). They use Command and Control (C2) frameworks to look like legitimate corporate traffic.*

### Core Concepts to Master
*   **Beacons & Callbacks**: Setting jitter times (delaying packet communication so it looks like human behavior rather than an automated machine script).
*   **Redirectors**: Setting up intermediate VPS servers using Apache or Nginx reverse proxies to hide the actual IP address of your backend team server.

### Frameworks to Learn (Open Source & Free)
*   **Sliver**: A highly modular, secure cross-platform implant framework written in Go.
*   **Havoc**: A modern, sleek post-exploitation command and control framework that mimics commercial tools like Cobalt Strike.

---

## ☁️ Phase 5: Hybrid Cloud Exploitation (AWS / Azure)
*Modern corporate infrastructure is rarely entirely on-premise. It is synced to the cloud.*

### Core Concepts to Master
*   **Microsoft Entra ID (Azure AD)**: Learn how traditional local AD accounts sync to Azure via Entra Connect.
*   **Identity & Access Management (IAM)**: Master user roles, policies, group privileges, and access keys.

### Primary Attack Vectors
*   **Cloud Pivoting**: Bypassing on-premise boundaries to steal Azure Global Admin privileges, or finding leaked AWS access keys inside compromised on-premise file shares.
*   **Privilege Escalation**: Exploiting loose IAM policies to assume higher administration roles.

### Best Free Training Resources
*   **AWS Range**: Deploy **CloudGoat** (by Rhino Security Labs) within an AWS Free Tier account to practice automated cloud security misconfigurations.
*   **Local Cloud Range**: Run **LocalStack** to fully emulate an AWS environment locally on your laptop without paying cloud bills.

---

## 🥷 Phase 6: Basic Defense Evasion & Initial Access
*This is the entry gate into Exploit Development. You must sneak past defenses to drop your tools.*

### Core Concepts to Master
*   **AMSI Bypass**: Bypassing Microsoft's Antimalware Scan Interface to run malicious PowerShell lines in memory.
*   **Payload Obfuscation**: Learning how basic signature scanning works, and using custom wrappers (written in C# or Go) to encrypt shellcode until execution.
*   **Living off the Land (LotL)**: Using legitimate binary tools pre-installed on Windows (`certutil.exe`, `powershell.exe`, `mshta.exe`) to execute actions instead of installing known malicious binaries.

---

## 📋 Actionable Checklist to Launch Your Transition

- [ ] **Step 1:** Watch TCM Security's free AD video course on YouTube.
- [ ] **Step 2:** Install VirtualBox + Vagrant and stand up the GOAD network.
- [ ] **Step 3:** Hack the GOAD network manually and document your progress on GitHub.
- [ ] **Step 4:** Master network pivoting inside TryHackMe's free Wreath Lab using Ligolo-ng.
- [ ] **Step 5:** Run your first local teamserver using Havoc C2 or Sliver.
