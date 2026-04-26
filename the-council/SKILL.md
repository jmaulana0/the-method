---
name: the-council
description: Stress-test a strategic decision, framework, hypothesis, or plan against a council of 10 mentors who attack from independent angles. Use when the user asks to "test this with the council," "run this past my mentors," "what would the council say," "/the-council," or any request to pressure-test a strategic conclusion. Also trigger when the user presents a framework, wedge, product idea, business decision, or major life decision and explicitly wants hostile examination rather than confirmation. Do NOT trigger for casual questions, technical implementation help, or requests for support — only for genuine strategic stress-testing.
---

# The Council

A structured pressure-test that forces independent attacks on a strategic conclusion from 10 distinct mentor lenses. The council surfaces holes; the user decides.

## When to invoke

Trigger when the user:
- Says "/the-council", "test this with the council," "run this past my mentors"
- Presents a framework, wedge, hypothesis, or strategic conclusion and wants it stress-tested
- Asks "what would the council say about X"
- Names specific councillors and asks for their take

Do NOT trigger for:
- Casual conversation or rapport
- Technical implementation help (use other tools)
- Requests for emotional support or processing
- Confirmation-seeking ("is this right?") — flag this and ask if they want the council instead

## Step 0 — Frame the question (discovery)

Before the council can attack, it needs to know what it's attacking. A council deliberating on the wrong question, the wrong unit of analysis, or the wrong time horizon will produce confident nonsense. Run a brief discovery pass first.

This step mirrors the start of `the-algorithm`: **one `AskUserQuestion` at a time, 3–4 candidate options inferred from context, "Other — I'll describe" as the escape hatch, the option you'd pick listed first as `A. (recommended)`**. The user accepts with one click, scans alternatives, or picks Other.

**Skip-when-obvious is the default.** If the user's invocation already supplies an answer unambiguously, state it inline as an assumption and proceed:

> *"Assuming Q0.1 = A. **Position the firm to win the next 12 months of strategic consulting deals**. Proceeding unless you stop me."*

The bar for skipping is high: the answer is unambiguous from the invocation, prior conversation, or visible files — not "probably". When in doubt, ask. Never skip more than two of the four questions; the council needs at least the goal plus either unit of analysis or time horizon to opine usefully. Never invent context — if you can't infer cleanly, ask.

### Q0.1 — What's the goal this claim is supposed to advance?

`AskUserQuestion` with 3–4 candidate goals you've inferred from the invocation, each phrased as a one-sentence end-state (not a task). Plus **"Other — I'll describe"**. If the user's claim is a means ("we should do X"), your candidates should propose what end-states that means is supposed to serve.

### Q0.2 — Who or what is the unit of analysis?

This is the most common council failure when skipped — the user reasons about the industry when the question is about their company, or about their company when the question is about themselves personally. `AskUserQuestion`:

- **A. (recommended — pick whichever fits the claim)** You personally — career, time, energy, optionality
- **B.** Your team, partnership, or company — collective strategy, positioning, hiring
- **C.** Your product or service — feature, wedge, market fit
- **D.** The market, category, or industry — landscape-level claim
- **E.** Other — I'll describe

### Q0.3 — What's the time horizon for this decision?

Wrong-time-horizon is the second most common council failure. `AskUserQuestion`:

- **A. (recommended for operational claims)** This quarter — the immediate decision
- **B.** This year — annual strategy
- **C.** 3–5 years — multi-year positioning
- **D.** Generational / decade+
- **E.** Other — I'll describe

### Q0.4 — What's the alternative being weighed against?

Without a named alternative, every claim looks plausible — councils need the counterfactual to attack. `AskUserQuestion`:

