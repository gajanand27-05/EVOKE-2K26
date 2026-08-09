# Phase 4 · Round 1 — Entry → Discovery → Event Detail

*Review report and decision log. Deliberately short — this phase produces interfaces, not another constitution.*

| | |
|---|---|
| **Artifact** | `wireframes/phase-4/round-1.html` (open in a browser; also published for review) |
| **Screens built** | P-01 Welcome Beat · P-03 Landscape · P-04 Event Detail (all 16 events) |
| **Fidelity** | Low. Greyscale, system type, visible zone boundaries, no brand colour, no motion. |
| **Content** | Real. All 16 events from the rulebook via Phase 0 §3.1. No lorem, no invented facts. |
| **Status** | **Round 1 complete — awaiting review. Round 2 not started.** |

---

## 1. What was prototyped

Three screens, clickable end-to-end: Welcome → Landscape → any of 16 Event Details → back. Plus three prototype controls that are *not* product features: viewport (mobile/tablet/desktop), season state G1 (Announcement / Registration Open / Closed), and an annotations layer that maps every block to its Phase 3 zone.

Default season is **Announcement**, because that is the honest current state — dates, fees and registration mechanics are unknown, so registration cannot be presented as open.

## 2. What works

- **Progressive Confidence holds across the three screens.** Welcome answers *what is this*, Landscape answers *what can I do*, Detail answers *can I do it*. Each screen ends where the next begins.
- **Cluster-first discovery survives real content.** Four worlds genuinely reduce the choice; the tiles are scannable at 390px without zooming.
- **Honest gaps read as confidence, not absence.** Marking eligibility, fee, judging criteria and durations as TBD makes the page feel more trustworthy, not less. This was the biggest surprise of the round.
- **The season switch proves the G1 architecture.** One state change correctly rewrites the Welcome status line, the CTA label, all 16 status badges and the Detail decision zone — with no screen breaking.
- **Zone G disabled state carries its reason** in every season, so no dead button ever appears.

## 3. What does not work — findings

| # | Finding | Severity | Where |
|---|---|---|---|
| **F1** | **Clusters are 6 / 2 / 5 / 3, not 4 × 4.** Phase 3 §10.E describes the five-second scan as "4 clusters × 4 events each", and the §8.A keyboard tab-order table numbers exactly four tiles per cluster. Real content contradicts both. Mind has only 2 events and reads as an afterthought; Stage has 6 and dominates the scroll. | **Medium** | Phase 3 §8.A, §10.E |
| **F2** | **Mind cluster looks broken at two events.** Two tiles under a heading with a blurb costs more vertical space than it returns. Either Mind absorbs a third event, or cluster headers compress when a cluster is small. | Medium | P-03 Zone B |
| **F3** | **Judging criteria exist for only 6 of 16 events.** Zone E is half-empty for ten events. The honest TBD is correct, but Zone E's two-column layout was designed assuming both columns fill. | Medium | P-04 Zone E |
| **F4** | **Four events have no stated duration and one has no stated team size.** Fashion Show (team size), Instrumental Music, Cooking Without Fire, G.K. Quiz (duration). Quick-facts cards therefore show TBD in a slot participants will most want filled. | Medium | P-04 Zone C |
| **F5** | **"Where" (On-Stage / Off-Stage) is weak as a quick fact.** It duplicates information the cluster already carries and earns a card that could hold something decision-relevant. | Low | P-04 Zone C |
| **F6** | **Phase 4 brief mentions "searching"; Phase 3 §10.A explicitly rejects search** for 16 events. Not silently resolved — see Decision D3. | Low | Conflict |
| **F7** | **Two events cannot be prepared in advance** (Collage, Pencil Sketch — on-the-spot themes). Currently a footnote under the rules. This is expectation-setting important enough to sit higher. | Low | P-04 Zone D |

## 4. Simulated usability findings

| Scenario | Result | Where they hesitate |
|---|---|---|
| "I want to do Solo Dance." | **Completes.** Stage → Solo Dance → rules clear in one screen. | None. |
| "Do we have enough people for Group Dance?" | **Completes.** "5–8" is visible on the tile before opening the event. | None — the tile answering it without a tap is the round's best result. |
| "What do I bring for Vegetable Carving?" | **Completes.** Zone E names vegetables and tools. | Brief — they scroll past rules first. Materials sit below judging. |
| "What are the rules for Cooking Without Fire?" | **Completes with a gap.** All four rules are shown, but duration is TBD, which is the next thing they ask. | At Zone C. |
| "Am I allowed to enter two events?" | **Fails honestly.** FAQ says TBD. | This question has no answer anywhere on the platform. |

