# Capstone Projects

Five projects, escalating in difficulty. Each lives in its own crate inside a Cargo workspace under `~/projects/rust/`.

---

## Project 1 — `todo-cli` (Weeks 3–4)
**Skills:** ownership, modules, `serde`, `clap`, error handling, `Result`/`?`.

### Spec
Minimum viable: `todo add "buy milk"`, `todo list`, `todo done 2`, `todo rm 2`.
Stretch: `--filter pending|done`, due dates, priority, JSON persistence in `~/.todo.json`.

### Crates
- `clap` (derive macros) — argument parsing
- `serde` + `serde_json` — persistence
- `anyhow` — top-level error type
- `chrono` — due dates (stretch)

### Acceptance
- [ ] `cargo clippy -- -D warnings` clean
- [ ] At least 5 unit tests + 1 integration test in `tests/cli.rs` using `assert_cmd`
- [ ] README with install + usage gif

---

## Project 2 — `minigrep+` (Weeks 6–7)
**Skills:** iterators, file I/O, regex, error types with `thiserror`, parallelism.

### Spec
`mg "pattern" path/` — recursive search with line numbers, colored output. Stretch: glob filters, parallel walking, `--json` output.

### Crates
- `regex` — pattern matching
- `walkdir` or `ignore` (the one ripgrep uses)
- `anstream` + `anstyle` — colored output that respects `NO_COLOR`
- `rayon` — parallelism (stretch)
- `thiserror` — typed errors

### Acceptance
- [ ] Searches a 10k-file repo without OOM
- [ ] Benchmark vs `grep -r` (you won't beat ripgrep — that's fine)
- [ ] Honors `.gitignore` (stretch, but easy with `ignore` crate)

---

## Project 3 — `link-checker` (Weeks 9–10)
**Skills:** async/await, Tokio, `reqwest`, structured concurrency, retries, tracing.

### Spec
`link-check https://example.com --depth 2` crawls and reports broken links. Bounded concurrency, retry on 5xx, progress bar.

### Crates
- `tokio` (rt-multi-thread, macros)
- `reqwest` — HTTP client
- `scraper` — HTML parsing
- `tracing` + `tracing-subscriber` — structured logs
- `indicatif` — progress bar
- `tokio-retry` — backoff

### Acceptance
- [ ] Concurrency capped via `Semaphore` (no fork-bomb on huge sites)
- [ ] Graceful Ctrl-C — flushes in-flight, prints partial report
- [ ] 1000 URLs in < 30s on a normal home connection

---

## Project 4 — `tasker-api` (Weeks 11–13)
**Skills:** Axum, `sqlx`, JWT auth, migrations, Docker, observability.

### Spec
REST API with `users` and `tasks`. Endpoints: `POST /signup`, `POST /login`, `GET /tasks`, `POST /tasks`, `PATCH /tasks/:id`, `DELETE /tasks/:id`. JWT in `Authorization: Bearer`.

### Crates
- `axum`, `tower`, `tower-http`
- `tokio`
- `sqlx` (postgres, runtime-tokio, migrate, macros)
- `argon2` — password hashing
- `jsonwebtoken` — JWT
- `serde`, `serde_json`
- `tracing`, `tracing-subscriber`, `tower-http::trace`
- `validator` — input validation
- `thiserror`

### Acceptance
- [ ] `sqlx migrate` up + down
- [ ] Integration tests spin up Postgres via `testcontainers` or external `docker compose`
- [ ] Dockerfile builds < 200MB image (multi-stage, distroless or alpine)
- [ ] Deployed to Fly.io / Railway / Shuttle, smoke-tested with `curl`

---

## Project 5 — `tinykv` (Weeks 14–15)
**Skills:** atomics, RwLock, TCP server, custom protocol, benchmarks, profiling.

### Spec
Embedded + networked key-value store. Phase A: in-process API `kv.set("k","v")`. Phase B: TCP server with line-based protocol (`SET k v\n`, `GET k\n`). Phase C: TTL + optional write-ahead log.

### Crates
- `tokio` (net, sync)
- `dashmap` *(or roll your own with `RwLock<HashMap>`)*
- `bincode` — WAL serialization
- `criterion` — micro-benchmarks
- `flamegraph` (binary) — profiling

### Acceptance
- [ ] 10k ops/sec single-threaded baseline
- [ ] Flamegraph generated and one bottleneck identified in commit message
- [ ] WAL replay on restart correctness test

---

## Project 6 — Capstone: Rust Tutor (Week 16)
See `04-tutor-agent.md` — combines Axum (Phase 4), `tokio` (Phase 3), CLI ergonomics (Phase 1–2), and the Anthropic API.
