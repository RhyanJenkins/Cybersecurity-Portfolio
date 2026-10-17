# Homelab Infrastructure

This section documents the architecture, implementation, security controls, and ongoing development of my self-hosted cybersecurity homelab.

The environment is designed to support hands-on security engineering, authorized penetration testing, centralized monitoring, incident response, and digital forensics training.

## Featured Infrastructure Project

### PRJ-001 — Cybersecurity Homelab Architecture & Security Design

**Category:** Infrastructure & Security Engineering  
**Status:** Active — Documentation in Progress

A virtualized cybersecurity environment built across two Proxmox VE hosts, with separate roles for security monitoring, network defense, offensive testing, and intentionally vulnerable systems.

The environment incorporates OPNsense for network segmentation and firewall enforcement, Wazuh for centralized security monitoring, and Kali Linux for controlled security assessments.

[**View PRJ-001 — Complete Project Documentation**](PRJ-001-homelab-architecture/)

## Infrastructure Overview

| Component | Purpose |
|---|---|
| Proxmox VE | Virtualization and infrastructure administration |
| OPNsense | Network routing, segmentation, and firewall enforcement |
| Wazuh SIEM | Centralized security monitoring and log analysis |
| Kali Linux | Authorized security testing and reconnaissance |
| Debian Linux | Linux administration, hardening, and endpoint monitoring |
| Metasploitable 2 | Intentionally vulnerable testing environment |
| Tailscale | Secure remote administration |
| nftables | Linux host firewall management |

The lab separates security testing systems from intentionally vulnerable targets through OPNsense-controlled network boundaries.

Firewall logging and centralized monitoring support investigations into network activity, system behavior, and security events.

## Technical Documentation

| Document | Description |
|---|---|
| [Architecture & Security Design](PRJ-001-homelab-architecture/architecture.md) | System roles, network separation, and security architecture |
| [Physical & Virtual Infrastructure](PRJ-001-homelab-architecture/infrastructure.md) | Hardware specifications, VM placement, and virtualization design |
| [Network Topology](PRJ-001-homelab-architecture/network-topology.md) | Logical network diagram, security zones, and communication paths |
| [Security Monitoring](PRJ-001-homelab-architecture/security-monitoring.md) | Wazuh integration, logging architecture, and monitoring limitations |
| [Validation & Evidence](PRJ-001-homelab-architecture/validation-and-evidence.md) | Connectivity testing, security validation, findings, and evidence status |
| [Evidence Management](PRJ-001-homelab-architecture/evidence/README.md) | Evidence requirements, templates, integrity, and documentation standards |

## Related Security Investigation

### CASE-001 — FTP Traffic & SIEM Visibility Investigation

An ongoing investigation examining firewall traffic visibility and security event correlation between OPNsense and Wazuh during controlled FTP testing.

The investigation documents verified network activity, Wazuh search results, and unresolved monitoring questions.

[View CASE-001 Investigation](../03-incident-response/CASE-001-ftp-siem-visibility/)

## Documentation & Security Standards

Infrastructure documentation emphasizes verified configurations, reproducible testing, evidence-based findings, and clear identification of outstanding issues.

Public records exclude live management addresses, credentials, and other sensitive infrastructure information. Original evidence is maintained separately from sanitized material prepared for publication.

---

**Project Status:** Active  
**Environment:** Authorized private cybersecurity homelab

[Return to Main Portfolio](../README.md)