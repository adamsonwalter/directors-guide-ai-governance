# Director's Guide to AI Governance OKF Bundle — Knowledge Projection

| Field            | Value                                                 |
|---|---|
| Generated        | 2026-07-03T03:05:05Z |
| Scope            | master (all concepts) |
| Concepts included| 19 |
| Log head         | 2026-07-03 |
| Sync status      | Current |

> **UPLOAD INSTRUCTIONS**: Upload THIS FILE ONLY to your cloud LLM Project
> (Gemini Gem, Claude.ai Project, ChatGPT Project). Do NOT upload index.md,
> log.md, or individual concept files alongside it — this file already
> contains the ontology and all concepts.
> To update: regenerate this file and replace the existing upload.
> ONE FILE IN = ONE FILE OUT.

## §0 Ontology

> This file is maintained by agents (ENRICHMENT_AGENT, ONTOLOGY_AGENT) and by humans.
> It is the authoritative registry for this bundle. All agents MUST consult it before
> creating a new `type`, registering a new relationship, or adding tags.
> To extend the ontology: add an entry in the correct section below and update `timestamp`.
> Never delete entries — deprecate them (see §DEPRECATED TYPES).

---

# Type Registry

All valid values for the `type` frontmatter field in this bundle.
Agents MUST reject or flag any concept using a `type` not listed here,
and propose an addition via the ONTOLOGY_AGENT (see §EXTENDING).

## Core Knowledge Types

| Type | Description | Typical Body Sections |
|---|---|---|
| `Concept` | A discrete idea, entity, or domain term. | Schema, Examples, Citations |
| `Playbook` | Step-by-step procedure for a known task. | Trigger, Steps, Outcome |
| `Decision` | A recorded decision with context and rationale. | Context, Options, Chosen, Rationale |
| `API Endpoint` | An external or internal API surface. | Schema, Authentication, Examples |
| `Metric` | A measurable quantity with definition and source. | Formula, Source, Caveats |
| `Reference` | A pointer to an external source or document. | Summary, Citations |
| `Glossary Term` | A domain vocabulary definition. | Definition, Related Terms |
| `Person` | A named individual (role-based, not PII). | Role, Expertise, Related Concepts |
| `Organisation` | A company, team, or institution. | Description, Relationships |
| `Event` | A time-bound occurrence. | Date, Participants, Outcome |
| `Dataset` | A named collection of data. | Schema, Source, Access |
| `System` | A software system, platform, or tool. | Description, API Endpoint refs |
| `Process` | A recurring business or technical workflow. | Steps, Actors, Inputs, Outputs |

## Memory & Governance Types (system-managed)

> NOTE (v2.0): `Inference`, `Loop Health Report`, `Decay Report`, and
> `Contradiction Record`, plus the `confidence`/`memory_tier` fields, belong to
> the OPTIONAL T3 cognitive layer. A default (T1/T2) bundle does not use them.
> Field and rule definitions live in `optional/ontology-ext.md`.

| Type | Description | Created By |
|---|---|---|
| `Ontology` | This file. The bundle's type and relationship registry. | Human / ONTOLOGY_AGENT |
| `Stub` | A placeholder for a known gap. Confidence 0.0. | ENRICHMENT_AGENT (gap-finder) |
| `Inference` | A relationship or claim derived by an agent from existing concepts. | CONSUMPTION_AGENT |
| `Agent Instruction` | An instruction file for agent behavior (ALL CAPS .md files). | Human |
| `Loop Health Report` | Periodic diagnostic snapshot of bundle health metrics. | LOG_AGENT |
| `Decay Report` | List of stale, isolated, or low-confidence concepts. | CONFORMANCE_AGENT |
| `Contradiction Record` | A logged contradiction event and its resolution. | ENRICHMENT_AGENT |

## Project-Specific Types

> Add domain-specific types below as the bundle grows.
> Format: `| Type | Description | Typical Body Sections |`

| Type | Description | Typical Body Sections |
|---|---|---|
| `Erratum` | A documented factual error or material omission in the source Guide, paired with the canonical/corrected position and a confidence grade (CONFIRMED / UNSETTLED / REASONED VIEW). Used so the bundle does not silently inherit the source document's mistakes. | Guide Statement, Canonical Position, Why It Matters, Confidence |

---

# Relationship Taxonomy

Cross-links between concepts carry meaning inferred from surrounding prose.
This taxonomy standardises that meaning for agents and human readers.

Agents SHOULD annotate links with a relationship label in the surrounding prose.
The label does NOT appear in the markdown link syntax — it appears as natural language.

| Relationship | Direction | Prose signal | Example |
|---|---|---|---|
| `depends-on` | A → B | "requires", "built on", "cannot run without" | System A depends on API B |
| `implements` | A → B | "implements", "is an instance of", "follows" | Playbook implements Process |
| `contradicts` | A ↔ B | "disputes", "conflicts with", "challenges" | Decision A contradicts Metric B |
| `supersedes` | A → B | "replaces", "supersedes", "updates" | Concept A supersedes Concept B |
| `references` | A → B | "see", "refer to", "documented in" | Playbook references Dataset |
| `related-to` | A ↔ B | "related", "connected", "associated" | Concept A related to Concept B |
| `part-of` | A → B | "belongs to", "is part of", "component of" | Metric is part of System |
| `derived-from` | A → B | "derived from", "based on", "calculated using" | Metric derived from Dataset |
| `authored-by` | A → B | "authored by", "written by", "maintained by" | Playbook authored by Person |
| `governs` | A → B | "governs", "constrains", "regulates" | Ontology governs all Concepts |

---

# Tag Taxonomy

All valid tags for the `tags` frontmatter field.
Tags are lowercase, hyphenated. Agents MUST use registered tags.
Unregistered tags trigger a Type Orphan gap flag (T3 only; see `optional/LLM_WIKI.MD` §GAP-FINDING).

## System Tags (reserved)

| Tag | Meaning |
|---|---|
| `system` | Bundle infrastructure: ontology, instructions, health reports |
| `governance` | Policies, rules, constraints |
| `stub` | Incomplete / placeholder concept |
| `review-required` | Needs human or agent verification |
| `archived` | Superseded or deprecated |
| `inference` | Agent-derived, not directly sourced |
| `disputed` | Contains an unresolved contradiction |

## Domain Tags

> Add project-specific tags below as the bundle grows.
> Format: `| tag-name | meaning |`

| tag-name | meaning |
|---|---|
| `ontology` | Concepts relating to ontology design and structure |
| `operating-model` | Operating model framework components |
| `foundations` | AI Governance Foundations topics |
| `technology` | Technology trends, categories, and tokenomics |
| `regulatory` | Board obligations, directors' duties, and legal landscape |
| `risk` | Opportunities and risks of AI adoption |
| `strategy` | AI strategy and alignment with organisational goals |
| `structure` | AI governance structures, roles, and responsibilities |
| `practices` | Risk management frameworks, controls, and vendor oversight |
| `enablers` | Enablers such as technology infrastructure, literacy culture |
| `case-study` | Real-world organisation case studies |
| `checklist` | Practical checklists for SME and NFP boards |
| `privacy` | Privacy Act 1988 (Cth) and ADM-disclosure specific concepts |
| `errata` | Concepts recording a hard error or gap in the source Guide and its correction |
| `appendix` | Concepts sourced from the Guide's Appendices (A–D) |


---

# Concept Hierarchy Rules

OKF does not enforce a taxonomy, but this bundle follows these hierarchy conventions
to keep the directory structure navigable:

1. **Subdirectory = semantic group.** Group related concepts under a subdirectory
   when three or more concepts share a tag or parent type.

2. **No more than three levels deep.** `root/domain/subdomain/concept.md`.
   Deeper nesting degrades traversal. Flatten if you hit four levels.

3. **Stub concepts live in `stubs/`.** All `type: Stub` files go here until filled.
   When a stub is filled (content added, confidence > 0.50), ENRICHMENT_AGENT moves
   the file to its correct semantic subdirectory.

4. **Reports live in `reports/`.** All `type: Loop Health Report` and `type: Decay Report`
   files go here. Excluded from the main index.md sections; listed under `## Reports`.

5. **Archived concepts live in `archive/`.** All superseded concepts are moved here
   after supersession. They retain their frontmatter and body. They are excluded from
   active index.md sections but included in `## Archive` for auditability.

---

# Validation Rules

CONFORMANCE_AGENT checks these rules in addition to OKF v0.1 base conformance (§9):

| Rule | Check | Severity |
|---|---|---|
| V1 | Every concept's `type` is registered in this Ontology | ERROR |
| V2 | Every concept's `tags` are registered in this Ontology | WARNING |
| V3 | No concept has `confidence` without `confidence_sources` | WARNING |
| V4 | Every `type: Stub` concept is in the `stubs/` subdirectory | WARNING |
| V5 | Every `type: Inference` has `inferred_from` listing at least one source | ERROR |
| V6 | No concept has `superseded_by` without a reciprocal `supersedes` in the target | ERROR |
| V7 | Every contradiction comment `<!-- CONFLICT -->` has a corresponding LOG entry | WARNING |
| V8 | This `ontology.md` file has `memory_tier: semantic` and `confidence: 1.0` | ERROR |

---

# Deliverable Parity Contracts

> Most derived output never needs this section: `projections/` files are **regenerated in full**
> every time PROJECTION_AGENT runs, so they cannot silently drift. This section exists for a
> narrower, riskier case — a **hand-authored, self-contained interactive artifact** (an HTML/JS
> decision tool, a dashboard, a slide-deck generator, an embedded lookup table, etc.) that carries
> its **own denormalized snapshot** of one or more concept subdirectories, because it needs custom
> rendering PROJECTION_AGENT's flat-markdown output cannot produce. That snapshot is hand-edited,
> not regenerated — so the moment a concept is added, retired, or renamed and the deliverable is
> not touched in the same pass, it silently goes stale. Register a contract here **the first time**
> such a deliverable is built, and CONFORMANCE_AGENT will catch drift automatically from then on
> instead of relying on someone noticing.

**Format** — one row per deliverable that embeds a source-concept snapshot:

| Field | Meaning |
|---|---|
| `Contract ID` | Short slug identifying the contract. |
| `Deliverable file` | Path to the artifact, relative to bundle root (typically under `deliverables/`). |
| `Source scope` | The concept subdirectory, or a `type`/`tag` filter, being mirrored. |
| `Identity key` | How ONE record in the deliverable maps 1:1 to ONE source file (a lettered/numbered `id`, a filename slug, a title match…). CONFORMANCE_AGENT diffs on this key, not just a count, so it can name exactly which record is missing or extra — not just report "counts don't match". |
| `Severity` | `ERROR` (the deliverable ships broken or misleading to an end user/client) or `WARNING` (cosmetic drift only). Default to `ERROR` for anything client-facing. |

