# Physical and Virtual Infrastructure

**Project:** PRJ-001 — Cybersecurity Homelab Architecture & Security Design  
**Platform:** Proxmox VE  
**Documentation Status:** Active

## 1. Infrastructure Overview

The cybersecurity homelab operates across two physical systems running Proxmox VE.

Each host has a designated role within the environment:

- **pve1:** Security monitoring and supporting infrastructure.
- **pve2:** Security testing, firewall services, and virtualized lab systems.

This arrangement supports cybersecurity exercises involving network reconnaissance, penetration testing, security monitoring, and incident investigations.

## 2. Physical Hardware

### pve1 — HP ENVY Desktop

**Model:** HP ENVY TE01-1xxx

| Component | Specification |
|---|---|
| Processor | Intel Core i5-10400 |
| CPU Cores / Threads | 6 cores / 12 threads |
| Base Frequency | 2.90 GHz |
| Memory | 12 GB DDR4 |
| Memory Speed | 2667 MT/s |
| Storage | Approximately 1 TB NVMe SSD |
| Hypervisor | Proxmox VE |

**Primary Role:** Security monitoring infrastructure.

The host runs the Wazuh SIEM virtual machine, providing centralized monitoring capabilities for the cybersecurity environment.

### pve2 — Dell Inspiron Laptop

**Model:** Dell Inspiron 15 3520

| Component | Specification |
|---|---|
| Processor | Intel Core i7-1255U |
| CPU Cores / Threads | 10 cores / 12 threads |
| Memory | 16 GB |
| Storage | Approximately 1 TB NVMe SSD |
| Hypervisor | Proxmox VE |
| Wired Networking | USB 3.0 Gigabit Ethernet adapter |

**Primary Role:** Security testing and lab virtualization.

The host runs virtual machines used for network security, penetration testing, Linux administration, and controlled security exercises.

## 3. Virtual Machine Inventory

| Virtual Machine | Host | Primary Function |
|---|---|---|
| Wazuh SIEM | pve1 | Centralized security monitoring |
| OPNsense | pve2 | Firewall, routing, and network segmentation |
| Kali Linux | pve2 | Offensive security testing |
| Debian Linux | pve2 | Linux administration and security monitoring |
| Metasploitable 2 | pve2 | Intentionally vulnerable target |

### Wazuh SIEM

Wazuh provides centralized security monitoring and supports analysis of security events generated throughout the homelab.

Previously verified monitoring integrations include Debian Linux and OPNsense.

### OPNsense

OPNsense provides firewall and routing services for the cybersecurity lab.

The firewall separates the security testing network from the intentionally vulnerable network.

Previous testing confirmed that traffic between Kali Linux and Metasploitable traverses OPNsense.

### Kali Linux

Kali Linux provides security assessment and penetration testing tools.

The system is used for authorized reconnaissance, vulnerability assessment, and controlled attack simulations.

### Debian Linux

Debian provides a general-purpose Linux environment for system administration, security configuration, and defensive security exercises.

The system is integrated with Wazuh for security monitoring.

### Metasploitable 2

Metasploitable is an intentionally vulnerable Linux virtual machine used for controlled penetration testing.

The VM is hosted on pve2 and connected to Proxmox bridge `vmbr2`.

Testing confirmed communication between Kali and Metasploitable through OPNsense.

## 4. Virtualization Design

Proxmox VE provides centralized management of the virtual machines running on each physical host.

The virtualization environment supports:

- Virtual machine deployment and configuration
- Virtual network interfaces and Linux bridges
- VM snapshots
- Resource allocation
- Remote administrative access

Virtualization allows multiple cybersecurity systems to operate on shared physical hardware while maintaining separate virtual machine environments.

## 5. Resource Considerations

The homelab operates using existing consumer hardware rather than dedicated enterprise infrastructure.

Resource allocation must account for available CPU capacity, memory, and storage.

The physical hosts have different hardware capabilities and workloads.

The environment is designed to support practical cybersecurity learning while operating within these hardware constraints.

## 6. Remote Infrastructure Management

Tailscale provides remote administrative connectivity to the Proxmox hosts.

This enables access to the virtualization management interfaces without requiring direct public exposure of those interfaces.

Live management addresses and private access identifiers are excluded from public documentation.

## 7. Infrastructure Validation

Previously completed validation activities include:

- Proxmox host management connectivity
- Virtual machine network connectivity
- SSH access to Linux systems
- OPNsense routing and firewall testing
- Wazuh agent connectivity verification
- Controlled penetration testing connectivity
- Remote Proxmox management through Tailscale

These activities help establish that the infrastructure supports its intended cybersecurity training functions.

## 8. Future Improvements

Potential future infrastructure improvements include:

- Additional forensic analysis environments
- Expanded network monitoring capabilities
- Additional intentionally vulnerable systems
- Improved backup and recovery procedures
- Security automation
- More detailed resource utilization documentation

---

**Project Status:** Active  
**Documentation:** Maintained as the homelab evolves.
