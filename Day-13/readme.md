# Day 13: Web Application Security — The OWASP Top 10

## 🌐 Why Web Application Security?
Web applications are always online, publicly reachable, and packed with logic that processes user input—making them the number-one attack target. While a firewall acts like a fortress wall, the web application is the open gate everyone is allowed to walk through. A single flaw in a login or checkout form can expose entire customer databases.

* **The OWASP Top 10:** A free, industry-standard awareness document maintained by the Open Worldwide Application Security Project (OWASP) outlining the most critical web application security risks.
* **Golden Rule of Web Security:** *All user input is guilty until proven innocent.*

---

## 💉 Injection & Cross-Site Scripting (XSS)

### 1. SQL Injection (SQLi)
* **Mechanism:** Occurs when untrusted user input is treated as executable code rather than data, altering the backend database query.
* **Example:** A vulnerable query like `SELECT * WHERE user='$input'` can be bypassed by entering `admin' --`, commenting out the password verification check and potentially dumping entire user tables.
* **Remediation:** Use **parameterised queries / prepared statements** so input is strictly handled as data.

### 2. Cross-Site Scripting (XSS)
* **Mechanism:** Injects malicious JavaScript into a trusted website so it executes inside other visitors' browsers—allowing attackers to steal session cookies, capture keystrokes, or redirect users.
* **Types:**
  * **Stored XSS:** Malicious script is permanently saved on the target server (e.g., in a comment section or user profile) and runs for every visitor.
  * **Reflected XSS:** Malicious script is embedded inside a crafted URL link and reflected back in the immediate server response.
* **Remediation:** Properly **encode output** before rendering and enforce a strong **Content-Security-Policy (CSP)**.

---

## 🔐 Access Control, Authentication & Configuration

### Broken Access Control (#1 Risk)
* **Mechanism:** Users access data or perform actions outside their intended permissions—such as **IDOR (Insecure Direct Object Reference)**, where changing `/invoice?id=1001` to `1002` reveals another customer's invoice due to a missing permission check.
* **Remediation:** Enforce server-side authorization checks on every single request and action.

### Broken Authentication
* **Mechanism:** Flaws in session and login management—allowing weak passwords, missing MFA, predictable session tokens, or no login lockout (enabling automated credential stuffing).
* **Remediation:** Enforce strong password policies, MFA, account lockouts/rate limiting, and secure session handling.

### Security Misconfiguration (Most Common Issue)
* **Mechanism:** Leaving insecure default configurations active, running debug mode in production, keeping default credentials (e.g., `admin/admin`), or leaving `/admin` panels exposed.
* **Remediation:** Harden configurations, remove default accounts/pages, and deploy minimal installations.

### Sensitive Data Exposure
* **Mechanism:** Failing to protect confidential data via missing encryption, storing passwords in plaintext, or leaking secrets in error responses and logs.
* **Remediation:** Encrypt all data in transit (HTTPS/TLS) and at rest, and hash passwords with strong algorithms.

### Cross-Site Request Forgery (CSRF)
* **Mechanism:** Tricks a logged-in user's browser into submitting an unintended state-changing request (e.g., changing an email or initiating a transfer) because browsers automatically attach session cookies.
* **Remediation:** Implement anti-CSRF tokens and configure `SameSite` cookie attributes.

### Additional OWASP Top 10 Risks
* **Insecure Design:** Missing security architecture and threat modeling from the start.
* **Vulnerable & Outdated Components:** Importing flawed third-party libraries (e.g., Log4Shell).
* **Software & Data Integrity Failures:** Trusting unverified updates, CI/CD pipelines, or serialized data.
* **Security Logging & Monitoring Failures:** Lack of visibility allowing breaches to go undetected.
* **Server-Side Request Forgery (SSRF):** Tricking the server into making unauthorized internal or external requests.

---

## 🔍 Testing & Exploitation Tools

### How Attackers Find Web Flaws
Attackers map the application's pages, parameters, and APIs, then fuzz every input with crafted payloads (single quotes, script tags, altered IDs) while observing responses and leaked database errors.

* **Burp Suite:** The industry-standard intercepting proxy sitting between your browser and the web server. It lets testers pause, inspect, and modify HTTP requests in flight (e.g., altering `price=1000` to `price=1` in a checkout request).
* **OWASP ZAP:** Open-source web application security scanner and proxy for automated and manual vulnerability discovery.

### Safe & Legal Practice Labs
* **DVWA (Damn Vulnerable Web Application):** Classic intentionally vulnerable web app with selectable difficulty levels (*Easy, Medium, Hard*).
* **OWASP Juice Shop:** Modern intentionally insecure web application featuring 100+ hands-on hacking challenges.

---

## 🛡️ Developer Defenses & Governance

### Secure Coding Checklist
1. **Validate and sanitise** all incoming user input on the server.
2. **Use parameterised queries** to eliminate SQL injection.
3. **Encode all output** and configure a CSP to prevent XSS.
4. **Enforce server-side access control** on every endpoint (never trust client-side checks).
5. **Enforce HTTPS** and keep all frameworks, dependencies, and libraries patched.

### Web Application Firewall (WAF)
* Sits in front of web applications (e.g., **Cloudflare**, **AWS WAF**, **ModSecurity**) to filter common injection and XSS traffic patterns.
* Provides valuable **defence in depth**, though it is not a replacement for secure code since crafted payloads can bypass filters.

### Responsible Disclosure & Bug Bounties
* Always report discovered flaws privately to the organization and allow time for remediation before public disclosure.
* Legal bug-bounty platforms such as **HackerOne** and **Bugcrowd** authorize researchers to test scoped targets and earn rewards for valid findings.

---

## 💻 Lab Activity & Homework
* **Objective:** Run **DVWA** or **OWASP Juice Shop** locally, safely identify and exploit three real vulnerabilities (**SQL Injection**, **XSS**, and **Broken Access Control**), and document the exact developer code fix for each.
