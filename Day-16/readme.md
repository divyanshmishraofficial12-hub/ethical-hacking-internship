# Day 16: Incident Response — Handling a Breach

## 🚨 Security Events vs. Incidents
* **Security Event:** Any observable occurrence in a system or network (e.g., a user clicking a phishing link).
* **Security Incident:** Any event that actually harms or threatens systems or data (e.g., that phishing click leading to unauthorized access or data theft).
* **Incident Response (IR):** The structured, rehearsed process of managing an incident from initial alert to final lessons learned—acting as a practiced fire drill so teams execute calmly instead of improvising during a live crisis.

---

## 🔄 The 6-Phase Incident Response Lifecycle
Incident response operates as a continuous loop where lessons from the final phase feed directly back into preparation:

1. **Preparation:** Building IR plans, playbooks, roles, contact lists, detection tooling, and backups *before* an incident occurs, reinforced through regular drills.
2. **Detection & Analysis:** Confirming whether an alert represents a true incident and determining its scope—affected hosts, severity, and initial entry vector (building directly on Day 15 SIEM telemetry).
3. **Containment:** Stopping the spread immediately without destroying evidence (*"a tourniquet, not surgery"*). Isolate infected machines from the network, **but keep them powered on** so volatile memory (RAM) can be captured.
4. **Eradication:** Eliminating the threat completely—removing malware, revoking attacker access, deleting persistence mechanisms (e.g., scheduled tasks), resetting compromised passwords, and patching the root vulnerability.
5. **Recovery:** Restoring operations safely from known-clean backups (Day 5's 3-2-1 rule), rebuilding compromised systems, verifying cleanliness before reconnecting, and monitoring closely for attacker return.
6. **Lessons Learned:** Conducting a blameless post-incident review to build an accurate timeline, evaluate what worked or failed, and implement structural upgrades (e.g., enforcing SSH keys and MFA) so the same attack cannot succeed again.

---

## 📋 Playbooks & Team Structure

### Incident Playbooks
* Step-by-step response checklists tailored to specific incident types (phishing, ransomware, account compromise) so responders follow proven steps rather than guesswork.
* *Example — Phishing Playbook:* Isolate mailbox → reset password → check who else received the email → block sender → hunt for link clicks.

### Cross-Functional IR Roles
Incident response is a coordinated team effort across technical and business functions:
* **Incident Commander:** Leads the response and holds decision-making authority.
* **Technical Responders:** Execute containment, eradication, and system recovery.
* **Communications, Legal & Management:** Handle internal/external updates, regulatory compliance, and executive decisions.

---

## 🔍 Evidence Handling, Communication & Legal Duties

### Digital Evidence Preservation
* **Order of Volatility:** Capture volatile data first (RAM/memory before disk storage).
* **Cryptographic Hashing:** Hash collected evidence immediately (e.g., SHA-256, Day 4) to prove integrity and verify it remains unaltered.
* **Chain of Custody:** Maintain strict logs documenting who collected, transferred, and accessed every piece of evidence.
* **Work on Copies:** Never inspect or modify original evidence directly.

### Communication & Regulatory Reporting
* **Clear Communication:** Maintain a single internal source of truth for status updates and provide honest, timely disclosures to affected customers and regulators.
* **Strict Legal Deadlines:** Laws such as **GDPR** (typically 72 hours) and **India's DPDP Act** enforce mandatory breach notification windows. Involve legal counsel early to avoid regulatory penalties.

---

## 🎯 Tabletop Exercises & The Security Pipeline

### Tabletop Exercises
* Discussion-based simulations of realistic crisis scenarios (e.g., *"ransomware strikes at 2:00 AM"*) used to expose unclear ownership, missing permissions, and procedural gaps safely before a real breach tests them.

### The Detection-to-Response Pipeline
Effective cybersecurity operates across three connected layers:  
`Prevention (Weeks 1–3)` → `Detection (Day 15)` → `Response (Day 16)`

---

## 💻 Lab Activity & Homework for Day 17
* **Day 16 IR Tabletop Exercise:** Walk through a realistic ransomware scenario across all six incident response phases, make key containment and recovery judgment calls, and produce a structured incident timeline and summary report.
