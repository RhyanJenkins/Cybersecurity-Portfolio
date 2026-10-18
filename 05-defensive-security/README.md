# Defensive Security

This section documents the defensive security technologies, configurations, monitoring practices, and validation exercises implemented within my cybersecurity homelab.

My defensive security work focuses on protecting systems, controlling network communication, collecting security telemetry, and evaluating whether security controls provide the expected visibility and enforcement.

The environment supports hands-on development in network defense, endpoint security, security operations, and incident investigation.

## Defensive Security Environment

My defensive security environment uses Proxmox VE, OPNsense, Wazuh SIEM, and Debian Linux.

| Component | Defensive Function |
|---|---|
| OPNsense | Firewall enforcement, network routing, and traffic logging |
| Wazuh SIEM | Centralized security monitoring and event analysis |
| Debian Linux | Monitored endpoint and Linux security configuration |
| nftables | Linux host-based firewall management |
| Proxmox VE | Virtualization and infrastructure administration |
| Tailscale | Remote administration of authorized infrastructure |

These systems support the configuration, evaluation, and investigation of security controls within a privately managed environment.

[View Homelab Architecture](../01-homelab-infrastructure/PRJ-001-homelab-architecture/)

## Implemented Security Controls

### Network Segmentation & Firewall Enforcement

OPNsense provides network separation between the security testing LAN and the intentionally vulnerable target environment.

Firewall policies control routed traffic between these networks.

Previous validation confirmed:

- Communication from Kali Linux to Metasploitable 2 traverses OPNsense.
- OPNsense records relevant firewall traffic.
- Tested restrictions on vulnerable-network access to the primary home network and Internet were functioning during validation.

These findings apply to the tested conditions and do not establish comprehensive coverage of every protocol or network path.

### Centralized Security Monitoring

Wazuh serves as the centralized security monitoring platform.

Previously verified monitoring integrations include:

- OPNsense
- Debian Linux

Both integrations have been observed as active in the Wazuh interface.

The environment has also produced searchable OPNsense-related firewall alerts.

However, active agent connectivity and the presence of some security alerts do not guarantee complete visibility into every network event.

### Linux Endpoint Security

Debian Linux provides an environment for developing and testing host-level security controls.

Documented work includes:

- SSH connectivity and administration
- nftables host firewall configuration
- Wazuh agent deployment and connectivity validation
- Linux security monitoring and troubleshooting

The environment provides a foundation for future endpoint hardening, file integrity monitoring, and security configuration assessment exercises.

### Secure Remote Administration

Tailscale supports remote access to selected infrastructure management services without requiring their direct exposure through public Internet port forwarding.

This provides a practical environment for studying secure administration and the separation of management access from security testing activity.

## Security Monitoring & Detection Validation

Defensive security requires more than deploying monitoring software.

Individual security controls must be tested to determine whether they produce the expected results.

My validation activities include:

1. Generating or identifying security-relevant activity within the authorized environment.
2. Confirming network or endpoint behavior.
3. Examining the relevant firewall or system logs.
4. Searching available security monitoring data.
5. Comparing observations across data sources.
6. Documenting confirmed findings and unresolved limitations.

This approach supports practical development in security operations and detection analysis.

[View Security Monitoring Documentation](../01-homelab-infrastructure/PRJ-001-homelab-architecture/security-monitoring.md)

## Related Investigation

### CASE-001 — FTP Backdoor Traffic & SIEM Visibility Investigation

**Category:** Detection Analysis / Incident Response  
**Status:** Investigation Ongoing

This investigation examines differences between network-level visibility and centralized SIEM search results during controlled FTP-related testing.

**Documented findings:**

- Kali Linux successfully reached the target's FTP TCP port.
- OPNsense recorded a permitted TCP SYN packet.
- OPNsense-related firewall alerts were visible in Wazuh.
- A search for the specific target did not identify a corresponding Wazuh alert.
- The underlying cause remains unverified.

The investigation demonstrates the importance of validating individual stages of security monitoring rather than assuming that all logged activity will produce alerts.

[View CASE-001 Investigation](../03-incident-response/CASE-001-ftp-siem-visibility/)

## Tools & Technologies

| Technology | Application |
|---|---|
| OPNsense | Firewall policies, routing, and log analysis |
| Wazuh | Security event monitoring and alert investigation |
| Debian Linux | Endpoint security and administration |
| nftables | Host-based firewall configuration |
| SSH | Secure remote administration |
| Tailscale | Controlled infrastructure access |
| Proxmox VE | Security infrastructure virtualization |

The tools listed reflect documented implementations and testing activities, not full deployment or validation of every available security feature.

## Future Defensive Security Exercises

Planned development includes:

- SSH authentication failure detection
- Firewall block analysis and log correlation
- File Integrity Monitoring (FIM) validation
- Security Configuration Assessment (SCA)
- Linux system hardening and CIS benchmark review
- Suricata IDS/IPS deployment and investigation
- Wazuh Active Response testing
- Custom detection rules and alert tuning
- Multi-source security event correlation
- Incident timeline reconstruction

These are planned exercises and are not presented as completed implementations.

## Documentation & Validation Standards

Defensive security documentation emphasizes:

- Clear identification of security control objectives
- Accurate descriptions of implemented configurations
- Repeatable testing and validation procedures
- Preservation of relevant evidence
- Separation of verified observations and investigative hypotheses
- Documentation of security limitations and future improvements

Public documentation excludes credentials, private management endpoints, and other sensitive infrastructure information.

## Current Status

**Status:** Active — Security Controls Deployed and Validation Ongoing

Network segmentation, firewall logging, Wazuh monitoring integrations, and selected Linux security controls have been implemented and tested.

Dedicated defensive security case studies will be added as individual exercises are completed and their findings are reviewed.

---

**Focus:** Network Defense, Endpoint Security & Security Monitoring  
**Environment:** Authorized Private Cybersecurity Homelab

[Return to Main Portfolio](../README.md) | [View Homelab Infrastructure](../01-homelab-infrastructure/)