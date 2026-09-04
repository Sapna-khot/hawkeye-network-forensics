# Day 4 - HawkEye Network Forensics Investigation

## Objective

Continue the HawkEye Network Forensics investigation and document the evidence supporting the remaining CyberDefenders questions.

## Work Completed

Today I continued the investigation from Q4 onwards and analyzed multiple network-forensics artifacts using Wireshark and supporting verification methods.

The investigation covered:

- Ethernet conversations for link-level activity
- IPv4 conversations for identifying active internal systems
- DHCP traffic for hostname identification
- DNS queries and responses
- Domain-to-IP resolution
- IP geolocation and WHOIS information
- HTTP traffic and malware download activity
- HTTP server information
- MD5 hash verification
- Public IP identification
- SMTP communication and email-based data exfiltration
- Malware variant identification
- Credential extraction from the captured traffic
- Periodic data-exfiltration behavior

## Questions Completed

The investigation has now reached:

**24/24 CyberDefenders questions solved.**

Questions Q4-Q17 were documented with the available screenshots and packet-level evidence.

Questions Q19-Q24 have also been solved and their supporting screenshots are available locally. Due to the current upload limitation, these screenshots will be added to the GitHub repository during the final documentation update.

## Evidence Availability

Available screenshots currently documented in the repository:

- `04_q04_ethernet_conversations.png`
- `05_q07_q08_ipv4_conversations.png`
- `07_q10_q11_dns_response.png`
- `08_q12_ip_geolocation.png`
- `09_q13_whois_evidence.png`
- `10_q14_http_download.png`
- `11_q15_md5_hash.png`
- `12_q16_http_server.png`
- `13_q17_victim_public_ip.png`

The following evidence screenshots are not currently available in the repository:

- Q10 DNS query screenshot
- Q14 HTTP Object Export screenshot
- Q18 email-server country screenshot

The screenshots for Q19-Q24 exist locally and will be uploaded during the final documentation update.

## Investigation Progress

The investigation progressed from basic packet statistics to detailed analysis of:

1. Internal network hosts
2. DNS infrastructure
3. External domains and IP addresses
4. HTTP-based malware delivery
5. Malware identification and hashing
6. Victim public IP information
7. SMTP-based information exfiltration
8. Malware credentials and exfiltrated information
9. Periodic exfiltration behavior

## Key Learning

This stage demonstrated how a network-forensics investigation can reconstruct an attack by correlating multiple protocols rather than relying on a single packet.

DNS, DHCP, HTTP and SMTP traffic provided different pieces of evidence that could be correlated to reconstruct the victim, malicious infrastructure, downloaded malware and subsequent data-exfiltration activity.

## Next Steps

The next stage will focus on final evidence collection and documentation:

- Add Q19-Q24 screenshots
- Review all screenshots and filenames
- Update the final timeline
- Update the IOC documentation
- Review the final investigation report
- Add a final Day 5 completion entry
- Perform the final GitHub commit and push
