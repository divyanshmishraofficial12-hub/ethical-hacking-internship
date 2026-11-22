# Day 14: Ethical Hacking & the Penetration Testing Workflow

## ⚖️ The Ethics of Hacking

### What is Ethical Hacking?
Ethical hacking is the practice of attacking systems **with explicit permission** to discover and report security weaknesses before malicious actors exploit them. It uses the exact same technical skills as criminal hacking, separated by opposite intent and formal authorization (*a signed contract, not a hoodie*).

### Tester vs. Criminal
Three non-negotiable pillars separate an ethical penetration tester from a cybercriminal—remove any one, and the activity becomes a crime:
1. **Authorisation:** Explicit written permission from the system owner.
2. **Scope:** Clearly agreed boundaries and operational limits.
3. **Intent:** Reporting weaknesses to improve security rather than exploiting them for gain.

### The Hats (vs. Operational Teams)
* **White Hat:** Authorised, ethical security professionals employed to defend and test systems.
* **Black Hat:** Criminal hackers operating for financial gain, theft, or disruption.
* **Grey Hat:** Probes or hacks without permission, typically without malicious intent—**still illegal**.
* *(Note: Red, Blue, and Purple teams refer to organizational security roles, not hat colors.)*

---

## 🔄 The Penetration Testing Workflow

### What is a Pentest?
A penetration test is an authorised, simulated attack designed to uncover exploitable vulnerabilities and demonstrate their real-world business impact—proving what an attacker could actually achieve rather than merely listing theoretical flaws.

### The 6 Phases (Always in Order)
1. **Scope:** Agree on targets, limits, testing windows, and rules in writing.
2. **Recon:** Map the target using passive OSINT (Day 10) and active scanning (Day 12).
3. **Scan:** Identify exploitable vulnerabilities and misconfigurations.
4. **Exploit:** Break in and establish an initial foothold with proof.
5. **Post-Exploit:** Escalate privileges and assess lateral reach and impact.
6. **Report:** Deliver findings, business impact, evidence, and prioritised fixes.

### Scoping & Rules of Engagement (RoE)
* Before testing begins, both parties sign a written agreement defining what is **in scope** and **out of scope**, permitted testing hours, emergency contacts, and stop conditions.
* This document acts as your legal shield (*"get out of jail" letter*). Testing out-of-scope systems or outside approved windows creates direct legal liability.

### Reconnaissance
* Combines passive OSINT and active scanning to map infrastructure (such as outdated Apache versions or exposed login portals) before attempting exploitation. Attackers spend the majority of their time looking, not attacking.

---

## 💥 Breaking In: Exploitation & Post-Exploitation

### Exploitation
* Actively leveraging a discovered weakness to gain unauthorized access (running exploit code, injecting payloads, or cracking credentials).
* **Core Principle:** *A vulnerability is a theory; an exploit is the proof.*

### Metasploit Framework
* The industry-standard exploitation framework providing thousands of ready-to-use exploits and payloads (`search`, `use`, `set RHOSTS`, `exploit`), along with **Meterpreter**, an advanced interactive post-exploitation shell. Must only be targeted at systems you own or have written authorization to test.

### Payloads, Shells & Reverse Shells
* **Payload:** The code executed on the target immediately after a successful exploit.
* **Shell:** Command-line access to control the compromised target.
* **Reverse Shell:** Forces the target machine to initiate an outbound connection back to the tester's listener, bypassing inbound firewall blocks (*getting the house to call you instead of knocking on the door*).

### Privilege Escalation
* Initial exploitation rarely grants administrative rights. Privilege escalation elevates a low-level foothold to full `root` or `SYSTEM` control by abusing weak file permissions, SUID binaries, misconfigured `sudo` rules (e.g., `sudo vim` without password → `:!bash` → `root`), or kernel flaws (Day 7).
* **Core Principle:** *Getting in is the foothold; becoming root is the win.*

### Post-Exploitation
* Ethically assessing how far an attacker could pivot from the initial foothold—documenting reachable databases, internal networks, and persistence risks to prove business impact without modifying or exfiltrating sensitive data.

---

## 🛠️ The Craft, Reporting & Career Path

### Capture The Flag (CTF)
* Legal, gamified cybersecurity challenges where players compromise deliberately vulnerable machines to capture hidden flags on platforms like **TryHackMe**, **HackTheBox**, and **picoCTF**.

### The Pentest Report (The Real Deliverable)
The exploit proves the risk, but the report is the product that makes the organization safer:
1. **Executive Summary:** High-level risk overview written for non-technical leadership.
2. **Technical Findings:** Detailed breakdown of each flaw with severity ratings and proof/screenshots.
3. **Business Impact:** Clear explanation of real-world consequences in business terms.
4. **Prioritised Remediation:** Actionable, step-by-step fixes ranked by urgency.

### The Pentester's Toolkit
* **Recon:** Nmap
* **Vulnerability Scanning:** Nessus / OpenVAS
* **Web Application Testing:** Burp Suite
* **Exploitation:** Metasploit
* **Environment:** Kali Linux (bundling hundreds of specialized security tools)
* *(Tools don't make the hacker — structured methodology does.)*

### Legal & Ethical Boundaries
* Test only authorized targets, remain strictly inside scope, protect any encountered data, report all findings transparently, and never use access for personal gain.
* If real sensitive data is encountered during a test, **stop immediately**, document the exposure, report it securely, and touch nothing else.

### Becoming a Penetration Tester
* Master foundational networking, OS, and web security concepts, practice CTFs while maintaining a structured lab journal, earn hands-on certifications (**CompTIA PenTest+**, **eJPT**, **OSCP**), and build a public portfolio of documented write-ups.

---

## 💻 Lab Activity & Homework for Day 15
* **First Full Pentest:** On an authorised lab target, run reconnaissance with **Nmap**, exploit a vulnerability using **Metasploit** to gain a shell, attempt **privilege escalation**, and write a concise **one-page findings report**.
