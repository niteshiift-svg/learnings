# FreeStyle Libre — Sensor Issue Resolution Journey Map

**Persona:** Type 2 Diabetes Patient — FreeStyle Libre user
**Journey:** Sensor issue noticed → resolution confirmed + monitoring resumed
**State:** Current
**Style:** Full Swimlane
**Stages:** 7
**Phase 1 Date:** 2026-03-20
**Phase 2 Date:** 2026-03-23
**Phase 2 Inputs:** Internal operational analytics · Internal business case benchmarking

---

## Phase 2 — Enriched Summary Table

| | **S1: Issue Noticed** | **S2: Sense-Making** | **S3: Self-Troubleshoot** | **S4: Decision to Contact** | **S5: Support Interaction** | **S6: Resolution Execution** | **S7: Back to Monitoring** |
|---|---|---|---|---|---|---|---|
| **Actions** | Cross-checks reading with finger stick | Validates vs. symptoms; searches forums | Re-scans, restarts app, searches FAQ | Locates serial number; picks contact channel | Explains issue from scratch to agent | Waits for replacement; reverts to finger sticks | Applies sensor; cross-checks accuracy |
| **Touchpoints** | LibreLink app, sensor, glucometer | Glucometer, Google, Reddit/forums | LibreLink help, YouTube, forums | Google, freestyle.abbott, LibreLink About | Phone, live chat, online form | Email/tracking, glucometer (gap coverage) | LibreLink app, reader, HCP |
| **Thought** | "Is this reading real or is the sensor lying to me?" | "If I treat and it's not real I'll spike. If I ignore and it's real, I'm in danger." | "Let me fix this before sitting on hold." | "How do I contact them? Where's the serial number?" | "I've already tried everything. Why do I have to explain it all again?" | "I'm without a sensor for days. That feels like a safety risk." | "I hope this one works. Should I ask my doctor about Dexcom?" |
| **Emotion** | Frustrated | 🔴 Broken | Frustrated | Frustrated | Frustrated | Neutral | Neutral → Positive |
| **Moment of Truth** | ✅ Yes | ✅ Yes | — | — | ✅ Yes | — | ✅ Yes |
| **Process Owner** | Patient | Patient | Patient | Patient | Abbott Customer Care | Abbott Fulfillment | Patient |
| **Evidence Grade** | 🔴 Assumption | 🔴 Assumption | 🟡 Partial | 🔴 Assumption | 🟢 Evidence | 🟡 Partial | 🟡 Partial |
| **Pain / Gap** | No data — validate before acting | No data — validate before acting | No Abbott-owned self-serve path; patients default to forums, not Abbott channels | Serial number friction assumed — unconfirmed | Stage carries full patient load with no deflection; high agent variability means experience is luck-dependent | Complaint intake manual and inconsistent; no bridging support during sensor gap | No post-resolution outreach; trust recovery left entirely to chance |

---

## Phase 2 — Change Log

| Stage | Evidence Grade | What Changed | Pain / Gap Surfaced |
|---|---|---|---|
| 1 — Issue Noticed | 🔴 Assumption | No new data — unchanged from Phase 1 | No data — validate before acting |
| 2 — Sense-Making | 🔴 Assumption | No new data — unchanged from Phase 1 | No data — validate before acting |
| 3 — Self-Troubleshoot | 🟡 Partial | Internal data flags call volume reduction potential for transactional issues — implies deflection gap before Stage 5 | No structured Abbott self-serve path; patients exhaust forums before reaching Abbott |
| 4 — Decision to Contact | 🔴 Assumption | No new data — unchanged from Phase 1 | Serial number friction unconfirmed — needs direct VoC |
| 5 — Support Interaction | 🟢 Evidence | 27% auth/triage + 47% troubleshooting + 14% data entry confirms agent overload; bottom-quartile AHT 40–50% worse than top confirms high variability | Agent carries entire load with no upstream deflection; patient experience at the most critical MoT is highly variable — effectively luck-dependent by agent |
| 6 — Resolution Execution | 🟡 Partial | Post-call complaint intake flagged as significant time drain; 14% data entry confirms manual back-end | Complaint data capture is inconsistent; no bridge support offered during sensor gap period |
| 7 — Back to Monitoring | 🟡 Partial | NPS and retention uplift cited in business case as "to be validated" — confirms Stage 7 is commercially material but unmonitored | Abbott has no structured post-resolution touchpoint; what happens after replacement is shipped is unknown |

