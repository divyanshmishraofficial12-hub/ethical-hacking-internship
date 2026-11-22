# Day 15: Monitoring, Detection & SIEM

## 🏗️ The Foundation: Why Detection & Logs Matter

### Why Detection Matters & Dwell Time
* No defence is 100% impenetrable—attackers eventually get in. Detection is how defenders spot intrusions early and respond before minor compromises escalate into major breaches.
* **Dwell Time:** The duration an attacker remains inside a network undetected. In breaches like Target, alerts fired for weeks, but nobody was actively monitoring them. Detection requires both visibility tools and active human oversight.
* **Monitoring & Baselines:** Continuously observing systems, networks, and users against established **baselines** of normal activity so anomalies stand out (e.g., an internal server that only talks to three local hosts suddenly contacting a foreign IP at 3:00 AM).

### Logs — The Raw Evidence
* Logs record system activity—logins, errors, network connections, and configuration changes—acting as your network's black box. Without logs, incidents are invisible and unprovable.
* Attackers routinely delete local logs to cover their tracks, so logs must be **shipped off-box** and centralized immediately.

### Key Log Sources
* **Authentication:** Successful logins, failed attempts, and privilege escalation/usage.
* **Endpoint / EDR:** Process creation, file modifications, and endpoint security alerts.
* **Network:** Firewall traffic, web proxy records, and DNS queries.
* **Cloud:** API calls, configuration modifications, and IAM permission changes.

> 🔗 **Multi-Source Confirmation:** A brute-force attack appears in **authentication logs** → the dropped malware shows up in **endpoint logs** → its outbound C2 beacon appears in **DNS and firewall logs**. One attack confirmed across three independent sources.

---

## 🧠 The SIEM & Correlation

### What is a SIEM?
A **SIEM (Security Information and Event Management)** platform—such as **Splunk**, **Elastic**, **Microsoft Sentinel**, or **Wazuh**—serves as the central nervous system of a security team. It **collects, normalises, correlates, alerts, and stores** telemetry from across the environment, turning millions of raw log lines into a readable narrative.

### Correlation
Correlation links separate events that appear harmless individually into a high-confidence security alert:
* **Brute-Force Pattern:** One failed login is everyday noise; 10,000 failed logins followed by a successful authentication is a confirmed attack.
* **Impossible Travel:** A user account logging in from India and, five minutes later, logging in from Brazil signals account compromise even though neither login alone looks unusual.

---

## 🛡️ The SOC & Alert Management

### Security Operations Centre (SOC)
A **SOC** is the dedicated team and facility that monitors, detects, and responds to threats 24/7, primarily operating from a SIEM—enabling analysts to spot a ransomware alert at 2:00 AM, isolate the host, and contain the threat within minutes.

### SOC Tiers
* **Tier 1 (Triage):** Reviews incoming alerts, determines whether activity is genuine or benign, and escalates confirmed threats *(the primary entry-level cybersecurity role)*.
* **Tier 2 (Investigation):** Performs deep-dive analysis on escalated incidents to determine full scope and impact.
* **Tier 3 (Threat Hunting):** Conducts proactive threat hunting and handles the most complex, advanced intrusions.

### Alerts, Tuning & Alert Fatigue
* **Alert Fatigue:** When analysts are flooded with excessive low-value or false alerts (e.g., 5,000 alerts per day), real attacks get buried and missed. Tuning detection rules down to ~50 high-signal alerts makes monitoring effective.
* **False Positives vs. False Negatives:**
  * **False Positive:** An alert triggered by legitimate, harmless activity (wastes analyst time).
  * **False Negative:** A real attack that generates no alert (**the most dangerous failure**). Over-tuning rules to reduce noise risks silencing real detections.

---

## 🎯 Finding Threats: MITRE ATT&CK, Rules & Hunting

### MITRE ATT&CK
* A free, global knowledge base cataloging real-world adversary **tactics** (the *why*) and **techniques** (the *how*).
* SOC teams map their detection rules to ATT&CK to expose blind spots—such as having strong visibility for *Initial Access* but zero coverage for *Lateral Movement*.

### Detection Rules & Sigma
* **Detection Rules:** Automated logic instructing the SIEM which event patterns require an alert (e.g., *"20+ failed SSH logins from a single IP within 60 seconds"*).
* **Sigma:** An open, vendor-agnostic rule format allowing detection logic to be written once and deployed across different SIEM platforms.

### Threat Hunting
* Proactively searching networks and endpoints for hidden attackers who bypassed automated rules—operating under an **assume-breach** mindset.
* **Hypothesis-Driven:** Analysts formulate a hypothesis (e.g., *"If an adversary used this technique, we would see an encoded PowerShell pattern"*), query historical telemetry, and uncover silent intrusions.

### Detection-to-Response Handoff
* Detection identifies the intrusion and passes a structured, evidenced alert (compromised host, user account, timestamp, and activity timeline) to **Incident Response (Day 16)** so responders can isolate the exact affected machine immediately.

### Open-Source & Practice Mini-SOC Stack
* **SIEM:** Splunk Free, Elastic Security, Wazuh (SIEM + Endpoint agent)
* **Endpoint Telemetry:** Sysmon (detailed Windows event logging)
* **Network Detection (NIDS):** Zeek, Suricata

---

## 🔄 The Big Picture
Effective security relies on three sequential layers:
`Prevention (Weeks 1–3)` → `Detection (Day 15)` → `Response (Week 4)`

Even a hardened network can suffer a successful phish; detection catches the resulting C2 beacon within minutes, response isolates the host, and a potential catastrophic breach is contained as a routine incident report.

---

## 💻 Lab Activity & Homework for Day 16
* **Detection Lab:** Load the sample security logs into **Splunk Free** (or analyze them via the command line), identify the brute-force attack, extract the **attacker IP address** and **compromised user account**, and write **one custom detection rule**.
