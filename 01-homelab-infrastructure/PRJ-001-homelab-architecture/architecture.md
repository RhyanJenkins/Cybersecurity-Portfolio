# Cybersecurity Homelab — Technical Architecture

**Project:** PRJ-001 — Homelab Architecture & Security Design  
**Platform:** Proxmox VE  
**Documentation Status:** In Progress

## 1. Architecture Overview

This homelab uses Proxmox VE to host virtual machines for security monitoring, network defense, penetration testing, and cybersecurity investigations.

The environment includes a primary home network and a dedicated lab network managed by OPNsense.

The architecture supports controlled security testing, centralized log monitoring, and investigation of security events across multiple systems.

This document describes the verified infrastructure and identifies areas requiring further validation.

## 2. Physical Infrastructure

### pve1 — HP Desktop

**Role:** Virtualization host and security monitoring infrastructure

Known hosted services:

- Wazuh SIEM

Wazuh provides centralized security monitoring and supports log collection and investigation activities.

### pve2 — Dell Laptop

**Role:** Security testing and lab virtualization

Known hosted virtual machines:

- OPNsense
- Kali Linux
- Debian Linux
- Metasploitable

The environment supports offensive security testing, Linux administration, network security, and security monitoring exercises.


## 3. Network Architecture

### Network Segmentation

The cybersecurity homelab uses OPNsense to provide routing, firewall enforcement, and network separation between the security testing environment and the intentionally vulnerable target environment.

The architecture includes three logical networks:

| Network | Purpose |
|---|---|
| Primary Network | Home infrastructure and selected management services |
| Security Testing LAN | Security tools and monitored Linux systems |
| Vulnerable Network (VULN) | Intentionally vulnerable targets for authorized testing |

### Security Testing LAN

The security testing network hosts Kali Linux and Debian.

Kali provides offensive security testing capabilities, while Debian supports Linux administration, system hardening, and security monitoring exercises.

### Vulnerable Network

The VULN network contains Metasploitable 2, an intentionally vulnerable Linux system used for controlled penetration testing.

Metasploitable is hosted on pve2 and connected to Proxmox bridge `vmbr2`.

The bridge has a physical network interface attached, and the Metasploitable virtual network adapter does not use a VLAN tag.

### Verified Traffic Flow

The following communication path has been validated through previous security testing:

**Kali Linux → OPNsense → Metasploitable 2**

Testing confirmed that Kali could communicate with Metasploitable across the segmented networks.

OPNsense firewall logs provided visibility into the associated traffic.

Previous connectivity tests also confirmed restrictions on Metasploitable's access to the primary home network and Internet.

These controls help reduce the exposure of intentionally vulnerable systems.

### Security Monitoring

OPNsense is integrated with Wazuh, which operates on a separate Proxmox host.

Wazuh provides centralized collection and analysis of supported security events.

The monitoring architecture allows firewall activity to be investigated alongside information from monitored endpoints.

Firewall visibility and SIEM detection coverage are evaluated separately because observed network traffic does not necessarily produce a corresponding security alert.

### Public Documentation

The production homelab uses private IPv4 addressing.

Exact addressing, live management endpoints, and detailed firewall configurations are maintained in private infrastructure documentation.

Public architecture diagrams will use sanitized addressing and focus on logical security boundaries, communication paths, and defensive controls.

## 4. Security Monitoring Architecture

Wazuh is deployed as the centralized security monitoring platform.

Previously verified monitoring integrations include:

- Debian Linux Wazuh agent
- OPNsense Wazuh integration

The monitoring environment supports security event collection and analysis.

Network visibility depends on the available logging sources, network paths, and monitoring configurations.

The presence of a Wazuh agent or integration does not automatically guarantee that all network traffic or attack activity will generate detectable events.

## 5. Offensive Security Environment

Kali Linux provides security testing capabilities.

Metasploitable serves as an intentionally vulnerable target for authorized exercises.

Testing activities include network reconnaissance, vulnerability assessment, and controlled exploitation.

The environment is intended to support analysis of both attack behavior and defensive monitoring effectiveness.

## 6. Remote Administration

Tailscale provides remote access to the Proxmox management environment.

This enables administration without directly exposing Proxmox management services through public router port forwarding.

Live management addresses and private access identifiers are intentionally excluded from public documentation.

## 7. Security Boundaries and Controls

The homelab incorporates network segmentation, firewall enforcement, and centralized security monitoring to support controlled cybersecurity testing.

### Network Segmentation

OPNsense separates the security testing network from the intentionally vulnerable network.

Verified testing confirmed that traffic between Kali Linux and Metasploitable traverses OPNsense, allowing firewall policies to control communication between the two environments.

### Vulnerable System Isolation

Metasploitable operates within a dedicated vulnerable network.

Connectivity testing confirmed restrictions preventing the vulnerable system from accessing the primary home network and Internet.

These restrictions help reduce the risk associated with operating intentionally vulnerable systems.

### Firewall Enforcement and Visibility

OPNsense provides routing, firewall enforcement, and traffic logging between the security testing and vulnerable networks.

Firewall logs have been used to observe and investigate traffic generated during authorized penetration testing exercises.

### Centralized Security Monitoring

Wazuh provides centralized security monitoring, with previously verified integrations for OPNsense and Debian Linux.

The environment supports investigations involving network activity, security logs, and endpoint events.

### Monitoring Considerations

Firewall traffic visibility and SIEM detection coverage are distinct capabilities.

A firewall may record network activity without that activity necessarily generating a corresponding Wazuh event or alert.

Detection coverage must therefore be evaluated through controlled testing and log correlation.

## 8. Planned Documentation

Future additions will include:

- Sanitized network topology
- Verified traffic-flow diagrams
- Security control descriptions
- Network isolation testing
- SIEM visibility validation
- Technical troubleshooting case studies

## 9. Documentation Principles

This project follows these principles:

1. Document verified configurations.
2. Distinguish observed behavior from assumptions.
3. Record security limitations.
4. Exclude sensitive live management details from public documentation.
5. Update architecture records when the environment changes.

---

**Status:** Architecture documentation in progress.
