---
name: deeper-prompt
description: Upgrade any prompt or task into a deeper, more ambitious version BEFORE executing it, using Felix Rieseberg's four-ambition framework (altitude / depth / range + external verification). This skill should be used when the user asks to improve, rewrite, review, stress-test, or design a prompt, hands over a vague or under-powered task, or asks for a "deeper version" of a task. Do NOT trigger for trivial wording tweaks the user explicitly wants kept small, or for casual Q&A. 触发词：升级提示词 / 改写提示词 / 优化 prompt / 提示词评审 / 更深的版本 / 提示词设计 / prompt 改进。
agent_created: true
---

# Deeper Prompt — Pre-Execution Prompt Upgrader

> Named after the core principle: **deeper, not bigger**.

Replace "take the task and start working" with "four-question self-check → rewrite
the prompt → user confirmation → then execute".
Methodology source: Felix Rieseberg (Engineering Manager, Anthropic), "How to be
more ambitious: A tutorial for humans with models", felixrieseberg.com, 2026-10-13.
Full methodology, case library and attribution: `references/methodology-en.md`
(Chinese version: `references/methodology-zh.md`).

## Core Principles

1. **Deeper, not bigger**: upgrade by changing methods, tools, raw materials and
   acceptance criteria — not by asking for more output.
2. **Acting as an expert switches vocabulary, not methods**: never use "you are a
   senior X" role-play as the upgrade mechanism; borrow the expert's tools, raw
   materials and working actions instead.
3. **Never let the model judge itself**: the rewritten prompt must include an
   acceptance mechanism outside the model (auto-runnable tools, tests, benchmarks,
   independent data checks, real users) — ideally a tool the model can run itself
   and get immediate feedback from.
4. **Upgrade the prompt first, execute second**: the deliverable is the rewritten
   prompt; execute only after the user confirms.
5. Reply in the user's current language.

## Trigger / No-Trigger

- Trigger: improving, rewriting, reviewing, or stress-testing a prompt; designing a
  new prompt; a handed-over task that is clearly under-powered ("just fill the
  template", "just give me a table"); the user explicitly asks for a "deeper version".
- No trigger: casual Q&A; the user explicitly says "just change these words, keep
  the structure"; pure formatting adjustments.

## Workflow (five phases; execute phase 5 only after 1–4)

### Phase 1 · Recon

- Read the original task and answer "the goal behind the goal": what does the user
  really want to happen once this is done? Who reviews the result and what decision
  do they make? (the altitude question)
- Check prerequisites: can the model currently access raw data, install and run
  tools (MCP, local scripts, files)? If not, say so explicitly — it caps the
  achievable depth — and list in the rewrite what the user must provide.

### Phase 2 · The Four Depth Questions (answer each in writing before rewriting)

1. What would a top professional in this field do here that the task does not ask for?
2. What is the **rawest material** they would start from, instead of already
   digested second-hand information?
3. What **specific methods and tools** would they use?
4. What, other than the model and the user, would **prove the result is right**?

### Phase 3 · Range Expansion

- Replace the **nouns** in the task with **verbs** to expose what the task really is.
- Based on the verbs, pick 2–3 seemingly unrelated fields and list the **methods**
  each would contribute (not personas). "Short seller" means the adversarial
  investigation they run before opening a position — not imitating their voice.

### Phase 4 · Rewrite the Prompt

Output in the fixed structure (see the template section in `references/methodology-*.md`):

```
1. TRUE GOAL      — ask for the outcome, not the task (one sentence)
2. RAW MATERIALS  — which rawest data/files to start from; list anything missing
                    as a request to the user
3. METHODS/TOOLS  — the concrete tools a top practitioner uses (databases,
                    statistical models, test frameworks…)
4. AMBITION TARGET — set a goal one order of magnitude higher and declare it reasonable
5. EXTERNAL CHECK — who judges: auto-runnable tools / tests / benchmarks /
                    independent data verification
6. PROHIBITIONS   — no role-play filler, no self-grading, no degrading to
                    table-filling
```

Deliver the rewrite plus a diff note versus the original prompt (what changed and
why). **Wait for the user's confirmation** before executing; converge on rejected
parts per the user's feedback.

### Phase 5 · Execute

- Execute per the rewrite; after each phase, run the external check defined in
  section 5 before moving on.
- Attempt at least two different approaches before reporting failure.
- Deliver: results + external-verification evidence + which raw materials were used.

## Self-Check (verify every item after rewriting)

- [ ] A **deeper** version, not a bigger one (methods changed, not just more output)
- [ ] Has raw-material sources; not summarizing second-hand digests further
- [ ] Names concrete tools/methods; no jargon stuffing
- [ ] Has an external verification mechanism outside the model
- [ ] Has an ambition target declared as reasonable (order-of-magnitude, not +10%)
- [ ] No "you are a senior X, act as…" persona anywhere
- [ ] Lists the data/permissions the user must provide

## Anti-Patterns (any occurrence → rework)

| Anti-pattern | Replacement |
|---|---|
| "Act as a senior data analyst" | Demand databases + statistical models on raw data |
| Lowering the goal the moment the model objects | Restate solvability, raise ambition (10s → 5s → 200ms) |
| "Verify what I believe" (confirmation bias) | "Adversarially reproduce this assumption from raw data" |
| Model grading its own output | Automated tests, benchmarks, or independent data checks |
| Multi-persona role-play chat | Have the model run each role's **investigation actions** |

## Resource Index

- `references/methodology-en.md`: full English methodology — four ambitions, five
  depth tactics, range techniques, case library (quarterly review / churn /
  crash-free app), the original prompt (EN/中文), attribution and further reading.
- `references/methodology-zh.md`: the same content in Chinese.
- Load the `-en` file for English-speaking users, otherwise load `-zh`.
