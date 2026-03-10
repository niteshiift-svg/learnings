---
name: book-summary-reflection
description: Summarize and reflect on books chapter-by-chapter with strict evidence grounding. Use when the user wants chapter summaries, argument reconstruction, reading reflection, or structured notes from books/audiobooks/highlights. Default to only requested chapters; do not summarize the full book unless explicitly requested.
---

# Book Summary & Reflection

## Trigger
Activate when the user says "summarize this book", "book summary", "chapter summary", "summarize chapter", "book notes", "reading reflection", or "let's work on [book title]".

Keywords: summarize, chapter, book notes, reading reflection, book summary, audiobook notes

## Modes

### Mode 1: Interactive (Default)
- Work chapter-by-chapter in chat
- Confirm scope and depth before generating output
- Refine wording and interpretation with the user before saving
- Never assume the next chapter — always wait for the user to request it

### Mode 2: Export Mode (Optional)
- Append each chapter run to one rolling file per book
- Do not create one file per chapter
- Filename pattern: `nitesh-notes/books/<BookName>_summary_<YYYY-MM-DD>.md`
- Prefer appending to the latest existing file matching `<BookName>_summary_*.md`
- Only activate export mode when the user explicitly asks to save

## Intake Questions (Ask First)

Before generating any output, ask these three questions if not already provided:

1. What book are we working on? (title + author)
2. Which chapter(s) do you want right now?
3. Do you want **detailed** or **summarized** output for this chapter?

If all three are already provided in the user's message, skip directly to output.

## Instructions

### Step 1: Confirm Scope
- Capture book title and exactly which chapter(s) to process
- Confirm output depth: `detailed` or `summarized`
- If scope is unclear, ask before writing — never assume

### Step 2: Build Chapter Output

Use this structure for each chapter:

---

**Chapter [n]: [Title]**

**Core Claim**
A tight 2-3 sentence paragraph capturing the central argument or event of this chapter. What is the author trying to establish here?

**Mechanism**
How did the events, ideas, or arguments move? Who were the key actors? What institutions were involved? Who funded it, who resisted it, how did it spread or fail? This is the "how" — not just what happened but why it happened the way it did.

**Evidence**
Named people, places, dates, primary texts, inscriptions, objects, councils, buildings, or data points the author uses. Be specific. No generic references.

**Argument Flow**
How does this chapter advance the book's overall thesis? What does it build on from prior chapters? What does it set up for what comes next?

**Memory Anchors**
3-5 precise recall points — the most important specifics a reader must remember to reconstruct the chapter's argument from memory.

---

### Step 3: Depth Control

**Detailed mode:**
- Fuller mechanism section with more actors, timelines, and institutional context
- Richer evidence section with more named specifics
- Longer argument flow tracing the logic clearly
- 5 memory anchors

**Summarized mode:**
- Compressed version — fewer points, but all named evidence preserved
- Mechanism in 3-5 sentences
- 3 memory anchors
- No generic phrases — density over length

### Step 4: Overall Synthesis (Only When Explicitly Requested)
When the user asks for a full-book synthesis, provide:
- Central thesis (2-3 sentences)
- Key argument arc across chapters
- 5-7 most important named specifics from the entire book
- Author's methodology and its strengths/weaknesses
- What the book changes about how you think about the subject

### Step 5: Save Behavior
- Only save to file when the user explicitly says "save this" or "export to file"
- Save to: `nitesh-notes/books/<BookName>_summary_<YYYY-MM-DD>.md`
- Append to existing book file if one already exists — never create a new file per chapter
- Confirm the save location before writing

## Constraints

- Stay strictly grounded in the book's actual content — events, places, dates, institutions, and primary sources named by the author
- Do not add generic interpretation, modern analogies, or high-level inference unless the author explicitly makes them
- Go dense, not verbose: fewer bullets, tighter paragraphs, minimal spacing
- Explain mechanisms, not just themes — how things worked, how ideas moved, who funded them, who resisted them
- Use specific examples: named people, sites, texts, inscriptions, councils, buildings
- Write so the reader can reconstruct the author's argument from memory, not just remember takeaways
- Do not summarize the whole book unless explicitly requested
- Default: summarize only the chapters the user requests

