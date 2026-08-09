# EVOKE 2K26 — Phase Roadmap (canonical)

This document is the **single source of truth** for what each phase number means and what the project's intended implementation stack is.

Individual phase documents were written at different times and some contain stale forward-references — Phase 2, for example, calls Phase 3 "Wireframes". **Where a phase document disagrees with this file, this file wins.**

---

## The phases

| Phase | Name | Deliverable | Status |
|---|---|---|---|
| 0 | Discovery | `PHASE-0-DISCOVERY.md` | Complete (constitution) |
| 1 | Brand Bible | `PHASE-1-BRAND-BIBLE.md` | Complete (constitution) |
| 1.5 | Creative Direction Review | `PHASE-1-5-CREATIVE-REVIEW.md` | Complete (constitution) |
| 1.75 | Product Charter | `PHASE-1-75-PRODUCT-CHARTER.md` | Complete (constitution) |
| 2 | Experience Direction | `PHASE-2-EXPERIENCE-DIRECTION.md` | Complete — owner gate open (`APPROVALS.md`) |
| 2.5 | Structural Architecture / IA Validation | `PHASE-2-5-STRUCTURAL-ARCHITECTURE.md` | Complete — owner gate open |
| 3 | Interface Architecture | `PHASE-3-INTERFACE-ARCHITECTURE.md` | **Approved** 2026-08-09 (9.7/10) |
| 4 | Wireframe & Interaction Prototyping | `wireframes/phase-4/` + round review docs | **In progress** — Round 1 complete, awaiting review |
| 5 | High-Fidelity Visual Design | not started | Blocked on Phase 4 |
| 6 | Implementation | not started | Blocked on Phase 5 |

**Phase 4 was redefined by the owner on 2026-08-09.** It was previously scoped as "Motion & Interaction Blueprint". Motion is already sufficiently constrained by Phase 1.5 (laws, gestures, tempo, named exceptions, reduced-motion, performance bounds), and motion should not be designed before the interface has been seen. Phase 4 is therefore **Wireframe & Interaction Prototyping** — low-fidelity, testable interfaces built with real event content.

**Phase 4 runs in five reviewed rounds**, one at a time, each stopping for owner review before the next begins:

1. Entry → Event Discovery → Event Detail — **complete (v1), approved**
2. Event Detail → Registration → Payment placeholder → Confirmation → Your Space — **prototyped (v0), held: blocked by organizer question A1**
3. Schedule, announcements, support, secondary areas — not started
4. System states across every screen

*Round structure amended 2026-08-09: the originally separate Rounds 2 (registration flow) and 3 (payment, confirmation, Your Space) were merged into a single Round 2, because registration and its confirmation are one continuous decision and testing them apart would test neither honestly. Later rounds shift up by one; Phase 4 now runs in four rounds, not five.*

**Standing constraint (owner, 2026-08-09):** stop expanding the architecture documentation. Do not add further architecture unless an actual contradiction is discovered. Phase 4 output is interface artifacts, not specification.

## Standing practice — the amendment loop

**When reality contradicts the architecture, the architecture is amended first and the prototype follows.** Never the reverse, and never "note it and move on".

The loop, in order:

```
contradiction discovered (usually mid-build, on contact with real content)
        ↓
STOP building
        ↓
amend the architecture, and record the amendment in its Amendment Log
        ↓
build from the amendment
        ↓
re-test
```

Two things this prevents:

1. **Documentation drift** — a prototype that quietly does something the specification does not say, so the specification slowly becomes fiction.
2. **The prototype outranking the architecture undocumented** — where the real design lives in whoever last touched the code.

The amendment is written *before* the fix, not after. In practice contradictions surface mid-build rather than during a tidy review step: Amendment AM-05 was found on the first screen of Round 2, when registration could not honestly declare how many steps it had. Had that waited until the round's report, five screens would have been built on a statement known to be untrue.

Amendments are numbered `AM-nn` and live in the amended document's own Amendment Log, so the record sits beside the thing it corrects. (`A1`–`A8`, `B1`–`B12` etc. are content-object codes from the Phase 2.5 inventory — do not reuse them for amendments.)

## The constitutions

Phases 0, 1, 1.5, and 1.75 are **immutable**. Every later phase must trace its decisions back to them. A contradiction requires written justification and owner approval — never a silent change of direction.

## Intended implementation stack

**HTML, CSS, JavaScript, Python, Supabase** — for the implementation phase only (Phase 6).

This is a project-level decision, recorded here. It is *not* set by Product Charter §6, which is the 4-question decision filter; documents that previously cited "Charter §6" for the stack were miscitations and have been corrected to point here.

## Gates

Each phase defines an owner approval gate. Their current status is recorded in [`APPROVALS.md`](APPROVALS.md) — all are currently open.
