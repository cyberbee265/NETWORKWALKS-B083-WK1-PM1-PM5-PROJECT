# NETWORKWALKS-B083-WK2-PM1-PM5-PROJECT
Hands-on cybersecurity lab documenting web reconnaissance, DNS enumeration, WAF detection, HTTP analysis and authorized network discovery using Kali Linux, WHOIS, nslookup, DNSRecon, WhatWeb, WAFW00F, cURL and Nmap/Zenmap.

**PENETRATION TESTING REPORT**

📌 Project Overview

As part of my cybersecurity learning journey, I completed a hands-on Web Reconnaissance, DNS Enumeration and Network Discovery exercise using Kali Linux, VirtualBox and Nmap.

The objective of this project was to understand how security professionals gather information about a target during the reconnaissance phase and how different tools provide different pieces of information.

For the web reconnaissance stage, I used networkwalks.com to practice passive and non-intrusive information gathering with:

WHOIS

nslookup

DNSRecon

WhatWeb

WAFW00F

cURL


I also downloaded and installed Nmap/Zenmap on Windows and used it to perform network discovery and port scanning within my own environment.

> Ethical note: The web reconnaissance activities were performed for educational purposes. Network scanning should only be conducted against systems and networks that you own or have explicit authorization to test.




---

🧰 Tools & Technologies

Tool Purpose

Kali Linux Cybersecurity testing environment
VirtualBox Virtualization and lab environment
WHOIS Domain registration and ownership information
nslookup DNS resolution
DNSRecon DNS enumeration
WhatWeb Web technology fingerprinting
WAFW00F Web Application Firewall detection
cURL HTTP response/header analysis
Nmap Network discovery and port scanning
Zenmap Graphical interface for Nmap
Windows CMD Local network configuration and troubleshooting



---

1️⃣ WHOIS Enumeration

I started the reconnaissance process with WHOIS:

whois networkwalks.com

WHOIS provided publicly available domain information, including:

Domain name

Registrar

Registration information

Domain status

Name servers


This helped me understand how publicly available registration information can be used during the reconnaissance stage.

I also encountered an initial DNS-related problem where WHOIS returned:

Temporary failure in name resolution

This became one of the challenges I had to troubleshoot during the project.


---

2️⃣ DNS Enumeration with nslookup

I used nslookup to resolve the domain:

nslookup networkwalks.com

Initially, the command failed because Kali could not communicate with the DNS server:

communications error to 8.8.8.8#53: host unreachable
no servers could be reached

After troubleshooting my network configuration, I was able to successfully resolve the domain.

The successful result returned an address for:

networkwalks.com

This gave me practical experience with DNS resolution and helped me understand how DNS connects domain names to IP addresses.


---

3️⃣ DNSRecon

Next, I performed DNS enumeration using:

dnsrecon -d networkwalks.com

The tool identified several DNS records, including:

SOA records

NS records

A records

MX records

TXT records

SRV records


The exercise helped me understand how DNS records can reveal information about the infrastructure supporting a domain.


---

4️⃣ WhatWeb

I used WhatWeb to fingerprint the technologies used by the website:

whatweb networkwalks.com

The results provided information about the website's technology stack.

Among the information observed were technologies associated with:

Apache

WordPress

jQuery

Bootstrap

Other web components


This demonstrated how technology fingerprinting can help a security analyst understand what technologies may be running behind a web application.


---

5️⃣ WAFW00F

I also used WAFW00F to determine whether a Web Application Firewall could be identified:

wafw00f https://networkwalks.com

The result indicated the presence of:

ModSecurity (SpiderLabs) WAF

This was an interesting part of the exercise because it showed me how defensive technologies can sometimes be fingerprinted during reconnaissance.


---

6️⃣ cURL

I used cURL to examine the HTTP response from the website:

curl -I https://networkwalks.com

This allowed me to inspect HTTP response headers and other information returned by the web server.

I observed information such as:

HTTP/2 200
server: Apache
content-type: text/html

I also observed security-related headers and other HTTP information.

This helped me understand how much useful information can sometimes be obtained simply by examining an application's HTTP responses.


---

7️⃣ Nmap & Zenmap

Another major part of the project was learning how to use Nmap.

I downloaded and installed Nmap/Zenmap on my Windows system.

I used Zenmap to perform a scan against my local host:

127.0.0.1

The scan identified the host as being up and reported open TCP ports including:

