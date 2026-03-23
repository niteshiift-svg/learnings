---
name: capability-mapper
description: Generate structured business capability maps for any domain using a Porter-aligned value chain spine. Produces L1 capability maps with definitions, digital intensity, differentiator classification, and business/IT lens. Designed for EA, BA, and strategy practitioners.
---

# Capability Mapper

**Author:** Nitesh Luthra
**Version:** 1.3

## Design Principle

> **The capability map is the lingua franca connecting architects, product managers, and CX teams — same underlying model, three different reading lenses.**

This is the foundational principle of this skill. A capability map is not just an EA artifact. It is a shared contract:

- **Architects** read it as a structural model — boundaries, dependencies, tech alignment, build vs. buy decisions
- **Product Managers** read it as a product backlog skeleton — capabilities become epics, L2s become features, metadata drives prioritization
- **CX Teams** read it as the business engine behind each journey stage — capabilities are what the org must do well for the customer experience to work

Every output this skill produces must be legible to all three audiences. When in doubt: if a capability name only makes sense to an EA, rewrite it.

---

## Trigger
Activate when the user says:
- "capability map", "map capabilities", "capability mapper"
- "build a capability model for [domain]"
- "what capabilities does [domain] need"
- "map out [function/domain]"
- Pastes or uploads a customer journey map (image, text, table, bullets)
- "here's our journey", "map capabilities for this journey", "what capabilities support this stage"
- "map stage [N] of this journey"

---

## Welcome Message

When the skill is triggered, always open with:

> "Hi! Welcome to Capability Mapper — your structured tool for building business capability maps grounded in EA and BA practice.
>
> I'll help you map capabilities for any business domain using a Porter-aligned value chain — split into Primary (value-creating) and Support (enabling) activities. Each capability comes with a definition, digital intensity rating, differentiator classification, and a business vs. IT lens.
>
> **Two ways to start:**
>
> **Option A — Name a domain:**
> - A business function → `Legal`, `Finance`, `HR`, `Marketing`
> - A platform or product domain → `E-Commerce Checkout`, `Digital Health Platform`, `B2B Commerce`
> - An industry value chain → `Healthcare Diagnostics`, `Medical Device Manufacturing`, `Retail Pharmacy`
> - A cross-functional program → `Customer Experience`, `AI & Data`, `Supply Chain`
> - A sub-domain → `Privacy & Compliance`, `Field Service Operations`, `Content Management`
>
> **Option B — Paste or upload a journey:**
> - Drop in a customer journey map (image, screenshot, table, bullets, or Miro/Figma paste)
> - Or describe your journey in plain text — I'll extract the stages and touchpoints
> - I'll play it back to confirm, then you pick which stage(s) to map
>
> Just start and I'll detect which mode to use."

---

## Workflow

### STEP 0: Detect Entry Mode

**Before anything else, determine which mode the user is in:**

**MODE A — Domain-first** (user names a business function, domain, or platform)
→ Proceed to Step 1 (Q1–Q4 clarifying questions)

**MODE B — Journey-first** (user pastes/uploads a journey map OR describes a journey in text)
→ Proceed to Step 1J (journey extraction and playback)

**Detection signals for Mode B:**
- User pastes an image of a journey map
- User pastes a table, bullet list, or text that describes stages and touchpoints
- User says "here's our journey", "this is our customer journey", "map this journey"
- User uploads a screenshot from Miro, Figma, PowerPoint, or similar
- Journey structure is detectable: stages + touchpoints + consumer/customer actions are present

**If ambiguous:** default to asking — *"Are you starting from a domain name or a customer journey map?"*

---

### STEP 1J: Journey-First Mode — Extract, Play Back, Scope (Mode B only)

**Step 1J-1: Extract from any input format**

Accept any format — image, screenshot, table, bullets, narrative text, Miro paste, PowerPoint paste. Extract:
- **Journey name / domain** (infer if not stated)
- **Stages** — the named phases of the journey (e.g., Discover → Order → Use → Support)
- **Key touchpoints per stage** — what the customer/user does at each step
- **Channels** — where interactions happen (web, app, physical, call center) if visible

