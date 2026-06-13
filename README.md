# Cybersecurity Domains

```
Cybersecurity
├── Offensive security
│   ├── Web / app pentesting
│   │   ├── OWASP Top 10 — Injection, XSS, IDOR, SSRF
│   │   ├── API security — REST, GraphQL, OAuth abuse
│   │   ├── SAST / code review — Static analysis, secret scanning
│   │   ├── Business logic — WebSockets, race conditions
│   │   └── DAST — Dynamic runtime testing
│   │
│   ├── Infrastructure pentesting
│   │   ├── Network — Port scanning, OS fingerprinting, pivoting
│   │   ├── Wireless / RF — Wi-Fi, Bluetooth, SDR, SS7/IMSI
│   │   ├── Cloud — IAM misconfig, S3 exposure, serverless
│   │   ├── OT / ICS / SCADA — Industrial control systems
│   │   └── Mobile — Android/iOS APK reversing, MDM bypass
│   │
│   ├── Enterprise red teaming
│   │   ├── OSINT / recon — Maltego, Shodan, theHarvester
│   │   ├── Social engineering — Phishing, vishing, pretexting
│   │   ├── Active Directory — Kerberoasting, pass-the-hash, DCSync
│   │   ├── Network pivoting — Tunneling, proxy chains, lateral movement
│   │   ├── Covert C2 — Beaconing, domain fronting, sleep timers
│   │   ├── Cloud red teaming — AAD, GCP, AWS lateral movement
│   │   └── Physical intrusion — Tailgating, lock picking, RFID cloning
│   │
│   ├── Vulnerability research
│   │   ├── Source code audit — Manual review, taint analysis
│   │   ├── Fuzzing — AFL++, libFuzzer, coverage-guided
│   │   ├── Vulnerability classes — UAF, heap spray, TOCTOU, format strings
│   │   ├── Binary analysis — Ghidra, Binary Ninja, IDA Pro
│   │   └── Responsible disclosure — CVE, bug bounty, coordinated
│   │
│   └── Exploit development
│       ├── Stack / heap overflows — Buffer overflows, heap grooming
│       ├── ROP chains — DEP/NX bypass, gadget chaining
│       ├── Memory leaks — ASLR bypass, info disclosure
│       ├── Kernel / driver — LPE, rootkits, privilege escalation
│       ├── Shellcode — Position-independent, staged payloads
│       └── Browser exploitation — JIT spraying, sandbox escape, V8
│
├── Defensive security
│   ├── Blue teaming / SOC
│   │   ├── SIEM monitoring — Splunk, Sentinel, ELK, QRadar
│   │   ├── EDR / XDR — CrowdStrike, Defender, SentinelOne
│   │   ├── Firewall / WAF — Policy, segmentation, IPS tuning
│   │   ├── Threat hunting — Hypothesis-driven, anomaly-based
│   │   └── Deception technology — Honeypots, honeytokens, canaries
│   │
│   ├── Detection engineering
│   │   ├── Sigma / YARA — Portable, vendor-agnostic rules
│   │   ├── MITRE ATT&CK — TTP mapping, coverage gap analysis
│   │   ├── Telemetry analysis — Log pipelines, enrichment
│   │   └── Alert tuning — FP reduction, baseline baselining
│   │
│   ├── Forensics / IR (DFIR)
│   │   ├── Log analysis — Windows event logs, syslog, PCAP
│   │   ├── Memory forensics — Volatility, dump acquisition
│   │   ├── Network captures — Wireshark, Zeek, full-packet PCAP
│   │   ├── Disk / file forensics — FTK, Autopsy, timeline analysis
│   │   └── IR playbooks — Contain, eradicate, recover, post-mortem
│   │
│   ├── Malware analysis
│   │   ├── Static triage — Hashes, strings, PE headers, imports
│   │   ├── Dynamic sandbox — Any.run, Cuckoo, behavioral logs
│   │   ├── Advanced reversing — Decompilation, de-obfuscation
│   │   └── Crypto key extraction — Config parsing, in-memory recovery
│   │
│   └── Cyber threat intelligence (CTI)
│       ├── Tactical / technical — IOCs, TTPs, Sigma from threat reports
│       └── Strategic / operational — Actor profiles, ISACs, dark web
│
└── Cross-cutting domains
    ├── Cryptography
    │   ├── Cryptanalysis — Side-channel, timing, differential attacks
    │   ├── TLS / PKI — Cert pinning, downgrade attacks, mTLS
    │   └── Implementation flaws — Padding oracles, weak RNG, IV reuse
    │
    ├── Identity & access management (IAM)
    │   ├── OAuth / OIDC — Token theft, consent phishing, redirect abuse
    │   ├── SSO / SAML — Assertion forgery, XML signature wrapping
    │   └── Privilege escalation — Cloud IAM misconfig, RBAC abuse
    │
    ├── Application security / secure SDLC
    │   ├── Threat modeling — STRIDE, PASTA, attack trees, DFDs
    │   ├── SCA — Open-source dependency vulnerability management
    │   ├── Secrets management — Vault, leak scanning, rotation
    │   └── DevSecOps — CI/CD security gates, shift-left testing
    │
    └── GRC & compliance
        ├── Standards — ISO 27001, SOC 2, NIST CSF, CIS Controls
        ├── Regulation — GDPR, HIPAA, PCI-DSS, DORA, NIS2
        ├── Risk assessment — Asset inventory, risk register
        └── Audit — Gap analysis, third-party reviews, pentest scope
```
