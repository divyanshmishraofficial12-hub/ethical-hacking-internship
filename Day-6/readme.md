# Day 6: How the Internet Works (IP, Ports, DNS & Firewalls)

## 🌐 Network Addressing & Identifiers

### IP Addresses (Layer 3)
* **IPv4 vs. IPv6:** IPv4 uses 32-bit dotted-decimal notation (e.g., `192.168.1.10`); IPv6 uses 128-bit hexadecimal notation (e.g., `2001:db8::1`).
* **Private IP Ranges (RFC 1918):** Used within local area networks (LANs) and not routable on the public internet:
  * `10.0.0.0` – `10.255.255.255`
  * `172.16.0.0` – `172.31.255.255`
  * `192.168.0.0` – `192.168.255.255`
* **Public IP:** Assigned by the ISP, representing the network edge on the public internet.

### MAC Addresses (Layer 2)
* **Physical Address:** A 48-bit hardware identifier burned into the Network Interface Card (NIC) (e.g., `3C:5A:B4:12:34:56`).
* **Structure:** The first 3 bytes represent the Organizationally Unique Identifier (OUI / Manufacturer).
* **Security Consideration:** Operates strictly inside local subnets. Can be easily spoofed using software tools, making MAC filtering an ineffective standalone security control.

---

## 🏗️ Architectural Models: OSI vs. TCP/IP

### The 7-Layer OSI Model
Mnemonic: *"Please Do Not Throw Sausage Pizza Away"*

| Layer # | Layer Name | Functions & Data Units | Protocols & Concepts |
| :--- | :--- | :--- | :--- |
| **7** | **Application** | Human-computer interaction | HTTP, HTTPS, DNS, SSH, FTP, SMTP |
| **6** | **Presentation** | Data formatting, encryption, compression | TLS/SSL, JPEG, ASCII |
| **5** | **Session** | Session maintenance & connection setup | NetBIOS, RPC |
| **4** | **Transport** | End-to-end communication (Segments/Datagrams) | TCP, UDP, Port numbers |
| **3** | **Network** | Path determination & IP routing (Packets) | IPv4, IPv6, ICMP, IPsec |
| **2** | **Data Link** | Physical addressing & switching (Frames) | MAC addresses, Ethernet, Switches, VLANs |
| **1** | **Physical** | Binary transmission across physical media (Bits) | Cables, Fiber, Wi-Fi radio waves |

### TCP vs. UDP (Transport Layer)
* **TCP (Transmission Control Protocol):** Connection-oriented, reliable, orders packets, retransmits lost data.
  * **3-Way Handshake:** `SYN` → `SYN-ACK` → `ACK`.
  * **Use Cases:** Web (HTTP/S), Email (SMTP), File transfer (FTP), Remote access (SSH).
* **UDP (User Datagram Protocol):** Connectionless, lightweight, fast, no delivery guarantees.
  * **Use Cases:** DNS queries, streaming video, VoIP, online gaming.

---

## 🚪 Ports & Key Services

Ports (0–65535) route network traffic to specific applications running on a host:

| Port | Service | Description | Security Risk / Context |
| :--- | :--- | :--- | :--- |
| **21** | FTP | File Transfer Protocol | Unencrypted data & password transmission |
| **22** | SSH | Secure Shell | Encrypted remote command line administration |
| **25** | SMTP | Simple Mail Transfer Protocol | Email routing between servers |
| **53** | DNS | Domain Name System | Name resolution (UDP/TCP) |
| **80** | HTTP | Hypertext Transfer Protocol | Unencrypted web traffic |
| **443** | HTTPS | HTTP Secure | Web traffic encrypted via TLS |
| **445** | SMB | Server Message Block | File sharing (Targeted by EternalBlue/WannaCry) |
| **3306** | MySQL | MySQL Database | Database service (Should not face public internet) |
| **3389** | RDP | Remote Desktop Protocol | Windows Remote Desktop (Primary target for ransomware entry) |

---

## 🔀 Core Network Services & Infrastructure

* **DNS (Domain Name System):** Resolves human-readable domain names to IP addresses via UDP port 53.
  * **Resolution Hierarchy:** Resolver → Root Server → TLD Server (`.com`) → Authoritative Nameserver.
* **DHCP (Dynamic Host Configuration Protocol):** Automatically configures network parameters (IP, Subnet Mask, Gateway, DNS).
  * **DORA Process:** `Discover` → `Offer` → `Request` → `Acknowledge`.
* **NAT (Network Address Translation):** Allows multiple private host IPs to share a single public ISP address, acting as a natural boundary against unsolicited inbound connections.
* **Network Devices:**
  * **Switch (Layer 2):** Forwards frames within a local network using MAC address tables.
  * **Router (Layer 3):** Routes packets across different subnets using IP address tables.
  * **Firewall:** Filters traffic using predefined rules (IPs, ports, protocols). Enforces a **Default Deny Inbound** posture.

---

## ⚠️ Network Attack Vectors & Mitigation

* **Man-In-The-Middle (MitM):** Attackers position themselves between communicating parties to inspect or alter traffic.
* **ARP Spoofing:** Exploits the unauthenticated nature of ARP by broadcasting fake MAC-to-IP pairings to redirect local traffic through the attacker's machine.
* **Network Segmentation:** Isolates subnets into dedicated Virtual LANs (VLANs) with firewalls restricting inter-VLAN movement, containing potential breach lateral movement.

---

## 🛠️ CLI Network Reconnaissance Commands

* `ping <target>`: Test reachability and round-trip time (RTT) via ICMP Echo Requests.
* `traceroute <target>` / `tracert <target>`: Trace the hop-by-hop router path to a destination.
* `nslookup <domain>`: Query DNS servers to check IP resolution records.
* `netstat -ano` / `ss -tulpn`: Inspect active network sockets, listening ports, and associated Process IDs (PIDs).
