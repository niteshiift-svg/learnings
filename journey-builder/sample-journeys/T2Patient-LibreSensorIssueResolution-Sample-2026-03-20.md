# FreeStyle Libre — Sensor Issue Resolution Journey

**Persona:** Type 2 Diabetes Patient — FreeStyle Libre user
**Journey:** Sensor issue noticed → resolution confirmed + monitoring resumed
**State:** Current
**Style:** Full Swimlane
**Stages:** 7
**Date:** 2026-03-20
**Evidence:** All 7 stages at Assumption — Phase 2 enrichment not yet run

---

## Research Context

Generated with Claude Research-Led mode. Web research surfaced the following before stage generation:
- **Common issues:** Inaccurate/false low readings, sensor fell off, early sensor failure, Bluetooth/app connectivity drop, error codes on reader
- **Key insight:** Patients often don't know if a low reading is real or a sensor error — creates high-anxiety sense-making moment before any troubleshooting
- **Self-help path:** Patients hit forums (diabetes.co.uk, Reddit, BreakthroughT1D), app help, and manual before calling Abbott
- **Support friction:** Sensor serial number required upfront — many patients don't know where to find it
- **Resolution paths:** Replacement shipped / troubleshooting coaching / clinical escalation / recall pathway (FreeStyleCheck.com)
- ⚠️ **Active Safety Context:** Libre 3 recall (Nov 2025) — falsely low glucose readings linked to 736 injuries and 7 deaths. Replacement via FreeStyleCheck.com.

---

## Journey Map

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

🏷  Evidence Grade    Assumption

👤  Process Owner
    Patient — still self-managed. Forum community fills support gap.

⚙️  Back Stage
    · LibreLink app error handling and in-app troubleshooting logic
    · Abbott FAQ and help content (often surface-level, not scenario-specific)
    · Peer forum community acting as unpaid first-line support
    🔍 Gap Candidate: Abbott FAQ does not cover scenario-specific error
       resolution — patients default to forums instead
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

🏷  Evidence Grade    Assumption

👤  Process Owner
    Abbott Customer Care

⚙️  Back Stage
    · Case management / CRM system
    · Serial and lot number validation
    · Replacement eligibility determination logic
    · FDA adverse event reporting trigger (if injury or serious complaint)
    · Escalation routing to clinical support team
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

🏷  Evidence Grade    Assumption

👤  Process Owner
    Abbott Fulfillment / Replacement Logistics

⚙️  Back Stage
    · Replacement warehouse and fulfillment centre
    · Shipping logistics (UPS/FedEx)
    · Clinical review team (escalation path)
    · FDA adverse event reporting system
    · Recall management — FreeStyleCheck.com pathway
    🔍 Gap Candidate: No bridging support offered during sensor gap period —
       patients left without monitoring coverage for 1–5 days with no guidance
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

🏷  Evidence Grade    Assumption

👤  Process Owner
    Patient — back to self-managed. Abbott has no post-resolution touchpoint.

⚙️  Back Stage
    · LibreLink app / sensor hardware
    · No structured Abbott follow-up or post-resolution outreach exists
    🔍 Gap Candidate: No post-resolution check-in from Abbott —
       trust recovery left entirely to chance
```

---

## Journey Summary

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
JOURNEY SUMMARY — PHASE 1
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Persona:     Type 2 Diabetes Patient — FreeStyle Libre user
Journey:     Sensor issue noticed → resolution confirmed + monitoring resumed
State:       Current
Style:       Full Swimlane
Stages:      7
Evidence:    All 7 stages at Assumption — ready for Phase 2 enrichment

Moments of Truth identified: 4
  · Stage 1 — Issue Noticed: first test of device trust
  · Stage 2 — Sense-Making: core safety risk — patient makes medical
    decisions with unreliable data
  · Stage 5 — Support Interaction: relationship recovery moment —
    agent quality determines churn vs. loyalty
  · Stage 7 — Back to Monitoring: trust restoration or final churn trigger

Gap Candidates identified: 4 (flagged for Phase 3)
  · Stage 2: No in-app triage for "is this reading real?"
  · Stage 3: FAQ does not cover scenario-specific errors
  · Stage 4: Serial number not surfaced proactively on error
  · Stage 6: No bridging support during sensor gap period
  · Stage 7: No post-resolution follow-up from Abbott
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```
