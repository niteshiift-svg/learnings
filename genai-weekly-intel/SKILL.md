---
name: genai-weekly-intel
description: Produce a weekly GenAI intelligence brief focused on hyperscalers and key players (OpenAI, Anthropic/Claude, xAI/Grok, Microsoft, Google, AWS, Salesforce, Adobe, and other major app players). Use when a user asks for GenAI news/trend analysis, company update tracking, concise fact-based summaries, or a single-player update with weekly document output.
---

# GenAI Weekly Intel

**Author:** Nitesh Luthra
**Version:** 1.1

## Trigger
Activate when the user asks for:
- "GenAI weekly brief", "weekly GenAI update", "GenAI news this week"
- "what happened in AI this week", "AI trends this week"
- "update on [company]", "what's new with OpenAI / Anthropic / Google / AWS"
- "single-player update for [company]"

## Modes

### Mode 1: Full Weekly (Default)
Cover all hyperscalers and key players in the tracking universe. Time window: previous 7 days unless user specifies dates.

Players covered (in order):
1. OpenAI
2. Anthropic / Claude
3. Google / DeepMind
4. Microsoft / Copilot
5. AWS / Amazon
6. xAI / Grok
7. Meta AI
8. Salesforce / Einstein
9. Adobe / Firefly
10. Notable others (if significant news)

### Mode 2: Single-Player
Use when the user names one company only. Lock scope to that player. Produce Player Snapshot output.

### Mode 3: LinkedIn Post (Optional Add-On)
When user asks for a LinkedIn post alongside the brief or on its own:
- Always placed at the end of the brief output — after Sources
- Pick the single most compelling signal or tension from the week — not a product announcement recap
- Structure: sharp 1-line opener (observation or tension, not a question) → 4-6 tight inference bullets → 1-2 sentence close (synthesis, nuance, or trade-off)
- Each bullet is a standalone inference or signal — not a summary of what happened. Use em-dashes and colons to pack meaning. Start bullets with the insight, not the company name.
- Closing line: acknowledge complexity or a real trade-off — never a call to action or hype ending
- Max 3-4 hashtags — relevant, not performative. Place at the very end.
- 150-200 words total
- Voice: practitioner insider, not tech journalist. Inference-first. No superlatives ("game-changing", "exciting", "incredible"). No vendor cheerleading. Comfortable sitting with nuance.
- Never prescribe actions to the reader — surface the signal, let them draw the conclusion
- Label it clearly: `--- LinkedIn Post ---`

Example post style (reference only — do not reuse):
```
AI vendor alignment is quietly becoming a governance question — not just a capability one.

A few inferences from this week in GenAI:
- Vendor posture is diverging: Anthropic drew a public line on autonomous weapons use; xAI walked directly into the Pentagon. Enterprises now have visible camps to choose from.
- Computer use crossed human baseline — GPT-5.4 at 75% OSWorld signals agentic automation is moving from research to enterprise-ready faster than most roadmaps assumed.
- Platform vs. model: AWS committed $50B to OpenAI while building the infrastructure to run all models — the bet is on inference volume, not model ownership.
- Healthcare AI is consolidating fast — Microsoft and Google both presented clinical AI platforms at HIMSS26; five major health systems signed with Google Cloud this week alone.

The tricky part for enterprises isn't picking the best model anymore — it's knowing which vendors' values and risk posture align with your own.

#GenAI #EnterpriseAI #HealthcareAI #AIStrategy
```

### Mode 4: Deck Slide Format (Optional Add-On)
When user asks for a deck or slide-ready version:
- Produce one slide per major player (title + 3 bullets max)
- Each bullet: one fact or one strategic inference — never both mixed
- Add a "Week's Top 3 Moves" summary slide at the start
- Add a "Watch Next Week" slide at the end
- Label each slide clearly: `--- Slide: [Title] ---`
- Keep bullets under 12 words each — deck-ready, not paragraph prose

