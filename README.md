# AI for CISA and IT Auditors: Creative Workflow Accelerators

**Practical AI workflows for CISA and IT auditors: walkthroughs, audit programs, SOC 2 review, control mapping, evidence, findings, and auditing AI.**

For hiring managers and teams in IT audit, internal audit, GRC and assurance, and for auditors who want to use AI without giving up professional judgment.

> An independent portfolio project: self-directed and built from public sources, not client or employer work. Vendor features mentioned are vendor claims, not independently tested. "CISA" here means ISACA's Certified Information Systems Auditor credential.

## What it is

A plain-language guide to nine places where AI can speed up IT audit work, and where a person has to stay in charge. AI drafts, sorts and flags. The auditor decides, tests and signs. Each use case has a workflow table, a human-check list, an example prompt and a free way to practice on public or made-up material.

**Why now:** in the IIA's 2025 North American Pulse, 41% of chief audit executives said their function uses GenAI for audit work, but only 15% provide assurance over their organization's own GenAI use. Audit teams are adopting AI faster than most organizations are governing it. ([details and sources](01-overview-and-guardrails.md#why-this-matters-now))

## The pattern behind every use case

**Input → AI step → human check → output**

| Step | Who | What good looks like |
|---|---|---|
| Input | Auditor | Approved data only; public or sanitized for practice; clear scope |
| AI step | Tool | Draft, summarize, group, compare or flag. Never "conclude." |
| Human check | Auditor | Trace every claim to the source; re-perform anything that counts as evidence |
| Output | Auditor | A work paper the auditor can defend without the AI, plus a note that AI was used |

## The nine use cases

| # | Use case | What AI speeds up | Page |
|---|---|---|---|
| 1 | Walkthrough interviews → process narratives and flowcharts | Notes to a first-draft narrative | [02 Planning and fieldwork](02-planning-and-fieldwork.md) |
| 2 | Interview prep and question generation | Open questions, follow-ups, red-flag answers | [02 Planning and fieldwork](02-planning-and-fieldwork.md) |
| 3 | Drafting audit programs and test steps | Test steps from NIST 800-53A objectives | [02 Planning and fieldwork](02-planning-and-fieldwork.md) |
| 4 | Document summarization, incl. SOC 2 reports | Exceptions, CUECs, carve-outs, bridge letters | [03 Documents, mapping and evidence](03-documents-mapping-and-evidence.md) |
| 5 | Policy-to-control and control-to-framework mapping | First-pass gap analysis anchored to SCF / NIST OLIR | [03 Documents, mapping and evidence](03-documents-mapping-and-evidence.md) |
| 6 | Evidence review and anomaly flagging | Triage of tickets and access reviews (and when a script beats an LLM) | [03 Documents, mapping and evidence](03-documents-mapping-and-evidence.md) |
| 7 | Findings and report drafting | Criteria / condition / cause / effect / recommendation | [04 Reporting, monitoring and auditing AI](04-reporting-monitoring-and-auditing-ai.md) |
| 8 | Continuous auditing and monitoring ideas | Leaver checks, config drift, CISA KEV matching | [04 Reporting, monitoring and auditing AI](04-reporting-monitoring-and-auditing-ai.md) |
| 9 | Using AI to audit AI systems | Audit program and question bank on NIST AI RMF, IIA, COSO, ISO 42001, OWASP | [04 Reporting, monitoring and auditing AI](04-reporting-monitoring-and-auditing-ai.md) |

## Guardrails (headline)

**AI output is not evidence, and AI is not the auditor.** No real client or employer data in free or personal AI tools. Every citation, standard number and quote is opened and checked. No conclusion, rating or sample selection is decided by the AI. AI use is logged so a reviewer can re-perform the work. Full guardrail table and "hard no" list: [01 Overview and guardrails](01-overview-and-guardrails.md#where-ai-should-not-be-used-guardrails).

## Skills demonstrated

- IT audit methodology: walkthroughs, test design (examine / interview / test), evidence, sampling, findings
- Third-party assurance: SOC 2 Type II review, CUECs, subservice carve-outs, bridge letters
- Control and framework mapping: ISACA ITAF and CISA domains, COBIT 2019, NIST CSF 2.0, NIST SP 800-53 / 800-53A, SCF, NIST OLIR
- AI governance and auditing AI: NIST AI RMF and AI 600-1, IIA AI Auditing Framework, COSO GenAI guidance, ISO/IEC 42001, OWASP Top 10 for LLM Applications
- Responsible AI use: confidentiality, hallucination checks, automation bias, documentation of AI use

## Repo map

| File | What's inside |
|---|---|
| [01-overview-and-guardrails.md](01-overview-and-guardrails.md) | Why it matters, the pattern, all nine use cases, guardrails, try-it-this-week list |
| [02-planning-and-fieldwork.md](02-planning-and-fieldwork.md) | Use cases 1-3: walkthroughs, interview prep, audit programs |
| [03-documents-mapping-and-evidence.md](03-documents-mapping-and-evidence.md) | Use cases 4-6: SOC 2 and document review, control mapping, evidence triage |
| [04-reporting-monitoring-and-auditing-ai.md](04-reporting-monitoring-and-auditing-ai.md) | Use cases 7-9: findings, continuous monitoring, auditing AI |
| [sources.md](sources.md) | Main sources and the list of claims still to verify |

## Related projects

- [AI Supply Chain Risk Assessment](https://github.com/Starboy1968/ai-supply-chain-risk-assessment): nine scored AI-related supply chain risks, with controls, warning indicators (KRIs) and a 30/60/90-day plan.
- [AI-Assisted Risk Analysis](https://github.com/Starboy1968/ai-assisted-risk-analysis): a reusable risk-analysis prompt and a worked example where an AI first draft is checked and corrected by a human reviewer.
- [Reading the Room: Power and Behavior Risk Indicators](https://github.com/Starboy1968/power-behavior-risk-indicators): observable signs of how power, incentives and group behavior shape risk decisions, and how to turn them into solid findings.
- [Behavioral Supply Chain Risk: Human Factors, AI, and Audit](https://github.com/Starboy1968/behavioral-supply-chain-risk-audit-ai): how bias and pressure create supply chain risk, and how AI triage, audit evidence and human review help catch it.
- [Playing the Risk Game: Game Theory for Supply Chain Risk and AI Governance](https://github.com/Starboy1968/supply-chain-ai-governance-strategy): plain-language game theory that explains why supply chain and AI risks persist, and which incentives to change.
- [AI in Supply Chain Operations: A Strategist's Field Guide](https://github.com/Starboy1968/ai-in-supply-chain-operations): how a supply chain manager can use AI in six everyday jobs, and what to check before trusting it.
- [Healthcare Cyber Risk Program: An OSINT Case Study](https://github.com/Starboy1968/healthcare-cyber-risk-osint-case-study): a cyber risk program for a fictional regional health system, built only from public sources.

## Author

Rashon Alsberry, supply chain and third-party risk analyst - [starboy1968.github.io](https://starboy1968.github.io)