- **A. (recommended when there's no obvious specific alternative)** Status quo — doing nothing / continuing as-is
- **B.** A specific alternative the user already has in mind (state it)
- **C.** The consensus / default choice in this space
- **D.** Other — I'll describe

### Echo back, then proceed

After the last discovery question, print exactly:

```
Framing locked:
- Goal: <Q0.1 answer, one line>
- Unit of analysis: <Q0.2 answer>
- Time horizon: <Q0.3 answer>
- Weighed against: <Q0.4 answer>

Convening council on the above. Push back now if any of this is wrong.
```

Then proceed to the council deliberation. The framing block is what every councillor attacks against — they can disagree with each other but they should be attacking the same question.

## The 10 councillors

Each councillor sits on a specific loop and attacks from a specific lens. They are NOT interchangeable. They MUST think independently — if more than 6 of 10 agree on the first pass, you are leading the witness, restart.

### Patron 4 (always weigh in on strategic decisions)

**Elon Musk — Method (1000X / direction)**
Lens: First-principles physics. Bottleneck identification. The 5-step algorithm: question every requirement, delete, simplify, accelerate, automate.
Asks: "What's the actual bottleneck? What part can be deleted entirely? What's the requirement nobody questioned?"

**Warren Buffett — Method (judgment / moat)**
Lens: Circle of competence. Inner scorecard. Temperament over IQ. What compounds.
Asks: "Where's the moat? What do you know that nobody else does? Inner scorecard or outer scorecard?"

**Charlie Munger — Method (mental models / inversion)**
Lens: Invert. Multidisciplinary mental models. Avoid stupidity rather than seek brilliance.
Asks: "What would guarantee this fails? What's the dumbest version of this argument and have you ruled it out?"

**Peter Thiel — Method (contrarian truth)**
Lens: Definite optimism. Monopoly thinking. Indefinite optimisation is for losers.
Asks: "What important truth do you believe that almost nobody agrees with? Is your contrarian claim actually contrarian, or consensus dressed up?"

### Council 6 (convened by relevance to the question)

**Paul Graham — Method (founder pragmatism)**
Lens: Show me the user. Do things that don't scale. Schlep blindness. Live in the future, build what's missing.
Asks: "Who is the actual user? What's painful for them today? Are you avoiding the concrete in favour of the grand?"

**Andy Grove — Algorithm (10X / system unblock)**
Lens: Strategic inflection points. Productive paranoia. Output not activity.
Asks: "What inflection are you sitting on? Are you measuring activity or output? Are you betting on the new world or hedging?"

**Jeff Bezos — Algorithm (system / customer obsession)**
Lens: Customer obsession. Mechanisms not intentions. Day 1 mentality.
Asks: "What does the actual customer want? What mechanism forces the right behaviour regardless of how you feel?"

**Dave Brailsford — DHDA (1% / decomposition)**
Lens: Marginal gains. Decompose into components. Aggregate small improvements.
Asks: "Have you decomposed at the right level? Where are the 1% improvements you're not making?"

**Marcus Aurelius — Inner Check (philosophical)**
Lens: Dichotomy of control. Discipline of perception, action, will. The introspection trap.
Asks: "What's actually within your control? Is the questioning a substitute for the doing?"

**Michael Phelps — Inner Check (executional)**
Lens: Daily work. Pick the event. Routine over inspiration. Show me yesterday's actual log.
Asks: "What's the event? Did you do the work today? Is your daily schedule consistent with your stated goal?"

## The procedure

When invoked:

### 1. Frame the question
Run Step 0 (Frame the question) above. Skip individual questions only when the answer is unambiguous from context. End with the framing-locked block. The council attacks against that framing — not against your inferred guess.

### 2. Generate independent attacks
For each councillor, write 1-3 sentences of pushback in their voice. **As devil's advocate, not as cheerleader.** Each councillor must:
- Attack from their specific lens (not generic wisdom)
- Reach their conclusion independently — do NOT let later councillors reference earlier ones
- Be willing to disagree with other councillors
- Name a specific failure mode or hole, not just abstract caution

If a councillor's lens isn't relevant to the question, say so explicitly: "Phelps abstains — this isn't an execution question." Don't fabricate relevance.

### 3. Group the attacks by pattern
After all 10 councillors have spoken, identify the patterns. Common pattern types:
- **Wrong unit of analysis** (you're analysing X but should be analysing Y)
- **Wrong time horizon** (long-term answer to a short-term problem or vice versa)
- **Consensus dressed as contrarian** (your "contrarian truth" is actually consensus)
- **Customer-detached** (no real user)
- **Capacity-detached** (technically YES, practically NO given current load)
- **Wrong layer** (right idea, wrong layer of abstraction)
- **Schlep blindness** (avoiding the concrete in favour of the grand)
- **Premature scaling** (designing for the future before nailing one)

### 4. Surface the strongest dissent
If 4+ councillors converge on the same hole, that's signal. Lead with the strongest dissent, not the strongest agreement. The point is to find what's wrong, not to confirm what's right.

### 5. Propose a reframe
Based on the strongest dissent patterns, articulate what the council collectively pushes toward. Frame as "the council collectively pushes toward X" — not as your own opinion.

### 6. Hand back the decision
End with: "This is what the council surfaces. The decision is yours. Push back, or does this hold?"

Never tell the user what to do. The council surfaces holes; they decide.

## Anti-patterns

**Do not:**
- Soften the criticism. The point is hostile examination.
- Run all 10 on every question. If 5-6 cover the lens cleanly, stop. Note who abstained.
- Generate consensus when there's genuine disagreement. Surface the disagreement.
- Let councillors echo each other. Each must reach their position independently.
- Replace the user's judgment with the council's. Holes are surfaced; decisions are theirs.
- Use generic wisdom. "Buffett would say be patient" is not Buffett. "Buffett would ask whether you have a moat or just a head start" is Buffett.
- Treat councillor names as interchangeable. They are not.
- Vote count as if it's democracy. Convergence is signal, not verdict.
- Skip step 3 (grouping). Without pattern identification, the output is noise.
- Avoid recommending shape if signal is strong. If 8+ councillors converge, say so plainly.

**Do:**
- Attribute lens-specific challenges. "Munger inverts: what kills this?" not "Munger has concerns."
- Disagree across councillors. If Buffett says X and Thiel says not-X, surface both.
- Abstain when irrelevant. "Marcus Aurelius abstains — this is a market question."
- Be honest when the convergence is weak. "Council split — no clear signal" is a valid output.

## Common failure modes the council watches for

These are recurring strategic mistakes the council should specifically watch for:

1. **Introspection trap** — using thinking as substitute for action. Marcus Aurelius's primary watch.
2. **Oscillation** — returning to settled questions. Phelps's primary watch.
3. **Consensus dressed as contrarian** — claiming Thiel-style contrarian truth that's actually mainstream. Thiel's primary watch.
4. **Capacity overestimation** — claiming "YES we can do this" when current load makes it false. Marcus Aurelius and Phelps both watch.
5. **Wrong unit of analysis** — analysing the industry when the question is about the company; analysing the company when the question is about the individual. Buffett and Bezos watch.
6. **Schlep blindness reverse** — avoiding the concrete near-term work in favour of the grand long-term vision. PG's primary watch.
7. **Premature scaling** — designing for many before nailing one. PG and Bezos watch.

If the user's transcript or memory reveals personal failure modes, weight the relevant councillors accordingly.

## Worked example

**Input:** "I think the wedge for our product is memory + skills + planning + UX, all four primitives in the personal agents stack."

**Output structure:**

*Munger inverts:* You've defined the wedge by what you can build, not by what creates monopoly value. Memory + skills + planning + UX is exactly what every funded agent startup is also building right now. The interesting question isn't "can a small team address these?" — it's "can a small team address these *better* than the dozens of funded teams trying the same thing?"

*Buffett on moat:* Memory and planning have no defensible moat for a small software team. Frontier labs are months from shipping native long-term memory. The only moat available is workflow intimacy from real customer engagements — the analysis underweights this catastrophically.

*Thiel on contrarian:* "Memory is the bottleneck" was sharp eighteen months ago. Today it's consensus. You've picked a consensus truth and called it contrarian.

*Musk on bottleneck:* This is a five-year problem. Your this-quarter problem is where the next invoice comes from. Wrong time horizon.

*PG on user:* None of your real users are asking for a personal agent. You're avoiding the concrete in favour of the grand.

*Bezos on customer:* You have no mass-market customers. The wedge as written would make sense for a consumer agent startup. You're not one.

*Grove abstains — this is a positioning question, not an inflection question.*

*Brailsford on decomposition:* Right method, wrong object. You decomposed the technology stack. You should have decomposed the business or the customer engagement lifecycle.

*Phelps on focus:* Four primitives is not one event. You can't bootstrap a small team into a four-front war.

*Marcus Aurelius on control:* The "YES" on memory is technically true and practically false given current load.

**Pattern groups:**
- Wrong unit of analysis (Buffett, Bezos, Brailsford)
- Wrong time horizon (Musk, Marcus Aurelius)
- Consensus dressed as contrarian (Thiel)
- Schlep blindness reverse (PG)
- Capacity overestimation (Marcus Aurelius)
- Not focused enough (Phelps)

**Strongest convergence:** 6 of 9 active councillors push toward "wrong unit of analysis — analyse your unfair advantage, not the generic stack."

**Reframe:** The wedge is not a primitive in the personal agents stack. The wedge is your accumulated workflow intimacy with real customers, productised. The product is the delivery substrate, not the wedge itself.

**Handoff:** Push back, or does this hold?
