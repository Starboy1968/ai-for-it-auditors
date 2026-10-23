# AI for CISA and IT Auditors: Creative Workflow Accelerators

> **Purpose:** a practical guide to where AI can speed up IT audit and assurance work, and where a person has to stay in charge. Every use case follows the same shape: **input → AI step → human check → output**. AI drafts, sorts, and flags. The auditor decides, tests, and signs.

**In one line:** AI is a fast first-draft partner for the writing-heavy and reading-heavy parts of an audit. It is not evidence, and it is not the auditor.

**A naming note:** "CISA" here means ISACA's Certified Information Systems Auditor credential, not the US Cybersecurity and Infrastructure Security Agency. (The agency shows up once, in use case 8, for its KEV catalog.)

> **About this guide:** an independent, self-directed portfolio project built from public sources. It is not client or employer work. Vendor features described here are vendor claims, not independently tested. Example prompts use public or made-up material only.

## Why this matters now
- **41%** of chief audit executives in the IIA's 2025 North American Pulse said their function uses GenAI for internal audit work, up from 15% the year before. Only **15%** provide assurance over their organization's own GenAI use. ([IIA 2025 Pulse](https://www.theiia.org/globalassets/site/resources/research-and-reports/pulse-of-internal-audit/2025-iia-pulse-report.pdf))
- In ISACA's 2026 AI Pulse Poll, **90%** of respondents believe employees use AI, but only **38%** say their organization has a formal, comprehensive AI policy. ([ISACA 2026](https://www.isaca.org/about-us/newsroom/press-releases/2026/ai-use-accelerates-while-governance-and-roi-lag-says-new-isaca-research))
- The gap is the point: audit teams are adopting AI faster than most organizations are governing it. Auditors need to know both sides, how to use it and how to audit it.

## The pattern behind every use case

| Step | Who | What good looks like |
|---|---|---|
| **Input** | Auditor | Approved data only. Public or sanitized for practice. Clear scope. |
| **AI step** | Tool | Draft, summarize, group, compare, or flag. Never "conclude." |
| **Human check** | Auditor | Trace every claim back to the source. Re-perform anything that counts as evidence. |
| **Output** | Auditor | A work paper the auditor can defend without mentioning the AI, plus a note that AI was used. |

**Rule of thumb:** if a reviewer asked "how do you know?", the answer must point to a source document or a test, never to "the AI said so."

## The nine use cases

| # | Use case | What it speeds up | Note |
|---|---|---|---|
| 1 | Walkthrough interviews → process narratives and flowcharts | Turning meeting notes into written narratives | [Planning and fieldwork (use cases 1-3)](02-planning-and-fieldwork.md) |
| 2 | Interview prep and question generation | Open questions, follow-ups, red-flag answers | [Planning and fieldwork (use cases 1-3)](02-planning-and-fieldwork.md) |
| 3 | Drafting audit programs and test steps | First draft of test steps from a control objective | [Planning and fieldwork (use cases 1-3)](02-planning-and-fieldwork.md) |
| 4 | Document summarization (policies, contracts, SOC 2 reports) | Finding CUECs, exceptions, carve-outs, gaps | [Documents, mapping and evidence (use cases 4-6)](03-documents-mapping-and-evidence.md) |
| 5 | Policy-to-control and control-to-framework mapping | First-pass gap analysis | [Documents, mapping and evidence (use cases 4-6)](03-documents-mapping-and-evidence.md) |
| 6 | Evidence review and anomaly flagging | Triage of tickets and access lists | [Documents, mapping and evidence (use cases 4-6)](03-documents-mapping-and-evidence.md) |
| 7 | Findings and report drafting | Structure and tone of findings | [Reporting, monitoring and auditing AI (use cases 7-9)](04-reporting-monitoring-and-auditing-ai.md) |
| 8 | Continuous auditing and monitoring ideas | Recurring exception checks | [Reporting, monitoring and auditing AI (use cases 7-9)](04-reporting-monitoring-and-auditing-ai.md) |
| 9 | Using AI to audit AI systems | Inventory, governance, and risk questions | [Reporting, monitoring and auditing AI (use cases 7-9)](04-reporting-monitoring-and-auditing-ai.md) |

## Where AI should NOT be used (guardrails)

| Risk | What goes wrong | Guardrail |
|---|---|---|
| **Confidentiality** | Client or employer data pasted into a consumer chatbot leaves the organization's control. Some firms limit uploads, and some don't allow GenAI in audit procedures at all ([PCAOB staff, Jul 2024](https://pcaobus.org/documents/generative-ai-spotlight.pdf)). | Never paste employer or client data into a free consumer tool. Use only firm-approved tools for real work. |
| **Hallucinated citations** | Deloitte Australia partly refunded a A$440K government report after it was found to contain fabricated citations and a made-up court quote. The revised report disclosed GPT-4o use. ([Guardian](https://www.theguardian.com/australia-news/2025/oct/06/deloitte-to-pay-money-back-to-albanese-government-after-using-ai-in-440000-report), [AP](https://apnews.com/article/australia-ai-errors-deloitte-ab54858680ffc4ae6555b31c8fb987f3)) | Open and check every citation, clause number, and quote against the original. |
| **Automation bias** | A confident, tidy answer gets accepted because it looks finished. | Treat AI output like a junior's first draft. PCAOB-interviewed firms said the person using the tool owns the result, and reviewers apply the same diligence as usual. |
| **AI output treated as evidence** | A summary of a SOC 2 report is not the SOC 2 report. A flagged list is not a tested exception. | Evidence = source documents and re-performed tests. AI output is a pointer to where to look. |
| **Undocumented AI use** | A reviewer can't tell what was AI-drafted or what was checked. | Log the tool, what went in, what came out, and what was changed. The IIA's Global Internal Audit Standards (Standard 14.6) already expect documentation that lets a reviewer re-perform the work. |
| **Loss of professional skepticism** | The AI frames the story first, and the auditor stops asking "what's missing?" | Write your own hypothesis before reading the AI output. Ask the AI for the weakest point in its own answer. |
| **Firm and client policy** | Using an unapproved tool can breach engagement terms, even if nothing leaks. | Check the firm's AI policy first. If there isn't one, that is itself a finding (only 38% have one, per ISACA 2026). |

**Hard "no" list (for real engagements):**
- [ ] No real client or employer data in free or personal AI accounts
- [ ] No AI-generated citation, standard number, or quote left unchecked
- [ ] No conclusion, opinion, or rating decided by the AI
- [ ] No sample selection handed to an LLM when a tool with a random seed and a log can do it
- [ ] No sending AI-drafted findings to management before a human reviewer signs off

## Try it this week (free tools, public documents only)

- [ ] **NotebookLM (now "Gemini Notebook")**: upload a public company's published code of conduct plus [NIST CSF 2.0](https://nvlpubs.nist.gov/nistpubs/CSWP/NIST.CSWP.29.pdf). Ask "Where does the policy not cover the Govern function?" Check every citation it gives. ([Google help](https://support.google.com/notebooklm/answer/16269187))
- [ ] **ChatGPT Free or Claude Free, training settings off first**: ChatGPT under Settings > Data Controls ([OpenAI](https://help.openai.com/en/articles/7730893-data-controls-in-chatgpt)); Claude under Settings > Privacy ([Anthropic](https://www.anthropic.com/news/updates-to-our-consumer-terms)). Rewrite one public audit finding in criteria / condition / cause / effect / recommendation form.
- [ ] **Otter.ai Basic**: record a 15-minute mock walkthrough with a friend about a made-up process (e.g., "how a coffee shop orders beans"). Turn the transcript into a narrative and mark what the transcript doesn't support. ([Otter pricing](https://otter.ai/pricing))
- [ ] **Taguette**: tag your own mock interview notes by theme ("workaround," "manual step," "single approver"). Compare your tags with the AI's grouping. ([Taguette](https://www.taguette.org/))
- [ ] **Secure Controls Framework (SCF)**: map one sentence from a public security policy to NIST CSF 2.0, ISO 27001, and SOC 2 using the SCF spreadsheet columns. Then ask an AI to do the same and compare. ([SCF download](https://securecontrolsframework.com/free-content/scf-download))
- [ ] **Log it**: write down what broke and what you had to correct.

## Links
- Start: [README](README.md)
- Next: [Planning and fieldwork (use cases 1-3)](02-planning-and-fieldwork.md)
- Then: [Documents, mapping and evidence (use cases 4-6)](03-documents-mapping-and-evidence.md) · [Reporting, monitoring and auditing AI (use cases 7-9)](04-reporting-monitoring-and-auditing-ai.md)
- Sources and claims to verify: [sources.md](sources.md)

## Sources and claims to verify
All main sources and the list of claims still to verify are in [sources.md](sources.md). Each use-case page also links its own sources inline.

---
Rashon Alsberry, independent portfolio project - [starboy1968.github.io](https://starboy1968.github.io)