---

## Phase 2 — Enrichment Summary

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
ENRICHMENT SUMMARY — PHASE 2
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Inputs used:     Internal operational analytics · Internal business case benchmarking

Evidence:        1 stage (Stage 5)
Partial:         3 stages (Stages 3, 6, 7)
Assumption:      3 stages (Stages 1, 2, 4) — no data, validate before Phase 3

Pains & Gaps identified: 4
  · Stage 3: No Abbott-owned self-serve path — patients default to forums
  · Stage 5: Agent overloaded; auth + triage + troubleshoot + data entry all sequential; high variability by agent quartile
  · Stage 6: Manual complaint intake; inconsistent data capture; no bridge support during sensor gap
  · Stage 7: No post-resolution outreach; NPS/retention impact unvalidated

Strongest evidence:  Stage 5
Research needed:     Stages 1, 2, 4 — still Assumption; highest priority for VoC before Phase 3

Narrative:
The enrichment confirms Stage 5 as the single most data-supported pain point in this
journey — and it is structurally overloaded. Authentication, triage, troubleshooting,
and manual data entry all fall sequentially on a single agent interaction, with no
deflection upstream and no tooling efficiency downstream. The 40–50% AHT gap between
agent quartiles means patient experience at the most critical moment of truth is
highly variable and effectively luck-dependent. The deeper risk is that Stages 1, 2,
and 4 — where patients are most vulnerable and most likely to act unsafely or drop
off — remain entirely unvalidated, and are the priority evidence gap before Phase 3.
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## Phase 1 — Base Journey Map

### Research Context

Generated with Claude Research-Led mode. Web research surfaced the following before stage generation:
- **Common issues:** Inaccurate/false low readings, sensor fell off, early sensor failure, Bluetooth/app connectivity drop, error codes on reader
- **Key insight:** Patients often don't know if a low reading is real or a sensor error — creates high-anxiety sense-making moment before any troubleshooting
- **Self-help path:** Patients hit forums (diabetes.co.uk, Reddit, BreakthroughT1D), app help, and manual before calling Abbott
- **Support friction:** Sensor serial number required upfront — many patients don't know where to find it
- **Resolution paths:** Replacement shipped / troubleshooting coaching / clinical escalation / recall pathway (FreeStyleCheck.com)
- ⚠️ **Active Safety Context:** Libre 3 recall (Nov 2025) — falsely low glucose readings linked to 736 injuries and 7 deaths. Replacement via FreeStyleCheck.com.

---

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
STAGE 1 — Issue Noticed
Sensor behaves unexpectedly → patient registers something is wrong
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

🎯  Actions
    · Glances at reader or phone — sees error code, unexpected low/high, or no reading
    · Checks sensor physically — notices partial detachment or scan failure
    · Receives alarm notification (false low alert, often at night)
    · Does a finger stick to cross-check the reading

📱  Touchpoints
    · FreeStyle LibreLink app or reader
    · Sensor on arm
    · CGM alarm / push notification
    · Finger stick glucometer (cross-check)

💭  Thought
    "Something's wrong — this reading doesn't feel right.
     Is my sugar actually this low or is it the sensor?"

😐  Emotion        Frustrated → Broken
    Confusion mixed with health anxiety — especially for a night alarm.
    Severity depends on reading type: a false low at 2am = Broken.

⚡  Moment of Truth    Yes
    First moment where trust in the device is tested. Patients who have
    experienced this before enter with pre-existing scepticism.
    A single unresolved doubt here begins the erosion of device loyalty.

🏷  Evidence Grade    Assumption

👤  Process Owner
    Patient — fully self-managed at this stage. No Abbott touchpoint yet.

