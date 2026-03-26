---
name: podcast-takeaway
description: Extract structured takeaways from a podcast episode given a YouTube or Spotify link. Produces episode metadata, core thesis, key insights, frameworks, quotes, action items, and AI/Product/Strategy relevance. Use when the user shares a podcast link or says "podcast takeaway", "summarize this podcast", or "notes from this episode".
---

# Podcast Takeaway

**Author:** Nitesh Luthra
**Version:** 1.1

## Modes

| Mode | When to use | Output |
|---|---|---|
| **Standard** (default) | User shares a link with no mode specified | ~5 min read — metadata + thesis + takeaways + quotes + actions + relevance |
| **Deep Notes** | User says "deep dive", "deep notes", "full notes" — or Claude offers and user confirms | ~15 min read — everything in Standard plus argument structure, chapter/segment breakdown, extended quotes, connections, open questions |

**When to offer Deep Notes:** If a transcript is available and the episode is >45 min or covers a complex topic, after generating Standard output ask:
> "Transcript is available and this is a long/complex episode. Want a deep dive version with full segment breakdown and extended notes?"

## Trigger
Activate when the user shares a YouTube or Spotify link in a podcast context, or says:
- "podcast takeaway", "podcast notes", "summarize this episode", "notes from this podcast"
- "what did I learn from [podcast]", "brief on this episode", "deep dive on this podcast"

---

## Step 0 — Detect Input Type

Identify the input:

| Input | Type | Action |
|---|---|---|
| YouTube link (youtube.com, youtu.be) | Video/Podcast | Fetch page + search for transcript |
| Spotify link (open.spotify.com/episode/) | Podcast | Fetch episode page for show notes + search for transcript |
| Episode title or description (pasted) | Text | Use directly |
| No input yet | — | Ask: "Share a YouTube or Spotify link, or paste the episode title/description." |

---

## Step 1 — Extract Content

### YouTube
1. WebFetch the YouTube URL — extract title, channel, upload date, description
2. WebSearch for `"[episode title]" transcript` — look for auto-generated or published transcript
3. If transcript found: use full transcript for analysis
4. If no transcript: use video description + WebSearch for episode summary/show notes from podcast website

### Spotify
1. WebFetch the Spotify episode URL — extract title, show name, host, date, episode description
2. WebSearch for `"[episode title]" "[show name]" transcript` — many shows publish transcripts on their site
3. If transcript found: use full transcript for analysis
4. If no transcript: use episode description + show notes only — note this in output as **[Show notes only — no transcript found]**

### Minimum viable content
If only show notes / description are available (no transcript), proceed but flag it:
> ⚠️ No transcript found. Analysis based on episode description and show notes — may be incomplete.

---

## Step 2 — Generate Structured Output

Produce the following sections in order. Use clean markdown, no filler text.

---

### EPISODE BRIEF

| Field | Value |
|---|---|
| Title | |
| Show | |
| Host | |
| Guest(s) | |
| Date | |
| Length | |
| Source | YouTube / Spotify |
| Link | |

---

### WHAT IT'S ABOUT
2–3 sentences. Plain language. What is this episode actually about — not just the title.

---

### CORE THESIS
The central argument or idea the episode is building toward. 1–2 sentences. This is not a summary — it is the *point* of the episode.

---

### KEY TAKEAWAYS
5–7 bullets. Each one is a discrete, actionable or memorable idea. Lead with the insight, not the context.

- Takeaway 1
- Takeaway 2
- ...

---

### FRAMEWORKS & MENTAL MODELS
Named frameworks, models, or structured thinking tools mentioned. If none, omit this section.

| Name | What it is | Where it applies |
|---|---|---|
| | | |

---

### MEMORABLE QUOTES
2–3 direct quotes worth keeping. Attribute to speaker. Only include if sourced from transcript — do not fabricate.

> "Quote here." — Speaker

---

### ACTION ITEMS
What to *do* with this episode. 3–5 bullets. These are concrete, not generic.

- Action 1
- Action 2
- ...

---

### RELEVANCE — AI / PRODUCT / STRATEGY
Flag how this episode connects to: **AI & GenAI**, **Product Management**, or **Strategy & Leadership**.

| Domain | Relevant? | Why |
|---|---|---|
| AI & GenAI | Yes / Partial / No | |
| Product Management | Yes / Partial / No | |
| Strategy & Leadership | Yes / Partial / No | |

**Key connection:** 1–2 sentences on the most direct application.

---

### REFERENCE LINKS
Any articles, transcripts, show notes, or related content found during research. Always include if found — these are the "go deeper" resources.

| Resource | What it covers |
|---|---|
| Link title — URL | One line on what's there |

If no external references found beyond the episode itself, omit this section.

---

## Step 2b — Deep Notes (if mode = Deep Notes)

Run this section **in addition to** all Standard sections. Insert after RELEVANCE.

---

### ARGUMENT STRUCTURE
How does the episode build its case? Map the logical flow: setup → tension → argument → resolution.

1. Setup — what problem or context is established
2. Tension — what challenge, paradox, or question is raised
3. Argument — how the guest/host addresses it
4. Resolution / Takeaway — what conclusion or call-to-action is reached

---

### SEGMENT BREAKDOWN
Break the episode into 4–8 named segments with timestamps (if available) and a 2–3 sentence summary of each.

| Segment | Timestamp | Summary |
|---|---|---|
| | | |

---

### EXTENDED QUOTES
5–8 quotes that capture the nuance of the argument. Prioritize quotes that would not survive paraphrasing — where the specific wording matters. Attribute to speaker.

> "Quote." — Speaker

---

### CONNECTIONS & CONTRASTS
What does this episode connect to, challenge, or extend?

- **Connects to:** [other ideas, frameworks, or episodes this builds on]
- **Contrasts with:** [counterarguments or competing views mentioned or implied]
- **Extends:** [how this advances thinking on a known topic]

---

### OPEN QUESTIONS
What did the episode leave unresolved, debate without settling, or raise without answering?

- Question 1
- Question 2
- ...

---

## Step 3 — Close

After output is generated, always ask:

> "Want to go deeper, save this, or both?
> - **Deep dive** — full segment breakdown, argument structure, extended quotes, open questions
> - **Save** — write to `nitesh-notes/podcasts/[ShowName]_[EpisodeTitle]_[YYYY-MM-DD].md`
> - **Both** — deep dive first, then save the full version"

Handle responses:
- "deep dive" / "go deeper" → run Step 2b, then offer to save again
- "save" → write Standard output to file
- "both" → run Step 2b, then save the full output (Standard + Deep Notes) to file
- "neither" / "no" → done

Only save if user confirms. Append to existing file if same show/episode already exists.

---

## Quality Rules

- Never fabricate quotes — only include quotes sourced from transcript
- If transcript not available, flag it clearly at the top of output
- Keep takeaways crisp — one idea per bullet, no multi-clause rambling
- Relevance table must be honest — "No" is a valid answer
- Do not pad output — if frameworks section is empty, skip it
- Episode Brief table must be complete — do not leave fields blank without noting "Not found"
