# AI Audit Accelerators: Planning and Fieldwork

Part of [AI for CISA and IT Auditors](README.md) (see the [overview and guardrails](01-overview-and-guardrails.md)). Use cases 1–3.

Every example prompt below is labeled **example**. Use them only with public or made-up material unless your firm has approved the tool.

---

## 1. Walkthrough interviews → process narratives and flowcharts

**What it speeds up**
- Turning an hour of walkthrough notes or a transcript into a clean, step-by-step process narrative
- Drafting a first flowchart from that narrative

**Workflow**

| Input | AI step | Human check | Output |
|---|---|---|---|
| Approved transcript or typed notes from the walkthrough | Draft a numbered narrative: who does what, in which system, with what evidence. Then list the steps as a flowchart outline (start, decision points, handoffs, end). | Compare every step with the notes. Mark anything the AI added that nobody said. Confirm key controls with the process owner. | Narrative and flowchart in the work papers, marked "AI-assisted first draft, reviewed by [auditor]" |

**The human check**
- [ ] Every step in the narrative can be traced to a line in the notes
- [ ] Gaps are left as gaps ("not discussed"), not filled with a guess
- [ ] Controls are labeled as **described** until they are tested
- [ ] The process owner confirms the final narrative

**Example prompt (example)**
```
From the notes below, write a numbered process narrative.
For each step give: role, action, system, evidence created.
Do not add steps that are not in the notes. Where something is unclear,
write "UNCLEAR - ask owner". Then list the decision points for a flowchart.
```

