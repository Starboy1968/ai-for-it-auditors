# AI Audit Accelerators: Documents, Mapping and Evidence

Part of [AI for CISA and IT Auditors](README.md) (see the [overview and guardrails](01-overview-and-guardrails.md)). Use cases 4–6.

---

## 4. Document summarization (policies, contracts, SOC 2 reports)

**What it speeds up**
- Pulling the audit-relevant parts out of long documents
- Building a first-pass review checklist for a vendor's SOC 2 report

**Workflow**

| Input | AI step | Human check | Output |
|---|---|---|---|
| A policy, contract, or SOC 2 Type II report (approved tool only; SOC reports are usually under NDA) | Extract into a table: scope, period, opinion type, exceptions, CUECs, carve-outs, dates. Quote the page or section for each item. | Open every cited page. Confirm exceptions word for word. Check nothing important is missing from the list. | Vendor review memo with page references |

**What to pull from a SOC 2 report**

| Item | Plain meaning | Why it matters |
|---|---|---|
| **Report period and type** | Type II covers how controls worked over a period | A Type I only shows design at one point in time |
| **Opinion** | Clean (unmodified) or qualified | A qualified opinion is a headline, not a footnote |
| **Exceptions / deviations** | Tests where the control didn't work | Decide if any hit controls your organization relies on |
| **Complementary user entity controls (CUECs)** | Controls the vendor assumes **you** run (e.g., managing your own users' access) | A clean report doesn't cover these. Someone on your side must own and test them. |
| **Carve-outs (subservice organizations)** | Parts of the service run by another company and excluded from the report | The risk moved, it didn't disappear. You may need that company's report too. |
| **Gap to today (bridge letter)** | A management-signed, unaudited letter covering the time since the report period ended | It's a statement, not an audit. Note the length of the gap. |

**The human check**
- [ ] Every exception the AI lists is found on the cited page
- [ ] Search the report yourself for "exception," "deviation," and "qualified" (AI summaries can skip items)
- [ ] Each CUEC has a named owner on your side
- [ ] The bridge letter period actually reaches today

**Example prompt (example)**
```
From this SOC 2 Type II report, build a table with: report period, opinion,
every exception (quote it and give the page), every CUEC (quote it and give the page),
and every subservice organization that is carved out.
If you can't find an item, write "NOT FOUND". Do not summarize away exceptions.
```

**Real-world signal**
- PCAOB staff reported firms see future uses in summarizing accounting policy and legal documents and in checking whether audit documentation is complete. ([PCAOB, Jul 2024](https://pcaobus.org/documents/generative-ai-spotlight.pdf))
- KPMG says its Audit Chat is used to search, extract, and summarize contract data (VENDOR CLAIM). ([KPMG](https://kpmg.com/us/en/media/news/kpmg-clara-smart-audit-platform.html))

**Practice for free**
- [ ] Real SOC 2 reports are usually confidential, so practice on public documents instead: a public company's privacy policy or published terms of service, or a public government audit report
- [ ] Build the table above for "who is responsible for what" (the CUEC idea applies to any shared-responsibility document, e.g., a cloud provider's public shared responsibility page)

---

## 5. Policy-to-control and control-to-framework mapping (gap analysis)

**What it speeds up**
- A first pass at "which requirement does this policy sentence cover?" and "which requirements have nothing mapped?"

**Workflow**

| Input | AI step | Human check | Output |
|---|---|---|---|
| Policy statements + a real crosswalk (SCF spreadsheet or a NIST OLIR mapping) | Suggest matches between each policy sentence and crosswalk rows. List requirements with no match. | Accept or reject each match yourself. A word match isn't a control match. Confirm "covered" items actually have an operating control, not just policy text. | Mapping table with status: covered / partial / gap |

**Free, real crosswalks to anchor the AI**
- **Secure Controls Framework (SCF):** free Excel/CSV or OSCAL JSON download, maps to 200+ frameworks, also on GitHub with no registration. ([SCF](https://securecontrolsframework.com/free-content/scf-download))
- **NIST OLIR:** free crosswalks from CSF 2.0 to ISO 27001, SP 800-53, and CIS. ([NIST OLIR](https://csrc.nist.gov/projects/olir))

**Why anchor:** an AI asked to map "from memory" can invent control IDs. Give it the crosswalk rows and ask it to choose only from those.

**The human check**
- [ ] Every ID in the output exists in the crosswalk file
- [ ] "Partial" is used honestly (policy says it, nobody does it = partial at best)
- [ ] Gaps are confirmed by a second pass, not just by "the AI found no match"

**Example prompt (example)**
```
Here are 10 policy statements and 40 rows from the SCF spreadsheet (ID, control, NIST CSF 2.0 column).
For each statement, pick up to 2 SCF rows from this list ONLY, and say covered / partial / no match.
Then list SCF rows that no statement covers.
```

**Real-world signal (vendor material)**
- An audit supervisor at FlowServe told Workiva the team combined CSRD, the California privacy law, and GDPR requirements into one view to see overlaps and gaps (customer story). ([Workiva](https://www.workiva.com/blog/gen-ai-impact-internal-audit))
- Optro/AuditBoard says machine learning suggests links between controls and framework requirements and finds duplicate issues (VENDOR CLAIM). ([AuditBoard](https://soxhub-site.netlify.app/platform/ai/))

**Practice for free**
- [ ] Take 10 sentences from a public company's security policy
- [ ] Map them yourself using SCF, then ask an AI to do it, then compare
- [ ] Write down each disagreement and who was right

---

## 6. Evidence review and anomaly flagging

**What it speeds up**
- Triage of large evidence sets: change tickets, access review sign-offs, user lists
- Reading the free-text parts (ticket descriptions, approval comments) that formulas can't

**The key rule:** **AI flags, the auditor tests.** A flag is a lead, not an exception. Every flagged item is re-checked against source evidence before it goes in the work papers.

**Workflow**

| Input | AI step | Human check | Output |
|---|---|---|---|
| Change tickets export (approved tool, sanitized where possible) | Read the free-text fields and flag tickets where: approval came after deployment, the approver is the requester, "emergency" is used without a reason, or test evidence is missing | Pull each flagged ticket from the source system. Confirm or clear. Also spot-check unflagged tickets (the AI misses things too). | Exception list with ticket references and confirmed status |
| Active user list + HR termination list | **Don't use an LLM for this.** Do an exact match on employee ID with a spreadsheet lookup or a short script. | Check name/ID mismatches by hand. Confirm each "active leaver" in the system itself. | List of terminated users with active access |
| Quarterly access review sign-offs | Summarize reviewer comments; flag reviews approved with zero changes across many users, or signed by someone reviewing their own access | Inspect the review evidence and timestamps yourself | Notes for testing |

**When a script or spreadsheet beats an LLM**

| Task | Better tool | Why |
|---|---|---|
| Matching user lists to HR terminations | Spreadsheet lookup (XLOOKUP) or a short script | Exact, repeatable, every row, no guessing |
| Comparing dates (approved before deployed?) | Spreadsheet formula | Arithmetic should be exact |
| Counting, totals, duplicates | Spreadsheet / pivot table | LLMs can miscount long lists |
| Sample selection | Random number with a recorded seed | Has to be re-performable |
| Reading free-text justifications, grouping comments by theme | LLM | That's where language models actually help |
| Writing the script itself | LLM drafts, human reads and tests it | The auditor should be able to explain every line |

**Data confidentiality**
- [ ] Real access lists and HR data contain personal data. Use only firm-approved tools, never a free consumer account.
- [ ] Remove names and use IDs where the test allows it
- [ ] For practice, make a fake dataset (20 made-up users, 5 made-up leavers)

**Example prompt (example, made-up data)**
```
Below are 30 made-up change tickets (ID, requester, approver, approval date,
deploy date, type, description). Flag tickets where approver = requester,
approval date is after deploy date, or type = emergency with no reason given.
Return ticket IDs and the rule each one broke. Do not guess at missing fields; mark them MISSING.
```
Then check the date rule yourself with a spreadsheet formula and compare.

**Practice for free**
- [ ] Build a fake 20-user list and a fake 5-person leaver list in a spreadsheet
- [ ] Find the active leavers with XLOOKUP first, then ask an AI to do it, and compare
- [ ] Note which errors each method made

## Links
- Overview: [Overview and guardrails](01-overview-and-guardrails.md)
- Previous: [Planning and fieldwork (use cases 1-3)](02-planning-and-fieldwork.md) · Next: [Reporting, monitoring and auditing AI (use cases 7-9)](04-reporting-monitoring-and-auditing-ai.md)
- Sources: [sources.md](sources.md)
