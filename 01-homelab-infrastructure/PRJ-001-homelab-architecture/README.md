# PRJ-001: Cybersecurity Homelab Architecture & Security Design

**Project Type:** Infrastructure & Security Engineering  
**Environment:** Self-Hosted Cybersecurity Homelab  
**Status:** Active — Documentation in Progress

## 1. Project Overview

This project documents the architecture, implementation, and security design of a virtualized cybersecurity homelab developed for hands-on training in offensive security, defensive security, digital forensics, and incident response.

The environment uses two Proxmox VE hosts to support centralized security monitoring, network defense, Linux administration, penetration testing, and controlled security investigations.

Its primary purpose is to provide an environment where security controls can be configured, tested, monitored, and evaluated through repeatable technical exercises.

## 2. Project Objectives

- Build and administer a virtualized cybersecurity infrastructure.
- Implement network segmentation and firewall policies.
- Deploy and integrate centralized security monitoring.
- Perform authorized security testing against intentionally vulnerable systems.
- Validate network connectivity and security boundaries.
- Investigate firewall and endpoint security events.
- Develop repeatable evidence collection and technical documentation practices.
- Support future digital forensics and incident response exercises.

## 3. Infrastructure Overview

### Physical Hosts

| Host | Platform | Primary Role |
|---|---|---|
| pve1 | HP ENVY Desktop | Centralized security monitoring |
| pve2 | Dell Inspiron Laptop | Network security, testing, and lab virtualization |

### Virtual Machine Placement

| Virtual Machine | Host | Function |
|---|---|---|
| Wazuh SIEM | pve1 | Centralized security monitoring |
| OPNsense | pve2 | Firewall, routing, and network segmentation |
| Kali Linux | pve2 | Authorized penetration testing |
| Debian Linux | pve2 | Linux administration and endpoint monitoring |
| Metasploitable 2 | pve2 | Intentionally vulnerable testing target |

These systems form a controlled environment for evaluating network activity, firewall behavior, endpoint security, and monitoring visibility.

[View Physical & Virtual Infrastructure](infrastructure.md)

## 4. Network Architecture & Security Design

The homelab uses separate logical network zones to distinguish trusted infrastructure, security testing systems, and intentionally vulnerable targets.

### Network Zones

| Zone | Purpose |
|---|---|
| Primary Network | Home infrastructure and selected management services |
| Security Testing LAN | Kali Linux, Debian Linux, and security testing activities |
| Vulnerable Network | Metasploitable 2 and controlled security targets |

OPNsense provides routing and firewall enforcement between the security testing and vulnerable networks.

Previous testing verified that Kali-to-Metasploitable traffic traverses OPNsense and that the firewall records relevant network activity.

Connectivity testing also confirmed restrictions on access from the vulnerable environment to the primary home network and Internet. These results apply to the tested communication paths and do not establish that every possible path has been evaluated.

### Network Topology

A logical network topology diagram has been documented using Mermaid.

The diagram represents the virtual infrastructure, security zones, traffic paths, and monitoring relationships without exposing live management addresses.

[View Network Topology & Diagram](network-topology.md)

## 5. Security Monitoring Architecture

Wazuh serves as the centralized security monitoring platform for the homelab.

Previously verified integrations include:

- Debian Linux Wazuh agent
- OPNsense Wazuh integration

The environment supports investigation of security events associated with network activity, endpoint behavior, and system configuration.

OPNsense provides firewall-level visibility into routed traffic, while Wazuh provides centralized analysis of collected security events.

An active monitoring integration does not guarantee that every generated firewall event will produce a searchable security alert.

[View Security Monitoring Documentation](security-monitoring.md)

## 6. Offensive Security Environment

Kali Linux provides tools for authorized reconnaissance, vulnerability assessment, and controlled security testing.

Metasploitable 2 serves as an intentionally vulnerable target within the segmented lab environment.

Security exercises support the evaluation of:

- Network connectivity and exposed services
- Firewall rule behavior
- Network reconnaissance activity
- Security monitoring visibility
- Evidence collection and event correlation

Testing is limited to authorized systems within the privately controlled environment.

## 7. Validation & Testing

The homelab has been used to validate infrastructure connectivity, security monitoring integrations, and selected network controls.

### Documented Validation Activities

| Area | Recorded Result |
|---|---|
| Proxmox management | Connectivity previously verified |
| Kali-to-Metasploitable routing | Communication confirmed |
| OPNsense firewall logging | Relevant traffic observed |
| Vulnerable network restrictions | Tested restrictions previously confirmed |
| Debian SSH connectivity | Confirmed |
| Debian Wazuh agent | Previously confirmed active |
| OPNsense Wazuh integration | Previously confirmed active |
| FTP traffic visibility | Firewall activity observed; SIEM correlation unresolved |

Historical test results and preserved evidence are distinguished from findings requiring additional validation.

[View Infrastructure Validation & Evidence](validation-and-evidence.md)

## 8. Related Security Investigation

### CASE-001 — FTP Traffic & SIEM Visibility Investigation

**Status:** Investigation Ongoing

This investigation examines the differences between firewall traffic visibility and Wazuh SIEM search results during controlled FTP testing against Metasploitable 2.

Documented observations include:

- TCP connectivity to the target's FTP port
- Permitted traffic recorded in OPNsense firewall logs
- No matching alert identified through the documented Wazuh search criteria
- An unresolved question concerning the underlying event collection, indexing, detection, or search process

The available evidence does not establish successful FTP backdoor exploitation or conclusively identify the cause of the missing search results.

[View CASE-001 Investigation](../../03-incident-response/CASE-001-ftp-siem-visibility/)

## 9. Challenges & Lessons Learned

Building and maintaining the homelab has required troubleshooting across virtualization, networking, firewall configuration, security monitoring, and remote administration.

Key lessons include:

- Network connectivity and security monitoring must be validated separately.
- Firewall logging and SIEM alert generation represent different stages of security visibility.
- Infrastructure changes should be followed by repeatable validation.
- Investigative conclusions must be supported by available evidence.
- Unresolved technical findings should remain documented until sufficiently investigated.

## 10. Future Development

Planned improvements and exercises include:

- Digital forensic evidence acquisition and analysis
- Incident timeline reconstruction
- Network packet analysis
- Advanced Wazuh detection engineering
- Suricata IDS/IPS integration and analysis
- Linux security hardening
- Security automation and scripting
- Expanded validation and evidence preservation

These activities are planned and are not represented as completed implementations.

## 11. Evidence & Documentation Standards

Public documentation prioritizes accuracy, repeatability, and responsible disclosure.

Original evidence is retained privately, while selected sanitized artifacts may be published to support project findings.

Live management addresses, credentials, and sensitive infrastructure identifiers are excluded from public records.

[View Evidence Management Standards](evidence/README.md)

## Technical Documentation

| Document | Description |
|---|---|
| [Architecture & Security Design](architecture.md) | Detailed infrastructure and security architecture |
| [Physical & Virtual Infrastructure](infrastructure.md) | Hardware, virtual machines, and resource considerations |
| [Network Topology](network-topology.md) | Logical diagram, network zones, and traffic relationships |
| [Security Monitoring](security-monitoring.md) | Monitoring integrations and detection limitations |
| [Validation & Evidence](validation-and-evidence.md) | Testing history, verified results, and evidence status |
| [Project Evidence](evidence/README.md) | Evidence requirements and reusable documentation templates |

---

**Project Status:** Active  
**Documentation:** In Progress  
**Environment:** Authorized Private Cybersecurity Homelab

[Return to Homelab Infrastructure](../README.md) | [Main Portfolio](../../README.md)