# Offensive Security

This section documents my hands-on development in offensive cybersecurity through authorized testing, network reconnaissance, service enumeration, vulnerability assessment, and controlled security exercises.

My offensive security work is conducted within a privately managed cybersecurity homelab designed to support practical learning while providing opportunities to evaluate defensive monitoring and network security controls.

The objective is to understand how vulnerabilities and exposed services can be identified, how testing activity interacts with security controls, and how technical findings can be documented accurately.

## Testing Environment

My offensive security environment is hosted on Proxmox VE and incorporates network segmentation through OPNsense.

| Component | Function |
|---|---|
| Kali Linux | Primary security testing workstation |
| Metasploitable 2 | Intentionally vulnerable testing target |
| OPNsense | Firewall enforcement, routing, and traffic logging |
| Proxmox VE | Virtualization and isolated lab infrastructure |
| Wazuh SIEM | Security monitoring and defensive visibility analysis |

Kali Linux and Metasploitable 2 operate on separate logical networks, with routed communication controlled by OPNsense.

This architecture supports the study of network behavior, service exposure, firewall enforcement, and monitoring visibility.

[View Homelab Architecture](../01-homelab-infrastructure/PRJ-001-homelab-architecture/)

## Practical Testing Activities

### Network Reconnaissance

Hands-on exercises have included network discovery, port scanning, and service identification using Nmap.

These activities support an understanding of network exposure, reachable services, and information gathering during authorized security assessments.

### Service Connectivity Validation

Netcat has been used to evaluate TCP connectivity to services running on the vulnerable testing environment.

A documented FTP connectivity test confirmed that TCP port 21 was reachable on Metasploitable 2.

Port reachability demonstrates connectivity to a service. It does not, by itself, establish successful vulnerability exploitation.

### Firewall & Traffic Analysis

Testing traffic between Kali Linux and Metasploitable 2 has been examined using OPNsense firewall logs.

These observations help evaluate whether traffic reaches the intended destination, how firewall rules are applied, and which events are visible to defensive monitoring systems.

### Security Monitoring Correlation

Offensive testing provides opportunities to examine how network activity appears in Wazuh and other monitoring sources.

This allows offensive activity to be evaluated alongside defensive visibility, including situations where a corresponding security alert cannot be established.

## Tools & Technologies

| Tool | Application |
|---|---|
| Kali Linux | Security testing environment |
| Nmap | Network discovery, port scanning, and service identification |
| Netcat | TCP connectivity validation |
| Metasploitable 2 | Vulnerable service testing |
| OPNsense | Firewall logging and traffic analysis |
| Wazuh | Security event investigation |
| Proxmox VE | Lab virtualization and network infrastructure |

The listed tools are part of my documented testing environment. Their inclusion does not imply that every feature or exploitation technique has been used.

## Related Investigation

### CASE-001 — FTP Backdoor Traffic & SIEM Visibility Investigation

**Status:** Investigation Ongoing

This case study originated from controlled FTP-related testing against Metasploitable 2.

Follow-up validation confirmed network connectivity and documented firewall activity, while the corresponding Wazuh alert could not be identified through the recorded search criteria.

The investigation demonstrates the relationship between offensive testing and defensive monitoring.

Successful FTP backdoor exploitation has not been established by the available evidence.

[View CASE-001 Investigation](../03-incident-response/CASE-001-ftp-siem-visibility/)

## Assessment Methodology

My testing documentation follows a structured process:

1. **Scope:** Identify authorized systems, objectives, and testing boundaries.
2. **Reconnaissance:** Identify reachable hosts, ports, and services.
3. **Enumeration:** Gather additional information relevant to the assessed services.
4. **Validation:** Examine observed behavior and determine what the testing actually establishes.
5. **Defensive Review:** Compare testing activity with available firewall and monitoring records.
6. **Reporting:** Document procedures, supporting evidence, findings, limitations, and lessons learned.

Individual exercises will document the specific methodology and tools used rather than assuming every stage was completed.

## Future Development

Planned exercises include:

- Expanded service enumeration and vulnerability assessment
- Web application security testing
- Controlled exploitation and post-exploitation analysis
- Linux privilege escalation exercises
- Network segmentation and firewall bypass validation within authorized scope
- Detection and log correlation following simulated attacks
- Reproducible vulnerability reporting

These activities represent future development objectives and are not presented as completed investigations.

## Documentation & Testing Standards

All offensive security exercises are limited to systems I own or have explicit authorization to test.

Technical reports distinguish confirmed results from hypotheses, record relevant testing conditions, and preserve supporting evidence where available.

Public documentation excludes sensitive live infrastructure information, credentials, and unnecessary exposure of private systems.

## Current Status

**Status:** Active — Exercises and Documentation in Progress

The testing environment is operational, and network reconnaissance and connectivity validation activities have been performed.

Dedicated offensive security case studies will be added as individual exercises are completed and their findings reviewed.

---

**Focus:** Authorized Security Testing & Vulnerability Assessment  
**Environment:** Private Cybersecurity Homelab

[Return to Main Portfolio](../README.md) | [View Incident Response](../03-incident-response/)