## Output Style (Required)

Two-layer format for every player:

**Layer 1 — Strategic positioning** (1 sentence, interpretation):
> "AWS is establishing itself as the AI production platform for enterprises prioritizing control, governance, and integration."

**Layer 2 — Fact-based change lines** (specific, date-anchored, verifiable):
> "AWS launched Nova Forge and Trainium3 on March 4, 2026, introducing on-demand fine-tuning and custom silicon for enterprise workloads."

Keep Layer 1 strategic and concise. Keep Layer 2 factual, date-specific, and source-backed. Never mix interpretation into fact lines.

## Workflow

### Step 0: Load Previous Brief (Delta Mode)

Before generating any output, check for the most recent saved brief in `nitesh-notes/genai-intel/`.

- Look for the latest `GenAI-Weekly-Brief-*.md` file (full mode) or `<Player>-Trends-*.md` (single-player mode)
- If found: load it and use it as the baseline for week-over-week comparison
- If not found: skip delta and generate the brief normally — note "No prior brief found — delta not available this week"

**Delta rules:**
- A player section is only written in full if something materially changed this week vs. last week
- If a player has no material change: write one line only — `**[Company]:** No material change from last week.` — do NOT repeat last week's content
- Strategic positioning only updates if the direction actually shifted — do not rewrite for style
- Benchmark scores only update rows where new scores were published this week — carry forward prior scores with a "—" marker, not blank cells
- Watchlist Next Week: cross-check against last week's watchlist — if a watchlist item resolved, note the outcome; if still pending, carry it forward with a status update

**Delta change markers** (use inline, consistently):
- `[NEW]` — first time this appears in the brief
- `[CHANGED]` — existed last week, materially different this week
- `[RESOLVED]` — was on watchlist last week, outcome now known
- `[PENDING]` — was on watchlist last week, still unresolved
- `[NO CHANGE]` — player or item unchanged; one-line only, no full section

### Step 1: Define Scope

**Always ask this first — before generating any output:**

Present the following numbered list and ask the user to pick:

```
Which players do you want to cover this week?

1. OpenAI
2. Anthropic / Claude
3. Google / Gemini
4. Microsoft / Copilot
5. AWS / Amazon
6. xAI / Grok
7. Meta AI
8. Others (Salesforce, Adobe, and notable emerging players)
9. All of the above

Reply with a number or numbers (e.g. "1, 3" or "9 for all").
```

- If the user already specified a player in their trigger message, skip this question and proceed directly
- If the user picks a single number: activate Mode 2 (Single-Player)
- If the user picks multiple numbers or "9": activate Mode 1 (Full Weekly) scoped to selected players
- Default time window: previous 7 days unless user specifies dates

### Step 2: Gather Source Material
- Primary sources first: official blogs, release notes, docs, company announcements
- High-quality secondary: Reuters, Financial Times, Bloomberg, TechCrunch, VentureBeat, The Information
- Do not limit to company websites only
- If source data is unavailable or uncertain, say so explicitly — never fabricate

### Step 3: Build Player Sections

For each player:

**[Company Name]**

*Strategic positioning:* 1 sentence on overall direction.

*What changed this week:*
- `<Company> announced/released <update> on <Month Day, Year> to <objective/outcome>, including <key detail>.`
- 2-3 bullets max. Date-specific. Source-backed.

*Adoption trend:*
- 2-3 metrics showing how usage is evolving (MAU/WAU, app downloads, enterprise customers, API volume, revenue signals)
- If unavailable: "Adoption data not disclosed this week."

*Overall inference:* 2-3 sentence paragraph interpreting direction and implications.

*Healthcare / Med-Tech relevance:* [High / Medium / None] — 1 sentence on why this matters for healthcare AI, clinical workflows, regulatory tech, or enterprise health systems. Write "None this week." if not applicable.

---

### Step 3b: Regulatory & Policy Tracker

