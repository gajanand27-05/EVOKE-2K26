# Phase 4 · Round 1 — Entry → Discovery → Event Detail

*Review report and decision log. Deliberately short — this phase produces interfaces, not another constitution.*

> **These prototypes are iteration artifacts, not deliverables.** No version is final. `wireframes/phase-4/CHANGELOG.md` records what each version got wrong and why it changed — that record, not any single prototype, is the durable output of this phase.

| | |
|---|---|
| **Artifact** | `wireframes/phase-4/round-1.html` — **v1** (history and reasons: `wireframes/phase-4/CHANGELOG.md`) |
| **Screens built** | P-01 Welcome Beat · P-03 Landscape · P-04 Event Detail (all 16 events) |
| **Fidelity** | Low. Greyscale, system type, visible zone boundaries, no brand colour, no motion. |
| **Content** | Real. All 16 events from the rulebook via Phase 0 §3.1. No lorem, no invented facts. |
| **Status** | **v1 complete — re-tested. Round 2 not started.** |

> **v1 (2026-08-09)** applied the corrections approved after the review of v0. Per owner instruction, the architecture was amended *first* and the prototype was then brought into line — the prototype never silently compensates for an architectural error. See Phase 3 **Amendment Log**, entries AM-01–AM-04.

---

## 1. Corrections made

| Approved decision | Architecture change | Prototype change |
|---|---|---|
| **Clusters are 6 / 2 / 5 / 3** | Amendments **AM-01** (tab order is positional, never numbered) and **AM-02** (the "4 clusters × 4 events" model withdrawn; fixed 2×2 cluster grid removed) | Tiles flow with `auto-fill` so a 6-event and a 2-event cluster both look deliberate; small clusters get a compressed header |
| **Four-tile keyboard model** | **AM-01** — §8.A rewritten with positional order and the real per-cluster counts | Tab order is DOM order; no index depends on a count |
| **Judging criteria: adaptive, never fabricated** | **AM-03** — Zone E is two-column *only* when both blocks have content; empty second column forbidden; B8 marked conditional (6 of 16) in §5.4 and §5.6 | Zone E renders one column, two columns, or a single honest line, according to what the source actually contains |
| **Text search rejected** | **AM-04** — §10.A records the re-evaluation against real content and the standing rejection | No search field. Annotation states the decision in place |
| **TBD strategy** | No change — validated as-is | No change |
| **Payment** | Untouched | Untouched |

**Cluster membership was not altered.** Real content wins; the grouping in Phase 0 §3.4 was correct from the start. The 4×4 error entered at Phase 3 and has been removed there.

## 2. Phase 3 assumptions invalidated

| Assumption | Where it lived | Verdict |
|---|---|---|
| Each cluster holds four events | §8.A tab table, §10.E scan narrative, §6.B mobile/desktop layout | **Withdrawn** (AM-01, AM-02) |
| Landscape can use a fixed 2×2 cluster grid | §6.B desktop | **Withdrawn** (AM-02) |
| Zone E is a two-column layout | §3 P-04 blueprint, §6.D | **Conditional now** (AM-03) |
| Every event has judging criteria | implied by Zone E being "Required" | **False** — 6 of 16 (AM-03) |

Two things survived contact with real content unchanged: the **cluster concept** and the **TBD placeholder strategy**.

## 3. One new defect, found while re-testing

Building the adaptive Zone E exposed a case the fix itself had missed: **three events (Dumb Charades, G.K. Quiz, Fashion Show) have neither judging criteria nor a materials list.** The first implementation labelled their zone "Materials" while showing none. Fixed — the zone label is now derived from what is actually rendered. Recorded because it is the same class of error as the original: a label asserting content that isn't there.

## 4. Simulated usability evaluations

*These are simulated evaluations, not validation. No real participant has seen this. Validation requires actual students and coordinators.*

| Scenario | Result | Notes |
|---|---|---|
| **Discover events across uneven clusters** | **Pass** | The 6/2/5/3 split now reads as four named worlds of different sizes rather than a broken grid. Mind (2 events) no longer looks like a rendering failure. Nobody counts events; they read group names. |
| **Find an event with judging criteria** (Group Dance) | **Pass** | Seven criteria in the left column, materials right. Densest page in the set and still scannable. |
| **Find an event without judging criteria** (Solo Dance) | **Pass** | One column, materials only, plus one line stating criteria are not in the rulebook. No hollow box. |
| **Understand TBD information** (Cooking Without Fire) | **Pass with a caveat** | Fee and eligibility read as *pending*, not *absent*. The caveat is unchanged from v0: a participant who wants the duration has nowhere to go, because Contact is also unresolved. |
| **Navigate discovery → detail → back** | **Pass** | Tile → detail → "← All events" returns to the same scroll context. Focus lands on the event heading on arrival. |

