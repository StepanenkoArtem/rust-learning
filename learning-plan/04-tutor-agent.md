# Rust Tutor — Agent (your daily learning tool)

The Rust Tutor is a **Claude Code subagent** you invoke with `@rust-tutor` while working in this repo. It is **not a project you build** — it's the tool you use **from Week 1, every day**, to learn Rust.

## Where it lives
`/.claude/agents/rust-tutor.md` — the agent file. Frontmatter declares its trigger phrases and tool access; the body is its system prompt.

## How to invoke
- Direct: `@rust-tutor warm me up` or `@rust-tutor explain this error: …`
- Implicit: any message that mentions Rust learning will route to it (description-based routing).

## What it does
| Mode | Trigger | Behavior |
|---|---|---|
| **Daily warm-up** | "warm me up", `@rust-tutor` solo | Reads roadmap + journal, runs 1 spaced-repetition flashcard, picks today's kata, scaffolds `TODO(human)`. |
| **Concept teach** | "explain X", "what is X" | Diagnostic question → minimal compilable example in `src/scratch/` → Insight footer. |
| **Code review** | "review this", "check my Rust" | `clippy` + `fmt --check`, walks findings worst→best, ends with one targeted exercise. |
| **Borrow-checker triage** | error code or `cannot borrow` text | Explains *why* the compiler complained, offers 2 fixes with trade-offs, picks one. |
| **Curriculum tracking** | "where am I", "what's next" | Reads `01-roadmap.md` + `katas.csv` + journal; tells you the current phase + week + remaining items. |
| **Project pairing** | working inside one of the `learning-plan/03-projects.md` projects | Drives a TDD-ish loop with `cargo test` + Learn-by-Doing prompts. |

## Files the tutor reads/writes

**Reads (source of truth, rarely modified):**
- `learning-plan/01-roadmap.md` — curriculum + dates
- `learning-plan/02-resources.md` — books, docs
- `learning-plan/03-projects.md` — project specs

**Writes (mutable progress state):**
- `learning-plan/journal/YYYY-Www.md` — weekly log (created from `_template.md`)
- `learning-plan/katas.csv` — every attempted kata
- `learning-plan/flashcards.md` — concept Q/A with Leitner box
- `src/scratch/*.rs` — disposable concept demos
- `src/kyu_<n>/<slug>.rs` — kata solutions
- `src/lib.rs` — module registration

## Pedagogy baked in
1. **Diagnose first** — one targeted question before any explanation.
2. **Show, don't tell** — every concept gets a `cargo build`-able example.
3. **Learn-by-Doing** — code > 20 lines always has a `TODO(human)` block holding the 2–10 most instructive lines.
4. **Borrow-checker fluency** — explain *why the error exists* before showing the fix.
5. **Spaced repetition** — every ~5th turn, surface a prior concept.
6. **Level-matched analogies** — JS/Python/Ruby, never C.

## Why a Claude Code subagent (not a custom-built CLI)
- Zero infrastructure. The file is the agent.
- Already lives next to your code — Read/Edit/Bash on this repo for free.
- Routing is automatic via the description field.
- You'll edit the system prompt as you learn what's missing — fast iteration.

If, much later, you want a standalone web app version (Axum + Anthropic SDK + sandboxed `cargo` runner), it can be a side project — but it's **not required** by this learning plan. The subagent is the answer to "how do I get a Rust tutor."

## Iterating on the tutor
After each week's retro, ask yourself:
1. Where did the tutor over-explain? (tighten that section in the system prompt)
2. What did it forget to do? (add a rule)
3. Did it match my level, or talk down/over? (adjust the learner profile)

Edit `.claude/agents/rust-tutor.md` directly. The agent improves alongside you.
