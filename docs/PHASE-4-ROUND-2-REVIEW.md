# Phase 4 · Round 2 — Registration → Payment placeholder → Confirmation → Your Space

*Short by design. This phase makes interfaces, not constitutions.*

| | |
|---|---|
| **Artifact** | `wireframes/phase-4/round-2.html` — **v0** |
| **Screens** | P-04 handoff · P-06 · P-07 · P-08 · P-09 · P-10 (placeholder) · P-11 · P-12 · P-13 |
| **Test events** | **Solo Dance** (solo) and **Group Dance** (5–8 members) — the two extremes of the real roster range |
| **Status** | **Reviewed 2026-08-09 — NOT APPROVED. Blocked by one business rule (F9 / question A1). Round 3 not started.** |

> Registration is prototyped under an assumed **Registration Open** season. That is the only way to test it; the real season today is Announcement. The assumption is stated in the prototype banner rather than hidden.

---

## 1. What was prototyped

The full commitment path, clickable: event handoff → declare intent → your details (with team roster for team events) → agreements → review → payment placeholder → confirmation → Your Space. Plus the empty dashboard, the pause-and-resume path, and real inline validation with an error summary.

Two prototype controls: event (solo vs team) and **fees: unknown / if fees apply** — the second exists solely to prove a payment step can be inserted later without the flow changing shape.

## 2. What works

- **Solo and team read as native, not as variants.** Solo Dance never mentions a roster; Group Dance never apologises for having one.
- **Nothing is asked that was not declared.** Step 1 lists what is coming; every field that appears was named there.
- **The review restates the whole registration in one sentence** before the summary table — "You're registering for Group Dance as a team of 6 from [school]" — which is where commitment actually happens.
- **The amount is named at review and transacted at the next step.** The corrected order holds end to end.
- **Validation behaves:** inline messages in plain words, an error summary with a count, focus moved to the first bad field, `aria-invalid` set, nothing lost.
- **Pause and resume works** and returns to the event page rather than home, because that is where the rules are.

## 3. Findings

| # | Finding | Severity | Blocked on |
|---|---|---|---|
| **F8** | **The declared step count cannot be stated honestly.** Phase 3 §9 promises the participant a declared number of steps; §14.C says C-05 supports "4 or 5". But whether payment exists at all is unknown, so both numbers are invented. → **Amendment AM-05** applied: the declaration now reads *"Step N of 4, plus payment if fees apply"*, with the conditional step drawn as a visibly provisional marker. | **High** | Resolved in architecture |
| **F9** | **Is the person registering also a participant?** The roster labels Member 1 as "you", which assumes a student registering themselves. Phase 0 §2.2 documents a *coordinator* registering teams — and a coordinator is not a participant, so for them the roster is wrong by one person. **Phase 0 Q4** (who registers: school or individual) is unanswered. | **High** | **Organizer — Q4** |
| **F10** | **Team roster density.** Group Dance at its maximum of 8 members means 16 roster inputs plus 4 of your own — **20 fields on a phone**. It works, but it is the longest single screen in the platform by a wide margin. | Medium | Your decision |
| **F11** | **The payment screen cannot be completed by design.** Failure, pending and retry behaviour depend entirely on the gateway. Round 4 (system states) will not be able to finish the payment states either. | Medium | **Organizer** |
| **F12** | **Confirmation retrieval has no mechanism.** The receipt must be retrievable (Phase 2.5 invariant 2.4), but the only route is Your Space, which needs an account, and the auth model (C6) is unresolved. Today the reference number *is* the entire retrieval story. | **High** | **Auth decision** |

**F9 and F12 are the round's real output.** Both are the kind of gap that would have been invisible until implementation, and both are decisions rather than design problems.

## 4. Simulated usability evaluations

*Simulated, not validation. No real participant has seen this.*

