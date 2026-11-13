# Day 11: Hardening Systems (Shrinking the Attack Surface)

## 🛡️ What is System Hardening?
Hardening is the process of reducing a system's **attack surface** by removing, disabling, and locking down unnecessary software, services, ports, and accounts. A fresh server often ships with dozens of active services "to be helpful"—turning off the ones nobody uses immediately eliminates potential entry points.

> 💡 **Core Principle:** *You can't exploit a service that isn't running.*

### Key Concepts & Standards
* **Attack Surface:** The sum of all potential entry points an attacker can target—open ports, running services, user accounts, installed software, and exposed network interfaces.
* **Security Baselines:** A documented, known-good secure configuration applied consistently across systems so security posture is standardized and configuration drift can be measured (e.g., **CIS Benchmarks**, **DISA STIGs**).
* **CIS Benchmarks:** Free, consensus-driven hardening guides from the Center for Internet Security for operating systems, cloud platforms, and applications, complete with step-by-step settings, rationale, and audit checks.

---

## 🔒 Locking Down the System

### 1. Accounts & Access Control
* Enforce the **Principle of Least Privilege** across all user and service accounts.
* Remove default, guest, and unused legacy accounts (e.g., forgotten `test` accounts).
* Separate administrative accounts from standard day-to-day user accounts and enforce strong authentication.

### 2. Services & Network Ports
* Disable all unnecessary background services and close their associated ports.
* Bind remaining services strictly to the interfaces that require access (e.g., bind MySQL port `3306` to `localhost` rather than exposing it to the public internet).

### 3. SSH Hardening (`/etc/ssh/sshd_config`)
SSH is the primary external target on Linux servers. Lock it down using:
* **Key-Based Authentication:** Disable password logins (`PasswordAuthentication no`).
* **Disable Root Login:** Prevent direct root access over SSH (`PermitRootLogin no`).
* **Account Whitelisting:** Restrict access to explicit users (`AllowUsers <username>`).
* **Brute-Force Protection:** Deploy `fail2ban` to automatically block repeated failed login attempts.

### 4. Host Firewalls
Configure a host-level firewall (`ufw` or `iptables` on Linux; Windows Defender Firewall on Windows) using a **default-deny inbound** policy, explicitly allowing only required ports:
```bash
ufw allow 443
ufw allow 22
ufw enable