**The abandonment risk is F4 + the two-event question:** a participant who reaches Zone C and finds their key fact unknown has no path to an answer, because Contact (Q12) is also unresolved. Not fixable in design — it is blocked on the organizer.

## 5. Accessibility check

Passing at wireframe level: skip link first in DOM, one `<h1>` per screen, real `<button>`/`<ol>`/`<dl>` semantics, `aria-pressed` on all toggles, `aria-expanded` on FAQ, visible 3px focus ring on both themes, all targets ≥44px, status text never colour-only, disabled states explained, `prefers-reduced-motion` honoured. Focus moves to the heading on screen change.

**Open:** the mobile drawer (A-05) is stubbed, so its focus trap is untested — Round 4.

## 6. Mobile and density

Mobile is the design origin, not a shrink. Detail at 390px runs long — Group Dance is the worst case at 7 judging criteria plus 4 rules — which is why Zone G is sticky. **No typography was shrunk to fit**; where density hurts, the finding is recorded instead (F3, F5).

## 7. EVOKE Test

| Question | Result |
|---|---|
| Could this belong to another festival? | **Not yet provable.** At wireframe fidelity the slip/edge language is structural only. This is expected, but it means EVOKE Test #1/#3 cannot truly be passed until Phase 5. |
| Generic card-grid or hero? | **No.** No hero image, no marketing banner, no carousel, no cross-sell. |
| Does it feel like a participant platform, not a website? | **Yes.** Every screen moves toward one decision. |
| Is the loud rationed? | **Yes** — arguably too much. See D5. |
| Does every element earn its place? | **One failure:** F5. |

## 8. Decision log

| # | Decision | Reason | Constitution | Rejected alternative |
|---|---|---|---|---|
| **D1** | Default season = Announcement | It is the truth today; dates and fees are unknown | Charter §7; Phase 2.5 §11.1 | Defaulting to Registration Open — would present an invented state |
| **D2** | Closed/soon events still open their Detail page | Rules are valuable even when registration is shut | Phase 3 §10.B | Disabling the tile — creates a dead end |
| **D3** | No search box | Phase 3 §10.A justified its removal for 16 events; the Phase 4 brief's mention of search is noted, not silently actioned | Phase 3 §10.A | Adding search "because the brief said so" — would override an approved decision without justification |
| **D4** | TBD facts shown as declared gaps, never omitted | An omitted fee reads as "free" — an invented answer | Phase 2 §15.4 | Hiding unknown fields |
| **D5** | Wireframe uses blue annotations, never amber | Prevents anyone reading wireframe emphasis as brand accent | User brief §17 | Brand colours at wireframe stage |
| **D6** | Season switch built as a live control | Makes the G1 architecture testable rather than asserted | Phase 2.5 G1 | Describing seasons in prose |

## 9. Proposed changes — for your decision, not yet applied

1. **F1/F2** — either accept uneven clusters and compress small-cluster headers, or revisit the Mind grouping. *Recommendation: accept the unevenness, compress the header.* The grouping is truthful; the layout should bend, not the content.
2. **F3** — collapse Zone E to a single column when judging criteria are absent, so ten events stop showing a half-empty grid.
3. **F5** — drop the "Where" quick fact; the cluster tag already carries it.
4. **F7** — promote "theme announced on the spot" from footnote to a quick fact for Collage and Pencil Sketch.
5. **F4** — no design fix. Add to the organizer question list: Fashion Show team size, and durations for Instrumental Music, Cooking Without Fire, G.K. Quiz.
6. **Phase 3 §8.A/§10.E** need a correction for the 4×4 assumption. Small edit, real inconsistency.

## 10. Stop conditions

None triggered. No constitution was violated, nothing was invented, and no flow depended on unknown payment rules — payment is untouched in Round 1.

**Round 2 (Event Detail → Registration Entry → Registration Flow) is not started and will not start without your approval.**