135/tcp open msrpc
445/tcp open microsoft-ds
5357/tcp open wsdapi

This helped me understand the relationship between:

IP address → open ports → services

For example, Nmap identified port 445 as associated with Microsoft-DS/SMB-related services.

I also used Windows networking commands such as:

ipconfig

to examine my network interfaces, IPv4 addresses, subnet masks and gateways.


---

🌐 Network Configuration & Troubleshooting

One of the most challenging parts of the project was getting my Kali Linux network working correctly inside VirtualBox.

At one point, Kali showed:

eth0 ethernet disconnected

I created a NetworkManager connection:

sudo nmcli connection add type ethernet ifname eth0 con-name eth0-dhcp ipv4.method auto

The connection was successfully created, but attempting to activate it resulted in:

Connection activation failed:
IP configuration could not be reserved

I then restarted NetworkManager:

sudo systemctl restart NetworkManager

After restarting it, the interface changed to:

eth0 ethernet connecting (getting IP configuration)

I also checked the interface and routing configuration using:

ip -br addr

and:

ip route

At one stage, I was able to communicate with my local virtual machine:

10.0.2.2

but external connectivity to:

8.8.8.8

was initially unsuccessful.

Eventually, I was able to establish external connectivity and successfully perform DNS queries against networkwalks.com.


---

🧩 Challenges Encountered

This project taught me that cybersecurity isn't just about knowing commands. Troubleshooting is a major part of the job.

Challenge 1 — Kali Network Connectivity

Kali initially showed the Ethernet interface as disconnected.

Challenge 2 — DHCP

The interface was detected but struggled to obtain an IP address.

Challenge 3 — DNS Resolution

nslookup initially returned:

host unreachable

and:

no servers could be reached

Challenge 4 — Routing

I had to inspect my routing table and understand how traffic was being directed through the virtual network.

Challenge 5 — Understanding Tool Output

Another challenge was learning that simply running a command isn't enough.

I had to understand what the output meant, what information was relevant and how the result of one tool could guide the next stage of the investigation.


---

🧠 Key Lessons Learned

This project gave me practical experience with several important cybersecurity concepts.

🔹 Reconnaissance

I learned how different reconnaissance tools complement each other.

🔹 DNS

I gained a better understanding of:

A records

NS records

MX records

TXT records

SRV records

SOA records


🔹 Web Fingerprinting

I learned how tools such as WhatWeb can help identify technologies used by a web application.

🔹 WAF Identification

WAFW00F demonstrated how defensive technologies such as ModSecurity can be detected during reconnaissance.

🔹 Network Discovery

Using Nmap helped me understand how to identify hosts, open ports and associated services within an authorized environment.

🔹 Linux Networking

Troubleshooting Kali gave me practical exposure to:

Network interfaces

DHCP

DNS

Routing

NetworkManager

VirtualBox networking



---

📊 Project Workflow

My overall workflow was:

VirtualBox
     ↓
Kali Linux Network Configuration
     ↓
DNS Connectivity
     ↓
WHOIS
     ↓
nslookup
     ↓
DNSRecon
     ↓
WhatWeb
     ↓
WAFW00F
     ↓
cURL
     ↓
Nmap / Zenmap
     ↓
Analyze & Document Results


---

📸 Evidence

Screenshots included in this repository document:

Kali Linux network configuration

DNS troubleshooting

Successful nslookup

WHOIS enumeration

cURL results

WAFW00F results

DNSRecon enumeration

VirtualBox lab configuration

Windows network configuration

Nmap/Zenmap scan results

Open ports discovered during the local scan



---

🎯 Conclusion

This project was more than simply running cybersecurity commands.

I started with basic reconnaissance and gradually connected the information gathered from different tools. When things didn't work, particularly with my Kali Linux networking and DNS resolution, I had to troubleshoot the underlying problem before continuing.

The experience reinforced an important lesson for me:

> Cybersecurity is not just about knowing the tools; it's about understanding the technology behind the tools, interpreting their results, troubleshooting problems and documenting your findings.



I'm continuing to build my practical cybersecurity skills through hands-on labs and projects, with a growing focus on network security, reconnaissance, vulnerability assessment, SOC operations and security monitoring.


---

👨‍💻 Author

Sulaimon Omobolaji Olore

Cybersecurity Learner | Network Security | Reconnaissance | Vulnerability Assessment
