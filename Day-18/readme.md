# Day 18: Governance, Risk & Compliance (GRC)

## 🏛️ What is GRC?
**GRC** stands for **Governance, Risk, and Compliance**—the business and strategic layer of cybersecurity that directs technical controls toward real organizational priorities:
* **Governance:** Sets the rules, policies, and strategic direction (e.g., the board allocating security budget).
* **Risk Management:** Identifies, scores, and prioritizes what threats to address first.
* **Compliance:** Proves the organization meets applicable laws, regulations, and industry standards.

> 💡 **Core Principle:** Buying security tools without GRC is like renovating random rooms while the roof leaks. Technical controls ask *"can we?"*; GRC asks *"should we?"*.

---

## 📊 Risk Management & Risk Registers

### Measuring Risk
Risk quantifies the likelihood of an event and the severity of its consequences on a unified scale:  
`Risk = Likelihood × Impact`

### The Risk Register
A **Risk Register** is a central, living document that turns vague security concerns into an actionable, accountable list. Every entry tracks:
* **Risk Description**
* **Likelihood & Impact Scores**
* **Risk Owner** (accountable individual)
* **Planned Treatment & Status**

### The 4 Risk Treatments
Once a risk is scored, leadership selects one of four responses:
1. **Mitigate:** Implement technical or procedural controls to reduce likelihood or impact (e.g., deploying MFA and backups against ransomware).
2. **Transfer:** Shift financial impact to a third party (e.g., cyber insurance or managed security outsourcing).
3. **Avoid:** Eliminate the risk entirely by stopping the risky activity or removing a vulnerable feature.
4. **Accept:** Acknowledge and retain low residual risk when the cost of remediation outweighs the potential loss.

---

## 📜 Governance Hierarchy: Policies to Guidelines
Governance translates leadership intent into daily operations through four structured tiers:

| Tier | Purpose | Example |
| :--- | :--- | :--- |
| **Policy** | Formal, mandatory high-level rule | *"All sensitive data must be encrypted."* |
| **Standard** | Specific technical requirement to satisfy a policy | *"Use AES-256 for data at rest and TLS 1.3 in transit."* |
| **Procedure** | Step-by-step operational instructions (*how-to*) | Step-by-step runbook for configuring BitLocker/LUKS. |
| **Guideline** | Recommended best practice (non-mandatory) | Tips for organizing encrypted backup drives. |

> *"A policy without a procedure is a wish; a procedure without a policy is improvisation."*

---

## ⚖️ Compliance, Frameworks & Laws

### Compliant vs. Secure
* **Compliant:** Meeting a minimum legal, regulatory, or contractual checklist and proving it. Failing compliance leads to fines, lawsuits, and lost contracts.
* **Secure:** Being genuinely protected against real-world attackers. An organization can pass every compliance audit and still be breached through an uncovered attack vector—use compliance as a **floor**, not a ceiling.

### Key Standards & Regulations
* **ISO 27001:** The leading international standard for establishing, auditing, and certifying an **Information Security Management System (ISMS)**—widely required in B2B contracts.
* **NIST Cybersecurity Framework (CSF):** Organizes cybersecurity programs into six core functions:  
  `Govern` → `Identify` → `Protect` → `Detect` → `Respond` → `Recover`
* **GDPR (EU) & India's DPDP Act:** Data privacy laws granting individuals rights over their personal data, requiring strict safeguards and mandatory breach notifications backed by heavy financial penalties.
* **PCI-DSS:** Contractual security standard governing any organization that stores, processes, or transmits payment card data (non-compliance can revoke card-processing privileges).

---

## 🔍 Audits, Awareness & Third-Party Risk

### Audits (*"Show Me, Don't Tell Me"*)
* An independent, evidence-based verification confirming that actual practices match written policies and standards. Audits uncover control gaps, prove compliance, and drive continuous improvement.

### Security Awareness Programs
* Hardens the human layer through ongoing training and phishing simulations, tracked using measurable metrics such as **phishing click rates** and **incident reporting rates**.

### Third-Party Risk Management (TPRM)
* An organization's security is only as strong as its vendors'—breaches like **Target** (via an HVAC contractor) and **SolarWinds** (via a compromised software update) demonstrate that attackers exploit trusted external partners to bypass perimeter defenses.

### GRC Career Paths
* GRC bridges technical security and business leadership, opening roles such as **GRC Analyst**, **Risk Analyst**, **Compliance Officer**, and **IT Security Auditor**.

---

## 💻 Lab Activity & Homework for Day 19
* **Day 18 Risk Register Lab:** Convert the week's incident findings into a scored **Risk Register** containing likelihood, impact, assigned owner, and risk treatment for each finding, accompanied by recommended organizational security policies.