⚙️  Back Stage
    · LibreLink app alarm logic and threshold settings
    · Sensor hardware — filament, adhesive, transmitter
    · No Abbott agent involved at this stage
```

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
STAGE 2 — Sense-Making & Worry
Patient tries to determine: is this reading real, or is the sensor wrong?
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

🎯  Actions
    · Checks symptoms against the reading (do I feel low? Am I sweating?)
    · Does repeat finger stick to confirm or rule out the sensor
    · Checks sensor age in app — is it still in warm-up or near end of life?
    · Searches "FreeStyle Libre inaccurate readings" on Google
    · Scans diabetes forums to see if others are reporting the same problem

📱  Touchpoints
    · Finger stick glucometer
    · Google / search engine
    · diabetes.co.uk, Reddit r/diabetes, BreakthroughT1D community
    · LibreLink app — sensor history and age check

💭  Thought
    "Is this real or is the sensor lying to me? If I treat this low
     and it's not real, I'll spike. If I ignore it and it is real,
     I'm in danger. What do I do?"

😐  Emotion        Broken
    Highest anxiety point in the entire journey. Patient faces a
    medical decision with no trustworthy data source. This is where
    harm — and dangerous compensating behaviour — can occur.

⚡  Moment of Truth    Yes
    If the patient treats a false low with fast-acting sugar, their
    glucose spikes. If they ignore a real low, they risk hypoglycaemia.
    The sensor's unreliability forces an impossible decision.
    This stage is the core safety risk of the entire journey.

🏷  Evidence Grade    Assumption

👤  Process Owner
    Patient — no Abbott touchpoint. Peer community partially fills the gap.

⚙️  Back Stage
    · Forum communities absorbing the support load Abbott isn't providing here
    · No structured Abbott guidance exists for this exact moment
    · ⚠️ Recall context (Nov 2025): false low readings on Libre 3 linked to
      736 injuries, 7 deaths — this stage is where that risk materialises
    🔍 Gap Candidate: No proactive Abbott communication or in-app triage
       guidance for "is this reading real?" — patients navigate this alone
```

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
STAGE 3 — Self-Troubleshoot
Patient attempts to fix the problem before contacting support
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

🎯  Actions
    · Re-scans sensor with phone or reader
    · Restarts LibreLink app and toggles Bluetooth off/on
    · Presses sensor down to check adhesion
    · Opens in-app help — looks for error guidance
    · Watches YouTube tutorials for the specific error
    · Posts on forum asking for help
    · Pulls out paper manual (if they kept it)

📱  Touchpoints
    · LibreLink app — in-app help / troubleshooting flows
    · FreeStyle Libre reader
    · YouTube
    · diabetes.co.uk / Reddit / BreakthroughT1D forums
    · Abbott FAQ / support pages
    · Paper manual

💭  Thought
    "Let me try to fix this myself before sitting on hold.
     Maybe it's just the Bluetooth. Other people must have had this."

😐  Emotion        Frustrated
    Patient is problem-solving but it's extra burden layered on top
    of already managing a chronic condition. Time and energy drain.

⚡  Moment of Truth    No

🏷  Evidence Grade    Partial
    Internal data signals call volume reduction potential for transactional
    issues — implies self-serve deflection gap before Stage 5.

👤  Process Owner
    Patient — still self-managed. Forum community fills support gap.

⚙️  Back Stage
    · LibreLink app error handling and in-app troubleshooting logic
    · Abbott FAQ and help content (often surface-level, not scenario-specific)
    · Peer forum community acting as unpaid first-line support
    🔍 Gap Candidate: No structured Abbott self-serve path — patients exhaust
       forums before reaching Abbott-owned channels