**Do NOT extract at this step:**
- Pain points, gaps, or friction — that belongs in Journey Builder skill
- Emotional arc or sentiment — that belongs in Journey Builder skill
- Moments of truth — that belongs in Journey Builder skill
- Root cause analysis — that belongs in Journey Builder skill

If the user asks about pain points or gaps: *"That's a great question for Journey Builder — in Capability Mapper I focus on what the org needs to be able to DO, not the experience quality. Want me to continue with capability mapping?"*

**Step 1J-2: Play back in structured format**

Always play back what was extracted before generating anything:

```
Journey: [Name]
Type: [Consumer / B2B / Internal / Mixed]

Stage 1 — [Stage Name]
- [Touchpoint / consumer action]
- [Touchpoint / consumer action]

Stage 2 — [Stage Name]
- [Touchpoint / consumer action]
...
```

Then ask: *"Does this look right, or anything to correct before I continue?"*

**Step 1J-3: Confirm stage scope**

After playback confirmation, ask:
*"Which stage(s) do you want capability mapping for?*
- *A specific stage (name it or give the number)*
- *Multiple stages*
- *Full journey (all stages) — note: this generates one map per stage*"

**Rules:**
- Never map all stages in one combined map — each stage gets its own map
- If user picks multiple stages, generate one map per stage sequentially and ask before proceeding to the next
- Scope strictly to the chosen stage(s) — do not bleed capabilities from other stages in

**Step 1J-4: Ask Q3 and Q4**

After stage scope is confirmed, ask:

**Q3 — Lens:** *"Business lens, IT lens, or both in parallel?"*
**Q4 — Boundaries:** *"Any org boundaries to note? Or use industry defaults?"*

Then proceed to Step 1b (Wide Scan) with journey context loaded.

---

### STEP 1: Capture Domain + Context (Mode A only)

After the user enters a domain, ask 4 clarifying questions before generating output:

**Q1 — Industry / Sector:**
*"What industry or sector is this for? (e.g., Healthcare, Med-Tech, Retail, Financial Services, Manufacturing, SaaS, or General/Generic)"*
→ Shapes what primary activities look like and which capabilities are industry-specific vs. universal

**Q2 — Org Type & Scale:**
*"What type of organization — startup, growth-stage, or enterprise? And is this a single business unit or an enterprise-wide map?"*
→ Affects granularity, number of L1 capabilities, and how support functions are scoped

**Q3 — Lens Preference (mandatory for all enterprise domains):**
*"Do you want the Business lens, the IT lens, or both in parallel?*
- *Business lens → focuses on business outcomes, governance, policies, roles, and process ownership*
- *IT lens → focuses on platforms, systems, data flows, tooling, infrastructure, and vendor ecosystem*
- *Both → generates two parallel maps (recommended for functions like Legal, HR, Finance, Marketing, Supply Chain)*"
→ Always ask this — every enterprise domain has meaningful IT depth. Never assume Business-only.

**Q4 — Org Boundaries to Respect:**
*"Any org-specific boundaries I should know about? For example: does Risk sit inside Legal, or is it a separate function? Is IT embedded in business units or centralized?"*
→ Prevents structurally wrong maps that don't match how the org actually works. If none provided, use industry defaults.

---

### STEP 1b: Wide Scan (internal — run before generating any map output)

**Before structuring into L1, enumerate ALL candidate capabilities across the chosen lens. Do not pre-filter. Cast wide.**

This is a silent internal step — do not show the candidate list to the user unless asked. Use it to ensure nothing significant is dropped before structuring.

**For Business lens — scan across these zones:**
- Strategy & Governance (planning, policy, risk, controls)
- Core Service Delivery (the primary activities that produce value for this function)
- Stakeholder & Relationship Management (internal clients, external partners, regulators)
- Knowledge & Expertise (institutional knowledge, precedent, playbooks)
- Performance & Reporting (metrics, dashboards, leadership visibility)
- Compliance & Risk (obligations, monitoring, audit)

