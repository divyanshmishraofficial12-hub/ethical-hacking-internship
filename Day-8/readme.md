# Day 8: Reading Network Traffic with Wireshark

## 🦈 Why Packet Capture?
Logs can be edited or faked; **packets on the wire represent the ground truth**. Packet capture records actual data crossing the network to verify what truly occurred during a security incident.

---

## 📦 Wireshark & Packet Fundamentals
* **Wireshark:** The industry-standard network packet analyzer that decodes packet layers into human-readable structures.
* **The Encapsulation Onion:** Data is wrapped in headers layer by layer:  
  `Ethernet Frame (MAC)` ➔ `IP Packet (IP)` ➔ `TCP Segment (Port)` ➔ `Data Payload`
* **Capturing Best Practices:** Capture short targeted bursts (10–30 seconds) on the active network interface to prevent massive, unmanageable `.pcap` files.

---

## 🔍 Filters & The TCP Handshake

### Capture vs. Display Filters
* **Capture Filters:** Applied *before* recording; determines what data gets written to disk. (Data missed here cannot be recovered).
* **Display Filters:** Applied *after* recording; isolates specific traffic from the captured file.
* **Golden Rule:** *Capture broad, filter on display.*

### Key Display Filters
* `ip.addr == 10.0.0.5` – Isolate traffic involving a specific host.
* `tcp.port == 80` – Filter by specific service port.
* `http`, `dns`, `tls` – Filter by protocol type.
* Combine conditions using logical operators: `&&` (AND), `||` (OR), `!` (NOT).

### TCP Connection Lifecycle & Flags
* **3-Way Handshake:** `SYN` ➔ `SYN-ACK` ➔ `ACK` (Establishes a connection).
* **FIN:** Polite connection teardown.
* **RST:** Abrupt reset/connection termination.

---

## 🕵️ Identifying Attacks in Wireshark

### 1. Cleartext Password Sniffing & Following Streams
* **Follow Stream:** Right-click a packet ➔ **Follow ➔ TCP Stream** to reassemble the entire conversation into a readable transcript.
* Unencrypted protocols (**HTTP, FTP, Telnet**) expose credentials in plain sight (e.g., HTTP `POST` body data or Base64 `Authorization` headers).
* **Mitigation:** Enforce encrypted protocols (**HTTPS, SFTP, SSH**).

### 2. ARP Spoofing (Man-in-the-Middle)
* **Signature:** Multiple MAC addresses claiming ownership of the same IP address or a burst of unsolicited ARP responses.
* **Wireshark Warning:** Displays *"Duplicate use of IP address detected"*.

### 3. Port Scanning
* **Signature:** Rapid bursts of `SYN` packets sent to numerous ports from a single source IP in a short period.
* **Display Filter:** `tcp.flags.syn == 1 && tcp.flags.ack == 0`
* **Port Status Signals:** `SYN-ACK` (Open), `RST` (Closed), No response (Filtered by firewall).

### 4. Malware Beaconing (C2 Communication)
* **Signature:** Compromised hosts initiating clockwork, periodic connections to an external Command & Control (C2) IP address (e.g., contacting an external host every 15 seconds).
* **Analysis Menu:** Go to **Statistics ➔ Conversations** to rank top talkers and identify non-human traffic patterns.

---

## 💻 CLI Packet Capture: `tcpdump`
Used on headless Linux servers where no GUI is available:
```bash
# Capture traffic on eth0 interface and output to a pcap file
sudo tcpdump -i eth0 -w capture.pcap

# Read and inspect a pcap file directly from terminal
tcpdump -r capture.pcap
