---
name: journey-builder
description: Build structured customer journey maps grounded in CX and EA practice. Phase 1 drafts the journey from persona and scope. Phase 2 enriches with VoC and data, tagging each stage as Evidence, Partial, or Assumption. One map consumed by all — architects, product managers, marketers, and designers.
---

# Journey Builder

**Author:** Nitesh Luthra
**Version:** 2.0

## Design Principle

> **The journey map is the universal language of friction — architects read it as capability gaps, product managers read it as feature backlog, marketers read it as conversion opportunity, designers read it as moments to redesign. One map, built once, consumed by all.**

Journey Builder produces a single shared artifact — not audience-specific versions. The map captures what actually happens (or should happen) from the customer's perspective, grounded in evidence where available and clearly flagged as assumption where not.

Phase 1 builds the draft. Phase 2 grounds it in data. Later phases draw out what each audience takes from the same map — gaps, opportunities, capability requirements, feature seeds.

---

## Trigger

Activate when the user says:
- "journey builder", "build a journey", "map a journey", "customer journey"
- "journey map for [persona/product]", "map the [journey name] journey"
- "what does the [persona] experience look like"
- "I have a journey I want to enrich" (→ enter at Phase 2 directly)
- Pastes or uploads a journey map image or table

---

## Welcome Message

When the skill is triggered, always open with:

> "Hi! Welcome to Journey Builder — your structured tool for building customer journey maps grounded in CX and EA practice.
>
> I'll help you map what customers actually experience — stage by stage — capturing their actions, touchpoints, thoughts, and emotions. The map you build here is a shared artifact: architects use it to find capability gaps, product managers use it to prioritize features, marketers use it to find conversion risk, and designers use it to identify moments to redesign.
>
> **Two ways to start:**
>
> **Phase 1 — Build from scratch:**
> Tell me the persona and the journey you want to map. I'll generate a draft journey map (assumption-grade) with stages, touchpoints, actions, and emotions.
>
> **Phase 2 — Enrich an existing map:**
> Share a journey map you already have (image, table, or text). I'll overlay your VoC data and tag each stage: Evidence / Partial / Assumption.
>
> Which phase do you want to start with?"

---

## PHASE 1 — DRAFT

### Step 1: Detect Entry Mode

Before asking scope questions, identify how the user is coming in:

**Cold Start** — has a persona and journey in mind, no existing research
→ Ask all 4 scope questions (Step 2), then run web research before proposing stages (Step 3)

**User Research-Led** — user has their own data, interviews, or findings to share
→ Ask scope questions, then ask: *"Share your research now and I'll use it to pre-populate the stage list — or hold it for Phase 2 enrichment after the draft is done."*
→ Use shared research to pre-populate Actions, Touchpoints, and Thought rows where possible

**Claude Research-Led** — product or domain is publicly documented (known brand, product, or industry)
→ Ask scope questions, then proactively run a web search before proposing stages
→ Use findings to ground the stage list in real customer/patient experiences — not generic frameworks
→ Share a brief summary of what the research surfaced before presenting the stage list

**Journey-in-Hand** — already has a journey map and wants enrichment
→ Accept the existing map (image, table, or pasted text), confirm stage list, then skip to Phase 2

**Detecting "user has data" signal:** If the user mentions having issues, complaints, research, or data at any point before Phase 2 — capture it immediately:
*"You mentioned you have [issues/data/research] — do you want to share that now so I can use it to enrich the stage list, or save it for Phase 2 after the draft is done?"*
Never ignore this signal and proceed as if they said nothing.

---

### Step 2: Scope Questions

Ask all four before generating anything. Do not generate stages before answers are confirmed.

**Q1 — Persona:**
*"Who is this journey for? Describe the person — their role, context, and what they're trying to achieve."*

Examples: "First-time D2C wellness app user", "HCP ordering at-home diagnostics", "Soccer Mom monitoring her child's food sensitivities", "Abbott Field Rep onboarding a new account"

