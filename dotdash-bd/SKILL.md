---
name: dotdash-bd
description: Build an MBB-style dot-dash storyline for a consulting business development (BD) pitch deck. Use this skill whenever the user is preparing a pitch, proposal, or BD deck for a prospective client — including phrases like "BD deck", "pitch deck", "proposal storyline", "draft a pitch for [company]", "storyline for [prospect]", "help me pitch [X]", or "dot-dash this for [client]". Also trigger when the user shares a transcript, brief, or call notes from a prospect and asks how to structure a response. Use this skill even when the user only says something like "let's storyline this" or "make a pitch outline" — if the context is winning new consulting work, this skill applies. Do NOT use this skill for problem-solving / case-style decks (a separate non-BD storyline skill exists for that). The skill produces a strict dot-dash text outline only — no slide building.
---

# Dotdash BD Storyline

A skill for building MBB-style dot-dash storylines for consulting business development pitches. Produces a strict, text-only dot-dash outline that the user takes into slides themselves.

## Core principles (non-negotiable)

- **Conclusion first, always.** Every section, every dot, every dash leads with the takeaway, then supports it. Never lead with background or process.
- **Action titles, not topics.** Each dot is a full-sentence insight or conclusion. "Supply chain analysis" ❌ → "Supply chain optimisation can reduce costs by 20% within 18 months" ✓.
- **Most-important-first within every section.** Order dashes under each dot from most to least important. Never bury the key evidence at the bottom.
- **Horizontal flow test.** Reading only the dots in sequence must tell the complete story. If it doesn't, the dots are wrong.
- **Questions are fine in the skeleton, sparing in the final deck.** The dot-dash is a text-format skeleton built before the deck to pressure-test framing and clarity. Questions can appear in the skeleton as thinking tools. In the final deck, one or two questions are fine — but the bulk of the product should be statements and conclusions, not open questions.
- **One page if possible.** The whole storyline should fit on a single page of text before any slides exist. This is a feature, not a constraint — if it doesn't fit on one page, the framing isn't tight enough yet.

## Writing standards

Every dot and dash should pass the bar of good consulting writing:

- Don't mumble. Every dot is a clear conclusion, not a hedge.
- Short words, short sentences. "Use" not "utilise". "Now" not "currently".
- Active voice, concrete verbs. "We cut costs 20%" not "costs were reduced".
- Cut adjectives and adverbs that don't earn their place. "Significant", "robust", "leverage" are usually padding.
- One idea per dot. If a dot has an "and" linking two distinct insights, split it.

But override prose-writing rules on length: the dot-dash is not prose. Each dot is a single sentence. Each dash is a single line — a fact, a number, an exhibit reference. No paragraphs. No throat-clearing. The whole point is that the user can scan it in 30 seconds.

## When this skill triggers

Run the full workflow below. Do not skip the interview phase, even if the user seems to be in a hurry — the cheapest place to fix a wrong storyline is before any slides exist.

## Phase 1: Context gathering (before anything else)

Pull in as much context as possible about the prospect before drafting. Be proactive — fetch what you can, then ask the user for what you can't reach.

### Auto-fetch (do this without asking)

If the user mentions a company name or URL, immediately:

- `web_fetch` the company website (about page, services page, leadership page)
- `web_search` for recent news about the company (last 12 months)
- `web_search` for analyst coverage / industry reports if the sector is consulting-relevant
- If the company is publicly listed, `web_search` for the most recent annual report or investor presentation, then `web_fetch` it

Do all of the above in parallel where possible. Report back briefly on what was found before asking for the rest.

### Ask the user to provide

Then prompt the user for the private context the skill can't reach:

- Call/meeting transcripts with the prospect (paste or upload)
- Internal notes on the prospect (Obsidian, Notion, Google Docs)
- Any company brief or RFP they've shared
- Prior email exchanges if relevant
- Specific people the user has spoken to and what they told them

Do not proceed to Phase 2 until the user has either provided this context or explicitly said "go with what you have."

## Phase 2: Strategic framing (three decisions)

Before drafting, lock in three framing choices with the user. Ask them as discrete questions — do not assume.

### Decision 1: Opportunity or Problem positioning

Ask whether the storyline should be framed as:

- **Opportunity** — aspirational, confident. "You could be doing X — here's how we get you there." Default for cold/warm outreach where the prospect hasn't yet admitted pain.
- **Problem** — urgent, direct. "Something is broken and getting worse — here's how to fix it." Use only when the prospect has explicitly framed their own situation as urgent or broken.

Do not default. Always ask. Phrase it exactly as "opportunity or problem framing?" — these are the preferred terms (not "springboard / burning platform").

### Decision 2: BD stage

Ask which stage the deck is for, because this changes which sections to include:

- **Early BD** — first proper pitch. Sections: Context → Hypothesised problems → Hypothesised answer → Why us (team) → Why us (past work).
- **Mid BD** — they've shown interest, want more detail. Add: Timeline.
- **Late BD** — close to signing. Add: Workplan + Commercials.

