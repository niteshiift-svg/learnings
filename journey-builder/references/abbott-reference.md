# Abbott Company Reference
Journey Builder v1.1

This is a **living reference file** — it captures Abbott-specific nuances that inform journey maps: personas, touchpoints, regulatory context, and terminology. It grows as more journeys are run and validated.

This file is **not** a journey template library. Completed journey maps are saved separately in `nitesh-notes/journey-maps/samples/` when the user confirms.

Cross-reference this file when: a user names an Abbott persona, product, or business context. Always confirm with the user before applying a pre-built profile.

---

## Persona Library

### Soccer Mom (At-Home Diagnostics)
**Profile:** Female, 30–45, suburban, 1–3 children. Health-conscious, time-pressed, digitally comfortable but not clinically literate. Primary healthcare decision-maker for her family.
**Goal:** Find, order, and interpret a health test for her child without navigating complex clinical systems.
**Frustrations:** Medical jargon in results, waiting with no status updates, unclear next steps after results, needing a doctor just to interpret a basic answer.
**Digital comfort:** High on mobile and consumer apps. Low on clinical portals and PDF lab reports.
**Default style:** Healthcare
**Default product line:** At-Home Diagnostics

---

### HCP — Healthcare Provider (Ordering Context)
**Profile:** Physician, NP, or PA ordering diagnostic tests for patients. Time-constrained, evidence-focused, minimal patience for workflow friction.
**Goal:** Order the right test efficiently, track specimen status, and receive actionable results to inform patient care decisions.
**Frustrations:** Complex ordering systems, unclear test menus, slow turnaround time, results without clinical context or recommended next steps.
**Digital comfort:** High on EHR. Moderate on standalone ordering portals.
**Default style:** Full Swimlane

---

### Abbott Field Rep
**Profile:** Abbott sales or clinical specialist managing HCP accounts or pharmacy relationships in the field.
**Goal:** Onboard new accounts, drive product adoption, resolve issues before they escalate, and demonstrate value to HCP partners.
**Frustrations:** Lack of real-time account data, complex onboarding documentation, unclear escalation paths, disconnected CRM and field tools.
**Digital comfort:** High on mobile CRM. Lower on internal back-office systems.
**Default style:** Standard

---

### Caregiver
**Profile:** Adult (30–60) managing health decisions for an elderly or chronically ill family member. Often under emotional and logistical stress.
**Goal:** Navigate healthcare systems on behalf of someone else — ordering tests, interpreting results, and coordinating with providers.
**Frustrations:** Results not shared with the caregiver, communication gaps between systems and care teams, unclear or clinical-only instructions.
**Digital comfort:** Variable — often lower than the primary patient profile.
**Default style:** Standard or Healthcare depending on product
**Note:** Caregiver journeys often overlap with patient journeys but have an additional coordination layer — always clarify if the persona is acting for themselves or on behalf of someone else.

---

### Patient — Chronic Condition (CGM / Libre Context)
**Profile:** Adult managing a chronic condition (typically Type 1 or Type 2 diabetes) using continuous glucose monitoring technology.
**Goal:** Monitor and manage their condition with minimal friction — understand glucose data, act on it, stay adherent.
**Frustrations:** Sensor application errors, data interpretation confusion, connecting readings to lifestyle decisions, inconsistent connectivity between sensor and app.
**Digital comfort:** Medium — motivated to engage but needs guided setup and clear guidance.
**Default style:** Healthcare or Standard
**Default product line:** CGM — FreeStyle Libre
**Type 2 nuance:** Less clinically experienced than Type 1 patients; more likely to be confused by sensor errors and less likely to know the support process. Higher anxiety around false low readings.

---

## Product Line Nuances

### At-Home Diagnostics (BinaxNOW, Food Sensitivity, Infectious Disease)
**Key nuances:**
- OTC vs. Rx path creates two distinct journey branches — always clarify early
- Specimen collection at home is a high-anxiety stage — instructions must be clear or patient abandons
- Result interpretation is a known pain point — clinical language without guidance causes distress
- No real-time status during lab processing — creates anxiety gap

**Back-stage actors:** Warehouse (shipping), MD Rx (prescription authorization), CLIA Lab (processing), MD Review (result release for Rx tests)

**Regulatory gates:**
- Rx Required — MD authorization before specimen collection (Rx tests only)
- CLIA Lab Processing — CLIA-certified lab required
- MD Review — result held until MD releases to patient (Rx tests only)

---

### CGM — FreeStyle Libre
**Key nuances:**
- Sensor application is the highest abandonment risk stage for new users — physical placement matters
- Connectivity issues (Bluetooth drop, app permissions) are common first-week friction
- Inaccurate readings create patient safety risk — false lows can cause dangerous compensating behaviour
- ⚠️ **Active Safety Context (as of Nov 2025):** Abbott recalled certain Libre 3 and Libre 3 Plus sensors due to falsely low glucose readings — linked to 736 injuries and 7 deaths in the US. Replacement via FreeStyleCheck.com. Flag this in any Libre 3 issue resolution journey.
- Support process requires sensor serial number (found in LibreLink app → About section → last 3 sensors) — patients often don't know this upfront
- Phone support hours: 855-632-8658, 7 days 8am–8pm ET; live chat 24/7
- No post-resolution follow-up from Abbott — identified gap in patient trust recovery

