# Journey Styles — Reference Guide
Journey Builder v1.0

---

## Row Catalog

### Mandatory Rows (Standard and above — always produced)

| Row | Icon | What it captures |
|---|---|---|
| Stage Name | — | Journey stage name, trigger, and outcome boundary |
| Actions | 🎯 | What the customer actively does — specific verbs, not descriptions |
| Touchpoints | 📱 | Channel or surface they interact with |
| Thought | 💭 | What they're thinking at this moment — first person, specific |
| Emotion | 😐 | Emotional state — four-grade scale only |
| Moment of Truth | ⚡ | Yes/No flag + reason why this stage makes or breaks the experience |
| Evidence Grade | 🏷 | Assumption (Phase 1) → Evidence / Partial / Assumption (Phase 2) |

### Optional Rows (style-dependent — only added when style requires or user requests)

| Row | Icon | When it appears |
|---|---|---|
| Process Owner | 👤 | Full Swimlane, Healthcare |
| Back Stage | ⚙️ | Full Swimlane, Healthcare |
| Regulatory Gate | 🏥 | Healthcare only |
| Data Signals | 📊 | Phase 2 enrichment — all styles |
| Desired Experience | ✨ | Future State style only |
| Target Emotion | 🎯 | Future State style only |
| Capability Required | 🔧 | Future State style only — feeds Capability Mapper |
| Opportunities | 💡 | Phase 3 Diagnose only — **never generated in Phase 1 or 2** |

---

## Named Styles

### Express
**Use for:** Quick workshops, early ideation, executive briefings, time-boxed sessions
**Mandatory rows:** Stage, Actions, Touchpoints
**Stage count:** 3–5
**Note:** Express maps are fast — no Thought, Emotion, or MOT rows. Use only when speed matters more than depth. Flag to user that Express maps cannot be enriched to Evidence grade without first upgrading to Standard.

---

### Standard
**Use for:** D2C consumer apps, SaaS products, B2C services, wellness platforms
**Mandatory rows:** Stage, Actions, Touchpoints, Thought, Emotion, MOT, Evidence Grade
**Stage count:** 4–6
**Default:** Apply Standard when no stronger signal suggests another style.

---

### Full Swimlane
**Use for:** Complex operations, B2B services with service delivery, multi-actor journeys, internal employee journeys
**Mandatory rows:** All Standard rows + Process Owner + Back Stage
**Stage count:** 5–8
**Note:** Back Stage should only include actors and systems actually known or referenced by the user. Never invent back-stage actors.

---

### Healthcare
**Use for:** Abbott at-home diagnostics, CGM journeys, Rx-involved experiences, any journey with clinical or lab touchpoints
**Mandatory rows:** All Full Swimlane rows + Regulatory Gate
**Stage count:** 5–7
**Auto-suggest when:** persona is patient, HCP, or caregiver; product involves Rx, Lab, specimen collection, clinical result delivery, or MD review
**Reference:** Back-stage actors and regulatory gates for Abbott product lines are in `abbott-reference.md`

---

### Future State
**Use for:** Target experience design, transformation programs, capability planning, aspirational journey mapping
**Mandatory rows:** Stage, Desired Experience, Target Emotion, Capability Required, MOT
**Rows excluded:** Thought, Emotion (current), Back Stage, Regulatory Gate
**Stage count:** 4–6
**Important:** Capability Required rows in Future State maps feed directly into Capability Mapper (Mode B). Format them as: "[What the org must be able to do]" — not "build X system" or "implement Y tool." Capability, not solution.

---

## Emotion Grading Scale

Use exactly four grades. Never use freeform emotion labels.

| Grade | Meaning | Signal to look for |
|---|---|---|
| **Positive** | Customer feels confident, satisfied, or delighted | Experience meets or exceeds expectation |
| **Neutral** | Customer is proceeding without strong feeling | Functional but unremarkable — gets the job done |
| **Frustrated** | Customer is experiencing friction, confusion, or delay | Experience falls below expectation but is recoverable |
| **Broken** | Customer is blocked, lost, or about to abandon | Experience fails at a critical point — churn or drop-off risk |

**Grading rules:**
- Never assign Positive without a clear signal of delight or satisfaction
- Neutral is not a default — it means the experience is genuinely unremarkable, not that you don't know
- Frustrated and Broken are different: Frustrated = still in the journey but struggling; Broken = likely to exit
- If the emotional state is unclear from user input or domain knowledge, flag as: `[Assumed — validate]`

