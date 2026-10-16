
# Cybersecurity Homelab — Network Topology

**Project:** PRJ-001  
**Diagram Type:** Logical network architecture  
**Status:** Documented and maintained

## Network Diagram

```mermaid
flowchart TB
    HOME["Home Network / Router"]

    subgraph PVE1["pve1 — HP Desktop"]
        WAZUH["Wazuh SIEM"]
    end

    subgraph PVE2["pve2 — Dell Laptop"]
        FW["OPNsense Firewall"]

        subgraph LAN["Security Testing LAN"]
            KALI["Kali Linux"]
            DEBIAN["Debian Linux"]
        end

        subgraph VULN["Vulnerable Network"]
            META["Metasploitable 2"]
        end
    end

    HOME --- PVE1
    HOME --- FW
    KALI <-->|Routed traffic| FW
    DEBIAN --- FW
    FW <-->|Filtered traffic| META
    FW -.->|Security logs| WAZUH
    DEBIAN -.->|Wazuh agent| WAZUH
```

## Network Zones

### Primary Network

Provides connectivity to the Proxmox infrastructure
and selected management services.

### Security Testing LAN

Hosts security testing and monitored Linux systems,
including Kali Linux and Debian.

### Vulnerable Network

Contains Metasploitable 2, an intentionally vulnerable
system used for authorized security testing.

OPNsense controls routed communication between the
security testing and vulnerable networks.

## Verified Traffic Flow

Previous testing confirmed communication from Kali Linux
to Metasploitable through OPNsense.

OPNsense firewall logs provided visibility into the
associated traffic.

## Security Monitoring

Wazuh provides centralized security monitoring.

OPNsense and Debian have been integrated with Wazuh
for security event collection and investigation.

## Diagram Notes

- This is a logical architecture diagram.
- Physical wiring and bridge uplinks are not depicted.
- Live IP addresses and management endpoints are excluded.
- Monitoring relationships are distinct from traffic paths.
- The diagram is maintained as the environment changes.
