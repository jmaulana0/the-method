# the-method

> A small collection of decision-making skills for AI coding agents.

The skills here force the agent (and you) through structured thinking before acting — questioning the requirement, attacking the conclusion from independent angles, surfacing holes. Designed for [Claude Code](https://claude.com/claude-code) and [claude.ai](https://claude.ai), but the markdown ports cleanly to any agent that can load custom instructions.

Sister project: **[the-algorithm](https://github.com/jmaulana0/the-algorithm)** — Elon Musk's five-step method as an interactive skill. The two share a common discovery vocabulary (goal, unit of analysis, time horizon, alternative).

## Skills

| Skill | What it does |
|---|---|
| **[the-council](./the-council/)** | Stress-tests a strategic decision against 10 independent mentor lenses (Musk, Buffett, Munger, Thiel, Graham, Grove, Bezos, Brailsford, Aurelius, Phelps). Surfaces holes; you decide. |

## Install

### Claude Code

```bash
git clone https://github.com/jmaulana0/the-method.git
cp -r the-method/the-council ~/.claude/skills/
```

Claude Code will pick the skill up automatically on next session start. Invoke explicitly with `/the-council` or implicitly by saying things like *"test this with the council"* or *"what would the council say about X"*.

### claude.ai

Settings → Customize → Skills → **Add skill** → **Upload a skill** → select `the-council/SKILL.md`.

### Other agents (Cursor, Windsurf, Cline, Codex, etc.)

Copy the body of [`the-council/SKILL.md`](./the-council/SKILL.md) (everything after the YAML frontmatter) into your agent's custom instructions or rules file:

- **Cursor** → `.cursorrules`
- **Windsurf** → `.windsurfrules`
- **Cline** → `.clinerules`
- **Codex** → `AGENTS.md`
- **Anything else** → system prompt

## When to use it

Use the council for **strategic** decisions that benefit from hostile examination — wedge hypotheses, positioning calls, market reads, major life decisions, framework critiques. Skip it for technical implementation, casual questions, or emotional support.

Pair with **the-algorithm** for execution decisions: the-algorithm asks *"what's the goal, gap, and primitive on the critical path?"*; the-council asks *"is the goal even the right goal?"*

## Credit

Mentor lenses distilled from public talks, books, and interviews — Musk (Starbase tours), Buffett (Berkshire letters), Munger (*Poor Charlie's Almanack*), Thiel (*Zero to One*), Graham (essays), Grove (*Only the Paranoid Survive*), Bezos (shareholder letters), Brailsford (Sky cycling interviews), Aurelius (*Meditations*), Phelps (*Beneath the Surface*).

## License

[MIT](LICENSE)
