---
type: Concept
title: "AI Governance Practices"
description: "Boards must oversee how AI risks are identified and managed through existing frameworks, including vendor risk and cyber security."
resource: "A Director's Guide to AI Governance (AICD/HTI, v2, June 2026), pp.35-39"
tags: ["governance", "operating-model", "practices"]
timestamp: 2026-07-13T03:05:00Z
---

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

Organisations should review privacy policies and processes for AI-specific risks — for example, AI agents collecting personal information during interactions, or personal information used to train in-house models. From **10 December 2026**, organisations subject to the Privacy Act using ADM systems must meet new disclosure requirements — see [Privacy Act ADM Disclosure Duty](/foundations/privacy-act-adm-disclosure.md) for the corrected APP 1.7 applicability gate and APP 1.8 three-limb kinds-based test (the Guide's own summary of this duty on this page is inconsistent with its Appendix A wording — see [Hard-Error Register — HE-1](/errata/privacy-act-hard-error-register.md)). Some organisations go beyond minimum disclosure — CBA's *Our Approach to Adopting AI* (2025) report is cited as a notable transparency example.

## Questions for directors to ask (p.39)

1. What steps are we taking to be confident that we are meeting our legal and regulatory obligations for the use of AI and associated data collection, storage, and use?
2. Does our risk management framework adequately address our AI-related risks? Does it differentiate between high-risk and low-risk AI applications?
3. What controls are in place to manage agentic risks?
4. Do our existing privacy, data governance, cyber and procurement policies address AI?

## Governance red flags (p.39)

1. The organisation's risk management framework does not address AI risks.
2. There is no process to assess and evaluate the risks of any AI enabled application or system.
3. Agentic AI systems have been adopted without rigorous risk identification and controls.
4. Data governance and privacy controls and policies have not been reviewed to ensure they are fit for purpose for AI systems.

## Related Concepts
* [Case Study: Atlassian's Responsible Tech Review](/case-studies/atlassian-case-study.md)
* [Case Study: Commonwealth Bank of Australia (CBA)](/case-studies/cba-case-study.md)
* [AI Governance Structure](/operating-model/governance-structure.md)
* [AI Strategy Alignment](/operating-model/strategy.md)
* [AI Opportunities and Risks](/foundations/opportunities-and-risks.md)
* [The Role of the Board and the Regulatory Landscape](/foundations/board-role-regulatory-landscape.md)
* [Privacy Act ADM Disclosure Duty](/foundations/privacy-act-adm-disclosure.md)
