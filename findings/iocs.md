---

# Confirmed Investigation Indicators

## Network Indicators

| Indicator | Value | Context |
|---|---|---|
| Internal DNS Server | `10.4.10.4` | Organization DNS infrastructure |
| Suspicious Domain | `proforma-invoices.com` | Domain queried by victim |
| Domain IP | `217.182.138.150` | IP resolved from suspicious domain |
| Victim Public IP | `173.66.146.112` | Public address associated with victim |

## Malware Indicators

| Indicator | Value | Context |
|---|---|---|
| Malware Filename | `tkraw_Protected99.exe` | Executable downloaded by accountant |
| MD5 | `71826ba081e303866ce2a2534491a2f7` | Hash of downloaded file |
| Malware Variant | `Reborn V9` | Variant identified during exfiltration analysis |
| Malware Hosting Software | `LiteSpeed` | Web server hosting malware |

## Email / Exfiltration Indicators

| Indicator | Value | Context |
|---|---|---|
| Email Server Software | `Exim 4.91` | SMTP server involved in first extraction |
| Recipient | `sales.del@macwinlogistics.in` | Destination email account |
| Email Server Country | `United States` | Geographic location |
| Exfiltration Interval | `10 minutes` | Recurring data-exfiltration frequency |

## Credentials Observed in Captured Traffic

> These credentials are documented strictly as forensic findings from the challenge PCAP and should not be reused.

| Type | Value |
|---|---|
| SMTP Password | `Sales@23` |
| Bank of America Credentials | `roman.mcguire:P@ssw0rd$` |

## Evidence Status

The indicators above were identified during analysis of the HawkEye challenge PCAP.

Supporting screenshots for Q19-Q24 are available locally but have not yet been added to the repository because of the current upload limitation. They will be included during the final Day 5 documentation update.