**Back-stage actors:** HCP (prescription/clinical oversight), Pharmacy (dispense), Abbott Customer Care, FreeStyle LibreLink app, Abbott Fulfillment (replacement logistics)

---

### Nutrition (Ensure, Glucerna, Similac)
**Key nuances:**
- No Regulatory Gates for OTC nutrition — skip Healthcare style unless HCP ordering context applies
- Trial/tolerability is a critical early stage — taste and texture are real drop-off factors
- Caregiver is often the buyer, not the end consumer (Ensure for elderly parent, Similac for infant)

---

### Specialty Pharmacy / Rx (AllianceRx Walgreens context)
**Key nuances:**
- Prior Authorization is the highest friction and delay stage — often opaque to the patient
- Cold chain handling adds complexity for temperature-sensitive medications
- HUB services (patient support programs) exist but are underutilised by patients who don't know they're available

**Regulatory gates:** Prior Authorization (PA) before dispense; cold chain handling for temperature-sensitive medications

---

## Abbott-Specific Touchpoints

| Touchpoint | Context |
|---|---|
| Abbott.com / product site | Discovery and product information |
| Retail shelf / pharmacy | Physical discovery and OTC purchase |
| FreeStyle LibreLink app | Digital companion for CGM — data viewing, alerts, trend analysis |
| MyFreeStyle portal | Account management and supply ordering for Libre |
| FreeStyleCheck.com | Recall replacement portal — Libre 3 / Libre 3 Plus affected sensors |
| Mia | Abbott's enterprise GenAI knowledge assistant (internal use — not customer-facing) |
| Abbott Customer Care | Phone and chat support — setup, troubleshooting, replacement |
| Results portal / email | Digital result delivery for at-home diagnostic tests |
| HCP order portal | B2B ordering system for HCP-initiated diagnostic orders |
| GPASS | Global Payments accountability system — HCP engagement and TOV tracking (Sunshine Act / Open Payments compliance) |
| AbbottStore.com | D2C e-commerce for select Abbott consumer products |

---

## Regulatory Touchpoints by Product Area

| Gate | What it means in the journey | Appears in |
|---|---|---|
| Rx Required | Customer needs a prescription before specimen collection | At-Home Dx — Stage 3 |
| MD Rx Authorization | Abbott-affiliated MD authorizes the test collection | At-Home Dx — Stage 3 Back Stage |
| CLIA Lab Processing | Specimen processed by CLIA-certified laboratory | At-Home Dx — Stage 4 Back Stage |
| MD Result Review | MD reviews result before release to patient | At-Home Dx — Stage 5 Back Stage |
| Prior Authorization (PA) | Insurance approval required before pharmacy dispenses | Specialty Pharmacy — Stage 2 |
| Sunshine Act / GPASS | HCP engagement and payment transparency reporting | OEC / HCP-facing journeys |
| FDA Adverse Event Reporting | Triggered when a serious injury or complaint is filed with Abbott Customer Care | CGM / Dx support journeys |

---

## Abbott Terminology Reference

| Term | What it means in journey context |
|---|---|
| Specimen | The collected biological sample (blood, saliva, swab) shipped to the lab |
| Collection | The act of collecting the specimen at home per kit instructions |
| MD Rx | Physician authorization for a prescription test — required before collection |
| Result release | Moment when MD Review is complete and results become visible to the patient |
| OTC test | Over-the-counter — no Rx required, patient self-administers and reads results |
| Rx test | Prescription required — involves MD authorization, lab processing, and MD result review |
| GPASS | Global Payments Accountability System — tracks HCP transfers of value for compliance |
| HCP | Healthcare provider — physician, NP, PA, or pharmacist |
| TOV | Transfer of Value — any payment or benefit provided to an HCP, tracked under Sunshine Act |
| PA | Prior Authorization — payer approval required before a medication or test is dispensed |
| CLIA | Clinical Laboratory Improvement Amendments — federal certification required for clinical lab testing |
| Lighthouse | Abbott's term for a high-visibility GenAI pilot program |
| BTS | Business Technology Solutions — Abbott's enterprise technology division |
| Mia | Abbott's enterprise knowledge assistant, built on GenAI, for internal employee use |
| Libre 3 recall | Nov 2025 correction — falsely low glucose readings; replacement via FreeStyleCheck.com |

---

## How to Extend This File

Add to this file when:
- A new Abbott persona is encountered and confirmed during a journey run
- A new product nuance is surfaced by web research or user-provided knowledge
- A new regulatory gate or touchpoint is identified
- A new safety alert or recall is issued for an Abbott product

**Do not add:** Completed journey maps or stage templates — those go to `nitesh-notes/journey-maps/samples/` when user confirms.
