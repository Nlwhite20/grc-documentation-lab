# Security Response Library

Draft 2026-10-13. Reusable answers to common security questionnaire questions, written from the
confirmed [control inventory](control-inventory.md), [TSC mapping](tsc-mapping.md) and
[CAIQ self-assessment](caiq-self-assessment.md). Questions are phrased in my own words.

Each answer has a **limits of claim** line: what the answer does not prove. An answer must not be
reused without its limits.

Self-assessment by the lab owner; not independently verified.

## Governance

### RL-01. Do you have written information security policies?

**Answer:** No. Each lab has written scope and approval rules, and some procedures exist (password change, backup standard, restore test plan), but there is no policy set.

**Evidence:** [control inventory](control-inventory.md) C-22; [TSC mapping](tsc-mapping.md) gap G-1

**Limits of claim:** Rules and procedures are not policies; nothing is reviewed on a schedule.

### RL-02. Have you had an independent audit or SOC 2 report?

**Answer:** No. This repository is a self-assessment against the SOC 2 Trust Services Criteria and the CSA CAIQ.

**Evidence:** [TSC mapping](tsc-mapping.md); [CAIQ self-assessment](caiq-self-assessment.md)

**Limits of claim:** Self-assessed by the person who runs the controls; not tested by anyone independent.

### RL-03. Who is responsible for security?

**Answer:** One person, the lab owner, holds every role. Administrator, operator, reviewer and approver are the same person.

**Evidence:** [system description](system-description.md)

**Limits of claim:** There is no segregation of duties. This cannot be fixed by one person; compensating measures are written approvals and published records.

### RL-04. Do you maintain a risk register?

**Answer:** Yes. Every lab has a risk register with likelihood, impact, treatment and status. Risks stay open until evidence closes them.

