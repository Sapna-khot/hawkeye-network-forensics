# HawkEye Investigation Timeline

| Sequence | Event | Evidence | Status |
|---|---|---|---|
| 1 | HawkEye lab scenario reviewed | CyberDefenders lab instructions | Completed |
| 2 | Safe VMware Ubuntu environment prepared | VMware Ubuntu VM | Completed |
| 3 | PCAP opened in Wireshark | `stealer.pcap` | Completed |
| 4 | Capture statistics examined | Capture File Properties | Completed |
| 5 | Protocol hierarchy examined | Wireshark Protocol Hierarchy | Completed |
| 6 | Network conversations examined | Wireshark Conversations | Completed |
| 7 | Initial CyberDefenders questions investigated | Lab question interface | In progress |
| 8 | Deeper DNS/HTTP/SMTP investigation | PCAP traffic | Pending |

## Initial Findings

- The capture contains 4003 packets.
- The capture duration is 01:03:41.
- Multiple network protocols are present.
- TCP represents a significant portion of the captured traffic.
- Network conversations were reviewed as an initial step toward identifying important communicating hosts.

Further conclusions will only be added after packet-level investigation and verification.
