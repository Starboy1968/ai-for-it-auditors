# AI Audit Accelerators: Reporting, Monitoring and Auditing AI

Part of [AI for CISA and IT Auditors](README.md) (see the [overview and guardrails](01-overview-and-guardrails.md)). Use cases 7–9.

---

## 7. Findings and report drafting

**What it speeds up**
- Turning rough test notes into a structured finding
- Tone editing: clear, factual, not accusatory
- Predicting the questions management will ask

**The structure**
- The IIA's Global Internal Audit Standards (2024) describe a finding as the gap between **criteria** (what should be) and **condition** (what is), with **root cause** and **effect** (Standard 14.3), followed by **recommendations or action plans** (Standard 14.4). ([IIA Standards](https://www.theiia.org/globalassets/site/standards/globalinternalauditstandards_2024january9.pdf))
- Trainers often call this the "5 Cs." The Standards also say findings should be written "succinctly, in plain language."

| Part | Question it answers | Made-up example |
|---|---|---|
| **Criteria** | What should happen? | Access policy: leavers' accounts are disabled within 1 business day |
| **Condition** | What actually happened? | 4 of 25 sampled leavers still had active accounts 10+ days after leaving |
| **Cause** | Why? | HR notifies IT by email; no ticket, no tracking |
| **Effect** | So what? | Former staff could still reach company data |
| **Recommendation** | What fixes the cause? | Automate the HR-to-IT handoff and run a weekly leaver match |

**Workflow**

| Input | AI step | Human check | Output |
|---|---|---|---|
| Your own test results and notes (no client names in free tools) | Arrange into criteria / condition / cause / effect / recommendation. Suggest a neutral tone. List likely management questions. | Every number matches the work papers. Cause is confirmed with management, not guessed. Rating comes from the firm's methodology, never from the AI. | Draft finding ready for review |

**The human check**
- [ ] Every number and date matches the work papers
- [ ] Root cause was discussed with management (the Standards expect this "when possible")
- [ ] The AI didn't soften the condition or inflate the effect
- [ ] Severity rating set by the auditor using the firm's scale

**Example prompt (example)**
```
Rewrite these notes as one audit finding with five headings:
Criteria, Condition, Cause, Effect, Recommendation.
Plain language, neutral tone, no blame. Do not change any number.
Then list 5 questions management is likely to ask about it.
```

