# 16-Week Roadmap (2026-05-18 → 2026-09-06)

Legend: 📘 theory · 🛠️ practice (katas/rustlings) · 🚧 project · 🎯 milestone

---

## Phase 1 — Foundations (Weeks 1–4)
*Goal: stop fighting the borrow checker. Read & write idiomatic basic Rust.*

### Week 1 · 2026-05-18 → 2026-05-24 — Setup & Hello, Rust
- 🤖 **Activate `@rust-tutor`** from Day 1. Use it for every kata, every concept, every borrow-checker error. (See `04-tutor-agent.md`.)
- 📘 The Rust Book Ch. 1–3 (variables, types, control flow)
- 📘 Watch: "Rust in 100 seconds" + "Crust of Rust: Lifetime annotations" (intro only)
- 🛠️ Install `rustup`, `cargo`, `rust-analyzer`, `clippy`, `rustfmt`. `cargo new` a scratchpad.
- 🛠️ Rustlings: `intro`, `variables`, `functions`, `if`
- 🛠️ Codewars: 5× **8 kyu** Rust katas (logged via `@rust-tutor`)
- 🎯 **Milestone:** can build/run/test a Cargo project; clippy clean; tutor is part of daily flow.

### Week 2 · 2026-05-25 → 2026-05-31 — Ownership & Borrowing
- 📘 Book Ch. 4–5 (ownership, structs)
- 📘 Watch: Jon Gjengset – "Crust of Rust: Smart Pointers" (first 30 min)
- 🛠️ Rustlings: `move_semantics`, `primitive_types`, `structs`, `vecs`
- 🛠️ Codewars: 8× **8 kyu**
- 🎯 **Milestone:** explain "move vs borrow vs copy" in your own words in `journal/`.

### Week 3 · 2026-06-01 → 2026-06-07 — Enums, Pattern Matching, Errors
- 📘 Book Ch. 6, 9 (enums, `Result`/`?`, panic vs recoverable)
- 🛠️ Rustlings: `enums`, `strings`, `error_handling`, `options`
- 🛠️ Codewars: 5× **8 kyu** + 5× **7 kyu**
- 🚧 Begin **Project 1: `todo-cli`** — scaffold with `clap`, in-memory storage.
- 🎯 **Milestone:** `todo add / list / done` works with `Result<_, Box<dyn Error>>`.

### Week 4 · 2026-06-08 → 2026-06-14 — Collections, Traits, Generics
- 📘 Book Ch. 7, 8, 10 (modules, vec/hashmap/string, generics, traits, lifetimes basics)
- 🛠️ Rustlings: `modules`, `hashmaps`, `traits`, `generics`, `lifetimes`
- 🛠️ Codewars: 8× **7 kyu**
- 🚧 `todo-cli`: persist to JSON file with `serde`. Add `--filter` flag.
- 🎯 **Milestone:** Phase 1 retro. Can read any Rust ≤200-line file and explain it.

---

## Phase 2 — Idioms & Standard Library (Weeks 5–7)
*Goal: write Rust that another Rustacean would call idiomatic.*

### Week 5 · 2026-06-15 → 2026-06-21 — Iterators & Closures
- 📘 Book Ch. 13, 14
- 📘 Read: "Effective Rust" items 1–10
- 🛠️ Rustlings: `iterators`, `traits` (revisit)
- 🛠️ Codewars: 10× **7 kyu** (force iterator chains, no `for` loops)
- 🎯 **Milestone:** rewrite 3 prior solutions in iterator style.

### Week 6 · 2026-06-22 → 2026-06-28 — Testing, Error Types, Modules
- 📘 Book Ch. 11, 7 (deep)
- 📘 `thiserror` + `anyhow` docs
- 🛠️ Rustlings: `tests`, `error_handling` (revisit)
- 🛠️ Codewars: 5× **6 kyu**
- 🚧 **Project 2 kickoff: `minigrep+`** — `ripgrep`-lite with regex, file walking (`walkdir`), colored output (`anstream`).
- 🎯 **Milestone:** custom error enum with `thiserror`; integration tests in `tests/`.

### Week 7 · 2026-06-29 → 2026-07-05 — Smart Pointers & Interior Mutability
- 📘 Book Ch. 15
- 📘 Watch: Jon Gjengset – "Crust of Rust: Smart Pointers" (full)
- 🛠️ Rustlings: `smart_pointers`
- 🛠️ Codewars: 5× **6 kyu**
- 🚧 `minigrep+`: add parallel file search using `rayon`.
- 🎯 **Milestone:** ship v0.1 of `minigrep+` to GitHub with README + benchmarks vs `grep`.

---

## Phase 3 — Concurrency & Async (Weeks 8–10)
*Goal: comfortably reason about threads, tasks, `Send`/`Sync`, futures.*

### Week 8 · 2026-07-06 → 2026-07-12 — Threads & Channels
- 📘 Book Ch. 16
- 📘 "Rust Atomics and Locks" (Mara Bos) — Ch. 1–2
- 🛠️ Rustlings: `threads`
- 🛠️ Codewars: 5× **6 kyu** (focus: data structures)
- 🎯 **Milestone:** build a thread-pool from scratch using `mpsc` channels.

