# Security Monitoring and Detection Architecture

**Project:** PRJ-001 — Cybersecurity Homelab Architecture & Security Design  
**Category:** Defensive Security / Security Operations  
**Platform:** Wazuh SIEM and OPNsense  
**Status:** Active

## 1. Overview

The cybersecurity homelab incorporates centralized security monitoring to support network analysis, security investigations, and incident response exercises.

Wazuh operates as the primary security monitoring platform, collecting and analyzing supported security events from integrated systems.

OPNsense provides firewall enforcement and network traffic logging, while Debian provides endpoint-level security telemetry.

Together, these components support investigations involving network activity, authentication events, and system behavior.

## 2. Monitoring Components

| Component | Platform | Monitoring Function |
|---|---|---|
| Wazuh SIEM | Proxmox VM on pve1 | Centralized event collection, analysis, and investigation |
| OPNsense | Proxmox VM on pve2 | Firewall logging and network security events |
| Debian Linux | Proxmox VM on pve2 | Endpoint monitoring and Linux security events |

### Wazuh SIEM

Wazuh serves as the centralized monitoring platform.

The deployment supports:

- Security event collection
- Log analysis and searching
- Agent-based monitoring
- Security investigations
- File Integrity Monitoring
- Security Configuration Assessment

The availability of these capabilities does not imply that every feature has been fully configured or validated.

### OPNsense Firewall

OPNsense provides network security controls and traffic visibility.

Its firewall logs can be used to examine traffic between the security testing and vulnerable networks.

OPNsense has been integrated with Wazuh for centralized security monitoring.

### Debian Linux

Debian operates as a monitored Linux endpoint.

A Wazuh agent has been installed and previously verified as active.

The system supports exercises involving authentication events, Linux security configuration, and endpoint monitoring.

## 3. Monitoring Architecture

The monitoring environment uses Wazuh as the centralized analysis platform.

OPNsense and Debian provide security telemetry through their monitoring integrations.

This architecture supports the investigation of events across network and endpoint sources.

The exact event types available depend on the configured log collection, decoders, rules, and monitoring settings.

## 4. Network Security Visibility

OPNsense provides firewall logging for routed traffic between the security testing and vulnerable networks.

Previous authorized penetration testing exercises generated network activity visible in OPNsense firewall logs.

This provides a source of network-level evidence during security investigations.

However, firewall log visibility does not guarantee that equivalent events will appear in Wazuh.

## 5. Endpoint Security Visibility

Debian provides endpoint-level security information through its Wazuh agent.

Depending on the configured monitoring capabilities, endpoint telemetry may include:

- Authentication events
- System logs
- File integrity changes
- Security configuration findings

Specific event sources and detection results are documented in individual investigations after validation.

## 6. Detection and Investigation Workflow

A typical investigation follows this process:

1. Generate or identify an event within the authorized lab.
2. Record the test conditions and relevant timestamps.
3. Examine available firewall or endpoint logs.
4. Search Wazuh for corresponding events.
5. Correlate evidence across available sources.
6. Determine whether expected monitoring occurred.
7. Document findings, limitations, and recommended improvements.

## 7. Detection Coverage and Limitations

Security monitoring effectiveness depends on the visibility and configuration of each component.

Relevant considerations include:

- Whether a system generates the expected logs
- Whether those logs are collected successfully
- Whether Wazuh can parse the received events
- Whether detection rules match the activity
- Whether alerts are generated and retained
- Whether timestamps can be correlated accurately

The presence of an active monitoring integration does not, by itself, establish complete detection coverage.

## 8. Investigation Opportunities

The monitoring environment supports exercises involving:

- Network reconnaissance
- SSH authentication failures
- Firewall rule violations
- Suspicious service activity
- File integrity changes
- Incident timeline reconstruction
- Cross-source log correlation

Results from completed investigations will be maintained as separate case studies.

## 9. Future Improvements

Potential improvements include:

- Expanded log collection
- Custom Wazuh detection rules
- Suricata IDS/IPS integration
- Active Response testing
- Improved evidence preservation procedures
- Additional endpoint monitoring
- Detection coverage validation

---

**Project Status:** Active  
**Monitoring Environment:** Operational  
**Detection Coverage:** Evaluated through individual exercises
