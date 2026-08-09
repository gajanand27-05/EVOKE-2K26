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
| 3 | Interface Architecture | `PHASE-3-INTERFACE-ARCHITECTURE.md` | Complete — owner gate open |
| 4 | Visual & Motion Design | not started | Blocked on Phase 3 approval |
| 5 | Implementation | not started | Blocked on Phase 4 |

**There is no separate wireframe phase.** Phase 3 delivers the wireframe *blueprint* — zones, hierarchy, reading order, and content objects per screen. Drawing wireframes and every visual decision (colour, type, spacing, motion, event marks, logo) belongs to Phase 4.

## The constitutions

Phases 0, 1, 1.5, and 1.75 are **immutable**. Every later phase must trace its decisions back to them. A contradiction requires written justification and owner approval — never a silent change of direction.

## Intended implementation stack

**HTML, CSS, JavaScript, Python, Supabase** — for the implementation phase only (Phase 5).

This is a project-level decision, recorded here. It is *not* set by Product Charter §6, which is the 4-question decision filter; documents that previously cited "Charter §6" for the stack were miscitations and have been corrected to point here.

## Gates

Each phase defines an owner approval gate. Their current status is recorded in [`APPROVALS.md`](APPROVALS.md) — all are currently open.
