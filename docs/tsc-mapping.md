# SOC 2 Trust Services Criteria: Mapping and Gap Analysis

Draft 2026-10-13. Maps my control inventory ([control-inventory.md](control-inventory.md)) to the
2017 Trust Services Criteria (revised points of focus, 2022). Criteria are referenced **by ID
only**; the topic column is my own short summary, not the AICPA text (see
[sources-and-licensing.md](sources-and-licensing.md)). NIST SP 800-53 references are a selection
taken from the AICPA's published TSC-to-800-53 mapping.

Self-assessment by the lab owner; not an audit, not independently tested.

## Scope

- **Assessed:** Security (common criteria CC1 to CC9) and Availability (A1).
- **Not assessed:** Confidentiality (C1), Processing Integrity (PI1) and Privacy (P1 to P8).
  The lab holds no customer or personal data and processes no transactions for anyone else.

## Rating

| Rating | Meaning |
| --- | --- |
| Addressed | Supported by an Implemented control with evidence |
| Partial | Some support, with a stated gap |
| Gap | No control in place |
| Not applicable | The criterion does not fit a one-person lab (reason given) |
| Out of scope | Covers a component excluded in the [system description](system-description.md) |

## Mapping

| Criterion | Topic (my summary) | Controls | Rating | Gap | NIST 800-53 (selected) |
| --- | --- | --- | --- | --- | --- |
| CC1.1 | Commitment to integrity and ethical values | none | Gap | No written code of conduct or acceptable use statement | PS-6 |
| CC1.2 | Independent oversight by a governing body | none | Not applicable | No board or governing body; one owner. Recorded as a limitation, not a pass | none in the mapping |
| CC1.3 | Structure, reporting lines and authority | C-22 | Partial | Authority and approval rules written down, but one person holds every role (no segregation of duties) | PL-9, PM-2 |
| CC1.4 | Competence of the people running controls | none | Gap | No training plan or competence record inside the control set | PS-3, PM-13 |
| CC1.5 | Accountability for control responsibilities | C-20, C-22 | Partial | Owners named on exceptions, not on individual risks; owner and reviewer are the same person | PS-8 |
| CC2.1 | Relevant, quality information to support control | C-08, C-21 | Partial | Logs and records exist; only one endpoint feeds the SIEM | CM-13 |
| CC2.2 | Internal communication of objectives and responsibilities | C-22 | Partial | Rules written per lab; no security policy set | PL-4, AT-2 |
| CC2.3 | Communication with external parties | C-21 | Partial | Public, corrected documentation on GitHub; no channel for others to report issues | PM-15 |
| CC3.1 | Objectives clear enough to assess risk | C-22 | Partial | Scope and backup objectives (RPO/RTO) written; no overall security objectives | RA-2, PM-11 |
| CC3.2 | Identifying and analysing risk | C-20 | Addressed | Risk register in every lab | RA-3 |
| CC3.3 | Considering fraud and misuse risk | none | Gap | Not considered in any risk register | none in the mapping |
| CC3.4 | Assessing risk from significant change | C-05, C-20 | Partial | Risks added after changes, but no required step to reassess risk before a change | RA-3 |
| CC4.1 | Ongoing and separate evaluations of controls | C-06, C-16 | Partial | Point-in-time reviews and tests; nothing scheduled; no independent assessor | CA-2, CA-7 |
| CC4.2 | Reporting and fixing control deficiencies | C-20, C-21 | Partial | Deficiencies recorded and published; reported only to myself | CA-5 |
| CC5.1 | Choosing control activities that reduce risk | C-20 | Partial | Treatments recorded per risk; no overall control selection method | AC-1 |
| CC5.2 | General controls over technology | C-01 to C-19 | Partial | Technical controls exist; the policy documents that should govern them do not | AC-1, CM-1, IR-1 |
| CC5.3 | Policies and procedures put into practice | C-03, C-16 | Partial | Some procedures (password change, backup standard, restore test plan); no policies | PL-2 |
| CC6.1 | Logical access protections | C-01, C-03, C-04, C-18, C-23 | Partial | `kibanaserver` default password; no MFA | AC-3, IA-2, IA-5 |
| CC6.2 | Registering and removing users | C-23 | Partial | Single owner account per system and one backup account per client; no written provisioning or removal process | AC-2 |
| CC6.3 | Role-based, least-privilege access | C-15, C-23 | Partial | Backup clients cannot delete; root-only secret files; no separation of admin duties | AC-6 |
| CC6.4 | Physical access to facilities and hardware | none | Out of scope | The Mac host and home are excluded from the system | PE-2, PE-3 |
| CC6.5 | Secure disposal of data and assets | none | Gap | Test data removed after Lab 5, but no disposal procedure | MP-6 |
| CC6.6 | Protection at the system boundary | C-01, C-02, C-09 | Partial | No host firewall observed on the sensor; IDS sees only its own traffic | SC-7 |
| CC6.7 | Protecting data in transit and movement | C-18 | Partial | Encrypted in transit; no control over copying data to other media | SC-8 |
| CC6.8 | Preventing and detecting malicious software | C-08, C-09 | Partial | No anti-malware or file-integrity monitoring evidenced | SI-3, SI-7 |
| CC7.1 | Detecting configuration changes and vulnerabilities | C-06, C-11 | Partial | Vulnerability scanning on one agent; baseline checks not automated | RA-5, CM-6 |
| CC7.2 | Monitoring for anomalies and attacks | C-07, C-08, C-09, C-17 | Partial | Backup failures not notified; Firing alert not confirmed | SI-4, AU-6 |
| CC7.3 | Evaluating security events | C-10 | Partial | One documented investigation; no triage procedure | AU-6, SI-5 |
| CC7.4 | Responding to security incidents | C-21 | Partial | Incidents documented after the fact; no incident response plan | IR-4, IR-8 |
| CC7.5 | Recovering from incidents | C-14, C-16, C-21 | Partial | Restore tested once; no recovery plan per system | IR-4 |
| CC8.1 | Managing changes | C-05, C-13, C-22 | Partial | Two changes found unrecorded; one person requests, approves and makes each change | CM-3, CM-4 |
| CC9.1 | Reducing business disruption risk | C-14, C-15, C-16 | Partial | No contingency plan; no off-site copy | CP-2, CP-10 |
| CC9.2 | Managing vendor and partner risk | C-24 | Partial | One vendor review (Wazuh, 2026-10-13), which led to an upgrade; no periodic review of providers | SA-9, SR-6 |
| A1.1 | Capacity monitoring and planning | C-07 | Partial | CPU and disk monitored on the NOC host; no capacity planning | SC-5 |
| A1.2 | Backup, recovery infrastructure and environmental protection | C-14, C-15, C-17 | Partial | Two VMs not backed up; no off-site copy; environmental protection out of scope | CP-9 |
| A1.3 | Testing recovery | C-16 | Partial | One test round; monthly tests not scheduled | CP-4 |

