# Resources

## Books — read in this order
1. **The Rust Programming Language** ("the Book") — https://doc.rust-lang.org/book/
   *The canonical starting point. Free, official, recently revised for 2024 edition.*
2. **Rust by Example** — https://doc.rust-lang.org/rust-by-example/
   *Companion to the Book. Use as reference, don't read cover-to-cover.*
3. **Effective Rust** by David Drysdale — https://www.lurklurk.org/effective-rust/
   *35 idioms. Read after Phase 1.*
4. **Asynchronous Programming in Rust** ("async-book") — https://rust-lang.github.io/async-book/
   *Free, official. Read in Phase 3.*
5. **Zero To Production In Rust** by Luca Palmieri — paid (~$40). Worth every cent for Phase 4.
6. **Rust Atomics and Locks** by Mara Bos — https://marabos.nl/atomics/ (free online).
   *Best concurrency book in any language. Phases 3 & 5.*
7. **The Rustonomicon** — https://doc.rust-lang.org/nomicon/
   *Skim only. Tells you when `unsafe` is OK.*
8. **The Rust Performance Book** — https://nnethercote.github.io/perf-book/

## Interactive / video
- **Rustlings** — embedded in this repo at `./rustlings/` (gitignored, local-only). Drive via `cd rustlings && rustlings watch`. Do **in lockstep** with the Book — finish Book §X.Y → run the matching exercise set → don't advance until it passes. Set up with `cargo install rustlings && cd /tmp && rustlings init && mv /tmp/rustlings ~/projects/rust-learning/rustlings` (init refuses inside an existing Cargo project; staging via `/tmp` is the fix). Upstream: https://github.com/rust-lang/rustlings.
- **Jon Gjengset — "Crust of Rust"** YouTube series — deep streams on iterators, lifetimes, async, atomics. *Best for after you've read each topic in the Book.*
- **Let's Get Rusty** YouTube — short, beginner-friendly explainers. Skip if Jon's pace works.
- **Exercism — Rust track** — https://exercism.org/tracks/rust — gentler ramp than Codewars; mentor reviews are gold.

## Practice platforms
- **Codewars** — Rust track. Filter by kyu (8 = trivial, 1 = hard). 8→5 over 16 weeks.
- **Exercism Rust track** — 100+ exercises, optional mentor feedback.
- **Advent of Code** — past years (2020–2024). Great Phase 2 / 5 practice.
- **LeetCode** — solving easy/medium with Rust forces ownership thinking on classic algos.

## Tooling — install Week 1
```
rustup component add clippy rustfmt rust-analyzer
cargo install cargo-watch cargo-edit cargo-expand cargo-audit cargo-nextest
cargo install sqlx-cli criterion-cli flamegraph
```
- **rust-analyzer** — LSP server. Works in VSCode, JetBrains, Helix, Neovim.
- **clippy** — lints. Run `cargo clippy -- -D warnings` in CI.
- **rustfmt** — formatter. Pre-commit hook recommended.
- **cargo-watch** — `cargo watch -x test` for instant feedback.
- **cargo-nextest** — faster test runner with better output.
- **cargo-expand** — see what macros expand to. Great learning tool.

## Reference docs to bookmark
- **std docs** — https://doc.rust-lang.org/std/ (open `Vec`, `HashMap`, `Result`, `Option`)
- **Rust Reference** — https://doc.rust-lang.org/reference/ (when you need exact semantics)
- **Cargo Book** — https://doc.rust-lang.org/cargo/
- **crates.io** + **lib.rs** — package discovery; lib.rs has better quality signal
- **docs.rs** — auto-built docs for every published crate

## Communities
- **/r/rust** — weekly "Hey Rustaceans" thread is great for newbie questions.
- **Rust Users Forum** — https://users.rust-lang.org/ — high-quality answers.
- **Rust Discord / Zulip** — `#beginners` channels.
