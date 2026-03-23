---
name: journey-builder
description: Build structured customer journey maps grounded in CX and EA practice. Phase 1 drafts the journey from persona and scope. Phase 2 enriches with VoC and data, tagging each stage as Evidence, Partial, or Assumption. One map consumed by all — architects, product managers, marketers, and designers.
---

# Journey Builder

**Author:** Nitesh Luthra
**Version:** 1.1

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

### Step 5: Journey Summary

After all stages, produce a summary block:

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
> 1. **Enrich** — bring in VoC data, NPS, research, or tickets to evidence-grade each stage (Phase 2)
> 2. **Adjust** — edit any stage before moving forward
> 3. **Save** — export this map to a markdown file
> 4. **Add to sample journeys** — save as a reusable reference example for this persona/product combination
> 5. **Start over** — map a different journey
>
> Just reply with a number or tell me what you need."

---

## PHASE 2 — ENRICH

### Step 1: Accept VoC / Data Input

If not already provided, ask:

> "Share the data you want to overlay on this journey. I'll accept any format:
> - Raw verbatims or quotes from user interviews
> - NPS themes or open-text responses
> - Support ticket categories or top issues
> - Survey results — quantitative or qualitative
> - Session analytics signals (drop-off points, time-on-task, error rates, funnel conversion)
> - Stakeholder observations or field research notes
>
> Paste whatever you have — I'll structure it and map it to the right stages."

If entry mode was Research-Led (flagged in Phase 1) → user likely has data ready. Accept immediately without re-asking.

---

### Step 2: Map Signals to Stages

For each VoC signal or data point:
- Identify which stage it belongs to
- Classify as: Pain Point / Positive Signal / Drop-off Risk / Behavioral Data
- Note source type: Interview / NPS / Ticket / Survey / Analytics

**Signal mapping rule:** Map to the stage where the friction **originates**, not where the complaint **surfaces**.

Example: User reports "I didn't know where my sample was" in a post-results NPS survey → maps to the Shipping/Lab stage, not the Results stage, because that's where the information gap begins.

If a signal clearly spans multiple stages, assign to the earliest stage it affects.

---

### Step 3: Update Evidence Tags

For each stage, update the Evidence Grade based on data provided:

| Tag | Criteria |
|---|---|
| **Evidence** | 2+ independent data sources confirm the experience at this stage |
| **Partial** | 1 data source, or data is indirect / inferential |
| **Assumption** | No data — based on domain knowledge or best practice only |

**Source independence rule:** Two sources are independent if they come from different research methods. Two NPS verbatims from the same survey = one source. NPS verbatim + support ticket category = two independent sources.

Flag Assumption stages explicitly after enrichment:
*"Stage [N] — [Name] remains at Assumption. No data was provided for this stage. Flag for research before acting on gaps here."*

---

### Step 4: Output Evidence-Layered Map

Re-output each stage with evidence annotations added below the existing rows:

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
STAGE [N] — [Stage Name]
🏷  Evidence Grade: [Evidence / Partial / Assumption]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

[All Phase 1 rows retained as-is]

📊  Data Signals
    · [Signal] — Source: [Interview / NPS / Ticket / Survey / Analytics]
    · [Signal] — Source: [...]

⚠️  Assumption Flag    [only if grade = Assumption]
    No data backing this stage. Validate before drawing conclusions or prioritizing changes here.
```

---

### Step 5: Enrichment Summary

After all stages, produce an updated summary:

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
ENRICHMENT SUMMARY — PHASE 2
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Evidence:       [N] stages
Partial:        [N] stages
Assumption:     [N] stages — flagged for validation

Strongest evidence:   Stage [X] — [Name], Stage [Y] — [Name]
Weakest coverage:     Stage [A] — [Name], Stage [B] — [Name] → prioritize research here

Data sources used: [list]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

### Step 6: Offer Next Steps (Phase 2)

> "Your journey map is now evidence-layered.
>
> What next?
> 1. **Save** — export enriched map to markdown
> 2. **Adjust** — add more data or correct any stage
> 3. **Next phase** — gap and opportunity analysis (Phase 3 — coming soon)
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
10. **Known recall or safety issue must be flagged** — if web research surfaces a known recall, safety alert, or regulatory correction for the product being mapped, flag it with a ⚠️ Safety Context note in the relevant stage(s). Never suppress this.
11. **Never auto-save to reference files** — do not add content to `abbott-reference.md` or any reference file without explicit user confirmation. Reference files are updated intentionally, not automatically.

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
- Never open with "I'm excited to" or generic preamble — lead with the welcome message exactly as written
- Never auto-save journey content to reference files — always ask the user first
- Never ignore a "user has data" signal — always surface it and let the user decide when to use it