| Contract ID | Deliverable file | Source scope | Identity key | Severity |
|---|---|---|---|---|
| *(none at bundle initialisation — register the first time a hand-authored deliverable snapshots concept data; see worked example below)* | — | — | — | — |

**Worked example** (illustrative only — this is not a live contract in this seed ontology; shown
so a domain builder can copy the pattern exactly):

| Contract ID | Deliverable file | Source scope | Identity key | Severity |
|---|---|---|---|---|
| `scenario-decision-map` | `deliverables/app-1-7-trigger-test-decision-map.html` | `scenarios/scenario-*.md` (one row per file) | Scenario letter — the concept's `title: "Scenario X — …"` matched against the deliverable's embedded `id` field | ERROR |

This is the exact fix applied retroactively to the `privacy-act-okf` bundle after its
`scenarios/` directory grew to nine concepts (A–I) while its interactive decision-map deliverable
had silently stalled at seven (A–G) for several days — an *additive* new Scenario concept did not
read, on a first pass, like it triggered "update the deliverable", because the old instruction was
conditional ("if the new material changes scenarios…") rather than unconditional on any create/
retire event. See CHANGELOG.md [2.2.0] and AGENTS.MD §ENRICHMENT_AGENT / §CONFORMANCE_AGENT for
how this is now enforced unconditionally, at write time and at audit time, for every bundle built
from this kit — not just the one where the gap was first found.

---

# ONTOLOGY_AGENT — Extension Protocol

When ENRICHMENT_AGENT encounters an unregistered `type` or `tag`, it does NOT silently
accept it. It triggers ONTOLOGY_AGENT:

```
AGENT: ONTOLOGY_AGENT
TRIGGER: Unregistered type or tag detected during ENRICHMENT or CONFORMANCE

ACTIONS:
  1. Propose the new type or tag entry in the correct section of ontology.md.
  2. Include: name, description, typical use, example concept.
  3. Write the proposed addition as a <!-- PROPOSED: --> comment at the bottom
     of the appropriate section in ontology.md.
  4. Set `review_required: true` in ontology.md frontmatter.
  5. LOG_AGENT records: **Ontology Proposal**: [type/tag name] — awaiting approval.
  6. HALT. Do not write the concept using the unregistered type until approved.

APPROVAL:
  A human (or agent with explicit authority) removes the <!-- PROPOSED: --> comment
  and promotes the entry to the active table. Removes `review_required: true`.
  LOG_AGENT records: **Ontology Extension**: [type/tag name] — approved and registered.

REJECTION:
  Human removes the <!-- PROPOSED: --> comment without promoting it.
  ENRICHMENT_AGENT maps the rejected concept to the nearest registered type.
```

---

# Deprecated Types

Types that were once valid but are no longer in use. Agents encountering these
types in existing concept files should flag for migration, not auto-migrate.

| Deprecated Type | Replaced By | Migration Note |
|---|---|---|
| *(none at initialisation)* | — | — |

---

# Ontology Version History

| Version | Date | Change |
|---|---|---|
| 0.1 | 2026-06-19 | Initial ontology for bundle bootstrap kit |
| 0.2 | 2026-07-03 | Added **§Deliverable Parity Contracts** — an opt-in registry for hand-authored interactive deliverables that embed a denormalized snapshot of a concept subdirectory. Generalises a bundle-specific fix (`privacy-act-okf` scenario/decision-map drift) into a reusable kit pattern. Empty template + one illustrative worked example; no live contract in this seed ontology. Paired with AGENTS.MD changes enforcing it at write time (ENRICHMENT_AGENT) and audit time (CONFORMANCE_AGENT CHECK_7). No new types/tags. |
| 0.3 | 2026-07-03 | Canonical re-ingestion of the full source PDF/extracted text (56 pages) against `directors-guide-hard-error-register.md`. Added type `Erratum` (Project-Specific Types) and tags `privacy`, `errata`, `appendix` (Domain Tags) — ONTOLOGY_AGENT extension proposed and approved same-session under direct instruction from the bundle owner. Registered a `checklists/hard-error-register.md` concept (type `Erratum`, one row per HE-1…HE-7 finding) so the bundle carries a permanent correction layer instead of silently repeating the Guide's page 39 / Table 4 / p.49 misstatements. Filled two whole-section gaps that existed only as a single generic bullet or not at all: the Privacy Act ADM-disclosure duty (new `foundations/privacy-act-adm-disclosure.md`) and Part 3 – Measuring AI Returns (new `operating-model/measuring-ai-returns.md`), plus Appendix A's full regulatory obligations table (new `foundations/regulatory-obligations-appendix-a.md`) and Appendix B resources. Added the previously-missing fifth case study, Telstra (`case-studies/telstra-case-study.md` — present in the Guide body p.45 but omitted from its own Contents page and from this bundle). Corrected two case-study drift errors against source (CBA model-governance structure; Westpac literacy-program mechanics, which had been paraphrased into content not in the Guide). Expanded the glossary from 6 to the Guide's full ~25-term Appendix D, and rebuilt the SME/NFP checklist to mirror Appendix C's four-category table verbatim rather than an invented 5-step list. See `log.md` for the full per-file mutation record. |

## AI Governance Enablers

*Type: Concept | Tags: governance, operating-model, enablers | Updated: 2026-07-03T02:55:56Z*

# AI Governance Enablers

Beyond structures and practices, successful AI governance depends on key enablers that support responsible adoption and mitigate risks.

## AI Technology and Supporting Infrastructure

A pre-condition of significant organisational investment in AI is enhancing the underlying digital, data, and technology infrastructure (Figure 4): **computing power** (cloud infrastructure or in-house servers), **high-quality data sets** (securely protected organisational data), and **networking** (high-speed connectivity). Boards should receive assurance the infrastructure can support current and planned AI workloads, including that management understands how non-linear growth in compute demand affects capital allocation and operating expenditure.

## AI Literacy and Responsible Culture

An organisational culture that embraces AI knowledge, literacy, and responsible use is critical, particularly given the high incidence of shadow AI. Boards should support training programs to raise AI literacy across the workforce (and volunteers, for many NFPs) and foster an ethical culture of compliance, with the board itself potentially setting a 'tone from the top'.

## Stakeholder Engagement

Organisations must remain sensitive to the impact of AI on internal and external stakeholders:
* **Customers and clients**: Transparency about AI deployment, including use of personal information, consistent with Privacy Act requirements; targeted consultation may be appropriate for sensitive deployments (e.g. a care-sector NFP), though this is unlikely to be feasible for organisations with very large customer bases.
* **Employees**: Consultation, training and support should accompany widespread AI adoption. HTI's *Invisible Bystanders* research found worker engagement is often limited despite employees' critical role in successful implementation; industrial relations laws may also require consultation on AI changes materially affecting work or employment.
* **Suppliers**: Consultation may be appropriate where AI systems alter the supplier relationship or use supplier data.
* **Broader stakeholders**: Larger organisations' stakeholders extend to the community, government and regulators — key to reputation and social licence, particularly where AI trials affect large numbers of customers or employees.

