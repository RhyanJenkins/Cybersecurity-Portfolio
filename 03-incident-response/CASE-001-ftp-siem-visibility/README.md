# CASE-001: FTP Backdoor Traffic and SIEM Visibility Investigation

**Category:** Incident Response / Network Security / Detection Analysis
**Environment:** Private Cybersecurity Homelab
**Status:** Investigation Ongoing

## 1. Executive Summary

This case study examines security monitoring visibility during a controlled FTP backdoor test against an intentionally vulnerable Metasploitable 2 virtual machine.

The test was conducted from Kali Linux within a segmented cybersecurity homelab.

Network traffic associated with the test was observed in OPNsense firewall logs. However, corresponding events were not located during subsequent searches in Wazuh.

The investigation focuses on understanding the differences between network-level visibility, centralized log collection, and security alert generation.

The root cause of the missing Wazuh search results has not yet been conclusively determined.

## 2. Investigation Objectives

- Generate security-relevant activity within an authorized lab environment.
- Verify network communication between the attacking and target systems.
- Examine firewall logs associated with the test.
- Search Wazuh for corresponding security events.
- Compare available evidence across monitoring platforms.
- Identify potential gaps in security event visibility.
- Document investigative findings and limitations.

## 3. Lab Environment

| Component        | Role                                                       |
| ---------------- | ---------------------------------------------------------- |
| Kali Linux       | Security testing workstation                               |
| Metasploitable 2 | Intentionally vulnerable target                            |
| OPNsense         | Network routing, firewall enforcement, and traffic logging |
| Wazuh SIEM       | Centralized security event monitoring                      |
| Proxmox VE       | Virtualization infrastructure                              |

Kali Linux and Metasploitable operate on separate logical networks.

Previous testing confirmed that communication between these systems traverses OPNsense.

The lab is privately controlled and used for authorized cybersecurity exercises.

## 4. Test Scenario

The investigation originated from a controlled FTP backdoor test against Metasploitable 2.

Kali Linux was used to initiate testing against the vulnerable target.

The test generated network activity that could be examined through OPNsense firewall logging.

The investigation then attempted to identify corresponding records within Wazuh.

Detailed execution commands, timestamps, and supporting artifacts will be added after reviewing the original exercise records.

## 5. Initial Observations

### OPNsense Firewall

Relevant network activity was observed in the OPNsense firewall logs during the test.

This established that the firewall provided visibility into the tested communication path.

### Wazuh SIEM

Searches were performed for activity associated with the test, including searches using the involved IP addresses.

Corresponding events were not located during the investigation.

This observation does not establish that Wazuh failed to receive the underlying log data.

## 6. Preliminary Analysis

The observations raise several investigative questions:

1. Were the relevant firewall events forwarded to Wazuh?
2. Were the events successfully received and processed?
3. Did the available decoders recognize the log format?
4. Were the events indexed or retained in a searchable location?
5. Did the configured detection rules generate alerts?
6. Were the searches performed against the appropriate time range and data source?

These questions represent investigative leads rather than confirmed causes.

## 7. Findings

**Finding 1 — Firewall Visibility**

OPNsense recorded traffic associated with the controlled test.

**Finding 2 — SIEM Search Visibility**

Corresponding activity was not located during the initial Wazuh searches.

**Finding 3 — Root Cause**

The cause of the visibility difference remains undetermined.

Additional validation is necessary before concluding whether the issue involves forwarding, collection, parsing, indexing, detection, or search configuration.

## 8. Evidence Status

The original investigation included screenshots of OPNsense and Wazuh.

Evidence artifacts have not yet been attached to this public case study.

Before publication, selected artifacts will be reviewed for accuracy, timestamps, sensitive information, and relevance.

## 9. Investigation Status

The investigation remains open.

Future work will focus on validating the event collection path and determining why the expected activity was not located in Wazuh.

## 10. Lessons Learned

This exercise highlights the importance of distinguishing among:

- Network traffic visibility
- Firewall event generation
- Centralized log ingestion
- Event parsing and indexing
- Detection rule matching
- Security alert generation

A functioning monitoring integration does not guarantee that every security-relevant event will be visible through every search or alert interface.

---

**Case Status:** Open
**Root Cause:** Not yet verified
**Evidence:** Pending review and publication
**Testing Scope:** Authorized private homelab