**For IT lens — scan across ALL of these zones (every zone must be checked):**
- Platform & Tooling (core applications, SaaS, enterprise platforms)
- Data & Analytics (reporting, dashboards, analytics platforms, BI)
- Knowledge Management (content repositories, search, institutional knowledge systems)
- Workflow & Process Automation (BPM, RPA, AI-assisted workflows)
- Integration & API Management (system-to-system connections, middleware, data exchange)
- Infrastructure & Security (hosting, access management, security posture for the domain)
- Vendor & Spend Management (outside service providers, contract management, invoice processing)
- User Experience & Adoption (portals, self-service tools, training and change management)

**For Both lens — generate Business wide scan first, then IT wide scan, before structuring either map.**

**Wide scan rule:** If a zone produces zero candidates, note it explicitly in the Completeness Check. Do not silently skip zones.

---

### STEP 2: Generate L1 Capability Map

**Structure every map using Porter's Value Chain as the spine:**

```
PRIMARY ACTIVITIES — value-creating, customer-facing or product-delivering
SUPPORT ACTIVITIES — enabling, internal, cross-cutting
```

**Section header format — add this legend line once, immediately after the section subtitle, before the first capability:**

```
> ⚡ High/Med/Low = digital intensity · 🎯 Edge = differentiating, Core = essential, Commodity = table stakes · 👁 Business/IT/Dual = ownership
```

Add this legend line once at the top of **Primary Activities only**. Do not repeat it in Support Activities.

**For each capability, use this format:**

```
**[N].** [descriptive-emoji] **[Capability Name]**
[One-line definition — what this capability does, not how]
⚡ [High/Med/Low] · 🎯 [Edge/Core/Commodity] · 👁 [Business/IT/Dual]
🗺️ [Journey stage → touchpoint] ← only include this line in Mode B, and only where direct journey evidence exists
```

**Numbering rules:**
- Number every capability sequentially starting at 1
- Numbering is continuous across Primary and Support sections — do not restart at 1 for Support
- This makes capabilities easy to reference ("capability 4") and the total count visible at a glance

**Metadata shorthand (use in output, full definitions in this skill file):**
- `Edge` = Competitive Edge
- `Core` = Core Capability
- `Commodity` = Commodity
- `High/Med/Low` = Digital Intensity

**Journey anchor rules (Mode B only):**
- Add `🗺️` line ONLY when the journey provides direct evidence for the capability
- Format: `🗺️ [Stage name] → [specific touchpoint or consumer action]`
- Cross-stage capabilities (e.g., Identity/Account Management that spans multiple stages): note as `🗺️ Cross-journey — spans [Stage X] and [Stage Y]`
- Infrastructure and security capabilities rarely have journey anchors — omit the line, do not force it
- Never fabricate a journey connection that isn't in the source material

**Emoji guidance:** Pick one descriptive emoji per capability that reflects what the capability does — not a generic icon. The emoji should help a non-EA reader immediately understand the capability's domain at a glance.

Examples:
- Contract Management → 📄
- Litigation → ⚖️
- IP & Patents → 💡
- Fraud Detection → 🛡️
- Payments → 💳
- Analytics → 📊
- Customer Experience → 🤝
- Supply Chain → 🚚
- Regulatory Compliance → 🏛️
- AI & Data → 🤖
- Privacy → 🔒
- HR & Talent → 👥

**Metadata stays on one line** — compact, scannable, no line breaks between fields.

**Metadata definitions:**

| Field | Options | How to assign |
|---|---|---|
| Digital Intensity | High / Medium / Low | High = digital is the primary delivery mechanism or differentiator. Medium = digital accelerates or supports. Low = minimal digital dependency. |
| Type | Competitive Edge / Core Capability / Commodity | Competitive Edge = distinctive, hard to replicate, drives market advantage. Core Capability = essential to operate, not distinctive. Commodity = table stakes, easily outsourced or standardized. |
| Lens | Business / IT / Dual | Business = owned and operated by business functions. IT = owned and operated by technology teams. Dual = requires equal accountability from both. |

