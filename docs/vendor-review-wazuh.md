# Third-Party Risk Review: Wazuh

Review date 2026-10-13. A vendor and product risk review of Wazuh, the SIEM used in this lab
(control C-24 in the [control inventory](control-inventory.md); CAIQ STA-08.1 and STA-14.1).
Self-assessment by the lab owner from public sources; not a vendor audit, and no questionnaire was
sent to the vendor.

## What is used

| Item | Detail |
| --- | --- |
| Product | Wazuh 4.14.7: manager, indexer and dashboard, single-node Docker deployment on `wazuh-siem`; agent 4.14.7 on `soc-endpoint-01` |
| Role in the lab | Security event collection, alerting, vulnerability detection |
| Commercial relationship | None. Self-hosted open-source software; no support contract, no SLA, no data processing agreement |
| Licence | GNU GPL version 2 (with OpenSSL linking terms); copyright Wazuh Inc., based on earlier work by Trend Micro ([LICENSE](https://github.com/wazuh/wazuh/blob/main/LICENSE)) |
| Data shared with the vendor | The manager downloads vulnerability content from Wazuh's feed. Whether any other data is sent to Wazuh Inc. was **not reviewed** |

## Vendor security practices

| Area | Finding | Source |
| --- | --- | --- |
| Vulnerability reporting | Reports go through GitHub security advisories or a security mailbox | [Security policy](https://github.com/wazuh/wazuh/security/policy) |
| Fix and disclosure | Investigate, fix, release, then disclose, within 90 days of a report; disclosure may be delayed so users can patch | [Security policy](https://github.com/wazuh/wazuh/security/policy) |
| CVE practice | Issues in released (GA) versions are tracked as GitHub advisories and considered for a CVE; pre-release issues are not | [Security policy](https://github.com/wazuh/wazuh/security/policy) |
| Supported versions | **Not stated.** The policy does not say which versions receive security fixes | [Security policy](https://github.com/wazuh/wazuh/security/policy) |
| Bug bounty | None | [Security policy](https://github.com/wazuh/wazuh/security/policy) |
| Release cadence | 4.14.x patch releases roughly monthly (4.14.6 on 1 July, 4.14.7 on 29 July, 4.14.8 on 23 September 2026) | [Release notes](https://documentation.wazuh.com/current/release-notes/index.html) |
| Active exploitation history | CVE-2025-24016, a remote code execution flaw in the Wazuh server fixed in 4.9.1, was exploited by Mirai botnets in 2025 | [Help Net Security](https://helpnetsecurity.com/2025/06/10/unpatched-wazuh-servers-targeted-by-mirai-botnets-cve-2025-24016) |

## Advisories affecting the version in use

On 2026-10-13, the day of this review, CVE records were published for flaws in Wazuh up to and
including 4.14.7 that are fixed in **4.14.8** (released 2026-09-23). The lab runs 4.14.7, so it is
in the affected range for each item below.

| CVE | Component | Flaw (summary) | CVSS 3.1 | Precondition | Applicability to this lab |
| --- | --- | --- | --- | --- | --- |
| CVE-2026-74034 | Manager | An enrolled agent can make the manager read arbitrary files as root | 7.5 | An enrolled agent | **Applies.** Enrollment ports are open on the lab network by design; whether enrollment requires a password is not documented |
| CVE-2026-74045 | Manager | An enrolled agent can overflow a heap buffer and crash the analysis engine | 7.1 | An enrolled agent | **Applies**, as above |
| CVE-2026-74047 | Manager | An API user with read access to agents can retrieve the enrollment password | 6.5 | An API account with agent read access | Applies. The API is loopback-only and has only the owner's account |
| CVE-2026-74041 | Manager | A configuration-validation bypass lets an API user with config-update rights run commands as root | 9.1 | An API account with config-update rights | Applies if the owner's admin account is compromised |
| CVE-2026-74035 | Manager | A delegated user administrator can take over the built-in superuser with an empty password | 7.2 | A delegated user-admin account | Precondition not present: no delegated admin accounts exist (not independently verified) |
| CVE-2026-74040, CVE-2026-74043 | Manager (cluster) | A cluster worker can overwrite protected files on the master or write files anywhere | 9.1, 9.0 | Control of a cluster node or the cluster key | Deployment is single-node; that clustering is disabled was **not verified** |
| CVE-2026-74036 | Agent | A compromised manager can run commands as root on agents through unsigned policy files | 7.2 | Control of the manager | Applies to agent 002 if the manager is compromised |

Scores and version ranges come from the vendor's advisories as republished by a CVE aggregator
([Strix](https://www.strix.ai/cve/CVE-2026-74034)); NVD analysis was still pending. They have not
been checked against every individual GitHub advisory. Per the lab's rules, a matching version is
not treated as proof of exposure or of safety: applicability above is assessed from the lab's
documented configuration.

Two High-severity advisories published 2026-08-18 (GHSA-6j39-726h-fx6p and GHSA-3jff-488g-335f /
CVE-2026-61800) list 4.14.7 as the patched version, so they do not affect the lab.

## Assessment

| Factor | Rating | Reason |
| --- | --- | --- |
| Inherent risk | High | The SIEM sees all security telemetry, runs as root on agents, and is a known exploitation target |
| Vendor transparency | Good | Public advisories, CVE assignment for released versions, detailed release notes |
| Vendor gaps | Medium | No stated supported-version policy; no bounty; no support relationship for this lab |
| Current exposure | **High** | Several High and Critical flaws published today affect the running version; a fix has been available for 20 days |

**Overall:** acceptable to keep using, **on condition** that the manager and agent are upgraded to
4.14.8. Until then, the lab carries known, fixable vulnerabilities in its most privileged system.

## Proposed actions (not approved or started)

| # | Action | Notes |
| --- | --- | --- |
| V-1 | Upgrade the Wazuh manager, indexer and dashboard to 4.14.8, then the agent | A change under the SIEM lab's rules; needs its own plan and approval. Upgrading the manager first also allows the agent hold (vulnerability-management-lab exception R-03) to be lifted |
| V-2 | Check and record whether agent enrollment requires a password | Read-only check; determines exposure to CVE-2026-74034 and CVE-2026-74045 |
| V-3 | Confirm clustering is disabled in the single-node deployment | Read-only check |
| V-4 | Subscribe to Wazuh GitHub security advisories and review monthly | Turns this one-off review into a recurring control (C-24) |
| V-5 | Review whether the manager sends data to Wazuh beyond feed downloads | Completes the data-sharing row above |

## Limits of this review

Based only on public information read on 2026-10-13. No vendor questionnaire, contract or
independent test. Advisory details were not all verified against the original GitHub advisories,
and the lab's exposure was assessed from documentation, not by testing.