```

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
STAGE 4 — Decision to Contact Abbott
Self-troubleshooting exhausted — patient hunts for how to reach support
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

🎯  Actions
    · Searches "FreeStyle Libre customer support" on Google
    · Navigates freestyle.abbott to find the right support page
    · Locates sensor serial number in LibreLink app (About section)
    · Chooses contact channel: phone / online form / live chat
    · Checks FreeStyleCheck.com if they've seen recall news
    · Notes support hours: 8am–8pm ET (may need to wait)

📱  Touchpoints
    · Google search
    · freestyle.abbott/us-en/support
    · FreeStyleCheck.com (recall pathway)
    · LibreLink app — About section for serial number lookup
    · Phone: 855-632-8658
    · Online sensor support form / live chat

💭  Thought
    "How do I even contact them? And do I need the serial number?
     Where do I find that? This is taking way too long."

😐  Emotion        Frustrated
    Friction in navigating to support and preparing required information.
    Many patients give up here or vent on social media instead.

⚡  Moment of Truth    No
    But a high drop-off risk stage — patients who cannot easily find
    support contact or serial number may abandon the process entirely.

🏷  Evidence Grade    Assumption

👤  Process Owner
    Patient → handoff to Abbott Customer Care imminent

⚙️  Back Stage
    · Abbott support website navigation and contact routing
    · IVR phone system (if calling)
    · Serial number lookup logic in LibreLink app
    · Recall site routing (FreeStyleCheck.com separate from main support)
    🔍 Gap Candidate: Serial number not surfaced proactively in the app
       when a sensor error occurs — patient must know to look in About section
```

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
STAGE 5 — Support Interaction
Patient contacts Abbott — issue explained, case triaged
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

🎯  Actions
    · Calls 855-632-8658, submits online form, or opens live chat
    · Waits on hold or completes guided form questions
    · Provides sensor serial number, lot number, issue description
    · Describes what they've already tried (repeating Stage 3 steps)
    · Agent reviews case and determines replacement eligibility
    · May be asked to confirm shipping address and medical details

📱  Touchpoints
    · Phone: 855-632-8658 (7 days, 8am–8pm ET)
    · Live chat (24/7)
    · Sensor support form — freestyle.abbott
    · Email confirmation of case / reference number

💭  Thought
    "I just want this fixed. I've already tried everything.
     Why do I have to explain it all again?
     I hope they don't make me jump through hoops for a replacement."

😐  Emotion        Frustrated
    Hold times, repeating information already tried, and uncertainty
    about whether a replacement will actually be approved.

⚡  Moment of Truth    Yes
    The quality of this interaction determines whether Abbott recovers
    the patient relationship. A fast, empathetic agent who validates
    the patient's frustration and issues a replacement without friction
    can reverse the trust damage from earlier stages.
    A poor interaction — long hold, scripted responses, denial of
    replacement — accelerates churn and drives negative word-of-mouth.

🏷  Evidence Grade    Evidence
    27% of agent time on auth/triage + 47% on troubleshooting + 14% on
    manual data entry confirms full agent load. Bottom-quartile AHT 40–50%
    worse than top quartile confirms high variability in patient outcome.
    Two independent sources: operational analytics + internal benchmarking.

👤  Process Owner
    Abbott Customer Care

⚙️  Back Stage
    · Case management / CRM system
    · Serial and lot number validation
    · Replacement eligibility determination logic
    · FDA adverse event reporting trigger (if injury or serious complaint)
    · Escalation routing to clinical support team
    🔍 Gap Candidate: No upstream deflection and no agent tooling efficiency —
       auth + triage + troubleshoot + data entry all sequential on single call