### Week 9 · 2026-07-13 → 2026-07-19 — Async & Tokio
- 📘 Book Ch. 17 (async)
- 📘 "Asynchronous Programming in Rust" (async-book) Ch. 1–4
- 📘 Tokio tutorial (full)
- 🛠️ Codewars: 3× **6 kyu** + 2× **5 kyu**
- 🚧 **Project 3 kickoff: `link-checker`** — async CLI that crawls a site, reports broken links. Uses `reqwest`, `tokio`, bounded concurrency with `Semaphore`.
- 🎯 **Milestone:** explain `Pin`, `Future`, `.await` in your own words.

### Week 10 · 2026-07-20 → 2026-07-26 — Real-world Async Patterns
- 📘 "Atomics and Locks" Ch. 3–5
- 📘 Tokio: tracing, cancellation, graceful shutdown
- 🛠️ Codewars: 5× **5 kyu**
- 🚧 `link-checker`: progress bar (`indicatif`), structured logging (`tracing`), retries with backoff (`tokio-retry`).
- 🎯 **Milestone:** ship `link-checker` v0.1; can crawl 1k pages in <30s.

---

## Phase 4 — Web Backend (Weeks 11–13)
*Goal: production-style REST API, end-to-end.*

### Week 11 · 2026-07-27 → 2026-08-02 — Axum & HTTP
- 📘 "Zero To Production In Rust" (Pavlov) Ch. 1–4
- 📘 Axum docs + examples
- 🛠️ Codewars: 3× **5 kyu**
- 🚧 **Project 4 kickoff: `tasker-api`** — REST API for a task manager. Axum + Tokio, JSON in/out, layered errors.
- 🎯 **Milestone:** `GET /tasks`, `POST /tasks` endpoints with proper status codes.

### Week 12 · 2026-08-03 → 2026-08-09 — Database & sqlx
- 📘 "Zero To Production" Ch. 5–7
- 📘 `sqlx` docs (offline mode, migrations)
- 🛠️ Codewars: 2× **5 kyu**
- 🚧 `tasker-api`: Postgres backend with `sqlx`, migrations with `sqlx-cli`. Compile-time-checked queries.
- 🎯 **Milestone:** integration tests against a Dockerized Postgres pass.

### Week 13 · 2026-08-10 → 2026-08-16 — Auth, Telemetry, Deploy
- 📘 "Zero To Production" Ch. 8–11
- 📘 `tower`, `tower-http` middleware
- 🚧 `tasker-api`: JWT auth, `tracing` + OTLP, Dockerfile, deploy to Fly.io or Railway.
- 🎯 **Milestone:** API live on the internet with basic auth + observability.

---

## Phase 5 — Systems & Performance (Weeks 14–15)
*Goal: speak fluently about memory layout, atomics, `unsafe`.*

### Week 14 · 2026-08-17 → 2026-08-23 — Atomics, Locks, Memory Order
- 📘 "Atomics and Locks" Ch. 6–8 (memory ordering, building locks)
- 📘 "The Rustonomicon" Ch. 1–4 (skim — `unsafe`, layout, alias)
- 🛠️ Codewars: 2× **5 kyu** + 1× **4 kyu**
- 🚧 **Project 5: `tinykv`** — in-memory KV-store with TTL, RWLock, optional WAL on disk.
- 🎯 **Milestone:** benchmark `tinykv` with `criterion`; profile with `samply` or `flamegraph`.

### Week 15 · 2026-08-24 → 2026-08-30 — Performance & FFI taste
- 📘 "The Rust Performance Book" — relevant chapters (alloc, profiling, inlining)
- 📘 `bindgen` / `cbindgen` quick read (not full project)
- 🛠️ Codewars: 1× **4 kyu**
- 🚧 `tinykv`: add a TCP server protocol (Tokio); 10k concurrent ops/s target.
- 🎯 **Milestone:** flamegraph of `tinykv` reviewed; one optimization committed with before/after numbers.

---

## Phase 6 — Freestyle & Portfolio (Week 16)
*Goal: integrate, reflect, make the work visible.*

### Week 16 · 2026-08-31 → 2026-09-06 — Polish & Ship
Pick **one** of the following — whichever excites you most:
- 🚧 **Option A — OSS contribution:** find one good-first-issue in a Rust crate you've used (rustlings, ripgrep, axum-extra, sqlx, indicatif). Ship one merged PR.
- 🚧 **Option B — Stretch a prior project:** add a real feature to `tinykv` (Raft-lite snapshot? cluster-of-2 replication?) or `tasker-api` (background job runner?).
- 🚧 **Option C — Teach what you learned:** 2 short blog posts on the two concepts that took longest to click.

Plus, regardless of choice:
- 🛠️ Polish READMEs, demos, screenshots for `todo-cli`, `minigrep+`, `link-checker`, `tasker-api`, `tinykv`. Pin the best 3 on your GitHub profile.
- 🛠️ Final retro in `journal/2026-W36.md`: what still feels murky, what's the next 3-month goal, how `@rust-tutor` should evolve next.
- 🎯 **Final milestone:** 5 projects on GitHub, 1 deployed API, ~150 katas logged, `@rust-tutor` tuned and in daily use.