---

## Stage Count Guidelines

| Journey Type | Recommended | Hard Max |
|---|---|---|
| D2C / consumer app | 4–5 | 6 |
| SaaS onboarding | 4–6 | 7 |
| Healthcare / diagnostic | 5–7 | 8 |
| At-home test kit (Abbott) | 6 | 7 |
| B2B / enterprise | 5–8 | 8 |
| Loyalty / retention loop | 3–5 | 6 |
| Internal employee journey | 4–6 | 7 |

**If the journey exceeds the hard max:**
Propose splitting into sub-journeys before generating. Examples:
- "Awareness to Purchase" + "Onboarding to First Value"
- "Pre-Collection" + "Collection to Results"
- "Onboarding" + "Activation" + "Retention"

Never cram more than 8 stages into a single map — it loses scanability and becomes unactionable.

---

## Moment of Truth Identification Criteria

A stage qualifies as a Moment of Truth if ANY of the following are true:

1. Customer makes a go/no-go decision (purchase, consent, re-order, abandon)
2. Trust is established or broken (first result delivery, first error message, first contact with support)
3. Emotional peak or valley — highest Positive or deepest Broken emotion in the map
4. Churn or abandonment risk is highest at this stage
5. Brand perception is formed or cemented here — customer forms a lasting impression

**Calibration:** Most journeys have 2–4 MOTs. Healthcare and support journeys may have more due to patient safety stakes. Flag if you are identifying 5 or more — that is over-flagging. Not every high-friction stage is a Moment of Truth — reserve the flag for stages where the customer relationship is genuinely won or lost.

---

## Commonly Missed Stages

These stages are frequently omitted in cold-start journeys but are often the most insightful. Prompt for them when the journey type matches.

| Stage | Journey types where it's commonly missed | Why it matters |
|---|---|---|
| **Sense-Making / Worry** | Healthcare, support/resolution, diagnostic | Patient/customer tries to understand severity before acting — highest anxiety, often where dangerous compensating behaviour occurs |
| **Self-Troubleshoot** | Support, tech product, device | Customer tries to fix it themselves before contacting support — peer forums absorb load that the org should own |
| **Decision to Contact** | Support, complaints, returns | Navigating to support is itself a friction-filled stage — serial number hunts, hold time anticipation, channel confusion |
| **Post-Resolution / Back to Normal** | Support, onboarding, healthcare | Trust recovery or churn crystallisation — often omitted, but where NPS and word-of-mouth form |
| **Monitoring Gap** | Healthcare device, subscription | Period between issue and fix — patient/customer is exposed and unsupported, often invisible to the org |
| **Workaround** | Any high-friction journey | What the customer does instead of using the product/service — signals unmet need and hidden competitive risk |
| **Caregiver Coordination Layer** | Healthcare, elderly care, paediatric | When a third party (caregiver) is managing the journey on behalf of the patient — adds coordination friction invisible in patient-only maps |

---

## Evidence Tagging Rules (Phase 2)

| Tag | Criteria |
|---|---|
| **Evidence** | 2+ independent data sources confirm the experience at this stage |
| **Partial** | 1 data source, OR data is indirect / inferential |
| **Assumption** | No data — based on domain knowledge, analogous products, or best practice only |

### Source types accepted

| Source type | Independence note |
|---|---|
| User interviews / ethnographic research | Each study = 1 source |
| NPS open-text themes | Entire NPS survey = 1 source regardless of volume |
| Support ticket categories | Ticket corpus = 1 source |
| Survey results (quantitative or qualitative) | Each distinct survey = 1 source |
| Session analytics (drop-off, time-on-task, funnel conversion) | Analytics dataset = 1 source |
| Stakeholder or SME observations | Each distinct observer / session = 1 source |
| Field research notes | Each field session = 1 source |

**Source independence rule:** Two sources are independent only if they come from different research methods.
- NPS verbatim + support ticket = 2 independent sources ✓
- Two NPS verbatims from the same survey = 1 source ✗
- User interview + session recording of the same session = 1 source ✗

### Signal mapping rule
Map VoC signals to the stage where the friction **originates**, not where the complaint **surfaces**.

Example: Customer reports "I had no idea where my sample was" in a post-results NPS survey.
→ Map to the Shipping / Lab Analysis stage — that is where the information gap begins.
→ Do not map to the Results stage — that is only where the complaint became visible.
