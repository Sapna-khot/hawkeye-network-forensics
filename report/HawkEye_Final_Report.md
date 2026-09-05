# HawkEye Network Forensics Investigation Report

## 1. Executive Summary

This report documents the investigation of the CyberDefenders HawkEye Network Forensics challenge using the provided network capture file.

The investigation was performed in an isolated Ubuntu virtual machine using Wireshark and CyberChef. Network traffic was analyzed to reconstruct the attack timeline, identify the compromised system, determine the malware download, and investigate the subsequent exfiltration of stolen information.

The investigation identified a malicious executable named `tkraw_Protected99.exe`, hosted on `proforma-invoices.com`. The downloaded file was verified using its MD5 hash. Further analysis of SMTP traffic revealed that the malware used an external email server to transmit stolen information.

The investigation successfully answered all 24 questions in the HawkEye lab.

---

## 2. Investigation Objectives

The primary objectives were:

- Analyze the provided PCAP file.
- Determine the structure and duration of the network capture.
- Identify the most active systems in the organization.
- Identify the organization's DNS server.
- Investigate suspicious DNS queries.
- Identify the malicious file downloaded by the victim.
- Determine the malware-hosting infrastructure.
- Identify the victim's public IP address.
- Analyze SMTP communication used for data exfiltration.
- Identify the malware variant.
- Recover evidence of stolen credentials.
- Determine the frequency of data exfiltration.
- Document relevant Indicators of Compromise (IoCs).
- Reconstruct the incident timeline.

---

## 3. Tools and Environment

### Analysis Environment

- Ubuntu Linux
- VMware virtual machine
- Wireshark
- CyberChef
- Web-based IP/WHOIS verification

### Investigation Data

- HawkEye network capture (`stealer.pcap`)

The malware executable was analyzed through static evidence such as its filename, MD5 hash, HTTP traffic, and network behavior. The executable was not executed.

---

## 4. Capture Overview

| Attribute | Finding |
|---|---|
| Total packets | 4003 |
| Capture duration | 01:03:41 |
| First packet (UTC) | 2019-04-10 20:37 |
| Most active link-level system | `00:08:02:1c:47:ae` |
| NIC Manufacturer | Hewlett-Packard |
| NIC Manufacturer Headquarters | Palo Alto |
| Internal computers involved | 3 |
| Most active network-level computer | `Beijing-5cd1-PC` |
| Organization DNS server | `10.4.10.4` |

---

## 5. Network Investigation

### 5.1 Link-Level Analysis

Ethernet conversations were analyzed to determine the most active system at the link level.

The most active MAC address was identified as:

`00:08:02:1c:47:ae`

The associated NIC manufacturer was identified as Hewlett-Packard.

The headquarters of Hewlett-Packard was identified as Palo Alto.

---

### 5.2 Network-Level Analysis

IPv4 conversations were analyzed to identify systems operating inside the organization's private `/24` network.

Three computers were identified as participating in the capture.

The most active network-level computer was:

`Beijing-5cd1-PC`

The organization's internal DNS server was identified as:

`10.4.10.4`

---

## 6. DNS Investigation

Packet 204 was examined to identify the domain requested by the victim.

The queried domain was:

`proforma-invoices.com`

The domain resolved to:

`217.182.138.150`

External IP verification identified the associated country as:

`France`

The DNS activity provided the first significant indicator connecting the victim's network activity to the malicious infrastructure.

---

## 7. Victim System Identification

HTTP traffic was analyzed to identify information about the victim's operating system.

The HTTP User-Agent contained:

`Windows NT 6.1`

The victim was therefore identified as running a Windows operating system corresponding to Windows NT 6.1.

The public IP address associated with the victim was identified as:

`173.66.146.112`

---

## 8. Malware Download Investigation

HTTP traffic was analyzed to identify files downloaded by the victim.

The malicious executable was:

`tkraw_Protected99.exe`

The HTTP request showed the executable being downloaded from:

`proforma-invoices.com`

The MD5 hash of the downloaded file was verified as:

`71826ba081e303866ce2a2534491a2f7`

The malware-hosting web server was identified as:

`LiteSpeed`

The executable was treated as malware and was not executed during the investigation.

---

## 9. SMTP Exfiltration Investigation

SMTP traffic was analyzed to investigate the transmission of stolen information.

The external email server was associated with the United States.

The SMTP server software was identified as:

`Exim 4.91`

The stolen information was sent to:

`sales.del@macwinlogistics.in`

The SMTP authentication process exposed a Base64-encoded password.

The encoded value was decoded using CyberChef and produced:

`Sales@23`

This demonstrated that the malware used SMTP authentication to send the collected information.

---

## 10. Malware Identification

Analysis of the extracted data revealed the malware variant:

`HawkEye Keylogger - Reborn v9`

The malware was responsible for collecting information from the victim system and transmitting the collected data through email.

---

## 11. Credential Theft Evidence

The exfiltrated information contained credentials associated with Bank of America.

The recovered credential pair was:

`roman.mcguire:P@ssw0rd$`

This information demonstrates that the malware was capable of collecting browser/account credentials from the compromised system.

The recovered credential is included strictly as forensic evidence from the controlled CyberDefenders lab environment.

---

## 12. Exfiltration Frequency

SMTP communication was examined to identify repeated extraction activity.

The investigation determined that the collected information was exfiltrated every:

`10 minutes`

Repeated SMTP/EHLO communication supported the periodic nature of the data-exfiltration mechanism.

---

## 13. Incident Timeline

| Stage | Finding |
|---|---|
| Initial capture | Network activity begins in the recorded PCAP |
| DNS activity | Victim queries `proforma-invoices.com` |
| DNS resolution | Domain resolves to `217.182.138.150` |
| HTTP activity | Victim connects to the malicious web infrastructure |
| Malware download | `tkraw_Protected99.exe` is downloaded |
| File verification | MD5 identified as `71826ba081e303866ce2a2534491a2f7` |
| Malware identification | HawkEye Keylogger - Reborn v9 identified |
| SMTP connection | Victim communicates with external Exim mail infrastructure |
| Authentication | SMTP authentication uses recovered credentials |
| Exfiltration | Stolen information is sent to `sales.del@macwinlogistics.in` |
| Repeated activity | Data is exfiltrated every 10 minutes |

---

## 14. Indicators of Compromise

### Network Indicators

| Type | Indicator |
|---|---|
| Suspicious domain | `proforma-invoices.com` |
| Domain IP | `217.182.138.150` |
| Victim public IP | `173.66.146.112` |
| Internal DNS | `10.4.10.4` |
| SMTP server IP | `23.229.162.69` |

### File Indicator

| Type | Indicator |
|---|---|
| Filename | `tkraw_Protected99.exe` |
| MD5 | `71826ba081e303866ce2a2534491a2f7` |

### Email Indicators

| Type | Indicator |
|---|---|
| Recipient | `sales.del@macwinlogistics.in` |
| SMTP software | Exim 4.91 |
| Authentication password | `Sales@23` |

---

## 15. MITRE ATT&CK Mapping

The observed behavior can be mapped conceptually to several MITRE ATT&CK techniques:

| Technique | Observed Behavior |
|---|---|
| T1059 | Command/interpreter-related malware activity |
| T1189 | Malicious content obtained through external web infrastructure |
| T1566 | Social-engineering/phishing-related delivery context |
| T1071.003 | DNS used for network communication |
| T1071.001 | HTTP-based communication |
| T1071.003 / Email-related communication | SMTP used for data transmission |
| T1555 | Credential collection from browser/account data |
| T1041 | Exfiltration over C2 channel / external communication |

The mapping is intended as an analytical classification of the observed behavior rather than a claim that every technique was independently proven by the PCAP.

---

## 16. Investigation Findings

The investigation established the following:

1. The capture contained 4003 packets over a duration of 01:03:41.
2. Three internal computers participated in the capture.
3. `Beijing-5cd1-PC` was the most active system at the network level.
4. The victim queried the suspicious domain `proforma-invoices.com`.
5. The domain resolved to `217.182.138.150`, located in France.
6. The victim was running Windows NT 6.1.
7. The victim downloaded `tkraw_Protected99.exe`.
8. The file MD5 was `71826ba081e303866ce2a2534491a2f7`.
9. The malware was hosted on a LiteSpeed web server.
10. The victim's public IP was `173.66.146.112`.
11. Stolen information was transmitted through SMTP.
12. The receiving mail infrastructure used Exim 4.91.
13. The stolen information was sent to `sales.del@macwinlogistics.in`.
14. The malware was identified as HawkEye Keylogger - Reborn v9.
15. Bank of America credentials were found within the collected information.
16. Data was exfiltrated approximately every 10 minutes.

---

## 17. Conclusion

The HawkEye PCAP investigation demonstrates a complete malware infection and information-exfiltration workflow.

Network evidence showed suspicious DNS activity followed by an HTTP download of a malicious executable. Subsequent analysis identified the malware as HawkEye Keylogger - Reborn v9. SMTP traffic then revealed the transmission of collected information to an external email account.

The investigation successfully reconstructed the major stages of the incident and identified network, file, email, and credential-related indicators.

All 24 CyberDefenders HawkEye questions were successfully solved and documented.

---

## 18. Evidence Handling

The investigation was conducted in an isolated virtual machine environment.

The malicious executable was not executed. Analysis was based on:

- PCAP traffic
- Wireshark packet inspection
- HTTP metadata
- SMTP communication
- DNS responses
- Static file hashing
- CyberChef decoding
- External IP/WHOIS verification

Screenshots supporting the investigation are maintained in the repository's `screenshots/` directory.

---

## 19. Disclaimer

This report was prepared for cybersecurity training, network forensics practice, and defensive security analysis using the CyberDefenders HawkEye lab environment.

Recovered credentials and malware indicators are included only as forensic evidence from the controlled training scenario.
