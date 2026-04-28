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

Specific values, no ranges. Pick from the table — never split the difference.

| Element | Size (pt) | Weight |
|---------|-----------|--------|
| Hero / display title (cover only) | 48 | Bold |
| Section / divider title | 32 | Bold |
| Slide main title (Action Title) | 28 | Bold |
| Section header / subtitle | 20 | SemiBold |
| Body / content text | 16 | Regular |
| Supporting body / sub-bullets | 14 | Regular |
| Labels / captions / source lines | 10 | Regular or Italic |

**Hard floor: 10pt.** No text on any slide goes below 10pt. If content won't fit at 10pt+, cut content; don't shrink type.

### Per-slide font-size limiter

The table above is the *deck-wide* scale, not a menu to draw from on every slide. **Use at most 3 distinct font sizes on a single slide** (4 only if a source / footnote line is also needed). Bouncing between 28 → 14 → 10 → 13 → 11 → 10 → 9 makes the slide look noisy and amateurish; sticking to a small set reads cleanly.

Typical 3-size combinations:

| Slide type | Sizes used |
|------------|------------|
| Standard content slide | Action Title 28 / Body 16 / Source 10 |
| Content slide with subtitle / lead | Action Title 28 / Subtitle 20 / Body 16 (+ Source 10) |
| Card or panel slide | Action Title 28 / Card title 16 / Sub-bullets 14 (+ Source 10) |
| Cover slide | Hero 48 / Subtitle 20 |
| Section divider | Section title 32 / Subtitle 20 |

Pick a combination per slide and use *only* those sizes. If a slide genuinely needs a fifth size, it's a sign the slide is doing too much — split it.

In `pptxgenjs`, multiply pt by 100: 28pt → `fontSize: 2800`.

---

## Line spacing

McKinsey and top consulting firms prioritise **readability from a distance**, **white space**, and **clean, consistent formatting**. Line spacing is a key part of that.

### Defaults — specific values, no ranges

| Element | Line spacing | Why |
|---------|--------------|-----|
| Headers / titles / Action Titles | **1.0 (single)** | Keeps titles compact and punchy. No wasted vertical space on short titles. |
| Top-level body bullets (slide-level) | **1.5** | McKinsey 2026 default — readable from the back of the room with airy white space. |
| Sub-bullets / body text **inside sub-components** (cards, callouts, panels) | **1.15–1.25** | Tighter inside boxed elements; preserves the breathing room around the sub-component itself. The one place a small range is allowed: tune within 1.15–1.25 to fit the available space on the slide. |
| Chart labels / footnotes / source lines | **1.0** | Dense but legible at small sizes. |
| Space After between paragraphs / sections | **12pt** | Creates a clear break between groups of text or between text and charts. Use Space After, not blank lines. |

**Pick one value per element type and apply it to every slide.** Never mix 1.0 and 1.5 on the same role within a deck — that's the inconsistency McKinsey reviewers flag first.

### Key principles

- **Consistency is king** — every slide in the deck must use the same line-spacing system. Never mix 1.0 and 1.5 randomly.
- **Prioritise white space** — McKinsey slides feel "airy" even with a lot of content. White space is the design.
- **Readable from the back of a conference room** — every choice serves this rule.
- The 2026 SlideUplift McKinsey guide explicitly recommends **1.5 or 2.0 for body text**.

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

- **Titles / headers → 1.0.** Compact and punchy.
- **Top-level body bullets → 1.5.** Never single-space body text in presentations; it looks cramped when projected.
- **Sub-component sub-bullets → 1.15–1.25.** Tighter inside cards, callouts, panels; flex within this range based on how much space the slide has.
- **Between blocks → 12pt Space After**, not extra blank lines or stretched line spacing.
- **Consistency is king** — every slide in the deck uses the same values for the same role.

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
- Source lines ("Source: …") always at the bottom of the slide, 10pt, muted colour.
- No italic for body text; reserve italic for taglines, pull-quotes, or source citations.

(Pick the actual typeface per project. Default to a single sans-serif family with at least Regular / SemiBold / Bold available.)

---

## Column grid

Use one of two column systems on every content slide. Specific widths, no improvising. The grid leaves room to layer diagrams and images alongside text without crowding.

### Shared constants

| Constant | Value |
|----------|-------|
| Slide left margin | 0.5 in |
| Slide right margin | 0.5 in |
| Slide top margin | 0.4 in |
| Slide bottom margin | 0.4 in (above source line) |
| Column gutter | 0.333 in |
| Usable content width | 12.333 in |

### Thirds system — column widths: 1/3, 2/3, full

| Layout | Left col | Gutter | Right col |
|--------|---------:|-------:|----------:|
| Full | — | — | 12.333 |
| 1/3 left + 2/3 right | 4.0 | 0.333 | 8.0 |
| 2/3 left + 1/3 right | 8.0 | 0.333 | 4.0 |

Use the thirds system when one side carries the dominant message (text or visual) and the other side is supporting.

### Quarters system — column widths: 1/4, 1/2, 3/4, full

| Layout | Left col | Gutter | Centre col | Gutter | Right col |
|--------|---------:|-------:|-----------:|-------:|----------:|
| Full | — | — | — | — | 12.333 |
| 1/2 left + 1/2 right | 6.0 | 0.333 | — | — | 6.0 |
| 1/4 left + 3/4 right | 3.0 | 0.333 | — | — | 9.0 |
| 3/4 left + 1/4 right | 9.0 | 0.333 | — | — | 3.0 |
| 1/4 + 1/2 + 1/4 (rare, 3-col) | 3.0 | 0.167 | 6.0 | 0.167 | 3.0 |

Use the quarters system for symmetric layouts (1/2 + 1/2), narrow rails (1/4 + 3/4), or framed centre content (1/4 + 1/2 + 1/4).

### Vertical zones

| Zone | y-position | Height | Notes |
|------|-----------:|-------:|-------|
| Action Title band | 0.4 | 0.8 | Top of slide; 28pt bold |
| Sub-title / lead band | 1.2 | 0.4 | Optional; 20pt SemiBold |
| Content body | 1.7 | 5.0 | Where columns live |
| Source line | 6.9 | 0.2 | 10pt at bottom |

### Why two grid systems

- **Thirds (1/3 + 2/3)** — the workhorse for content slides. Asymmetry signals which side is leading.
- **Quarters (1/4, 1/2, 3/4, full)** — when you need symmetry, narrower rails for sidebars, or a centred showcase for a diagram or image.

Either way, the gutter is always 0.333 in (or 0.167 in in the rare 3-column layout). Pick a system per slide and stay in it.

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
- [ ] No text below 10pt
- [ ] At most 3 distinct font sizes on the slide (4 only if a source / footnote line is included)
- [ ] Typeface set explicitly on every text box
- [ ] Action Title present, top-left, ≤2 lines
- [ ] Source line at bottom if any data is cited
- [ ] Margins respected (0.5 in left/right, 0.4 in top/bottom)
- [ ] Headers / titles at 1.0; body bullets at 1.5; sub-component sub-bullets 1.15–1.25 (flex per slide)
- [ ] Space After 12pt between blocks
- [ ] Em dashes minimized; none in speaker notes
- [ ] Line spacing consistent across the entire deck