**Real-world signal (vendor material)**
- TeamMate+ AI Editor (Wolters Kluwer, Jun 2025) has built-in prompts to improve clarity, adjust tone, summarize, expand short notes, and translate; Wolters Kluwer says it includes a PII blocker and no data retention (VENDOR CLAIM). ([Wolters Kluwer](https://www.wolterskluwer.com/en/news/wolters-kluwer-transforms-audit-documentation-launch-teammate-ai-editor))
- An audit supervisor at FlowServe told Workiva the team uses GenAI to predict management's questions before reports go out (customer story). ([Workiva](https://www.workiva.com/blog/gen-ai-impact-internal-audit))
- PCAOB staff found some firms let staff use GenAI for first drafts of memos, with the user still responsible for the work. ([PCAOB, Jul 2024](https://pcaobus.org/documents/generative-ai-spotlight.pdf))

**Practice for free**
- [ ] Take a finding from a public government audit report, strip it to bullet notes, ask an AI to rebuild it in five parts, and compare with the original

---

## 8. Continuous auditing and monitoring ideas

> **These are ideas, not documented deployments.** They are simple patterns a team could pilot. Most are better done with scripts and scheduled reports than with an LLM; AI helps write the script, explain results, and draft the exception summary.

| Idea | Data | Rule | Where AI helps | Human check |
|---|---|---|---|---|
| **Recurring leaver check** | HR terminations + active accounts | Any leaver still active after the policy window | Draft the matching script; summarize the weekly result in plain language | Confirm each hit in the source system before raising it |
| **Access review exceptions** | Review sign-off exports | Reviews approved with zero changes, late, or self-reviewed | Group reviewer comments by theme | Inspect the actual review evidence |
| **Config drift** | Current config exports vs an approved baseline | Any setting that changed from baseline without a change ticket | Explain what a changed setting does | Match each drift to a ticket or raise it |
| **KEV vs asset inventory** | The free [CISA Known Exploited Vulnerabilities catalog](https://www.cisa.gov/known-exploited-vulnerabilities-catalog) (CSV/JSON feed) + asset/software inventory | Any inventory item matching a KEV entry that's past its patch target | Normalize messy product names before matching | Confirm the version and patch state on the asset itself |
| **Emergency change watch** | Change tickets | Share of "emergency" changes per month above a set level | Summarize justifications | Sample and test the outliers |

**Notes on the KEV idea**
- The KEV catalog lists vulnerabilities with reliable evidence of active exploitation, an assigned CVE ID, and an available fix. ([CISA KEV](https://www.cisa.gov/known-exploited-vulnerabilities-catalog))
- For US federal civilian agencies, remediation deadlines now come from **BOD 26-04** (Jun 10, 2026), which revoked and replaced BOD 22-01 (the 2021 directive that created KEV). ([BOD 26-04 guidance](https://www.cisa.gov/news-events/directives/bod-26-04-implementation-guidance-prioritizing-security-updates-based-risk))
- CISA itself says KEV is not the only list to worry about: many risks (e.g., misconfigurations) have no CVE ID.
- For other organizations it's a free, defensible priority list: "are we exposed to things attackers are already using?"

**The human check**
- [ ] Each rule has a written owner, threshold, and follow-up path before it runs
- [ ] Hits are leads; each is confirmed before it's called an exception
- [ ] The script is version-controlled and re-performable

**Practice for free**
- [ ] Download the KEV CSV. Make a fake 15-item software inventory. Match them in a spreadsheet, then ask an AI to explain the top 3 hits in plain language.

---

## 9. Using AI to audit AI systems

**What it speeds up**
- Building an AI audit program from free frameworks
- Drafting governance interview questions and test ideas for AI tools in use

**Frameworks to anchor on (all real; most free)**

| Source | What it gives the auditor |
|---|---|
| **IIA AI Auditing Framework** (Sept 2024 update) | Three areas: Governance, Management, Internal Audit, built on the Three Lines Model ([IIA](https://www.theiia.org/globalassets/site/content/tools/professional/aiframework-sept-2024-update2.pdf)) |
| **NIST AI RMF 1.0 + Generative AI Profile (NIST AI 600-1)** | Four functions: **Govern, Map, Measure, Manage**, plus a free Playbook of suggested actions ([NIST](https://www.nist.gov/publications/artificial-intelligence-risk-management-framework-generative-artificial-intelligence), [Playbook](https://www.nist.gov/itl/ai-risk-management-framework/nist-ai-rmf-playbook)) |
| **COSO GenAI guidance** | Applies the COSO 2013 internal control framework to GenAI; names risks such as prompt manipulation, "opaque reasoning," model drift, and frequent configuration changes ([COSO](https://www.coso.org/generative-ai)) |
| **ISO/IEC 42001:2023** | Certifiable AI management system standard (policy, risk and impact assessment, internal audit, management review). Paid standard; free ISO explainer ([ISO](https://www.iso.org/insights/iso-42001-explained)) |
| **OWASP Top 10 for LLM Applications 2025** | Security risks for LLM apps, starting with **LLM01 Prompt Injection** (direct and indirect, e.g., instructions hidden in a file the model reads) ([OWASP](https://genai.owasp.org/llmrisk/llm01-prompt-injection/)) |
| **Banking model risk guidance** | SR 11-7 (2011) was the long-time US standard for model risk management. On Apr 17, 2026 the Fed, OCC, and FDIC replaced it with revised guidance (**SR 26-2** / OCC Bulletin 2026-13). The new guidance says GenAI and agentic AI are **not** in its scope. ([Fed SR 26-2](https://www.federalreserve.gov/supervisionreg/srletters/SR2602.htm), [OCC 2026-13](https://www.occ.gov/news-issuances/bulletins/2026/bulletin-2026-13.html)) |

**What to audit (question bank, organized by NIST AI RMF function)**

| Function | Area | Example questions |
|---|---|---|
| **Govern** | Policy and ownership | Is there an AI use policy? Who approves a new AI tool? Is there a named owner per system? |
| **Govern** | Shadow AI | How would you know if staff used an unapproved AI tool? (ISACA 2026: 90% believe employees use AI; 38% of organizations have a comprehensive policy) |
| **Map** | Model inventory | Is there a list of every AI system and model, including vendor features switched on inside existing software? What decisions does each one touch? |
| **Map** | Data lineage | Where did the training or reference data come from? Who can change it? Is personal data in it? |
| **Measure** | Performance and drift | What does "working" mean for this model, how is it measured, and how often? |
| **Measure** | Bias and fairness | Were outcomes compared across groups the decision affects? Who decided what counts as fair here? (NIST lists "fair, with harmful bias managed" as a trustworthiness characteristic) |
| **Manage** | Human oversight | Which outputs need a human sign-off? Is there evidence the human actually reviewed, or just clicked approve? |
| **Manage** | Security | Has the tool been tested for prompt injection? Can it take actions (send, delete, pay) without approval? (OWASP LLM01; LLM06 Excessive Agency) |
| **Manage** | Third-party AI | Does the vendor contract cover data use for training, retention, and audit rights? |

**Workflow**

| Input | AI step | Human check | Output |
|---|---|---|---|
| The organization's AI inventory or list of AI tools in use + one framework (e.g., NIST AI RMF Playbook) | Draft an audit program: risk → control → test → evidence, per function | Confirm each control exists in the framework text. Tailor to what the organization actually uses. | AI governance audit program |
| A specific AI tool (in a test environment, with permission) | Generate test prompts for known risks (e.g., does it reveal its instructions, follow instructions hidden in an uploaded file) | Only test with written authorization, in scope, on non-production data. Record results yourself. | Test results with screenshots |

**The human check**
- [ ] Prompt-injection testing is authorized in writing and scoped (it's security testing)
- [ ] "We have a policy" is tested against what people actually do
- [ ] The inventory includes AI features inside existing vendor tools, not just standalone apps
- [ ] Bias questions are about measured outcomes, not stated intentions

**Why this is a gap worth filling**
- Only **15%** of CAEs in the IIA 2025 Pulse said they provide assurance over their organization's GenAI use. ([IIA](https://www.theiia.org/globalassets/site/resources/research-and-reports/pulse-of-internal-audit/2025-iia-pulse-report.pdf))
- ISACA also offers an AI Audit Toolkit (Excel control library) and the AAIA credential; AAIA requires an active CISA or a qualifying credential, so it's not entry-level. ([ISACA AAIA](https://www.isaca.org/credentialing/aaia), [Toolkit](https://www.isaca.org/store2/product/WAICAT))

**Practice for free**
- [ ] Using the NIST AI RMF Playbook, write 5 interview questions for "who approves new AI tools?"
- [ ] Pick one public AI tool you use and fill in one row of a model inventory: purpose, data in, data out, owner, human check
- [ ] Read OWASP LLM01 and write two test ideas in plain language

## Links
- Overview: [Overview and guardrails](01-overview-and-guardrails.md)
- Previous: [Documents, mapping and evidence (use cases 4-6)](03-documents-mapping-and-evidence.md)
- Sources: [sources.md](sources.md)
