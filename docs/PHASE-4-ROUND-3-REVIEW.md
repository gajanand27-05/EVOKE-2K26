# Phase 4 · Round 3 — Supporting experiences

*Schedule · Support/FAQ · Announcements (stopped)*

| | |
|---|---|
| **Artifact** | `wireframes/phase-4/round-3.html` — **v0** |
| **Built** | P-14 Schedule (four season states, two densities) · P-16 Support/FAQ · P-19 hub |
| **Stopped** | Announcements — architecture contradiction, see F17 |
| **Untouched** | Rounds 1 and 2. Verified byte-identical to their commits |
| **Status** | **v0 complete — awaiting review. Round 4 not started.** |

---

## 1. What was prototyped

**Schedule (P-14)** across four states: not published (the honest current state), published, dense, and post-event archive. Density switches between 3 events and all 17 entries (16 events, with G.K. Quiz split into prelims and final). Includes parallel events, a *not yet scheduled* section for events confirmed without times, and cluster filtering.

**Support/FAQ (P-16)** — ten questions people actually ask, in four groups, with **two visibly distinct kinds of missing information**.

**Hub (P-19)** — the route in, reached from the footer rather than a permanent menu item.

Every time, date and venue is a literal `[TIME]` / `[VENUE]` token. Nothing on any screen could be mistaken for a confirmed date.

## 2. What worked

- **The two postures are the round's main result.** "Not announced yet" (dashed, warm) is a promise that an answer is coming. "Not in the rulebook" (solid, neutral) is a fact about the source. A participant reading *"How are ties decided? — not in the rulebook"* stops waiting; the same question under a generic grey "TBD" would leave them checking back forever.
- **The empty schedule still answers something.** It names what is missing, when it arrives, and redirects to per-event durations — the part that *is* knowable. No call to action beyond the way back; a participant who came for a date is allowed to leave (Phase 2 Part 23).
- **Parallel events read correctly** — "at the same time", plus a rule down the left edge. Never colour alone.
- **Not-yet-scheduled events have a home.** Two events sit in their own section rather than being hidden or given invented times.
- **One fact, one home held.** FAQ answers about materials and team sizes point at the event page instead of restating it.

## 3. What failed, or stopped

| # | Finding | Severity | Blocked on |
|---|---|---|---|
| **F17** | **Announcements has no home this round may touch.** The brief names "P-15 Announcements"; in Phase 3 **P-15 is About**, and announcements have no screen at all. Phase 2.5 §2.3 #2 bans a news/blog section outright, and §5.1 gives announcements exactly two homes: Your Space (frozen) and Welcome-latest (Round 1). Building it meant inventing a banned screen or editing a frozen one. **Stopped.** | **High** | Your decision |
| **F14** | **The escape hatch is missing.** Phase 2.5 §5.2 guarantees every doubt is one hop from its answer; Phase 2 Part 14 forbids dead ends. Both depend on a contact route that cannot exist while Q12 is unresolved. The FAQ is where the guarantee visibly breaks: an eleventh question has nowhere to go. | **High** | **Organizer — question B5** |
| **F18** | **"My events" and conflict warnings are blocked.** The brief asks the schedule to answer *"what do I need to care about?"* before showing everything. Filtering to a participant's own events needs the registration data model — frozen behind A1 — and a real conflict warning needs to know which events are theirs. Cluster filtering offered instead. | Medium | **A1** |
| **F15** | **A schedule without dates cannot be planned from.** Ordering, grouping, filtering and the unscheduled section all work; a participant can still plan nothing. The Approach season cannot honestly begin until dates and venue arrive. | Medium | **Organizer — C2, C3** |
| **F13** | **No Contact card in the hub.** Correct in isolation — publishing an affordance with nothing behind it is forbidden — but it is the same root cause as F14. | Medium | **Organizer — B5** |

## 4. Architecture assumptions tested

| Assumption | Result |
|---|---|
| Announcements need no dedicated screen (Phase 2.5 §2.3, §5.1) | **Contradicted by the round's own brief** — unresolved, F17 |
| Schedule is a standalone page reachable in one hop (Phase 3 §3.8) | **Held** |
| The quiet-corners hub prevents footer overcrowding (P-19) | **Held** — three cards, not five |
| Placeholder postures are sufficient (Phase 2.5 §11.1) | **Held, and extended.** The five postures cover *why* a fact is missing; this round found the participant also needs to know *whether it is coming*. "Honest wait" and "quiet gap" are architecturally different but were rendering identically. Now visually distinct |
| Text search rejected (AM-04) | **Held** — no search added; grouping was sufficient at ten questions |

**Amendments made: none.** F17 is an explicit structural ban, and a ban cannot be overturned by the agent that tripped over it. The proposal is in §11 for your decision.

## 5. Simulated usability evaluations

*Simulated, not validation. No real participant has seen this.*

