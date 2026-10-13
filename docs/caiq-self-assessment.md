# CSA CAIQ v4.0.3 Self-Assessment

2026-10-13. All 261 answers confirmed by the lab owner. Answers to the Cloud Security Alliance Consensus Assessments Initiative
Questionnaire v4.0.3, for the lab described in [system-description.md](system-description.md).
Questions are referenced **by ID only**; the questionnaire itself is not reproduced, modified or
redistributed (see [sources-and-licensing.md](sources-and-licensing.md)). Notes are my own words.

Self-assessment by the lab owner, answering as the provider (CSP); not a CSA STAR submission and
not independently verified.

## Answer rules

| Answer | Used when |
| --- | --- |
| Yes | An Implemented control with evidence fully covers the question |
| No | Not in place, **or only partly in place** (the note says which part exists). CAIQ has no "partial" answer, so partial is answered No |
| NA | Does not apply to a one-person lab with no customers and no personal data (reason given) |

Questions asking whether a policy exists, or is reviewed at least annually, are answered No: there
is no policy set (gap G-1 in [tsc-mapping.md](tsc-mapping.md)).

Ownership: **CSP-owned** (the lab owner) unless stated. Control IDs refer to
[control-inventory.md](control-inventory.md).

## Status

| Round | Domains | Questions | Owner confirmation |
| --- | --- | --- | --- |
| 1 | A&A, AIS, BCR, CCC | 48 | Confirmed by owner 2026-10-13 |
| 2 | CEK, DCS | 46 | Confirmed by owner 2026-10-13 |
| 3 | DSP, GRC, HRS | 53 | Confirmed by owner 2026-10-13 |
| 4 | IAM, IPY, IVS, LOG | 61 | Confirmed by owner 2026-10-13 |
| 5 | SEF, STA, TVM, UEM | 53 | Confirmed by owner 2026-10-13 |

## Overall result

261 questions: **2 Yes** (BCR-08.3, IPY-03.1), **215 No**, **44 NA**. Most No answers
reflect the missing policy set and processes (gaps G-1 to G-7 in [tsc-mapping.md](tsc-mapping.md)),
not missing technical controls.

## Round 1: A&A, AIS, BCR, CCC

