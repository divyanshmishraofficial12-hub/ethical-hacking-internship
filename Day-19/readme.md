# Day 19: Cloud & Modern Security

## ☁️ Cloud Computing & The Shared Responsibility Model

### What the Cloud Means for Security
* The cloud is rented infrastructure over the internet—servers, storage, and services you do not physically own or control. Because organizations run their workloads in the cloud, attackers target it just as heavily.
* While you do not own the hardware, you remain accountable for securing everything you deploy on it.

### The Shared Responsibility Model
Security duties are split between the cloud provider and the customer:
* **Cloud Provider (Security *of* the Cloud):** Secures physical datacentres, hardware, underlying networking, and facilities.
* **Customer (Security *in* the Cloud):** Secures data, user access, permissions, and resource configurations.

> 💡 **Core Analogy:** *The provider locks the building; you still have to lock your own apartment.* Most cloud breaches occur on the customer's side of the line.

---

## ⚠️ Top Cloud Risks: Misconfiguration, IAM & Leaked Keys

### 1. Cloud Misconfiguration (#1 Cloud Risk)
* Leaving cloud resources configured insecurely—such as public storage buckets, open network ports, default settings, or overly broad permissions.
* Thousands of major breaches have resulted from storage buckets accidentally set to **public**, exposing millions of records with zero hacking required (*a checkbox left ticked*).

### 2. Identity & Access Management (IAM)
* **IAM** governs who can access what across cloud resources using users, roles, and permission policies.
* Applying the **Principle of Least Privilege** is the single most critical cloud security skill—granting an application full administrator access *"just to make it work"* allows an attacker who compromises that app to take over the entire cloud account.

### 3. Leaked Cloud Access Keys
* Cloud access keys act as master passwords for your infrastructure.
* Automated bots continuously scan public GitHub repositories; a cloud key committed to a public repo can be discovered and abused within minutes to spin up expensive crypto-mining servers (*the lifespan of an ice cube in July*).

---

## 🧩 Modern Attack Surfaces: APIs, Containers & DevSecOps

### API Security
* **APIs** connect modern services together and become prime targets when they lack proper authentication, expose excessive data, or omit rate limits—allowing attackers to alter a single ID parameter and leak records across accounts.

### Containers (Docker & Kubernetes)
* Containers package applications alongside their dependencies and power most modern cloud workloads.
* Building from a popular base image containing a known vulnerability propagates that flaw into every running container—making automated **container image scanning** essential.

### DevSecOps ("Shift Left")
* Integrates automated security checks directly into the CI/CD development pipeline so every commit is scanned for vulnerabilities and leaked secrets before deployment.
* *Fixing a security bug in development costs a coffee; fixing it after a breach costs the company.*

---

## 🛡️ Zero Trust Architecture

### Replacing the Castle-and-Moat Model
* Traditional security trusted everything inside the corporate network perimeter. Cloud adoption, remote work, and mobile devices erased that perimeter, making *"inside equals safe"* dangerous.
* **Zero Trust Principle:** *Never trust, always verify.* No user, service, or device is trusted implicitly based on network location—every access request is continuously authenticated, authorized, and validated (so even a stolen laptop on office Wi-Fi cannot access internal resources).

> 🏰 **Old Model:** Trust the castle walls.  
> 🔐 **Zero Trust:** Check ID at every door.

---

## 🤖 AI in Attack & Defence + Modern Account Security

### The AI Arms Race
* **Attackers Use AI For:** Flawless, hyper-personalized phishing in any language, voice and video deepfakes (such as the 2024 scam where a finance worker joined a video call with deepfakes of the CFO and colleagues and transferred $25 million), and automated vulnerability discovery.
* **Defenders Use AI For:** Spotting anomalies across massive log volumes, triaging SOC alerts, detecting novel malware behaviorally, and automating incident response.
* **New AI-Specific Risks:** Prompt injection, data poisoning, and employees pasting confidential company secrets into public AI tools.

### Evolving Account Attacks & Phishing-Resistant MFA
* Traditional MFA is increasingly challenged by **MFA fatigue** (push bombing), **SIM-swapping**, and **real-time phishing proxies**.
* **Solution:** Deploy **phishing-resistant MFA** using **passkeys** and hardware security keys.

---

## 🎯 Enduring Security Principles
Tools and cloud platforms evolve every year, but foundational principles remain constant:
1. Protect **Confidentiality, Integrity, and Availability (CIA)**.
2. Enforce **Least Privilege** across every identity and service.
3. **Never trust, always verify** every access request.

---

## 💻 Lab Activity & Homework for Day 20
* **Day 19 Cloud IAM Audit:** Review the sample cloud IAM policy and storage configuration, identify public access exposures and over-privileged permissions, and rewrite them to enforce least privilege.
* **Capstone Preparation:** Prepare your **CAPSTONE presentation** for Day 20 demo day.
