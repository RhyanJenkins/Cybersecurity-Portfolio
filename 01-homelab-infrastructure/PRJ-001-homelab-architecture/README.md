# PRJ-001: Cybersecurity Homelab Architecture & Security Design

**Project Type:** Infrastructure and Security Engineering  
**Environment:** Self-hosted Cybersecurity homelab  
**Status:** Active — Documentation in Progress

## 1. Project Overview

This project documents the architecture, implementation, and security design of a virtualized cybersecurity homelab built for practical training in offensive security, defensive security, digital forensics, and incident response.

The environment uses Proxmox VE as its virtualization platform, with dedicated virtual machines supporting penetration testing, security monitoring, network defense, and Linux administration.

The homelab provides a controlled environment for generating security events, investigating suspicious activity, evaluating security controls, and developing practical cybersecurity skills.

## 2. Project Objectives

- Build and administer a virtualized cybersecurity environment.
- Configure network segmentation and firewall policies.
- Deploy centralized security monitoring.
- Perform authorized penetration testing against intentionally vulnerable systems.
- Investigate network traffic and security events.
- Develop troubleshooting, documentation, and incident investigation skills.
- Support future digital forensics and incident response exercises.

## 3. Technologies Used

| Technology | Purpose |
|---|---|
| Proxmox VE | Virtualization and VM management |
| OPNsense | Firewall, routing, and network security |
| Wazuh | Centralized security monitoring and log analysis |
| Kali Linux | Offensive security and testing |
| Debian Linux | Linux administration and security monitoring |
| Metasploitable | Intentionally vulnerable testing environment |
| Tailscale | Secure remote administration |
| nftables | Linux host firewall management |

## 4. Infrastructure Architecture

The environment uses multiple Proxmox hosts to support cybersecurity training and experimentation.

Virtual machines are assigned roles based on their intended purpose, including network security, offensive testing, defensive monitoring, and vulnerable target systems.

OPNsense provides firewall and routing capabilities for the lab network.

Wazuh provides centralized security monitoring and supports analysis of security events collected from integrated systems.

Kali Linux is used to perform authorized testing against lab targets, while Debian provides a platform for Linux security configuration and investigation exercises.

A sanitized network topology diagram will be added after the current infrastructure connections have been verified.

## 5. Security Design

### Network Security

OPNsense is used to manage network traffic and implement firewall policies within the cybersecurity environment.

The environment supports testing firewall behavior, observing network traffic, and investigating security events.

### Security Monitoring

Wazuh is deployed as the security monitoring platform.

The environment includes monitored systems and supports exercises involving log analysis, security investigations, and event correlation.

### Offensive Security

Kali Linux and intentionally vulnerable targets support controlled security testing.

Testing is performed within authorized lab environments for educational and defensive research purposes.

### Remote Administration

Tailscale provides remote administrative connectivity to selected homelab systems without requiring direct public exposure of their management interfaces.

## 6. Validation and Testing

The environment has been used for:

- Network connectivity testing
- Nmap reconnaissance
- SSH connectivity validation
- Firewall rule testing
- Wazuh agent connectivity checks
- Controlled penetration testing
- Security log investigation

Detailed results and supporting evidence will be documented in their respective project reports.

## 7. Challenges and Lessons Learned

Building the homelab has involved troubleshooting network connectivity, firewall behavior, VM configuration, monitoring integration, and security event visibility.

These challenges provide opportunities to develop systematic troubleshooting and investigation techniques.

Specific issues, supporting evidence, resolutions, and unresolved limitations will be documented as separate technical case studies.

## 8. Future Development

Planned improvements and exercises include:

- Digital forensic evidence acquisition and analysis
- Incident timeline reconstruction
- Network packet analysis
- Advanced Wazuh detection engineering
- IDS/IPS analysis
- Linux security hardening
- Security automation and scripting

## 9. Documentation and Security

Public documentation excludes sensitive credentials, private management endpoints, and configuration information that could unnecessarily expose the live environment.

Where appropriate, sanitized diagrams and example addressing will be used.

---

**Project Status:** Active  
**Documentation:** In progress  
**Environment:** Authorized private cybersecurity homelab
