# Day 1 – HawkEye Network Forensics Lab

## Objective

Started the HawkEye Network Forensics lab from CyberDefenders as part of the cybersecurity internship assignment. The objective is to investigate a suspected malware infection and possible data exfiltration using network traffic analysis.

## Initial Exploration

I first explored the complete HawkEye lab scenario and reviewed the instructions and questions to understand the investigation requirements.

I learned that the lab focuses on reconstructing a suspected HawkEye keylogger-related incident by analyzing a provided PCAP file. The investigation involves identifying suspicious network activity, communication patterns, indicators of compromise (IoCs), and possible credential/data exfiltration.

## Safe Analysis Environment

The investigation was performed inside a VMware Ubuntu virtual machine to keep the analysis environment isolated from the host system.

The provided PCAP was opened in Wireshark for network traffic analysis.

## Initial Wireshark Analysis

I performed an initial examination of the PCAP using Wireshark.

The following areas were examined:

- Capture File Properties
- Packet count and capture duration
- Protocol Hierarchy Statistics
- Network Conversations
- Source and destination communication patterns

### Initial Capture Statistics

From Wireshark Capture File Properties:

- Total packets: 4003
- First packet displayed: 2019-04-11 02:07:07
- Last packet displayed: 2019-04-11 03:10:48
- Capture duration: 01:03:41
- Captured bytes: 2,390,126
- Average packet size: 597 bytes

Evidence:

![Wireshark Capture Statistics](../screenshots/01_capture_statistics.png)

## Protocol Analysis

I examined Wireshark's Protocol Hierarchy Statistics to understand the types of network traffic present in the capture.

The capture contains TCP and UDP traffic along with protocols including DNS, HTTP, SMTP, SMB/SMB2, TLS and other network protocols.

This initial analysis helped identify the protocols that may require deeper investigation during the next stages of the lab.

Evidence:

![Wireshark Protocol Hierarchy](../screenshots/02_protocol_hierarchy.png)

## Conversation Analysis

I also examined the Wireshark Conversations window to understand the communication between hosts.

The conversation statistics provide information about packet counts, transferred bytes, source/destination addresses and communication direction. This will be useful for identifying potentially significant hosts and network connections during the investigation.

Evidence:

![Wireshark Conversations](../screenshots/03_conversations.png)

## CyberDefenders Questions

I started solving the questions provided in the HawkEye lab.

### Q1 – How many packets does the capture have?

**Answer:** `4003`

The answer was verified using Wireshark Capture File Properties.

### Q2 – At what time was the first packet captured (UTC)?

The timestamp was identified from the capture properties, but the UTC conversion/input format still requires verification before recording the final answer.

### Q3 – What is the duration of the capture?

**Answer:** `01:03:41`

The duration was verified using Wireshark Capture File Properties.

## Tools Used

- VMware – isolated analysis environment
- Ubuntu – forensic analysis workstation
- Wireshark – packet capture and network traffic analysis
- CyberDefenders – Blue Team investigation lab

## Learning

Today I learned how to begin a network-forensics investigation from a PCAP file, examine basic capture statistics, understand protocol distribution, inspect network conversations, and connect packet-level evidence with investigation questions.

The next stage will focus on deeper analysis of DNS, HTTP, SMTP and other relevant traffic to identify suspicious activity and potential indicators of compromise.
