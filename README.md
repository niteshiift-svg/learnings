# Claude Skills Creation
various projects, artifacts related to GenAI area


| # | Skill | Trigger | What It Does |
|---|-------|---------|--------------|
| 1 | GenAI Weekly Intel | "GenAI weekly brief" / "what happened in AI this week" | Produces a delta-tracked weekly intelligence brief across 10 AI players with regulatory, benchmark, and LinkedIn post add-ons |
| 2 | Book Summary & Reflection | "book summary" / "summarize chapter" | Generates evidence-grounded chapter summaries with 5-part structure and memory anchors for precise recall |

## 1- GenAI Weekly Intel

A Claude Code skill that produces a weekly intelligence brief tracking the GenAI competitive landscape across major players — OpenAI, Anthropic, Google, Microsoft, AWS, xAI, Meta, Salesforce, Adobe, and others.

### What it does
- **Full Weekly Brief** — covers all players, delta-tracked week-over-week
- **Single-Player Deep Dive** — focused snapshot on one company
- **Regulatory & Policy Tracker** — FDA, EU AI Act, US AI policy, enterprise governance
- **Benchmark Tracker** — frontier model scores (SWE-Bench, GPQA, OSWorld) with sourcing
- **LinkedIn Post add-on** — practitioner-voice post built from the week's top signal
- **Deck Slide Format** — slide-ready bullets per player

### Output structure
Each player section follows a two-layer format:
1. **Strategic positioning** — 1-sentence interpretation of direction
2. **Fact-based change lines** — date-anchored, source-backed updates

Outputs are auto-saved to `nitesh-notes/genai-intel/` with dated filenames.

### How to run
- /genai-weekly-intel
- /genai-weekly-intel single-player: Anthropic
- /genai-weekly-intel + LinkedIn post



## 2- Book Summary & Reflection

A Claude Code skill for deep, evidence-grounded chapter-by-chapter book summaries. Built for non-fiction readers who want to reconstruct arguments from memory, not just collect takeaways.

### What it does
- **Chapter summaries** — structured output per chapter on demand
- **Two depth modes** — Detailed (richer mechanism, 5 memory anchors) or Summarized (compressed, 3 anchors)
- **Full-book synthesis** — optional, only when explicitly requested
- **Export to file** — appends all chapters to one rolling file per book

### Output structure per chapter
Each chapter follows a 5-part format:
1. **Core Claim** — the central argument in 2-3 sentences
2. **Mechanism** — how ideas moved, who funded them, who resisted, how they spread
3. **Evidence** — named people, dates, places, primary texts, institutions
4. **Argument Flow** — how this chapter advances the book's overall thesis
5. **Memory Anchors** — 3-5 precise recall points to reconstruct the argument

Outputs are saved to `nitesh-notes/books/<BookName>_summary_<YYYY-MM-DD>.md`.

### How to run
/book-summary-reflection
/book-summary-reflection Inglorious Empire, Chapter 3, detailed
/book-summary-reflection same book, Chapter 4, summarized



### Design principles
- Strictly grounded in the book's content — no generic inference or modern analogies added
- Named specifics only — no vague references ("several historians", "many examples")
- Mechanism over themes — explains how things worked, not just what happened
- Never summarizes chapters you didn't ask for