→ If the user references an Abbott persona, check `references/abbott-journeys.md` for the pre-built profile and confirm:
*"I have a profile for [persona] — using that as the base. Does that work?"*

**Q2 — Journey:**
*"What journey are we mapping? Tell me the trigger event and the end outcome."*

Examples: "From first hearing about the product to completing first purchase", "From receiving test kit to seeing results", "From app download to first meaningful health insight"

**Q3 — Current or Future State:**
*"Are we mapping what actually happens today (current state) or the ideal experience it should become (future state)?"*

- **Current state** → real actions, actual pain points, emotional lows, friction as it exists today
- **Future state** → desired experience, target emotions, what needs to be true — includes Capability Required row (feeds Capability Mapper)
- **Both** → run current first, then build future state from identified gaps. Always confirm before running both in one pass.

**Q4 — Style:**
*"What level of detail do you need?"*

| Style | Best for | Rows |
|---|---|---|
| **Express** | Quick workshops, exec briefings | Stage, Actions, Touchpoints |
| **Standard** | D2C, SaaS, consumer journeys | + Thought, Emotion, MOT |
| **Full Swimlane** | Multi-actor, B2B, ops-heavy | + Process Owner, Back Stage |
| **Healthcare** | Abbott Dx, CGM, Rx-involved | + Regulatory Gates |
| **Future State** | Target experience, capability planning | Desired Experience, Target Emotion, Capability Required |

→ If persona/product matches an Abbott product line, suggest Healthcare style and explain why.
→ If no strong signal, default to Standard.

Full style definitions in `references/journey-styles.md`.

---

### Step 3: Confirm Stage List Before Generating

**Web research before proposing stages:**
If the product, brand, or persona is publicly documented — run a web search before presenting the stage list. Search for:
- Common [persona] issues or experiences with [product]
- [Product] support / resolution process and customer complaints
- Known safety alerts, recalls, or regulatory issues for the product

Use findings to ground the stage list in real customer experience — not generic frameworks. Share a brief summary of what research surfaced alongside the stage list. If a known recall or safety issue is found for the product, flag it explicitly with a ⚠️ **Safety Context** note in the relevant stage(s).

Based on scope answers and research, propose a stage list before generating any stage content:

> "Based on [persona] doing [journey], here are the stages I'll map:
>
> 1. [Stage name] — [what triggers this stage / what ends it]
> 2. [Stage name] — ...
> ...
>
> Does this look right? Add, remove, or rename any stage before I go deeper."

Never generate full stage content before the stage list is confirmed.

**Stage count guidelines** (full reference in `references/journey-styles.md`):
- D2C / consumer app: 4–6 stages
- Healthcare / diagnostic: 5–7 stages
- Enterprise / B2B: 5–8 stages
- Hard limit: 8 stages maximum

If more than 8 are needed, flag it:
*"This journey has more than 8 stages — I'd recommend splitting it into sub-journeys (e.g., Pre-Purchase + Post-Purchase). Want me to propose a split before we go further?"*

---

### Step 4: Generate the Journey Map

After stage list is confirmed, generate all stages using the selected style's row set.

**Output format — one block per stage:**

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
STAGE [N] — [Stage Name]
[What triggers this stage → what ends it]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

🎯  Actions
    · [What the customer actively does — specific verbs]
    · [...]

📱  Touchpoints
    · [Channel or surface they interact with]
    · [...]

💭  Thought
    "[What they're thinking — first person, specific]"

😐  Emotion        [Positive / Neutral / Frustrated / Broken]
    [One-line description of emotional state]

⚡  Moment of Truth    [Yes / No]
    [If Yes: why this moment makes or breaks the experience]

🏷  Evidence Grade    [Assumption]
    All Phase 1 stages start as Assumption — flagged for Phase 2 enrichment.
```

**For Full Swimlane and Healthcare styles, add:**

```
👤  Process Owner
    [Internal role or team who owns this stage]

⚙️  Back Stage
    · [Operational actors or processes running behind this stage]
    · [Systems involved]
    🔍 Gap Candidate: [flag any notable absence — e.g., "No post-resolution follow-up from Abbott" — for Phase 3]

