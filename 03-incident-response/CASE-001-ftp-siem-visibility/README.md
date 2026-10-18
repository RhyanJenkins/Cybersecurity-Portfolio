# CASE-001: FTP Backdoor Traffic and SIEM Visibility Investigation

**Category:** Incident Response / Network Security / Detection Analysis  
**Environment:** Private Cybersecurity Homelab  
**Related Exercise:** EX-002 — FTP Traffic and SIEM Visibility Investigation  
**Status:** Investigation Ongoing  
**Root Cause:** Not Yet Determined

## 1. Executive Summary

This case study examines security monitoring visibility during controlled FTP-related testing against a Metasploitable 2 virtual machine.

Testing originated from Kali Linux in a segmented cybersecurity homelab. Network traffic between Kali and the target traversed an OPNsense firewall.

The investigation began following an FTP backdoor testing exercise in which relevant traffic was observed in OPNsense but corresponding activity was not identified through Wazuh searches.

A subsequent validation exercise, EX-002, confirmed that the target's FTP TCP port was reachable and that OPNsense recorded a permitted TCP SYN packet associated with the test.

However, a Wazuh Threat Hunting search did not locate a corresponding alert using the documented criteria.

The investigation remains open. Available evidence does not establish successful FTP backdoor exploitation or conclusively identify why the expected activity was not found in Wazuh.

## 2. Investigation Objectives

- Validate communication between the security testing and vulnerable networks.
- Confirm firewall visibility into FTP-related traffic.
- Examine source, destination, protocol, port, and firewall action.
- Review Wazuh agent connectivity and available security alerts.
- Search for events corresponding to the controlled test.
- Identify limitations in available monitoring evidence.
- Document verified findings and unresolved investigative questions.

## 3. Lab Environment

| Component | Role |
|---|---|
| Kali Linux | Security testing workstation |
| Metasploitable 2 | Intentionally vulnerable target |
| OPNsense | Firewall, routing, and traffic logging |
| Wazuh SIEM | Centralized security monitoring |
| Proxmox VE | Virtualization platform |

Kali and Metasploitable operate on separate logical networks.

Previous validation confirmed that their routed communication traverses OPNsense.

The environment is privately controlled and used exclusively for authorized testing.

[View Homelab Architecture](../../01-homelab-infrastructure/PRJ-001-homelab-architecture/)

## 4. Test Scenario and Methodology

### Initial Investigation

The investigation originated from controlled FTP backdoor testing against Metasploitable 2.

Relevant network activity was observed through OPNsense firewall logging, but corresponding records were not identified in subsequent Wazuh searches.

The original testing history is retained separately from the later connectivity validation because the available evidence does not establish that both activities generated identical network events.

### EX-002 — Follow-Up Validation

On October 16, 2026, additional testing and evidence collection were performed.

The validation involved:

1. Confirming that the Wazuh monitoring agents were active.
2. Reviewing existing OPNsense-related Wazuh alerts.
3. Testing connectivity from Kali to the target's FTP port.
4. Examining the corresponding OPNsense firewall event.
5. Searching Wazuh Threat Hunting for activity involving the target.

The follow-up established a verified network-level observation and a separate, unsuccessful attempt to locate a corresponding Wazuh alert.

## 5. Evidence and Observations

### 5.1 Wazuh Agent Connectivity

The Wazuh dashboard displayed active integrations for:

- OPNsense
- Debian Linux

This confirmed that both agents were reported as active at the time of observation.

Agent connectivity alone does not establish complete collection or detection coverage.

### 5.2 Existing Wazuh Firewall Alerts

Wazuh Threat Hunting displayed firewall-related alerts from the OPNsense agent.

One observed alert type was associated with Wazuh rule 87702, describing multiple firewall block events from the same source.

This demonstrates that some OPNsense-related security activity was available in Wazuh.

It does not establish that the permitted FTP event was ingested, decoded, indexed, or converted into an alert.

### 5.3 Kali FTP Connectivity Test

Kali Linux was used to test TCP connectivity to port 21 on the Metasploitable target.

The Netcat test returned a result indicating that the FTP TCP port was open.

**Verified observation:** TCP connectivity to the target's FTP port was successful.

**Limitation:** An open port does not establish that a vulnerability was exploited or that the FTP backdoor was activated.

### 5.4 OPNsense Firewall Event

OPNsense Firewall Live View recorded a permitted TCP SYN packet associated with the connectivity test.

| Field | Observed Value |
|---|---|
| Date | October 16, 2026 |
| Displayed Time | 20:02:48 |
| Source | Kali Linux |
| Source Port | 34342 |
| Destination | Metasploitable 2 |
| Destination Port | TCP/21 |
| Protocol | TCP |
| TCP Flags | SYN |
| Firewall Action | Pass |
| Interface | vtnet1 |
| Direction | In |
| Firewall Rule | 49 |
| Rule Label | Log Kali to Metasploitable |

