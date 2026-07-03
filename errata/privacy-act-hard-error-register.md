---
type: Erratum
title: "Hard-Error Register — Privacy Act / ADM Disclosure Content in the Guide"
description: "Seven audited errors and gaps in the Guide's treatment of the Privacy Act automated-decision-making disclosure duty, graded CONFIRMED / UNSETTLED / REASONED VIEW against the canonical Privacy Act 1988 (Cth) position as at 2 July 2026."
resource: "directors-guide-hard-error-register.md (source audit, supplied by bundle owner)"
tags: ["errata", "regulatory", "privacy", "review-required"]
timestamp: 2026-07-03T02:55:56Z
---

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
