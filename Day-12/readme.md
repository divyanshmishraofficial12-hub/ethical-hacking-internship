# Day 12: Vulnerability Scanning — Finding Weaknesses with Nmap

## 🎯 Overview
Vulnerability scanning identifies known security weaknesses across networks and hosts before attackers can exploit them. This module covers core risk terminology, active vs. passive reconnaissance, Nmap scanning techniques, vulnerability scoring standards (CVE & CVSS), and remediation prioritization.

---

## 🧩 Core Security Concepts

### Vulnerability vs. Exploit vs. Threat vs. Risk
* **Vulnerability:** A weakness an attacker can leverage—such as a missing patch, weak configuration, default password, or exposed service *(the unlocked door)*.
* **Exploit:** The tool, code, or technique used to take advantage of a vulnerability *(the lockpick)*.
* **Threat:** Any actor or event capable of exploiting a weakness *(the burglar)*.
* **Risk:** The likelihood and potential impact of a compromise ($\text{Risk} = \text{Likelihood} \times \text{Impact}$).
  * *Real-World Example:* Unpatched SMB + EternalBlue exploit + a worm author on a hospital network = the high risk that caused **WannaCry**.

### Reconnaissance & Scanning Workflow
* **Passive Reconnaissance:** Gathering intelligence via OSINT without touching or alerting the target.
* **Active Reconnaissance:** Probing the target directly through network scans.
* **Standard Discovery Sequence:**  
  `Host Discovery` → `Port Scan` → `Service & Version Enumeration` → `Vulnerability Checks`

---

## 🔍 Nmap (Network Mapper)
Nmap is the industry-standard open-source network scanner used to discover live hosts, map open ports, identify running services and software versions, fingerprint operating systems, and run vulnerability scripts.

### Port States
| State | Meaning | Network Response |
| :--- | :--- | :--- |
| **Open** | An application/service is actively listening on the port. | Replies with `SYN-ACK` |
| **Closed** | The host is reachable, but no service is listening on the port. | Replies with `RST` |
| **Filtered** | A firewall or packet filter is blocking probes, hiding port status. | No response / ICMP unreachable |

### Common Nmap Scan Flags
* `nmap -sS <target>` — **TCP SYN Scan:** Fast, stealthy default scan (requires `root`/`sudo`).
* `nmap -sV <target>` — **Service/Version Detection:** Probes open ports to determine exact software and version numbers.
* `nmap -O <target>` — **OS Detection:** Fingerprints the target's operating system.
* `nmap -sC <target>` / `--script` — **NSE Scripts:** Runs Nmap Scripting Engine scripts for deeper enumeration and vulnerability checks.

> 💡 **Scanning Best Practice:** Start with lightweight discovery scans, then run deeper version and script scans only on relevant hosts and ports.

---

## 📊 Rating Flaws & Vulnerability Scanners

### CVE & CVSS
* **CVE (Common Vulnerabilities and Exposures):** A global catalog assigning a unique ID to every publicly known vulnerability (e.g., `CVE-2021-44228` for Log4Shell) so defenders, vendors, and tools reference the exact same flaw.
* **CVSS (Common Vulnerability Scoring System):** Rates flaw severity on a **0.0 to 10.0** scale based on exploitability and impact:
  * **0.0 – 3.9:** Low
  * **4.0 – 6.9:** Medium
  * **7.0 – 8.9:** High
  * **9.0 – 10.0:** Critical

### Dedicated Vulnerability Scanners
Tools like **Nessus** (commercial) and **OpenVAS / Greenbone** (open-source) go beyond port discovery by testing services against extensive vulnerability databases to produce prioritized reports listing CVEs, severity ratings, and exact remediation steps.

### Authenticated vs. Unauthenticated Scans
* **Unauthenticated Scan:** External view showing what an outside attacker sees from the network perimeter.
* **Authenticated Scan:** Logs into target hosts with credentials to inspect missing patches, local packages, and internal configurations from the inside. Use both for complete outside-in and inside-out visibility.

---

## 🛠️ Acting on Scan Results & Vulnerability Management

### Prioritizing Fixes
Raw CVSS scores alone do not tell the whole story. Rank remediation by:
1. **CVSS Severity**
2. **Exposure** (internet-facing assets take priority over isolated internal hosts)
3. **Active Exploitability** (e.g., flaws listed in **CISA KEV** — Known Exploited Vulnerabilities)
4. **Business Impact**

### Report Triage & Accuracy
* **False Positive:** A reported vulnerability that does not actually exist on the system (wastes remediation time).
* **False Negative:** An actual vulnerability that the scanner failed to detect (the highest security risk).
* **Triage Workflow:** Group findings by severity → validate results to filter false positives → assign owners and patches → re-scan to verify fixes.

### Vulnerability Management Lifecycle
`Inventory` → `Scan` → `Prioritise` → `Remediate` → `Verify` → `Repeat`

### Scanning vs. Penetration Testing
* **Vulnerability Scanning:** Automated, frequent (e.g., weekly) detection of known flaws.
* **Penetration Testing:** Periodic, human-led exploitation that chains weaknesses together to demonstrate real-world business impact.

---

## ⚖️ Legal & Ethical Boundaries
* Only scan networks and systems you own or have **explicit written authorization** and defined scope to test.
* Unauthorized scanning is illegal and can disrupt or crash fragile production systems. Practice exclusively in isolated lab environments (e.g., **Metasploitable**, **HackTheBox**).

---

## 💻 Lab Activity: Scanning Metasploitable with Nmap
* **Objective:** Perform host discovery, port scanning (`-sS`), and service/version enumeration (`-sV`) against a vulnerable **Metasploitable** VM to map exposed services and identify outdated software versions.
