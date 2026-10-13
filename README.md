# GRC Documentation Lab

> Status: **complete (2026-10-13).**
>
> **Self-assessment, not an audit.** This repository applies GRC practices to my own home lab.
> It does not claim compliance with, or certification to, SOC 2, ISO 27001, CSA STAR or any
> other framework.

## Purpose

Practise core GRC work on a real (lab) environment, with every claim tied to evidence from my
other lab repositories.

## Deliverables

| Deliverable | Result |
| --- | --- |
| [System description](docs/system-description.md) | Scope, components, roles, third parties and data. One person holds every role, so there is no segregation of duties |
| [Control inventory](docs/control-inventory.md) | 24 controls: 8 Implemented, 16 Partial, each linked to evidence; plus a list of what no control covers |
| [SOC 2 TSC mapping and gap analysis](docs/tsc-mapping.md) | 36 Security and Availability criteria: 1 Addressed, 29 Partial, 4 Gap, 1 Not applicable, 1 Out of scope; seven main gaps (G-1 to G-7) |
| [CSA CAIQ v4.0.3 self-assessment](docs/caiq-self-assessment.md) | 261 answers keyed by question ID, confirmed by me in five rounds: 2 Yes, 215 No, 44 NA |
| [Security response library](docs/response-library.md) | 34 reusable questionnaire answers, each with evidence and a "limits of claim" line |
| [Third-party risk review: Wazuh](docs/vendor-review-wazuh.md) | Acceptable on condition of upgrading to 4.14.8: CVEs published on the review date affected the version in use. Upgraded the same day; enrollment without a password remains open |

Source material and how it is used: [sources and licensing](docs/sources-and-licensing.md).

## Main findings

- The technical controls are stronger than the governance around them. Most CAIQ "No" answers come
  from missing policies, plans and schedules (gaps G-1 and G-4), not missing technology.
- Segregation of duties cannot be achieved by one person (G-2); the compensating measures are
  written approvals before changes and published records.
- Monitoring covers one endpoint (G-3), and backups cover two of four VMs with no off-site copy (G-7).
- The SIEM ran a Wazuh version with newly published High and Critical CVEs; it was upgraded to
  4.14.8 the same day. Agent enrollment without a password remains open.

## AI Collaboration and Human Validation

Drafted with Claude as an assistant from my lab repositories. Claude read the repositories and
source files and wrote drafts in my lab folders through the Claude desktop app; I reviewed every
document, made the judgment calls, and ran and approved every commit. Rules: [CLAUDE.md](CLAUDE.md).

| What I asked for | What the AI proposed or assumed | What was checked or changed | Result |
| --- | --- | --- | --- |
| Use AICPA and CSA material | Fill in the CAIQ and quote the criteria | Downloaded the files and read their notices: CAIQ may not be modified or redistributed; AICPA grants no reuse | Reference by ID, own-words descriptions, source files kept out of Git; checked that no 7-word phrase is shared with the CAIQ |
| Control inventory | 10 Implemented controls; some evidence cited only by risk ID | The AI's own review against the repos found overclaims; I approved the fixes | Two controls downgraded to Partial, one wording corrected, every status linked to a real file (8 Implemented) |
| TSC mapping with NIST references | NIST controls picked for each criterion | A script checked every reference against the AICPA mapping and found 3 wrong | Corrected before commit; 49 of 49 now match |
| Risk ownership | Risk registers name an owner per risk | Checked the five registers: none has an owner column; only exceptions name owners | The claim was in three documents; fixed in a separate correction commit |
| CAIQ answers | Draft answers with stated rules (partial = No) | I confirmed all 261 in five rounds and decided each judgment call; unevidenced claims were removed before confirmation | One Yes downgraded to No because the evidence was not in the repos |
| Response library AI-use answer | "The owner runs every command" | Not true: the AI also ran commands on my Mac through the desktop app | Answer corrected to describe what the AI actually did |
| Wazuh vendor review | Review of vendor practices | Checked current advisories rather than relying on earlier reviews | Found CVEs published that day affecting the version in use |

Limitations: single-operator lab, so review is not independent; AI-drafted text was checked by me,
not by a second person.