Always include this section in full weekly mode. Include in single-player mode only if relevant to that player.

Cover:
- **FDA**: AI/ML in medical devices, SaMD guidance, 510(k)/PMA AI-related decisions
- **EU AI Act**: Enforcement milestones, high-risk AI classification updates, compliance deadlines
- **US AI Policy**: Executive orders, NIST AI framework updates, congressional AI legislation
- **Enterprise AI Governance**: Major industry frameworks, responsible AI standards, audit requirements
- **Data Privacy**: HIPAA intersections with AI, cross-border data rules affecting AI platforms

Format per item:
`[Regulatory body / jurisdiction] [did X] on [date], affecting [who / what scope].`

If no significant regulatory news this week: write "No material regulatory developments this week."

### Step 3c: Benchmark Tracker

Include in full weekly mode. Show a snapshot table of the latest publicly available benchmark scores for frontier models. Update only rows where new scores were released this week — mark unchanged rows as "—".

```
| Model                  | Coding (SWE-Bench) | Reasoning (GPQA Diamond) | Multimodal (MMMU) | Computer Use (OSWorld) | Updated |
|------------------------|--------------------|--------------------------|-------------------|------------------------|---------|
| GPT-5.4 (OpenAI)       |                    |                          |                   |                        |         |
| Claude Sonnet 4.6      | 79.6%              | Not disclosed            | Not disclosed     | 72.5%                  | Feb 17, 2026 |
| Gemini 3.1 Pro         | Not disclosed      | 94.3%                    | Not disclosed     | Not disclosed          | Feb 19, 2026 |
| Grok 3 (xAI)           | 58.6%*             | Not disclosed            | Not disclosed     | Not disclosed          | *Contested: self-reported 72–75% |
| Llama 4 Maverick (Meta)| ~62% (HumanEval)   | Not disclosed            | 73.4%             | Not disclosed          | Contested — see note |
```

Notes:
- GPT-4o is no longer OpenAI's frontier model — replaced by GPT-5.4 as of March 2026. Update scores when official benchmarks are published.
- Grok 3 coding score is contested: xAI self-reported 72–75% on SWE-Bench; independent testing (vals.ai) shows 58.6%. Use independent score until verified.
- Llama 4 Maverick benchmarks contested — Meta's claims against GPT-4o and Gemini could not be independently reproduced. Flag with caution.
- HumanEval is a different benchmark from SWE-Bench — not directly comparable; noted where used.

Rules:
- Only include scores from official model cards, company blogs, or peer-reviewed evals — no third-party speculation
- If a score is unavailable or unverified: write "Not disclosed"
- Add a 1-sentence interpretation below the table: what the scores collectively signal about capability shifts this week

### Step 3d: Legal, Privacy & OEC Implications

Always include in full mode. Include in single-player mode only if relevant to that player.

This section is written for Legal, Privacy, and Office of Ethics & Compliance (OEC) audiences — not for technologists. Surface signals that have direct bearing on enterprise risk, data handling obligations, vendor contracts, employee use policies, and regulatory exposure.

Cover the following lenses:

- **Data Privacy & HIPAA**: Any AI product updates that change how patient data, PII, or PHI is handled, stored, or processed. Flag vendor changes to data retention, training data use, opt-out policies, or cross-border data flows.
- **Employee AI Use Policy**: Any developments that affect acceptable use of AI tools by employees — new agentic capabilities, autonomous task execution, multi-model data sharing, or shadow AI risks.
- **Vendor Contract & IP Risk**: New AI features that touch IP ownership, output licensing, indemnification exposure, or terms-of-service changes that affect enterprise agreements.
- **Ethics & Responsible AI**: Model behavior changes, bias disclosures, safety refusals, autonomous weapons / surveillance stances, or public commitments that affect how vendors align with enterprise ethics frameworks.
- **Regulatory Exposure**: Developments that increase or decrease exposure under EU AI Act, FDA SaMD guidance, EEOC AI hiring rules, FTC AI regulations, or sector-specific compliance requirements.

