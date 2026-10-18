# CASE-001 — EX-002 Public Evidence

**Case:** CASE-001 — FTP Backdoor Traffic and SIEM Visibility Investigation  
**Exercise:** EX-002 — FTP Traffic and SIEM Visibility Investigation  
**Status:** Public evidence package proposed; case investigation remains open  
**Originals:** Stored privately; files linked here are sanitized presentation copies

## Evidence index

| Public screenshot | Source / observation | Interpretation / limits |
|---|---|---|
| [Wazuh agent status](EX-002-20261016-145747-wazuh-agent-status-sanitized.png) | Wazuh shows two active agents, `debian-lab` and `OPNsense.internal`. | Active agent status does not verify that the specific FTP firewall event was ingested or indexed. |
| [Wazuh OPNsense alerts](EX-002-20261016-150707-wazuh-agent-events-sanitized.png) | Threat Hunting shows 125 OPNsense-agent alerts during the displayed last-24-hours interval, including rule 87702 for multiple firewall blocks from the same source. | These block alerts have not been correlated to the permitted FTP packet. |
| [Kali FTP connectivity check](EX-002-20261016-150352-kali-ftp-port-check-sanitized.png) | Netcat reports Metasploitable's TCP port 21 as open. | Supports TCP service reachability, **not** successful FTP backdoor exploitation. |
| [OPNsense traffic view](EX-002-20261016-150449-opnsense-traffic-view-sanitized.png) | Firewall Live View shows permitted TCP traffic involving the Kali and Metasploitable lab networks. | The expanded firewall record below provides more precise packet context. |
| [OPNsense October 16 event detail (E06)](EX-002-S01-E06-opnsense-ftp-event-details-sanitized.png) | OPNsense records a permitted inbound TCP SYN to port 21 under rule 49, `Log Kali to Metasploitable`, at displayed timestamp `2026-10-16T20:02:48`. | Confirms the SYN packet was passed/logged; does not by itself prove completion of a TCP session or exploitation. Event timezone is unverified. |
| [OPNsense October 15 event detail](EX-002-20261015-071108-opnsense-ftp-details-sanitized.png) | An **earlier**, separate permitted inbound TCP SYN to port 21 under the same labeled rule at displayed timestamp `2026-10-15T11:49:23`. | Historical firewall observation, not evidence of the October 16 Wazuh search result. |
| [Wazuh October 16 search — no results (E07)](EX-002-S01-E07-wazuh-ftp-search-no-results-sanitized.png) | Threat Hunting searched for `10.20.20.143` with `OPNsense.internal (002)` selected and displayed time range `Oct 16, 2026 @ 11:00:00.000 → now`; result: **“No results match your search criteria.”** | Confirms **no matches under the displayed filters and time range**, not that the firewall record was never forwarded, ingested, archived, decoded, or indexed. The query/search timezone has not been independently reconciled with the OPNsense event timestamp. |

## Replacement note

The October 15 **Wazuh historical IP-search** screenshot has been removed from this public evidence selection. It showed one historical alert and therefore must not be presented as the October 16 zero-match result. The separate October 15 **OPNsense firewall event** screenshot remains because it documents a distinct historical firewall observation.

## Sanitization and traceability

The original screenshots are retained privately. These published candidates are sanitized presentation copies; some were cropped, and internal rule UUIDs and home-management addresses were redacted. The new E07 screenshot has been re-encoded without embedded metadata and has pixel-identical visible content to the supplied image. Its source filename was `EX-002-S01-E07-wazuh-ftp-search-no-results.png.png`; the double extension was corrected in the sanitized public filename.

Isolated lab IP addresses, port numbers, command output, timestamps, and selected lab hostnames remain visible to permit event correlation. **Public IP-disclosure policy remains subject to owner approval.** Review all screenshots before publishing. Image filename dates/times are not independently verified event timestamps. Existing evidence IDs E06 and E07 have been preserved; other files have not been assigned new E-numbers. Original-file hashes are not documented here and must not be invented.

## Related reports

- [Full case study](../README.md)
- [Homelab architecture](../../../01-homelab-infrastructure/PRJ-001-homelab-architecture/)