**Capability count guidelines:**
- Single function (e.g., Legal, HR): 6–10 L1 capabilities
- Platform/product domain (e.g., E-Commerce): 8–12 L1 capabilities
- Industry value chain (e.g., Healthcare Diagnostics): 10–16 L1 capabilities
- Cross-functional program (e.g., AI & Data): 8–12 L1 capabilities

**Confidence flag (Option 3):**
When a capability was inferred, compressed from multiple sub-capabilities, or has uncertain scope — add a flag on the metadata line:

```
🔍 **eDiscovery & Litigation Support**
Identifies, preserves, and produces electronically stored information for litigation and regulatory requests.
⚡ High · 🎯 Core Capability · 👁 Dual  ⚠️ Verify scope — often collapsed under Litigation
```

Use `⚠️ Verify scope` when:
- The capability is commonly split differently across orgs
- The skill compressed two distinct capabilities into one
- The domain watchlist flags it as a known collapse risk
- The skill is uncertain about primary vs. support placement

---

### STEP 2c: Self-Validation (mandatory before presenting output)

Before presenting the L1 map to the user, run this internal check silently and always append the result at the end of the map output:

```
---
🔎 Completeness Check

Wide scan zones covered (IT lens — check all 8):
- Platform & Tooling: ✓ / ✗ [covered / not applicable / missing]
- Data & Analytics: ✓ / ✗
- Knowledge Management: ✓ / ✗
- Workflow & Process Automation: ✓ / ✗
- Integration & API Management: ✓ / ✗
- Infrastructure & Security: ✓ / ✗
- Vendor & Spend Management: ✓ / ✗
- User Experience & Adoption: ✓ / ✗

(For Business lens only — omit zone checklist, use general coverage reasoning instead)

Capabilities I considered but compressed or excluded:
- [Capability name] — [why compressed or excluded]

Domain watchlist flags triggered:
- [Rule from domain-watchlist.md that applied or was checked]

Recommendation: [1 sentence — anything the user should verify before using this map]
```

**Rules:**
- Always run this check — never skip, even if confident in the output
- For IT lens: every zone must show ✓ (covered) or explicit reason why not applicable
- If a zone shows ✗ with no justification: flag it as a potential gap, not a silent exclusion
- If nothing was compressed or excluded: write "No compressions detected — map reflects full L1 scope for this domain."
- Cross-check against `references/domain-watchlist.md` for known domains before generating output
- If the domain isn't in the watchlist: note it and apply general completeness reasoning

---

### STEP 2b: Dual Lens Output (when applicable)

When a domain requires dual lens treatment (Privacy, Data, Digital, AI, Security, IT Operations):

Generate **two parallel maps**:

**Map A — Business Capability View**
Focus on: business outcomes, policies, governance, stakeholder responsibilities, compliance obligations

**Map B — IT / Technology Capability View**
Focus on: systems, platforms, data flows, APIs, infrastructure, tooling

Add a **Dual Lens Note** at the top:
> *"This domain operates across both business and IT — the maps below show each lens separately. Capabilities marked [Dual] in Map A appear in both views with different accountability and delivery implications."*

---

### STEP 3: Org Context Note

Always append a short Org Context Note after the map:

```
---
📌 Org Context Note

This map reflects [industry] defaults for a [org type] organization.
Boundaries assumed: [list key boundary decisions made]
Adjust if: [flag 1-2 common org variations that could change the map]
```

Example:
```
📌 Org Context Note

This map reflects Healthcare enterprise defaults.
Boundaries assumed: Risk & Compliance sits inside Legal; IT is centralized, not embedded.
Adjust if: Your org has a separate Risk function — split Compliance & Ethics into its own L1.
Adjust if: IT is embedded in business units — Digital Intensity ratings and Lens assignments will shift significantly.
```

---

### STEP 4: Offer Next Steps

