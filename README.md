# rust-learning

A public log of one programmer learning Rust, in the open.

**Owner:** [@StepanenkoArtem](https://github.com/StepanenkoArtem)
**Plan:** 16 weeks · 2026-05-18 → 2026-09-06 · ~10 h/week
**Status:** *Bootstrapped — kicks off Week 1 on 2026-05-18*

This repo is a learning workspace, not a product. It holds the curriculum, weekly journal, kata solutions, and a bespoke teaching agent. Forks welcome if you want to use the same plan as a template.

---

## What's in here

| Path | What it is |
|---|---|
| [`learning-plan/`](./learning-plan/) | The full 16-week plan: roadmap, resources, project specs, agent design |
| [`learning-plan/01-roadmap.md`](./learning-plan/01-roadmap.md) | Week-by-week dated milestones — the curriculum contract |
| [`learning-plan/journal/`](./learning-plan/journal/) | Weekly retro entries (`YYYY-Www.md`) |
| [`learning-plan/katas.csv`](./learning-plan/katas.csv) | One row per attempted Codewars kata |
| [`learning-plan/flashcards.md`](./learning-plan/flashcards.md) | Spaced-repetition concept Q/A (Leitner box) |
| [`src/kyu_<n>/`](./src/) | Kata solutions, organized by Codewars difficulty (8kyu = easiest) |
| [`.claude/agents/rust-tutor.md`](./.claude/agents/rust-tutor.md) | The Rust Tutor — a Claude Code subagent that teaches, reviews, and tracks progress |
| [`CLAUDE.md`](./CLAUDE.md) | Operating instructions for AI agents working in this repo |

## The 16-week plan at a glance

| Phase | Weeks | Dates | Focus | Project |
|---|---|---|---|---|
| 1 Foundations | 1–4 | 2026-05-18 → 06-14 | Ownership, borrowing, types | `todo-cli` |
| 2 Idioms & stdlib | 5–7 | 06-15 → 07-05 | Iterators, smart pointers | `minigrep+` |
| 3 Concurrency & async | 8–10 | 07-06 → 07-26 | Threads, Tokio | `link-checker` |
| 4 Web backend | 11–13 | 07-27 → 08-16 | Axum + sqlx + Postgres | `tasker-api` |
| 5 Systems & perf | 14–15 | 08-17 → 08-30 | Atomics, locks, profiling | `tinykv` |
| 6 Freestyle | 16 | 08-31 → 09-06 | OSS contribution / blog / polish | — |

Full breakdown: [`learning-plan/01-roadmap.md`](./learning-plan/01-roadmap.md).

## The Rust Tutor agent

A teaching subagent that runs inside [Claude Code](https://docs.claude.com/en/docs/claude-code) — invoked with `@rust-tutor` from anywhere in this repo. It:

- reads the curriculum + latest journal entry to know what week you're on,
- picks a kata one notch above your last solved kyu and scaffolds a `TODO(human)` skeleton,
- runs `cargo clippy` / `fmt` and walks findings worst→best,
- explains *why* the borrow checker complained before showing the fix,
- surfaces a spaced-repetition flashcard every ~5 turns.

Pedagogy is encoded in the system prompt at [`.claude/agents/rust-tutor.md`](./.claude/agents/rust-tutor.md):
no C/C++ analogies, no `Rc<RefCell<T>>`-first answers, no `unsafe` until Phase 5, Learn-by-Doing for any code over ~20 lines.

The agent is a **tool used from Day 1**, not a project to build.

## Build & test

```bash
cargo build
cargo test                              # all katas
cargo test kyu_8::reverse_string        # one kata's tests
cargo clippy -- -D warnings             # lints as errors
cargo fmt --check                       # formatter check
```

Edition: **2024**. Package name: `rust_learning` (Cargo names use `_`). No third-party dependencies yet — by design; they get added when the curriculum justifies them.

## Adding a kata

```bash
# 1. solution file
src/kyu_<n>/<slug>.rs    # solution + #[cfg(test)] mod tests

# 2. register in the kyu module
src/kyu_<n>/mod.rs       # add: pub mod <slug>;

# 3. register the kyu module (only first time at that level)
src/lib.rs               # add: pub mod kyu_<n>;
```

## Why public

Public learning repos are an honest signal. The journal, flashcards, and 16 weeks of dated commits show *the process*, not just the artifact. Take what's useful.

## License

MIT — see [`LICENSE`](./LICENSE) (TBD).