| ID | Answer | Owner | Note | Controls |
| --- | --- | --- | --- | --- |
| A&A-01.1 | No | CSP-owned | No audit and assurance policy | none |
| A&A-01.2 | No | CSP-owned | No policy to review | none |
| A&A-02.1 | No | CSP-owned | No independent assessment; this document is a self-assessment | none |
| A&A-03.1 | No | CSP-owned | No independent assessment or audit plan | none |
| A&A-04.1 | No | CSP-owned | Partly: the TSC mapping checks controls against one framework; no verification against legal or contractual requirements | C-20 |
| A&A-05.1 | No | CSP-owned | Partly: this lab records scope, control assessment and gaps; no defined audit management process | C-20 |
| A&A-06.1 | No | CSP-owned | Partly: gaps have proposed fixes; none approved as a corrective action plan | C-20 |
| A&A-06.2 | No | CSP-owned | Partly: findings and status published on GitHub; reported to no one but the owner | C-21 |
| AIS-01.1 | No | CSP-owned | No application security policy | none |
| AIS-01.2 | No | CSP-owned | No policy to review | none |
| AIS-02.1 | No | CSP-owned | Partly: hardening decisions documented for the SIEM; no baseline for other applications | C-01, C-03 |
| AIS-03.1 | No | CSP-owned | Partly: recovery objectives defined for backups only; no wider metrics | C-16 |
| AIS-04.1 | No | CSP-owned | Small operational scripts written (backup, restore test) with no defined development lifecycle | none |
| AIS-05.1 | No | CSP-owned | Partly: upgrades reviewed case by case against release notes; no written acceptance criteria | C-24 |
| AIS-05.2 | No | CSP-owned | Partly: restore and canary tests are scripted but run by hand | C-16 |
| AIS-06.1 | No | CSP-owned | Partly: SIEM deployed from a documented compose file; no standard deployment method | C-05 |
| AIS-06.2 | No | CSP-owned | Deployments are manual | none |
| AIS-07.1 | No | CSP-owned | Partly: a written prioritisation, remediation and exception method (vulnerability-management-lab) is applied to OS packages and the Wazuh agent (exception R-03 in that lab); it is not set out as an application security process | C-12, C-20 |
| AIS-07.2 | No | CSP-owned | Remediation is manual | none |
| BCR-01.1 | No | CSP-owned | No business continuity policy | none |
| BCR-01.2 | No | CSP-owned | No policy to review | none |
| BCR-02.1 | No | CSP-owned | Partly: recovery objectives set for two backed-up systems; no impact analysis | C-14 |
| BCR-03.1 | No | CSP-owned | Partly: backup strategy in place; no defined risk appetite | C-14, C-15 |
| BCR-04.1 | No | CSP-owned | No business continuity plan (gap G-4) | none |
| BCR-05.1 | No | CSP-owned | Partly: backup standard and restore test plan written; no continuity plan to support | C-14, C-16 |
| BCR-05.2 | No | CSP-owned | Partly: backup documents published on GitHub; there is no continuity documentation set | C-14 |
| BCR-05.3 | No | CSP-owned | No periodic review scheduled | none |
| BCR-06.1 | No | CSP-owned | Partly: restores tested once; no plan to exercise | C-16 |
| BCR-07.1 | No | CSP-owned | No stakeholder communication procedure | none |
| BCR-08.1 | No | CSP-owned | Partly: daily encrypted backups of two systems; `ubuntu-mgmt`, `noc-monitoring` and SIEM alert history are not backed up | C-14 |
| BCR-08.2 | No | CSP-owned | Partly: encrypted, append-only and sent over TLS; availability limited because every copy is on one Mac | C-14, C-15, C-18 |
| BCR-08.3 | Yes | CSP-owned | File, folder and point-in-time restores passed with hash verification ([backup results](https://github.com/Nlwhite20/backup-restore-lab/blob/main/docs/results.md)). Limit: tested once, not yet on a schedule | C-16 |
| BCR-09.1 | No | CSP-owned | No disaster response plan | none |
| BCR-09.2 | No | CSP-owned | No plan to update | none |
| BCR-10.1 | No | CSP-owned | No plan to exercise | none |
| BCR-10.2 | NA | CSP-owned | Home lab; emergency authorities have no role in its recovery | none |
| BCR-11.1 | No | CSP-owned | All equipment on one Mac; no redundant equipment elsewhere | none |
| CCC-01.1 | No | CSP-owned | No change management policy | none |
| CCC-01.2 | No | CSP-owned | No policy to review | none |
| CCC-02.1 | No | CSP-owned | Partly: changes approved and logged; no testing or release standard, and two changes were found unrecorded | C-05, C-22 |
| CCC-03.1 | No | CSP-owned | Partly: risks recorded, but not required before a change | C-20 |
| CCC-04.1 | No | CSP-owned | Partly: only the owner has admin access; nothing technically stops unrecorded changes | C-23 |
| CCC-05.1 | NA | CSP-owned | No customers and no service level agreements | none |
| CCC-06.1 | No | CSP-owned | Partly: documented baselines for some systems; not for all | C-06 |
| CCC-07.1 | No | CSP-owned | Partly: drift found by manual review (Finding 001); no automatic detection or notification | C-06 |
| CCC-08.1 | No | CSP-owned | Partly: an exception process exists for vulnerabilities; not for changes or emergencies | C-12, C-20 |
| CCC-08.2 | No | CSP-owned | No policy exception process (GRC-04) to align with | none |
| CCC-09.1 | No | CSP-owned | Partly: backups can restore configuration; no defined rollback procedure | C-14 |

**Round 1 (48):** 1 Yes, 45 No, 2 NA.

## Round 2: CEK, DCS

The physical environment (the home and the Mac host) is out of scope in the
[system description](system-description.md). Physical and data-centre questions are answered NA
on that basis, with the reason given; policy questions are still answered No.

| ID | Answer | Owner | Note | Controls |
| --- | --- | --- | --- | --- |
| CEK-01.1 | No | CSP-owned | No cryptography or key management policy | none |
| CEK-01.2 | No | CSP-owned | No policy to review | none |
| CEK-02.1 | No | CSP-owned | One person handles all keys; roles not defined in writing | none |
| CEK-03.1 | No | CSP-owned | Partly: backups encrypted at rest by restic; traffic protected by TLS and SSH. Certification of the libraries not verified; at-rest encryption of VM disks not assessed | C-14, C-18 |
| CEK-04.1 | No | CSP-owned | Partly: software default algorithms used (restic encryption, an EC TLS certificate); no data classification to base choices on | C-14, C-18 |
| CEK-05.1 | No | CSP-owned | Partly: the backup server certificate was created under approval and logged; no procedure for cryptographic changes | C-05, C-22 |
| CEK-06.1 | No | CSP-owned | No analysis of downstream effects for cryptographic changes | none |
| CEK-07.1 | No | CSP-owned | No cryptographic risk programme | none |
| CEK-08.1 | NA | CSP-owned | No customers, so no customer-managed keys | none |
| CEK-09.1 | No | CSP-owned | Key management not audited | none |
| CEK-09.2 | No | CSP-owned | Key management not audited | none |
| CEK-10.1 | No | CSP-owned | Partly: keys created with standard tools (OpenSSL, restic); no written specification of strength or random number generation | C-18 |
| CEK-11.1 | No | CSP-owned | Partly: each key has one purpose and secret files are root-only; no key management process | C-04, C-18 |
| CEK-12.1 | No | CSP-owned | No rotation period; the backup server certificate is valid to 2029 | none |
| CEK-13.1 | No | CSP-owned | No revocation process | none |
| CEK-14.1 | No | CSP-owned | No key destruction process | none |
| CEK-15.1 | No | CSP-owned | No process for keys created but not yet authorised | none |
| CEK-16.1 | No | CSP-owned | No process for key state changes | none |
| CEK-17.1 | No | CSP-owned | No process to deactivate expired keys | none |
| CEK-18.1 | No | CSP-owned | No archived key repository | none |
| CEK-19.1 | No | CSP-owned | No process for compromised keys | none |
| CEK-20.1 | No | CSP-owned | Partly: backup repository passwords are kept in root-only files and in the owner's password manager (backup standard); the trade-off between losing keys and exposing them is not assessed | C-14 |
| CEK-21.1 | No | CSP-owned | No tracking of cryptographic material | none |
| DCS-01.1 | No | CSP-owned | No equipment disposal policy | none |
| DCS-01.2 | No | CSP-owned | No data destruction procedure (gap G-5) | none |
| DCS-01.3 | No | CSP-owned | No policy to review | none |
| DCS-02.1 | No | CSP-owned | No policy for moving hardware, software or data off site | none |
| DCS-02.2 | No | CSP-owned | No authorisation requirement defined for transfers | none |
| DCS-02.3 | No | CSP-owned | No policy to review | none |
| DCS-03.1 | No | CSP-owned | No working environment policy | none |
| DCS-03.2 | No | CSP-owned | No policy to review | none |
| DCS-04.1 | No | CSP-owned | No physical media transport policy | none |
| DCS-04.2 | No | CSP-owned | No policy to review | none |
| DCS-05.1 | No | CSP-owned | Partly: data types listed in the system description; not classified by risk | none |
| DCS-06.1 | No | CSP-owned | Partly: components listed in the system description; no tracked asset inventory | none |
| DCS-07.1 | NA | CSP-owned | Physical environment out of scope | none |
| DCS-07.2 | NA | CSP-owned | Physical environment out of scope | none |
| DCS-08.1 | No | CSP-owned | Partly: the Wazuh agent and each backup client authenticate with their own key or account; no equipment identity check | C-08, C-15 |
| DCS-09.1 | NA | CSP-owned | Physical environment out of scope | none |
| DCS-09.2 | NA | CSP-owned | Physical environment out of scope | none |
| DCS-10.1 | NA | CSP-owned | No data centre | none |
| DCS-11.1 | NA | CSP-owned | No data centre or staff | none |
| DCS-12.1 | NA | CSP-owned | Physical environment out of scope | none |
| DCS-13.1 | NA | CSP-owned | No data centre | none |
| DCS-14.1 | NA | CSP-owned | Physical environment out of scope | none |
| DCS-15.1 | NA | CSP-owned | Physical environment out of scope | none |

**Round 2 (46):** 0 Yes, 35 No, 11 NA.

## Round 3: DSP, GRC, HRS

The lab holds no personal data about anyone other than the owner (for example, the owner's own
account names in logs) and has no employees or contractors. Questions that depend on either are
answered NA with the reason given.

| ID | Answer | Owner | Note | Controls |
| --- | --- | --- | --- | --- |
| DSP-01.1 | No | CSP-owned | No data classification or handling policy | none |
| DSP-01.2 | No | CSP-owned | No policy to review | none |
| DSP-02.1 | No | CSP-owned | No secure disposal method (gap G-5) | none |
| DSP-03.1 | No | CSP-owned | Partly: data types and locations listed in the system description; not maintained as an inventory | none |
| DSP-04.1 | No | CSP-owned | Data not classified by sensitivity | none |
| DSP-05.1 | No | CSP-owned | Partly: architecture documents show SIEM and backup data paths; no complete data flow document | C-08, C-14 |
| DSP-05.2 | No | CSP-owned | No scheduled review | none |
| DSP-06.1 | No | CSP-owned | Partly: the owner holds every role; ownership not recorded per data set | none |
| DSP-06.2 | No | CSP-owned | Nothing to review | none |
| DSP-07.1 | No | CSP-owned | Partly: security decisions recorded (loopback-only admin interfaces, append-only backups, secrets kept out of Git); no secure design standard | C-01, C-04, C-15 |
| DSP-08.1 | NA | CSP-owned | No personal data of others processed | none |
| DSP-08.2 | NA | CSP-owned | No personal data of others processed | none |
| DSP-09.1 | NA | CSP-owned | No personal data of others processed | none |
| DSP-10.1 | No | CSP-owned | Partly: sensitive data (secrets, backups) sent only over TLS or SSH; no defined transfer process | C-18 |
| DSP-11.1 | NA | CSP-owned | No data subjects other than the owner | none |
| DSP-12.1 | NA | CSP-owned | No personal data of others processed | none |
| DSP-13.1 | NA | CSP-owned | No personal data passed to sub-processors | none |
| DSP-14.1 | NA | CSP-owned | No data owners other than the lab owner | none |
| DSP-15.1 | NA | CSP-owned | No separate production and non-production environments | none |
| DSP-16.1 | No | CSP-owned | No retention or deletion rules for logs or backups | none |
| DSP-17.1 | No | CSP-owned | Partly: secrets root-only and kept out of Git; backups encrypted; no lifecycle process | C-04, C-14 |
| DSP-18.1 | NA | CSP-owned | No customers and no personal data of others | none |
| DSP-18.2 | NA | CSP-owned | No customers to notify | none |
| DSP-19.1 | No | CSP-owned | Partly: the system description states where data is kept and backed up; no defined procedure | none |
| GRC-01.1 | No | CSP-owned | No information governance policy | none |
| GRC-01.2 | No | CSP-owned | No policy to review | none |
| GRC-02.1 | No | CSP-owned | Partly: risk registers record identification, rating, owner, treatment and acceptance; no formal risk management programme or policy | C-20 |
| GRC-03.1 | No | CSP-owned | No policies to review | none |
| GRC-04.1 | No | CSP-owned | Partly: risk exceptions have owners and review triggers; there are no policies for an exception to deviate from | C-12, C-20 |
| GRC-05.1 | No | CSP-owned | Partly: controls exist across several areas; not organised as a security programme | none |
| GRC-06.1 | No | CSP-owned | Partly: the system description states that one person holds every role; governance responsibilities not set out | C-22 |
| GRC-07.1 | No | CSP-owned | Partly: licence terms for the reference documents recorded; no register of legal or regulatory requirements | none |
| GRC-08.1 | No | CSP-owned | No documented contact with special interest groups; vendor advisories are read, which is not the same | C-24 |
| HRS-01.1 | NA | CSP-owned | No employees or contractors | none |
| HRS-01.2 | NA | CSP-owned | No employees or contractors | none |
| HRS-01.3 | NA | CSP-owned | No employees or contractors | none |
| HRS-02.1 | No | CSP-owned | No acceptable use policy (proposed under gap G-1) | none |
| HRS-02.2 | No | CSP-owned | No policy to review | none |
| HRS-03.1 | No | CSP-owned | No clear workspace policy | none |
| HRS-03.2 | No | CSP-owned | No policy to review | none |
| HRS-04.1 | No | CSP-owned | No remote working policy | none |
| HRS-04.2 | No | CSP-owned | No policy to review | none |
| HRS-05.1 | NA | CSP-owned | No employees | none |
| HRS-06.1 | NA | CSP-owned | No employees | none |
| HRS-07.1 | NA | CSP-owned | No employees | none |
| HRS-08.1 | NA | CSP-owned | No employees | none |
| HRS-09.1 | No | CSP-owned | Partly: the system description states the owner's roles; responsibilities not set out per asset | C-22 |
| HRS-10.1 | NA | CSP-owned | No employees or contractors to sign agreements | none |
| HRS-11.1 | No | CSP-owned | No security awareness programme (gap G-5) | none |
| HRS-11.2 | No | CSP-owned | No programme to update | none |
| HRS-12.1 | No | CSP-owned | The owner holds security certifications, but they are not part of a training programme | none |
| HRS-12.2 | No | CSP-owned | No programme of updates | none |
| HRS-13.1 | No | CSP-owned | Partly: rules written per lab; no policies or compliance obligations communicated | C-22 |

**Round 3 (53):** 0 Yes, 35 No, 18 NA.

## Round 4: IAM, IPY, IVS, LOG

"Communications between environments" (IVS-03) is read as traffic between the lab's systems. The
lab is one non-production environment with no tenants, so questions about separating production
from non-production, or tenants from each other, are answered NA.

| ID | Answer | Owner | Note | Controls |
| --- | --- | --- | --- | --- |
| IAM-01.1 | No | CSP-owned | No identity and access management policy | none |
| IAM-01.2 | No | CSP-owned | No policy to review | none |
| IAM-02.1 | No | CSP-owned | Partly: a password change procedure exists for the SIEM; no password policy | C-03 |
| IAM-02.2 | No | CSP-owned | No policy to review | none |
| IAM-03.1 | No | CSP-owned | Partly: one owner account per system and one backup account per client; access levels not recorded or reviewed | C-23 |
| IAM-04.1 | No | CSP-owned | One person holds every role (gap G-2) | none |
| IAM-05.1 | No | CSP-owned | Partly: backup clients can add but not delete; secret files root-only; the owner has full admin rights everywhere | C-15, C-04 |
| IAM-06.1 | No | CSP-owned | No provisioning process | none |
| IAM-07.1 | No | CSP-owned | No de-provisioning process | none |
| IAM-08.1 | No | CSP-owned | No access reviews | none |
| IAM-09.1 | No | CSP-owned | One person holds every privileged role | none |
| IAM-10.1 | No | CSP-owned | Admin rights are standing, not time-limited | none |
| IAM-10.2 | No | CSP-owned | No segregated privileged roles to protect | none |
| IAM-11.1 | NA | CSP-owned | No customers | none |
| IAM-12.1 | No | CSP-owned | The owner's admin rights can alter logs; logging is not read-only | none |
| IAM-12.2 | No | CSP-owned | No read-only logging to control | none |
| IAM-13.1 | No | CSP-owned | Partly: each system has a named owner account and one person uses it; no defined process | C-23 |
| IAM-14.1 | No | CSP-owned | No multi-factor authentication | C-23 |
| IAM-14.2 | No | CSP-owned | Partly: certificates identify the SIEM components and the backup server; not used for every system identity | C-18 |
| IAM-15.1 | No | CSP-owned | Partly: passwords entered at hidden prompts, never on a command line, stored root-only or in a password manager; one service password still on its default; no defined process | C-03, C-04 |
| IAM-16.1 | No | CSP-owned | No process to verify access is authorised | none |
| IPY-01.1 | No | CSP-owned | No policy | none |
| IPY-01.2 | No | CSP-owned | No policy | none |
| IPY-01.3 | No | CSP-owned | No policy | none |
| IPY-01.4 | No | CSP-owned | No policy | none |
| IPY-01.5 | No | CSP-owned | No policy to review | none |
| IPY-02.1 | NA | CSP-owned | No customers | none |
| IPY-03.1 | Yes | CSP-owned | Administration over SSH; backups over TLS with a pinned certificate ([backup build log](https://github.com/Nlwhite20/backup-restore-lab/blob/main/docs/build-log.md), [SIEM architecture](https://github.com/Nlwhite20/wazuh-siem-lab/blob/main/docs/architecture.md)). Limits: metrics collection inside the NOC VM is plain HTTP; the method used for the one-off copy to the Mac was not recorded | C-18 |
| IPY-04.1 | NA | CSP-owned | No customers or contracts | none |
| IVS-01.1 | No | CSP-owned | No infrastructure security policy | none |
| IVS-01.2 | No | CSP-owned | No policy to review | none |
| IVS-02.1 | No | CSP-owned | Partly: CPU and disk monitored on the NOC host; no capacity planning | C-07 |
| IVS-03.1 | No | CSP-owned | Partly: the IDS sees only the sensor's own traffic | C-09 |
| IVS-03.2 | No | CSP-owned | Partly: SSH and TLS evidenced ([backup build log](https://github.com/Nlwhite20/backup-restore-lab/blob/main/docs/build-log.md), [SIEM architecture](https://github.com/Nlwhite20/wazuh-siem-lab/blob/main/docs/architecture.md)); Wazuh agent channel encryption is the vendor default but not verified in the lab | C-18 |
| IVS-03.3 | No | CSP-owned | Partly: firewalls on the SIEM and backup server; backup port open to two authenticated clients only; no firewall observed on the sensor | C-02 |
| IVS-03.4 | No | CSP-owned | Reviewed once (exposure audit); no annual review scheduled | C-06 |
| IVS-03.5 | No | CSP-owned | Partly: allowed ports documented for the SIEM, backup server and NOC host; not for every host | C-01, C-02 |
| IVS-04.1 | No | CSP-owned | Partly: hardening recorded for some systems; no baseline per host; hypervisor host out of scope | C-06 |
| IVS-05.1 | NA | CSP-owned | The whole lab is one non-production environment | none |
| IVS-06.1 | NA | CSP-owned | No tenants | none |
| IVS-07.1 | NA | CSP-owned | Nothing migrated to cloud environments | none |
| IVS-08.1 | No | CSP-owned | Partly: high risks identified in risk registers; environments not rated by risk | C-20 |
| IVS-09.1 | No | CSP-owned | Partly: firewall, IDS and SIEM in layers; no response procedure for network attacks | C-02, C-08, C-09 |
| LOG-01.1 | No | CSP-owned | No logging and monitoring policy | none |
| LOG-01.2 | No | CSP-owned | No policy to review | none |
| LOG-02.1 | No | CSP-owned | No log retention rules; SIEM alert history is not backed up | none |
| LOG-03.1 | No | CSP-owned | Partly: SSH, sudo, PAM, AppArmor and IDS events collected from one endpoint; three VMs not enrolled | C-08 |
| LOG-03.2 | No | CSP-owned | Partly: security alerts appear in the SIEM dashboard; no notification of security alerts evidenced | C-08 |
| LOG-04.1 | No | CSP-owned | Partly: the SIEM is reachable only by the owner through an SSH tunnel; no record of log access kept | C-01 |
| LOG-05.1 | No | CSP-owned | Partly: SIEM rules flag unusual activity on one endpoint | C-08, C-10 |
| LOG-05.2 | No | CSP-owned | Partly: one documented investigation; no triage procedure | C-10 |
| LOG-06.1 | No | CSP-owned | Partly: chrony on the VMs; clocks drifted after the host slept and were corrected by hand | C-19 |
| LOG-07.1 | No | CSP-owned | No written logging requirements | none |
| LOG-07.2 | No | CSP-owned | No scope to review | none |
| LOG-08.1 | No | CSP-owned | Partly: security records collected centrally for one endpoint only | C-08 |
| LOG-09.1 | No | CSP-owned | Logs can be changed or deleted by the owner's admin account; not protected | none |
| LOG-10.1 | No | CSP-owned | No reporting on cryptographic operations | none |
| LOG-11.1 | No | CSP-owned | Key events not logged or monitored | none |
| LOG-12.1 | NA | CSP-owned | Physical environment out of scope | none |
| LOG-13.1 | No | CSP-owned | Partly: target-down alerts in the NOC and an hourly backup freshness check; agent queue overflow can drop events unnoticed | C-07, C-17 |
| LOG-13.2 | No | CSP-owned | Partly: availability alerts go to Discord (Firing message not confirmed); backup failures not notified | C-07, C-17 |

**Round 4 (61):** 1 Yes, 53 No, 7 NA.

## Round 5: SEF, STA, TVM, UEM

Endpoint (UEM) questions cover the operator's Mac as well as the VMs. The Mac's own hardening is
out of scope in the system description, but unlike data-centre questions these controls clearly
apply to a workstation that administers everything, so they are answered No ("not assessed"),
not NA.

| ID | Answer | Owner | Note | Controls |
| --- | --- | --- | --- | --- |
| SEF-01.1 | No | CSP-owned | No incident management or forensics policy | none |
| SEF-01.2 | No | CSP-owned | No policy to review | none |
| SEF-02.1 | No | CSP-owned | No incident handling policy | none |
| SEF-02.2 | No | CSP-owned | No policy to review | none |
| SEF-03.1 | No | CSP-owned | No incident response plan (gap G-4) | none |
| SEF-04.1 | No | CSP-owned | No plan to test | none |
| SEF-05.1 | No | CSP-owned | No incident metrics | none |
| SEF-06.1 | No | CSP-owned | Partly: one documented investigation; no triage procedure | C-10 |
| SEF-07.1 | No | CSP-owned | No breach notification process | none |
| SEF-07.2 | NA | CSP-owned | No customers, service agreements or legal reporting duties; no breach identified | none |
| SEF-08.1 | No | CSP-owned | No authority contacts kept | none |
| STA-01.1 | No | CSP-owned | No shared responsibility policy | none |
| STA-01.2 | No | CSP-owned | No policy to review | none |
| STA-02.1 | No | CSP-owned | Partly: third parties and their use listed in the system description; responsibilities not split between the owner and each provider | none |
| STA-03.1 | NA | CSP-owned | No customers | none |
| STA-04.1 | No | CSP-owned | Partly: this questionnaire records an owner per question; third-party responsibilities not analysed | none |
| STA-05.1 | No | CSP-owned | Shared responsibility documents of GitHub, Discord and other providers not reviewed | none |
| STA-06.1 | No | CSP-owned | Partly: the owner's responsibilities are assessed once in this self-assessment; many are not implemented | none |
| STA-07.1 | No | CSP-owned | Partly: third parties listed in the system description; not maintained as an inventory | none |
| STA-08.1 | No | CSP-owned | Partly: vendor advisories reviewed for Wazuh and suricata-update; no periodic review of all providers | C-24 |
| STA-09.1 | NA | CSP-owned | No customers or service agreements | none |
| STA-10.1 | NA | CSP-owned | No customer agreements | none |
| STA-11.1 | No | CSP-owned | No annual internal assessment process; this is the first assessment | none |
| STA-12.1 | No | CSP-owned | Providers' standard terms accepted; no requirements set | none |
| STA-13.1 | No | CSP-owned | Providers' governance not reviewed | none |
| STA-14.1 | No | CSP-owned | Partly: a Wazuh vendor review is planned in this lab; no periodic assessment process | C-24 |
| TVM-01.1 | No | CSP-owned | Partly: a written prioritisation method exists; no vulnerability management policy | C-12 |
| TVM-01.2 | No | CSP-owned | No policy to review | none |
| TVM-02.1 | No | CSP-owned | No malware protection policy | none |
| TVM-02.2 | No | CSP-owned | No policy to review | none |
| TVM-03.1 | No | CSP-owned | Partly: remediation and exception steps defined; no schedule or emergency route | C-12 |
| TVM-04.1 | No | CSP-owned | Partly: IDS rules downloaded at install; no update schedule evidenced. The SIEM's vulnerability feed is updated by the vendor | C-09, C-11 |
| TVM-05.1 | No | CSP-owned | Partly: SIEM vulnerability detection covers packages on one agent; container images and other hosts not covered | C-11 |
| TVM-06.1 | No | CSP-owned | No independent penetration testing; the exposure audit was self-run | none |
| TVM-07.1 | No | CSP-owned | Partly: vulnerability detection runs on one agent; three VMs not covered | C-11 |
| TVM-08.1 | No | CSP-owned | Partly: own risk-based method using CVSS severity, whether code is running or reachable, and fix availability; not an industry-recognised framework as a whole | C-12 |
| TVM-09.1 | No | CSP-owned | Partly: findings and remediation tracked and published; no stakeholder notification beyond the owner | C-12, C-21 |
| TVM-10.1 | No | CSP-owned | Partly: finding counts recorded at baseline and re-scan; not at defined intervals | C-12 |
| UEM-01.1 | No | CSP-owned | No endpoint policy | none |
| UEM-01.2 | No | CSP-owned | No policy to review | none |
| UEM-02.1 | No | CSP-owned | No approved list of applications or sources | none |
| UEM-03.1 | No | CSP-owned | Partly: ARM64 compatibility of container images checked for the NOC host; no general process | none |
| UEM-04.1 | No | CSP-owned | Partly: the Mac and VMs are listed in the system description; not maintained as an inventory | none |
| UEM-05.1 | No | CSP-owned | No endpoint enforcement | none |
| UEM-06.1 | No | CSP-owned | The Mac is out of scope; lock screen setting not assessed | none |
| UEM-07.1 | No | CSP-owned | Partly: endpoint VM patching logged under change control; the Mac not covered | C-13 |
| UEM-08.1 | No | CSP-owned | Disk encryption on the Mac and VMs not assessed | none |
| UEM-09.1 | No | CSP-owned | No anti-malware evidenced on the VMs; the Mac's built-in protection not assessed | none |
| UEM-10.1 | No | CSP-owned | Partly: firewalls on two VMs, none observed on the sensor; the Mac not assessed | C-02 |
| UEM-11.1 | No | CSP-owned | No data loss prevention | none |
| UEM-12.1 | NA | CSP-owned | No managed mobile devices | none |
| UEM-13.1 | No | CSP-owned | No defined remote deletion process; the Mac's remote-erase capability not assessed | none |
| UEM-14.1 | NA | CSP-owned | No third-party devices access the lab | none |

**Round 5 (53):** 0 Yes, 47 No, 6 NA.
