# HawkEye Network Forensics Investigation

## CyberDefenders – HawkEye Lab

This repository documents my investigation of the HawkEye
Network Forensics lab from CyberDefenders.

The objective of this investigation is to analyze captured
network traffic, reconstruct the attack sequence, identify
Indicators of Compromise (IOCs), investigate malware delivery,
and analyze potential data exfiltration.

## Investigation Objectives

- Analyze PCAP network traffic
- Identify the infected host
- Investigate DNS activity
- Analyze HTTP traffic
- Identify malware delivery
- Investigate SMTP communication
- Analyze potential data exfiltration
- Decode encoded data
- Identify Indicators of Compromise
- Reconstruct the attack timeline

## Tools Used

- Wireshark
- CyberChef
- VirusTotal
- WHOIS
- VMware
- Ubuntu

## Environment

The investigation is performed inside a VMware virtual
machine to provide an isolated analysis environment.

Malware samples are not executed as part of this
network-forensics investigation.

## Repository Structure

```text
hawkeye-network-forensics/
├── README.md
├── report/
│   └── HawkEye_Final_Report.md
├── findings/
│   ├── answers.md
│   ├── iocs.md
│   └── timeline.md
├── notes/
│   ├── day1.md
│   ├── day2.md
│   ├── day3.md
│   └── day4.md
├── screenshots/
└── references/
    └── tools.md
