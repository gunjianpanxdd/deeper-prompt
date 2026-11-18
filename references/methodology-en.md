# Being Ambitious with AI — Full Methodology (English)

> Source: Felix Rieseberg (Engineering Manager at Anthropic; led engineering for
> Claude.ai, Cowork, and Claude Code Desktop; co-maintainer of Electron), "How to be
> more ambitious: A tutorial for humans with models", felixrieseberg.com,
> published 2026-10-13. This file is an operational digest of that methodology,
> referenced by the skill workflow; the methodology belongs to the original author.

## 1. Background

Most people use AI to answer trivia and soften emails. Model capabilities advance
unevenly — "stunning in some directions, deficient in others" (Terence Tao). The
industry slogan is "be more ambitious with AI", but nobody says how. This digest
turns the slogan into concrete steps.

**Hard prerequisite**: the model needs a computer on which it can install software,
plus access to relevant data (via MCP connectors or other means). Without raw-data
and tool access, depth and range both cap out at half strength.

## 2. The Four Ambitions

| Type | Definition | Treatment |
|---|---|---|
| Speed | Same work in less time | Universally understood; skipped |
| Altitude | Raise abstraction: ask for the outcome, not the task | Section 3 |
| Depth | Think like a field-leading expert: raw data, tools, underlying problems | Section 4 (the most valuable part) |
| Range | Borrow methods from fields the task doesn't seem to need | Section 5 |

## 3. Altitude

**Ask: what do you really want to happen once this task is done? What is the goal
behind the goal?**

- Felix used to ask Claude to fix crashes one by one; then he gave it the goal
  "keep the app crash-free", plus crash reports, a version↔commit mapping, and
  Windows/macOS/Linux machines so it could independently reproduce and verify fixes.
- The quarterly business review (QBR) ladder, low to high:
  1. Don't just update template numbers — hand over as much data as possible:
     "tell me what changed this quarter, why, and what we should do about it."
  2. "Work out which three decisions are most urgent, with for/against arguments."
  3. "The review exists so leadership catches problems early and moves money and
     people to the right places. Design a better way to do that than a quarterly
     deck, show from our own history that it would have caught things sooner, and
     run it beside the current one for a quarter."
- **Fit test**: altitude works best when the work leads to meetings and follow-up
  decisions; it works poorly for pure creative work — reach for depth or range there.
- Altitude is where durable human-out-of-the-loop workflows come from.

## 4. Depth — the most valuable part

Core observation: **when prompted to act like a professional, models often switch
vocabulary without switching methods.** A model asked to act as a data scientist
happily answers with Markdown tables; a real data scientist touches databases and
statistical models.

Five tactics (running example: "our users are quietly churning; find out why"):

1. **Insist on the instruments used by the best in the field.** When Claude reaches
   for Markdown tables, insist on databases and statistical models. You don't need
   to know what experts use — the model usually does.
2. **Pick unreasonable goals and tell the model they're reasonable.** Website loads
   in 10s and you need 5s? Ask for 200ms. Model says impossible? Reiterate that it
   is solvable and keep going. Psychological basis: specific hard goals beat "do
   your best" (Locke & Latham's 35-year goal-setting research synthesis).
3. **Challenge what you know.** Much business "knowledge" is a rough approximation
   of reality. Give the model raw data and ask it to adversarially check
   assumptions: "We believe churn is an onboarding problem. Try to reproduce that
   from the raw data."
4. **Produce new knowledge.** With the model already deep in the data, hunt blind
   spots: "Build a simulation of our customers that reproduces the last year from
   our logs. Then find the earliest churn signal we don't know about yet, and show
   it predicts on data it has not seen." (held-out validation)
5. **Use an outside judge.** Do not ask the model to judge itself (the author
   expects model intelligence to eventually fix this, but as of October 2026,
   insist on outside validation). Ideally a tool the model can run itself and get
   immediate feedback from: unit tests, benchmarks, lint, type checks, independent
   data checks.

### The depth prompt (verbatim, copy-paste ready)

English original:

> I want a deeper version of this task, not a bigger one. Before rewriting it:
> (1) say what a top professional in this field would do here that I'm not asking for;
> (2) name the rawest material they would start from instead of what has already been
> digested for me; (3) name the specific methods and tools they would use;
> (4) say what, other than you or me, would show the result is right.
> Then rewrite my prompt to ask for exactly that.

Chinese rendering:

> 我要的是这个任务更深的版本，而不是更大的版本。在重写之前，请先：
> (1) 说出这个领域的顶尖专业人士在这里会做、而我没有要求的事；
> (2) 指出他们会从哪种最原始的材料入手，而不是那些已经被消化过的二手信息；
> (3) 说出他们会用的具体方法和工具；
> (4) 说明除了你和我之外，还有什么能证明结果是对的。
> 然后把我的提示词改写成恰好要求做到这些的样子。

**The key is the last step**: don't have the AI start working — have it upgrade
your prompt first.

## 5. Range

Consider the work from perspectives of more fields than would have been economical
in the past. Multi-agent systems (threads, orchestrators, subagents) make this
economical for the first time. The author reports the most "magic" here.

Two techniques:

1. **Replace nouns with verbs** (from Tom Kelley & Jonathan Littman, *The Art of
   Innovation*). A quarterly review isn't "a deck" — it's "getting busy people to
   believe a story about cause and effect, and to decide under uncertainty, in 30
   minutes". The verbs reveal which fields to bring in.
2. **Assemble the crew.** If the deck fails, aliens blow up Earth — who does humanity
   call? Production quality: an analyst, a journalist, an editor, maybe a motion and
   audio designer. Adversarial review: a red team of a short seller and a forensic
   accountant.

**The easiest trap — accidental role play**: role play makes transcripts weirder
without improving outcomes. Use the crew to find fields and techniques, then have
the model **do** what each does. Don't ask the model to write like a short seller;
ask it to do what a short seller does to research their position.

## 6. Anti-Patterns Quick Reference

| Anti-pattern | Replacement |
|---|---|
| Role-play prompts (vocabulary switch, not method switch) | Borrow the expert's tools, raw materials and working actions |
| Lowering the goal the moment it's questioned | Restate solvability; raise ambition |
| Asking AI to confirm your beliefs | Adversarially reproduce assumptions from raw data |
| Model self-grading | Outside judge (auto-runnable, immediate feedback) |
| Multi-persona conversational theater | Run each persona's investigation actions |

## 7. Why Ambition

Humans are held back by what they believe possible. Psychology calls it
**self-efficacy**: people who believe they can do more actually accomplish more,
and the evidence says it can be engineered — Michelangelo didn't want to paint the
Sistine Chapel because he saw himself as a sculptor, not a painter. In 1939, UC
Berkeley grad student George Dantzig arrived late, mistook two problems on the
blackboard for homework, and solved them — they were two famously unsolved problems.
Model capability now jumps every few weeks; the constraint is usually on the human side.

## 8. Attribution & Further Reading

- Original essay: https://felixrieseberg.com/how-to-be-more-ambitious-a-tutorial-for-humans-with-models (2026-10-13)
- Community implementations of the depth prompt as a Claude Code Skill (e.g. `/be-ambitious`, DannyMac180/skills)
- The noun-to-verb technique comes from: Tom Kelley & Jonathan Littman, *The Art of Innovation*