| # | Scenario | Result |
|---|---|---|
| 1 | Register alone for Solo Dance | **Pass.** Four steps, no roster, no mention of teams anywhere. |
| 2 | Register a team of 6 for Group Dance as a coordinator | **Pass with a blocking ambiguity.** The flow completes, but F9 means we may be collecting five participants and one coordinator, or six participants. The interface cannot tell, and neither can the coordinator. |
| 3 | Reach review, go back and correct one name | **Pass.** Per-row Edit links return to the exact step; entered data survives; the review reflects the change. |
| 4 | Abandon, close browser, return, resume | **Pass.** The resume prompt names the event and the step. "Start over" is offered without penalty. |
| 5 | Arrive at payment with fees unknown | **Pass — and the most useful test in the round.** With fees unknown there is no payment step at all; review leads straight to confirmation, and the fee line reads "Not known. If a fee applies you will see it before paying." Switching the control to "if fees apply" inserts a fifth step and changes no other screen. The placeholder architecture is now demonstrated rather than asserted. |
| 6 | Return a week later to find your registration | **Pass structurally, fails in practice.** Your Space shows the registration, its reference and an honest "nothing new yet". But getting *into* Your Space needs auth that does not exist — F12. |

## 5. Accessibility

Labels above every input; `aria-required` and `aria-invalid` set; errors as text with a counted summary in `role="alert"`; focus moves to the first invalid field; the agreement checkbox is a real checkbox reachable by Space and never pre-checked; the continue button is disabled *with a written reason*; targets ≥44px; visible focus ring on both themes; reduced motion respected.

**One issue found and fixed during the round:** the error summary was initially rendered after the fields, so a screen-reader user met the errors before the summary. It now precedes the form, matching DOM order to reading order.

## 6. Density

Group Dance at 8 members is the worst case in the platform and it was tested first rather than last. It holds, but only because each member is a bounded block with two fields. No typography was shrunk. F10 records the length honestly rather than hiding it behind a smaller font.

## 7. EVOKE Test

| Question | Result |
|---|---|
| Generic form flow? | **No.** The declared-steps promise, the restatement sentence and the stamp are specific to this platform's contract. |
| Could another school reuse it unchanged? | **No** — it is shaped around this rulebook's team ranges and rules. |
| Is the loud rationed? | **Yes.** The only emphatic moment is the confirmation stamp, which is the one moment that earns it. |
| Does every element earn its place? | **Yes.** No field exists that Phase 3 §9 did not specify. |
| Identity survives logo removal? | **Still unprovable at this fidelity** — unchanged from Round 1, and expected until Phase 5. |

## 8. Decision log

| # | Decision | Reason | Rejected alternative |
|---|---|---|---|
| **D9** | Step count declared conditionally | A fixed count is an invented fact while fee existence is unknown | Saying "4 steps" and silently adding a fifth later |
| **D10** | Member 1 labelled "you" | The least-assuming reading for a student registering themselves; flagged rather than resolved | Adding a "are you participating?" field — that invents a requirement |
| **D11** | Amount shown at review, paid at next step | Money follows commitment (corrected §9.A) | Collecting payment before review |
| **D12** | `[AMOUNT]` shown as a literal token | Makes the gap visible and machine-searchable before launch | A plausible-looking number "for demo purposes" |
| **D13** | Reference number issued at confirmation | Something concrete to hold while auth is unresolved | Promising an account that does not exist |

## 9. Proposed changes — not applied

1. **F10** — consider collapsing completed roster members to a single summary line, so an 8-member team reads as a list rather than a wall. Structural change; needs approval.
2. **F9** — no design fix. Needs the Q4 answer. Until then the coordinator path should not be advertised.
3. **F12** — needs the auth decision. Options worth considering: a reference-number lookup with no account at all, which would remove the auth dependency from retrieval entirely.

## 10. Stop conditions

**One triggered, deliberately reported rather than worked around:** F9 meets the stop condition "team registration rules turn out to be underspecified for a real event". I did not invent a resolution — the prototype uses the least-assuming reading and flags the ambiguity in place.

## 11. Is Round 2 ready for approval?

**Reviewed and held.** Verdict 2026-08-09: prototype quality accepted (9.8/10); round **blocked by F9**, which is a product rule, not a design problem. The registration flow is frozen until question A1 is answered — see `ORGANIZER-QUESTIONS.md`. Accepted as passing: solo and team registration, declared steps, review-before-commitment, validation and accessibility, resume, unknown-payment handling, and the payment-insertion architecture (to be kept exactly as built). F10 remains a proposal, not an approved change; F11 and F12 remain pending decisions.

**Prototype assessment was: yes, as a prototype.** The flow is complete, honest and testable, and it surfaced three high-severity gaps that were previously invisible.

**But two of those gaps are now blocking Round 3 and beyond:** F9 (who registers) and F12 (how a receipt is retrieved) are decisions, not designs. Round 3 can proceed without them; implementation cannot.

**Round 3 is not started.**
