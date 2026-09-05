# HawkEye Network Forensics Investigation

![CyberDefenders](https://img.shields.io/badge/CyberDefenders-HawkEye-blue)
![Network Forensics](https://img.shields.io/badge/Focus-Network%20Forensics-orange)
![Wireshark](https://img.shields.io/badge/Tool-Wireshark-blue)
![CyberChef](https://img.shields.io/badge/Tool-CyberChef-green)


# HawkEye Network Forensics Investigation

> **CyberDefenders Network Forensics Challenge | Wireshark | CyberChef | PCAP Analysis**

---

## 📌 Project Overview

This repository documents a complete **Network Forensics investigation** of the **HawkEye** challenge from CyberDefenders.

The investigation was performed using a controlled Ubuntu virtual machine environment with **Wireshark** and **CyberChef**.

The objective was to analyze the provided network capture, reconstruct the attack activity, identify the compromised system, investigate malicious network communication, identify the downloaded malware, and determine how stolen information was exfiltrated.

The investigation successfully solved **24/24 questions** from the HawkEye challenge.

---

## 🎯 Investigation Objectives

The investigation focused on:

- Analyzing the provided PCAP file.
- Identifying active systems within the organization.
- Investigating Ethernet and IPv4 conversations.
- Identifying the organization's DNS server.
- Analyzing suspicious DNS requests and responses.
- Identifying malicious HTTP traffic.
- Identifying the downloaded malware.
- Calculating and verifying the malware MD5 hash.
- Identifying the malware-hosting web server.
- Identifying the victim's public IP address.
- Analyzing SMTP communication.
- Identifying the email account used for data exfiltration.
- Recovering and decoding SMTP authentication information.
- Identifying the malware variant.
- Identifying stolen credentials within the exfiltrated data.
- Determining the data-exfiltration frequency.
- Documenting Indicators of Compromise (IoCs).
- Reconstructing the investigation timeline.

---

# 🛠️ Tools & Technologies

| Tool / Technology | Purpose |
|---|---|
| **Wireshark** | Packet capture and network traffic analysis |
| **CyberChef** | Base64 decoding and data analysis |
| **Ubuntu Linux** | Forensic analysis environment |
| **VMware** | Isolated virtual machine environment |
| **WHOIS / IP Lookup** | External infrastructure verification |
| **Git** | Version control |
| **GitHub** | Investigation documentation and project repository |

---

# 🔬 Investigation Methodology

The investigation followed a structured network-forensics workflow.

```text
                    HawkEye PCAP
                         |
                         v
                Capture Statistics
                         |
                         v
              Protocol & Conversations
                         |
             +-----------+-----------+
             |                       |
             v                       v
        Network Analysis        DNS Analysis
             |                       |
             |                       v
             |              Suspicious Domain
             |                       |
             |                       v
             |                 Domain IP
             |                       |
             +-----------+-----------+
                         |
                         v
                  HTTP Analysis
                         |
                         v
                Malware Download
                         |
                         v
                 File Hash Analysis
                         |
                         v
                  SMTP Analysis
                         |
                         v
                Data Exfiltration
                         |
                         v
                 Malware Analysis
                         |
                         v
               IoCs & Timeline

```

## Repository Structure

```text
HawkEye-Network-Forensics/
│
├── findings/
│   ├── answers.md
│   ├── iocs.md
│   └── timeline.md
│
├── notes/
│   ├── day1.md
│   ├── day2.md
│   ├── day3.md
│   └── day4.md
│
├── references/
│   └── tools.md
│
├── report/
│   └── HawkEye_Final_Report.md
│
├── screenshots/
│   ├── 01_capture_statistics.png
│   ├── 02_protocol_hierarchy.png
│   ├── 03_conversations.png
│   ├── 04_q04_ethernet_conversations.png
│   ├── 05_q07_q08_ipv4_conversations.png
│   ├── 07_q10_q11_dns_response.png
│   ├── 08_q12_ip_geolocation.png
│   ├── 09_q13_whois_evidence.png
│   ├── 10_q14_http_download.png
│   ├── 11_q15_md5_hash.png
│   ├── 12_q16_http_server.png
│   ├── 13_q17_victim_public_ip.png
│   ├── 14_q19_smtp_server_software.png
│   ├── 15_q20_email_recipient.png
│   ├── 16_q21_smtp_password_wireshark.png
│   ├── 17_q21_smtp_password_decoded.png
│   ├── 18_q22_q23_malware_and_bank_credentials.png
│   └── 19_q24_exfiltration_interval.png
│
├── .gitignore
└── README.md
