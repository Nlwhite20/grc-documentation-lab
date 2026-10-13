# System Description (home lab)

Draft 2026-10-13. Describes the environment that the control inventory and self-assessments
cover. Modelled loosely on the system description section of a SOC 2 report; this is not one.

## Purpose of the system

A personal lab used to practise IT operations, security monitoring and GRC. It processes only
lab data: configuration files, system and security logs, alerts, scan results and backups. No
customer, employer or third-party personal data.

## In scope

| Component | Role | Detail (from lab repositories) |
| --- | --- | --- |
| Mac host | Hypervisor (UTM) and operator workstation; holds the third backup copy | Apple silicon Mac; VMs on UTM shared (NAT) network |
| `wazuh-siem` | SIEM | Ubuntu 24.04; Wazuh 4.14.8 single-node (upgraded from 4.14.7 on 2026-10-13) (manager, indexer, dashboard) in Docker; admin interfaces bound to loopback ([wazuh-siem-lab](https://github.com/Nlwhite20/wazuh-siem-lab)) |
| `soc-endpoint-01` | Monitored endpoint and IDS sensor | Ubuntu 26.04; Wazuh agent 002; Suricata 8.0.3 ([network-security-lab](https://github.com/Nlwhite20/network-security-lab)) |
| `ubuntu-mgmt` | Management, scanner, backup server | Ubuntu 26.04; restic rest-server (append-only, TLS) ([backup-restore-lab](https://github.com/Nlwhite20/backup-restore-lab)) |
| `noc-monitoring` | Availability monitoring | Ubuntu; Prometheus, Grafana, Uptime Kuma, alerting to a private Discord channel ([noc-monitoring-lab](https://github.com/Nlwhite20/noc-monitoring-lab)); usually powered off |
| Lab network | Connectivity | UTM shared network (NAT) on the Mac; isolation from the home network not independently tested |

## Out of scope

The Mac's own operating system hardening, the home network and router, GitHub and Discord as
services (they are third parties, see below), and the inactive VM clone `noc-monitoring-02`.

## People and roles

One person (the lab owner) holds every role: administrator, operator, reviewer and approver.
**There is no segregation of duties**; this is a known limitation of the self-assessment.

## Third parties relied on

| Third party | Used for |
| --- | --- |
| Ubuntu (Canonical) | Operating systems, packages, security tracker data |
| Wazuh | SIEM software and vulnerability feed |
| Open Information Security Foundation (Suricata, suricata-update) and Proofpoint ET Open rules | IDS software and rules |
| restic project | Backup software |
| GitHub | Public documentation repositories |
| Discord | Alert notification channel (NOC lab) |
| Anthropic (Claude) | AI assistant for drafting and planning; all actions run and approved by the owner |

## Data

| Data | Where | Protection |
| --- | --- | --- |
| Configuration and secrets (agent keys, service passwords) | Lab VMs | Root-only files; never committed; rotated defaults where documented |
| Logs and alerts | Wazuh indexer, VM logs | Loopback-only access to the SIEM; not published |
| Backups | `ubuntu-mgmt`, Mac copy | Encrypted by restic; append-only server |
| Public documentation | GitHub | Sanitized: no real addresses, usernames or credentials |