**Real-world signal (vendor material)**
- KPMG says its teams, using Microsoft Copilot from April 2024, "transform the walkthrough experience by generating process narratives and flowcharts based on meetings with clients" (VENDOR CLAIM). ([KPMG](https://kpmg.com/us/en/media/news/kpmg-clara-smart-audit-platform.html))
- An audit supervisor at FlowServe told Workiva the team builds narratives from meeting transcripts, which led to better follow-up questions, then creates flowcharts from them (customer story published by the vendor). ([Workiva](https://www.workiva.com/blog/gen-ai-impact-internal-audit))
- Optro (AuditBoard's new name since Mar 2026) says its "Document Intelligence" turns walkthrough notes into detailed narratives (VENDOR CLAIM). ([PR Newswire](https://www.prnewswire.com/news-releases/auditboard-launches-accelerate-delivering-enterprise-grade-ai-automation-for-grc-teams-302590866.html), [Optro rename](https://optro.ai/blog/meet-optro-auditboard-unveils-new-identity-as-ai-transforms-grc))

**Practice for free**
- [ ] Record a 15-minute mock walkthrough about a made-up process (e.g., "how a small shop approves refunds") with Otter.ai Basic
- [ ] Ask a free AI tool for the narrative using the prompt above
- [ ] Highlight in a second color every sentence the transcript doesn't support

---

## 2. Interview prep and question generation

**What it speeds up**
- Going from "here is the policy and the risk" to a full interview guide: open questions, follow-ups, and what a worrying answer sounds like

**Workflow**

| Input | AI step | Human check | Output |
|---|---|---|---|
| The relevant policy section + one risk statement (e.g., "terminated users keep access") | Draft 8–10 open questions, a follow-up for each, and examples of red-flag answers | Cut leading or yes/no questions. Add questions about workarounds and exceptions. Match questions to the evidence you'll ask for. | Interview guide with an evidence request list |

**The human check**
- [ ] Questions are open ("Walk me through…", "What happens when…"), not yes/no
- [ ] Each question links to a control or a risk, not to curiosity
- [ ] Red-flag answers are cues to dig, not conclusions
- [ ] The guide asks for evidence, so the interview isn't the only support (inquiry alone is usually not enough evidence)

**Example output shape (example, made-up access policy)**

| Open question | Follow-up | Red-flag answer (dig further) |
|---|---|---|
| Walk me through what happens when someone leaves the company. | Who tells IT, and how fast? | "HR usually emails us when they remember." |
| How do you know every account was removed? | Can you show me last month's list? | "We trust the ticket was closed." |
| What happens when a manager needs access restored for a leaver? | Who approves that, and is it logged? | "We just turn it back on, it's quicker." |
| Who reviews access to the finance system? | What did the last review change? | "Nothing ever changes, so we approve it all." |

**Example prompt (example)**
```
Policy section: [paste public or made-up policy].
Risk: terminated users keep system access.
Write 8 open interview questions for the IT access owner.
For each, add one follow-up and one example answer that should make an auditor dig deeper.
No yes/no questions.
```

**Why it works:** NIST SP 800-53A Rev. 5 lists three assessment methods: **examine, interview, and test**. AI helps you prepare the interview, so the interview leads straight into examine and test. ([NIST SP 800-53A Rev. 5](https://csrc.nist.gov/pubs/sp/800/53/a/r5/final))

**Practice for free**
- [ ] Take a public university's published acceptable-use or access policy
- [ ] Generate a guide with the prompt above, then rewrite the three weakest questions yourself

---

## 3. Drafting audit programs and test steps

**What it speeds up**
- First draft of test steps from a control objective, with design and operating-effectiveness steps split out
- Cross-referencing each step to frameworks a reviewer will recognize

**Workflow**

| Input | AI step | Human check | Output |
|---|---|---|---|
| A control objective (e.g., "Changes to production are authorized, tested, and approved before deployment") | Draft test steps: inquiry, inspection, re-performance; suggested evidence; sample population. Suggest framework references. | Open each framework reference and confirm it exists and says what the AI claims. Set sample sizes from the firm's methodology, not the AI. | Draft audit program, with references checked |

**Frameworks to map to (only what's real; open each one to check)**

| Framework | What it gives you | Example for change management |
|---|---|---|
| **ISACA ITAF, 4th ed. (2020)** | Mandatory IT audit standards: general (1000 series), performance (1200 series: planning, risk assessment, evidence), reporting (1400 series) ([ISACA](https://www.isaca.org/about-us/newsroom/press-releases/2020/isaca-updates-it-audit-framework-itaf)) | Performance standards shape how evidence is gathered |
| **CISA job practice (2024)** | Five domains: 1 IS Auditing Process (18%), 2 Governance and Management of IT (18%), 3 IS Acquisition, Development and Implementation (12%), 4 IS Operations and Business Resilience (26%), 5 Protection of Information Assets (26%) ([ISACA outline](https://www.isaca.org/credentialing/cisa/cisa-exam-content-outline)) | Domain 4: "IT Change, Configuration, and Patch Management" |
| **COBIT 2019** | Governance and management objectives ([ISACA COBIT](https://www.isaca.org/resources/cobit)) | BAI06 Managed IT Changes |
| **NIST CSF 2.0** | Outcomes under six functions: Govern, Identify, Protect, Detect, Respond, Recover ([CSWP 29](https://nvlpubs.nist.gov/nistpubs/CSWP/NIST.CSWP.29.pdf)) | Find the matching outcome with the free CSF 2.0 Reference Tool / OLIR rather than trusting an AI-given ID |
| **NIST SP 800-53 / 800-53A Rev. 5** | Controls plus ready-made assessment objectives ("Determine if…") and methods (examine, interview, test); downloadable as CSV and spreadsheet ([NIST downloads](https://csrc.nist.gov/projects/risk-management/sp800-53-controls/downloads)) | CM-3 Configuration Change Control |

**The human check**
- [ ] Every framework ID was opened and read, not copied from the AI
- [ ] Steps test what the control **does**, not just whether a policy exists
- [ ] Sample size and selection follow the firm's methodology (ITAF also has a companion sampling guideline)
- [ ] Each step names the evidence that would prove it

**Best trick:** give the AI the real 800-53A assessment objective text for the control (from NIST's free CSV) and ask it to turn the "Determine if…" statements into plain test steps. The AI then rewrites real criteria instead of inventing them.

**Example prompt (example)**
```
Control objective: changes to production are authorized, tested, and approved before deployment.
Below are the NIST SP 800-53A assessment objectives for CM-3 (pasted from the NIST CSV).
Turn them into test steps. For each step give: method (examine/interview/test),
evidence to request, and what an exception looks like. Do not add framework references I did not provide.
```

**Real-world signal (vendor material)**
- Optro/AuditBoard says its AI drafts risk statements, control descriptions, and test steps, and a person must edit and approve them (VENDOR CLAIM). ([AuditBoard blog](https://auditboard.com/blog/auditboard-transforms-internal-audit-with-advanced-ai-capabilities/))
- KPMG says GenAI added to KPMG Clara in July 2024 helps write test procedures (VENDOR CLAIM). ([KPMG](https://kpmg.com/us/en/media/news/kpmg-clara-smart-audit-platform.html))

**Practice for free**
- [ ] Download the 800-53A Rev. 5 CSV, pick AC-2 (Account Management), and draft a one-page test program with the prompt above
- [ ] Check: did any step drift away from the NIST text?

## Links
- Overview: [Overview and guardrails](01-overview-and-guardrails.md)
- Next: [Documents, mapping and evidence (use cases 4-6)](03-documents-mapping-and-evidence.md)
- Sources: [sources.md](sources.md)