## Related Concepts
* [Case Study: Westpac – Building Senior Leadership's AI Literacy](/case-studies/westpac-case-study.md)
* [Case Study: Telstra – AI Governance Operating Model in Action](/case-studies/telstra-case-study.md)

---
## AI Governance Practices

*Type: Concept | Tags: governance, operating-model, practices | Updated: 2026-07-03T02:55:56Z*

# AI Governance Practices

Boards must oversee how AI-specific risks are identified, monitored, and managed through the organisation's existing risk management frameworks and controls.

## Risk Management Frameworks

AI risks should not be treated in isolation. Instead, they should be integrated into the organisation's enterprise risk management (ERM) framework. Key practices include:
* Conducting regular AI stocktakes and risk assessments before deployment.
* Establishing monitoring processes for algorithmic drift, bias, and performance.
* Integrating AI risk management with cyber security and data governance.

### Common controls by risk (Table 5)

| Risk / risk driver | Common controls |
|---|---|
| Cyber security | Rapid patching; updated existing controls (encryption, access controls, monitoring, incident response); AI threat modelling, red-teaming, penetration testing. |
| Privacy | Privacy impact assessments for AI systems; privacy policies/notifications addressing AI-specific data practices; secure data throughout the AI system lifecycle. |
| Output quality | Model testing, validation and fine-tuning; staff training on AI limitations; human review of outputs in high-stakes contexts. |
| Output explainability | Documentation of model design, inputs and intended use; processes for explaining AI-driven decisions to affected individuals. |
| Fairness and discrimination | Representativeness/quality assessment of training data; fairness and bias testing across protected attributes; AI impact assessments. |
| Shadow AI | Acceptable use policies for employee AI use; staff training on AI risks and obligations; monitoring of AI use across networks. |
| Agentic AI | Documented risk appetite on permitted agent tasks; access controls limiting what agents can read, modify or action; logging and auditability of agent actions. |

The HTI Corporate Leaders Survey found cyber security is the most concerning risk area for board oversight of AI, and boards typically consider cyber security and data governance risks in tandem given their interdependence with AI risk.

## Vendor and Supplier Risk Management

Most organisations adopt AI through third-party vendors and Software-as-a-Service (SaaS) products, and risk can extend to a "4th party" layer where a vendor's models are hosted on hyperscaler cloud infrastructure, creating supply-chain concentration risk. While these risks may originate with vendors, accountability remains with the organisation. Boards should oversee:
1. What testing/trialling of the vendor's products was undertaken prior to adoption, and whether results are consistent with the organisation's AI risk appetite.
2. The provider's location, ownership structure, interdependencies with other IT infrastructure, and fallback arrangements in the event of failure.
3. Monitoring of the provider's data governance and cyber security posture.
4. Whether performance and data security are reflected in contractual obligations — reporting, incident notification, and testing rights.

## AI policies and processes

The board should have confidence management maintains an **AI inventory/register** (tracking all approved AI systems/tools and key information about them) and a central **AI policy** setting out rules and processes for AI use, including which systems are approved or prohibited — often owned by a senior manager accountable for AI. The NAIC's AI policy guide and template provides a practical starting point.

## Privacy and transparency

Organisations should review privacy policies and processes for AI-specific risks — for example, AI agents collecting personal information during interactions, or personal information used to train in-house models. From **10 December 2026**, organisations subject to the Privacy Act using ADM systems must meet new disclosure requirements — see [Privacy Act ADM Disclosure Duty](/foundations/privacy-act-adm-disclosure.md) for the corrected three-limb test (the Guide's own summary of this duty on this page is inconsistent with its Appendix A wording — see [Hard-Error Register — HE-1](/errata/privacy-act-hard-error-register.md)). Some organisations go beyond minimum disclosure — CBA's *Our Approach to Adopting AI* (2025) report is cited as a notable transparency example.

## Related Concepts
* [Case Study: Atlassian's Responsible Tech Review](/case-studies/atlassian-case-study.md)
* [Case Study: Commonwealth Bank of Australia (CBA)](/case-studies/cba-case-study.md)
* [AI Governance Structure](/operating-model/governance-structure.md)
* [AI Strategy Alignment](/operating-model/strategy.md)
* [AI Opportunities and Risks](/foundations/opportunities-and-risks.md)
* [The Role of the Board and the Regulatory Landscape](/foundations/board-role-regulatory-landscape.md)
* [Privacy Act ADM Disclosure Duty](/foundations/privacy-act-adm-disclosure.md)

---
## AI Governance Structure

*Type: Concept | Tags: governance, operating-model, structure | Updated: 2026-07-03T02:55:56Z*

# AI Governance Structure

Organisations need clear structures to manage and monitor AI. While dedicated AI governance bodies may not be necessary for every organisation, the board must have clear visibility over how AI is managed.

## Roles and Responsibilities

The board should work with management to map AI-related responsibilities across the organisation, including:
* Clarifying who is accountable for AI risk assessments, data controls, and model performance monitoring.
* Regularly reviewing and updating these roles in line with changing business operations and technological developments.

APRA's 2026 guidance sets an expectation, for its regulated population, that governance structures encompass "ownership and accountability across the AI lifecycle, from design and development through to deployment, monitoring and decommissioning" — a yardstick the Guide treats as relevant to all organisations. At minimum, most large organisations should have a senior executive (or executives) accountable for AI governance — in smaller organisations this may be the CEO; in larger ones a standalone role (Chief AI Officer, Chief Data Officer) or shared across the CTO/CIO and other senior roles.

### Who holds AI responsibility today (Box 10)

The HTI Corporate Leaders Survey asked which role(s) are primarily responsible for ensuring AI systems operate safely, lawfully and responsibly: CEO/Managing Director (52.9%), CTO/CIO/Chief Data Officer (46.1%), a legal or compliance executive (31.8%), a risk-focused executive (23.4%), and the board (21.8%). The CEO was more likely identified as responsible in small/medium organisations; a technology-focused executive was more likely in large organisations (200+ staff).

### Decision-making and escalation

Organisations may use existing governance processes or establish a dedicated, often management-led AI committee — which can bring cross-functional expertise, support well-rounded decisions, build internal capability, and speed up decision-making by centralising approval of new AI systems and use cases. In smaller organisations it may be more practical to rely on existing governance processes rather than a dedicated committee.

## Board AI Literacy

A critical enabler of effective AI governance is the board's own AI literacy. Directors should proactively build their understanding of AI concepts (such as generative vs agentic AI, and tokenomics) to ask management the right questions and seek appropriate assurance. Boards lacking these skills can undertake training, recruit members with relevant skills/experience, or establish an AI expert advisory committee.

## Related Concepts
* [Case Study: Canteen – Listening to the Voice of Members](/case-studies/canteen-case-study.md)
* [Case Study: Westpac – Building Senior Leadership's AI Literacy](/case-studies/westpac-case-study.md)
* [Case Study: Telstra – AI Governance Operating Model in Action](/case-studies/telstra-case-study.md)
* [AI Governance Practices](/operating-model/governance-practices.md)
* [AI Strategy Alignment](/operating-model/strategy.md)
* [The Role of the Board and the Regulatory Landscape](/foundations/board-role-regulatory-landscape.md)

---
## AI is a Transformative Technology

*Type: Concept | Tags: governance, foundations, technology | Updated: 2026-07-03T02:55:56Z*

# AI is a Transformative Technology

Artificial Intelligence (AI) is a general-purpose technology that is increasingly reshaping how Australian organisations operate, compete, and create value. It is both a significant transformational opportunity and a material source of risk.

## Key Categories of AI

AI is not a single technology. Organisations are using a variety of AI systems with different capabilities, risk profiles, and governance implications:

* **Traditional AI**: Trained to perform defined, specialised tasks to solve specific problems (narrow AI). Examples include machine learning, expert systems, recommendation algorithms, facial recognition, and automated decision-making.
* **Generative AI**: Can generate new content, including text, audio, video, and code, and can be used for a broad range of purposes (general-purpose AI). Examples include large language models (LLMs).
* **Agentic AI**: Uses generative AI in combination with other systems and tools to plan and act across multiple steps to achieve defined goals. It can operate with varying degrees of autonomy and human oversight.

## Governance Implications

Unlike legacy software systems built with explicit rules coded by developers, AI systems are not programmed with fixed rules. Instead, they are trained on data to identify patterns. This makes AI systems less predictable and more difficult to explain, a challenge that is amplified in agentic AI systems.

## Tokenomics and Cost

AI tokens are the units LLMs use to process information (tokenisation). The cost of using an AI system is generally priced on a per-token basis. Input tokens (what is sent) and output tokens (what is generated) are charged separately, with output tokens often costing more due to computational demand. Boards must monitor these costs as usage grows.

## Shadow AI and Embedded AI

AI is often embedded within third-party Software as a Service (SaaS) products without clear disclosure. Furthermore, employees may use AI tools on an unapproved ('shadow') basis without formal oversight, introducing hidden data privacy and cyber risks.

## AI adoption in Australia

HTI's Corporate Leaders Survey (419 directors, senior executives and decision-makers, late 2025) found 90% of surveyed organisations are using or planning to use AI, up from 64% in 2022. Adoption varies by industry (highest in retail trade, and health and education) and by size — the National AI Centre found 82% of organisations with 200–500 employees had adopted AI in 2025, compared with 33% of micro-businesses. Separately, NAB research found 42% of SMEs are now using AI, led by property services, finance and insurance, and business services. Agentic AI use is also growing: 32.5% of organisations reported at least one agentic AI use case, with a further 12.9% planning adoption (deployed most in IT/security, marketing/sales, and back-office activities); a 2026 Deloitte report found 23% of businesses already using agentic AI to at least a moderate extent, expected to rise to 74% within two years.

## Terms that can signal AI use (Box 3)

Directors should be alert to terminology that may indicate AI use within the organisation, including where AI is embedded in third-party products without clear disclosure: **model or algorithm**, **expert systems**, **training data**, **natural language systems**, **process automation**, **automated decision-making**, and **agents**.

## How AI is used by organisations

HTI identifies four common use-case categories to help boards assess governance maturity against level of ambition:

* **Tactical tools** — individual/ad hoc staff use for localised productivity gains (e.g. an AI assistant drafting correspondence or summarising documents).
* **Process transformation** — AI redesigning specific end-to-end processes for measurable efficiency gains (e.g. a customer-facing AI agent handling routine queries).
* **Systematic uplift** — AI applied to core enabling infrastructure or standard ways of working at scale (e.g. modernising legacy code, patching cyber vulnerabilities).
* **Organisational transformation** — AI used to reshape the operating model itself (e.g. redesigning HR and technology functions to work alongside AI agents).

## Related Concepts
* [Glossary of AI Governance Terms](/checklists/glossary.md)
* [Appendix C: SME and NFP Director Checklist](/checklists/sme-nfp-checklist.md)
* [AI Opportunities and Risks](/foundations/opportunities-and-risks.md)
* [Measuring Value and Returns from AI](/operating-model/measuring-ai-returns.md)

---
## AI Opportunities and Risks

*Type: Concept | Tags: governance, foundations, risk | Updated: 2026-07-03T02:55:56Z*

# AI Opportunities and Risks

Deploying AI systems requires boards to navigate a complex dynamic of opportunity and risk, balancing technological innovation with organisational responsibility.

## Opportunities

* **Reduced errors and improved quality**: AI can be prone to errors when inputs fall outside training data, but often outperforms other approaches — including many human experts — for well-defined, repetitive, pattern-recognition tasks.
* **New products and services**: AI supports design, prototyping and testing of new products, and can help maintain legacy products where expertise is scarce.
* **Improved customer experience**: Natural-language and scale capabilities can reduce wait times, synthesise information, and deliver more personalised experiences.
* **Improved employee experience**: Reduces time on low-value administrative tasks and can guide workers through complex tasks and problem-solving.
* **Improved productivity**: Reduces administrative burden through automation and helps teams analyse trends, summarise information and generate content — among the primary benefits organisations report from AI adoption.

Organisations that invest strategically in AI capabilities reportedly outperform slower-adopting peers, with stronger returns from AI systems. Under-investment risks falling behind on cost, product/service innovation, customer service and talent retention. See [Measuring Value and Returns from AI](/operating-model/measuring-ai-returns.md) for how boards should evaluate whether these benefits are actually being realised.

### Opportunities and challenges for SMEs and NFPs

Smaller organisations can deploy accessible, low-cost AI tools — e.g. AI features within accounting products, social media advertising tools, or fundraising-pattern insights for charities. Challenges include a lack of dedicated IT/data specialists, burdensome subscription costs, staff training taking a backseat to operational concerns, heightened data governance and privacy risk where vulnerable-community data is involved, and limited capacity to respond to elevated cyber risk (e.g. patching legacy systems).

## Where AI risks and harms come from (Table 3)

| Source of risk | Summary and examples |
|---|---|
| **AI systems failure** | Where AI systems create harm because they fail to perform as intended: poor or biased system performance, system fragility/unreliability, security failures or vulnerabilities. |
| **Malicious or misleading use** | Where AI systems are deliberately used to create or amplify harm: scams and fraud, misinformation at scale, AI-powered cyber attacks, price or service discrimination. |
| **Inappropriate or reckless use** | Where AI is used without sufficiently considering the risk of harm: facial recognition without authority, mass surveillance, excessive workforce deployment causing loss of critical skills, overuse of generative AI causing significant energy consumption/emissions. |

## Key areas of AI-related risk (Table 4)

| Risk | Description |
|---|---|
| **Cyber security** | New threat vectors (convincing phishing/deepfakes) and amplified existing vulnerabilities (prompt manipulation, training data poisoning), often compounded by gaps in basic access controls. |
| **Privacy and data governance** | Applies to both inputs and AI **outputs** containing personal information, including inferred or incorrect information. Risks include use of personal information beyond its original purpose and inadvertent exposure of sensitive data. |
| **Output issues: quality and explainability** | Generative AI is prone to 'hallucinations' — coherent but incorrect outputs — because it generates responses probabilistically. Explainability is a related challenge: it is often not possible to explain how a model reached an output or fully validate its reasoning, which can make it difficult to justify outcomes where a decision has a significant effect on an individual. *(The Guide's own wording here — "legal or similarly significant effects" — imports GDPR Article 22 language rather than the Australian APP 1.7/1.9 "significantly affect... rights or interests" test; see [Hard-Error Register — HE-2](/errata/privacy-act-hard-error-register.md).)* |
| **Employee and workforce impacts** | AI may automate some roles/tasks while augmenting others, supporting productivity and new ways of working. |
| **Fairness and discrimination** | AI can inherit and amplify real-world biases, from pre-existing biases, non-representative datasets, or the algorithmic approach itself, producing unlawful or discriminatory outcomes. |
| **Shadow AI** | Staff using public AI tools (e.g. ChatGPT) at work may not realise uploaded information can lose confidentiality, or that outputs may be confidently-stated hallucinations. |

## Agentic AI — potential for elevated risk

Agentic AI inherits generative AI's risks (including hallucination) and adds new ones from its autonomy, complexity and scale: an agent may act in ways not intended or authorised because instructions were unclear, it misinterprets its goal, or it errs during execution. Risk is amplified where agents orchestrate across multiple systems (expanding the attack surface and straining coordination) and where high-autonomy, continuously-operating systems let errors go undetected and compound over time. Although Australian courts have not yet ruled on AI-agent liability, in Canada the Civil Resolution Tribunal of British Columbia dismissed Air Canada's argument that it was not responsible for misleading statements made by its website chatbot — AI agents are IT systems, not employees or contractors.

## The human impact

AI can disproportionately affect already-vulnerable groups, particularly in decisions about access to products and services — even small errors or biases can cause significant harm at scale. Decisions about reducing headcount versus augmenting the workforce involve trade-offs between efficiency and the value of human contribution, judgement and relationships; how an organisation manages transition, reskilling and redeployment shapes employee trust, retention and its ability to attract talent.

## Sustainability considerations

AI systems have significant lifecycle energy and resource needs, including chip/server manufacture and data centre water use for cooling; environmental impact varies with query type, processing required, model size and the energy sources powering infrastructure. For organisations under Australia's mandatory climate reporting regime, AI-related emissions may be reportable as scope 3 emissions.

## Related Concepts
* [AI Governance Practices](/operating-model/governance-practices.md)
* [AI Strategy Alignment](/operating-model/strategy.md)
* [The Role of the Board and the Regulatory Landscape](/foundations/board-role-regulatory-landscape.md)
* [AI is a Transformative Technology](/foundations/transformative-technology.md)
* [Measuring Value and Returns from AI](/operating-model/measuring-ai-returns.md)
* [Hard-Error Register — Privacy Act / ADM Disclosure Content in the Guide](/errata/privacy-act-hard-error-register.md)

---
## AI Strategy Alignment

*Type: Concept | Tags: governance, operating-model, strategy | Updated: 2026-07-03T02:55:56Z*

# AI Strategy Alignment

The board should approach decision-making on AI and AI-related investments with discipline, ensuring that decisions align with the organisation's overall strategy, values, and purpose.

## Defining Risk Appetite for AI

Given the distinctive risks associated with AI (such as lack of explainability and potential bias), the board should work with management to establish a specific risk appetite for AI. This appetite must be reflected in internal policies and the risk management framework.

## Baseline

Before developing and implementing an AI strategy, good practice is a detailed data inventory, stocktake or mapping exercise of how AI, machine learning and other data tools are used, and which datasets and resources this use relies on — giving the board visibility over existing capabilities, data quality, risks and dependencies so investment decisions are grounded in operational reality. This is particularly important for smaller organisations with limited resources.

## Resourcing and Prioritisation

Effective AI implementation cannot occur in a vacuum. The board must oversee:
* Allocating adequate resources for technology, infrastructure, and human capabilities — recognising larger organisations may need specialist internal teams (data scientists, AI architects, cloud engineers) while smaller organisations are more likely to rely on external resources.
* Ensuring data quality is sufficient to support planned AI models, since poor data governance can result in misleading insights, flawed decisions and unintended biases (e.g. discriminatory profiling or hiring practices).
* Prioritising AI use cases based on strategic value and risk profile rather than pursuing ad-hoc pilots ('AI for AI's sake').

How to measure whether these investments actually deliver value is addressed separately — see [Measuring Value and Returns from AI](/operating-model/measuring-ai-returns.md).

## Related Concepts
* [AI Governance Practices](/operating-model/governance-practices.md)
* [AI Governance Structure](/operating-model/governance-structure.md)
* [AI Opportunities and Risks](/foundations/opportunities-and-risks.md)
* [Measuring Value and Returns from AI](/operating-model/measuring-ai-returns.md)

---
## Appendix A: Regulatory Obligations and AI

*Type: Reference | Tags: regulatory, foundations, appendix | Updated: 2026-07-03T02:55:56Z*

# Appendix A: Regulatory Obligations and AI

*Current as at June 2026.* A range of existing Australian laws are relevant to the
development and use of AI systems — the National AI Plan (December 2025) confirmed
Australia will rely on existing laws rather than a standalone AI statute, while leaving
open targeted reform where regulatory gaps emerge.

## Privacy

The *Privacy Act 1988* (Cth) applies to the collection, use, storage, disclosure and
destruction of personal information, including where personal information is used to
**train, test or use** an AI system. Personal information is broadly defined to include
any information that could identify an individual.

The Privacy Act does **not** apply to all organisations — the small business exemption and
the employee-records exemption both carry material carve-backs and boundaries; see
[Hard-Error Register — HE-3](/errata/privacy-act-hard-error-register.md) rather than
relying on a simple turnover test.

The OAIC has released guidance on the application of the Privacy Act to AI systems,
including *Guidance on privacy and developing and training generative AI models* (23
October 2024) and *Guidance on privacy and the use of commercially available AI products*
(17 January 2025). The Privacy Commissioner has also ruled on the use of AI in the form of
facial recognition technology in the retail sector: see *Bunnings Group Limited and Privacy
Commissioner* [2026] ARTA 130, in which the Administrative Review Tribunal upheld
Bunnings' use of facial recognition technology (Gilbert + Tobin, 6 February 2026).

Since **2025**, the Privacy Act includes a **statutory tort for serious invasions of
privacy**. A person who alleges their privacy has been seriously invaded by another
person (including an organisation) can bring proceedings for breach of this tort — in
practice this could include a serious invasion of privacy using an AI system, such as
biometric or facial-recognition deployment without valid consent.

From **10 December 2026**, organisations covered by the Privacy Act must, in certain
circumstances, include details in their privacy policies about the use of computer
programs to make, or to do a thing substantially and directly related to making, a
decision — required where the decision could significantly affect an individual's rights
or interests and the program uses their personal information. See the dedicated concept:
[Privacy Act ADM Disclosure Duty](/foundations/privacy-act-adm-disclosure.md).

## Consumer protection

The provision of AI-enabled goods or services to consumers in trade or commerce is
subject to the Australian Consumer Law (ACL) (Schedule 2, *Competition and Consumer Act
2010* (Cth)), which prohibits misleading or deceptive conduct, unconscionable conduct, and
false or misleading representations, and contains consumer guarantees and a product
liability regime for defective goods.

In 2025 Treasury reviewed the ACL and found it broadly capable of adapting to AI-enabled
goods and services when read with other relevant laws. In October 2025 the ACCC took
enforcement action against Microsoft Australia under the ACL, alleging it misled about 2.7
million Australian customers when communicating subscription options and price increases
after integrating Copilot into Microsoft 365 plans. The ACCC has separately observed that
retail is using AI chatbots at higher rates than other sectors and advised that chatbot
responses must not be contrary to ACL obligations. Organisations may also mislead
consumers through **'AI-washing'** — making misleading or overstated claims about a
product's AI capabilities — a practice both the ACCC and ASIC have flagged.

## Anti-discrimination

AI system outputs can directly or indirectly discriminate against individuals on
protected attributes, including where training data reflects historical biases.
Commonwealth and State anti-discrimination laws prohibit direct and indirect
discrimination based on protected attributes such as race, sex, age and disability.
Organisations should ensure their use of AI systems does not result in unlawful
discrimination.

## Industrial relations

The *Fair Work Act 2009* (Cth) regulates the employment lifecycle and is triggered where
new technologies materially affect employees. The introduction of AI will often constitute
a **'major workplace change'** under the Fair Work Act, most modern awards and enterprise
agreements where it is likely to have significant effects on employees — changes to roles,
hours, skills requirements or job loss. In those circumstances the employer must undertake
certain steps, including consultation and consideration of measures to mitigate adverse
impacts. Unfair dismissal, redundancy, procedural fairness protections and modern
award/enterprise agreement consultation clauses are all likely to be relevant to AI
deployment.

## Work health and safety

Australia's harmonised work health and safety laws impose a primary duty of care to
ensure, so far as is reasonably practicable, the health and safety of workers and other
persons — a duty that applies when organisations develop, procure or deploy AI systems.
Measures may include incorporating AI-related risks into WHS risk assessments,
consultation and training.

In **2026**, the NSW Parliament amended the *Work Health and Safety Act 2011* (NSW) (via
the *Work Health and Safety Amendment (Digital Work Systems) Act 2026* (NSW)) to add a new
duty to ensure, so far as is reasonably practicable, that workers are not exposed to health
and safety risks arising from the **allocation of work by a digital work system**.

## Duty of care (negligence)

Organisations that use AI systems owe a duty of care to people affected by that use, so as
to avoid causing reasonably foreseeable harm. An organisation may breach this duty where
harm results from foreseeable risks associated with the AI system and the organisation
failed to take reasonable steps to prevent or mitigate those risks. Manufacturers,
distributors and retailers may owe duties of care in negligence for AI-enabled products,
and may also be subject to ACL product liability obligations.

## Environmental / climate reporting

Australia's mandatory climate reporting regime (Part 2M, *Corporations Act 2001* (Cth))
is being phased in by entity size, with Group 1 entities (largest emitters/corporations)
required to disclose from 1 January 2025, and Group 2 and Group 3 entities phasing in from
1 July 2026 and 1 July 2027 respectively; NFPs meeting the size thresholds are included.
Covered entities must prepare climate-related disclosures under **AASB S2** in a dedicated
Sustainability Report within their annual report. AI-related emissions are likely captured
indirectly through scope 2 and scope 3 disclosures — particularly electricity consumption
from data centres and cloud services — requiring assessment and reporting of material
emissions associated with computational infrastructure and third-party AI providers.

## Cyber security

The *Security of Critical Infrastructure Act 2018* (Cth) regulates specified critical
infrastructure assets across key sectors, imposing cyber/information security risk
management and incident reporting obligations. The *Cyber Security Act 2024* (Cth)
mandates minimum cyber security standards for certain internet-connected products,
introduces mandatory reporting of ransomware payments by specified entities, and
establishes a voluntary, limited-use information-sharing framework for significant cyber
incidents.

## Copyright

The *Copyright Act 1968* (Cth) protects original works created by human authors. Using
copyright-protected material to train or operate AI systems may involve acts of
reproduction that infringe copyright, unless the organisation has the copyright holder's
consent, relies on a licensing arrangement, or the use falls within a fair dealing
exception.

## Related Concepts
* [Privacy Act ADM Disclosure Duty](/foundations/privacy-act-adm-disclosure.md)
* [Hard-Error Register — Privacy Act / ADM Disclosure Content in the Guide](/errata/privacy-act-hard-error-register.md)
* [The Role of the Board and the Regulatory Landscape](/foundations/board-role-regulatory-landscape.md)
* [Appendix B: Resources](/checklists/appendix-b-resources.md)

---
## Appendix B: Resources

*Type: Reference | Tags: governance, checklist, appendix | Updated: 2026-07-03T02:55:56Z*

# Appendix B: Resources

## Federal Government

* NAIC, *Essential AI practices*
* NAIC, *AI and Australian law*
* NAIC, *Planning for AI*
* ASD, *Artificial intelligence for small business: Managing cyber security risk*
* OAIC, *Guidance on privacy and the use of commercially available AI products*

## AICD

* *AI use by directors and boards: Early insights*
* *Cyber Security Governance Principles* Version 2 (with the CSCRC)
* *Data Governance Foundations for Boards* (with Allens and Melbourne Business School)
* *Effective board minutes and the use of AI* (with the Governance Institute of Australia)
* *AI Fluency for Directors Sprint* (short course)
* *AI Governance for Directors Webinar Series*
* *Ethics in the Boardroom* 2nd edition (with The Ethics Centre)
* *Cyber Security for Directors* (short course)

## HTI

* *AI Governance Lighthouse Case Study: Telstra*
* *AI Governance Operating Model*
* *Designing AI Governance Structures*
* *People, Skills, and Culture for Effective AI Governance*
* *From Invisible to Involved: A Guide to Worker Engagement on AI*
* *'Invisible Bystanders': How Australian Workers Experience the Uptake of AI and
  Automation*

## Other

* Business Council of Australia, *Adopting AI in the Workplace*
* Governance Institute of Australia, *Governance in the Age of Agentic AI*
* Commonwealth Bank of Australia, *Our Approach to Adopting AI*

## Related Concepts
* [Appendix A: Regulatory Obligations and AI](/foundations/regulatory-obligations-appendix-a.md)
* [Glossary of AI Governance Terms](/checklists/glossary.md)

---
## Appendix C: SME and NFP Director Checklist

*Type: Playbook | Tags: governance, checklist, appendix | Updated: 2026-07-03T02:55:56Z*

# Appendix C: SME and NFP Director Checklist

> Small and medium-sized enterprises (SMEs) and not-for-profits (NFPs) face unique resource
> constraints but must still discharge their duties with due care and diligence when
> adopting AI. Reproduces Appendix C (p.52), which mirrors the "Boards of SMEs and NFPs"
> callout box embedded in each Part 2 section.

## AI Strategy

* Understand where AI is already being used in the organisation, including AI features in
  third-party products and services.
* Discuss the organisation's risk appetite for AI use with management.
* Understand whether new resources and significant investment are required to support AI
  deployment.
* Assess where AI could add value and support strategic objectives, including
  opportunities to enhance existing processes and resources (such as current SaaS
  subscriptions) in a cost-effective way.

## AI Governance Structure

* Assign accountability for AI oversight to an appropriate senior leader.
* Establish a proportionate process for approving the use of AI systems in line with their
  potential impact on the organisation and stakeholders.
* Establish when and how the board will be updated or consulted on AI systems, including
  working with management to develop targeted metrics on AI use, effectiveness, and risks.
* Consider how external assistance may help AI deployment in a cost-effective way.

## AI Governance Practices

* Oversee the development of a practical, accessible AI policy that sets clear boundaries
  for AI use, including restricting the use of unapproved tools with sensitive
  organisational data.
* Discuss potential risks for your organisation in relation to AI, including the process
  for patching cyber and data vulnerabilities.
* Ensure existing risk controls are reviewed to assess whether they effectively manage
  AI-related risks, such as privacy, data governance and cyber security.

## AI Governance Enablers

* Consider whether existing technology and data systems effectively support AI
  deployment, including whether improvements to data collection and quality are needed.
* Form a view of internal capability to effectively use AI and invest in foundational AI
  training for leadership, staff, contractors and volunteers, where appropriate.
* Engage with employees, volunteers, clients and stakeholders to understand how AI use may
  affect them, and identify internal champions who can advocate for effective, responsible
  AI use across the organisation.

## Related Concepts
* [AI Strategy Alignment](/operating-model/strategy.md)
* [AI Governance Structure](/operating-model/governance-structure.md)
* [AI Governance Practices](/operating-model/governance-practices.md)
* [AI Governance Enablers](/operating-model/governance-enablers.md)
* [AI is a Transformative Technology](/foundations/transformative-technology.md)

---
## Case Study: Atlassian's Responsible Tech Review

*Type: Concept | Tags: case-study, governance, practices | Updated: 2026-07-03T02:55:56Z*

# Case Study: Atlassian's Responsible Tech Review

Atlassian uses a **Responsible Tech Review Template** completed by product teams prior to deploying AI use cases. 

## Key Lessons in Governance

* **Simplification**: Initial templates were lengthy and complex, creating barriers to compliance. Atlassian shortened the template and used clearer language to improve usability.
* **Accessibility**: As AI use expanded, non-technical teams needed to complete assessments. The template was redesigned to be understandable without deep technical expertise.
* **Trust & Culture**: Atlassian relied on its strong culture of responsible technology use and prior investments in AI literacy to simplify the process without compromising assessment quality.


## Related Concepts
* [AI Governance Practices](/operating-model/governance-practices.md)

---
## Case Study: Canteen – Listening to the Voice of Members

*Type: Concept | Tags: case-study, governance, structure | Updated: 2026-07-03T02:55:56Z*

# Case Study: Canteen – Listening to the Voice of Members

Canteen, a national not-for-profit supporting young people affected by cancer, ensures
young people drive the organisation. The majority of Canteen's Board of Directors are
young leaders: **five Member Directors** (young people) sit alongside **four Associate
Directors** who are volunteers bringing relevant expertise to the board.

## Governance Approach

* **AI Sprint Committee**: In response to member calls to embrace AI, Canteen established
  a **time-bound (12-month)**, management-led AI Sprint Committee as a board-linked
  governance and innovation body, tasked with setting guardrails, clarifying
  accountabilities, and integrating AI oversight into Canteen's existing governance
  practices while identifying appropriate innovation opportunities.
* **Structured member consultation**: Frequent, structured consultation with staff and
  young people is built into the committee's work, so members continue to have a voice in
  shaping how AI is used — keeping AI use aligned with Canteen's mission.

## Related Concepts
* [AI Governance Structure](/operating-model/governance-structure.md)

---
## Case Study: Commonwealth Bank of Australia (CBA)

*Type: Concept | Tags: case-study, governance, practices, structure | Updated: 2026-07-03T02:55:56Z*

# Case Study: Commonwealth Bank of Australia (CBA)

At CBA, the board holds the CEO and the executive leadership team accountable for the
management of AI-related risks and opportunities. AI is treated as a **material risk**
under the Risk Management Framework (RMF), overseen at both board and management levels
through existing risk committee structures.

## Key Governance Elements

* **Business unit risk committees**: Management-led committees that assist in managing
  risk in line with the RMF and, in respect of AI, may review and evaluate AI models.
* **Model Risk Governance Committee**: A separate committee that oversees the design and
  operation of CBA's Model Risk Framework and supports approval of AI models.
* **AI Risk Committee**: Oversees the AI risk framework and provides challenge and advice
  for higher-risk AI use cases.

*Correction (2026-07-03): the previous version of this concept described a generic "Model
Registry" and "human-in-the-loop" framing not present in the Guide's actual case study
text. It has been rewritten to match the Guide's three-committee structure (business unit
risk committees, Model Risk Governance Committee, AI Risk Committee) under CBA's RMF.*

## Related Concepts
* [AI Governance Practices](/operating-model/governance-practices.md)
* [AI Governance Structure](/operating-model/governance-structure.md)

---
## Case Study: Telstra – AI Governance Operating Model in Action

*Type: Concept | Tags: case-study, governance, structure, practices, enablers | Updated: 2026-07-03T02:55:56Z*

# Case Study: Telstra – AI Governance Operating Model in Action

Telstra, Australia's largest telecommunications company, applies all four components of
HTI's AI Governance Operating Model.

> **Note:** this case study appears in the Guide's body text (p.45) but was omitted from
> the Guide's own Contents page (which lists only CBA, Atlassian, Canteen and Westpac) and
> was missing from this bundle prior to the 2026-07-03 canonical re-ingestion.

## Strategy

Telstra does not run a standalone AI strategy separate from the rest of the business.
Instead, AI is treated as a core enabler of the organisation's corporate strategy —
included as a means of achieving its overarching goal of meeting customers' connectivity
needs.

## AI Governance Structures

Telstra has a dedicated management-led AI governance body responsible for overseeing and
approving high-impact AI use cases. This was previously the **Risk Council for Data and AI
(RCAID)**, but concerns emerged about RCAID's overlap with existing functions and its
scalability given the speed of AI adoption. RCAID was redesigned as the **AI Risk
Oversight Council (AIROC)**, which has simplified and faster processes and, by removing
overlapping checks with existing privacy and cyber security controls, focuses solely on
AI-specific risks.

## AI Governance Practices

Telstra embedded governance into everyday practice by simplifying the language used in
policy, templates and processes to make them accessible to non-technical audiences. It
removed ambiguous terminology, rewrote templates in plain English, and developed a single
platform and end-to-end workflow to guide staff through AI use case approval.

## AI Governance Enablers

As AI capability spread across the organisation, Telstra strengthened training, staff
engagement and culture. Completion of its Copilot training and Responsible AI module was
made a prerequisite for Microsoft 365 Copilot access — resulting in more than **18,000
completions** and helping build responsible AI capability across the organisation.

## Related Concepts
* [AI Governance Structure](/operating-model/governance-structure.md)
* [AI Governance Practices](/operating-model/governance-practices.md)
* [AI Governance Enablers](/operating-model/governance-enablers.md)

---
## Case Study: Westpac – Building Senior Leadership's AI Literacy

*Type: Concept | Tags: case-study, governance, enablers | Updated: 2026-07-03T02:55:56Z*

# Case Study: Westpac – Building Senior Leadership's AI Literacy

Westpac has placed executive AI literacy at the centre of its AI governance efforts,
recognising that effective oversight depends on informed leadership.

## Literacy Program Details

* **Executive AI Council**: A strategic management forum, meeting monthly, that brings
  together the CEO and executive team — deliberately **not** a risk or governance forum,
  but a vehicle to demonstrate, share and accelerate cultural change. Each session
  features practitioners from across the business (developers, product owners) presenting
  AI use cases via live demonstrations rather than slide decks, with executive questions
  focused on the practitioner's journey rather than only technical detail.
* **Quarterly board updates**: The board receives a quarterly update on AI.
* **Structured AI education series**: The board builds AI literacy alongside the
  executive team through sessions sequenced cumulatively — first culture and
  transformation, then responsible AI, then a technical grounding in AI itself — giving
  both groups a shared baseline understanding of the technology and its opportunities and
  risks for the bank.

*Correction (2026-07-03): the previous version of this concept described "interactive
workshops," "scenario modelling," and simulations to "model future adaptation scenarios" —
content not present in the Guide's Westpac case study (that language instead appears
elsewhere in the Guide, in Box 4's general list of ways boards can harness AI). It has been
rewritten to match the Guide's actual Executive AI Council / board education series
description.*

## Related Concepts
* [AI Governance Enablers](/operating-model/governance-enablers.md)
* [AI Governance Structure](/operating-model/governance-structure.md)

---
## Glossary of AI Governance Terms

*Type: Reference | Tags: governance, system, appendix | Updated: 2026-07-03T02:55:56Z*

# Glossary of AI Governance Terms

> Reproduces the Guide's Appendix D verbatim (pp.53-54). Two governance-relevant terms not
> in the Guide's own glossary — **Tokenomics** and **Algorithmic Drift** — are retained
> below as bundle additions and marked accordingly, since they are used elsewhere in this
> bundle.

* **Artificial intelligence (AI)**: A set of technologies that enable machines to perform tasks that typically require human intelligence, such as analysing data, generating content, making predictions or supporting decisions.
* **Agentic AI**: AI systems capable of executing tasks with a degree of autonomy, often coordinating actions across systems or workflows to achieve an objective.
* **ACCC**: Australian Competition and Consumer Commission.
* **ACL**: Australian Consumer Law.
* **ADM**: Automated decision-making.
* **AASB**: Australian Accounting Standards Board.
* **AI6 (National AI Centre guidance)**: A set of six essential practices developed by the National AI Centre to support the safe and responsible development and use of AI systems — accountability, impact assessment, risk management, transparency, testing and monitoring, and maintaining human control.
* **AI assurance**: Processes that provide confidence that AI systems are operating as intended and within defined risk parameters, including testing, validation and audit.
* **AI governance**: The structures, processes and controls used to oversee the development, deployment and use of AI systems within an organisation.
* **AI inventory (or AI register)**: A consolidated record of the AI systems used within an organisation, including information about their purpose, design, risks and associated controls.
* **AI literacy**: The knowledge and capability required to understand AI systems, their limitations and their potential risks and benefits.
* **AI risk**: The potential for AI systems to create adverse outcomes, including operational, regulatory, ethical, reputational or societal harm, or to amplify existing risks.
* **AI risk appetite**: The level and type of AI-related risk that an organisation is willing to accept in pursuit of its objectives, as set or endorsed by the board.
* **AI strategy**: The organisation's approach to using AI to support its objectives, including how AI investments are prioritised, governed and aligned with broader strategy.
* **AI system**: A machine-based system that, for explicit or implicit objectives, infers, from the input it receives, how to generate outputs such as predictions, content, recommendations, or decisions that can influence physical or virtual environments. Different AI systems vary in their levels of autonomy and adaptiveness after deployment. (OECD definition — see Box 1.)
* **AI token**: A small unit of text — such as a word, part of a word, or punctuation — that an AI model processes and generates to understand and produce a result.
* **APRA**: Australian Prudential Regulation Authority.
* **ASD**: Australian Signals Directorate.
* **ASIC**: Australian Securities and Investments Commission.
* **Bias (in AI systems)**: Systematic and unfair outcomes resulting from skewed data, model design or deployment decisions, potentially disadvantaging individuals or groups.
* **Data governance**: The framework for managing data across its lifecycle, including data quality, security, accessibility and compliance with legal and regulatory requirements.
* **Digital infrastructure**: The computing, data storage, networking and cloud systems that support AI systems and broader digital operations within an organisation.
* **Explainability**: The extent to which the behaviour or outputs of an AI system can be understood and explained to stakeholders and regulators.
* **Generative AI**: AI systems that create new content — such as text, images or code — based on patterns learned from large datasets. Often referred to as 'general-purpose AI'.
* **Human oversight**: The involvement of people in monitoring, reviewing or intervening in AI system outputs or decisions.
* **Machine learning (ML)**: A subset of AI in which systems are trained on data to recognise patterns and improve performance over time without being explicitly programmed for each task.
* **NAIC**: National AI Centre.
* **Responsible AI**: An approach to AI that emphasises lawful, ethical and transparent use, aligned with organisational values and societal expectations.
* **SaaS**: Software-as-a-service.
* **Shadow AI**: The use of AI tools by employees without formal approval, governance or oversight by the organisation.
* **Traditional AI**: AI systems that analyse data to identify patterns, make predictions or optimise processes, typically within well-defined tasks. Also referred to as analytical AI or 'narrow AI'.
* **Tokenomics** *(bundle addition, not in Guide Appendix D — see Box 2, p.12)*: The pricing and resource model of modern LLMs, where usage costs are calculated separately for input and output tokens processed.
* **Algorithmic Drift** *(bundle addition, not in Guide Appendix D)*: The degradation of an AI model's predictive performance over time due to changes in real-world data environments; referenced in [AI Governance Practices](/operating-model/governance-practices.md) as a monitoring concern.

## Related Concepts
* [AI is a Transformative Technology](/foundations/transformative-technology.md)
* [Appendix B: Resources](/checklists/appendix-b-resources.md)

---
## Hard-Error Register — Privacy Act / ADM Disclosure Content in the Guide

*Type: Erratum | Tags: errata, regulatory, privacy, review-required | Updated: 2026-07-03T02:55:56Z*

# Hard-Error Register — Privacy Act / ADM Disclosure Content in the Guide

> **Purpose.** This concept exists so the bundle does not silently repeat the Guide's own
> mistakes. Every other concept in this bundle that touches the 10 December 2026
> automated-decision-making (ADM) disclosure duty should be read together with this
> register, not instead of it. Confidence grades follow the source audit: **CONFIRMED**
> (enacted wording / explicit OAIC or Explanatory Memorandum statement), **UNSETTLED**
> (awaiting OAIC binding guidance, expected ~September 2026), **REASONED VIEW**
> (inference or advisory material, not itself enacted text).
>
> This is information to support a decision, not legal advice. Before any external claim
> or compliance position is relied on, have it confirmed by a qualified Australian privacy
> lawyer — particularly the UNSETTLED points below.

## HE-1 — The APP 1.8 disclosure content is misstated on p.39 (most consequential error)

**Guide says (p.39):** "Broadly, organisations will need to explain when ADM systems are
used, what decisions those systems make, and what personal information is used."

**Canonical position (CONFIRMED — enacted APP 1.8 wording):** the privacy policy must set
out three things, all at the level of *kinds*, not occasions:
1. the **kinds of personal information** used in the operation of the program;
2. the **kinds of decisions made *solely*** by the program; and
3. the **kinds of decisions for which the program does a thing *substantially and directly
   related*** to making the decision — i.e. human-assisted decisions.

**Why this is wrong, not merely loose:** "when ADM systems are used" implies occasion-based
transparency; the Act requires no individual notification, no per-decision record, and no
statement of *when* a system was used — the duty is a privacy-policy disclosure only.
"What decisions those systems make" drops limb 3 entirely — the assisted-decision limb is
the provision's distinctive reach, and is exactly what defeats the "a human signs off, so
we're fine" assumption. A director acting on p.39 as written would scope only fully
automated decisions and miss most real exposure. Internally inconsistent: the Guide's own
Appendix A (p.49) states the test correctly ("computer programs to make, or to do a thing
substantially and directly related to making, a decision"). Page 39 — the page a busy
director is most likely to act on — contradicts it.

**Bundle correction:** see [Privacy Act ADM Disclosure Duty](/foundations/privacy-act-adm-disclosure.md), which states the three-limb kinds-based test as the primary formulation.

## HE-2 — An EU threshold is substituted for the Australian one (p.24, Table 4)

**Guide says (p.24):** "Where AI is used in decisions with legal or similarly significant
effects, this can make it difficult to justify outcomes..."

**Canonical position (CONFIRMED divergence; classification as an error is a REASONED
VIEW):** "legal or similarly significant effects" is GDPR Article 22 language. The
Australian test is whether the decision **"could reasonably be expected to significantly
affect the individual's rights or interests"** (APP 1.7(b), APP 1.9(c)) — more than
trivial, counting both adverse *and* beneficial effects, with statutory examples including
decisions affecting rights under a contract or access to a significant service. The
Australian trigger is **broader** than GDPR at the front end (it captures assisted
decisions, not only "solely automated" ones) and **narrower** at the remedy (disclosure
only — no right to contest, no right to an explanation of a specific decision). Importing
the EU phrase invites both under-scoping the trigger and over-reading the remedy.

## HE-3 — The exemption picture is overstated and incomplete (p.49)

**Guide says (p.49):** "The Privacy Act applies to all organisations unless exempt under
the small business exemption."

**Canonical position (CONFIRMED):** two material defects.
1. **The small business exemption has carve-backs.** A business at or under A$3M turnover
   is still caught if it is a health-service provider holding health information, trades in
   personal information, is a contracted service provider under a Commonwealth contract, or
   operates a residential-tenancy database. The Guide's sentence would tell a sub-$3M
   allied-health or government-supplier reader they are out of scope when they are in it.
2. **The employee-records exemption (s 7B(3)) is never mentioned anywhere in the Guide**,
   despite substantial coverage of workforce AI. It is the exemption most relevant to the
   ADM duty, and its boundaries are where boards get caught: it covers **current and former
   employees only**. It gives **no protection** for **job applicants** (AI recruitment
   screening is one of the most common APP 1.7 triggers), **volunteers** (directly relevant
   to the Guide's NFP audience), **government employers**, or **third-party HR/payroll/ATS
   vendors** processing the data. Per *Lee v Superior Wood* [2019] FWCFB 2434, the exemption
   also does not authorise the *collection* of (especially sensitive) employee data — APP 3
   applies to collection first.

## HE-4 — No enforcement consequence is stated for the December 2026 duty (pp.18, 39, 49)

**Guide says:** the 10 December 2026 date, three times (Table 1 p.18, p.39, Appendix A
p.49) — with no consequence of non-compliance stated anywhere.

**Canonical position (CONFIRMED figures; penalty unit A$364 from 1 July 2026):** a
deficient privacy policy is enforceable **without going to court** by OAIC infringement
notice under s 80UB — **60 penalty units (A$21,840)** for an unlisted body corporate,
**200 penalty units (A$72,800)** for a listed corporation (s 80UB(1A)), **12 penalty units
(A$4,368)** for an individual — and by Federal Court civil penalty under **s 13K (1,000
penalty units = A$364,000 per contravention)** for a body corporate. Broader interference
penalties escalate through **s 13H (10,000 penalty units = A$3.64M)** and **s 13G**
(serious/repeated). On s 13G, note the correction most relevant to this Guide's mid-market
readers: **below roughly A$167M turnover the 30%-of-turnover limb, not the A$50M figure, is
the operative maximum** — e.g. about A$4.2M for a A$14M-turnover company. A director's
guide that gives the deadline but not the enforcement mechanics leaves boards unable to
weigh the risk it is asking them to govern. *(Classified as a hard gap rather than a
misstatement — nothing wrong is asserted; the decisive facts are absent.)*

## HE-5 — The statutory term "computer program" is never surfaced (throughout)

**Guide frames** the December 2026 duty entirely inside an *AI* guide ("organisations
subject to the Privacy Act that use automated decision-making (ADM) systems, including AI
systems", p.39).

**Canonical position (CONFIRMED — Explanatory Memorandum):** the operative statutory term
is **"computer program"**; the word "artificial intelligence" appears nowhere in the
operative provisions. The EM confirms scope spans "pre-programmed rule-based processes,
artificial intelligence and machine learning processes", and the OAIC's May 2026 Issues
Paper treats **spreadsheets such as Excel** as within scope. A board that scopes its
disclosure inventory by asking "where do we use AI?" — the question this Guide trains it to
ask via Box 3 (p.13) — will **under-capture**: a 20-year-old rules-based scoring engine or a
decision-driving spreadsheet is equally caught. Box 3 partially mitigates by listing
"automated decision-making" as an AI-signalling term, but the Guide never states that the
legal duty is technology-neutral. *(REASONED VIEW as to reader effect; CONFIRMED as to the
statutory scope.)*

## HE-6 — The pending OAIC binding guidance is never mentioned (pp.39, 49)

**Guide says:** "Regulatory obligations in respect of AI and privacy are expected to
continue to evolve and it is imprtant [sic] that organisations monitor developments" —
generic only.

**Canonical position (CONFIRMED as to the consultation; the resolutions themselves are
UNSETTLED):** the OAIC issued an ADM Issues Paper on 18 May 2026 and **binding guidance is
expected around September 2026** — i.e. roughly three months before the compliance date,
and before this Guide's readers must have updated policies. The unsettled points it will
resolve are exactly the ones a board acting on this Guide needs flagged: the meaning of
**"substantially and directly related"**, the **drafting standard** the policy must meet (a
generic "we may use automated tools" line will not meet it), and who has **"arranged for"**
a program in a vendor/SaaS supply chain. Presenting the duty as fully settled understates
board-level timing risk.

## HE-7 — Editorial defects (quality signal, not substance)

Typographical errors survive in a v2 flagship publication: "arrangeents" (p.16, fn 2);
"valurable", "minium" (p.32); "these the risks" (p.35 heading text — rendered "have
visibility over these the risks associated with these providers"); "companes" (p.37);
"imprtant" (p.39); "approach to to" (p.40); "the the human impact" (p.24, cross-reference
text); "Do we received timely..." (p.33). Individually trivial; collectively relevant to
how much weight a reader should place on unverified detail elsewhere in the Guide.

## What the Guide gets right (verified — no correction needed)

- **10 December 2026** commencement: correct, consistently stated (CONFIRMED).
- Appendix A's formulation of the trigger (p.49): correct, including "make, or do a thing
  substantially and directly related to making, a decision" and the significant-effect
  condition (CONFIRMED).
- Statutory tort for serious invasions of privacy "since 2025": correct — commenced June
  2025 (CONFIRMED). See p.49 and the [Bunnings ARTA facial-recognition footnote](/foundations/regulatory-obligations-appendix-a.md).
- Privacy obligations attach to AI **outputs** containing personal information, "including
  inferred or incorrect information" (p.24): correct and important — inferences and
  hallucinations about an identifiable person are themselves personal information
  (CONFIRMED).
- National AI Plan (December 2025): no standalone AI statute; existing-law approach —
  correct (CONFIRMED).
- No overclaim that this is Australia's "first AI law" or an EU AI Act equivalent — the
  Guide avoids the misleading-conduct trap (ACL s 18) that afflicts much commentary on this
  reform.

## Related Concepts
* [Privacy Act ADM Disclosure Duty](/foundations/privacy-act-adm-disclosure.md)
* [Appendix A: Regulatory Obligations and AI](/foundations/regulatory-obligations-appendix-a.md)
* [The Role of the Board and the Regulatory Landscape](/foundations/board-role-regulatory-landscape.md)

---
## Measuring Value and Returns from AI

*Type: Concept | Tags: governance, operating-model, strategy | Updated: 2026-07-03T02:55:56Z*

# Measuring Value and Returns from AI

AI has the potential to deliver significant benefits for organisations, but realising
those benefits is not automatic. Boards have an important role in overseeing whether
investments in AI are generating sustainable value.

## Key points

* Greater value is realised where AI is used to transform processes, systems or business
  models, yet relatively few organisations have moved beyond the pilot phase in these
  strategies.
* AI ROI assessment should focus on specific, measurable use cases and test whether the
  investment has been realised in terms of organisational efficiency and improved outputs.

## The board's role in AI ROI

Board oversight of return on investment from AI serves three functions:

1. **Supports oversight of strategic and technology investments.** Boards should
   understand what value AI investments are expected to deliver, over what timeframe, and
   how success will be measured.
2. **Promotes organisational discipline and focus.** Requiring clear use cases, defined
   success metrics and structured evaluation processes helps avoid fragmented AI adoption
   that consumes resources without delivering meaningful outcomes.
3. **Value and risk in AI deployment are closely connected.** AI systems that create
   significant commercial, regulatory or reputational risks may ultimately erode rather
   than create organisational value. Boards should consider whether AI benefits are being
   achieved in a manner that is safe, lawful and aligned with the organisation's risk
   appetite.

## The challenge of measuring AI returns

Evidence on AI investment returns remains mixed. Some studies report that 80% of
organisations have not seen a tangible impact on profitability from generative AI
investments, and that 95% of AI pilots fail. Yet other research reports broader benefits:
KPMG's Global AI Pulse Q1 2026 survey found 64% of organisations have seen real business
value (rising to 82% among 'AI leaders'), and Deloitte research found 61% of Australian
companies reported efficiency improvements from AI use.

Early generative AI benefits often appear as individual productivity gains that do not
automatically translate into bottom-line impact. Greater value is typically realised where
AI transforms processes, systems or business models — but relatively few organisations
currently operate at this level: Deloitte research found 30% of Australian businesses
report using AI to transform their processes, compared to 34% globally. At the same time,
pressure to demonstrate returns is intensifying — the Kyndryl Readiness Report found 61%
of business leaders reported increasing pressure to demonstrate AI ROI in 2025.

## A structured framework for AI ROI

* **Focus on a specific, targeted use case** rather than a general capability or system.
  For each use case, identify the specific business improvement sought and the metrics
  that will demonstrate success.
* **Approach ROI with the implementation phase in mind.** AI initiatives typically move
  through three phases, each with a distinct ROI profile: **experimentation** (can we do
  this?), **integration** (does it work?), and **scaling** (can this be rolled out?).
* **Take a broad view of benefits** to capture the full range of direct and indirect
  benefits AI investments achieve over time.
* **Test assumptions at the integration and scaling phases**, particularly:
  1. **adoption** — what proportion of the target user base is actively using the
     capability?
  2. **translation efficiency** — how well does the targeted business improvement
     translate into broader organisational value?
  3. **accuracy and performance** — how well does the AI use case perform, and can the
     organisation rely on it for the quality and consistency required?
* **Model all relevant costs**, including token costs associated with usage and the cost
  of staff training and quality assurance.

This framework applies to organisations of any size, but the level of evaluation and
governance effort should be proportionate to the opportunity, cost, risk and complexity of
the deployment.

## Related Concepts
* [AI Strategy Alignment](/operating-model/strategy.md)
* [AI is a Transformative Technology](/foundations/transformative-technology.md)

---
## Privacy Act ADM Disclosure Duty

*Type: Concept | Tags: governance, regulatory, privacy, foundations | Updated: 2026-07-03T02:55:56Z*

# Privacy Act ADM Disclosure Duty

From **10 December 2026**, organisations covered by the *Privacy Act 1988* (Cth) must
disclose in their privacy policies certain uses of computer programs — including but not
limited to AI systems — to make, or substantially and directly assist in making, decisions
that significantly affect an individual using their personal information. This is a
**privacy-policy disclosure duty**, not an individual-notification or per-decision
transparency duty.

> **Correction notice.** The Guide states this duty inconsistently — correctly in Appendix
> A (p.49) but incorrectly on p.39, the page a director is most likely to act on. This
> concept states the corrected, enacted position. See
> [Hard-Error Register — HE-1](/errata/privacy-act-hard-error-register.md) for the
> full comparison.

## The three-limb disclosure test (APP 1.8)

The privacy policy must set out, at the level of **kinds** — not individual occasions or
per-decision records — three things:

1. the **kinds of personal information** used in the operation of the program;
2. the **kinds of decisions made *solely*** by the program (fully automated decisions); and
3. the **kinds of decisions for which the program does a thing *substantially and directly
   related*** to making the decision — i.e. **human-assisted** decisions where a person
   signs off but the program did the substantive work.

Limb 3 is the provision's distinctive reach. It is what defeats the assumption that "a
human signs off, so we're fine" — a board that scopes its disclosure inventory to
fully-automated decisions only will under-capture its real exposure.

## The trigger: "significantly affect"

The duty applies where the decision **could reasonably be expected to significantly affect
the individual's rights or interests** (APP 1.7(b), APP 1.9(c)) — more than trivial,
capturing both **adverse and beneficial** effects, with statutory examples including
decisions affecting rights under a contract or access to a significant service.

This is an **Australian-specific test**, not the GDPR Article 22 "legal or similarly
significant effects" standard. The Australian trigger is *broader* than GDPR at the front
end (it captures human-assisted decisions, not only solely-automated ones) but *narrower*
at the remedy (disclosure only — there is no individual right to contest an ADM decision or
to an explanation of a specific decision under this duty). See
[Hard-Error Register — HE-2](/errata/privacy-act-hard-error-register.md).

## Technology-neutral scope: "computer program", not "AI"

The operative statutory term is **"computer program"**. The word "artificial intelligence"
does not appear in the operative provisions. The Explanatory Memorandum confirms scope
spans "pre-programmed rule-based processes, artificial intelligence and machine learning
processes", and the OAIC's May 2026 Issues Paper treats **spreadsheets such as Excel** as
within scope. A board that inventories its exposure by asking "where do we use AI?" will
under-capture — a decades-old rules-based scoring engine or a decision-driving spreadsheet
is equally caught. See [Hard-Error Register — HE-5](/errata/privacy-act-hard-error-register.md).

## Exemption boundaries

The Privacy Act does **not** apply to all organisations by default — but the small business
exemption is narrower than a simple turnover test suggests, and the employee-records
exemption is a separate, frequently-missed boundary. See
[Hard-Error Register — HE-3](/errata/privacy-act-hard-error-register.md) for both.

## Enforcement

A deficient privacy policy is enforceable **without going to court** by OAIC infringement
notice (penalty units, scaling by entity type), and by Federal Court civil penalty for more
serious or repeated interferences with privacy. See
[Hard-Error Register — HE-4](/errata/privacy-act-hard-error-register.md) for the specific
penalty-unit figures and dollar values (current from 1 July 2026).

## What remains unsettled

The OAIC issued an ADM Issues Paper on 18 May 2026; **binding guidance is expected around
September 2026** — roughly three months before the compliance date. Unsettled points
include the meaning of "substantially and directly related", the drafting standard a
policy must meet, and who has "arranged for" a program in a vendor/SaaS supply chain. See
[Hard-Error Register — HE-6](/errata/privacy-act-hard-error-register.md).

## Related regulatory context

Since **2025**, the Privacy Act also includes a **statutory tort for serious invasions of
privacy** — a separate mechanism (not part of the ADM disclosure duty) that can apply to,
for example, the deployment of facial recognition technology without valid consent. See
[Appendix A: Regulatory Obligations and AI](/foundations/regulatory-obligations-appendix-a.md).

## Related Concepts
* [Hard-Error Register — Privacy Act / ADM Disclosure Content in the Guide](/errata/privacy-act-hard-error-register.md)
* [The Role of the Board and the Regulatory Landscape](/foundations/board-role-regulatory-landscape.md)
* [Appendix A: Regulatory Obligations and AI](/foundations/regulatory-obligations-appendix-a.md)

---
## The Role of the Board and the Regulatory Landscape

*Type: Concept | Tags: governance, foundations, regulatory | Updated: 2026-07-03T02:55:56Z*

# The Role of the Board and the Regulatory Landscape

The board plays a critical role in overseeing that the organisation's use of AI aligns with its strategy, risk appetite, and values. While directors do not need to be technical experts, they require a minimum viable understanding of AI to provide effective human oversight.

## Directors' Duties and AI

Board-level oversight of AI and AI-related risk management forms part of directors' existing duties under the *Corporations Act 2001* (Cth). Directors must act with due care, diligence, in good faith, and for a proper purpose when deploying and using AI systems.

ASIC Report 798 (*Beware the gap: Governance arrangements in the face of AI innovation*, October 2024) states: "Company directors and officers must discharge their duties with a reasonable degree of care and diligence. These duties extend to the adoption, deployment and use of AI. Directors and officers should be aware of the use of AI within their companies, the extent to which they rely on AI-generated information to discharge their duties and the reasonably foreseeable associated risks."

The AICD practice statement *Directors' oversight of company compliance obligations* and its supporting legal opinion (October 2024) outlines the duty of care and diligence owed by company directors — central to how boards approach non-financial risk, including AI governance.

### AI used by the board itself

Directors should not rely on AI-generated summaries or analysis as a substitute for their own review of board papers, and should ensure board AI use does not undermine confidence in management or blur accountability. In *ASIC v Bekier (Liability Judgment)* [2026] FCA 196, Justice Michael Lee commented on the use of AI in analysing board papers, noting the need for caution: "There is nothing inherently objectionable in obtaining such assistance [from AI], but what ought not occur is that this development becomes an excuse for a failure to instil discipline in the provision of information to directors or leads to a quiet normalisation of private reliance by them upon computer-generated distillations, unregulated by any agreed policy."

## Regulatory Landscape

In December 2025, the National AI Plan confirmed Australia will not introduce standalone AI legislation, relying instead on existing laws, while leaving open targeted reform where gaps emerge. Table 1 (below) summarises the key existing frameworks; see [Appendix A: Regulatory Obligations and AI](/foundations/regulatory-obligations-appendix-a.md) for the full detail on each.

| Law | Summary |
|---|---|
| **Privacy Act 1988** | Applies to collection, use, storage, disclosure and destruction of personal information, including where used to train, test or use an AI system, unless exempt. From **10 December 2026**, organisations must disclose in their privacy policies where they use personal information in certain automated decision-making — see [Privacy Act ADM Disclosure Duty](/foundations/privacy-act-adm-disclosure.md) for the corrected three-limb test (the Guide states this duty inconsistently between p.18/p.39 and p.49 — see [Hard-Error Register — HE-1](/errata/privacy-act-hard-error-register.md)). |
| **Australian Consumer Law (ACL)** | Prohibits misleading or deceptive conduct, unconscionable conduct, and false or misleading representations in trade or commerce; includes consumer guarantees and a product liability regime. May apply to 'AI-washing' or other misleading claims about AI capabilities. |
| **Anti-discrimination laws** | Commonwealth and State laws prohibit direct and indirect discrimination on protected attributes (race, sex, age, disability), including where a system is trained on data reflecting historical biases. |
| **Work health and safety laws** | Harmonised WHS laws impose a primary duty of care for worker health and safety, relevant to developing, procuring or deploying AI systems. NSW has separately enacted a duty regarding health and safety risks from work allocated by a digital work system. |
| **Law of negligence** | Organisations owe a duty of care to people affected by their AI use, to avoid reasonably foreseeable harm; breach may arise where harm results from foreseeable risks the organisation failed to reasonably mitigate. |
| **Copyright Act 1968** | Protects original human-authored works. Using copyright-protected material to train or operate AI systems may infringe copyright unless consent, a licence, or a fair dealing exception applies. |
| **Fair Work Act 2009** | AI introduction will often constitute a 'major workplace change' under the Act and most awards/agreements where it materially affects employees, triggering consultation and mitigation-measure obligations. |

*Table 1: Overview of key regulatory frameworks (p.18).*

### Cyber security risk and regulatory obligations

ASIC and APRA have both called for greater board vigilance on cyber and data risk settings given rapid AI advances. In May 2026, ASD, APRA and ASIC each issued separate guidance in a short period on elevated cyber risks from AI adoption, with common messages on rapid vulnerability patching and strong privileged access management. The *Cyber Security Act 2024* (Cth) and *Security of Critical Infrastructure Act 2018* (Cth) impose related risk management and reporting requirements.

### Australian Government guidance

Australia's (voluntary) **AI Ethics Principles** — human, societal and environmental wellbeing; human-centred values; fairness; privacy protection and security; reliability and safety; transparency and explainability; contestability; and accountability — align closely with the OECD AI Principles. In October 2025 the National AI Centre published *Guidance for AI Adoption*, setting out six essential practices known as the **AI6** (decide who is accountable; understand impacts and plan accordingly; measure and manage risks; share essential information; test and monitor; maintain human control), replacing the earlier ten voluntary guardrails under Australia's Voluntary AI Safety Standard.

### International regulatory landscape

| Country / Region | AI regulatory approach |
|---|---|
| European Union | Most comprehensive AI-specific regulation via the EU AI Act — a risk-based framework with graduated obligations by risk level, phased implementation, and extraterritorial reach. |
| United Kingdom | Pro-innovation, principles-based approach relying on existing regulators applying five key principles: safety, transparency, fairness, accountability and contestability. |
| United States | No comprehensive federal AI statute; a growing number of states have enacted AI-related laws addressing specific risks and use cases. |
| Canada | No comprehensive AI-specific legislation — the proposed Artificial Intelligence and Data Act did not progress; AI is regulated through existing federal and provincial laws. |
| China | Integrates AI governance into existing laws, supplemented by AI-specific administrative measures. |

*Table 2: Selected international approaches to AI regulation (p.20).*

## Ethical Considerations

AI systems can behave in ways that are less transparent and harder to test. Boards must address ethical questions that extend beyond legal compliance, asking: *'We can, but should we?'* The AICD and The Ethics Centre's joint publication *Ethics in the Boardroom* (2nd edition) provides a framework for this.

## Related Concepts
* [AI Governance Practices](/operating-model/governance-practices.md)
* [AI Governance Structure](/operating-model/governance-structure.md)
* [AI Opportunities and Risks](/foundations/opportunities-and-risks.md)
* [Privacy Act ADM Disclosure Duty](/foundations/privacy-act-adm-disclosure.md)
* [Appendix A: Regulatory Obligations and AI](/foundations/regulatory-obligations-appendix-a.md)
* [Hard-Error Register — Privacy Act / ADM Disclosure Content in the Guide](/errata/privacy-act-hard-error-register.md)

---
