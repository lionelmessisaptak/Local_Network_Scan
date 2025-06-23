# Local Network Scan using Nmap

This project demonstrates the use of Nmap to scan a local network, identify active hosts, discover open ports, and assess potential vulnerabilities. It includes detailed analysis and captures network behavior during the scan using Wireshark.

## Objective

- Scan the local network (`192.168.0.0/24`) to find active hosts
- Discover open TCP ports and running services
- Analyze vulnerabilities associated with exposed services
- Capture and observe network traffic during the scan

## Tools Used

- Nmap 7.95
- Wireshark
- Linux terminal

## Scan Command Used

/bin/bash
nmap -sS 192.168.0.0/24

-sS: TCP SYN scan (stealth scan)

Results Summary
Hosts Found
192.168.0.1 (TP-Link Router)

192.168.0.104

192.168.0.106

Open Ports on 192.168.0.1
Port	Service	Description
22	SSH	Secure Shell access
53	DNS	Domain Name System
80	HTTP	Web server (unencrypted)
1900	UPNP	Unusual to see on TCP, potential misconfiguration

Vulnerability Overview
SSH (22): Risk of brute-force attacks, weak credentials

DNS (53): Vulnerable to cache poisoning, amplification, or misconfigured zone transfers

HTTP (80): Susceptible to injection attacks, outdated server issues

UPNP (1900): Can expose internal devices, enable RCE or DDoS vectors

Mitigation recommendations are included in the Open Port Details and Vulnerabilities.txt.

Network Behavior (Wireshark)
During the scan, TCP SYN packets were observed from the scanner (192.168.0.6) to the router (192.168.0.1). These packets stopped once the scan completed, confirming Nmap’s SYN scanning behavior.

Files Included
Scan_details.txt: Raw Nmap scan output

Open Port Details and Vulnerabilities.txt: Port descriptions and known vulnerabilities

Local_Network_Scan-NMAP.html: Formatted Nmap output

Wireshark_Packets.pdf: Screenshot of captured network packets

Conclusion
This scan reveals how even a small number of exposed ports can present meaningful attack surfaces if not properly configured. Regular network scanning and auditing can help identify and mitigate these exposures proactively.
