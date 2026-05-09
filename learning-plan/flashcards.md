# Spaced-Repetition Flashcards

Maintained by `@rust-tutor`. New cards appended after each new concept; reviewed cards updated in place.

**Box schedule (Leitner-ish):**
- Box 1 → review next day
- Box 2 → review +3 days
- Box 3 → review +1 week
- Box 4 → review +2 weeks
- Box 5 → review +1 month

Correct answer: promote box +1. Wrong/fuzzy: demote to box 1.

| Q | A | last_reviewed | box |
|---|---|---|---|
| What does *ownership* mean in 1 sentence? | Each value has exactly one owner; when the owner goes out of scope, the value is dropped. | — | 1 |
| Move vs Copy — when does each happen? | `Copy` types (primitives + types implementing `Copy`) are duplicated on assignment; non-`Copy` types are *moved* and the source becomes invalid. | — | 1 |
| `&T` vs `&mut T`? | `&T` = shared, immutable borrow (many allowed). `&mut T` = exclusive (only one at a time; no shared borrows alive during its lifetime). | — | 1 |
| Why does Rust have `Option<T>` instead of null? | Forces the caller to handle the absent case at compile time; no `NullPointerException` class of bug exists. | — | 1 |
| `String` vs `&str`? | `String` owns a heap-allocated, growable UTF-8 buffer. `&str` is a borrowed view (slice) into one — no allocation, fixed size. | — | 1 |
