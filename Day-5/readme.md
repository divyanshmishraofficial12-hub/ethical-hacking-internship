# Day 5: Security Hygiene & the Human Layer (Week 1 Wrap-up)

## 🧼 What is Security Hygiene?
Security hygiene is the set of routine, foundational habits—updates, backups, MFA, least privilege—that stop the vast majority of cyber attacks before advanced tools are needed. Most breaches exploit missing basic controls rather than zero-day vulnerabilities.

---

## ⚙️ Core Defensive Basics

### 1. Patch Management & Updates
* **Immediate Application:** Once a patch is released publicly, attackers reverse-engineer it to target unpatched systems within days.
* **Automate:** Enable automatic updates across OS, browsers, apps, phones, and routers.
* *Example:* The Equifax breach (147 million records stolen) occurred because a known vulnerability patch went unapplied for two months.

### 2. The 3-2-1 Backup Rule
* **3** total copies of your data (1 primary + 2 backups).
* **2** different storage media types (e.g., local disk + external drive/cloud).
* **1** copy kept offsite or offline (air-gapped so ransomware cannot reach it).
* *Rule:* Regularly test your restoration process. An untested backup is only a hope.

### 3. Least Privilege & System Hardening
* Perform daily work on a standard user account; reserve administrative permissions strictly for software installs.
* **Device Hardening Checklist:**
  1. **Full-Disk Encryption:** Enable BitLocker, FileVault, or device defaults.
  2. **Screen Locks:** Set short timeouts (1–2 minutes) protected by strong PINs or biometrics.
  3. **Network Defense:** Enable host firewalls and turn off unused services.
  4. **Device Management:** Enable remote tracking and remote-wipe functionality.
  5. **Visibility:** Always show file extensions (exposing tricks like `invoice.pdf.exe`) and uninstall unused applications.

---

## 🌐 Network Security & Safe Browsing

### Home Routers & Public Wi-Fi
* **Router Setup:** Change factory admin passwords, use WPA2/WPA3 encryption, update firmware, disable WPS/remote management, and place IoT devices on a guest network. (e.g., the Mirai botnet hijacked 600,000 devices using default credentials).
* **Public Wi-Fi:** Treat untrusted networks as monitored. Use HTTPS, a VPN, or a mobile hotspot for sensitive transactions. Forget public access points after use.

### Privacy & Footprint Management
* Minimize public personal data on social media (birthdays, locations, ID badge photos) that attackers use for spear-phishing recon.
* Keep browser extensions to a minimum (extensions can read active page data).
* Do not save payment card details directly in browsers.
* Never click "Enable Content" or enable macros in received attachments.

---

## 👤 The Human Layer & Organizational Culture

### Reporting Culture
* **Speed Over Perfection:** Promptly report suspicious emails, clicked links, unexpected MFA prompts, or lost devices.
* **Blameless Environment:** Security teams prioritize rapid reporting to contain breaches quickly over assigning blame. A reported mistake is a 5-minute fix; a hidden one becomes a 5-month breach.

### Spotting Scams & Vishing
* **Red Flags:** Urgency, secrecy, requests for money, OTPs, or remote system access.
* **Verification:** Banks and official organizations will never ask for secret OTPs or account passwords. Hang up and verify by calling official contact numbers directly.

---

## 🛡️ UK Cyber Essentials: The 5 Core Controls
1. **Firewalls:** Control inbound and outbound network traffic.
2. **Secure Configuration:** Remove default accounts and disable unnecessary services.
3. **Access Control:** Enforce least privilege access combined with MFA.
4. **Malware Protection:** Use antivirus/EDR and practice safe downloading.
5. **Patch Management:** Apply critical security updates within 14 days.
6. *(The 6th Element)* **Blameless Reporting Culture:** Catches attacks early in the execution lifecycle.

---

## 📅 Week 1 Course Summary
* **Day 1:** Security Fundamentals, CIA Triad, Assets, Threats, Risk ($Risk = Likelihood \times Impact$).
* **Day 2:** Threat Landscape (Malware types, Phishing vectors, Social Engineering, Attack Chains).
* **Day 3:** Identity & Authentication (Password security, Hashing/Salting, MFA tiers, Passkeys).
* **Day 4:** Cryptography Basics (Encoding vs. Encryption vs. Hashing, Symmetric/Asymmetric, HTTPS).
* **Day 5:** Security Hygiene, Hardening, Human Layer Defense.