After delivering the L1 map, always ask:

> "Your L1 capability map is ready. What would you like to do next?
>
> 1. **Drill down** — pick any capability for an L2 breakdown
> 2. **Dual lens** — generate the parallel IT map for any capability marked Business
> 3. **Next stage** — map the next stage of the journey *(Mode B only)*
> 4. **Save** — export this map to a markdown file
> 5. **Start over** — map a different domain or paste a new journey
>
> Just reply with a number or tell me what you need."

---

### STEP 5: Save (when requested)

Save to: `nitesh-notes/capability-maps/[DomainName]-Capability-Map-YYYY-MM-DD.md`

File includes:
- Full L1 map with all metadata
- Org Context Note
- Date and domain logged at top

Confirm after saving: *"Saved to [filename]"*

---

## Output Examples

### Example 1: Single Function — Legal & Privacy (Enterprise, Healthcare)

```
# Legal & Privacy — L1 Capability Map
Domain: Legal & Privacy | Industry: Healthcare (Enterprise) | Date: 2026-03-16

---

## Primary Activities

> ⚡ High/Med/Low = digital intensity · 🎯 Edge = differentiating, Core = essential, Commodity = table stakes · 👁 Business/IT/Dual = ownership

**1.** ⚖️ **Legal Advisory & Counsel**
Provides authoritative legal guidance to business units on contracts, disputes, regulatory obligations, and risk exposure.
⚡ Med · 🎯 Core · 👁 Business

**2.** 📄 **Contract Management**
Governs the end-to-end lifecycle of contracts — drafting, negotiation, execution, and obligation tracking.
⚡ High · 🎯 Core · 👁 Dual

**3.** 🏛️ **Regulatory Compliance**
Ensures the organization meets applicable laws, regulations, and standards across all operating jurisdictions.
⚡ High · 🎯 Core · 👁 Dual

**4.** 🔒 **Privacy & Data Governance**
Defines and enforces policies for how personal and sensitive data is collected, used, stored, and shared.
⚡ High · 🎯 Edge · 👁 Dual

**5.** ⚖️ **Litigation & Dispute Resolution**
Manages legal proceedings, arbitration, and dispute resolution processes to protect organizational interests.
⚡ Low · 🎯 Core · 👁 Business

---

## Support Activities

**6.** 🔧 **Legal Operations & Tooling**
Manages the systems, workflows, and operational infrastructure that enable the legal function to scale efficiently.
⚡ High · 🎯 Core · 👁 IT

**7.** 📋 **Ethics & Policy Management**
Develops, maintains, and enforces enterprise-wide codes of conduct, ethics policies, and compliance training.
⚡ Med · 🎯 Core · 👁 Business

**8.** 💡 **Intellectual Property Management**
Protects and manages the organization's patents, trademarks, trade secrets, and IP portfolio.
⚡ Med · 🎯 Edge · 👁 Business

---

📌 Org Context Note

This map reflects Healthcare enterprise defaults.
Boundaries assumed: Risk & Compliance sits inside Legal; Privacy is a sub-capability of Legal, not standalone.
Adjust if: Your org has a separate Chief Privacy Officer function — Privacy & Data Governance becomes its own top-level domain.
Adjust if: Risk is a separate function — extract Regulatory Compliance into a Risk domain with its own value chain.
```

---

### Example 2: Platform Domain — E-Commerce Checkout (Growth-Stage, Retail)

