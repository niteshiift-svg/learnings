# Domain Watchlist — Never Collapse Rules

This file defines known capability collapse risks per domain.
The skill must cross-check this list before generating any L1 map.
If the domain matches, apply the rules listed. Flag any collapsed capability with ⚠️ Verify scope.

---

## Legal

**Never collapse:**
- `eDiscovery & Litigation Support` into `Litigation & Dispute Resolution`
  → eDiscovery is a distinct, high-digital, IT-heavy capability. It involves legal hold management, data preservation, ESI collection, and review platforms (Relativity, Reveal). Collapsing it hides significant tech investment and risk.
- `Contract Lifecycle Management (CLM)` into generic `Contract Management`
  → CLM is a platform-driven capability (Ironclad, DocuSign CLM, Icertis). When IT lens is included, always separate CLM as its own entry.
- `Legal Knowledge Management` into `Legal Operations`
  → Especially relevant when GenAI is in scope — legal KM is a distinct AI opportunity zone.

**IT lens — never omit these for enterprise Legal IT maps:**
- `Legal Knowledge Management` — High digital. Often collapsed into Legal Operations but is a distinct AI opportunity zone. Surfaces via Knowledge Management zone in wide scan.
- `Legal Spend & Vendor Management` — Managing outside counsel, billing guidelines, invoice review, budget tracking. Platform class: BrightFlag, TyMetrix, SimpleLegal. Surfaces via Vendor & Spend Management zone.
- `Legal Technology & Infrastructure` — Platform backbone, integrations, and security posture for the legal tech ecosystem. Not the same as Legal Operations tooling. Surfaces via Infrastructure & Security / Platform & Tooling zones.
- `Legal Analytics & Reporting` — Matter status, spend visibility, risk exposure dashboards for leadership. High digital. Surfaces via Data & Analytics zone.

**Always check:**
- Is Privacy a separate function? If yes, exclude `Privacy & Data Governance` from the Legal map entirely.
- Is Risk & Compliance a separate function? If yes, exclude `Regulatory Compliance` from Legal and note it.
- Does the org have a standalone OEC / Ethics function? If yes, `Ethics & Policy Management` may belong there, not in Legal.

---

## Finance

**Never collapse:**
- `Treasury & Cash Management` into `Financial Planning & Analysis`
  → Treasury manages liquidity, hedging, and cash positioning — operationally distinct from FP&A which is forward-looking planning.
- `Controllership & Accounting` into `Finance Operations`
  → Controllership owns the books, period close, and financial reporting integrity. It is not the same as operational finance.
- `Tax Management` into `Regulatory Compliance`
  → Tax is a standalone capability with its own systems (OneSource, Vertex), cross-border complexity, and transfer pricing obligations.
- `Audit & Internal Controls` into `Risk Management`
  → Internal Audit has independence requirements that make it structurally distinct from operational risk.

**Always check:**
- Is Procurement / Sourcing under Finance or a separate function? Shapes whether `Spend Management` appears in this map.
- Does the org have a separate Investor Relations function? If public company, `Investor Relations` is a distinct capability.

---

## HR / Human Capital

**Never collapse:**
- `Talent Acquisition` into `Talent Management`
  → Recruiting, sourcing, and hiring is operationally and system-distinct from performance management, development, and succession. Different platforms (Workday Recruiting vs. Workday Talent).
- `Learning & Development` into `Employee Experience`
  → L&D is a distinct investment center with its own platforms (LMS, content libraries) and metrics (completion, skill gaps).
- `Workforce Planning & Analytics` into `HR Operations`
  → Strategic workforce planning and people analytics is a Dual-lens, high-digital capability — often collapsed but distinct.
- `Compensation & Benefits` into `Total Rewards`
  → Total Rewards is the umbrella; Compensation and Benefits are often managed by separate teams with separate systems.

**Always check:**
- Is Payroll in-house or outsourced? If outsourced, reduce to `Payroll Oversight` rather than a full capability.
- Is DEI a standalone function or embedded in HR? Shapes whether it appears as a separate L1.

---

## Marketing

**Never collapse:**
- `Content Strategy & Production` into `Campaign Management`
  → Content creation, governance, and asset management is a distinct capability — especially when a DAM (Digital Asset Management) system is in scope.
- `Marketing Analytics & Attribution` into `Campaign Management`
  → Analytics and attribution is a Dual-lens, high-digital capability with its own platforms (Adobe Analytics, GA4, MTA models). Always separate.
