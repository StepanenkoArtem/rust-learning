# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repo is

A **personal Rust learning workspace**, not a product. Owner: Artem (junior / hobbyist). The bar is *"did I learn?"*, not *"is this prod-ready?"* — do not impose layered errors, structured logging, full test pyramids, or other production patterns on simple kata files. Lead refactor suggestions with the **pedagogical** angle, not the architectural one.

The curriculum runs **2026-05-18 → 2026-09-06**, ~10 h/week, 16 weeks, 6 phases. Source of truth: `learning-plan/01-roadmap.md`.

## The Rust Tutor agent (read before answering Rust questions)

`.claude/agents/rust-tutor.md` defines `@rust-tutor` — the daily-use teaching subagent. Its system prompt encodes pedagogy rules that **override default answer style** for any Rust learning interaction in this repo:

- Diagnose before explaining (one targeted question first).
- Show, don't tell — every concept gets a `cargo build`-able example in `src/scratch/`.
- For code > 20 lines, use the **Learn-by-Doing** pattern: drop a single `TODO(human)` block of 2–10 lines and *wait*.
- Explain *why the compiler complained* before showing a fix.
- **No C/C++ analogies** (learner is junior). JS / Python / Ruby analogies are fine.
- **Never lead with `Rc<RefCell<T>>`** as a borrow-checker fix.
- **No `unsafe` until Phase 5** (Week 14+, 2026-08-17+).

Route any "teach me", "review my Rust", "explain this error", "give me a kata", or curriculum-tracking request to `@rust-tutor`. If you are `@rust-tutor`, follow your system prompt verbatim — it is more specific than this file.

## Repo layout (the parts that aren't obvious)

```
.
├── Cargo.toml                package name = "rust_learning" (underscore); dir name is "rust-learning" (hyphen)
├── src/
│   ├── lib.rs                must register every kyu module (e.g. `pub mod kyu_8;`)
│   └── kyu_<n>/
│       ├── mod.rs            must `pub mod <slug>;` for each kata file
│       └── <slug>.rs         one kata = one file
├── learning-plan/            curriculum + mutable progress state
│   ├── README.md             plan overview
│   ├── 01-roadmap.md         **source of truth** for what to learn this week
│   ├── 02-resources.md       books / videos / tooling
│   ├── 03-projects.md        5 capstone project specs (todo-cli → tinykv)
│   ├── 04-tutor-agent.md     spec of the @rust-tutor subagent
│   ├── flashcards.md         spaced-repetition Q/A; tutor appends + updates Leitner box
│   ├── katas.csv             one row per attempted kata; tutor appends
│   └── journal/
│       ├── _template.md      weekly retro template — copy to `YYYY-Www.md`
│       └── YYYY-Www.md       weekly log (created lazily when needed)
└── .claude/agents/rust-tutor.md   the subagent
```

**Adding a kata** requires three edits, in this order:
1. Create `src/kyu_<n>/<slug>.rs` with the solution + `#[cfg(test)] mod tests`.
2. Add `pub mod <slug>;` to `src/kyu_<n>/mod.rs` (create the kyu dir + `mod.rs` if first kata at that level).
3. Add `pub mod kyu_<n>;` to `src/lib.rs` if it's the first kata at that level.

## Commands

```bash
# Build / test
cargo build
cargo test                          # all tests
cargo test <name>                   # single test by name substring
cargo test --lib kyu_8::reverse     # specific kata's tests

# Lint / format (run before commits)
cargo clippy -- -D warnings         # treat lints as errors
cargo fmt                           # apply formatting
cargo fmt --check                   # CI-style check
```

No build/CI/script wrappers exist — invoke `cargo` directly.

## Editing rules for this repo

- **Don't silently edit `learning-plan/01-roadmap.md`.** It's the curriculum contract; confirm with the owner before changing dates, phases, or milestones.
- **Free to write to** `src/`, `learning-plan/journal/*`, `learning-plan/katas.csv`, `learning-plan/flashcards.md`, `src/scratch/*`.
- **Flag any new dependency in `Cargo.toml`** before adding it. The `[dependencies]` section is intentionally empty until the curriculum justifies the addition.
- **Edition is 2024.** Use 2024-edition idioms; don't downgrade examples to 2021 syntax.

## Branch / commit conventions

Single branch `master` (owner prefers it over `main`). Remote: `origin` → `git@github.com:StepanenkoArtem/rust-learning.git`. `gpsup` (zsh alias) pushes the current branch and sets upstream.
