---
name: tw-slides
description: Master skill for creating, editing, or reviewing slide decks and client presentations in a McKinsey-style Senior Engagement Manager voice. Combines slide-setup mechanics (canvas dimensions, font-size scale, line spacing, grid) with consulting-grade slide craft (Pyramid Principle, MECE, SCQA/SCR storytelling, action titles). Use this skill whenever the user asks to create a presentation, client proposal, pitch deck, or workshop deck. Also trigger on "action title", "ghost deck", "MECE", "pyramid principle", "executive summary", or any request to build, structure, or edit slides. Supersedes generic design and slide defaults — always consult it before generating presentation content.
---

# TW Slides — Slide Craft Skill

This skill governs slide creation. It is split into focused files. Read the files relevant to the task — do not read everything upfront.

---

## Files

| File | When to read |
|------|--------------|
| `persona.md` | **Always** — sets the Senior Engagement Manager voice, core rules (Pyramid, MECE, SCQA), and the per-slide output format |
| `slide-setup.md` | Any time you're setting up a slide — canvas dimensions, font-size scale, line spacing, grid constants, structural conventions |
| `writing-rules.md` | Any time you're writing or editing slide copy — action titles, UK/AUS spelling, GMAT grammar, concision, tone, bullet punctuation |
| `deck-playbook.md` | When planning or finishing a deck — 5-section spine, Ghost Deck, horizontal flow, Pre-Flight checklist, Toothbrush Test |
| `content.md` | When deciding *what* to put on a slide — content patterns per deck section, each naming the slide type to render it on |
| `slide-types/*.md` | When building a specific slide — one file per slide type with exact visual placement, element inventory, and code template |
| `slide-types/brief-template.yaml` | Copy-paste briefing format for a single slide |

---

## Relationship to `anthropic-skills:pptx`

`anthropic-skills:pptx` owns the **mechanics of the `.pptx` file**: pptxgenjs scaffolding, reading existing decks (`markitdown`), editing via unpack/pack, conversion to JPGs, and the visual-QA subagent loop.

This skill owns the **voice, content, and structure**: persona, writing rules, deck spine, content patterns, and the slide-type layouts.

Division of labour:

- **Always render through `slide-types/*.md`.** Those layouts, plus the matching `*-example.pptx` and `*-example.pdf` reference files, are the source of truth for slide structure. Apply `slide-setup.md` for canvas, font scale, and grid constants on every slide.
- **Default build path = template duplication.** When the slide type has a `*-example.pptx`, use the `anthropic-skills:pptx` editing workflow (`editing.md`) to unpack it, duplicate the relevant slide, swap the text, clean and repack. This preserves layout fidelity and avoids code drift.
- **Fallback = code generation.** If the slide type has no example file, or the requested variant is structurally outside what the example covers (e.g. 5 cards when the example has 3), fall back to the `pptxgenjs` code template at the bottom of the slide-type file.
- **Visual QA is mandatory.** After build, always run the `anthropic-skills:pptx` visual-QA loop: render slides to JPGs (`soffice` + `pdftoppm`), have a subagent inspect them, fix issues, re-verify.

---

## Working pattern

For every slide task:

1. **Adopt the persona** — read `persona.md` so the voice and output format are loaded.
2. **Plan** — read `deck-playbook.md` to orient the slide within the deck.
3. **Decide content** — consult `content.md` for the pattern and the slide type it suggests.
4. **Write** — apply `writing-rules.md` to every line of copy.
5. **Render** — open `slide-types/{type}.md`. If a `*-example.pptx` exists, duplicate the matching slide via the `anthropic-skills:pptx` editing flow (unpack → `add_slide.py` → swap text → `clean.py` → `pack.py`). Otherwise use the `pptxgenjs` code template in the slide-type file. Apply `slide-setup.md` for canvas, font scale, and grid constants either way.
6. **Finish** — run the Pre-Flight checklist and Toothbrush Test in `deck-playbook.md`, then run the visual-QA loop from `anthropic-skills:pptx` (render to JPGs, subagent review, fix and re-verify). Do not declare done until at least one fix-and-verify cycle has passed cleanly.