- `Customer Insights & Research` into `Marketing Strategy`
  → Primary research, segmentation, and persona development is operationally distinct from strategic planning.
- `Brand Management` into `Marketing Communications`
  → Brand standards, architecture, and governance is a distinct capability — especially in multi-brand enterprises.

**Always check:**
- Is Digital Marketing a separate team or embedded? Shapes whether `Digital & Performance Marketing` is its own L1.
- Is Product Marketing under Marketing or Product? Shapes scope of this map.

---

## IT / Technology (Enterprise)

**Never collapse:**
- `Enterprise Architecture` into `IT Strategy & Planning`
  → EA is a distinct discipline with its own governance, tooling (ArchiMate, TOGAF), and accountability for standards and roadmaps.
- `Cybersecurity & InfoSec` into `IT Operations`
  → Security is always a standalone L1 in enterprise IT — it has its own org, budget, platforms, and regulatory obligations.
- `Data Platform & Engineering` into `Application Development`
  → Data infrastructure (lakes, warehouses, pipelines) is operationally and architecturally distinct from application delivery.
- `IT Vendor & Contract Management` into `IT Operations`
  → Vendor lifecycle, SLA governance, and contract management for IT is a distinct capability — especially when third-party spend is significant.

**Always check:**
- Is Cloud Platform Management a distinct team? If yes, separate from general IT Operations.
- Is AI/ML Platform a live program? If yes, `AI & ML Platform Engineering` should appear as a standalone capability, not folded into Data.

---

## Supply Chain

**Never collapse:**
- `Demand Planning & Forecasting` into `Supply Planning`
  → Demand sensing and statistical forecasting is distinct from supply balancing and MPS/MRP execution.
- `Logistics & Transportation` into `Distribution & Fulfillment`
  → Carrier management, freight optimization, and TMS platforms are distinct from warehouse and DC operations.
- `Supplier Relationship Management` into `Procurement`
  → SRM covers ongoing supplier performance, risk monitoring, and development — distinct from transactional buying.
- `Trade Compliance & Customs` into `Logistics`
  → Export controls, tariff classification, and customs clearance is a distinct regulated capability, especially for med-tech and global enterprises.

**Always check:**
- Is Quality Management under Supply Chain or a separate function? In Med-Tech, Quality is often standalone.
- Is Direct vs. Indirect Procurement split? If yes, scope the map to one or note both.

---

## Healthcare / Med-Tech (Industry-Specific)

**Never collapse:**
- `Regulatory Affairs` into `Legal & Compliance`
  → Regulatory Affairs owns FDA/EU MDR submissions, 510(k)/PMA strategy, and post-market surveillance. It is a primary activity in Med-Tech, not a support function.
- `Clinical & Medical Affairs` into `R&D`
  → Clinical evidence generation, KOL management, and medical education are distinct from product R&D.
- `Post-Market Surveillance` into `Quality Management`
  → PMS/PMCF involves ongoing signal detection, vigilance reporting, and regulatory feedback loops — distinct from QMS/manufacturing quality.
- `Health Economics & Market Access` into `Commercial / Sales`
  → HEOR, payer evidence, and reimbursement strategy is a distinct capability that bridges clinical and commercial.

**Always check:**
- Is Quality Management (QMS) under Operations or standalone? In Med-Tech, Quality is almost always a primary standalone domain.
- Is Cybersecurity for medical devices (SaMD, connected devices) in scope? If yes, it warrants a dedicated capability separate from enterprise IT security.

---

## Digital Commerce / E-Commerce

**Never collapse:**
- `eDiscovery & Litigation Support` — not applicable here, but flag if Legal is in scope
- `Search & Merchandising` into `Product Catalog Management`
  → Search relevance, ranking algorithms, and merchandising rules are distinct capabilities — often the highest-ROI optimization area in commerce.
- `Personalization & Recommendations` into `Customer Experience`
  → ML-driven personalization is a distinct, high-digital, Competitive Edge capability with its own platform (Recommendation engines, CDP).
- `Checkout & Payment` into `Order Management`
  → Checkout UX and payment processing have distinct ownership, platform dependencies, and compliance obligations (PCI-DSS).
- `Fraud Detection & Risk` into `Payments`
  → Fraud scoring and chargeback management is a distinct capability — often owned by a separate Risk or Trust & Safety team.

**Always check:**
- Is Marketplace (seller/vendor management) in scope, or is this a 1P commerce model only?
- Is B2B and B2C in scope together? If yes, scope the map to one model or note both — capability sets diverge significantly.