```

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
STAGE 6 — Resolution Execution
Resolution path determined — replacement, fix, escalation, or recall pathway
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

🎯  Actions
    · Path A — Replacement: receives shipping confirmation, waits 1–5 days
    · Path B — Troubleshooting: walks through steps with agent on call
    · Path C — Clinical escalation: transferred to clinical team for accuracy review
    · Path D — Recall: directed to FreeStyleCheck.com, registers affected sensor
    · Applies workaround in the interim (back to finger sticks)
    · Receives and opens replacement packaging

📱  Touchpoints
    · Email: shipping confirmation and tracking
    · UPS / FedEx delivery
    · FreeStyleCheck.com (recall pathway)
    · Abbott clinical support team (escalation)
    · Finger stick glucometer (gap coverage while waiting)

💭  Thought
    "Okay, replacement is coming. But I'm without a sensor for days.
     Do I still have finger stick supplies? This gap in monitoring
     feels like a real safety risk."

😐  Emotion        Neutral
    Relief that resolution is in motion, but frustration about the
    monitoring gap. T2 patients without backup supplies feel exposed.

⚡  Moment of Truth    No
    But the monitoring gap is a hidden pain point — not addressed
    by Abbott's current support process.

🏷  Evidence Grade    Partial
    Post-call complaint intake flagged as significant time drain.
    14% data entry overlap confirms manual back-end processing.
    One source (operational analytics).

👤  Process Owner
    Abbott Fulfillment / Replacement Logistics

⚙️  Back Stage
    · Replacement warehouse and fulfillment centre
    · Shipping logistics (UPS/FedEx)
    · Clinical review team (escalation path)
    · FDA adverse event reporting system
    · Recall management — FreeStyleCheck.com pathway
    🔍 Gap Candidate: Post-call complaint intake is manual with inconsistent
       data capture; no bridging support offered during sensor gap period
```

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
STAGE 7 — Back to Monitoring
New sensor applied — patient resumes CGM or considers switching
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

🎯  Actions
    · Receives replacement sensor
    · Applies new sensor — waits through 2-hour warm-up
    · Resumes CGM monitoring, checks accuracy with finger stick
    · Evaluates: does this one feel trustworthy?
    · May post about experience on forum or leave a product review
    · Considers whether to stay with FreeStyle Libre or ask HCP for alternative

📱  Touchpoints
    · LibreLink app — new sensor activation
    · FreeStyle Libre reader (if using)
    · Endocrinologist / care team (if issue was reported to doctor)
    · App store review / forum post (patient shares experience)

💭  Thought
    "I hope this one works. But I've lost a bit of confidence.
     What if it happens again? Should I ask my doctor about Dexcom?"

😐  Emotion        Neutral → Positive (if sensor works)
    Cautiously back to normal. Trust is not fully restored.
    If this sensor also fails, switching intent becomes decision.

⚡  Moment of Truth    Yes
    The moment the replacement sensor reads accurately is the
    trust recovery point. If the new sensor also fails — or if
    no follow-up comes from Abbott — the patient churns.
    This is also where word-of-mouth forms: forums, reviews, HCP conversations.

🏷  Evidence Grade    Partial
    NPS and customer retention cited as "to be validated" in internal
    business case — confirms Stage 7 is commercially material but unmonitored.
    One source (internal benchmarking).

👤  Process Owner
    Patient — back to self-managed. Abbott has no post-resolution touchpoint.

⚙️  Back Stage
    · LibreLink app / sensor hardware
    · No structured Abbott follow-up or post-resolution outreach exists
    🔍 Gap Candidate: No post-resolution check-in from Abbott —
       trust recovery and churn risk entirely unmonitored
```

---

## Journey Summary

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
JOURNEY SUMMARY — PHASE 2
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Persona:     Type 2 Diabetes Patient — FreeStyle Libre user
Journey:     Sensor issue noticed → resolution confirmed + monitoring resumed
State:       Current
Style:       Full Swimlane
Stages:      7
Phase:       2 — Enriched

Evidence:    1 stage (Stage 5)
Partial:     3 stages (Stages 3, 6, 7)
Assumption:  3 stages (Stages 1, 2, 4)

Moments of Truth identified: 4
  · Stage 1 — Issue Noticed: first test of device trust
  · Stage 2 — Sense-Making: core safety risk — patient makes medical
    decisions with unreliable data
  · Stage 5 — Support Interaction: relationship recovery moment —
    agent quality determines churn vs. loyalty
  · Stage 7 — Back to Monitoring: trust restoration or final churn trigger

Pains & Gaps confirmed: 4
  · Stage 3: No Abbott-owned self-serve deflection path
  · Stage 5: Agent overloaded; high variability by quartile; no upstream deflection
  · Stage 6: Manual complaint intake; no bridging support during sensor gap
  · Stage 7: No post-resolution outreach; trust recovery unmonitored
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```