**Summary (36 criteria):** 1 Addressed, 29 Partial, 4 Gap, 1 Not applicable, 1 Out of scope.

## Main gaps

Ordered by how many criteria each one affects. Fixes are proposals; none is approved or started.

| # | Gap | Criteria affected | Proposed fix (not started) |
| --- | --- | --- | --- |
| G-1 | No security policy set | CC1.1, CC2.2, CC5.2, CC5.3 | Short policies: acceptable use, access, change, backup, incident response |
| G-2 | No segregation of duties | CC1.3, CC1.5, CC6.3, CC8.1 | Cannot be fixed by one person. Compensating: written approvals before changes, published records, periodic outside review |
| G-3 | Monitoring coverage | CC2.1, CC6.6, CC7.1, CC7.2 | Enrol more agents; confirm sensor firewall; notify on backup failure |
| G-4 | No incident response or contingency plan | CC7.4, CC7.5, CC9.1 | Written plan with roles, contacts and recovery steps per system |
| G-5 | Fraud, competence and disposal not considered | CC1.4, CC3.3, CC6.5 | Add to the risk register; write a disposal step |
| G-6 | Access weaknesses | CC6.1, CC6.2 | Rotate `kibanaserver`; consider MFA on dashboards; write an account process |
| G-7 | Backup coverage | A1.2, CC9.1 | Back up `ubuntu-mgmt` and `noc-monitoring`; add an off-site copy |
