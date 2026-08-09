# Phase 4 — prototype changelog

Rounds are versioned independently. `round-1.html` is at v1; `round-2.html` is at v0.

---

## Round 2 · v0 — 2026-08-09

First build of the commitment path: registration → payment placeholder → confirmation → Your Space, tested against Solo Dance (solo) and Group Dance (5–8 members).

| Built this way | Why |
|---|---|
| Step count declared as "Step N of 4, plus payment if fees apply" | Building it exposed that neither "4 steps" nor "5 steps" can be stated honestly while fee existence is unknown. Fixed in the architecture first → **Amendment A5**, then in the prototype. |
| Roster Member 1 labelled "you" | The least-assuming reading. Whether the registrant is also a participant is genuinely unresolved (Phase 0 Q4) — flagged in place rather than resolved by invention. |
| `[AMOUNT]` shown as a literal token | Keeps the gap visible and machine-searchable. A plausible-looking number "for demo purposes" is exactly the failure mode the placeholder strategy exists to prevent. |
| Error summary moved above the form | Found during the accessibility pass: it was rendering after the fields, so a screen-reader user met the errors before the summary explaining them. |

**Not built:** any gateway, amount, method, refund rule, deadline, or auth mechanism. Three high-severity gaps (F9 registrant-vs-participant, F11 payment states, F12 receipt retrieval) are recorded as blocked on decisions, not designed around.

---

## Round 1 — prototype changelog

These prototypes are **iteration artifacts, not deliverables**. No version is "final". What matters here is not the preserved bytes of any one version — git holds those — but the recorded reason each version stopped being right.

**Current: v1** (`round-1.html`)

---

## v1 — 2026-08-09

*Applies Phase 3 Amendments A1–A4. Architecture was amended first; the prototype was then brought into line.*

| Change | Why it changed |
|---|---|
| Cluster tiles flow to fit available width; small clusters get a compressed header | v0 exposed that real clusters are **6 / 2 / 5 / 3**, not the 4 × 4 Phase 3 assumed. Mind, with two events, rendered as a near-empty row that read like a bug. The content is correct; the layout was wrong. → **Amendment A2** |
| Keyboard tab order stated positionally, no fixed per-cluster indices | Same root cause. Phase 3 §8.A enumerated absolute tab numbers assuming four tiles per cluster. Tile count is a property of content, not of interface. → **Amendment A1** |
| Zone E (judging & materials) renders one column, two columns, or a single line, depending on what the source contains | v0 held a fixed two-column layout, which left a hollow column on the **10 of 16 events with no stated judging criteria**. A hollow box implies information exists and is being withheld. The alternative — inventing plausible criteria — would have been the most damaging invention available on this platform. → **Amendment A3** |
| Zone E label derived from what is actually rendered | Found while testing the fix above: three events (Dumb Charades, G.K. Quiz, Fashion Show) have *neither* judging criteria nor materials, and the first fix labelled their zone "Materials" while showing none. Same class of error as the one being fixed — a label asserting content that isn't there. |
| Events without judging criteria still carry one honest line | Total silence would imply the event is unjudged, when in fact every event in the rulebook ends with "the judges' decision is final". Unknown ≠ none. |
| Search annotation now cites the standing decision | Text search was re-evaluated against all 16 real events and remains rejected. → **Amendment A4** |

**Not changed, deliberately:** cluster membership (real content wins — Phase 0 §3.4 was right all along; the 4 × 4 error entered at Phase 3), the TBD placeholder strategy (validated as-is), and payment (untouched).

**Proposed in v0 but not applied**, because they were not in the approved decision set: dropping the "Where" quick fact (F5), and promoting on-the-spot themes from footnote to quick fact (F7).

---

## v0 — 2026-08-09

First tangible interface for the project. P-01 Welcome → P-03 Landscape → P-04 Event Detail, built with all 16 real events, a live season switch, and a viewport switch.

**Its job was to be falsified, and it was.** Three findings justified the whole round:

1. Real cluster sizes contradicted the architecture's 4 × 4 model.
2. Judging criteria exist for only 6 of 16 events, breaking a layout that assumed symmetry.
3. Honest TBD markers made pages read as *more* trustworthy, not less — the opposite of what was expected.

Superseded by v1. Retrievable at commit `881e1ac`.

---

## How to read a version here

Each entry answers one question: **what did reality say that the previous version got wrong?** If a version changed for any other reason — taste, polish, a new idea — it does not belong in this phase.