**Evidence:** [vulnerability risk register](https://github.com/Nlwhite20/vulnerability-management-lab/blob/main/docs/risk-register.md); [backup risk register](https://github.com/Nlwhite20/backup-restore-lab/blob/main/docs/risk-register.md); [control inventory](control-inventory.md) C-20

**Limits of claim:** No owner is named per risk (exceptions name owners); one person holds every role; there is no organisation-wide register.

### RL-05. How do you handle risk exceptions?

**Answer:** Exceptions are recorded with an owner, affected asset, compensating controls and review triggers. Used in the vulnerability management lab, including an agent held at an older version so it stays compatible with the manager.

**Evidence:** [exceptions](https://github.com/Nlwhite20/vulnerability-management-lab/blob/main/docs/exceptions.md); [control inventory](control-inventory.md) C-12

**Limits of claim:** Residual risk ratings and review dates are still pending; no policy defines when an exception is allowed.

## Access control

### RL-06. Do you use multi-factor authentication?

**Answer:** No. Administration is over SSH and dashboards are reached through SSH tunnels with one owner account each.

**Evidence:** [NOC risk register](https://github.com/Nlwhite20/noc-monitoring-lab/blob/main/docs/risk-register.md) (R-08); [control inventory](control-inventory.md) C-23

**Limits of claim:** No MFA on any dashboard or system; accepted as a risk in the NOC lab.

### RL-07. Are administrative interfaces exposed to the network?

**Answer:** No, as last verified. The SIEM dashboard, API and indexer and the NOC dashboards are bound to loopback and reached through SSH tunnels. One drift was found, fixed and confirmed from another host.

**Evidence:** [Finding 001](https://github.com/Nlwhite20/wazuh-siem-lab/blob/main/docs/finding-001-dashboard-bind-drift.md); [exposure audit](https://github.com/Nlwhite20/network-security-lab/blob/main/docs/scan-and-exposure-audit.md); [NOC architecture](https://github.com/Nlwhite20/noc-monitoring-lab/blob/main/docs/architecture.md)

**Limits of claim:** Verified at points in time, not continuously. The Wazuh agent ports are open on the lab network by design.

### RL-08. Have default credentials been changed?

**Answer:** Partly. The Wazuh `admin` and `wazuh-wui` passwords were rotated using a written procedure.

**Evidence:** [password procedure](https://github.com/Nlwhite20/wazuh-siem-lab/blob/main/docs/password-change-procedure.md); [SIEM risk register](https://github.com/Nlwhite20/wazuh-siem-lab/blob/main/docs/risk-register.md) (R-03)

**Limits of claim:** The `kibanaserver` service account is still on its default password.

### RL-09. How are secrets handled?

**Answer:** Kept out of version control and off the command line. Secret files are git-ignored and root-only, passwords are typed at hidden prompts, and a manual scan for secrets and addresses runs before each commit.

**Evidence:** [backup lab rules](https://github.com/Nlwhite20/backup-restore-lab/blob/main/CLAUDE.md); [control inventory](control-inventory.md) C-04

**Limits of claim:** The scan is manual, not an automated git hook.

### RL-10. Do you apply least privilege?

**Answer:** Partly. Backup clients can add backups but cannot delete them; each has its own account. Secret files are readable by root only.

**Evidence:** [backup results](https://github.com/Nlwhite20/backup-restore-lab/blob/main/docs/results.md); [control inventory](control-inventory.md) C-15

**Limits of claim:** The owner has full admin rights everywhere, and they are permanent rather than time-limited.

## Data protection

### RL-11. Is data encrypted in transit?

**Answer:** Yes, for traffic between systems that was checked. Administration over SSH; backups over TLS with a pinned certificate; Wazuh dashboard, API and indexer use TLS.

**Evidence:** [backup build log](https://github.com/Nlwhite20/backup-restore-lab/blob/main/docs/build-log.md); [SIEM architecture](https://github.com/Nlwhite20/wazuh-siem-lab/blob/main/docs/architecture.md); [control inventory](control-inventory.md) C-18

**Limits of claim:** Wazuh agent channel encryption is the vendor default but was not verified. Metrics collection inside the NOC VM is plain HTTP and stays inside that VM.

### RL-12. Is data encrypted at rest?

**Answer:** Backups only. Backup repositories are encrypted by restic.

**Evidence:** [backup standard](https://github.com/Nlwhite20/backup-restore-lab/blob/main/docs/backup-standard.md)

**Limits of claim:** Disk encryption on the VMs and the Mac was not assessed.

### RL-13. Do you process personal data?

**Answer:** No personal data of anyone other than the owner. The lab holds configuration, logs, alerts, scan results and backups. Logs contain the owner's own account names.

**Evidence:** [system description](system-description.md)

**Limits of claim:** No customer, employer or third-party personal data; privacy questions were answered not applicable on that basis.

### RL-14. Do you have data retention and disposal rules?

**Answer:** No. Test data was removed after the backup lab, but no retention periods or disposal method are defined.

**Evidence:** [TSC mapping](tsc-mapping.md) gap G-5

**Limits of claim:** Log and backup retention are not set; backup pruning is not configured.

## Backup and continuity

### RL-15. Do you back up your systems?

**Answer:** Yes, for two systems. Daily encrypted restic backups of the endpoint and the SIEM configuration, with three copies: live, backup server and the Mac.

**Evidence:** [backup standard](https://github.com/Nlwhite20/backup-restore-lab/blob/main/docs/backup-standard.md); [backup results](https://github.com/Nlwhite20/backup-restore-lab/blob/main/docs/results.md); [control inventory](control-inventory.md) C-14

**Limits of claim:** `ubuntu-mgmt`, `noc-monitoring` and the SIEM's stored alert history are not backed up. All copies are on one Mac, so there is no off-site copy.

### RL-16. Are backups protected from deletion or ransomware?

**Answer:** Protected against a compromised client. The backup server runs append-only. A delete attempted from a client was refused with HTTP 403 in test R4.

**Evidence:** [backup results](https://github.com/Nlwhite20/backup-restore-lab/blob/main/docs/results.md); [backup risk register](https://github.com/Nlwhite20/backup-restore-lab/blob/main/docs/risk-register.md) (R-03, R-09)

**Limits of claim:** Does not protect against a compromised backup server. restic still exited 0 when the delete was refused, so automation that trusts exit codes would miss it.

### RL-17. Have you tested restoring from backup?

**Answer:** Yes, once. File, folder and point-in-time restores passed with hash verification. The folder restore took 0.73 s against a 30-minute recovery time objective. The first file test failed because of a script defect, which was fixed and retested.

**Evidence:** [backup results](https://github.com/Nlwhite20/backup-restore-lab/blob/main/docs/results.md); [control inventory](control-inventory.md) C-16

**Limits of claim:** One test round; monthly tests are not yet scheduled. The 24-hour recovery point objective has not been demonstrated over a full day.

### RL-18. Would you know if a backup failed?

**Answer:** It would be logged, not notified. An hourly check on the backup server flags any repository older than 26 hours.

**Evidence:** [backup results](https://github.com/Nlwhite20/backup-restore-lab/blob/main/docs/results.md) (R5); [backup risk register](https://github.com/Nlwhite20/backup-restore-lab/blob/main/docs/risk-register.md) (R-10)

**Limits of claim:** Nobody is notified; the warning sits in the server log.

### RL-19. Do you have a business continuity or disaster recovery plan?

**Answer:** No. Backup and restore procedures exist; there is no written continuity or recovery plan.

**Evidence:** [TSC mapping](tsc-mapping.md) gap G-4

**Limits of claim:** Recovery steps per system are not written down.

## Monitoring and incident response

### RL-20. Do you collect security logs centrally?

**Answer:** Yes, from one endpoint. Wazuh receives SSH, sudo, PAM, AppArmor and Suricata events from the monitored endpoint.

**Evidence:** [Investigation 001](https://github.com/Nlwhite20/wazuh-siem-lab/blob/main/docs/investigation-001-lab3-ids-alerts.md); [control inventory](control-inventory.md) C-08

**Limits of claim:** Three VMs are not enrolled. Agent queue overflow can drop events. No log retention rules; logs can be altered by the owner's admin account.

### RL-21. Do you run intrusion detection?

**Answer:** Yes, on one sensor. Suricata with ET Open rules; alerts reach Wazuh.

**Evidence:** [network-security build log](https://github.com/Nlwhite20/network-security-lab/blob/main/docs/build-log.md); [network-security risk register](https://github.com/Nlwhite20/network-security-lab/blob/main/docs/risk-register.md) (R-10)

**Limits of claim:** It sees only the sensor's own traffic. The default rules did not flag a full TCP connect scan as a port scan. Rules were downloaded at install with no update schedule evidenced.

### RL-22. Do you monitor availability?

**Answer:** Yes, in the NOC lab. Prometheus, Grafana and Uptime Kuma, with alerts routed to a private Discord channel.

**Evidence:** [INC-003](https://github.com/Nlwhite20/noc-monitoring-lab/blob/main/docs/incident-003-alerting-validation.md); [NOC architecture](https://github.com/Nlwhite20/noc-monitoring-lab/blob/main/docs/architecture.md)

**Limits of claim:** Monitors only the NOC VM itself; the Firing message was not confirmed; the NOC VM is usually powered off.

### RL-23. Do you have an incident response plan?

**Answer:** No. Incidents and tests are documented with timestamps, and dated corrections are published when an earlier record was wrong.

**Evidence:** [INC-003](https://github.com/Nlwhite20/noc-monitoring-lab/blob/main/docs/incident-003-alerting-validation.md); [control inventory](control-inventory.md) C-21

**Limits of claim:** Documentation is after the fact; there is no plan, contact list or defined response steps.

### RL-24. How do you triage alerts?

**Answer:** Case by case. One documented investigation correlated several fields before reaching a scoped conclusion.

**Evidence:** [Investigation 001](https://github.com/Nlwhite20/wazuh-siem-lab/blob/main/docs/investigation-001-lab3-ids-alerts.md); [control inventory](control-inventory.md) C-10

**Limits of claim:** One instance; no written triage procedure.

### RL-25. Are system clocks synchronised?

**Answer:** Yes, with known drift. chrony runs on the VMs.

**Evidence:** [NOC risk register](https://github.com/Nlwhite20/noc-monitoring-lab/blob/main/docs/risk-register.md) (R-13); [control inventory](control-inventory.md) C-19

**Limits of claim:** Clocks drifted after the host slept on several occasions and were corrected by hand; checks before timed tests are manual.

## Vulnerabilities and change

### RL-26. Do you scan for vulnerabilities?

**Answer:** Yes, on one endpoint. Wazuh vulnerability detection runs on the enrolled agent.

**Evidence:** [vulnerability-management-lab](https://github.com/Nlwhite20/vulnerability-management-lab); [control inventory](control-inventory.md) C-11

**Limits of claim:** Three VMs and the container images are not scanned.

### RL-27. How do you prioritise vulnerabilities?

**Answer:** With a written risk-based method. Priority depends on whether the code is running or reachable, its CVSS severity, and whether a fix is available. Unused vulnerable kernels were removed and the removal was verified by re-scan.

**Evidence:** [prioritisation method](https://github.com/Nlwhite20/vulnerability-management-lab/blob/main/docs/prioritization-method.md); [remediation results](https://github.com/Nlwhite20/vulnerability-management-lab/blob/main/docs/remediation-results.md)

**Limits of claim:** An own method using CVSS, not an industry framework as a whole; no remediation timelines.

### RL-28. How do you patch?

**Answer:** Under change control on the endpoint. Endpoint updates were logged, with the Wazuh agent deliberately held at the manager's version.

**Evidence:** [network-security build log](https://github.com/Nlwhite20/network-security-lab/blob/main/docs/build-log.md); [vulnerability risk register](https://github.com/Nlwhite20/vulnerability-management-lab/blob/main/docs/risk-register.md) (R-03); [control inventory](control-inventory.md) C-13

**Limits of claim:** The SIEM and NOC VMs have pending updates; no patch schedule.

### RL-29. How do you manage changes?

**Answer:** Logged, and normally approved in writing first. Changes are recorded in each lab's build log.

**Evidence:** [network-security build log](https://github.com/Nlwhite20/network-security-lab/blob/main/docs/build-log.md); [Finding 001](https://github.com/Nlwhite20/wazuh-siem-lab/blob/main/docs/finding-001-dashboard-bind-drift.md); [control inventory](control-inventory.md) C-05

**Limits of claim:** Two changes were later found unrecorded, and the Lab 5 clean-up had no separate recorded approval. One person requests, approves and makes every change.

### RL-30. Do you have penetration tests?

**Answer:** No. An exposure audit with nmap was run by the owner.

**Evidence:** [exposure audit](https://github.com/Nlwhite20/network-security-lab/blob/main/docs/scan-and-exposure-audit.md)

**Limits of claim:** Self-run; not independent.

## Third parties and other

### RL-31. How do you manage vendor risk?

**Answer:** By reviewing advisories for key software. Official release notes and advisories were reviewed for Wazuh and suricata-update, with applicability recorded.

**Evidence:** [exception evidence review](https://github.com/Nlwhite20/vulnerability-management-lab/blob/main/docs/exception-evidence-review.md); [control inventory](control-inventory.md) C-24

**Limits of claim:** One review; no schedule; providers such as GitHub and Discord are not reviewed. A Wazuh vendor review is planned in this lab.

### RL-32. Do you use AI tools?

**Answer:** Yes, for drafting and planning. Claude (Anthropic) drafts documents and commands. Claude reads lab repositories and writes drafts in the owner's lab folders through the Claude desktop app. Commands on the VMs, and every commit and push, are run by the owner, who reviews each document.

**Evidence:** [README](../README.md)

**Limits of claim:** The AI provider receives conversation content, which includes lab hostnames and addresses but never passwords. AI-drafted text is checked by the owner, not independently.

### RL-33. How is physical security handled?

**Answer:** Out of scope. The home and the Mac host are excluded from the system description.

**Evidence:** [system description](system-description.md)

**Limits of claim:** Not assessed.

### RL-34. Is the administrator's workstation hardened?

**Answer:** Not assessed. The Mac that runs the VMs and administers everything is out of scope.

**Evidence:** [system description](system-description.md); [CAIQ self-assessment](caiq-self-assessment.md) (UEM)

**Limits of claim:** Lock screen, disk encryption, firewall and anti-malware settings on the Mac were not checked.