## 5. Accessibility re-check

Re-run after the changes: skip link first in DOM; one `<h1>` per screen; `<button>`/`<ol>`/`<dl>` semantics intact; `aria-pressed` on every toggle; `aria-expanded` on FAQ; 3px focus ring visible on both themes; targets ≥44px; status never colour-only; disabled states always explained; `prefers-reduced-motion` honoured; focus moves to the heading on screen change.

**Improved by this revision:** removing the empty judging column removed an empty `<div>` that a screen reader would have announced as a region containing nothing.

**Still open:** mobile drawer (A-05) focus trap — stubbed, tested in Round 4.

## 6. EVOKE Test re-run

| Question | Result |
|---|---|
| Could this belong to another festival? | **Not yet provable at this fidelity** — unchanged from v0, and expected. The slip/edge language is structural only until Phase 5. |
| Could another school reuse this unchanged? | **No** — the cluster names, the 16 events and the rule structure are EVOKE's own. |
| Generic card-grid or hero? | **No.** |
| Participant platform rather than website? | **Yes** — every screen moves toward one decision. |
| Is the loud rationed? | **Yes.** |
| Does every element earn its place? | **Yes now.** The v0 failure was the empty judging column; it is gone. The "Where" quick fact remains under review — see §8. |
| Does every interaction have a reason? | **Yes** — no dead interactions; stubs state which round builds them. |

## 7. Remaining issues

| # | Issue | Severity | Blocked on |
|---|---|---|---|
| **F4** | Four events lack a stated duration or team size: Fashion Show (team size), Instrumental Music, Cooking Without Fire, G.K. Quiz (duration) | Medium | **Organizer.** No design fix exists |
| **F5** | "Where" (On-Stage / Off-Stage) duplicates the cluster tag as a quick fact | Low | Your decision — not approved in this revision, so not applied |
| **F7** | On-the-spot themes (Collage, Pencil Sketch) sit as a footnote rather than a quick fact | Low | Your decision — not approved in this revision, so not applied |
| — | Mobile drawer focus trap untested | Low | Round 4 |
| — | "Can I enter more than one event?" has no answer anywhere | Medium | **Organizer** |

F5 and F7 were proposed against v0 but were **not** in the approved decision table, so they were deliberately left unapplied.

## 8. Decision log

| # | Decision | Reason | Constitution | Rejected alternative |
|---|---|---|---|---|
| **D1** | Default season = Announcement | It is the truth today | Charter §7; Phase 2.5 §11.1 | Defaulting to Registration Open |
| **D2** | Closed/soon events still open their Detail page | Rules stay valuable when registration is shut | Phase 3 §10.B | Disabling the tile |
| **D3** | No search box | Phase 3 §10.A, re-confirmed as Amendment AM-04 | Phase 3 §10.A | Adding search because a later brief mentioned it |
| **D4** | TBD shown as declared gaps, never omitted | An omitted fee reads as "free" | Phase 2 §15.4 | Hiding unknown fields |
| **D5** | Blue annotations, never amber | Wireframe emphasis must not read as brand accent | Owner brief §17 | Brand colour at wireframe stage |
| **D6** | Season switch built as a live control | Makes G1 testable, not asserted | Phase 2.5 G1 | Describing seasons in prose |
| **D7** | Architecture amended before prototype | Prevents documentation drift; the prototype must never outrank the architecture undocumented | Owner instruction, 2026-08-09 | Fixing only the prototype |
| **D8** | Missing judging criteria still get one honest line | Total silence would imply the event is unjudged, when every event ends with the judges' decision | Phase 2 §15.1 | Omitting the zone entirely |

## 9. Is Round 1 ready for approval?

**Yes — with two caveats that are not design problems.**

Every approved correction is applied, in the required order: architecture first, prototype second. The five re-run scenarios pass. Accessibility improved. The EVOKE Test has no failures at this fidelity.

The caveats:

1. **F4 and the two-event question are blocked on the organizer**, not on design. They will persist through every remaining round until that information arrives.
2. **EVOKE Test #1 and #3 cannot be truly passed until Phase 5.** At wireframe fidelity, "would the identity survive the logo being removed" is not answerable — there is no identity applied yet. Recording this as a known limit rather than claiming a pass.

**Round 2 is not started and will not start without explicit approval.**