| # | Scenario | Path | Hesitation | Result |
|---|---|---|---|---|
| 1 | When is my event? | Hub → Schedule | At the empty state | **Partial.** Learns the schedule is not published and when it will be — but cannot answer the actual question. Honest, not satisfying |
| 2 | Did anything change since last time? | Hub → Announcements | Immediately | **Fail — stopped.** F17. No route exists |
| 3 | Question about an event rule | Hub → FAQ → event page | None | **Pass.** FAQ answers in outline and points to the authoritative page |
| 4 | I can't find my answer | FAQ → Zone C | Terminal | **Fail.** "No route available" is honest and still a dead end. F14 |
| 5 | No announcements yet | — | — | **Untestable.** Blocked by F17 |
| 6 | Schedule not published | Hub → Schedule | None | **Pass.** The strongest empty state in the platform so far |
| 7 | Scan several entries on mobile | Schedule, all 17 | At the third parallel block | **Pass with a caveat.** Time tokens stack above names on mobile; scanning works but is slower than the desktop two-column read |
| 8 | Return to the event I was exploring | FAQ → back → hub | None | **Pass.** Back is named, not generic |

**Four pass, two fail, one partial, one untestable.** Both outright failures are missing organizer facts, not design defects.

## 6. Accessibility

Heading hierarchy one `<h1>` per screen; accordions use real buttons with `aria-expanded`/`aria-controls`; filter chips are `aria-pressed`; result counts announced via `role="status"`; postures carry text, never colour alone; parallel events marked in words plus a border; targets ≥44px; focus visible on both themes; focus moves to the heading on navigation; reduced motion respected.

**One thing to watch:** the posture tags sit *inside* the accordion button, so a screen reader announces "Is there an entry fee? not announced yet" as one label. That reads well, but it means the posture cannot be styled as decorative later without losing it from the accessible name.

## 7. Mobile and density

Sparse (3 entries) and full (17) both hold. At 17 the schedule is long but scannable because day headers and the unscheduled section break it. On mobile each slot stacks time above name — correct for narrow widths, marginally slower to scan, recorded rather than fixed by shrinking type. FAQ answers were written at realistic lengths, from one line to four.

## 8. EVOKE Test

| Question | Result |
|---|---|
| Could this be a generic school FAQ? | **No.** The two-posture distinction is specific to a platform built on a previous edition's rulebook with an absent organizer |
| A generic event calendar? | **No.** It refuses to show a time it does not have, which every generic calendar does by default |
| A generic announcement feed? | **N/A** — not built |
| Restraint preserved? | **Yes.** No CTAs beyond the way back; empty states do not sell |
| Signature Language | **Cannot be assessed at this fidelity** — unchanged from Rounds 1 and 2, and will remain so until Phase 5 |

## 9. Cross-round regression

Verified programmatically, not by eye:

| Check | Result |
|---|---|
| Cluster distribution 6 / 2 / 5 / 3 | **PASS** |
| Adaptive judging logic intact | **PASS** |
| No fabricated judging criteria | **PASS** |
| TBD honesty intact | **PASS** |
| No search field | **PASS** |
| Rounds 1 and 2 files byte-identical to commits | **PASS** |

## 10. Remaining organizer dependencies

| Question | Now blocking |
|---|---|
| **B5** — official contact | F13, F14. The platform has no doubt-home at all. This has become the most damaging single gap |
| **C2 / C3** — dates and venue | F15. The schedule is structure without usefulness |
| **A1** — registrant identity | F18, plus all of Round 2 |
| **A2** — retrieval | The FAQ answer about finding your registration |
| **A3** — multiple events | The FAQ answer about entering more than one event |

**B5 has overtaken A1 in practical damage.** A1 freezes one round; B5 breaks a guarantee that spans the whole platform.

## 11. Proposed changes — NOT applied

1. **F17 — the announcements decision.** Three options, all yours:
   - **(a) Leave it as architected.** Announcements stay in Your Space and Welcome-latest. Consequence: only registered participants ever see them, so nothing can be announced to a prospective entrant.
   - **(b) Add a public announcements page** via the Phase 3 Part 3 page-contract process. Requires overturning Phase 2.5 §2.3 #2 in writing.
   - **(c) Extend Welcome-latest** to a small "recent updates" list on the Welcome screen — no new page, no blog, but visible before registering. *This looks like the smallest honest change, but it touches a Round 1 screen and so needs approval.*
2. **F14** — no design fix. Needs B5.
3. **Mobile schedule scanning** — a compact two-line variant could speed it up. Not applied; unproven whether it helps or merely compresses.

## 12. Readiness

**Round 3 is two-thirds complete and honest about the third.**

Schedule and Support are built, tested and ready for review. Announcements is stopped on a genuine architecture contradiction that requires a decision rather than a design.

The round did what it was meant to: it made the platform's two kinds of silence distinguishable, and it found that the support experience — the one place a participant goes when everything else has failed — currently ends in a wall.

**Round 4 not started. Round 2 untouched.**
