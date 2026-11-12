# Day 10: Social Engineering & OSINT (Hacking the Human)

## 🧠 What is Social Engineering?
Social engineering is the art of hacking people rather than machines. Because the human is often the weakest link in any security system, attackers exploit psychological triggers—**trust, fear, authority, curiosity, and helpfulness**—to trick targets into granting access or revealing sensitive information without needing a technical exploit.

### Psychological Triggers Exploited
* **Authority:** Impersonating leadership or technical support (*"I'm from IT / the CEO"*).
* **Urgency:** Manufacturing panic to force hasty mistakes (*"Do this in the next 5 minutes"*).
* **Social Proof:** Exploiting herd behavior (*"Everyone else on the team has already completed this"*).
* **Liking & Reciprocity:** Building rapport or offering an unsolicited favor before asking for something in return.

---

## 🎭 Core Social Engineering Techniques

* **Pretexting:** Inventing a believable scenario or identity after doing homework on the target (*"Hi, it's Raj from IT, we're migrating mailboxes—I just need your current password"*). Legitimate IT staff will never ask for your password.
* **Baiting:** Leaving a tempting physical or digital trap, such as a USB drive labeled *"Salaries 2026"* in a parking lot.
* **Tailgating:** Physically following an authorized badge-holder through a secure access door without authenticating.
* **Quid Pro Quo:** Offering a fake benefit or service (e.g., *"free IT troubleshooting"*) in exchange for login credentials or system access.

### Message-Based Con Vectors
* **Phishing:** Fraudulent emails sent broadly to harvest credentials or deliver malware.
* **Spear Phishing:** Highly targeted phishing aimed at a specific individual or organization using researched details.
* **Vishing (Voice Phishing):** Phone calls impersonating trusted institutions (e.g., a fake bank fraud agent asking you to "confirm" an OTP that actually authorizes an outgoing transfer).
* **Smishing (SMS Phishing):** Deceptive text messages containing malicious links or urgent alerts.

---

## 🔍 OSINT (Open-Source Intelligence)
OSINT is the legal collection and analysis of information from publicly available sources. Attackers use OSINT to build an intelligence profile on a target before launching an attack.

### Primary Intelligence Sources
* **LinkedIn:** Reveals employee names, roles, reporting structures, and internal org charts.
* **Job Postings:** Exposes an organization's exact tech stack (e.g., *"Must know Fortinet and Office 365"*).
* **GitHub:** Frequently exposes leaked API keys, hardcoded credentials, and internal project names.
* **Data Breach Repositories:** Provides historical leaked emails and reused passwords.

### Digital Footprint & Tradecraft
* **Digital Footprint:** Scattered public details combine into an actionable attack profile (e.g., a *"First day at work!"* selfie exposing an employee badge template, office address, and team members).
* **Google Dorks:** Advanced search operators used to uncover exposed sensitive files indexed by search engines:
  * `site:example.com` — Restricts search to a single domain.
  * `filetype:xlsx` / `filetype:pdf` — Searches for specific document types (e.g., exposed staff spreadsheets).
  * `intitle:"index of"` — Finds open, misconfigured web directories.
  * `inurl:login` — Locates administrative or portal login pages.
* **Metadata Analysis:** Hidden file properties (author names, software versions, edit history, GPS coordinates) embedded inside photos and documents. Tools like `exiftool` extract this in seconds—always strip metadata before sharing files publicly.
* **Sock Puppets:** Non-attributable, anonymous research accounts used during OSINT investigations to avoid alerting the target via profile view notifications.

---

## 🔗 Chaining Attacks & Watering Holes

### Combining OSINT with Social Engineering
Attackers chain minor public facts (`Name + Role + Email Format + Active Project + Personal Detail`) to craft spear-phishing messages convincing enough to bypass skepticism:
> *"Hi Priya, following up on the Acme migration before your leave on Friday—here's the updated doc."*  
> Every detail is accurate, lowering the victim's guard before opening a malicious attachment.

### Watering-Hole Attacks
Instead of contacting targets directly, attackers identify websites frequently visited by a specific group or industry, compromise those trusted sites, and wait for targets to infect themselves.

---

## 🛡️ Defense, Footprint Reduction & Ethics

### 1. Personal Defense
* **Pause and Verify:** Never let urgency bypass verification. Confirm unusual requests (like urgent wire transfers or gift card requests) through a **separate, trusted channel** (e.g., calling the sender directly on a known number).
* **Shrink Your Footprint:** Tighten social media privacy settings, avoid posting real-time locations or work badges, and delete unused accounts (*"You can't phish what you can't find"*).

### 2. Organizational Defense
* Conduct regular security awareness training and **educational phishing simulations** (which can reduce click rates from ~30% to ~4%).
* Enforce strict multi-channel verification procedures for financial transfers and sensitive data requests.
* Maintain a **blameless reporting culture** backed by a one-click *"Report Phishing"* button so incidents are caught early.

### 3. Legal & Ethical Boundaries
* Collecting publicly available information is generally legal, but using deception to extract private data or gain unauthorized access is illegal.
* Only perform OSINT or social engineering assessments against individuals and organizations where you hold explicit written authorization.
