# Day 9: Malware & How It Spreads (Kill Chain, C2 & Safe Analysis)

## 🦠 Understanding Malware
Malware is any software designed to cause harm—steal, spy, damage, extort, or gain unauthorized control. Malware is defined by **intent**, not by a single technique. A single phishing email can deliver a trojan that installs a keylogger, opens a backdoor, and drops ransomware.

---

## 🔗 The Cyber Kill Chain & Attack Mechanics

### The 6-Step Cyber Kill Chain
Defenders break links to stop attacks:
1. **Recon:** Identify targets and search for vulnerabilities.
2. **Deliver:** Send malicious content via phishing, malicious websites, or infected USBs (*Stopped by Security Awareness*).
3. **Exploit:** Trigger code execution via user click or software vulnerability (*Stopped by Patching*).
4. **Install:** Deploy payload and establish persistence (*Stopped by Endpoint Detection & Response / EDR*).
5. **Control (C2):** Establish outbound beaconing back to the attacker's server (*Stopped by Network Monitoring*).
6. **Act:** Execute final objective (data exfiltration, encryption, destruction).

> 💡 **Core Security Principle:** Defenders only need to break **one link** in the chain to neutralize the entire attack.

### Droppers vs. Payloads
* **Dropper:** The initial delivery vehicle used to gain a foothold on the target host (e.g., a macro inside an Office document).
* **Payload:** The actual malicious code executed after entry (e.g., keyloggers, ransomware).
* **Infection Vectors:** Phishing attachments/links, drive-by downloads, cracked software, malicious USBs, and malvertising.

---

## ⚙️ Persistence, C2 & High-Impact Threat Types

### 1. Persistence Mechanisms
Deleting the primary malware executable does not clear the infection if persistence remains active.
* **Windows Persistence:** Registry Run keys, Startup folders, Scheduled Tasks, System Services.
* **Linux Persistence:** `cron` jobs, `systemd` services, hidden profile scripts (`~/.bashrc`).

### 2. Command-and-Control (C2)
* **Beaconing:** Malware sends regular, periodic requests back to an attacker-controlled server to receive commands or upload stolen data.
* **Detection:** Identified by observing unnatural, clockwork traffic patterns originating from internal endpoints.

### 3. Ransomware & Botnets
* **Double Extortion:** Attackers exfiltrate sensitive data before encrypting local files, threatening public disclosure if the ransom is unpaid.
* **Ransomware-as-a-Service (RaaS):** Modern affiliate model where malware developers lease ransomware tools to lower-skilled criminal operators.
* **Botnets:** Network of compromised zombie devices controlled centrally to perform DDoS attacks, credential stuffing, or crypto-mining (e.g., the Mirai botnet).

---

## 🔬 Safe Malware Analysis

### Golden Rule of Malware Analysis
> ⚠️ **Never execute a suspicious sample on a host machine.** Conduct all dynamic testing within an isolated sandbox environment.

### Static vs. Dynamic Analysis
* **Static Analysis:** Inspecting file properties without executing the code (examining cryptographic hashes, file headers, embedded strings, and imported APIs).
* **Dynamic Analysis:** Executing the sample inside a monitored sandbox (e.g., ANY.RUN, Hybrid Analysis, or an isolated VM with snapshots) to observe behavior, registry edits, dropped files, and network traffic.

### File Hashes & VirusTotal Rules
* **Cryptographic Hashes (MD5 / SHA-256):** Act as unique digital fingerprints for identifying known malicious files across security platforms.
* **VirusTotal Operational Security (OpSec):**
  * **Do:** Search VirusTotal by looking up file **SHA-256 hashes**.
  * **Don't:** Upload actual files containing sensitive or proprietary data to public repositories.
  * *Note:* A zero-detection score ("Not Found") does not guarantee a file is safe; it may indicate a zero-day or targeted custom sample.

---

## 🛡️ Evasion & Incident Containment

### Detection Evasion Techniques
* **Packing & Polymorphism:** Encrypting payloads or altering binary signatures on each compilation to bypass signature-based antivirus.
* **Living off the Land (LotL):** Abusing legitimate system administrative tools (e.g., PowerShell, WMI) to blend in with normal administrative traffic.
* **Fileless Malware:** Executing directly within system RAM without writing binaries to the physical disk.
* **Antivirus vs. EDR:** Traditional Antivirus relies on static, known-bad signatures. **Endpoint Detection and Response (EDR)** monitors host process behavior in real time to catch novel and signatureless threats.

### 4-Step Incident Response Protocol
1. **Isolate:** Disconnect the compromised system from the network immediately (do **not** power off, as RAM forensics will be lost).
2. **Preserve:** Capture memory state and system event logs for investigative forensics.
3. **Eradicate:** Remove persistent registry entries, scheduled tasks, and malicious artifacts.
4. **Recover & Learn:** Restore data from clean offline backups, rotate compromised credentials, and patch the root entry point.