Format per item:
`[Lens] — [What happened] on [date]. [Why it matters for Legal/Privacy/OEC in 1 sentence.]`

If no material implications this week: write "No material Legal, Privacy, or OEC developments this week."

**Tone:** Factual and risk-aware. Not alarmist. Surface the signal — let Legal/OEC draw the conclusion. Never speculate on legal liability. If uncertain, flag it as a "watch item" rather than a finding.

Example:
```
## Legal, Privacy & OEC Implications

**Data Privacy & HIPAA** — Microsoft Copilot Cowork launched on March 9, 2026 with multi-step autonomous task execution across Outlook, Teams, and Excel. Enterprises should verify whether Cowork's cross-app data access is covered under existing Microsoft BAA agreements and confirm PHI handling scope before enabling for clinical users.

**Employee AI Use Policy** — OpenAI GPT-5.4 now executes autonomous computer-use tasks (75% OSWorld) as of March 5, 2026. Agentic AI tools that can take actions on behalf of employees — file creation, form submission, browser automation — may require acceptable-use policy updates to define authorization boundaries.

**Ethics & Responsible AI** — Anthropic's public refusal to permit Claude for mass surveillance and autonomous weapons use (March 5–6, 2026) creates a visible vendor alignment signal. Enterprises with ethics board requirements or responsible AI policies may find Anthropic's posture increasingly documentable for governance purposes.

**Vendor Contract & IP Risk** — No material developments this week.

**Regulatory Exposure** — California AG issued formal demand to xAI on deepfake content generation (March 7, 2026). Enterprises using Grok should review their acceptable-use terms in light of ongoing state-level AI content enforcement.
```

### Step 4: Assemble Final Brief

**Full mode output structure** (in order):
1. CIO Narrative — 2-paragraph strategic framing (full mode only)
2. Delta Summary — 3-5 bullets, plain prose, no tags
3. Company Updates — full sections for changed players only; one-liner [NO CHANGE] for unchanged players
4. Regulatory & Policy Tracker — delta only; carry forward [PENDING] items with status
5. Benchmark Tracker — update changed rows only; carry forward unchanged scores with "—" in Updated column
6. Legal, Privacy & OEC Implications — always included in full mode; include in single-player mode if relevant
7. Watchlist Next Week — resolve last week's items first, then add new ones
8. Sources

**CIO Narrative format:**

Always included in full mode. Never in single-player mode. Two paragraphs. Plain language. No jargon. No vendor cheerleading. Written for a CIO who reads this in 90 seconds.

**Paragraph 1 — The week's strategic theme:**
What is the single most important thing that happened in GenAI this week? Frame it as a strategic shift, not a product announcement. What does it signal about where the market is going?

**Paragraph 2 — Enterprise signal reading:**
What does this week's pattern suggest for enterprise organizations? Surface the implication — do not prescribe action. Write in the third person ("organizations that...", "enterprises operating in...") or signal framing ("the pattern worth watching is...", "this suggests..."). Never write "you should", "you must", or "action is overdue". The reader is intelligent — give them the inference, let them draw the conclusion.

Tone: Observational, not prescriptive. Peer-level insight, not consulting advice. Confident but not directive. No hype words ("exciting", "revolutionary", "game-changing").

Example:
```
## CIO Narrative

The defining move this week was not a product launch — it was a values test. Anthropic's refusal to permit Claude for mass surveillance and autonomous weapons, resulting in a DoD supply-chain risk designation, drew the clearest public line any frontier AI lab has drawn between commercial and government use. The market immediately clarified: Microsoft, Google, and AWS all confirmed Claude remains available to every non-defense enterprise customer. The era of AI vendors being all things to all buyers is ending.

What this week's pattern suggests is that vendor alignment is quietly becoming a governance question, not just a capability one. Enterprises in regulated industries — healthcare, life sciences, finance — will find Anthropic's posture increasingly legible against their own risk frameworks. And GPT-5.4's computer-use score (75% OSWorld, above human baseline) is worth watching not as a benchmark number, but as a signal that agentic workflow automation is moving from research to enterprise-ready faster than most roadmaps assumed.
```

