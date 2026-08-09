# EVOKE 2K26 — Approval Register

*The record of which phase gates have been signed, by whom, and when.*

| | |
|---|---|
| **Purpose** | Each phase document defines an owner gate that must be passed before the next phase begins. Until now those gates existed only inside the documents that defined them, with no record of whether they were ever actually passed. This file is that record. |
| **Rule** | A gate is **OPEN** until an owner records a decision here. Work may proceed past an open gate only as a deliberate, stated choice — never by default or by silence. |
| **Who signs** | The project owner (human). Agents do not sign gates and must not mark one PASSED on the owner's behalf. |

---

## Current status

| Gate | Defined in | Decision required | Status | Signed by | Date |
|---|---|---|---|---|---|
| **Phase 0 — Discovery approval** | `PHASE-0-DISCOVERY.md` §15 | Approve discovery; answer priority [MISSING] items | **OPEN** | — | — |
| **Phase 2 — Acceptance Review** | `PHASE-2-EXPERIENCE-DIRECTION.md` Appendix B | Answer the five questions; all five must pass | **OPEN** | — | — |
| **Phase 2.5 — Gatekeeper Review** | `PHASE-2-5-STRUCTURAL-ARCHITECTURE.md` Part 14 | Answer the five gate questions with evidence; sign the Readiness Report (Part 15) | **OPEN** — Part 15.1 records this row as PENDING | — | — |
| **Phase 3 — Interface Architecture approval** | `PHASE-3-INTERFACE-ARCHITECTURE.md` header + Part 17 | Approve the specification before Phase 4 begins | **PASSED** — scored 9.7/10 | Project owner | 2026-08-09 |

**Three gates remain open; Phase 3 is approved.**

---

## What this means in practice

Phase 2.5 and Phase 3 were both written and committed while the gates preceding them were open. That is a fact about how the work happened, not a defect in the work itself — but it does mean the documents downstream of those gates carry an assumption that was never confirmed by the owner.

Two honest options:

1. **Sign retroactively.** If the owner reads each document and accepts it, record the decision below. The gates close, and the assumption becomes a decision.
2. **Retire the gates.** If per-phase owner sign-off is not how this project actually runs, say so here and delete the gate sections from the phase documents so they stop asserting a process that isn't followed. A gate nobody uses is worse than no gate — it makes the documents claim a rigour the project doesn't have.

What should **not** happen is leaving the gates defined, unsigned, and silently walked past. That is the state this file exists to end.

---

## How to record a decision

Add a row to the log below and update the status table above. Keep it short and dated.

```
| YYYY-MM-DD | <gate> | PASSED / RETURNED / RETIRED | <who> | <one line: what was decided and why> |
```

## Decision log

| Date | Gate | Decision | By | Note |
|---|---|---|---|---|
| 2026-08-09 | Phase 3 — Interface Architecture | **PASSED** (9.7/10) | Project owner | Approved as a complete interface-architecture artifact, not a plan for wireframes. Standing instruction attached: stop expanding architecture documentation; the next phase produces interface artifacts, not another specification. |

---

## Related

- Phase roadmap and status: [`ROADMAP.md`](ROADMAP.md)
- Outstanding organizer information (Q1–Q22, Charter §7 TBDs): `PHASE-0-DISCOVERY.md` §10, `PHASE-1-75-PRODUCT-CHARTER.md` §7, `PHASE-3-INTERFACE-ARCHITECTURE.md` §17.D
