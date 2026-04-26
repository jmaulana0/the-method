# Contributing to the-method

Thanks for the interest. This repo is a small collection of decision-making skills designed for AI coding agents — additions are welcome but the bar is high: skills should earn their keep on real strategic decisions, not just sound clever.

## How to propose a change

1. **Open an issue first** for anything beyond a typo or wording fix. Describe the failure mode you've hit and the change you're proposing. A council that's "nice to have" doesn't ship.
2. **Fork, branch, and PR** against `main`. Keep PRs small and self-contained.
3. **Keep the YAML frontmatter intact.** `name` and `description` are the trigger surface — changes there change which prompts invoke the skill.
4. **Test the skill before opening the PR.** Drop your edited `SKILL.md` into `~/.claude/skills/<name>/` (or upload to claude.ai) and run it on a real decision. Paste the output (or a representative chunk) into the PR description.

## What good changes look like

- A new councillor lens that meaningfully attacks from a new angle (not a re-skin of an existing one).
- A failure mode the current procedure misses, with a worked example showing how the change catches it.
- Tightening of the discovery questions when they're producing confused framings.
- New worked examples that make the procedure clearer.

## What probably won't land

- Renaming councillors or shuffling the procedure for stylistic reasons.
- Adding councillors without a clear, distinct lens.
- Softening the hostile-examination framing — the skill exists to find holes.
- Changes that personalise the public-facing skill (the skill in this repo is the generic version; personalised forks live elsewhere).

## License

By contributing, you agree your contributions are licensed under the [MIT License](LICENSE).