**Delta Summary format:**

The summary is a clean executive narrative — no [NEW] / [CHANGED] tags. Plain prose. 3-5 bullets max. Written for a leader who has 60 seconds.

```
## What Changed This Week (vs. March 9, 2026)

- OpenAI launched GPT-5.4, now leading all models on computer use at 75% OSWorld
- AWS committed $50B to OpenAI — the largest enterprise AI infrastructure deal of the year
- Anthropic's DoD standoff hardened its regulated-industry positioning; court challenge filed
- Microsoft Dragon Copilot expanded to a full clinical platform at HIMSS26
- xAI signed into Pentagon classified systems, directly contrasting Anthropic's refusal

Players with no material change this week: Meta AI, Salesforce, Adobe
```

**Delta markers belong at the player section level only:**

Each player header shows its status for the week:
- `**OpenAI** [CHANGED]` — full section follows
- `**Meta AI** [NO CHANGE]` — one line only, no section
- `**Anthropic** [CHANGED]` — full section follows

Inside each changed player section, individual updates are tagged:
- `[NEW]` — first time this item appears
- `[CHANGED]` — existed last week, materially different now
- `[RESOLVED]` — was on watchlist, outcome now known
- `[PENDING]` — was on watchlist, still unresolved

See [references/weekly-brief-template.md](references/weekly-brief-template.md)

**Single-player output structure:**
See [references/player-focus-template.md](references/player-focus-template.md)

**Company tracking universe:**
See [references/company-watchlist.md](references/company-watchlist.md)

**Trigger prompts for running the skill:**
See [references/run-prompt-template.md](references/run-prompt-template.md)

### Step 5: Save by Default
- Always save automatically after generating output — do not wait for the user to ask
- Full mode: `nitesh-notes/genai-intel/GenAI-Weekly-Brief-YYYY-MM-DD.md`
- Single-player: `nitesh-notes/genai-intel/<Player>-Trends-YYYY-MM-DD.md`
- If a file for that date already exists, append to it — do not overwrite
- Confirm after saving: "Saved to [filename]"

## Quality Bar

- Separate strategic interpretation from factual updates — never mix
- At least one adoption metric per player when data available; if not: "Adoption data not disclosed this week."
- All factual lines must be date-specific and source-backed
- No vague claims without concrete evidence ("reportedly", "sources say" without citation = flag it)
- Sources consolidated at end — not inline
- Player headers in bold: **OpenAI**, **Anthropic**, etc.
- One blank line between major blocks inside each player section
- Healthcare / Med-Tech relevance must be included for every player — never skip
- Regulatory Tracker must always appear in full mode, even if result is "No material developments this week."
- Legal, Privacy & OEC section must always appear in full mode, even if result is "No material developments this week."
- Benchmark scores must cite source and date — never include unverified scores

## Anti-Patterns
- Never fabricate product names, launch dates, or metrics
- Never conflate strategic inference with factual update — keep layers clean
- Never skip the adoption trend section without noting unavailability
- Never produce the full brief if only one player was asked for
- Never omit sources — every factual claim needs one
- Never repeat last week's content verbatim — if nothing changed, write [NO CHANGE] and move on
- Never write a full player section for a player with no material change this week
- Never rewrite strategic positioning unless the direction actually shifted — cosmetic rewrites waste the reader's time
- Never carry forward unresolved watchlist items silently — always mark [PENDING] and note current status
- Never leave benchmark cells blank — use "—" for unchanged rows and "Not disclosed" for genuinely unavailable scores
