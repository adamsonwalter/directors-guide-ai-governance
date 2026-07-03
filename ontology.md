---
type: Ontology
title: Bundle Ontology
description: Single source of truth for all concept types, relationship semantics, tag taxonomy, and validation rules in this OKF bundle.
memory_tier: semantic
confidence: 1.0
okf_version: "0.1"
timestamp: 2026-07-03T05:20:08Z
tags: [ontology, system, governance]
---

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
| `Coverage Ledger` | An exhaustive inventory of every named structural unit in a source document (Box/Table/Figure/callout/appendix/quote), mapped to the bundle file(s) that capture it, with a Status column (Captured / Partial / Not applicable). A mechanical completeness gate — distinct from `Erratum`, which checks correctness of what *is* captured, not whether everything *was* captured. | Inventory, Status Legend, Gaps Found and Closed |

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
| `coverage` | Concepts that audit the bundle's completeness against a source document |


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
retire event. See [log.md](log.md) and AGENTS.MD §ENRICHMENT_AGENT / §CONFORMANCE_AGENT for
how this is now enforced unconditionally, at write time and at audit time, for every bundle built
from this kit — not just the one where the gap was first found.

---

# Source Coverage Contracts

> **Not the same problem as Deliverable Parity Contracts, above.** That section catches
> *concept → hand-authored deliverable* drift (a snapshot embedded in an HTML/JS artifact
> going stale after the source concepts change). This section catches a different failure:
> *source document → bundle* drift, where a named unit in the original source (a Box,
> Table, Figure, recurring callout, appendix, or cited case) was simply never transcribed
> into any concept file in the first place. There is no deliverable involved — the miss is
> in ENRICHMENT_AGENT's own INGEST/MAP pass, not in a downstream artifact. A bundle can be
> perfectly internally-conformant (every CHECK_1–7 passes) while still failing this, because
> none of CHECK_1–7 ever look back at the source document.
>
> **Why this exists:** during the 2026-07-03 canonical re-ingestion of the AICD/HTI
> Director's Guide, a full sequential read of the extracted text still missed four
> recurring "Questions for directors to ask" / "Governance red flags" boxes (pp.30, 33, 39,
> 43) — a single self-review pass, driven by "what stood out as substantively new," is
> correlated with its own blind spots and will re-miss the same class of content on a
> re-read. A second, independent review caught it.
>
> **This is now enforced at ingestion time, not just audited afterwards.** AGENTS.MD
> §ENRICHMENT_AGENT's `STATE: INVENTORY` and `GATE_5-COVERAGE` (added 2026-07-03) make
> building this ledger a mandatory, blocking step of any SOURCE-DOCUMENT MODE ingestion —
> the pipeline cannot hand off to LINK_AGENT/LOG_AGENT while any ledger row is unresolved.
> CHECK_9 below is the safety net for a bundle that predates this fix, or a session that
> skipped STATE: INVENTORY — it is no longer the primary defence.

**Format** — one row per source document being tracked for bundle completeness:

| Field | Meaning |
|---|---|
| `Contract ID` | Short slug identifying the contract. |
| `Coverage ledger file` | Path to the `type: Coverage Ledger` concept enumerating every named unit in the source. |
| `Source document` | The source PDF/text being tracked (with version/date). |
| `Identity key` | How ONE row in the ledger maps to ONE structural unit in the source (a Box/Table/Figure number, a page-anchored callout label, an appendix letter). |
| `Severity` | `ERROR` if an uncaptured unit would misrepresent the source's scope to a reader relying on the bundle as complete (e.g. a director-facing checklist item); `WARNING` if cosmetic (e.g. a front-matter foreword). |

| Contract ID | Coverage ledger file | Source document | Identity key | Severity |
|---|---|---|---|---|
| `directors-guide-coverage` | `errata/source-coverage-ledger.md` | *A Director's Guide to AI Governance* (AICD/HTI, v2, June 2026) | Box N / Table N / Figure N / page-anchored callout label / Appendix letter | ERROR |

CONFORMANCE_AGENT should treat a `Coverage Ledger` row marked anything other than
`Captured` or `Not applicable` as a live gap — see AGENTS.MD §CONFORMANCE_AGENT CHECK_9.

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
| 0.4 | 2026-07-03 | **Remediation pass**, triggered by an independent second review that found v0.3's re-ingestion — despite reading the full source text — still omitted the four recurring "Questions for directors to ask" / "Governance red flags" boxes (pp.30, 33, 39, 43) entirely, plus Box 4, Box 8 and the closing "Over the horizon" section. Root cause: v0.3's audit was a single sequential read with no exhaustive unit-by-unit inventory, so attention (tuned to find "the good stuff": errors, new stats, missing sections) silently deprioritised repetitive-but-real structural content. No existing CHECK_1–7 catches this class of miss — those checks validate internal bundle consistency, not source-document completeness. Added type `Coverage Ledger` and tag `coverage`, and a new **§Source Coverage Contracts** section (deliberately distinct from §Deliverable Parity Contracts — that section catches concept→deliverable drift; this one catches source→bundle omission, which has no deliverable involved). Registered contract `directors-guide-coverage` against `errata/source-coverage-ledger.md`, and added AGENTS.MD CHECK_9 (CHECK_8 was already in use for a log.md placeholder check) so a future CONFORMANCE_AGENT run can catch this mechanically rather than relying on a second re-read. All four Q&A/red-flag boxes, Box 4, Box 8 and "Over the horizon" are now captured; see `log.md`. |
| 0.5 | 2026-07-03 | **Process fix**, moving the safeguard from an after-the-fact audit (CHECK_9, v0.4) to a mandatory ingestion-time step. Added `SOURCE-DOCUMENT MODE` vs `NOTE MODE` to AGENTS.MD's ORCHESTRATOR routing table; added `STATE: INVENTORY` to ENRICHMENT_AGENT (mandatory in SOURCE-DOCUMENT MODE, skipped in NOTE MODE) — a mechanical, structure-driven enumeration pass that runs *before* any concept is written, so the Coverage Ledger is built from the document's own headings/numbering rather than from what a reader happened to notice; added `GATE_5-COVERAGE`, which blocks handoff to LINK_AGENT/INDEX_AGENT/LOG_AGENT while any ledger row remains "Not yet checked"; added Bundle Invariant #11 stating the same rule permanently. §Source Coverage Contracts (above) updated to describe CHECK_9 as the safety net, not the primary defence, now that STATE: INVENTORY exists. No new types/tags — this release is entirely inside AGENTS.MD's agent behaviour plus this explanatory update. |
