# Incident Response & Security Investigations

This section documents hands-on cybersecurity investigations performed within my authorized homelab environment.

The focus is on examining security events, correlating evidence across monitoring platforms, identifying limitations in available telemetry, and documenting findings through structured technical reports.

My investigation process emphasizes evidence-based conclusions, reproducible testing, and clear separation between verified observations and unresolved questions.

## Published Investigations

### CASE-001 — FTP Backdoor Traffic and SIEM Visibility Investigation

**Category:** Network Security / Incident Response / Detection Analysis  
**Related Exercise:** EX-002  
**Status:** Investigation Ongoing

An investigation examining differences between network-level firewall visibility and SIEM search results during controlled FTP-related testing against Metasploitable 2.

**Documented activities:**
- Validating TCP connectivity from Kali Linux to the vulnerable target
- Examining OPNsense firewall logs and event details
- Reviewing Wazuh agent connectivity and existing firewall alerts
- Searching for corresponding events in Wazuh Threat Hunting
- Comparing results across network and security monitoring sources
- Documenting investigative findings, limitations, and outstanding questions

**Current findings:**

OPNsense recorded permitted FTP-related traffic, while the documented Wazuh search did not identify a corresponding alert.

The reason for this visibility difference remains unresolved.

The investigation does not establish successful FTP backdoor exploitation or a failure of Wazuh log ingestion.

[**View CASE-001 — Complete Investigation**](CASE-001-ftp-siem-visibility/)

## Investigation Methodology

My cybersecurity investigations follow a structured process:

1. **Define the scope:** Establish objectives, involved systems, and authorized testing boundaries.
2. **Collect evidence:** Identify relevant logs, event records, screenshots, and technical artifacts.
3. **Validate observations:** Confirm what the available evidence demonstrates.
4. **Correlate events:** Compare timestamps, network activity, and monitoring results across sources.
5. **Document findings:** Distinguish confirmed results from hypotheses and unresolved questions.
6. **Identify next steps:** Record additional validation required to reach supported conclusions.

This methodology is refined as new exercises and investigations are completed.

## Technologies & Tools

| Technology | Investigative Purpose |
|---|---|
| Wazuh SIEM | Security event searching and alert analysis |
| OPNsense | Firewall event analysis and network traffic visibility |
| Kali Linux | Authorized security testing and validation |
| Debian Linux | Linux endpoint monitoring and security administration |
| Metasploitable 2 | Controlled testing against an intentionally vulnerable target |
| Proxmox VE | Virtualized investigation and testing environment |
| Obsidian | Investigation notes, evidence organization, and session documentation |

## Digital Forensics & Incident Response Development

Future investigation work will expand into:

- Digital evidence acquisition and preservation
- Incident timeline reconstruction
- Authentication and access investigations
- Network traffic and packet analysis
- Endpoint and file system artifact analysis
- Security event correlation
- Detection validation and incident reporting

These are continued development objectives, not completed investigations.

## Evidence & Reporting Standards

Investigation records are developed to preserve technical accuracy, reproducibility, and evidence integrity.

Original artifacts are maintained privately. Selected evidence may be sanitized and published after review.

Reports distinguish between observed activity, analytical interpretation, investigative limitations, and conclusions supported by available evidence.

---

**Investigation Environment:** Authorized Private Cybersecurity Homelab  
**Published Case Studies:** CASE-001  
**Current Investigation Status:** Open

[Return to Main Portfolio](../README.md) | [View Homelab Infrastructure](../01-homelab-infrastructure/)