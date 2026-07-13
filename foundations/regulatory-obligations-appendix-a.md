---
type: Reference
title: "Appendix A: Regulatory Obligations and AI"
description: "The Guide's full Appendix A survey of existing Australian laws relevant to developing and using AI systems, current as at June 2026: privacy, consumer law, anti-discrimination, industrial relations, WHS, negligence, environmental reporting, cyber security and copyright."
resource: "A Director's Guide to AI Governance (AICD/HTI, v2, June 2026), Appendix A, pp.48-50"
tags: ["regulatory", "foundations", "appendix"]
timestamp: 2026-07-13T03:05:00Z
---

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
or interests and the program uses their personal information. Full APP 1.7 gate order,
what the duty does **not** require, enforcement tiers, and unsettled points: see
[Privacy Act ADM Disclosure Duty](/foundations/privacy-act-adm-disclosure.md) (legal
authority: companion `privacy-act-okf`).

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
