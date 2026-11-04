# Day 3: Identity & Authentication (Passwords, Hashing & MFA)

## 🔑 Identity, Authentication & Authorization
* **Identity:** Who you claim to be (e.g., account name or username).
* **Authentication:** Proving you are who you claim to be (e.g., passwords, security keys).
* **Authorization:** Determining what resources or actions you are permitted to access.
* **Real-World Analogy:** Ticket name (Identity) → Passport check (Authentication) → Boarding pass gate access (Authorization).

### The Three Authentication Factors
1. **Something You Know:** Passwords, PINs, or passphrases.
2. **Something You Have:** Authenticator apps, hardware security keys, or SMS codes.
3. **Something You Are:** Biometric data (fingerprints, facial recognition).

---

## ⚠️ Passwords & Attack Vectors
Weak, reused, or predictable passwords account for over 80% of data breaches.

* **Passphrase vs. Password:** A 4-word random passphrase (e.g., `correct horse battery staple`) is longer, harder to crack, and easier to remember than short "complex" passwords (e.g., `Tr0ub4dor&3`).
* **Common Cracking Methods:**
  * **Brute Force:** Testing every potential character combination.
  * **Dictionary Attack:** Attempting known word lists and common password variations.
  * **Credential Stuffing:** Automating logins using leaked credentials from previous data breaches.
  * **Rainbow Tables:** Matching hashes against precomputed lookup tables.

---

## 🔐 Hashing and Salting
Websites must store passwords using cryptographic hashes, never in plain text.

* **Hashing:** A one-way mathematical function converting a password into a fixed-length string (e.g., SHA-256).
* **Salting:** Adding random data to the password before hashing. This ensures identical passwords produce distinct hashes and neutralizes rainbow table attacks.
* **Secure Algorithms:** `Argon2` and `bcrypt` are purpose-built for password hashing; standalone SHA-256 is not recommended for password storage.

---

## 🛡️ Multi-Factor Authentication (MFA) & Passkeys
Enabling MFA blocks roughly 99% of automated attacks by requiring a second factor.

### MFA Ranking (Strongest to Weakest)
1. **Hardware Security Keys:** (e.g., YubiKey) — Phishing-resistant.
2. **Authenticator Apps:** Generates time-based one-time passwords (TOTP).
3. **Push Notifications:** Susceptible to **MFA Fatigue (Push Bombing)** attacks (e.g., 2022 Uber breach).
4. **SMS / Email Codes:** Vulnerable to SIM-swapping and account recovery exploits.

### Advanced Concepts
* **Passkeys:** Passwordless authentication relying on public/private key pairs and local biometrics. Immune to standard phishing.
* **Single Sign-On (SSO):** Centralized login system reducing total password footprint across services.
* **Principle of Least Privilege:** Granting users minimum necessary system permissions to minimize impact if an account is compromised.
