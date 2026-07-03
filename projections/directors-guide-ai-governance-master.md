# Directors Guide AI Governance — Knowledge Projection

| Field | Value |
|---|---|
| Generated | 2026-07-03T02:02:34Z |
| Scope | master (all concepts) |
| Concepts included | 13 |
| Log head | 2026-07-03 |
| Sync status | Current |

> **UPLOAD INSTRUCTIONS**: Upload THIS FILE ONLY to your cloud LLM Project (Gemini Gem, Claude.ai Project, ChatGPT Project). Do NOT upload index.md, log.md, or individual concept files alongside it — this file already contains the ontology and all concepts.
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

*(empty at bundle initialisation — add as needed)*

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

---

## Case Study: Atlassian's Responsible Tech Review
*Type: Concept | Tags: case-study, governance, practices | Updated: 2026-07-03T02:02:05Z*

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
*Type: Concept | Tags: case-study, governance, structure | Updated: 2026-07-03T02:02:05Z*

# Case Study: Canteen – Listening to the Voice of Members

Canteen, a non-profit supporting young people impacted by cancer, ensures its youth-led mission drives its technology adoption.

## Governance Approach

* **AI Sprint Committee**: A time-bound, management-led committee established to review AI opportunities and risks.
* **Board Alignment**: Keeping the board informed of AI sprint outcomes and ensuring alignment with Canteen's ethical principles.
* **Stakeholder Focus**: Keeping the voices and safety of its young members at the center of all AI deployment decisions.


## Related Concepts
* [AI Governance Structure](/operating-model/governance-structure.md)

---

## Case Study: Commonwealth Bank of Australia (CBA)
*Type: Concept | Tags: case-study, governance, practices | Updated: 2026-07-03T02:02:05Z*

# Case Study: Commonwealth Bank of Australia (CBA)

The Commonwealth Bank of Australia (CBA) has developed a comprehensive responsible AI governance framework to support its deployment of machine learning and generative AI models.

## Key Governance Elements

* **Model Registry**: Maintaining a centralised inventory of all AI models, classifying them by risk level.
* **Human-in-the-Loop**: Ensuring critical customer-facing or financial decisions undergo human review.
* **Ethical Principles**: Testing models against core values, including fairness, transparency, and accountability.
* **Continuous Monitoring**: Regularly auditing models to detect algorithmic drift or bias.


## Related Concepts
* [AI Governance Practices](/operating-model/governance-practices.md)

---

## Case Study: Westpac – Building Senior Leadership's AI Literacy
*Type: Concept | Tags: case-study, governance, enablers | Updated: 2026-07-03T02:02:05Z*

# Case Study: Westpac – Building Senior Leadership's AI Literacy

Westpac has placed executive and board AI literacy at the center of its technological transformation.

## Literacy Program Details

* **Interactive Workshops**: Delivering hands-on workshops and simulations for senior leadership to understand AI capabilities and risks.
* **Scenario Modelling**: Running exercises to model future adaptation scenarios and identify strategic dependencies.
* **Board Capability**: Ensuring the board has the necessary vocabulary and framework to actively challenge management's AI strategy.


## Related Concepts
* [AI Governance Enablers](/operating-model/governance-enablers.md)
* [AI Governance Structure](/operating-model/governance-structure.md)

---

## Glossary of AI Governance Terms
*Type: Reference | Tags: governance, system | Updated: 2026-07-03T02:02:05Z*

# Glossary of AI Governance Terms

* **Agentic AI**: Systems that use generative AI to plan and act across multiple steps to achieve goals, operating with varying degrees of autonomy.
* **Generative AI**: Machine-learning models trained to generate new content, such as text, images, or code.
* **Traditional AI**: Narrow AI systems trained to perform specific, predefined tasks (e.g. classification or predictive analytics).
* **Tokenomics**: The pricing and resource model of modern LLMs, where costs are calculated based on the number of processed input and output tokens.
* **Shadow AI**: The unauthorised use of AI systems or tools by employees without the knowledge or approval of the IT or governance teams.
* **Algorithmic Drift**: The degradation of an AI model's predictive performance over time due to changes in real-world data environments.


## Related Concepts
* [AI is a Transformative Technology](/foundations/transformative-technology.md)

---

## SME and NFP Director Checklist
*Type: Playbook | Tags: governance, checklist | Updated: 2026-07-03T02:02:05Z*

# SME and NFP Director Checklist

Small and medium-sized enterprises (SMEs) and not-for-profits (NFPs) face unique resource constraints but must still discharge their duties with due care and diligence when adopting AI.

## Practical Steps for SME and NFP Boards

1. **Conduct an AI Stocktake**
   * Identify what AI tools are currently used across the organisation (including shadow AI or SaaS-embedded AI).
