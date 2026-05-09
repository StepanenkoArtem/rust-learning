# Rust Learning Plan — Artem

**Start:** 2026-05-18 (Mon) · **End:** 2026-09-06 (Sun) · **Budget:** ~10 h/week × 16 weeks
**Profile:** Junior / hobbyist · **Goals:** CLI tools, Web backend (Axum), Systems / performance
**Repo:** this directory (`rust-learning`) — Rust 2024 edition, already wired with `src/kyu_8/`.

## Files
- [`01-roadmap.md`](01-roadmap.md) — week-by-week dated milestones
- [`02-resources.md`](02-resources.md) — books, courses, docs, tools
- [`03-projects.md`](03-projects.md) — capstone project specs (CLI → Web → Systems)
- [`04-tutor-agent.md`](04-tutor-agent.md) — design spec for the Rust Tutor agent

## Time split (per week, ~10h)
| Block | Hours | What |
|---|---|---|
| Theory | 3h | Reading + watching, ~1 chapter/week |
| Hands-on exercises | 3h | Rustlings, Codewars katas |
| Project work | 3h | The phase project |
| Review + notes | 1h | Spaced-repetition flashcards, journal in `learning-plan/journal/` |

## How to use this plan
1. **Day 1:** activate `@rust-tutor` (Claude Code subagent at `.claude/agents/rust-tutor.md`). It reads this plan and drives your daily practice. See `04-tutor-agent.md`.
2. Each Monday, open `01-roadmap.md` and load that week's tasks into a TODO.
3. End each week with a 30-min retro entry in `journal/YYYY-Www.md` (template in `journal/_template.md`).
4. Skip nothing in **Phase 1** — ownership/borrowing fluency is the whole game.

## Success criteria (by 2026-09-06)
- [ ] Read **The Rust Book** end-to-end + completed all Rustlings.
- [ ] Solved **150+ Codewars katas** (8kyu→5kyu) in Rust, logged in `katas.csv`.
- [ ] Shipped **5 projects**: `todo-cli`, `minigrep+`, `link-checker`, `tasker-api`, `tinykv`.
- [ ] Can explain ownership, borrowing, lifetimes, `Send`/`Sync`, async/`.await` from memory.
- [ ] `@rust-tutor` tuned to your level, in daily use since Week 1.
