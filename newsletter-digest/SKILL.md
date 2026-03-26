---
name: newsletter-digest
description: Summarize subscribed email newsletters from Gmail organized by theme (GenAI/AI, Product & Strategy, Finance & Investing, Other) with narrative style, real reference links, and cross-theme action items. Use when the user says "newsletter digest", "summarize my newsletters", "what did I miss in my newsletters", or "newsletter brief".
---

# Newsletter Digest

**Author:** Nitesh Luthra
**Version:** 1.0

## Trigger
Activate when the user says:
- "newsletter digest", "summarize my newsletters", "newsletter brief"
- "what did I miss", "catch me up on newsletters"
- "newsletter summary for [today / this week / last 3 days]"

---

## Step 0 — Ask Date Range

Before doing anything else, ask:

> "How many days do you want to cover?
> - **1** — Today only
> - **3** — Last 3 days
> - **7** — Last 7 days (default)
> - **Custom** — e.g. 'last 2 days', 'since Monday'"

If the user already specified a range in their trigger ("newsletter digest last 3 days"), skip this and proceed.

Convert the chosen range to a Gmail date filter:
- Today → `after:YYYY/MM/DD` (today's date)
- Last 3 days → `after:YYYY/MM/DD` (3 days ago)
- Last 7 days → `after:YYYY/MM/DD` (7 days ago)
- Custom → parse and apply accordingly

---

## Step 1 — Fetch Newsletters from Gmail

Search Gmail for newsletter emails within the chosen date range. **Always search inbox and archive only — do NOT use `in:anywhere` or `includeSpamTrash: true`.**

If the user specified a sender filter (e.g. "ARK only", "just Silly Money"), add `from:` to the query. Otherwise search broadly:

```
after:YYYY/MM/DD (from:beehiiv.com OR from:substack.com OR from:arkinvest.com OR from:convertkit.com OR from:mailchimp.com OR from:morningbrew.com OR from:diamandis.com OR label:newsletters OR unsubscribe)
```

For each result:
- Read the full email body
- Extract: sender name, newsletter name, subject line, date, body content, embedded links

**Step 1b — Full Content Fetch (preview detection)**

After reading each email, check if the body is a short preview:

**Preview signals:**
- Body is under ~400 words, OR
- Contains phrases like "Read more", "Keep reading", "Continue reading", "Read on Substack", "View full post", OR
- Body ends abruptly mid-thought with a content link

**If preview detected:**
1. Extract the article URL — look for the first meaningful content link (Substack, beehiiv, Ghost, Every.to, etc.) — not tracking wrappers, unsubscribe links, or social icons
2. If the link is a tracking wrapper (`/e3t/`, `/click/`, `r.email.`, `/track/`): skip WebFetch — use email preview only and note "[Full content behind tracking link — preview only]"
3. If the link is a clean direct URL: WebFetch it to get the full post content
4. Use the fetched content for the digest instead of the email body
5. Note at bottom of that sender's section: "*Full post fetched from [domain]*"

**If no preview detected (full content in email):** proceed directly to classification — no WebFetch needed.

**Known sender → theme mapping (expand as new subscriptions are detected):**

| Sender / Domain | Newsletter Name | Theme |
|---|---|---|
| ark@arkinvest.com | ARK Invest | Finance & Investing |
| sillymoney@mail.beehiiv.com | Silly Money | Finance & Investing |
| aakashg / growproduct | Product Growth | Product & Strategy |
| theneurondaily.com / neuron | The Neuron Daily | GenAI / AI |
| aibyaakash.com | AI by Aakash | GenAI / AI |
| Every.to / every | Every | Product & Strategy |
| lenny@lennysnewsletter.com | Lenny's Newsletter | Product & Strategy |
| stratechery | Stratechery | Product & Strategy |
| morningbrew.com | Morning Brew | Other (General Business) |
| diamandis.com / Peter H. Diamandis | Metatrends | Other (Emerging Tech) |
| Saanya Ojha / The Change Constant | The Change Constant | Other |

**Optional sender filter:** If user says "ARK only" or "just [newsletter name]", restrict search to that sender and note it in the digest header.

**Auto-detect new newsletters:** If a sender isn't in the map but email contains "unsubscribe" and is clearly editorial content, classify as "Other" and note the sender name for potential future mapping.

---

## Step 2 — Classify by Theme

Group all fetched newsletters into four themes:

1. **GenAI / AI** — AI tools, model releases, enterprise AI, GenAI strategy
2. **Product & Strategy** — Product management, business strategy, innovation, leadership
3. **Finance & Investing** — Markets, investing, personal finance, macro
4. **Other** — Anything that doesn't fit cleanly above

If a newsletter spans two themes (e.g. ARK covers both investing and AI), place it in its dominant theme and note the crossover in the narrative.

---

## Step 3 — Extract Reference Links

For each newsletter, extract meaningful link labels from the email body (do not web search to resolve them yet):

1. Identify meaningful links — reports, articles, videos, research, tools
2. Filter out noise — unsubscribe links, social icons, tracking pixels, footer links, mailto:
3. Note whether links are tracking wrappers (patterns: `/e3t/`, `/click/`, `r.email.`, `/track/`, `?utm_`, `hs/preferences`)
4. In the digest output, show link labels only (no URL) for tracking wrappers — mark as `[label — link pending]`
5. Only include clean direct URLs if they are already non-tracking

**Deferred resolution:** After generating the digest, ask the user: "Want me to resolve the reference links? (uses extra web searches)". If yes, resolve via WebSearch using the link labels and update the digest before saving.

---

## Step 4 — Generate Digest Output

### Header

```
## Newsletter Digest — [Date Range]
[e.g. "Mar 24–26, 2026 · 3 newsletters · 2 themes"]
```

### Week's Signal
1–2 sentences. The single most important idea or pattern across all newsletters this period. Not a list — one synthesized observation.

---

### Per Theme → Per Sender

For each theme that has newsletters, output in this format:

```
### [Theme Name]

**[Newsletter Name]** · [Date] · [Issue title if available]
*[Strategic positioning — 1 sentence interpretation of the core argument]*

[Narrative paragraph 1 — what the newsletter is actually saying, with context]

[Narrative paragraph 2 — strategic inference, implication, or "why this matters"]

**Go deeper:** [Link label 1](URL) · [Link label 2](URL)

---
```

**Narrative style rules (borrow from genai-weekly-intel):**
- Two layers: what they said (factual) + what it means (inference) — never mixed in same sentence
- 2 short paragraphs per sender — each with one job
- Lead with the insight, not the setup
- Inference-first tone: practitioner, not journalist
- No superlatives — no "exciting", "game-changing", "incredible"
- If content is thin (short email, show notes only): one paragraph is fine — do not pad
- Flag if email had no substantive content: "[Newsletter name] — No substantive content this issue."

---

### Actions This Week

Cross-theme action items — only what's concrete and non-obvious.

| Theme | Action |
|---|---|
| GenAI / AI | ... |
| Product & Strategy | ... |
| Finance & Investing | ... |

3–5 rows max. Skip themes with no actionable signal.

---

## Step 5 — Save by Default

Always save after generating output — do not wait for user to ask.

Filename: `nitesh-notes/newsletters/Newsletter-Digest-YYYY-MM-DD.md`

If a file for that date already exists, append to it — do not overwrite.

Confirm: "Saved to `nitesh-notes/newsletters/Newsletter-Digest-YYYY-MM-DD.md`"

---

## Quality Rules

- Narrative over bullets — every sender gets prose, not a list
- Strategic layer and factual layer stay separate — never mix interpretation with fact
- Reference links must be real, working URLs — tracked/redirected links must be resolved via web search before including
- If a link can't be resolved: show the label only, no URL
- Theme classification must be honest — "Other" is fine; don't force-fit
- Week's Signal must be a synthesis, not a repeat of the first newsletter's point
- Actions must be concrete — "read the report" is not an action; "review 529 superfunding window before Q2" is
- Never fabricate content — if email body is empty or inaccessible, note it and skip
- New sender detected → note it at the bottom: "New sender detected: [name] — classified as [theme]. Add to sender map?"

---

## Anti-Patterns

- Never include unsubscribe links, social icons, or footer links as reference links
- Never pad thin newsletters with extra inference — if content is light, say so
- Never produce a digest if no newsletters found in the date range — say "No newsletters found for [range]" and offer to extend the window
- Never skip the Week's Signal — even one newsletter warrants a synthesis line
- Never leave Actions table empty if there are clear signals — extract at least one