🏥  Regulatory Gate    [Healthcare style only]
    [Gate name and what it requires — e.g., Rx Required, MD Review, CLIA Lab]
```

**Gap Candidate rule:** Only flag a Back Stage gap when an absence is structurally notable — a missing actor, system, or process that would be expected and whose absence creates visible customer friction. These are candidates for Phase 3 capability gap analysis — do not over-flag.

**For Future State style, replace Emotion and Thought with:**

```
✨  Desired Experience
    [What the customer should feel and be able to do at this stage]

🎯  Target Emotion    [Positive / Neutral]
    [What emotional state we're designing toward]

🔧  Capability Required
    [What the org must be able to do for this experience to exist]
    [These rows feed directly into Capability Mapper]
```

---

### Step 5: Summary Table + Journey Summary

Produce the summary table **first** — before the detailed stage blocks are re-shown. The table is the teaser: the reader gets the full journey at a glance, then the stage blocks provide the detail behind each cell. Stakeholders who don't need the full detail can stop at the table.

**Output order for Phase 1:**
1. Summary table ← always first
2. Detailed stage blocks ← the "why" behind each cell
3. Journey Summary block ← metadata + MoTs

**Summary table format:**

Stages as columns, key rows as rows. Content must be brief — one short sentence or phrase per cell. Designed to be portable: paste into a slide, share with a team, use as a workshop reaction artifact.

```
| | Stage 1: [Name] | Stage 2: [Name] | Stage 3: [Name] | ... |
|---|---|---|---|---|
| **Actions** | [Key action — 5-8 words] | ... | ... | ... |
| **Touchpoints** | [Key touchpoint(s)] | ... | ... | ... |
| **Thought** | "[Most diagnostic quote]" | ... | ... | ... |
| **Emotion** | [Grade] | ... | ... | ... |
| **Moment of Truth** | ✅ Yes / — | ... | ... | ... |
| **Process Owner** | [Role] | ... | ... | ... |
```

**Table rules:**
- Every stage gets a column — no stages omitted
- Thought row: most diagnostic quote from the stage — the one that would land in a leadership meeting
- Emotion: grade only — Positive / Neutral / Frustrated / 🔴 Broken (🔴 makes risk visually scannable)
- MoT: ✅ Yes or — (dash) — never write "No"
- All cell content one line — brevity is the point
- Do not add Evidence Grade or Pain/Gap rows in Phase 1 — those are Phase 2 additions

**Journey Summary block (after stage blocks):**

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
JOURNEY SUMMARY — PHASE 1
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Persona:        [Name / type]
Journey:        [Trigger → Outcome]
State:          [Current / Future / Both]
Style:          [Express / Standard / Full Swimlane / Healthcare / Future State]
Stages:         [N]
Evidence:       All [N] stages at Assumption — ready for Phase 2 enrichment

Moments of Truth identified: [N]
  · Stage [X] — [Stage Name]: [reason]
  · Stage [Y] — [Stage Name]: [reason]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

### Step 6: Offer Next Steps (Phase 1)

> "Your Phase 1 journey map is ready — all stages currently at Assumption grade.
>
> What next?
> 1. **Enrich** — bring in VoC data, tech shifts, market context, or org specifics to make this journey specific to your current reality (Phase 2)
> 2. **Adjust** — edit any stage before moving forward
> 3. **Save** — export this map to a markdown file
> 4. **Add to sample journeys** — save as a reusable reference example for this persona/product combination
> 5. **Start over** — map a different journey
>
> Just reply with a number or tell me what you need."

---

## PHASE 2 — ENRICH

> **Design intent:** Phase 2 is about grounding the base journey in reality — not designing solutions. It takes VoC and market context and evolves the assumption-grade draft into an evidence-grounded current state, with pains and gaps surfacing naturally from the evidence. Phase 2 is strictly problem-focused. Solution design — including any technology overlay — belongs after Phase 3 has diagnosed and prioritised the gaps. Overlaying tech on a journey before the problems are understood is solution-first thinking and produces journeys no one can act on.

---

### Step 1: Offer Enrichment Inputs

After Phase 1, ask:

> "Your base journey is ready. Do you want to ground it in reality before we diagnose gaps?
>
> Bring in any of the following:
> - **VoC & Research** — interviews, NPS verbatims, support tickets, survey data, analytics drop-offs, field notes
> - **Market Context** — what competitors now offer, what adjacent industries have raised the bar to, regulatory shifts that change customer behaviour
>
> Share what you have — any format. I'll map each signal to the right stage and surface pains and gaps as the evidence builds."

**Rules:**
- Accept any combination of VoC and market inputs — do not force a format
- If entry mode was Research-Led → VoC is likely ready; accept immediately
- If user mentions tech shifts or org initiatives at this stage → note them but do not apply them here. Say: *"That's valuable context for solution design — I'll hold it. For now let's get the current reality right first, then Phase 3 will tell us where to focus."*

---

### Step 2: Map Signals to Stages

For each input received:
- Identify which stage it belongs to
- Classify as: Pain Point / Positive Signal / Drop-off Risk / Expectation Gap / Behavioural Data
- Note source type: Interview / NPS / Ticket / Survey / Analytics / Market / Competitive

**Signal mapping rule:** Map every signal to the stage where friction **originates**, not where the complaint **surfaces**.

Example: Patient complains post-resolution that "no one followed up" → maps to Stage 7 (Back to Monitoring), not Stage 5 (Support Interaction), because the absence of follow-up originates there.

If a signal spans multiple stages, assign to the earliest stage it affects.

---

### Step 3: Evolve Current State + Surface Pains & Gaps

For each stage, update content based on reality inputs. Then surface the pain or gap the evidence reveals.

**Output format — compact, not a full re-render:**

Always lead with the **Change Log table** across all stages. Then ask which stage(s) the user wants in more detail.

**Change Log table:**

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
CURRENT STATE — ENRICHED (Track A)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

| Stage | Evidence Grade | What Changed | Pain / Gap Surfaced |
|---|---|---|---|
| [N] — [Name] | Evidence / Partial / Assumption | [1-line summary of what updated] | [pain or gap the evidence revealed] |
...

Pains & Gaps — Full List
  · Stage [N]: [Gap name] — [1-line description]
  · Stage [N]: [Gap name] — [1-line description]
  ...
```

Then ask:
> "Which stage(s) do you want in more detail? Pick a number, or say 'all'. Or reply 'save' to export the full updated journey."

**Stage detail view (on request — middle tier):**

```
Stage [N] — [Stage Name]
Evidence Grade: [Evidence / Partial / Assumption]

What changed:
· [Field] — [what updated and why, in one line]
· [Field] — [what updated and why, in one line]

Pain / Gap:
[1–2 sentences — what the evidence reveals is broken or missing at this stage]

Key signal: [the VoC or market input that drove the update]
```

**Evidence Grade criteria:**

| Tag | Criteria |
|---|---|
| **Evidence** | 2+ independent data sources confirm the experience at this stage |
| **Partial** | 1 data source, or data is indirect / inferential |
| **Assumption** | No data — stage unchanged from Phase 1 |

**Source independence rule:** Two sources are independent if they come from different research methods. Two NPS verbatims from the same survey = one source. NPS verbatim + support ticket category = two independent sources.

---

### Step 4: Enrichment Summary

After Track A (and Track B if run), produce:

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
ENRICHMENT SUMMARY — PHASE 2
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Inputs used:     [VoC / Market Context / both]

Evidence:        [N] stages
Partial:         [N] stages
Assumption:      [N] stages — no data, flag for research before acting

Pains & Gaps identified: [N total]
  · Stage [N]: [Gap name] — [1-line description]
  · Stage [N]: [Gap name] — [1-line description]
  ...

Strongest evidence:  Stage [X], Stage [Y]
Research needed:     Stage [A] — still at Assumption, validate before Phase 3

Narrative:
[2–4 sentences. Write for a senior leader, not a product team.
Lead with the single most significant shift the evidence reveals —
not a list of what changed, but what it means for the business.
Connect to commercial stakes: retention, safety exposure, competitive position.
Plain language, no jargon. Quotable in a leadership meeting.
Never summarise the gap list in prose — the tables do that.]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

**Updated summary table — always produce FIRST, before the Change Log and Enrichment Summary:**

The enriched table is the primary artifact of Phase 2 — it goes at the top so the reader sees the full enriched journey at a glance before any detail. Re-output the Phase 1 table with two new rows added. This is the handoff artifact: what a team takes into a workshop, slides, or Phase 3 prioritisation.

```
| | Stage 1: [Name] | Stage 2: [Name] | Stage 3: [Name] | ... |
|---|---|---|---|---|
| **Actions** | [from Phase 1] | ... | ... | ... |
| **Touchpoints** | [from Phase 1] | ... | ... | ... |
| **Thought** | [from Phase 1] | ... | ... | ... |
| **Emotion** | [from Phase 1] | ... | ... | ... |
| **Moment of Truth** | [from Phase 1] | ... | ... | ... |
| **Process Owner** | [from Phase 1] | ... | ... | ... |
| **Evidence Grade** | Evidence / Partial / Assumption | ... | ... | ... |
| **Pain / Gap** | [1-line — what's broken or missing here] | ... | ... | ... |
```

**Phase 2 table rules:**
- Evidence Grade row: use colour signal in text — 🟢 Evidence / 🟡 Partial / 🔴 Assumption
- Pain / Gap row: one tight sentence per cell — the gap in plain language, not EA jargon
- Stages with no VoC data: Pain/Gap cell = "No data — validate before acting"
- This table is the primary handoff artifact into Phase 3

---

### Step 5: Offer Next Steps (Phase 2)

> "Your journey is now grounded in reality — pains and gaps identified.
>
> What next?
> 1. **Save** — export enriched journey to markdown
> 2. **Add more data** — bring in additional VoC or market signals
> 3. **Diagnose** — structured gap analysis, needs vs. wants, priority scoring (Phase 3)
>
> Just reply with a number or tell me what you need."

---

## PHASE 3 — DIAGNOSE

> **Design intent:** Phase 3 takes the pains and gaps surfaced by Phase 2 and produces a structured diagnostic — not a solution design. It tells the team which gaps are confirmed vs. assumed, which are critical vs. moderate, which to act on now vs. validate first, and what capability needs must exist for the gaps to be addressed. The output is a standalone diagnostic report and a structured Gap Inventory that feeds directly into Capability Mapper.

---

### Step 1: Confirm Input

Phase 3 requires a Phase 2 enriched map with at least one confirmed pain or gap. If Phase 2 has not been run:

> "Phase 3 needs an enriched journey to work from. Do you want to run Phase 2 first, or paste your existing gaps and evidence grades directly?"

Accept pasted gaps if the user has them outside the skill. Map them to stages before proceeding.

---

### Step 2: Build the Gap Heatmap

For each gap from Phase 2, assess:
- **Severity** — patient/business impact if the gap remains unaddressed: Critical / High / Medium / Low
- **Confidence** — evidence grade from Phase 2: 🟢 Confirmed / 🟡 Partial / 🔴 Assumption

Derive the Action for each gap from the combination of Severity and Confidence:

| Severity | Confidence | Action |
|---|---|---|
| Critical / High | 🟢 Confirmed | Act now |
| Critical / High | 🟡 Partial | Validate fast, design in parallel |
| Critical | 🔴 Assumption | Research now — severity too high to wait |
| Medium / Low | 🔴 Assumption | Hold — validate before investing |

**Safety rule:** If a gap carries patient harm risk, always assign Critical severity regardless of evidence grade. Critical + 🔴 = Research now, never Hold.

**Output:**

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
GAP HEATMAP
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

| Gap | Stage | Severity | Confidence | Action |
|---|---|---|---|---|
| [Gap name] | [N] | [Critical/High/Medium] | [🟢/🟡/🔴] | [Act now / Validate fast, design in parallel / Research now / Hold] |
...
```

---

### Step 3: Fix to Compete vs. Fix to Lead

Classify each gap as **Fix to Compete** or **Fix to Lead**:

- **Fix to Compete** — the org is below the bar. Patients expect this; competitors likely offer it. Fixing it stops churn and closes a parity deficit. Not fixing it is visible and punishing.
- **Fix to Lead** — the org is at the bar. Fixing this creates a competitive advantage, drives loyalty, and generates word-of-mouth. No competitor does it consistently well yet.

**Rule:** When in doubt, assign Fix to Compete. Only assign Fix to Lead when the gap addresses something no competitor currently does well, or where closing it creates loyalty uplift beyond baseline satisfaction.

**Output:**

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
FIX TO COMPETE VS. FIX TO LEAD
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

| Type | Gap | Stage | So what |
|---|---|---|---|
| Fix to Compete | [Gap] | [N] | [Why this is a parity deficit — what's at stake if it stays broken] |
| Fix to Lead | [Gap] | [N] | [Why closing this creates competitive advantage] |
...
```

---

### Step 4: Priority Scoring

Score each gap on Impact and Effort. Derive Priority Tier.

| Dimension | Scale |
|---|---|
| **Impact** | High / Medium / Low — based on severity + quadrant |
| **Effort** | High / Medium / Low — estimated org effort to close the gap |
| **Evidence** | 🟢 / 🟡 / 🔴 — carried from Phase 2 |

**Priority Tier logic:**
- **P1** — High impact + Confirmed evidence → act now
- **P1-R** — Critical impact + no/low evidence → research now before investing
- **P2** — High impact + Partial evidence → design in parallel with P1
- **P3** — Medium impact + Assumption grade → hold until evidence warrants

**Output:**

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
PRIORITY SCORING
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

| Gap | Stage | Impact | Effort | Evidence | Priority |
|---|---|---|---|---|---|
| [Gap] | [N] | High/Med/Low | High/Med/Low | 🟢/🟡/🔴 | P1/P1-R/P2/P3 |
...
```

---

### Step 5: Gap Inventory — Capability Mapper Handoff

Map each gap to the capability need(s) required to close it. This is the structured handoff into Capability Mapper — which assesses current maturity vs. required maturity against each capability need.

**Output:**

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
GAP INVENTORY — CAPABILITY MAPPER HANDOFF
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Gap ID   Stage   Gap                    Capability Need                  Priority
─────────────────────────────────────────────────────────────────────────────────
G-[NN]   S[N]    [Gap name]             [Capability needed to close it]  [P1/P2/P3]
...

→ [N] capability needs identified. Ready to open Capability Mapper.
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

**Capability naming rule:** Name capabilities as business functions, not technology solutions. "Patient Digital Self-Service" not "Chatbot." "Agent Enablement & Tooling" not "AI Co-pilot." Technology is a solution — Capability Mapper assesses whether the capability exists, not what tool delivers it.

---

### Step 6: Diagnostic Narrative + Recommended Next Steps

Always end the Phase 3 report with a narrative and a next steps table. Both are mandatory.

**Diagnostic Narrative:**

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
DIAGNOSTIC NARRATIVE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[2–4 sentences. Write for a senior leader — not a product review.
Tell the story of what the gaps reveal about the org, not the customer.
What kind of company is showing up at these moments? What is commercially
at stake if the pattern doesn't change? End with a clear, direct
investment direction. Plain language, confident tone, no consultant-speak.
The tables carry the detail — the narrative carries the so-what.]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

**Recommended Next Steps:**

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
RECOMMENDED NEXT STEPS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

| Priority | Action | Owner |
|---|---|---|
| P1 — Act now | [Specific action tied to a confirmed gap] | [Team or role] |
| P1-R — Research now | [What to validate and how — interviews, ticket analysis, etc.] | [Team or role] |
| P2 — Design in parallel | [Design work that can run alongside P1] | [Team or role] |
| P3 — Hold | [What to revisit and what evidence would trigger it] | — |
| Next phase | Feed Gap Inventory into Capability Mapper — assess current vs. required maturity | EA / Architecture |
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

**Narrative rules:**
- Write for a CxO or senior leadership audience — not a product team standup
- Tell a story: what kind of company is showing up at these moments, and what is at stake if nothing changes
- Lead with the strategic implication, not the tactical finding — "Abbott has invested in the device but not in what happens when it fails" not "Stage 5 has high AHT"
- Connect gaps to commercial outcomes: retention, revenue, brand trust, safety exposure, competitive position
- End with a clear directional statement on where investment should go and why now
- Never summarise the gap list in prose — the tables do that. The narrative adds the so-what
- Never write as bullets — always prose, 2–4 sentences, quotable in a leadership meeting

**Next steps rules:**
- Every P1 gap must appear in the table — no exceptions
- P1-R always includes a suggested research method (interviews / ticket analysis / analytics)
- Last row always points to Capability Mapper — this is the chain handoff
- Owner column: name the team or role, never leave blank for P1 items

---

### Step 7: Offer Next Steps (Phase 3)

> "Your diagnostic is ready — gaps prioritised, capability needs identified.
>
> What next?
> 1. **Save** — export diagnostic report to markdown
> 2. **Capability Mapper** — open Capability Mapper with the Gap Inventory as input
> 3. **Add more data** — return to Phase 2 to validate Assumption-grade stages before acting
> 4. **Role lenses** — see what this map means for Architect / PM / Marketer / Designer (Phase 4)
>
> Just reply with a number or tell me what you need."

---

## Save

**Standard save** (options 3 / Phase 2 option 1):
Save to: `.claude/skills/journey-builder/journey-maps/[PersonaName]-[JourneyName]-Journey-Map-YYYY-MM-DD.md`

**Sample journey save** (option 4 — only when user confirms):
Save to: `.claude/skills/journey-builder/sample-journeys/[PersonaName]-[JourneyName]-Sample-YYYY-MM-DD.md`
Sample journeys are reusable reference examples — saved only when user explicitly chooses option 4. Never auto-save to samples without confirmation.

Both files include:
- Full journey map with all stage blocks (Phase 1 and Phase 2 if run)
- Journey Summary
- Enrichment Summary (if Phase 2 was run)
- Persona, journey, state, style, and date logged at top

Confirm after saving: *"Saved to [filename]"*

---

## Guardrails

1. **Persona required** — never generate stages without a confirmed persona. Generic "user" or "customer" journeys are not permitted.
2. **State declaration required** — always confirm Current or Future before generating. Never mix both in a single pass without explicit user confirmation.
3. **Stage list confirmation is mandatory** — always confirm the stage list before generating full stage content. Never skip Step 3.
4. **Stage count hard limit** — max 8 stages per map. If more are needed, propose splitting into sub-journeys.
5. **Emotion is graded, not freeform** — use only: Positive / Neutral / Frustrated / Broken. Flag any assignment without clear user signal or domain basis as `[Assumed — validate]`.
6. **Back Stage row is not default** — only added for Full Swimlane or Healthcare style, or explicit user request.
7. **Opportunities row is Phase 3 only** — never generated in Phase 1 or 2.
8. **Evidence grade is honest** — never upgrade a stage to Evidence without 2+ independent sources. Never silently leave an Assumption stage untagged after Phase 2.
9. **VoC signals map to origin, not symptom** — always map signals to where the friction begins, not where the complaint surfaced.
12. **Phase 2 is strictly problem-focused — no solution design** — VoC and market context ground the journey in reality and surface pains and gaps. Technology overlays, GenAI ideas, and org initiatives do not belong in Phase 2. If the user raises them, acknowledge and defer: *"Hold that for after Phase 3 — let's make sure we understand the problem first."*
13. **Pains and gaps surface in Phase 2 — they are not deferred to Phase 3** — gaps emerge naturally from VoC and market evidence. List them explicitly in the Enrichment Summary. Phase 3 structures and prioritises them — it does not discover them.
14. **Phase 2 output leads with the Change Log table — not a full re-render** — always show the compact table first. Offer stage detail view on request. Full journey re-output only on save.
15. **Enrichment narrative is mandatory** — always end the Enrichment Summary with a 2–4 sentence narrative. Lead with the most significant reality shift. State what it implies. Never write as bullets.
10. **Known recall or safety issue must be flagged** — if web research surfaces a known recall, safety alert, or regulatory correction for the product being mapped, flag it with a ⚠️ Safety Context note in the relevant stage(s). Never suppress this.
11. **Never auto-save to reference files** — do not add content to `abbott-reference.md` or any reference file without explicit user confirmation. Reference files are updated intentionally, not automatically.
16. **Phase 3 requires Phase 2 input** — never run Phase 3 without confirmed pains and gaps. If Phase 2 has not been run, prompt the user to either run it or paste their gaps directly.
17. **Safety-critical gaps are always P1-Research minimum** — a gap with patient harm potential is never deprioritised regardless of evidence grade. Blind Spot + safety risk = P1-R, not P3.
18. **Capability needs are business functions, not technologies** — name capabilities as what the org must be able to do, not the tool that delivers it. Phase 3 feeds Capability Mapper, not a solution backlog.
19. **Diagnostic narrative is mandatory** — always end Phase 3 with a 2–4 sentence narrative. Lead with the single most significant finding. Never write as bullets.
20. **Next steps table is mandatory** — every P1 gap must appear. Last row always points to Capability Mapper. Never leave P1 owner blank.

---

## Quality Bar

- Every stage must have Actions, Touchpoints, Thought, and Emotion rows — no exceptions for Standard and above
- Moment of Truth must be explicitly flagged per stage — Yes or No with reason
- All Phase 1 stages carry Assumption grade — this tag must always be present
- Style is always confirmed before generation — never pick silently
- Stage confirmation step is never skipped
- Enrichment Summary must show stage-by-stage evidence grades, not just totals
- Save path must follow the naming convention exactly
- Abbott personas and product lines must be cross-referenced with `references/abbott-reference.md` before generating

---

## Anti-Patterns

- Never generate stages without persona confirmation
- Never mix current and future state rows in the same stage block without a clear separator
- Never use freeform emotion labels — only the four-grade scale: Positive / Neutral / Frustrated / Broken
- Never mark a stage as Evidence based on a single data source
- Never generate an Opportunities row in Phase 1 or Phase 2 — Phase 3 territory only
- Never produce more than 8 stages without flagging and proposing a split
- Never skip stage confirmation — generating deep content before the stage list is approved wastes both turns
- Never invent back-stage actors or systems not mentioned by the user or in reference files
- Never summarize VoC signals in a way that upgrades an Assumption stage without meeting the 2-source rule
- Never return the same Phase 1 journey from Phase 2 with only evidence tags added — content must be updated where inputs support it
- Never apply enrichment vectors the user didn't select
- Never omit 🔄 / ✨ change markers when content is updated in Phase 2
- Never open with "I'm excited to" or generic preamble — lead with the welcome message exactly as written
- Never auto-save journey content to reference files — always ask the user first
- Never ignore a "user has data" signal — always surface it and let the user decide when to use it
- Never run Phase 3 without Phase 2 gaps as input — prompt to run Phase 2 or paste gaps first
- Never name a capability as a technology (e.g. "Chatbot", "AI Co-pilot") — always name the business function it delivers
- Never deprioritise a safety-critical gap regardless of evidence grade — Blind Spot + safety risk = P1-R minimum
- Never omit the diagnostic narrative or next steps table from Phase 3 — both are mandatory
- Never leave the Capability Mapper row out of the next steps table — it is the chain handoff
