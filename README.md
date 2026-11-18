# deeper-prompt

> Named after the core principle: **deeper, not bigger**.
> A skill that upgrades any prompt into a deeper, more ambitious version **before
> execution** — instead of just running the task as handed over.

Based on the four-ambition framework from **Felix Rieseberg** (Engineering Manager
at Anthropic; led Claude.ai, Cowork, and Claude Code Desktop), from his essay
[How to be more ambitious: A tutorial for humans with models](https://felixrieseberg.com/how-to-be-more-ambitious-a-tutorial-for-humans-with-models)
(2026-10-13).

## What it does

Replaces "take the task and start working" with a five-phase loop:

```
Recon → Four Depth Questions → Range Expansion → Rewrite → Confirm → Execute
```

- **Deeper, not bigger** — upgrade methods, tools, raw materials and acceptance
  criteria, not output volume
- **No expert role-play** — "act as a senior X" switches vocabulary, not methods;
  borrow the tools and raw materials a top practitioner actually uses
- **Never self-graded** — every rewrite ships with an external verification
  mechanism (tests, benchmarks, auto-runnable checks)
- **Prompt-first, execution-second** — the deliverable is a rewritten prompt; the
  agent waits for your confirmation before doing any work

## The core prompt

> I want a deeper version of this task, not a bigger one. Before rewriting it:
> (1) say what a top professional in this field would do here that I'm not asking for;
> (2) name the rawest material they would start from instead of what has already been
> digested for me; (3) name the specific methods and tools they would use;
> (4) say what, other than you or me, would show the result is right.
> Then rewrite my prompt to ask for exactly that.

## Why the classic "5-layer prompt design" falls short

The popular prompt-engineering recipe has five layers: **role** ("you are a senior
X"), **context**, **task**, **constraints**, **output format**. It optimizes how the
*request* is phrased — and that has a ceiling:

| | Classic 5-layer design | Ambition framework (this skill) |
|---|---|---|
| What it optimizes | How the prompt **sounds** | How the work is **done**: methods, tools, data, acceptance |
| Expert entry | The role layer "acts as" the expert — the model switches vocabulary, not methods | Borrows the expert's **tools, raw materials, working actions** (databases / statistical models, not tables) |
| Data | The context layer passes along second-hand, pre-digested material | Forces a return to the **rawest source** (logs / filings / code); missing inputs get requested from the user |
| Goal | The task layer relays the user's ask verbatim | Sets a goal **one order of magnitude higher** and declares it reasonable (10s → 5s → 200ms) |
| Acceptance | The constraint layer can only constrain format; quality rides on self-grading or eyeballing | Mandates an **outside judge**: tests, benchmarks, auto-runnable checks — never self-grading |
| Flow | Write five layers → execute | Four-question self-check → **rewrite the prompt first** → confirm → execute |

In one line: the 5-layer recipe **wraps** a mediocre task better; the ambition
framework **replaces** the task itself. The five layers can coexist — a rewritten
prompt can still be expressed in 5-layer form — but quality is decided by the goal,
the raw materials, the tools and the external check, exactly the four things the
5-layer recipe never touches.

## Structure

```
deeper-prompt/
├── SKILL.md                    # Skill entry (Chinese) — workflow, checklist, anti-patterns
├── SKILL.en.md                 # Full English mirror of the skill entry
└── references/
    ├── methodology-zh.md       # Full methodology in Chinese (cases, prompt, attribution)
    └── methodology-en.md       # Full methodology in English
```

## Install

Copy the `deeper-prompt/` folder into your agent's skills directory:

- WorkBuddy (user scope): `~/.workbuddy/skills/deeper-prompt/`
- Claude Code: `~/.claude/skills/deeper-prompt/`

Then trigger it with things like *"帮我升级这个提示词"*, *"我要这个任务更深的版本"*,
*"stress-test this prompt"*, or *"improve this prompt"*. (`SKILL.md` is the entry
file; `SKILL.en.md` is the English mirror for reference.)

## Attribution

Methodology © Felix Rieseberg — the skill operationalizes his public essay and
credits it throughout. The noun-to-verb technique originates from *The Art of
Innovation* (Tom Kelley & Jonathan Littman).

## License

MIT