2. **Define Acceptable Use Policies**
   * Establish simple guidelines on what customer or business data can be entered into public AI tools (e.g. ChatGPT).
3. **Assess Vendor Data Policies**
   * Verify if vendor tools use your organisation's data to train their models.
4. **Build Basic AI Literacy**
   * Encourage directors and staff to build foundational AI knowledge.
5. **Monitor Costs**
   * Keep track of software licensing and usage-based token costs.


## Related Concepts
* [AI is a Transformative Technology](/foundations/transformative-technology.md)

---

## The Role of the Board and the Regulatory Landscape
*Type: Concept | Tags: governance, foundations, regulatory | Updated: 2026-07-03T02:02:05Z*

# The Role of the Board and the Regulatory Landscape

The board plays a critical role in overseeing that the organisation's use of AI aligns with its strategy, risk appetite, and values. While directors do not need to be technical experts, they require a minimum viable understanding of AI to provide effective human oversight.

## Directors' Duties and AI

Board-level oversight of AI and AI-related risk management forms part of directors' existing duties under the *Corporations Act 2001* (Cth). Directors must act with due care, diligence, in good faith, and for a proper purpose when deploying and using AI systems. 

ASIC Report 798 (*Beware the gap: Governance arrangements in the face of AI innovation*, October 2024) emphasises that directors and officers must remain aware of AI use within their companies and the extent to which they rely on AI-generated information.

## Regulatory Landscape

Organisations must govern AI within existing legal and regulatory frameworks, including:
* **Privacy**: Managing personal data and information security.
* **Consumer Protection**: Avoiding misleading conduct or automated bias.
* **Discrimination**: Ensuring algorithms do not perpetuate unfair bias.
* **Work Health and Safety (WHS)**: Assessing the physical and psychological safety of AI-driven tools in the workplace.
* **Copyright & IP**: Managing training data provenance and output ownership.
* **Cyber Security**: Maintaining secure environments against AI-targeted attacks.

## Ethical Considerations

AI systems can behave in ways that are less transparent and harder to test. Boards must address ethical questions that extend beyond legal compliance, asking: *'We can, but should we?'*


## Related Concepts
* [AI Governance Practices](/operating-model/governance-practices.md)
* [AI Governance Structure](/operating-model/governance-structure.md)
* [AI Opportunities and Risks](/foundations/opportunities-and-risks.md)

---

## AI Opportunities and Risks
*Type: Concept | Tags: governance, foundations, risk | Updated: 2026-07-03T02:02:05Z*

# AI Opportunities and Risks

Deploying AI systems requires boards to navigate a complex dynamic of opportunity and risk, balancing technological innovation with organisational responsibility.

## Opportunities

* **Productivity & Efficiency**: Automation of repetitive tasks and process acceleration.
* **Product Quality & Service**: Hyper-personalised customer experiences and tailored product recommendations.
* **Decision-Making**: Faster data synthesis, pattern recognition, and predictive analytics.
* **Employee Experience**: Reducing administrative burdens to let employees focus on high-value tasks.

## Risks and Harms

* **Commercial Risk**: Underperforming investments, high computational/token costs, and vendor lock-in.
* **Reputational Risk**: Brand damage from algorithmic bias, 'hallucinations', or inappropriate customer interactions.
* **Regulatory Risk**: Non-compliance with privacy, consumer protection, or copyright laws.
* **Cyber Security & Privacy**: AI systems being exploited for data exfiltration or prompt injection attacks.
* **Human Impacts**: Job displacement, psychological safety concerns, and workforce transition friction.


## Related Concepts
* [AI Governance Practices](/operating-model/governance-practices.md)
* [AI Strategy Alignment](/operating-model/strategy.md)
* [The Role of the Board and the Regulatory Landscape](/foundations/board-role-regulatory-landscape.md)
* [AI is a Transformative Technology](/foundations/transformative-technology.md)

---

## AI is a Transformative Technology
*Type: Concept | Tags: governance, foundations, technology | Updated: 2026-07-03T02:02:05Z*

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


## Related Concepts
* [Glossary of AI Governance Terms](/checklists/glossary.md)
* [SME and NFP Director Checklist](/checklists/sme-nfp-checklist.md)
* [AI Opportunities and Risks](/foundations/opportunities-and-risks.md)

---

## AI Governance Enablers
*Type: Concept | Tags: governance, operating-model, enablers | Updated: 2026-07-03T02:02:05Z*

# AI Governance Enablers

Beyond structures and practices, successful AI governance depends on key enablers that support responsible adoption and mitigate risks.

## AI Technology and Supporting Infrastructure

