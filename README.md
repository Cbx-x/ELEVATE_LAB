🔐 Task 1 – Scan Your Local Network for Open Ports
📌 Internship: Elevate Lab – Cyber Security Internship
🛠 Tool Used: Nmap (Wireshark – Optional)
🎯 Objective

The objective of this task is to discover open ports on devices within my local network in order to understand network exposure and identify potential security risks.

This task focuses on basic network reconnaissance and service enumeration.

🌐 Step 1 – Identify Local Network Range

Using:

ifconfig


I identified my active interface:

IP Address: 192.168.218.135

Subnet Mask: 255.255.255.0

Therefore, my network range is:

192.168.218.0/24

🔎 Step 2 – Perform TCP SYN Scan

Command used:

sudo nmap -sS 192.168.218.0/24


Explanation:

-sS → TCP SYN (Half-open) scan

/24 → Scan entire subnet (254 possible hosts)

To save results:

sudo nmap -sS 192.168.218.0/24 -oN scan_results.txt

📊 Scan Results

(Attach your actual findings here)

Example format:

IP Address	Open Ports	Service
192.168.218.1	80/tcp	HTTP
192.168.218.135	22/tcp	SSH
🧠 Analysis of Open Ports
1️⃣ Port 22 – SSH

Used for remote login.

Risk: Brute-force attacks if weak passwords are used.

2️⃣ Port 80 – HTTP

Web service.

Risk: Unencrypted communication.

3️⃣ Port 445 – SMB (if found)

File sharing service.

Risk: Ransomware and remote exploitation.

Open ports increase the attack surface of a system.

🔍 Optional – Wireshark Analysis

Wireshark can be used to capture packets during the scan.

Filter used:

tcp.flags.syn == 1


Observation:

SYN packets sent from scanner.

SYN-ACK responses from open ports.

RST packets sent by Nmap to avoid completing handshake.

This confirms how TCP SYN scan works at packet level.

🔐 Security Risks Identified

Exposed remote access services

Possible outdated service versions

Lack of firewall filtering

Potential brute-force attack vectors

🛡 Mitigation Recommendations

Disable unused services

Configure firewall rules

Use strong authentication

Keep services updated

Restrict remote access

📚 Key Concepts Learned

Port Scanning

TCP SYN Scan

Network Reconnaissance

IP Ranges & Subnetting

Service Enumeration

Attack Surface Analysis

🎯 Conclusion

This task helped me understand how attackers identify exposed services in a network. By performing a TCP SYN scan, I was able to map active hosts and analyze open ports.

Network reconnaissance is the first step in ethical hacking and defensive cybersecurity.
