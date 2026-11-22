# Day 17: Digital Forensics Basics

## 🔬 What is Digital Forensics?
Digital forensics is the science of collecting, preserving, and analyzing digital evidence to reconstruct exactly what happened—**who did what, when, and how**—defensibly enough to hold up under legal scrutiny and in court.

* **Incident Response vs. Digital Forensics:** They operate as partners. **Incident Response (IR)** stops the bleeding (contains the breach and recovers systems), while **forensics** performs the autopsy (investigates the full story from evidence so nothing is guessed).
* **Why Preservation Matters:** Proper IR—such as isolating a compromised laptop from the network *without* powering it off (Day 16)—keeps volatile memory intact so forensics can later uncover critical clues.

---

## ⚖️ Evidence Handling & Core Principles

### 1. Order of Volatility
Digital evidence disappears at different speeds, so investigators collect the most fragile evidence first:
1. **Memory (RAM):** Vanishes immediately at power-off.
2. **Running Processes & Network Connections:** Fleeting live system state.
3. **Disk Storage:** Survives a reboot.
4. **Backups & Archives:** Most durable evidence.

### 2. Chain of Custody
* The documented, unbroken record tracking **who** handled evidence, **when**, and **what** they did with it—proving it was never altered or tampered with.
* Must remain unbroken from initial collection to the courtroom; a single undocumented gap can render valid evidence inadmissible.

### 3. Cryptographic Hashing
* Hashing seized evidence upon collection generates a unique digital fingerprint.
* Re-hashing the copy later proves it is bit-for-bit identical to the original evidence and was never modified during analysis.

### 4. Disk Imaging & Write-Blockers
* **Bit-for-Bit Disk Imaging:** Creates an exact byte-for-byte copy of a drive—including deleted files and hidden data—so analysts examine the working copy and never risk the original drive.
* **Write-Blockers:** Hardware or software tools that allow reading a drive without writing any data to it, preventing accidental changes that would taint evidence.

---

## 🔍 Disk, Memory, Registry & Network Forensics

### Memory (RAM) Forensics
* Captures critical clues that never touch the hard drive: active processes, open network connections, decrypted data, passwords, and **fileless malware**.
* Pulling the power plug destroys this evidence permanently.

### Timeline Analysis & File System Artefacts
* **Timeline Analysis:** Orders every timestamped artefact—file changes, logins, event logs, registry keys, and browser history—into a single chronological sequence revealing the attacker's step-by-step actions.
* **File System Artefacts:** Tracks **MAC timestamps** (*Modified, Accessed, Created*), file metadata, and deleted-file remnants.
* *"Deleted" rarely means gone—data remains recoverable on disk until overwritten.*

### Windows Registry & Network Artefacts
* **Windows Registry:** Acts as a detailed system diary alongside event logs, recording executed programs, connected USB devices, and user accounts.
* **Network Forensics:** Analyzes packet captures and connection logs to trace where stolen data went, what external C2 servers malware contacted, and how the attacker moved laterally.

---

## 🛠️ Forensics Toolkit & Anti-Forensics

### Essential Free & Open-Source Tools
* **Autopsy & The Sleuth Kit:** Disk analysis, timeline generation, and deleted-file recovery.
* **Volatility:** Memory (RAM) forensics and process analysis.
* **FTK Imager:** Bit-for-bit disk imaging and cryptographic hash verification.
* **Wireshark:** Network packet capture and traffic inspection.

### Anti-Forensics & Countermeasures
* **Attacker Techniques:** Deleting local logs, wiping files, modifying timestamps (timestomping), encrypting payloads, and executing fileless malware in memory.
* **Defender Countermeasures:** Centralized **off-box log shipping** (Day 15) and **live RAM captures** preserve evidence that attackers cannot erase locally.

---

## 📋 Rules, Ethics & The Forensic Report

### Forensic Rules of Engagement
* Only investigate systems you are explicitly authorized to examine.
* Handle all sensitive data confidentially.
* Stay objective—**follow the evidence wherever it leads**, rather than trying to prove a hunch.
* Document every action thoroughly, as findings face cross-examination.

### The Forensic Report (Final Deliverable)
A finding that cannot be tied directly to verified evidence is just an opinion. A defensible forensic report clearly documents:
1. **Scope:** Exact systems, drives, and artefacts examined.
2. **Methodology:** Tools and acquisition/analysis methods used (including hash verifications).
3. **Evidentiary Findings:** Specific findings tied directly to supporting artefacts.
4. **Timeline:** Clear chronological sequence of events.
5. **Conclusions:** Objective summary written clearly for both non-technical readers and courts.

---

## 💻 Lab Activity & Homework for Day 18
* **Day 17 Forensics Lab:** Load the provided disk image into **Autopsy**, verify its cryptographic hash, recover the deleted file, build an event timeline, and write a concise findings report.
