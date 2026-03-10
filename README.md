# learnings
various projects, artifacts related to GenAI area

## GenAI Weekly Intel

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
/genai-weekly-intel
/genai-weekly-intel single-player: Anthropic
/genai-weekly-intel + LinkedIn post
