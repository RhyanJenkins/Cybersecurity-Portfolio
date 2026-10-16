# Infrastructure Validation and Evidence

**Project:** PRJ-001 — Cybersecurity Homelab Architecture & Security Design  
**Category:** Infrastructure Validation / Security Testing  
**Status:** Historical validation documented; evidence collection ongoing

## 1. Purpose

This document records validation activities performed against the cybersecurity homelab.

The objective is to demonstrate that infrastructure components operate as intended and that security controls can be evaluated through repeatable testing.

Validation records distinguish between previously confirmed functionality, preserved evidence, and findings requiring further investigation.

## 2. Validation Summary

| ID | Validation Activity | Result | Evidence Status |
|---|---|---|---|
| VAL-001 | Proxmox management connectivity | Previously confirmed | Not attached |
| VAL-002 | Kali-to-Metasploitable connectivity | Confirmed | Not attached |
| VAL-003 | OPNsense traffic visibility | Confirmed | Historical screenshots referenced |
| VAL-004 | Vulnerable network isolation | Previously confirmed | Not attached |
| VAL-005 | Debian SSH connectivity | Confirmed | Not attached |
| VAL-006 | Debian Wazuh agent connectivity | Confirmed | Not attached |
| VAL-007 | OPNsense Wazuh integration | Confirmed | Not attached |
| VAL-008 | FTP backdoor activity in OPNsense | Observed | Historical screenshots referenced |
| VAL-009 | Corresponding FTP activity in Wazuh | Not located during investigation | Further analysis required |

## 3. Network Connectivity Validation

### Objective

Verify that the security testing environment can communicate with the intentionally vulnerable target network through OPNsense.

### Environment

- Source: Kali Linux
- Destination: Metasploitable 2
- Firewall: OPNsense
- Virtualization platform: Proxmox VE

### Observations

Previous testing confirmed that Kali could communicate with Metasploitable.

Traffic associated with testing was observed in OPNsense firewall logs.

### Conclusion

The tested communication path between the security testing and vulnerable networks was operational.

These results support the documented logical routing relationship through OPNsense.

## 4. Network Isolation Validation

### Objective

Evaluate whether the intentionally vulnerable environment is restricted from accessing the primary home network and Internet.

### Observations

Previous connectivity testing confirmed restrictions on access from the vulnerable environment to the primary home network and Internet.

### Conclusion

The tested restrictions were functioning during the previous validation.

These observations do not establish that every possible network path or protocol is blocked.

## 5. Wazuh Agent Connectivity

### Objective

Verify that monitored systems successfully connect to the Wazuh management platform.

### Observations

Debian Linux and OPNsense were previously confirmed as active integrations within Wazuh.

### Conclusion

The monitoring integrations were operational at the time of validation.

Agent connectivity alone does not establish complete security event collection or detection coverage.

## 6. Firewall and SIEM Visibility Investigation

### Objective

Compare firewall-level observations with centralized SIEM visibility during controlled penetration testing.

### Observations

During a controlled FTP backdoor test against Metasploitable:

- Relevant traffic was observed in OPNsense firewall logs.
- Corresponding events were not located during the initial Wazuh searches.

### Findings

The investigation identified a difference between observed firewall traffic and the events located in Wazuh.

The cause has not yet been conclusively established.

Possible areas for further investigation include log collection, forwarding, parsing, indexing, detection rules, and search criteria.

These are investigative possibilities, not verified causes.

## 7. Evidence Management

Evidence associated with validation activities should include:

- Unique evidence identifier
- Related validation or exercise ID
- Source system
- Collection date and time
- Time zone
- Collection method
- Original filename
- Integrity hash, where applicable
- Description of observed activity
- Sanitization or modification record

Original evidence should be preserved separately from edited copies intended for public release.

## 8. Evidence Limitations

Some validation activities were completed before the formal evidence documentation process was established.

Consequently, historical results may not have complete timestamps, command transcripts, or preserved screenshots.

These limitations are documented rather than reconstructed from assumptions.

Future exercises will use standardized evidence collection procedures.

## 9. Future Validation

Planned activities include:

- Repeatable network isolation tests
- Security event correlation
- Log forwarding verification
- Detection rule testing
- File integrity monitoring validation
- Incident timeline reconstruction
- Evidence integrity verification

---

**Validation Status:** Historical testing documented  
**Evidence Status:** Collection and organization ongoing  
**Outstanding Investigation:** FTP backdoor SIEM visibility
