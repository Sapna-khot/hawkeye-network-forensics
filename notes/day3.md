# Day 3 – HawkEye Network Forensics Investigation

## Objective

Continue the HawkEye Network Forensics investigation from Q4 onward and identify the systems, network infrastructure, suspicious domains, malicious downloads and communication channels involved in the incident.

## Activities Performed

### 1. Network Conversation Analysis

Analyzed Ethernet and IPv4 conversations in Wireshark to identify the most active network endpoints.

The internal host identified during the investigation was:

- `10.4.10.132`

The Ethernet conversation analysis was also used to identify the most active MAC address.

### 2. DNS Investigation

Filtered DNS traffic in Wireshark and investigated suspicious domain-resolution activity.

The DNS traffic revealed communication involving:

- Internal DNS server: `10.4.10.4`
- Suspicious domain: `proforma-invoices.com`
- Resolved external IP: `217.182.138.150`

Packet-level evidence was captured from the DNS query and response.

### 3. External Infrastructure Investigation

Investigated the external IP address associated with the suspicious domain using IP/WHOIS information.

The infrastructure was associated with France and OVH hosting infrastructure.

### 4. HTTP Investigation

Filtered HTTP traffic and identified a suspicious executable download.

The request showed:

- Host: `proforma-invoices.com`
- Requested file: `tkraw_Protected99.exe`
- Source: `10.4.10.132`
- Destination: `217.182.138.150`

The HTTP Object Export feature was used to identify the downloaded executable.

### 5. Malware Hash Analysis

The downloaded file was analyzed without executing it.

The MD5 hash was calculated locally for identification and investigation purposes.

MD5:

`71826ba081e303866ce2a2534491a2f7`

### 6. HTTP Server Analysis

HTTP response headers were examined to identify the web server software.

The server response indicated:

`LiteSpeed`

### 7. SMTP Investigation

SMTP traffic was filtered and examined to understand the email communication associated with the incident.

The investigation identified an SMTP communication channel involving the compromised host and an external mail server.

## Evidence Collected

Screenshots were captured for:

- Ethernet conversations
- IPv4 conversations
- DNS queries and responses
- Suspicious IP investigation
- HTTP malicious file download
- HTTP object export
- HTTP server headers
- MD5 hash calculation
- SMTP communication

## Security Approach

The downloaded executable was **not executed**. Analysis was performed using network evidence, file metadata and hash calculation to avoid unnecessary exposure to the malware.

## Learning Outcomes

- Learned how to identify active hosts using Wireshark Conversations.
- Practiced DNS-based investigation.
- Learned how to correlate domains with resolved IP addresses.
- Investigated malicious HTTP downloads.
- Used Wireshark HTTP Object Export.
- Calculated a malware file hash safely.
- Identified web server information from HTTP headers.
- Began investigating SMTP-based communication and potential data exfiltration.

## Next Steps

- Complete the remaining SMTP investigation.
- Analyze encoded authentication/data fields.
- Investigate possible credential theft and exfiltration.
- Complete the remaining CyberDefenders questions.
- Update the IOC list and incident timeline.
- Finalize the investigation report.
