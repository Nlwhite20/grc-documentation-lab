# GRC Documentation Lab

> Status: **in progress (2026-10-13).** System description and control inventory drafted.
>
> **Self-assessment, not an audit.** This repository applies GRC practices to my own home lab.
> It does not claim compliance with, or certification to, SOC 2, ISO 27001, CSA STAR or any
> other framework.

## Purpose

Practise core GRC work on a real (lab) environment, with every claim tied to evidence from my
other lab repositories:

| Deliverable | Status |
| --- | --- |
| [System description](docs/system-description.md) | Draft |
| [Control inventory](docs/control-inventory.md) | Draft |
| SOC 2 Trust Services Criteria mapping and gap analysis | Planned |
| CSA CAIQ v4 self-assessment (answers keyed by question ID) | Planned |
| Security response library (RFP and questionnaire style) | Planned |
| Third-party risk review (Wazuh) | Planned |

Source material and how it is used: [sources and licensing](docs/sources-and-licensing.md).

## AI Collaboration and Human Validation

Drafted with Claude as an assistant from my lab repositories; I review and approve every document
and commit. Rules: [CLAUDE.md](CLAUDE.md).

| What I asked for | What the AI proposed or assumed | What I checked or changed | Result |
| --- | --- | --- | --- |
| Use AICPA and CSA material | Fill in the CAIQ and quote the criteria | Downloaded the files and read their notices: CAIQ may not be modified or redistributed; AICPA grants no reuse | Reference by ID, own-words descriptions, source files kept out of Git |

Limitations: single-operator lab, so review is not independent.
