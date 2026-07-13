---
type: Concept
title: "Privacy Act ADM Disclosure Duty"
description: "From 10 December 2026, privacy policies must disclose the kinds of personal information, and kinds of solely- and substantially-assisted decisions, made by a computer program with a significant effect on an individual."
resource: "A Director's Guide to AI Governance (AICD/HTI, v2, June 2026), pp.18, 39, 49; Privacy and Other Legislation Amendment Act 2024 (Cth) sch 1 pt 15; privacy-act-okf (legal authority)"
tags: ["governance", "regulatory", "privacy", "foundations"]
timestamp: 2026-07-13T02:45:00Z
---

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

> **Legal authority.** Privacy Act APP 1.7–1.9 facts in this concept are kept aligned to
> the companion bundle `privacy-act-okf` (master projection
> `projections/privacy-act-adm-master.md`, Log head **2026-07-06** at last re-audit). Board
> framing stays in this bundle; statutory position follows that authority. Contested items
> stay UNSETTLED until that bundle re-grades them (binding OAIC guidance expected
> ~September 2026).

## When the duty applies — APP 1.7 (stop at the first NO)

The disclosure duty switches on only if **every** condition below is met. Evaluate in this
order (cheapest filters first; the contested limb last):

| Step | Question | If NO |
|---|---|---|
| 0 | Is the organisation an **APP entity**? (Turnover above A$3M, **or** smaller but caught regardless: health-service provider holding health information, trades in personal information, Commonwealth contracted service provider, residential-tenancy-database operator.) | Out of scope |
| 1 | Is **personal information** about the individual used in running the program? (Genuine de-identification exits here; reversible pseudonymisation does **not**.) | Out of scope |
| 2 | Could the decision reasonably be expected to **significantly affect** the person's rights or interests? (More than trivial; adverse **or** beneficial — APP 1.7(b), APP 1.9(c).) | Out of scope |
| 3 | Did the organisation **arrange for a computer program** to make the decision, or to do a thing **substantially and directly related** to making it? (Includes human-assisted decisions where a person signs off but the program did the substantive work. The "substantially and directly related" margin is **UNSETTLED**, pending OAIC binding guidance ~September 2026.) | Out of scope |
| 4 | Does an **exemption** apply? (Employee-records exemption s 7B(3) covers current/former employees only — not applicants, volunteers, government employers, or third-party HR vendors. See [HE-3](/errata/privacy-act-hard-error-register.md).) | If an exemption applies → out; if none → continue |

If all steps pass and no exemption applies → **APP 1.8 disclosure is required**. Always name
the deciding condition and its confidence (CONFIRMED / UNSETTLED) before stating a firm
in/out conclusion.

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

## What this duty does **not** require

APP 1.7–1.9 create a **privacy-policy update only**. They do **not** create:

- a right for individuals to **contest** an automated decision, or to refuse being subject to one;
- a right to the **reasoning behind a specific decision**;
- an obligation to **notify each affected person** when ADM is used for their decision;
- a **mandatory Privacy Impact Assessment** (though the OAIC treats PIAs as a reasonable step for high-risk AI);
- **per-decision audit logging** beyond existing APP obligations.

## Board-use boundary

Using AI to **digest board papers, minutes, or pack material** for the board's own governance
work is **not**, by itself, an APP 1.7 trigger. The ADM disclosure duty applies where a
computer program makes, or substantially and directly assists in making, a decision **about
an identifiable individual** using that person's personal information. Do not conflate
Corporations Act board-process risk (e.g. *ASIC v Bekier*, s 180) with the Privacy Act ADM
test unless those individual-decision conditions are met.

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
penalty-unit figures and dollar values (current from 1 July 2026), including the mid-market
worked case that separates s 13K, s 13H, and s 13G.

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