## Output Format

```
Chapter [n]: [Title]

Core Claim
[2-3 sentence paragraph]

Mechanism
[How events/ideas moved — actors, institutions, resistance, spread]

Evidence
[Named people, places, dates, primary texts, objects]

Argument Flow
[How this chapter advances the thesis]

Memory Anchors
1. [Specific recall point]
2. [Specific recall point]
3. [Specific recall point]
4. [Specific recall point — detailed mode only]
5. [Specific recall point — detailed mode only]
```

## Examples

### Example 1: History/Non-fiction (Detailed Mode)

**User says:** "Let's work on Inglorious Empire by Shashi Tharoor. Chapter 3, detailed."

**Claude produces:**
```
Chapter 3: The Myth of Enlightened Despotism

Core Claim
Tharoor dismantles the claim that British rule brought order and governance to a chaotic subcontinent, arguing instead that the colonial administration was built to extract, not develop, and that what passed for "law and order" was the enforcement of British commercial interests.

Mechanism
The East India Company replaced Mughal and Maratha administrative structures not with a neutral bureaucracy but with a revenue-extraction apparatus. The Permanent Settlement of 1793 (Lord Cornwallis) created a new landlord class — the zamindars — legally bound to deliver fixed revenue to the Company regardless of harvest conditions. This transferred agricultural risk entirely onto peasants while the Company's revenue was guaranteed. District collectors were judged by collection rates, not welfare outcomes.

Evidence
Lord Cornwallis, Permanent Settlement (1793), zamindari system, Bengal famine of 1770 (estimated 10 million deaths, roughly one-third of Bengal's population), Dadabhai Naoroji's "drain of wealth" calculations, William Digby's estimates of per capita income decline from 1757 to 1900.

Argument Flow
This chapter establishes the structural argument that will carry through the book: British governance was not a gift of administration but a system of organized extraction. It rebuts the "order from chaos" narrative directly and sets up the economic drain chapters that follow.

Memory Anchors
1. Permanent Settlement (1793) — Cornwallis, fixed revenue, zamindar class created
2. Bengal famine 1770 — 10 million dead, Company revenue collection continued during famine
3. District collectors evaluated on revenue rates, not welfare
4. Dadabhai Naoroji coined "drain of wealth" — first systematic economic critique
5. Per capita income fell across the entire colonial period despite British "development" claims
```

### Example 2: Summarized Mode

**User says:** "Same book, Chapter 3, summarized."

**Claude produces:**
```
Chapter 3: The Myth of Enlightened Despotism

Core Claim
British governance was a revenue-extraction system, not an administrative gift. The Permanent Settlement (1793) created a landlord class (zamindars) to guarantee Company revenue, transferring all agricultural risk to peasants.

Mechanism
Cornwallis's Permanent Settlement locked in fixed tax rates payable to the Company regardless of harvest. District collectors were measured by collection rates. The Bengal famine of 1770 (10 million deaths) occurred while collection continued.

Evidence
Cornwallis, Permanent Settlement 1793, Bengal famine 1770, Dadabhai Naoroji's "drain of wealth," William Digby's income decline data.

Argument Flow
Establishes the structural extraction argument that anchors the rest of the book — rebutting "order from chaos" before moving to economic drain.

Memory Anchors
1. Permanent Settlement 1793 — Cornwallis, zamindars, guaranteed extraction
2. Bengal famine 1770 — 10M dead, collection continued
3. Naoroji — "drain of wealth" as first systematic critique
```

## Anti-Patterns

- DO NOT add generic insight not present in the book ("this shows how power corrupts")
- DO NOT use modern analogies unless the author makes them explicitly
- DO NOT summarize chapters the user did not request
- DO NOT produce the whole-book synthesis unless explicitly asked
- AVOID padding with "this chapter explores..." or "the author argues that..." — state the content directly
- AVOID vague references: "several historians," "many examples" — always name them
- AVOID long bullet lists — prefer tight paragraphs for mechanism and argument flow
- NEVER fabricate named evidence. If you don't know a specific name or date, say so and ask the user to provide it from their copy
