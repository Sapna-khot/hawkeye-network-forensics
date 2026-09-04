# HawkEye Network Forensics - Answers

This document records the solved questions from the CyberDefenders HawkEye Network Forensics investigation.

> Investigation principle: Answers are supported by packet-level evidence, Wireshark analysis, and relevant external verification where required.

---

## Q1 - Number of Packets

**Question:** How many packets does the capture have?

**Answer:** `4003`

**Method:**  
Opened the PCAP in Wireshark and checked **Statistics → Capture File Properties**.

**Evidence:**  
The capture contains 4003 packets.

**Status:** ✅ Solved

---

## Q2 - First Packet Timestamp

**Question:** At what time was the first packet captured (UTC)?

**Answer:** `2019-04-10 20:37`

**Method:**  
Checked the first packet timestamp in Wireshark Capture File Properties and converted the displayed local timestamp to UTC.

**Status:** ✅ Solved

---

## Q3 - Capture Duration

**Question:** What is the duration of the capture?

**Answer:** `01:03:41`

**Method:**  
Checked the capture duration in Wireshark Capture File Properties.

**Status:** ✅ Solved

---

## Q4 - Most Active Computer at Link Level

**Question:** What is the most active computer at the link level?

**Answer:** `00:08:02:1c:47:ae`

**Method:**  
Analyzed the Ethernet conversations in Wireshark and identified the most active MAC address based on network activity.

**Evidence:**  
`04_q04_ethernet_conversations.png`

**Status:** ✅ Solved

---

## Q5 - NIC Manufacturer

**Question:** Manufacturer of the NIC of the most active system at the link level?

**Answer:** `Hewlett-Packard`

**Method:**  
Used the MAC address/OUI associated with the most active system to identify the NIC manufacturer.

**Status:** ✅ Solved

---

## Q6 - NIC Manufacturer Headquarters

**Question:** Where is the headquarter of the company that manufactured the NIC?

**Answer:** `Palo Alto`

**Method:**  
Verified the headquarters location of the identified NIC manufacturer.

**Status:** ✅ Solved

---

## Q7 - Number of Computers

**Question:** How many computers in the organization are involved in the capture?

**Answer:** `3`

**Method:**  
Analyzed IPv4 conversations and identified the internal hosts using the organization's private /24 network.

**Evidence:**  
`05_q07_q08_ipv4_conversations.png`

**Status:** ✅ Solved

---

## Q8 - Most Active Computer at Network Level

**Question:** What is the name of the most active computer at the network level?

**Answer:** `Beijing-5cd1-PC`

**Method:**  
Identified the most active internal IP from IPv4 conversations and correlated it with DHCP traffic. The DHCP Inform message was examined to identify the hostname.

**Evidence:**  
`05_q07_q08_ipv4_conversations.png`

**Status:** ✅ Solved

---

## Q9 - Organization DNS Server

**Question:** What is the IP of the organization's DNS server?

**Answer:** `10.4.10.4`

**Method:**  
Analyzed DNS traffic and identified the internal DNS server handling the organization's DNS requests.

**Status:** ✅ Solved

---

## Q10 - Domain Requested in Packet 204

**Question:** What domain is the victim asking about in packet 204?

**Answer:** `proforma-invoices.com`

**Method:**  
Inspected packet 204 and examined the DNS query information.

**Evidence:**  
DNS response evidence is available in:

`07_q10_q11_dns_response.png`

**Note:**  
A separate DNS query screenshot for Q10 is not currently available.

**Status:** ✅ Solved

---

## Q11 - Domain IP Address

**Question:** What is the IP of the domain in the previous question?

**Answer:** `217.182.138.150`

**Method:**  
Inspected the DNS response associated with the queried domain.

**Evidence:**  
`07_q10_q11_dns_response.png`

**Status:** ✅ Solved

---

## Q12 - IP Country

**Question:** Indicate the country to which the IP in the previous section belongs.

**Answer:** `France`

**Method:**  
Performed IP geolocation verification for `217.182.138.150`.

**Evidence:**
- `08_q12_ip_geolocation.png`

**Status:** ✅ Solved

---

## Q13 - Victim Operating System

**Question:** What operating system does the victim's computer run?

**Answer:** `Windows NT 6.1`

**Method:**  
Analyzed network/HTTP information and verified the operating-system identifier associated with the victim.

**Evidence:**  
`09_q13_whois_evidence.png`

**Status:** ✅ Solved

---

## Q14 - Malicious File

**Question:** What is the name of the malicious file downloaded by the accountant?

**Answer:** `tkraw_Protected99.exe`