Timeline, workplan, and commercials are always optional — prompt the user about each one separately if relevant.

### Decision 3: Desired action

Ask: "What do you want the prospect to do after reading this deck?" The answer shapes the resolution. Common answers: book a paid discovery sprint, sign an SOW, agree to a pilot, introduce to a decision-maker, share more data.

## Phase 3: Draft the dot-dash

### Canonical BD structure

Use this section sequence. Each section gets a labelled header in the output. Every dot is an action title (full-sentence conclusion). Every dash is supporting evidence, ordered most-important-first.

```
—— SO WHAT ——
[One-line summary of the entire pitch. The single sentence you'd say in a lift.]

—— CONTEXT ——
- [Action title summarising the prospect's current situation]
  - [Most important supporting fact]
  - [Next supporting fact]
- [Action title for the relevant market/industry shift]
  - [Supporting evidence]

—— HYPOTHESISED PROBLEMS ——
- [Action title naming the most important problem we've inferred]
  - [Why we believe this — evidence from transcripts, website, reports]
  - [Cost of inaction or size of the gap]
- [Second hypothesised problem]
  - [Supporting evidence]
[2-4 problems total. MECE. Most material first.]

—— HYPOTHESISED ANSWER ——
- [Action title stating our high-level recommended approach]
  - [What it looks like in practice]
  - [Why this approach beats alternatives]
- [Action title for the expected outcome / ROI]
  - [Quantified where possible]

—— WHY US (TEAM) ——
- [Action title on the team's distinctive fit for this problem]
  - [Reference to existing creds slides for the named team leads]
  - [Specific elements of background relevant to this prospect — e.g., MBB rigour, operator scale, network, embedded delivery model]

—— WHY US (PAST WORK) ——
- [Action title on the most relevant past case]
  - [What we did, what changed, quantified result if possible]
- [Second most relevant case]
  - [Same pattern]
[Ask the user to describe 3-5 past cases. Pick the 2-3 that best match this prospect's industry, problem type, or technical scope.]

—— [OPTIONAL] TIMELINE ——
- [Action title on overall delivery shape]
  - [Phase 1: weeks 1-X, what happens]
  - [Phase 2: weeks X-Y, what happens]

—— [OPTIONAL] WORKPLAN ——
- [Action title on how the work breaks down]
  - [Workstream 1, owner, deliverable]
  - [Workstream 2, owner, deliverable]

—— [OPTIONAL] COMMERCIALS ——
- [Action title on the commercial proposition]
  - [Pricing structure]
  - [ROI guarantee terms, if applicable]
```

### Past work elicitation

For the "Why us (past work)" section, do not invent cases. Post a direct request in chat asking the user for the case material — phrased something like:

> Before I fill in the Why us (past work) section, can you give me 3–5 past engagements to draw from? For each one, just a line or two on: industry, problem, what was done, outcome. I'll pick the 2–3 most relevant for this prospect and write the dots/dashes from those.

Wait for the user's response before completing that section. If they say "use what you've got" or "skip past work this time," respect that — leave a placeholder in the dot-dash and move on.

## Phase 4: Self-check before delivering

Before showing the user the draft, run these checks silently:

- **Horizontal flow** — read only the dots top to bottom. Does it tell the full story without the dashes? If not, fix the dots.
- **Action titles** — is every dot a full sentence stating a conclusion? No topic phrases like "Market overview" allowed.
- **Most-important-first** — within every section, is the strongest dot/dash on top?
- **MECE** — do the dots within each section overlap? Are any obvious points missing?
- **Questions** — strip questions that don't earn their place. One or two in the final deck is fine; more than that means the framing is weak.
- **One page** — is the whole thing readable on one page? If not, cut.
- **Conclusion first at every level** — the SO WHAT line, every section's first dot, every dot's first dash.

If any check fails, fix it before showing the user.

## Phase 5: Deliver

Output the dot-dash exactly in the format above. Plain text. No slide suggestions, no design notes, no "next steps" preamble. The user takes it into slides themselves.

After delivering, offer one round of refinement: "Want me to adjust the framing, swap in different cases, or sharpen any of the action titles?"

## What this skill does NOT do

- Build slides (use a separate slide-building skill)
- Problem-solving / hypothesis-driven case decks (different structure, separate skill)
- Invent past work, results, or numbers — always ground in what the user provides or what's verifiable

## Quick reference: BD vs problem-solving storyline

| | BD pitch | Problem-solving |
|---|---|---|
| **Goal** | Win the work | Prove the answer |
| **Opener** | Their context | Situation/Complication |
| **Core** | Hypothesised problems → answer | MECE arguments + evidence |
| **Closer** | Why us + past work | Recommendation + next steps |
| **Tone** | Confident, sales-aware | Rigorous, analytical |

This skill is for the left column only.