The timestamp is recorded as displayed in OPNsense. The display time zone has not been independently verified.

**Verified observation:** OPNsense permitted and logged the tested TCP SYN packet.

This confirms firewall visibility into the recorded communication attempt.

It does not, by itself, establish completion of a TCP session or successful exploitation.

### 5.5 Wazuh Threat Hunting Search

A follow-up search was performed in Wazuh Threat Hunting using the Metasploitable target's private IP address as the search term.

The search was restricted to the OPNsense agent, with a displayed time range beginning October 16, 2026, at 11:00 and ending at the time of the search.

No matching results were returned.

**Verified observation:** No corresponding result was identified under the displayed search criteria.

**Limitation:** This does not establish whether the underlying firewall record was forwarded, received, archived, decoded, indexed, or excluded from alert generation.

The difference between the OPNsense timestamp and Wazuh's displayed time settings has not been fully reconciled.

## 6. Evidence Correlation

| Evidence Source | Finding | Interpretation |
|---|---|---|
| Kali Linux | FTP TCP port reported open | Target port was reachable |
| OPNsense | Permitted TCP SYN recorded | Firewall observed the connection attempt |
| Wazuh Agents | OPNsense and Debian active | Agent connectivity confirmed |
| Wazuh Alerts | Other firewall alerts present | Some OPNsense event visibility confirmed |
| Wazuh Target Search | No matching result | No corresponding alert found using the recorded search criteria |

The available evidence supports network connectivity and firewall-level visibility.

It does not yet establish complete end-to-end visibility for the specific FTP event.

## 7. Investigative Findings

### Finding 1 — Network Connectivity

Kali successfully reached the target's FTP TCP port.

**Status:** Verified

### Finding 2 — Firewall Logging

OPNsense recorded a permitted TCP SYN packet associated with the test.

**Status:** Verified

### Finding 3 — Monitoring Integration

The OPNsense Wazuh agent was active, and unrelated firewall alerts were visible in Wazuh.

**Status:** Verified

### Finding 4 — SIEM Correlation

The documented Wazuh search did not locate a corresponding alert for the target.

**Status:** No Matching Result Identified

### Finding 5 — Root Cause

The reason for the missing Wazuh search result remains undetermined.

**Status:** Unresolved

## 8. Outstanding Investigative Questions

Further investigation is needed to determine:

1. Whether the specific permitted firewall event was forwarded to Wazuh.
2. Whether the event was received by the Wazuh manager.
3. Whether the event was successfully decoded.
4. Whether an applicable detection rule generated an alert.
5. Whether the event was retained in raw archives or another searchable data source.
6. Whether time-zone differences or search constraints affected correlation.

These are investigative leads, not confirmed explanations.

## 9. Evidence Management

The original EX-002 investigation evidence is maintained privately using structured evidence identifiers.

Collected material includes:

- Wazuh agent-status screenshots
- Existing OPNsense-related Wazuh alert results
- OPNsense firewall traffic views
- Kali TCP connectivity test output
- Expanded OPNsense firewall event details
- Wazuh search results showing no matches

Original screenshots are preserved separately from any copies prepared for public release.

**Public Evidence Status:** Sanitized artifacts have not yet been attached to this repository.

Before publication, selected artifacts will be reviewed for sensitive infrastructure details, timestamps, source context, accuracy, and evidence integrity.

## 10. Lessons Learned

This investigation demonstrates the importance of separating network connectivity, firewall visibility, centralized event collection, and SIEM alert generation.

An active monitoring agent does not guarantee that every observed event produces a searchable alert.

Likewise, an unsuccessful SIEM search does not conclusively establish that the underlying event was never received.

The investigation also reinforces the importance of preserving original evidence, documenting search criteria, and distinguishing verified findings from unresolved hypotheses.

## 11. Investigation Status and Next Steps

**Status:** Open — Further Validation Required

The next investigative phase will focus on verifying the underlying OPNsense-to-Wazuh event collection path.

Planned activities include:

- Inspecting available Wazuh raw event archives and relevant collection configuration
- Validating forwarding and receipt of permitted firewall events
- Reviewing decoding and detection-rule behavior
- Reconciling timestamps and search constraints
- Updating findings based on repeatable evidence

These validation activities have not yet been completed.

---

**Case ID:** CASE-001  
**Related Exercise:** EX-002  
**Investigation Status:** Open  
**Root Cause:** Not Verified  
**Public Evidence:** Pending Sanitization and Review  
**Testing Scope:** Authorized Private Homelab

[Return to Incident Response](../README.md) | [Main Portfolio](../../README.md)