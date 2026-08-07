# LLD Notes

Low-level design notes for L5 SDE / SysDev interviews. **Pattern first · Java primary · Spring notes · concurrency at the end because that's where the interview is won.**

Not a pattern catalogue. Each problem is reduced to the *shape* underneath the theming — parking lot is a resource-allocation problem, vending machine is a state machine — and then the patterns are chosen against that shape, with the ones that don't apply explicitly graded ❌ so you know what to *decline*.

Companion repo: [DSA-notes](https://github.com/KarthikGowdaRamakrishna/DSA-notes).

---

## Problems

| # | Problem | Underlying shape | Core patterns | Status |
|---|---|---|---|---|
| 1 | [Parking Lot](parking_lot/) | resource allocation | Singleton · Factory · **Strategy ×2** · Observer | ✅ |
| 2 | Vending Machine | state machine | State · Strategy | ☐ |
| 3 | Elevator System | state machine + scheduling | State · Strategy · Observer | ☐ |
| 4 | ATM | state machine + fallback chain | State · Chain of Responsibility | ☐ |
| 5 | LRU Cache | pure data structure | — (hashmap + doubly linked list) | ☐ |
| 6 | Splitwise | graph settlement | Strategy · Observer | ☐ |
| 7 | Tic Tac Toe / Chess | rules engine | Strategy · Factory · State | ☐ |
| 8 | Notification Service | fan-out | Observer · Adapter · Chain of Responsibility | ☐ |
| 9 | Rate Limiter | token accounting | Strategy · Singleton | ☐ |
| 10 | Logging Framework | pipeline | Chain of Responsibility · Singleton · Strategy | ☐ |

---

## Structure of each problem

Same skeleton every time, so you always know where to look and the narration order is muscle memory:

1. **The one idea** — the shape underneath the theming, and the 2–3 questions the interviewer is actually grading
2. **Requirements** — given · clarifying questions to *ask* · non-functional targets to *state*
3. **Core Operations & Complexity** — the naive cost vs the designed cost, and the structural decisions that close the gap
4. **The object model** — Mermaid class diagram · relationship types (composition vs aggregation, say the right word) · SOLID mapped to concrete decisions
5. **Design patterns** — the full catalogue graded against *this* problem: ✅ Core · ⭐ Strong · ⚠️ Situational · ❌ Not applicable
6. **Templates** — whiteboard-grade Java, plus the Python shape
7. **Concurrency** — the bug everyone writes, the ladder of fixes, which rung to recommend
8. **Interview narration order** — minute-by-minute, 45 min
9. **Extension questions** — one sentence ready for each
10. **Recall card** — the compressed layer for cold review
11. **Repo coverage** — what this discharges from the source catalogue

---

## How to use this

**Narrate, don't draw.** The single biggest scoring mistake in LLD is opening with a UML dump. Establish requirements → operations → *then* the classes fall out almost mechanically. §8 of each file is the minute-by-minute order.

**Grade patterns, don't recite them.** Naming four patterns that fit and explaining why six others *don't* scores far better than listing twelve. The ❌ rows in §5 are as important as the ✅ ones.

**Concurrency is not the epilogue.** It's usually an explicit requirement and it's where L5 separates from L4. Budget the last 8 minutes for it deliberately — §7.

**Practise out loud with a timer.** LLD is a *verbal* exam with code as evidence. Reading these silently will not transfer. Use the §8 table as the script and hold yourself to the minute markers.

**The Recall card is the re-review unit.** After the first full read, §10 alone should regenerate the design. If it doesn't, the gap is in §3, not §5 — go back to the operations table.

---

## Conventions

- Pattern verdicts: **✅ Core** (name it unprompted) · **⭐ Strong** (offer as an extension) · **⚠️ Situational** (only if the interviewer leans there — say the trade-off) · **❌ Not applicable** (know *why*, it's a scoring opportunity)
- Complexity uses `L` = floors/levels, `S` = slots per level, `T` = active transactions, `K` = size/type classes.
- Java is the reference implementation, with Spring wiring where it changes the answer. Python appears where the language forces a different concurrency approach.
- Blockquoted sentences are lines worth saying close to verbatim in the interview.

---

## Sources

- [awesome-low-level-design](https://github.com/ashishps1/awesome-low-level-design) — problems, pattern catalogue, class relationships, concurrency primers
- [algomaster.io/learn/lld](https://algomaster.io/learn/lld) — individual pattern write-ups, linked inline throughout