**Method:**  
Inspected HTTP traffic and identified the executable downloaded by the victim.

**Evidence:**  
`10_q14_http_download.png`

**Note:**  
A separate HTTP Object Export screenshot is not currently available.

**Status:** ✅ Solved

---

## Q15 - MD5 Hash

**Question:** What is the MD5 hash of the downloaded file?

**Answer:** `71826ba081e303866ce2a2534491a2f7`

**Method:**  
Calculated/verified the MD5 hash of the downloaded malicious file.

**Evidence:**  
`11_q15_md5_hash.png`

**Status:** ✅ Solved

---

## Q16 - Web Server Software

**Question:** What software runs the webserver that hosts the malware?

**Answer:** `LiteSpeed`

**Method:**  
Inspected the HTTP server response headers associated with the malware-hosting server.

**Evidence:**  
`12_q16_http_server.png`

**Status:** ✅ Solved

---

## Q17 - Victim Public IP

**Question:** What is the public IP of the victim's computer?

**Answer:** `173.66.146.112`

**Method:**  
Correlated the internal victim system with its external/public network communication.

**Evidence:**  
`13_q17_victim_public_ip.png`

**Status:** ✅ Solved

---

## Q18 - Email Server Country

**Question:** In which country is the email server to which the stolen information is sent?

**Answer:** `United States`

**Method:**  
Identified the external email server involved in the SMTP communication and verified its geographic location.

**Evidence:**  
No screenshot is currently available for Q18.

**Status:** ✅ Solved

---

## Q19 - Email Server Software

**Question:** Analyzing the first extraction of information. What software runs the email server to which the stolen data is sent?

**Answer:** `Exim 4.91`

**Method:**  
Analyzed the SMTP communication and examined the email server information.

**Evidence:**  
Screenshot available locally and will be added to the repository during the final documentation update.

**Status:** ✅ Solved

---

## Q20 - Recipient Email Account

**Question:** To which email account is the stolen information sent?

**Answer:** `sales.del@macwinlogistics.in`

**Method:**  
Inspected the SMTP communication and identified the recipient address.

**Evidence:**  
Screenshot available locally and will be added during the final update.

**Status:** ✅ Solved

---

## Q21 - SMTP Password

**Question:** What is the password used by the malware to send the email?

**Answer:** `Sales@23`

**Method:**  
Analyzed the SMTP authentication data and decoded the Base64-encoded credential information.

**Evidence:**  
Screenshot available locally and will be added during the final update.

**Status:** ✅ Solved

---

## Q22 - Malware Variant

**Question:** Which malware variant exfiltrated the data?

**Answer:** `Reborn V9`

**Method:**  
Analyzed the exfiltration-related email/network data and identified the malware variant.

**Evidence:**  
Screenshot available locally and will be added during the final update.

**Status:** ✅ Solved

---

## Q23 - Bank of America Credentials

**Question:** What are the Bank of America access credentials?

**Answer:** `roman.mcguire:P@ssw0rd$`

**Method:**  
Inspected the exfiltrated information and identified the Bank of America username and password.

**Evidence:**  
Screenshot available locally and will be added during the final update.

**Status:** ✅ Solved

---

## Q24 - Exfiltration Frequency

**Question:** Every how many minutes does the collected data get exfiltrated?

**Answer:** `10 minutes`

**Method:**  
Analyzed the timestamps of repeated exfiltration events and identified the recurring interval.

**Evidence:**  
Screenshot available locally and will be added during the final update.

**Status:** ✅ Solved

---

# Investigation Completion Status

| Question | Status |
|---|---|
| Q1 | ✅ Solved |
| Q2 | ✅ Solved |
| Q3 | ✅ Solved |
| Q4 | ✅ Solved |
| Q5 | ✅ Solved |
| Q6 | ✅ Solved |
| Q7 | ✅ Solved |
| Q8 | ✅ Solved |
| Q9 | ✅ Solved |
| Q10 | ✅ Solved |
| Q11 | ✅ Solved |
| Q12 | ✅ Solved |
| Q13 | ✅ Solved |
| Q14 | ✅ Solved |
| Q15 | ✅ Solved |
| Q16 | ✅ Solved |
| Q17 | ✅ Solved |
| Q18 | ✅ Solved |
| Q19 | ✅ Solved |
| Q20 | ✅ Solved |
| Q21 | ✅ Solved |
| Q22 | ✅ Solved |
| Q23 | ✅ Solved |
| Q24 | ✅ Solved |

**Overall Lab Status: 24/24 Questions Solved**

The remaining work is documentation evidence collection, specifically adding the locally available Q19-Q24 screenshots and completing the final Day 5 report update.