A pre-condition of significant organisational investment in AI is enhancing the underlying digital, data, and technology infrastructure. This includes computing capacity, data storage, and network capabilities. Boards should receive assurance that the infrastructure can support planned workloads.

## AI Literacy and Responsible Culture

An organisational culture that embraces AI knowledge, literacy, and responsible use is critical. Boards should support training programs to raise AI literacy across the workforce and foster an ethical culture of compliance.

## Stakeholder Engagement

Organisations must remain sensitive to the impact of AI on employees and customers:
* **Employees**: Managing job transition, supporting psychological safety, and clarifying acceptable use.
* **Customers**: Ensuring transparency, maintaining human-in-the-loop options, and protecting privacy.


## Related Concepts
* [Case Study: Westpac – Building Senior Leadership's AI Literacy](/case-studies/westpac-case-study.md)

---

## AI Governance Practices
*Type: Concept | Tags: governance, operating-model, practices | Updated: 2026-07-03T02:02:05Z*

# AI Governance Practices

Boards must oversee how AI-specific risks are identified, monitored, and managed through the organisation's existing risk management frameworks and controls.

## Risk Management Frameworks

AI risks should not be treated in isolation. Instead, they should be integrated into the organisation's enterprise risk management (ERM) framework. Key practices include:
* Conducting regular AI stocktakes and risk assessments before deployment.
* Establishing monitoring processes for algorithmic drift, bias, and performance.
* Integrating AI risk management with cyber security and data governance.

## Vendor Risk Management

Most organisations adopt AI through third-party vendors and Software-as-a-Service (SaaS) products. The board must ensure that management:
* Evaluates the data protection settings and security postures of AI vendors.
* Understands whether customer data is used to train vendor models.
* Manages vendor lock-in risks and dependencies.


## Related Concepts
* [Case Study: Atlassian's Responsible Tech Review](/case-studies/atlassian-case-study.md)
* [Case Study: Commonwealth Bank of Australia (CBA)](/case-studies/cba-case-study.md)
* [AI Governance Structure](/operating-model/governance-structure.md)
* [AI Strategy Alignment](/operating-model/strategy.md)
* [AI Opportunities and Risks](/foundations/opportunities-and-risks.md)
* [The Role of the Board and the Regulatory Landscape](/foundations/board-role-regulatory-landscape.md)

---

## AI Governance Structure
*Type: Concept | Tags: governance, operating-model, structure | Updated: 2026-07-03T02:02:05Z*

# AI Governance Structure

Organisations need clear structures to manage and monitor AI. While dedicated AI governance bodies may not be necessary for every organisation, the board must have clear visibility over how AI is managed.

## Roles and Responsibilities

The board should work with management to map AI-related responsibilities across the organisation, including:
* Clarifying who is accountable for AI risk assessments, data controls, and model performance monitoring.
* Regularly reviewing and updating these roles in line with changing business operations and technological developments.

## Board AI Literacy

A critical enabler of effective AI governance is the board's own AI literacy. Directors should proactively build their understanding of AI concepts (such as generative vs agentic AI, and tokenomics) to ask management the right questions and seek appropriate assurance.


## Related Concepts
* [Case Study: Canteen – Listening to the Voice of Members](/case-studies/canteen-case-study.md)
* [Case Study: Westpac – Building Senior Leadership's AI Literacy](/case-studies/westpac-case-study.md)
* [AI Governance Practices](/operating-model/governance-practices.md)
* [AI Strategy Alignment](/operating-model/strategy.md)
* [The Role of the Board and the Regulatory Landscape](/foundations/board-role-regulatory-landscape.md)

---

## AI Strategy Alignment
*Type: Concept | Tags: governance, operating-model, strategy | Updated: 2026-07-03T02:02:05Z*

# AI Strategy Alignment

The board should approach decision-making on AI and AI-related investments with discipline, ensuring that decisions align with the organisation's overall strategy, values, and purpose.

## Defining Risk Appetite for AI

Given the distinctive risks associated with AI (such as lack of explainability and potential bias), the board should work with management to establish a specific risk appetite for AI. This appetite must be reflected in internal policies and the risk management framework.

## Resourcing and Prioritisation

Effective AI implementation cannot occur in a vacuum. The board must oversee:
* Allocating adequate resources for technology, infrastructure, and human capabilities.
* Ensuring data quality is sufficient to support planned AI models.
* Prioritising AI use cases based on strategic value and risk profile rather than pursuing ad-hoc pilots.


## Related Concepts
* [AI Governance Practices](/operating-model/governance-practices.md)
* [AI Governance Structure](/operating-model/governance-structure.md)
* [AI Opportunities and Risks](/foundations/opportunities-and-risks.md)

---

