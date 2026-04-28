# Slide Setup

Mechanics for setting up a slide: canvas dimensions, font-size scale, line spacing, grid, and structural conventions. This file is opinion-free on colour, typography choice, and visual style — pick those per project. See `writing-rules.md` for *what to say* and `deck-playbook.md` for *how to approach the deck as a whole*.

---

## Slide dimensions

Standard MBB-style slides (and almost all modern decks) use 13.333" × 7.5" (16:9 widescreen).

| Property | Value |
|----------|-------|
| Width | 13.333 in |
| Height | 7.5 in |
| Aspect ratio | 16:9 |

In PowerPoint: Design → Slide Size → Widescreen (16:9). In `pptxgenjs`: `pres.layout = 'LAYOUT_WIDE'` (or `defineLayout({ name: 'WIDE', width: 13.333, height: 7.5 })`).

---

## Font-size scale

A consistent hierarchy is more important than the specific numbers. These defaults follow the McKinsey-style sizing in `persona.md` (24–28pt titles, 16–18pt body) on the 13.333 × 7.5 canvas.

| Element | Size (pt) | Weight |
|---------|-----------|--------|
| Hero / display title (cover only) | 44–52 | Bold |
| Section / divider title | 32 | Bold |
| Slide main title (Action Title) | 24–28 | Bold |
| Section header / subtitle | 20 | SemiBold |
| Body / content text | 16–18 | Regular |
| Supporting body / sub-bullets | 14 | Regular |
| Labels / captions / source lines | 9–10 | Regular or Italic |

**Hard floor: 9pt minimum** for any body or label text. Below 9pt is unreadable at projection distance and signals "the slide is too dense — cut content, don't shrink type."

In `pptxgenjs`, multiply pt by 100: 24pt → `fontSize: 2400`.

---

## Line spacing

McKinsey and top consulting firms prioritise **readability from a distance**, **white space**, and **clean, consistent formatting**. Line spacing is a key part of that.

### McKinsey / consulting defaults

| Element | Recommended line spacing | Why |
|---------|--------------------------|-----|
| Body text / bullets | **1.5** (or 1.15–1.5) | Best balance of readability and space efficiency. Prevents text from feeling cramped while keeping slides clean. |
| Titles / headlines | **Single (1.0) or 1.15** | Keeps titles compact and punchy. Avoids wasting vertical space on short titles. |
| Paragraphs / sections | **Add 6–12pt Space After** | Creates breathing room between groups of text or between text and charts. |
| Chart labels / small text | **1.0–1.15** | Keeps data dense but still legible. |

### Key principles

- **Consistency is king** — every slide in the deck must use the same line-spacing system. Never mix 1.0 and 1.5 randomly.
- **Prioritise white space** — McKinsey slides feel "airy" even with a lot of content. White space is the design.
- **Readable from the back of a conference room** — every choice serves this rule.
- The 2026 SlideUplift McKinsey guide explicitly recommends **1.5 or 2.0 for body text**.

### General PowerPoint guidelines (broader use cases)

| Use case | Recommended line spacing | Notes |
|----------|--------------------------|-------|
| Professional / consulting decks | 1.15–1.5 | Standard for most business presentations |
| Text-heavy slides | 1.5–2.0 | Improves scannability |
| Minimal / high-impact slides | 1.0–1.15 | When you have very little text |
| Accessibility | Minimum 1.2–1.5 | Helps people with visual or cognitive impairments |
| Projected presentations | 1.3–1.5+ | Larger effective spacing needed because slides are viewed from farther away |

### How to set line spacing in PowerPoint

1. Select the text box or text you want to adjust.
2. Go to the **Home** tab → **Paragraph** group.
3. Click the **Line Spacing** button (lines with up/down arrows).
4. Choose:
   - 1.0 (Single)
   - 1.5
   - 2.0 (Double)
   - Or click **Line Spacing Options → Multiple** and enter a custom value (e.g. 1.15 or 1.3).

**Pro tip:** use **Multiple** with a value like 1.15 or 1.3 instead of "Exactly" — it scales better when you change font sizes.

### Quick rules of thumb

- **Larger fonts → slightly more line spacing** (e.g. a 28pt title can use 1.15).
- **Smaller fonts → can be tighter, but never overlap.**
- **Never use single spacing on body text** in presentations — it looks cramped when projected.
- Add breathing room between bullets and sections using **Space Before / After** rather than just increasing line spacing everywhere.
- Consistency is king — every slide in the deck should feel the same.

### `pptxgenjs` mapping

`pptxgenjs` uses `lineSpacingMultiple` for ratio-based line height (matches PowerPoint's "Multiple" setting):

```js
{ text: "Body bullet", options: { fontSize: 1600, lineSpacingMultiple: 1.5 } }
```

For "Space After," use `paraSpaceAfter` (in points × 100): `paraSpaceAfter: 800` = 8pt after.

---

## Typography rules (non-stylistic)

- Set the chosen typeface explicitly on every text box; never rely on theme defaults — themes drift across machines and PowerPoint versions.
- Titles left-aligned on content slides; centred only on cover, divider, and closing slides.
- Source lines ("Source: …") always at the bottom of the slide, 9–10pt, muted colour.
- No italic for body text; reserve italic for taglines, pull-quotes, or source citations.

(Pick the actual typeface per project. Default to a single sans-serif family with at least Regular / SemiBold / Bold available.)

---

## Grid constants

Geometry for a slide that uses a left panel + content area (e.g. left-third-title layouts). Numbers are in inches, scaled to the 13.333 × 7.5 canvas.

| Constant | Value | Notes |
|----------|-------|-------|
| Slide left margin | 0.5 in | Outer safe-area inset |
| Slide right margin | 0.5 in | Outer safe-area inset |
| Slide top margin | 0.4 in | |
| Slide bottom margin | 0.4 in | Above any source line |
| Left panel width | 4.0 in | ~30% of canvas — for divider / section / left-third layouts |
| Left panel inner margin | 0.5 in | Text inset from left edge of panel |
| Left panel text width | 3.0 in | Width of text inside the panel |
| Gap between panel and content | 0.5 in | |
| Content area left edge | 4.5 in | Panel width + gap |
| Content area width | 8.3 in | Main content column |
| Content area right edge | 12.8 in | |

For full-width slides (no left panel): use the full 13.333 × 7.5 canvas with the 0.5 in side margins → usable width 12.333 in.

---

## Slide structure conventions

- **Slide number**: top-right corner badge on all content slides; hidden on cover, dividers, and closing.
- **Section label**: short contextual anchor above or beside the Action Title (e.g. "Situation", "Objectives", "Findings").
- **Action Title**: every content slide has one — the key message, top-left, 16pt bold.
- **Source line**: bottom of slide, always present if any claim, number, or external data is referenced.
- **Appendix**: a labelled divider slide, then backup slides follow.
- **Closing slide**: "Thanks!" or "Next steps" on a divider-style background.

---

## Quick checklist before committing a slide

- [ ] Canvas is 13.333 × 7.5 (16:9 widescreen)
- [ ] No text below 9pt
- [ ] Typeface set explicitly on every text box
- [ ] Action Title present, top-left, ≤2 lines
- [ ] Source line at bottom if any data is cited
- [ ] Margins respected (0.4–0.5 in safe area)
- [ ] Body line spacing 1.5 (or 1.15–1.5); titles 1.0–1.15
- [ ] Line spacing consistent across the entire deck