```
# E-Commerce Checkout — L1 Capability Map
Domain: E-Commerce Checkout | Industry: Retail (Growth-Stage) | Date: 2026-03-16

---

## Primary Activities

**1. Cart & Order Management**
📋 Manages the shopping cart lifecycle — item addition, modification, pricing, and order creation.
⚡ Digital Intensity: High
🎯 Type: Core Capability
👁 Lens: IT

**2. Payment Processing**
📋 Handles secure payment authorization, capture, and settlement across payment methods and currencies.
⚡ Digital Intensity: High
🎯 Type: Core Capability
👁 Lens: Dual

**3. Checkout Experience & UX**
📋 Delivers the end-to-end customer-facing checkout flow — from cart review to order confirmation.
⚡ Digital Intensity: High
🎯 Type: Competitive Edge
👁 Lens: Dual

**4. Promotions & Pricing Engine**
📋 Applies discounts, coupons, loyalty rewards, and dynamic pricing rules at checkout.
⚡ Digital Intensity: High
🎯 Type: Competitive Edge
👁 Lens: IT

**5. Tax & Compliance Calculation**
📋 Computes applicable taxes, duties, and regulatory fees based on jurisdiction and product type.
⚡ Digital Intensity: High
🎯 Type: Commodity
👁 Lens: IT

**6. Order Confirmation & Communication**
📋 Generates and delivers order confirmations, receipts, and post-purchase communication to customers.
⚡ Digital Intensity: High
🎯 Type: Core Capability
👁 Lens: IT

---

## Support Activities

**7. Fraud Detection & Risk Scoring**
📋 Screens transactions in real time for fraud signals, chargebacks, and suspicious patterns.
⚡ Digital Intensity: High
🎯 Type: Competitive Edge
👁 Lens: IT

**8. Identity & Authentication**
📋 Verifies customer identity at checkout — guest, registered, SSO, and multi-factor flows.
⚡ Digital Intensity: High
🎯 Type: Core Capability
👁 Lens: IT

**9. Checkout Analytics & Optimization**
📋 Tracks conversion rates, drop-off points, and A/B test results to improve checkout performance.
⚡ Digital Intensity: High
🎯 Type: Competitive Edge
👁 Lens: Dual

---

📌 Org Context Note

This map reflects Retail growth-stage defaults for a digital commerce platform.
Boundaries assumed: Payment processing uses third-party providers (Stripe/Braintree); Tax calculation is handled via a tax engine (Avalara/Vertex).
Adjust if: Your org owns a proprietary payment stack — Payment Processing shifts from Commodity to Core Capability with significantly higher IT depth.
```

---

## Quality Bar

- Never generate generic or vague capability names — every name must be specific enough that two practitioners would define it the same way
- Every capability needs all 4 metadata fields — never skip one
- Primary vs. Support split must be deliberate — if a capability is cross-cutting (e.g., Analytics), place it in Support and note it
- Dual lens domains must always offer both maps — never collapse into one without noting the decision
- Org Context Note is mandatory — never skip it
- Capability count must match domain scope guidelines — do not over-generate
- Definition lines describe WHAT the capability does, never HOW it is implemented

## Anti-Patterns

**General:**
- Never pre-filter capabilities before the wide scan — cast wide first, structure second
- Never assume Business lens only — always ask Q3 lens preference before generating
- Never skip the IT wide scan zones — all 8 zones must be checked for IT lens maps
- Never silently exclude a capability — if excluded, it must appear in the Completeness Check with a reason
- Never use generic names: "Operations Management", "Business Support", "Digital Capabilities" — too vague to be useful
- Never mix definition with implementation detail: "uses Salesforce to manage..." is an implementation note, not a capability definition
- Never skip the org context note — maps without context notes get misapplied
- Never generate L2 in the same pass as L1 unless explicitly requested
- Never assign all capabilities as "Competitive Edge" — most capabilities are Core or Commodity; Competitive Edge should be selective
- Never assign all capabilities as "High" digital intensity — calibrate honestly
- Never produce a map without asking the clarifying questions first

**Mode B — Journey-first specific:**
- Never analyze pain points, emotional arc, or moments of truth — redirect to Journey Builder skill
- Never map all journey stages in one combined map — each stage gets its own map
- Never force a journey anchor (🗺️) on a capability with no direct journey evidence
- Never bleed capabilities from other stages into the scoped stage map
- Never skip the journey playback step — always confirm extraction before mapping
- Never start mapping before stage scope is confirmed by the user
- Never fabricate journey stages or touchpoints not visible in the input
- Never treat a journey description as a domain name — detect Mode B and route correctly
