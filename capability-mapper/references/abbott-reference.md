# Abbott Reference — Org Boundaries & Domain Context

This file provides Abbott-specific org boundary context for use with the capability-mapper skill.
When mapping any domain for Abbott, cross-check this file to ensure structural accuracy.

Do NOT embed this into SKILL.md — keep the core skill generic EA/BA.
Load this file when Nitesh explicitly says "this is for Abbott" or context makes it clear.

---

## Abbott Org Structure — Known Boundaries

### Privacy
- **Privacy is a standalone function at Abbott** — not embedded in Legal.
- Has a dedicated Chief Privacy Officer (CPO) structure.
- When mapping Legal for Abbott: **exclude Privacy & Data Governance** from the Legal map.
- Privacy & Data Governance should appear as its own top-level domain map if in scope.

### OEC (Office of Ethics & Compliance)
- **OEC is a standalone function at Abbott** — separate from Legal.
- Owns Code of Business Conduct, compliance training, ethics hotline, third-party compliance.
- When mapping Legal for Abbott: **exclude Ethics & Policy Management** — it belongs to OEC.
- When mapping Regulatory Compliance for Abbott: scope carefully — OEC owns enterprise-wide compliance, while Regulatory Affairs owns FDA/MDR-specific regulatory submissions.

### Regulatory Affairs
- **Regulatory Affairs is a standalone primary domain at Abbott** — not a sub-capability of Legal or Compliance.
- Owns FDA submissions (PMA, 510(k)), EU MDR/IVDR, post-market surveillance, regulatory strategy.
- In Med-Tech context: Regulatory Affairs is a **primary activity** on the value chain (not support).
- Do not collapse into Legal & Compliance.

### Quality Management
- **Quality Management (QMS) is a standalone function at Abbott** — not embedded in Operations or Supply Chain.
- Owns QMS, CAPA, design controls, manufacturing quality, supplier quality.
- In Abbott's Med-Tech divisions: Quality reports independently, often at VP level.
- Keep separate from Regulatory Affairs (though closely linked operationally).

### IT Structure
- Abbott IT is largely **centralized under BTS (Business Technology Solutions)**.
- BTS serves multiple divisions: ARDx (diagnostics), nutrition, established pharma, vascular, electrophysiology.
- Enterprise capabilities (ERP, infrastructure, security, AI/data) live in BTS.
- Divisional IT is embedded within business units for execution but governed centrally.
- When assigning Lens for Abbott: **Dual** assignments are common given BTS partnership model.

### AI & Data (AI COE)
- Abbott has an **AI Center of Excellence (AI COE)** as a cross-functional program.
- AI COE sits at the intersection of BTS and business strategy.
- **AI & ML Platform Engineering** is a live, active program — do not fold into general Data Platform.
- GenAI programs in scope: Mia (enterprise knowledge assistant), Marketing GenAI, Regulatory Document Drafting Lighthouse.
- When mapping AI & Data for Abbott: always separate AI COE governance from AI platform delivery.

### Finance
- Treasury, Tax, and Internal Audit are standalone at Abbott enterprise level.
- Investor Relations is a distinct function (Abbott is NYSE-listed: ABT).
- Procurement/Sourcing: Abbott has a global procurement organization — not embedded in Finance.

### Supply Chain
- Abbott Supply Chain is complex: dual-use (nutrition + diagnostics + devices).
- **Trade Compliance & Customs** is a live, distinct capability — Abbott exports globally across regulated product categories.
- Quality Management is **not** under Supply Chain at Abbott — it is standalone.
- Direct vs. Indirect Procurement is split: Global Procurement handles indirect; divisional ops handle direct materials.

### HR / Human Capital
- Abbott HR is enterprise with divisional HRBPs.
- DEI is embedded in HR, not standalone at the L1 level.
- Payroll is managed in-house (not fully outsourced).
- Learning & Development: Abbott University exists as a distinct platform — L&D is a separate L1 capability.

---

## Abbott Industry Context

**Primary Industry:** Med-Tech, Healthcare, Life Sciences

**Regulatory environment:**
- FDA (US): PMA, 510(k), De Novo, IDE
- EU: MDR (Medical Device Regulation), IVDR (In Vitro Diagnostic Regulation)
- Post-market: PMCF (Post-Market Clinical Follow-Up), PMS (Post-Market Surveillance), Vigilance reporting
- Documents in scope: PMA, 510(k), CER (Clinical Evaluation Report), CEP, SSCP, IFU (Instructions for Use)

**GenAI tools in scope at Abbott:**
- Collate, Acolad, VML, Microsoft Copilot
- Mia — Abbott's enterprise GenAI knowledge assistant (internal)

**Strategic imperatives (Abbott Digital):**
- Instant Convenience
- Enhanced Digital Experiences
- Digitally Integrated Health & Wellness Experiences
- Personalization & Loyalty

---

## How to Use This File

When Nitesh says "this is for Abbott" or context clearly indicates Abbott:

1. Load this file before generating the L1 map
2. Apply the boundary overrides above for the relevant domain
3. Note in the Org Context Note: *"Boundaries reflect Abbott-specific org structure per abbott-reference.md"*
4. If a capability was excluded based on Abbott boundaries (e.g., Privacy excluded from Legal), call it out explicitly in the Completeness Check

Do not apply Abbott boundaries to generic/other-org maps.
