# EVOKE 2K26 - Phase 3: Interface Architecture Specification
*Parts 1-17: Master Screen Inventory · Screen Relationship Map · Wireframe Blueprint · Component Inventory · Component Relationships · Responsive Behaviour · State Architecture · Accessibility Architecture · Form Architecture · Search & Discovery · Navigation · Error/Empty/Loading States · Interaction Blueprint · Developer Contract · Designer Contract · Validation · Phase 3 Readiness*

| | |
|---|---|
| **Project** | EVOKE 2K26 - Participant & Registration Platform (Inter-School Festival) |
| **Phase** | 3 - Interface Architecture (NOT UI design, NOT code, NOT wireframes) |
| **Documents in force** | Phase 0 Discovery · Phase 1 Brand Bible · Phase 1.5 Creative Review + Appendix A · Phase 1.75 Product Charter · Phase 2 Experience Direction · Phase 2.5 Structural Architecture (all immutable) |
| **Status** | Draft for review - implementation begins only after approval |

> This document defines every screen that exists in the platform, how screens connect, and what structure each screen carries. It is the translation of five constitutions into operational structure. Nothing here is design - every screen is a solved user problem. Every zone answers a constitution mandate.
>
> **The Golden Question** (Phase 2.5): *Why does this exist? Why now? Why here? Why not somewhere else? Why should the user care?*
>
> **The One Last Rule:** nothing exists because it looks good. Everything exists because it improves clarity, confidence, trust, or progress.

---

## AMENDMENT LOG

This specification is a hypothesis until it meets real content. Where a Phase 4 prototype has falsified an assumption made here, the assumption is corrected in place *and* recorded below. The prototype never silently compensates for an architectural error — the architecture is amended, then the prototype follows.

| # | Date | Amendment | Falsified by | Sections changed |
|---|---|---|---|---|
| **AM-01** | 2026-08-09 | **Tab order is positional, not numbered.** The P-03 keyboard journey enumerated absolute tab indices assuming four tiles per cluster. Tile counts are a property of content, not interface. | Phase 4 Round 1 — real cluster sizes are Stage 6 · Mind 2 · Art 5 · Maker 3 | §8.A |
| **AM-02** | 2026-08-09 | **The "4 clusters × 4 events" model is withdrawn.** Cluster sizes are uneven and the layout must absorb that. Choice reduction comes from *naming* four groups, not from their being equal. A fixed 2×2 cluster grid is no longer specified. | Phase 4 Round 1 | §3 (P-03 blueprint), §6.B |
| **AM-03** | 2026-08-09 | **Zone E is adaptive, not fixed two-column.** Judging criteria exist in the source for only 6 of 16 events. Two columns appear only when both blocks have content; an empty second column is forbidden, because a hollow box implies withheld information. Criteria are never fabricated to fill it. | Phase 4 Round 1 | §3 (P-04 blueprint), §6.D, §5.4, §5.6 |
| **AM-04** | 2026-08-09 | **Text search re-evaluated against real content and still rejected** for the curated 16-event catalogue. Re-opened only if the catalogue grows substantially. | Phase 4 Round 1 | §10.A |
| **AM-05** | 2026-08-09 | **The declared step count is conditional, and must be worded as such.** §9 promises the participant a declared number of steps, and C-05 was specified to support "4 or 5". But whether a payment step exists at all is unknown (Charter §7), so neither "4 steps" nor "5 steps" can be stated honestly today. The declaration is therefore **"Step N of 4, plus payment if fees apply"**, with the conditional step shown as a distinct, visibly provisional marker. When fees are resolved the wording collapses to a fixed count with no structural change. | Phase 4 Round 2 | §9.A, §9.D, Part 4 C-05 |

**Not amended:** the cluster concept itself, which real content supports. Phase 0 §3.4 always recorded the true distribution — the 4×4 error was introduced at Phase 3, not inherited.

---

## PART 1 - MASTER SCREEN INVENTORY

The 11 page contracts from Phase 2.5 expand into practical screens. Multi-step flows become screens. Error states, loading states, and administrative views are included because the platform must be operational end-to-end, not aspirational.

**Screen categories:**
- **P** = Primary (part of the participant journey)
- **S** = System (auth, loading, error - invisible when healthy)
- **A** = Admin (organizer-only)
- **F** = Future (reserved, not built this season)

**Season availability codes:**
- **A** = Announcement · **R** = Registration Open · **P** = Approach · **L** = Live · **E** = Post-Event

---

### SCREEN P-01: Welcome Beat (Landing)

| Field | Definition |
|---|---|
| **Purpose** | Answer "What is EVOKE 2K26?" in one screen of reading and hand the visitor forward. (Phase 2.5 §3.1; Charter §3 step 1) |
| **Audience** | First-time visitors (students), parents, coordinators arriving cold |
| **Entry states** | Direct link (print/WhatsApp/QR); Google search; social media; direct URL |
| **Exit states** | → Landscape (primary); → Quiet Corners (About/FAQ); → Your Space (registered return) |
| **Dependencies** | A2 (tagline), A1 (festival description), G1 (season state), B11 (registration status) |
| **Primary action** | "Explore Events" → Landscape |
| **Secondary actions** | View About; View FAQ |
| **Success state** | Visitor knows what EVOKE is, the season state is honest, and the forward path is visible - within one screen of reading (Phase 2 Cognitive Load: Very Low → Low) |
| **Failure state** | Season = Announcement or Closed → honest status displayed; "Explore Events" is disabled, replaced by "Coming Soon" (Phase 2 Part 14; no dead ends) |
| **Season availability** | A · R · P · L · E (always exists, content varies by season) |
| **Constitutional trace** | Phase 0 §6.1 Home; Phase 2 Parts 1, 4, 12; Charter §3 step 1-2; Phase 2.5 §3.1 |
| **Golden Question** | Exists because every journey starts with "what is this?" Here because it is the first screen. Now because arrival demands orientation. Not elsewhere because no other screen is the front door. The user cares because confusion is the first enemy. |

---

### SCREEN P-02: Welcome Beat - Announcement State

| Field | Definition |
|---|---|
| **Purpose** | When the season = Announcement: hold the promise without selling. Show identity, state that details are coming, and leave the visitor with a known reason to return. |
| **Audience** | First-time visitors during the Announcement season |
| **Entry states** | Direct link; search; social share |
| **Exit states** | → Landscape (read-only preview); → About; → return later |
| **Dependencies** | A1-A3 (identity), G1 (season = Announcement), B1 (event list exists, preview-ready) |
| **Primary action** | "View Events" (read-only preview) → Landscape |
| **Secondary actions** | Share the announcement |
| **Success state** | Visitor understands EVOKE exists, sees it is pre-registration, and knows when to return |
| **Failure state** | N/A - the screen's job is to wait. Honest "Registration opens soon" posture (Phase 2.5 §11.1) |
| **Season availability** | A only |
| **Constitutional trace** | Phase 2 Part 12.1 entry states; Phase 2.5 §8.1; Charter §7 placeholders |
| **Golden Question** | Exists because the Announcement season needs a distinct posture (Phase 2.5 Part 8). Here because it is the arrival screen. Not the main Welcome because the promise is different: "I'm coming" vs "Register now." |

---

### SCREEN P-03: Landscape (Event List)

| Field | Definition |
|---|---|
| **Purpose** | Display the full store of 16 (or N) choices, cluster-grouped (Stage/Mind/Art/Maker), with honest status, so students can find their events. (Phase 2.5 §3.2; Phase 2 Part 3.3) |
| **Audience** | Students at intent-building; coordinators scanning clusters |
| **Entry states** | From Welcome Beat (primary); from search; from social share; from Your Space (cross-entry) |
| **Exit states** | → Event Detail (primary); → Rules & Eligibility (coordinators); → Welcome Beat (back) |
| **Dependencies** | B1 (event list), B2 (cluster tags), B11 (registration status per event) |
| **Primary action** | Select an event → Event Detail |
| **Secondary actions** | Filter by cluster; View Rules & Eligibility |
| **Success state** | Student narrows 16 events to a shortlist of 1-3 within a scanning session (Phase 2 Curiosity Curve: Peak at Landscape) |
| **Failure state** | Screen overwhelms → clusters prevent this (Phase 2 Part 3.3). All events closed → honest status per event; Landscape remains useful (Phase 2 Part 14) |
| **Season availability** | A · R · P · L · E (all seasons; in Announcement = read-only preview; in Post-Event = archive) |
| **Constitutional trace** | Phase 0 §3.1, §4.17; Phase 2 Parts 3, 5; Phase 2.5 §3.2; Charter §3 step 2-3 |
| **Golden Question** | Exists because "what can I do?" is the second question of every journey. Here because it follows identity. Not on Welcome because it overloads. The user cares because this is where they find "their" event. |

---

### SCREEN P-04: Event Detail (Generic template for all 16 events)

| Field | Definition |
|---|---|
| **Purpose** | Remove every doubt about ONE event so the student can choose it with certainty. The highest-stakes screen in the platform. (Phase 2.5 §3.3; Phase 2 Parts 9-10; Charter §3 steps 3-5) |
| **Audience** | Students deciding; coordinators verifying; parents checking |
| **Entry states** | From Landscape (primary); from search; from Your Space shortlist; from direct share link; from QR code |
| **Exit states** | → Registration (decision made); → Landscape (more options); → Rules & Eligibility (coordinator context); → Contact (doubt) |
| **Dependencies** | B3-B12 (personality, quick facts, theme, eligibility, rules, judging, materials, FAQ, registration status, requirements); G1 (season state) |
| **Primary action** | "Register for This Event" → Registration (when status = open) |
| **Secondary actions** | Back to Landscape; View general rules; Contact organizer |
| **Success state** | Student can answer "Do I want this? Can I do it? What do I need?" with zero remaining questions (Phase 2 Progressive Confidence: Certainty at event detail) |
| **Failure state** | Registration closed → honest status + alternatives (Phase 2 Part 14). Rule raises new question → FAQ or Contact is visible. Missing information → honest placeholder, never silence (Phase 2.5 §11.1) |
| **Season availability** | A · R · P · L · E (all seasons; in Approach = adds schedule link; in Post-Event = shows results if available) |
| **Constitutional trace** | Phase 0 §3.1, §4.x, §6.5; Phase 2 Parts 7, 9-10; Phase 2.5 §3.3; Charter §3 steps 3-5; Charter §5 |
| **Golden Question** | Exists because certainty is earned from rules, not sold by energy (Phase 2 Part 2.2). Here because the student has chosen an event. Not on Landscape because density kills scanning. The user cares because this screen decides whether they participate. |

---

### SCREEN P-05: Rules & Eligibility (General)

| Field | Definition |
|---|---|
| **Purpose** | The coordinator contract - general rules, quota policy, cross-event eligibility, and the link to per-event details. One place, faithful wording. (Phase 2.5 §3.4) |
| **Audience** | Coordinators primarily; parents; students cross-checking |
| **Entry states** | From Welcome Beat; from Landscape (coordinator path); from Event Detail |
| **Exit states** | → specific Event Detail; → Registration; → back to referencing page |
| **Dependencies** | C1 (general rules), B6 (eligibility policy), B1 (event list for cross-referencing) |
| **Primary action** | Link to a specific Event Detail (to see per-event rules) |
| **Secondary actions** | Start registration; Contact organizer |
| **Success state** | Coordinator can confirm "We may participate, and under which quotas" without contradictions |
| **Failure state** | TBD content (Q5, Q10) → honest placeholder with posture; never presented as fact (Phase 2.5 §11.1) |
| **Season availability** | A · R · P · L · E (always available; content is stable across seasons) |
| **Constitutional trace** | Phase 0 §2.2, §3.3; Phase 2 Part 10.1; Phase 2.5 §3.4, §5.1; Bible Constitution 19 |
| **Golden Question** | Exists because coordinators need the full contract before registering teams. Here as a separate page so it does not pollute event detail with general rules. Not inline because coordinators need the full picture. |

---

### SCREEN P-06: Registration - Step 1: Declare Intent

| Field | Definition |
|---|---|
| **Purpose** | The doorway opens: restate what the participant chose (event, team format) and declare the steps ahead. Nothing surprising (Phase 2 Part 10.2-10.3). |
| **Audience** | Students; coordinators registering teams |
| **Entry states** | From Event Detail ("Register" action) |
| **Exit states** | → Registration Step 2 (forward); → Event Detail (back out) |
| **Dependencies** | B11 (registration status = open), B12 (registration requirements), C2 (flow steps), C4 (data fields declaration) |
| **Primary action** | "Continue" → Step 2 |
| **Secondary actions** | Go back to event; View rules again |
| **Success state** | Participant sees: here is what I registered for, here is what I will be asked, here is what happens after - no surprises |
| **Failure state** | Registration closed → honest close message with alternatives (Phase 2 Part 14). Session expired → resume prompt |
| **Season availability** | R only |
| **Constitutional trace** | Phase 2 Parts 10.2-10.3; Phase 2.5 §3.5; Charter §3 step 6; Charter §5 |
| **Golden Question** | Exists because "nothing asked may be a surprise." Here because it is the registration threshold. The user cares because they are committing - they need a restatement of choice before being asked for data. |

---

### SCREEN P-07: Registration - Step 2: Participant Information

| Field | Definition |
|---|---|
| **Purpose** | Collect participant/school identity: name(s), school, class, team members (if team event). Only what was declared in Step 1. |
| **Audience** | Students entering individual data; coordinators entering team data |
| **Entry states** | From Registration Step 1 |
| **Exit states** | → Registration Step 3 (forward); → Registration Step 1 (back to edit) |
| **Dependencies** | C4 (data fields - TBD), B6 (eligibility constraints - Q5) |
| **Primary action** | "Continue" → Step 3 |
| **Secondary actions** | Back to edit; Pause and save (resume later - Phase 2 Part 14) |
| **Success state** | Information captured with inline validation; no field asked was not declared |
| **Failure state** | Validation error → inline, in Ringmaster voice (Phase 2 Part 14.3). Ineligible → honest message + nearest alternative |
| **Season availability** | R only |
| **Constitutional trace** | Phase 2 Part 10.3; Phase 2.5 §3.5; Charter §7 (fields TBD) |
| **Golden Question** | Exists because the platform must collect identity. Here after intent declaration so the user understands what is being asked. |

---

### SCREEN P-08: Registration - Step 3: Declaration & Agreement

| Field | Definition |
|---|---|
| **Purpose** | The participant acknowledges key rules: originality, decency, time limits, "judges' decision is final," and any TBD requirements. Not a legal wall - a confirmation that they read the essentials. |
| **Audience** | All registrants |
| **Entry states** | From Registration Step 2 |
| **Exit states** | → Registration Step 4 (forward); → Step 2 (back) |
| **Dependencies** | B7 (rules - summary only, link to full), B8 (judging criteria - reference), C3 (payment facts if applicable - TBD) |
| **Primary action** | "I understand. Continue." → Step 4 |
| **Secondary actions** | Back to edit; View full rules (link to Event Detail) |
| **Success state** | Participant acknowledges key commitments before reaching the final review |
| **Failure state** | Participant declines → flow gracefully exits to Event Detail; no penalty (Phase 2 Part 14) |
| **Season availability** | R only |
| **Constitutional trace** | Phase 2 Part 10.2; Phase 0 §3.3 (rules as contract); Phase 2.5 §3.5 |
| **Golden Question** | Exists because trust requires explicit acknowledgement, not assumed compliance. Here before the review step so the participant enters the final mirror with full knowledge. |

---

### SCREEN P-09: Registration - Step 4: Review & Confirm

| Field | Definition |
|---|---|
| **Purpose** | The final mirror: restate everything in one view - event, participants, team, agreed rules - and offer the final yes/no decision. |
| **Audience** | All registrants |
| **Entry states** | From Registration Step 3 |
| **Exit states** | → Registration Step 5 (submit); → Step 2 (edit information); → Event Detail (cancel) |
| **Dependencies** | C4 (all collected data), B11 (registration status), C3 (payment if applicable - TBD) |
| **Primary action** | "Confirm Registration" → Submit (Step 5) |
| **Secondary actions** | Edit details; Cancel and return to event |
| **Success state** | Participant reads their registration and clicks "yes" - the act is clear, complete, final |
| **Failure state** | Participant cancels → no penalty, returns to Event Detail. Error on submit → retry one action, data persists (Phase 2 Part 20.2) |
| **Season availability** | R only |
| **Constitutional trace** | Phase 2 Part 10.2 (restatement of choice); Phase 2.5 §3.5; Charter §3 step 6 |
| **Golden Question** | Exists because the last thought before committing must be "yes" (Phase 2 Part 10.2). Here after all steps so nothing is hidden. |

---

### SCREEN P-10: Registration - Step 5: Payment (TBD Placeholder)

| Field | Definition |
|---|---|
| **Purpose** | The money moment, released only when official payment information exists. Complete, unhurried, fully explained. (Phase 2 Part 15.4; Charter §7) |
| **Audience** | All registrants (if fees apply) |
| **Entry states** | From Registration Step 4 (Review) |
| **Exit states** | → Confirmation (success); → Registration Step 4 (back); → Contact (doubt) |
| **Dependencies** | C3 (payment facts - TBD), payment gateway (TBD) |
| **Primary action** | "Pay and Complete" → Confirmation (when resolved) |
| **Secondary actions** | Back; View payment details; Contact |
| **Success state** | Payment completes → Confirmation screen |
| **Failure state** | Payment failed → calm, unhurried state: "no double-charge" stated plainly, retry one action, entered data is not lost, contact path exists (Phase 2 Part 14.2); Payment pending → visible in Your Space, explained (Phase 2 Part 14) |
| **Season availability** | R only (structure exists; content is P-gated by Charter §7) |
| **Constitutional trace** | Phase 2 Part 15.4; Charter §3 step 7, §7; Phase 2.5 §3.5 |
| **Golden Question** | Exists because TBD registration may include fees. Here after the review step - money comes after commitment, never before. The user cares because payment is the highest-trust moment. |

> **Note on P-10:** This screen is structural. It is built with placeholder-tolerant architecture (Charter §7). If TBD resolves to "no fees," this screen is omitted and Step 4 goes directly to Confirmation.

---

### SCREEN P-11: Confirmation

| Field | Definition |
|---|---|
| **Purpose** | The receipt - the promise kept, the beginning of anticipation. Memory Anchor #5: The Stamp. (Phase 2.5 §3.6; Phase 2 Part 19.2) |
| **Audience** | Registered student and coordinator |
| **Entry states** | End of Registration flow (P-09 or P-10) |
| **Exit states** | → Your Space (primary); → Landscape (register more events); → Print/Share |
| **Dependencies** | C5 (confirmation record), C6 (participant identity - placeholder auth) |
| **Primary action** | "Go to Your Space" |
| **Secondary actions** | Register another event; Print/Share confirmation; View what's next |
| **Success state** | Participant holds a stamped record of what they registered for, knows what happens next, and has a home to return to |
| **Failure state** | N/A - if you reached this screen, it worked. Retrievability: record is always reachable via Your Space (Phase 2.5 invariant 2.4) |
| **Season availability** | R · P · L (post-registration; in Post-Event = memorial state) |
| **Constitutional trace** | Phase 2.5 §3.6; Phase 2 Parts 10.4, 12.2, 18-19; Charter §3 steps 8-9; Phase 1.5 Part 6.4 (Stamp) |
| **Golden Question** | Exists because commitment needs a receipt (Phase 2 Part 19). Here because the flow ends here. The user cares because "I'm in" must be undeniable. |

---

### SCREEN P-12: Your Space (Participant Dashboard)

| Field | Definition |
|---|---|
| **Purpose** | The return engine - everything a registered participant needs across the season, always showing what changed since the last visit. (Phase 2.5 §3.7; Phase 2 Part 12.2) |
| **Audience** | Registered students and coordinators only |
| **Entry states** | Login (placeholder auth - C6); post-registration hand-off; recovery from email/WhatsApp link |
| **Exit states** | → Landscape (register more, if open); → Schedule (approach/live); → Event Detail (check rules) |
| **Dependencies** | C5 (registrations), C6 (identity/profile), C7 (status changes), D1 (announcements), G1 (season state) |
| **Primary action** | "What changed" - the delta since last visit (C7) |
| **Secondary actions** | View registrations; View announcements; Go to Schedule; Edit profile |
| **Success state** | Every visit gives one clear "what now?" - the participant is oriented in time and knows their next beat (Phase 2 Part 8.3) |
| **Failure state** | No registrations → "You haven't registered yet" + path to Landscape (not a dead end). Login fails → recovery path (Phase 2 Part 14) |
| **Season availability** | R · P · L · E (after first registration; in Announcement = not yet accessible - no auth yet) |
| **Constitutional trace** | Phase 2.5 §3.7; Phase 2 Parts 8.3, 12.2, 19; Phase 0 §12.5 (announcements as source of truth) |
| **Golden Question** | Exists because the participant journey continues after registration (Phase 2 Part 19). Here because it is the only screen that needs auth - value before gate, never gate before value. |

---

### SCREEN P-13: Your Space - Empty State

| Field | Definition |
|---|---|
| **Purpose** | The "waiting slip" (Phase 1.5 Part 11.1.6) - when the participant has logged in but has no registrations. Negative space is the message: this slip waits for their name. |
| **Audience** | Logged-in visitors with no registrations |
| **Entry states** | Login with no existing registrations |
| **Exit states** | → Landscape (go find events) |
| **Dependencies** | C5 (empty), G1 (season state) |
| **Primary action** | "Explore Events" → Landscape |
| **Secondary actions** | N/A |
| **Success state** | Participant understands they are in the right place and knows how to start |
| **Failure state** | N/A |
| **Season availability** | R · P · L · E |
| **Constitutional trace** | Phase 1.5 Part 11.1.6; Phase 2.5 §3.7 failure state |
| **Golden Question** | Exists because the slip universality test (Phase 1.5 §11.2) requires empty states to use the slip language. Here because it is the dashboard's starting state. |

---

### SCREEN P-14: Schedule

| Field | Definition |
|---|---|
| **Purpose** | Logistics for the approach and live seasons - when and where each event runs, links to event details. (Phase 2.5 §3.8; Phase 2 Part 21) |
| **Audience** | Registered participants, coordinators, parents |
| **Entry states** | From Your Space; from Event Detail (during approach); from Quiet Corners |
| **Exit states** | → specific Event Detail; → Your Space |
| **Dependencies** | D2 (schedule - placeholder), G1 (season state), B11 (status) |
| **Primary action** | View per-event timing (scrollable/filters by cluster) |
| **Secondary actions** | Link to Event Detail; Filter by cluster |
| **Success state** | A participant can plan their day (coordinator) or understand their slot timing (student) |
| **Failure state** | TBD schedule (Q6) → honest posture: "Schedule will be published during the Approach phase." Not published as final when unconfirmed (Phase 2.5 §8.1) |
| **Season availability** | P · L (during Announcement and Registration = honest placeholder; in Post-Event = archive) |
| **Constitutional trace** | Phase 0 §Q6; Phase 2 Part 21; Phase 2.5 §3.8; Phase 2.5 §8.1 |
| **Golden Question** | Exists because logistics trust requires a time layout. Here as its own page - not embedded in event detail - so it is one hop from any return visit. |

---

### SCREEN P-15: Quiet Corners - About

| Field | Definition |
|---|---|
| **Purpose** | Answer "who runs this?" - host school/college, festival history, what EVOKE stands for. Builds trust for parents and newcomers. (Phase 2.5 §3.9) |
| **Audience** | Parents, newcomers, sponsors, media |
| **Entry states** | From Welcome Beat; from footer (any page); from search |
| **Exit states** | → back to referencing context; → Contact |
| **Dependencies** | A4 (host - P), A8 (history - F), A1-A3 (identity - pulled, not duplicated) |
| **Primary action** | Read; build trust |
| **Secondary actions** | Contact organizer; View FAQ |
| **Success state** | Parent or newcomer can confirm "this is official and appropriate" - reassurance (Phase 0 §2.3) |
| **Failure state** | Host TBD (Q19) → honest placeholder; do not invent an institution |
| **Season availability** | A · R · P · L · E (always available) |
| **Constitutional trace** | Phase 0 §2.3, §6.1; Phase 2 Part 15; Phase 2.5 §3.9 |
| **Golden Question** | Exists because trust Architecture (Phase 2 Part 15.1) demands official presence. Here in quiet corners because it answers doubt, not curiosity. |

---

### SCREEN P-16: Quiet Corners - FAQ

| Field | Definition |
|---|---|
| **Purpose** | Global FAQ: cross-event, cross-audience questions that don't belong to any single event page. (Phase 2.5 §3.9) |
| **Audience** | Everyone, especially parents and coordinators |
| **Entry states** | From any page (footer); from Welcome Beat; from quiet corners hub |
| **Exit states** | → back to referencing context; → specific Event Detail (if event-specific question) |
| **Dependencies** | E1 (global FAQ), B10 (event FAQ - linked, not duplicated per 2.5 §9.1) |
| **Primary action** | Find an answer |
| **Secondary actions** | Contact organizer; View specific event rules |
| **Success state** | Doubt answered in one hop. If question is event-specific, linked to the event's own FAQ |
| **Failure state** | Unanswered question → Contact route visible; no empty FAQ items (Phase 2.5 §10.1) |
| **Season availability** | A · R · P · L · E (always available; content evolves organically) |
| **Constitutional trace** | Phase 0 §6.2; Phase 2 Part 15; Phase 2.5 §3.9, §9.1 |
| **Golden Question** | Exists because cross-event questions exist that belong to no single event. Here in quiet corners, not on the main path - accessed when doubt arises. |

---

### SCREEN P-17: Quiet Corners - Contact

| Field | Definition |
|---|---|
| **Purpose** | The doubt-home - a real contact path to the organizer. Every failure journey eventually leads here. (Phase 2.5 §3.9; Phase 2 Part 15.2) |
| **Audience** | Everyone |
| **Entry states** | From any page (footer, recovery paths); from Failure states; from FAQ |
| **Exit states** | → back to referencing context |
| **Dependencies** | A7 (contact person - P), E2 (contact route - P) |
| **Primary action** | Reach a human |
| **Secondary actions** | View FAQ (if question is answered there) |
| **Success state** | Visitor has a real channel to reach the organizer - trust is maintained even when automated answers fail |
| **Failure state** | Contact TBD (Q12) → honest placeholder (Phase 2.5 §11.1: if no real contact, the affordance is not published - rather than invent one) |
| **Season availability** | A · R · P · L · E (always available when contact is resolved) |
| **Constitutional trace** | Phase 0 §Q12; Phase 2 Part 14.2, 15.2; Phase 2.5 §3.9, §10.1 |
| **Golden Question** | Exists because every doubt needs a human path. Here in quiet corners, not on the main path - always findable from the footer, never intrusive. |

---

### SCREEN P-18: Quiet Corners - Privacy

| Field | Definition |
|---|---|
| **Purpose** | Student-data trust - how participant data is handled, stored, and used. Required by Phase 0 Risk 14. |
| **Audience** | Parents, coordinators |
| **Entry states** | From footer; from Registration flow (link to full privacy policy) |
| **Exit states** | → back to referencing context |
| **Dependencies** | E3 (privacy note), C4 (data fields - links to what is collected) |
| **Primary action** | Read; verify trust |
| **Secondary actions** | Contact organizer with privacy questions |
| **Success state** | Parent or student can confirm their data is handled responsibly |
| **Failure state** | Content TBD → honest posture; do not omit (structural requirement) |
| **Season availability** | A · R · P · L · E (always available) |
| **Constitutional trace** | Phase 0 Risk 14; Phase 2.5 §3.9 |
| **Golden Question** | Exists because student data trust is a non-negotiable (Phase 0 Risk 14). Here because it answers a specific doubt, not a curiosity. |

---

### SCREEN P-19: Quiet Corners - Hub

| Field | Definition |
|---|---|
| **Purpose** | Single entry point into the quiet corners - routes to About, FAQ, Contact, Privacy. Prevents footer clutter from becoming a menu of decisions. |
| **Audience** | Everyone |
| **Entry states** | From footer "Info" or "More" link (any page) |
| **Exit states** | → About (P-15); → FAQ (P-16); → Contact (P-17); → Privacy (P-18) |
| **Dependencies** | A4-A7, E1-E3 (all quiet corner objects, as links) |
| **Primary action** | Choose a topic |
| **Secondary actions** | N/A |
| **Success state** | Visitor navigates to their specific question area in one tap |
| **Failure state** | N/A - all links are to real or honestly-placeholdered screens |
| **Season availability** | A · R · P · L · E |
| **Constitutional trace** | Phase 2.5 §3.9; Phase 0 §6.2 (information priority) |
| **Golden Question** | Exists because quiet corners are four screens, not one - the hub prevents the footer from becoming a decision grid. Here as the footer anchor. |

---

### SCREEN P-20: Post-Event - Gallery (Future)

| Field | Definition |
|---|---|
| **Purpose** | Social proof; future-participant magnet. What EVOKE looked like. (Phase 2.5 §3.10) |
| **Audience** | Future participants, parents, media |
| **Entry states** | From post-event Welcome Beat; from Your Space (post-event); from social |
| **Exit states** | → Welcome Beat; → Winners |
| **Dependencies** | D3 (gallery/photos - F), Q14 (photography - [MISSING]) |
| **Primary action** | Browse |
| **Secondary actions** | Share; See winners |
| **Success state** | "I was part of this" or "I want to be next time" |
| **Failure state** | Not built until content exists (F-gate, Phase 2.5 §8.1) - no empty gallery |
| **Season availability** | E only (reserved; not built until photography exists) |
| **Constitutional trace** | Phase 0 §5.5, Q14; Phase 2.5 §3.10 |
| **Golden Question** | Exists because memory anchors require evidence (Phase 2 Part 18.2). Here in post-event only - never before the event, always after. |

---

### SCREEN P-21: Post-Event - Winners (Future)

| Field | Definition |
|---|---|
| **Purpose** | The verdict - winners announced with the Stamp gesture (Phase 1.5 Part 6.4). Evidence that EVOKE keeps its promises. |
| **Audience** | Everyone, post-event |
| **Entry states** | From post-event Welcome Beat; from Gallery; from social |
| **Exit states** | → Gallery; → Welcome Beat |
| **Dependencies** | D4 (winners/results - F) |
| **Primary action** | View results |
| **Secondary actions** | Share; View gallery |
| **Success state** | Winners visible, results honest, the Stamp is earned |
| **Failure state** | Not built until content exists (F-gate) |
| **Season availability** | E only |
| **Constitutional trace** | Phase 2 Part 18.2; Phase 1.5 Part 6.4; Phase 2.5 §3.10 |
| **Golden Question** | Exists because "judges' decision is final" needs a home. Here in post-event only - never before the verdict. |

---

### SCREEN P-22: Login (Authentication)

| Field | Definition |
|---|---|
| **Purpose** | Gate to Your Space - authenticate a registered participant. Value before gate: login is offered only after the participant knows what they get. (Phase 2.5 §10.1) |
| **Audience** | Registered participants only |
| **Entry states** | From Your Space link (footer or Welcome Beat); from recovery email link |
| **Exit states** | → Your Space (success); → Login (retry on failure); → Contact (recovery) |
| **Dependencies** | C6 (participant identity - placeholder auth) |
| **Primary action** | "Login" |
| **Secondary actions** | "Forgot credentials" (recovery path - Phase 2 Part 14); Back to Welcome Beat |
| **Success state** | Participant reaches Your Space |
| **Failure state** | Wrong credentials → recovery path stated in place, honest voice, no blame (Phase 2 Part 14.3); Session expired → resume, not reset |
| **Season availability** | R · P · L · E (not in Announcement - no auth yet) |
| **Constitutional trace** | Phase 2.5 §3.7, §10.1; Phase 2 Part 12.2; Charter §7 (auth TBD) |
| **Golden Question** | Exists because Your Space needs a boundary. Here between public and private. Not before browsing - the platform does not gate value. |

---

### SCREEN P-23: Network Error

| Field | Definition |
|---|---|
| **Purpose** | Calm, informed, hopeful recovery from network failure. No dead ends (Phase 2 Part 14). |
| **Audience** | All visitors |
| **Entry states** | Any screen, during network interruption |
| **Exit states** | → Resume at current screen; → Retry |
| **Dependencies** | System-level (HTTP connectivity) |
| **Primary action** | "Try Again" → Resume where they stopped |
| **Secondary actions** | Back to previous page |
| **Success state** | Moment resumes; nothing is lost (Phase 2 Part 14.2: session continuity) |
| **Failure state** | Persistent network failure → graceful message + "You can finish this later" + save state |
| **Season availability** | All |
| **Constitutional trace** | Phase 2 Part 14; Phase 2.5 §10.1 |
| **Golden Question** | Exists because network failures are normal (Phase 0 Risk 8). Here as an overlay, not a page - the world doesn't reset. |

---

### SCREEN P-24: Registration Closed

| Field | Definition |
|---|---|
| **Purpose** | Honest closure: when registration is closed, state why and when/what is next. No urgency games, no dead links. (Phase 2 Part 14) |
| **Audience** | Late-arriving students, coordinators |
| **Entry states** | From Landscape (all events closed); from Welcome Beat (season changed); from Event Detail → Register |
| **Exit states** | → Landscape (browse events); → Your Space (if registered); → Contact; → return later |
| **Dependencies** | G1 (season state), B11 (registration status) |
| **Primary action** | "View Events" (read-only) or "Go to Your Space" (if registered) |
| **Secondary actions** | Contact organizer |
| **Success state** | Late visitor is informed, not rejected; included for next time |
| **Failure state** | N/A - every exit path is valid |
| **Season availability** | A (pre-registration starts) · E (post-registration ends) |
| **Constitutional trace** | Phase 2 Part 14.2; Phase 2.5 §10.1 |
| **Golden Question** | Exists because Phase 2's Failure Journeys mandate that closure feels calm, not rejected. Here as a distinct screen so it is not embedded in the registration flow. |

---

### SCREEN P-25: 404 - Lost Slip

| Field | Definition |
|---|---|
| **Purpose** | The named exception (Phase 1.5 §11.1.5): the page is a torn, empty slip - "this slip got lost." Uses the exception to the grammar to create a memorable moment that still solves the problem. |
| **Audience** | Anyone who hit a dead link |
| **Entry states** | Any invalid URL |
| **Exit states** | → Welcome Beat; → Landscape; → Contact |
| **Dependencies** | None |
| **Primary action** | "Go back" → Landing |
| **Secondary actions** | View Events; Contact |
| **Success state** | Visitor is not confused, the moment might even delight, and they are pointed forward |
| **Failure state** | N/A |
| **Season availability** | All |
| **Constitutional trace** | Phase 1.5 §11.1.5 (named exception: The Lost Slip); Phase 2 Part 14 (no dead ends) |
| **Golden Question** | Exists because every platform needs a dead-link handler. Here as the only page allowed to be "offstage" per the negative grammar exception. |

---

### SCREEN P-26: Loading / Skeleton

| Field | Definition |
|---|---|
| **Purpose** | Instant-over-delight loading (Phase 1 §11): slip skeleton with amber pulse. No spinners. |
| **Audience** | All visitors |
| **Entry states** | Any page load (transitional) |
| **Exit states** | → Loaded page |
| **Dependencies** | System-level |
| **Primary action** | Wait (passive) |
| **Secondary actions** | N/A |
| **Success state** | Load completes within 3 seconds on mid-range mobile (Phase 0 metric: mobile ≤3s) |
| **Failure state** | → Network Error (P-23) |
| **Season availability** | All |
| **Constitutional trace** | Phase 1 §11 (loading philosophy); Phase 0 §8 (Lighthouse ≥90) |
| **Golden Question** | Exists because the brand must hold even in loading (Phase 1.5 slip universality, §11.2). |

---

### SCREEN P-27: Registration Full (Event-Specific)

| Field | Definition |
|---|---|
| **Purpose** | When a specific event is full: honest, slightly disappointing but not rejecting. Offers nearest alternatives. (Phase 2 Part 14.2) |
| **Audience** | Student arriving at a filled event |
| **Entry states** | From Landscape (event tile = full); from Event Detail → Register |
| **Exit states** | → Landscape (see other events); → alternative Event Detail; → Contact |
| **Dependencies** | B11 (per-event status = full), B1 (other events available) |
| **Primary action** | "View Other Events" → Landscape |
| **Secondary actions** | "This event is still open" → alternative Event Detail; Contact organizer |
| **Success state** | Participant is offered a path forward, not a wall |
| **Failure state** | N/A - every exit leads somewhere real |
| **Season availability** | R only |
| **Constitutional trace** | Phase 2 Part 14.2; Phase 2.5 §10.1 |
| **Golden Question** | Exists because "no dead ends" (Phase 2 Part 14.1). Here as the event-level failure state. |

---

### SCREEN A-01: Admin - Login

| Field | Definition |
|---|---|
| **Purpose** | Organizer authentication - separate from participant auth. Invisible to participants. |
| **Audience** | Organizers only |
| **Entry states** | Admin URL (known only to organizers) |
| **Exit states** | → Admin Dashboard (success); → Admin Login (retry) |
| **Dependencies** | Admin credentials (organizer-defined) |
| **Primary action** | Login |
| **Secondary actions** | N/A |
| **Success state** | Organizer reaches Admin Dashboard |
| **Failure state** | Wrong credentials → retry; no participant-facing error |
| **Season availability** | All |
| **Constitutional trace** | Phase 2.5 §3.11; Phase 0 Q21, §7.4 |
| **Golden Question** | Exists because organizers need a boundary. Here as separate auth - never exposed to participants. |

---

### SCREEN A-02: Admin - Dashboard

| Field | Definition |
|---|---|
| **Purpose** | The organizer's control panel: season state, registration count, content status, announcements at a glance. (Phase 2.5 §3.11) |
| **Audience** | Organizers only |
| **Entry states** | From Admin Login |
| **Exit states** | → Admin Content; → Admin Registrations; → Admin Announcements; → Admin Season |
| **Dependencies** | F1-F4, G1-G3 (all admin objects) |
| **Primary action** | View season overview |
| **Secondary actions** | Publish announcement; Change season; Export registrations; Edit content |
| **Success state** | Organizer sees the state of the platform in one view and knows what needs attention |
| **Failure state** | N/A |
| **Season availability** | All |
| **Constitutional trace** | Phase 2.5 §3.11; Phase 0 Q21, §7.5 |
| **Golden Question** | Exists because organizers need to run the season without a developer (Phase 2.5 §3.11). Here as the admin home. |

---

### SCREEN A-03: Admin - Content Management

| Field | Definition |
|---|---|
| **Purpose** | Edit and publish content: event rules, festival description, dates, venue, FAQ entries. The organizer's content engine. |
| **Audience** | Organizers only |
| **Entry states** | From Admin Dashboard |
| **Exit states** | → Admin Dashboard; → Preview (publish flow) |
| **Dependencies** | F1 (content management), A1-A7, B1-B12, D1-D2, E1-E3 |
| **Primary action** | Edit/save content |
| **Secondary actions** | Preview changes; Revert; View content version history |
| **Success state** | Content updated without code changes (Phase 0 Risk 9: forbidden) |
| **Failure state** | Save fails → state preserved; retry path |
| **Season availability** | All |
| **Constitutional trace** | Phase 2.5 §3.11; Phase 0 Risk 9, Q21 |
| **Golden Question** | Exists because content must be editable without developer dependency. Here as the admin content surface. |

---

### SCREEN A-04: Admin - Registration Management

| Field | Definition |
|---|---|
| **Purpose** | View, manage, and export registrations. Operational necessity for organizers. |
| **Audience** | Organizers only |
| **Entry states** | From Admin Dashboard |
| **Exit states** | → Admin Dashboard; → export file |
| **Dependencies** | F2 (registration management & export), C5 (confirmation records) |
| **Primary action** | View registrations list |
| **Secondary actions** | Export (CSV/Excel); Filter by event/school; View individual registration |
| **Success state** | Organizer can see who registered, for what, and export the data |
| **Failure state** | Export fails → retry; data not lost |
| **Season availability** | R · P only (registrations exist) |
| **Constitutional trace** | Phase 2.5 §3.11; Phase 0 §7.4, Q22 |
| **Golden Question** | Exists because coordinators and event managers need registration data. Here in admin only - never participant-facing. |

---

### SCREEN A-05: Admin - Announcement Publishing

| Field | Definition |
|---|---|
| **Purpose** | Publish announcements that become the source of truth (Phase 0 12.5). Organizers create, platform displays. |
| **Audience** | Organizers only |
| **Entry states** | From Admin Dashboard |
| **Exit states** | → Admin Dashboard; → Preview before publish |
| **Dependencies** | F3 (announcement publishing), D1 (announcements) |
| **Primary action** | Create/publish announcement |
| **Secondary actions** | Edit existing; Archive old; Preview |
| **Success state** | Announcement visible in Your Space + Welcome Beat |
| **Failure state** | Publish fails → draft preserved; retry |
| **Season availability** | All |
| **Constitutional trace** | Phase 0 §12.5; Phase 2.5 §3.11, F3 |
| **Golden Question** | Exists because announcements replace WhatsApp as the source of truth. Here because it is a publishing action, not a public one. |

---

### SCREEN A-06: Admin - Season & State Control

| Field | Definition |
|---|---|
| **Purpose** | Flip the season state (G1): Announcement → Registration Open → Approach → Live → Post-Event. One toggle controls the entire platform's visibility. |
| **Audience** | Organizers only |
| **Entry states** | From Admin Dashboard |
| **Exit states** | → Admin Dashboard |
| **Dependencies** | G1 (season state) |
| **Primary action** | Change season state |
| **Secondary actions** | View current state; View what changes when state flips |
| **Success state** | Platform reflects the correct season across all screens |
| **Failure state** | State change fails → current state preserved; retry |
| **Season availability** | All |
| **Constitutional trace** | Phase 2.5 G1; Phase 0 §6.4 |
| **Golden Question** | Exists because the platform must always know its season. Here in admin only - one source of truth. |

---

### SCREEN A-07: Admin - Event Status Management

| Field | Definition |
|---|---|
| **Purpose** | Set per-event registration status: open/closed/full. Drives B11 across the platform. |
| **Audience** | Organizers only |
| **Entry states** | From Admin Dashboard; from Admin Registrations |
| **Exit states** | → Admin Dashboard |
| **Dependencies** | B11 (registration status), F2 (registration data), G1 (season state) |
| **Primary action** | Set event status |
| **Secondary actions** | View registration count per event; Bulk set status |
| **Success state** | Event status is accurate and reflected everywhere (computed, not hand-typed - Phase 2.5 §5.1) |
| **Failure state** | Status change fails → current status preserved |
| **Season availability** | R · P only |
| **Constitutional trace** | Phase 2.5 §5.1 (single-source: B11 derived from admin); Phase 2.5 §3.2 |
| **Golden Question** | Exists because registration status is the single-most time-sensitive fact on the platform. Here because it is admin-only - computed display everywhere else. |

---

### INVENTORY AUDIT

| Category | Count | Screens |
|---|---|---|
| **Primary (P)** | 25 | P-01 through P-27, excluding the two system overlays below |
| **Admin (A)** | 7 | A-01 through A-07 |
| **Future (F)** | 0 | Gallery (P-20) and Winners (P-21) are P, not F - they are structured but gated by content |
| **System (S)** | 2 | P-23 (Network Error), P-26 (Loading) - overlaid, not page-level; numbered in the P sequence, categorised as System |
| **Total** | **34** | All screens justified; no screen without Golden Question answer |

*Count note: P-01 through P-27 is 27 defined screens. Two of them (P-23, P-26) are System overlays rather than pages, leaving 25 Primary. 25 + 7 Admin = **34 screens total**. Earlier drafts of this document stated 32; that figure was arithmetically wrong and has been corrected throughout.*

**Verification:**
- Every screen traces to Phase 2.5 page contracts (§3.1-3.11).
- Multi-step registration (P-06 through P-11) accounts for 6 practical screens from Phase 2.5 §3.5.
- Quiet corners (P-15 through P-19) accounts for 5 practical screens from Phase 2.5 §3.9.
- Admin (A-01 through A-07) accounts for 7 practical screens from Phase 2.5 §3.11.
- System screens (P-23, P-26) account for overlay states required by Phase 0 Risk 8 and Phase 1 §11.
- Error/recovery screens (P-24, P-25, P-27) account for Phase 2 Part 14 failure journeys.
- No screen exists that does not answer a Golden Question.
- No justified screen from the constitutions is omitted.

---

## PART 2 - SCREEN RELATIONSHIP MAP

This section maps how all 34 screens connect LOGICALLY. It is not a sitemap. It defines the architecture of movement.

### 2.1 THE SPINE - The Primary Journey Path

The spine is the one path that matters most. Everything else is branch, recovery, or orbit.

```
P-01 Welcome Beat
  │
  ├── (Season = Announcement →)
  │   P-02 Welcome Beat - Announcement State
  │   └── P-03 Landscape (read-only preview)
  │
  └── (Season = Registration Open →)
      P-03 Landscape
        │
        ├── P-04 Event Detail
        │   │
        │   ├── P-06 Register: Declare Intent
        │   │   └── P-07 Register: Participant Info
        │   │       └── P-08 Register: Declaration & Agreement
        │   │           └── P-09 Register: Review & Confirm
        │   │               └── P-10 Register: Payment (TBD - may be skipped)
        │   │                   └── P-11 Confirmation
        │   │                       └── P-22 Login → P-12 Your Space
        │   │
        │   └── P-27 Registration Full (failure → back to P-03)
        │
        └── P-05 Rules & Eligibility
            └── P-04 Event Detail
                └── (→ registration path above)
```

**Spine properties:**
- **Direction:** Always forward (Welcome → Landscape → Detail → Registration → Confirmation → Your Space)
- **Cannot be reversed at will:** The forward path builds confidence; the back path preserves state (Phase 2 Part 11.3)
- **One primary action per screen:** The spine has no competing CTAs
- **Length:** 8 screens from arrival to confirmation — P-01, P-03, P-04, P-06, P-07, P-08, P-09, P-11 (9 when payment applies, adding P-10 between P-09 and P-11)

**Constitutional trace:** Charter §3 (9-step journey); Phase 2.5 §PART 6 (Progress before breadth)

---

### 2.2 HUB SCREENS - Screens that branch to 3+ destinations

A hub is any screen with 3+ logical exits. Hubs are navigation anchors, not dead-end destinations.

| Hub Screen | Destinations (≥3) | Role |
|---|---|---|
| **P-01 Welcome Beat** | P-03 Landscape; P-19 Quiet Corners Hub; P-22 Login (for registered); P-02 Announcement (season-dependent) | The primary routing node - routes by audience and season |
| **P-03 Landscape** | P-04 Event Detail (up to 16); P-05 Rules & Eligibility; P-01 Welcome (back); P-19 Quiet Corners Hub | The discovery node - routes by cluster and event |
| **P-04 Event Detail** | P-06 Registration; P-03 Landscape (back); P-05 Rules & Eligibility; P-19 Quiet Corners Hub; P-27 Full (failure) | The decision node - routes by intent |
| **P-12 Your Space** | P-03 Landscape; P-14 Schedule; P-04 Event Detail; P-19 Quiet Corners Hub | The return node - routes by "what changed" |
| **P-19 Quiet Corners Hub** | P-15 About; P-16 FAQ; P-17 Contact; P-18 Privacy | The reference node - routes by doubt type |
| **A-02 Admin Dashboard** | A-03 Content; A-04 Registrations; A-05 Announcements; A-06 Season; A-07 Event Status | The organizer node - routes by admin task |

**Hub rules:**
- A hub with >5 exits needs sub-grouping (Landscape uses clusters; Quiet Corners uses a dedicated hub - P-19)
- Every hub must have a "Back" retreat path
- No hub competes with the spine - hub exits are secondary to forward motion

**Constitutional trace:** Phase 2.5 §PART 6 (Navigation Logic); Phase 2 Part 8 (Attention Architecture)

---

### 2.3 TERMINAL SCREENS - Endpoints

A terminal screen is where a user "stays" to read, reflect, or complete. They are not stepping stones.

| Terminal Screen | Ending condition | What follows |
|---|---|---|
| **P-11 Confirmation** | "I'm registered" → stamped receipt | Anticipation; the participant goes to Your Space or returns later |
| **P-20 Gallery (F)** | Scroll and share | Exit to Welcome Beat or share on social |
| **P-21 Winners (F)** | Read the Stamp | Exit to Gallery or Welcome Beat |
| **P-15 About** | Read → trust built | Exit to Contact or back to context |
| **P-16 FAQ** | Find answer | Exit to referencing context or Contact (if unanswered) |
| **P-17 Contact** | Reach a human | Exit to referencing context |
| **P-18 Privacy** | Read → verify trust | Exit to referencing context |
| **P-05 Rules & Eligibility** | Confirm eligibility | Exit to Event Detail or Registration |

**Terminal rules:**
- Every terminal has at least one exit (no dead ends - Phase 2 Part 14)
- Terminal screens are read-first; action comes after understanding
- Confirmation (P-11) is the only terminal that carries celebration energy

**Constitutional trace:** Phase 2 Part 14 (no dead ends); Phase 2.5 §10.1 (dead end audit)

---

### 2.4 TRANSITIONAL SCREENS - You don't "stay" on these

A transitional screen is a bridge. Its purpose moves you forward or recovers you backward.

| Transitional Screen | Purpose | Time spent |
|---|---|---|
| **P-02 Welcome Beat - Announcement** | Hold during pre-reg season | Brief - read and leave |
| **P-06 Register: Declare Intent** | Doorway opener | Brief - restatement and continue |
| **P-07 Register: Participant Info** | Data collection | Moderate - form filling |
| **P-08 Register: Declaration** | Acknowledgement | Brief - read and agree |
| **P-09 Register: Review & Confirm** | Final mirror | Brief - review and commit |
| **P-10 Register: Payment (TBD)** | Money moment | Moderate - transaction |
| **P-22 Login** | Auth gate | Brief - input credentials |
| **P-23 Network Error** | Recovery overlay | Brief - retry |
| **P-24 Registration Closed** | Honest closure → redirect | Brief - read and redirect |
| **P-25 404 Lost Slip** | Dead-link recovery | Brief - orient and redirect |
| **P-27 Registration Full** | Honest rejection → redirect | Brief - read and redirect |
| **P-26 Loading** | Wait state | Instant - skeleton to content |

**Transitional rules:**
- No transitional screen asks the user to commit to staying
- Every transitional screen has a clear forward action (or recovery, if overlay)
- Registration steps (P-06 through P-10) form a continuous flow - they are transitional as a group

**Constitutional trace:** Phase 2 Part 10 (registration psychology); Phase 2 Part 14 (failure journeys)

---

### 2.5 FOREVER CONNECTED - Always Reachable

These screens/affordances are accessible from ANY screen in the platform. They never disappear.

| Always-reachable | How | From where |
|---|---|---|
| **Back to previous** | Browser back + visible back affordance | Every screen |
| **Quiet Corners Hub (P-19)** | Footer link ("Info" or "More") | Every public screen |
| **Welcome Beat (P-01)** | Logo/link (every screen) | Every screen |
| **Contact (P-17)** | Via P-19 hub (one tap from footer) | Every screen (via hub) |

**Forever rules:**
- No screen is more than 2 taps from a human (Contact)
- No screen is more than 1 tap from home (Welcome Beat)
- Back is always available (Phase 2.5 §PART 6: path never lost)
- Navigation chrome is minimal (Phase 2 Part 8.2: attention architecture)

**Constitutional trace:** Phase 2.5 §PART 6 (Navigation Logic); Phase 2 Part 12 (Entry & Exit Strategy)

---

### 2.6 SEASONAL CONNECTIONS - Connections that change by season

The platform's connections are not static. Season state (G1) controls which edges are active.

| Season | Active connections | Disabled/changed connections |
|---|---|---|
| **Announcement** | P-01 → P-02 → P-03 (read-only); → P-04 (read-only); → P-05; → P-19 hub | P-06 through P-11 (registration blocked); P-14 (schedule placeholder); P-12 (no auth yet) |
| **Registration Open** | Full spine active; P-12 via P-22; P-07 event status editable | P-20, P-21 (F-gate, not built); P-14 (placeholder) |
| **Approach** | Full spine (registration may still be open); P-14 active; P-12 full | P-02 (no longer relevant) |
| **Live** | P-14 active (live schedule); P-12 active (updates); P-03/P-04 (read-only) | Registration path (P-06 through P-11) closed |
| **Post-Event** | P-20, P-21 active (if content); P-14 archive; P-12 memorial | Registration path closed; P-02 not relevant |

**Seasonal rules:**
- Disabled edges are honest: "Coming soon" for upcoming, "Closed for this edition" for past
- Season state is managed in one place (A-06), displayed everywhere
- No screen is "broken" by season - it adapts (Phase 2.5 §8.1, §PART 6)

**Constitutional trace:** Phase 2.5 G1, §8.1, §PART 6; Phase 2 Part 21 (Time Architecture)

---

### 2.7 RECOVERY PATHS - How every dead end connects back

Every point where a user can get stuck has a named recovery path. This is the "no dead ends" guarantee.

| Stuck point | Recovery path | Screen |
|---|---|---|
| Registration abandoned mid-flow | Resume link → pick up at abandoned step (P-07 or P-08) | P-07 or P-08 |
| Registration closed by deadline | Honest close (P-24) → Landscape (read) → Your Space (if registered) | P-24 |
| Event full | Honest message (P-27) → Landscape (other events) → Contact | P-27 |
| Wrong credentials | Recovery path stated (P-22) → Contact if needed | P-22 |
| Payment failed | Honest failure → retry one action → data preserved → Contact | P-10 |
| 404 / dead link | Lost slip humor (P-25) → Welcome Beat → Landscape | P-25 |
| Network failure | Retry → resume at current screen → state preserved | P-23 (overlay) |
| No search result / wrong event | Back to Landscape → re-orient by cluster | P-04 |
| Logged in, no registrations | "Waiting slip" → Explore Events | P-13 |
| FAQ unanswered | Contact (one hop from FAQ) | P-16 → P-17 |
| Session expired | Resume one action → state restored | P-23 |

**Recovery rules:**
- Every recovery is one action (retry, go back, contact - never a journey)
- No recovery resets effort (Phase 2 Part 20.2: show what is preserved)
- Voice is calm, not apologetic (Phase 2 Part 14.3)
- No recovery is more than 2 taps from a working path

**Constitutional trace:** Phase 2 Part 14 (Failure Journeys); Phase 2 Part 20 (Recovery Experience); Phase 2.5 §10 (Dead End Audit)

---

### 2.8 FORBIDDEN PATHS - Paths that must never exist

| Forbidden path | Why | Constitution that forbids it |
|---|---|---|
| P-01 → P-10 (Payment before identity) | Money before trust destroys confidence | Charter §5; Phase 2 Part 9.2 |
| P-01 → P-07 (Info before event chosen) | Asking data before intent is a surprise | Phase 2 Part 10.2 |
| P-03 → P-10 (Payment before event detail) | No event context at payment destroys trust | Charter §5 |
| P-22 → P-01 (Login before anything) | Gate before value - forbidden | Phase 2.5 §2.3 #6 |
| Any → Empty content area (no placeholder) | Dead links are forbidden | Phase 2.5 §10.1 |
| P-04 → P-04 (same event detail loop) | Navigation trap - user can't leave | Phase 2.5 §PART 6 #5 |
| P-12 → P-06 (Your Space → Registration without going through Landscape/Detail) | Registration always starts from event intent | Phase 2 Part 10.2; Phase 2.5 §PART 6 #1 |
| P-20/P-21 → Registration during Post-Event | Dead registration during archive confuses | Phase 2.5 §8.1 (season timing) |
| Any public screen → A-01 (participant sees admin) | Admin is invisible | Phase 2.5 §2.4 (Admin invariant) |
| P-03 → P-04 → "Similar events" (cross-sell) | Dilutes confidence after choice | Phase 2.5 §4.3 (removed section) |
| P-01 → Auto-playing content | Distracts from orientation | Phase 1 §12.39 (blacklist) |
| P-24 → P-06 (Closed → Register) | Impossible action without honest status | Phase 2 Part 14; Phase 2.5 §10.1 |

**Forbidden path rules:**
- These paths are blocked architecturally (routing guards), not just by UI design
- If a forbidden path is attempted, it redirects to the nearest valid recovery path (Phase 2.5 §10.2)
- The "gate before value" forbidden path overrides all convenience shortcuts

**Constitutional trace:** Phase 2.5 §PART 6 (Navigation Logic); Phase 2 Part 9.2 (Information Release); Charter §5; Phase 2 Part 14

---

### RELATIONSHIP MAP SUMMARY

| Connection type | Count | Screens involved |
|---|---|---|
| **Spine edges** | 9 (10 when payment applies) | P-01 → P-03 → P-04 → P-06 → P-07 → P-08 → P-09 → (P-10) → P-11 → P-12 |
| **Hub branches** | 32 | 6 hubs × 5.3 average exits |
| **Terminal exits** | 20 | 8 terminals × 2.5 average exits |
| **Recovery paths** | 11 | Named for every stuck point |
| **Seasonal toggles** | 8 | 5 seasons × 1.6 average connection changes |
| **Forbidden paths** | 12 | Architecturally blocked |
| **Forever connected** | 4 | Available from every screen |

---

## PART 3 - WIREFRAME BLUEPRINT

For each screen from Part 1, this section defines the structural blueprint: content zones, hierarchy, reading order, interaction order, scanning order, decision order, season variations, and mobile vs desktop differences.

**Zone notation:**
- **[MAJOR]** = dominant visual area
- **[MINOR]** = supporting area
- **[TERTIARY]** = reference/secondary area
- **State codes:** S = static, I = interactive, D = dynamic

---

### P-01: Welcome Beat - Landing

**CONTENT ZONES (3 zones):**

| Zone | Size | Position | Content objects | Required? | State |
|---|---|---|---|---|---|
| **Zone A: Identity Statement** | [MAJOR] | Top, full width | A1 (festival description), A2 (tagline), A3 (edition identity) | Required | S |
| **Zone B: Season Status** | [MINOR] | Below A, inline | G1 (season state text), B11-derived (registration open/closed status) | Required | D |
| **Zone C: Forward Hand** | [MAJOR] | Bottom, centered | Primary CTA: "Explore Events" (→ P-03); Secondary: "About EVOKE" (→ P-19) | Required | I |

**Hierarchy (eye reads):**
1. A2 (tagline) - the first anchor
2. A1 (festival description) - what is this
3. B (status) - what can I do now
4. C (CTA) - what to do next

**Reading order:** Top → Bottom (linear descent, single column on mobile; generous spacing between zones - Phase 1.5 §4.1: sections are scenes)
**Interaction order:** Read A → Read B (status context) → Tap C (forward)
**Scanning order (5 seconds):** Tagline → "Registration open/closed" → "Explore Events" button
**Decision order:** The screen has only one decision: go forward. Status (B) informs whether the CTA leads to the spine or a placeholder.
**Season variations:**
- **Announcement:** B shows "Registration coming soon"; C primary = "View Events" (read-only)
- **Registration Open:** B shows "Registration is open"; C primary = "Explore Events"
- **Approach:** B shows "Schedule coming soon" alongside registration status
- **Live:** B shows "Festival is live - see schedule"; C primary = "View Schedule" (→ P-14)
- **Post-Event:** B shows "EVOKE 2K26 has ended"; C primary = "See Gallery" (→ P-20) or "See Winners" (→ P-21) if content exists

**Mobile vs Desktop differences:**
- **Mobile:** Single column, generous vertical spacing between zones (Bible §10 - breathing room). CTA is thumb-reachable (bottom of viewport on first paint - Phase 2 §13.1: thumb is lazy and honest).
- **Desktop:** A may span wider (12-col grid); B and C may sit in a compact block rather than full-width stacks. CTA can be a contained button group.

---

### P-02: Welcome Beat - Announcement State

**CONTENT ZONES (2 zones):**

| Zone | Size | Position | Content objects | Required? | State |
|---|---|---|---|---|---|
| **Zone A: Promise** | [MAJOR] | Top | A2 (tagline), A1 (short festival description) | Required | S |
| **Zone B: Honest Wait** | [MINOR] | Below A | G1 "Registration opens soon"; P-02 placeholder posture (Phase 2.5 §11.1) | Required | S |

**Hierarchy:** A → B → (implicit next: return later)
**Reading order:** Top-down; one screen, minimal
**Interaction order:** Read → exit or share
**Scanning order:** Tagline → "coming soon" → exit
**Decision order:** No decision - the screen waits
**Season variations:** Only in Announcement season
**Mobile vs Desktop:** Identical - minimal screen, no structural difference

---

### P-03: Landscape - Event List

**CONTENT ZONES (3 zones):**

| Zone | Size | Position | Content objects | Required? | State |
|---|---|---|---|---|---|
| **Zone A: Orientation Header** | [TERTIARY] | Top, narrow | Area identity ("Events"); breadcrumb (← Welcome) | Required | S |
| **Zone B: Cluster Groups** | [MAJOR] | Middle, scrollable | B2 (cluster tags: Stage/Mind/Art/Maker); B1 (event tiles within each cluster: name, brief descriptor, status badge) | Required | D |
| **Zone C: Quick Actions** | [MINOR] | Below B, fixed or inline | "View Rules & Eligibility" → P-05; "Back to beginning" → P-01 | Required | I |

**Hierarchy:**
1. Zone B - the events are the content
2. Zone A - "where am I"
3. Zone C - exit paths

**Reading order:** Top-down through clusters. Within each cluster: scan event tiles (F-pattern across tiles: name → cluster → status → tap). The 4 clusters create natural breaks in the scroll.
**Interaction order:** Scan clusters → select cluster of interest → scan events within → tap event → Event Detail
**Scanning order (5 seconds):** "Stage" cluster tag → first 2-3 event names → "Mind" cluster tag → its 2 event names → pattern recognized. Cluster sizes are uneven by content (Stage 6 · Mind 2 · Art 5 · Maker 3); the scan reads the *pattern of grouping*, not a fixed count per group. See Amendment AM-02.
**Decision order:** The screen guides toward narrowing: 16 events → pick cluster → scan events → pick event. Choice paralysis is prevented by cluster grouping (Phase 2 Part 3.3).
**Season variations:**
- **Announcement:** Status badges all show "Details coming" → read-only (no tap to register, tap to preview)
- **Registration Open:** Status badges show open/closed/full → tap to Detail → Register
- **Approach/Live:** Status badges adjusted; "View Schedule" may appear in Zone C
- **Post-Event:** Archive state - event tiles are read-only with optional "Winner" tag if P-21 exists

**Mobile vs Desktop differences:**
- **Mobile:** Clusters are sequential sections (not side-by-side). Event tiles are single-column cards. Cluster filter is a tap-to-collapse toggle (not permanent filter bar). Zone A is compact - title only.
- **Desktop:** Clusters may be side-by-side in a 2×2 grid (Stage/Mind top row, Art/Maker bottom row). Event tiles may show slightly more context per tile. Cluster filter is a sticky bar.

---

### P-04: Event Detail

**CONTENT ZONES (7 zones - the highest-density screen):**

| Zone | Size | Position | Content objects | Required? | State |
|---|---|---|---|---|---|
| **Zone A: Orientation Header** | [TERTIARY] | Top, narrow | Event name; cluster tag; breadcrumb (← Landscape); share option | Required | S |
| **Zone B: Personality** | [MAJOR] | Below A | B3 (event personality description) - the "is this me?" intro | Required | S |
| **Zone C: Quick Facts** | [MINOR] | Below B, grid/facts panel | B4 (team size, time limit, duration); B5 (theme, conditional - only if one exists); B6 (eligibility) | Required | S |
| **Zone D: Rules** | [MAJOR] | Below C, structured list | B7 (rules - faithful wording, scannable format) | Required | S |
| **Zone E: Judging & Materials** | [MINOR] | Below D, single flow; a second column only when both B8 and B9 have content | B8 (judging criteria - **conditional**, present for 6 of 16 events); B9 (things to bring) | Required (zone) / conditional (judging block) | S |
| **Zone F: FAQ** | [TERTIARY] | Below E, expandable | B10 (per-event FAQ) | Required | I |
| **Zone G: Decision** | [MAJOR] | Bottom, sticky on scroll | B11 (registration status); B12 (requirements summary if any); Primary CTA: "Register for This Event" (→ P-06) | Required | D |

**Hierarchy:**
1. Zone B (personality) - "is this me?"
2. Zone C (quick facts) - "can I do it?"
3. Zone D (rules) - "what exactly?"
4. Zone G (decision) - "yes"
5. Zone E (judging/materials) - supporting detail
6. Zone F (FAQ) - edge cases

**Reading order:** Custom - not Z, not F. A (orient) → B (emotion) → C (scan facts) → D (read rules, structured) → E (supporting detail) → F (expand only if needed) → G (decision). The G zone is sticky so it is always accessible.

**Interaction order:**
1. Read personality (B) - sets emotional context
2. Scan quick facts (C) - determines eligibility
3. Read rules (D) - removes doubt
4. Scroll to or tap sticky CTA (G) - register
5. Expand FAQ (F) only if a specific question remains
6. View judging/materials (E) before final decision or after registration

**Scanning order (5 seconds):** Event name → cluster tag → team size → time limit → "Register" button (sticky)
**Decision order:** The screen guides: Personality convinces → Facts confirm → Rules remove doubt → CTA converts. Zone G is always visible (sticky on scroll) so the decision is never lost in content density.

**Season variations:**
- **Announcement:** Zone G shows "Registration opens soon" - CTA disabled
- **Registration Open:** Zone G active - "Register" button
- **Approach:** Zone G replaced or supplemented by "View Schedule for this event" → P-14
- **Live:** Minimal - event info only; no registration
- **Post-Event:** Zone G shows winner status (if P-21 data exists); read-only

**Mobile vs Desktop differences:**
- **Mobile:** All zones are single-column, stacked. Zone C (quick facts) is compact cards (not grid). Zone E (judging/materials) is stacked, not side-by-side. Zone G is a fixed bottom bar (thumb-reachable at all times - Phase 2 §13.1). Zone F (FAQ) is accordion, not side-by-side.
- **Desktop:** Zone C may be a 3-column grid. Zone E is two-column **only when both a judging block and a materials block have content**; otherwise it is a single column (see Amendment AM-03). Zone G is inline at natural document flow (not sticky) - but still always accessible via scroll-back-to-top. Zone F may be side-by-side with Zone D on wide screens.

---

### P-05: Rules & Eligibility (General)

**CONTENT ZONES (4 zones):**

| Zone | Size | Position | Content objects | Required? | State |
|---|---|---|---|---|---|
| **Zone A: Orientation Header** | [TERTIARY] | Top, narrow | Page title; breadcrumb (← Landscape) | Required | S |
| **Zone B: General Rules** | [MAJOR] | Below A | C1 (general rules - faithful wording, structured sections) | Required | S |
| **Zone C: Eligibility & Quotas** | [MAJOR] | Below B | B6 (eligibility baseline); Q10 quota info (TBD posture) | Required | S (content P) |
| **Zone D: Cross-Reference** | [MINOR] | Bottom | "For per-event rules → view an Event Detail"; "Start Registration →" (links to P-06 via P-04) | Required | I |

**Hierarchy:**
1. Zone B (general rules) - the contract
2. Zone C (eligibility) - can we participate
3. Zone D (what next)

**Reading order:** Top-down (linear). Zone B is dense but structured - one rule per slip, scannable (Phase 1.5 §4.2: content on slips).
**Interaction order:** Read rules → check eligibility → link to specific event for detail or Register
**Scanning order (5 seconds):** "General Rules" → first 3 rule bullets → "Eligibility" → quota number → "Start Registration"
**Decision order:** The screen guides coordinators to confirm fit → then to register. No emotional sell - this is logistics calm (Phase 1 §2.3).

**Season variations:** Content is stable across seasons (C1 does not change by season)
**Mobile vs Desktop differences:**
- **Mobile:** All zones stacked single-column. Rule bullets are compact (short lines, readable at small sizes - Phase 1 §5.1). Zone D is compact.
- **Desktop:** Zone B may use a two-column rule display for scan-ability. Zone C may be inline with Zone B.

---

### P-06: Registration - Step 1: Declare Intent

**CONTENT ZONES (3 zones):**

| Zone | Size | Position | Content objects | Required? | State |
|---|---|---|---|---|---|
| **Zone A: Step Declaration** | [MINOR] | Top | Step indicator: Step 1 of 4 (or 5); "What I'll ask" - list of declared steps (C2) | Required | S |
| **Zone B: Intent Restatement** | [MAJOR] | Middle | Event name, cluster, team format, time limit - "Here is what you registered for" (B3, B4 restated) | Required | S |
| **Zone C: Action** | [MAJOR] | Bottom | "Continue" (primary, → P-07); "Go back to event" (secondary, → P-04) | Required | I |

**Hierarchy:** B → A → C (read intent → understand steps → proceed)
**Reading order:** Top-down; short, one-screen
**Interaction order:** Read intent → See steps ahead → Continue
**Scanning order (5 seconds):** Event name → team format → "4 steps" → "Continue"
**Decision order:** The screen asks one question: "Is this correct?" Yes → Continue. No → Go back.

**Season variations:** Only in Registration Open
**Mobile vs Desktop differences:**
- **Mobile:** Zones stacked, compact. Step indicator is a progress bar (visual, not text-heavy). Zone B is a single card.
- **Desktop:** Zone B may include a right-aligned summary panel. Progress bar is horizontal at the top.

---

### P-07: Registration - Step 2: Participant Information

**CONTENT ZONES (3 zones):**

| Zone | Size | Position | Content objects | Required? | State |
|---|---|---|---|---|---|
| **Zone A: Step Declaration** | [MINOR] | Top | Step indicator: Step 2 of 4 (or 5); progress bar | Required | S |
| **Zone B: Form Fields** | [MAJOR] | Middle | C4 (data fields - TBD: name, school, class, team members) - labels above, inline validation | Required | I |
| **Zone C: Action** | [MAJOR] | Bottom | "Continue" (→ P-08); "Back" (→ P-06); "Pause & Save" (resume later - Phase 2 Part 14) | Required | I |

**Hierarchy:** B → C (fill forms → submit)
**Reading order:** Field by field, top to bottom (linear form)
**Interaction order:** Fill fields → validate inline → Continue (or Back to edit)
**Scanning order (5 seconds):** "Step 2" → field labels → "Continue"
**Decision order:** The screen asks: "Is your information correct?" Proceed or go back.

**Season variations:** Only in Registration Open
**Mobile vs Desktop differences:**
- **Mobile:** Fields are single-column, full-width. Labels above fields (not inline). "Pause & Save" is compact (not competing with Continue).
- **Desktop:** Team member fields may be side-by-side (or one team member per row). Labels may be left-aligned with fields.

---

### P-08: Registration - Step 3: Declaration & Agreement

**CONTENT ZONES (3 zones):**

| Zone | Size | Position | Content objects | Required? | State |
|---|---|---|---|---|---|
| **Zone A: Step Declaration** | [MINOR] | Top | Step indicator: Step 3 of 4 (or 5) | Required | S |
| **Zone B: Key Agreements** | [MAJOR] | Middle | Rule summaries (B7 summary - not full text): originality, decency, time limits, "judges' decision is final"; link to full rules (→ P-04, Zone D) | Required | S |
| **Zone C: Action** | [MAJOR] | Bottom | "I understand. Continue." (→ P-09); "Back" (→ P-07); Decline → P-04 (no penalty) | Required | I |

**Hierarchy:** B → C (read agreements → acknowledge)
**Reading order:** Agreement items top to bottom → CTA
**Interaction order:** Read agreements → acknowledge → Continue
**Scanning order (5 seconds):** "Step 3" → 4 key agreements → "I understand. Continue."
**Decision order:** One decision: acknowledge or decline. The button text ("I understand") is the agreement itself.

**Season variations:** Only in Registration Open
**Mobile vs Desktop:** Same structure; mobile has more compact agreement items

---

### P-09: Registration - Step 4: Review & Confirm

**CONTENT ZONES (3 zones):**

| Zone | Size | Position | Content objects | Required? | State |
|---|---|---|---|---|---|
| **Zone A: Step Declaration** | [MINOR] | Top | Step indicator: Step 4 of 4 (or 5); "Final Review" | Required | S |
| **Zone B: Full Summary** | [MAJOR] | Middle | All collected data restated: event, participants, team, agreed rules (C4 display) | Required | S |
| **Zone C: Action** | [MAJOR] | Bottom | "Confirm Registration" (→ P-10 or P-11); "Edit" (→ P-07); "Cancel" (→ P-04) | Required | I |

**Hierarchy:** B → C (review → commit)
**Reading order:** Summary items top to bottom → CTA
**Interaction order:** Read summary → Confirm (or Edit to fix, Cancel to back out)
**Scanning order (5 seconds):** "Final Review" → event name → participant names → "Confirm Registration"
**Decision order:** The final yes/no - "Confirm" is the commit. "Edit" and "Cancel" are non-punishing exits.

**Season variations:** Only in Registration Open
**Mobile vs Desktop:** Same structure

---

### P-10: Registration - Step 5: Payment (TBD)

**CONTENT ZONES (3 zones - structure exists, content TBD):**

| Zone | Size | Position | Content objects | Required? | State |
|---|---|---|---|---|---|
| **Zone A: Step Declaration** | [MINOR] | Top | Step indicator (if payment is a step); "Payment" | Conditional (P-gated) | S |
| **Zone B: Payment Block** | [MAJOR] | Middle | C3 (payment facts - TBD); payment gateway UI (TBD) | Conditional (P-gated) | I |
| **Zone C: Action** | [MAJOR] | Bottom | "Pay and Complete" → P-11; "Back" → P-09; "Contact" → P-17 | Conditional (P-gated) | I |

**Hierarchy:** B → C
**Reading order:** Payment info → Pay
**Interaction order:** Review payment → Pay → Confirmation
**Scanning order (5 seconds):** Amount → "Pay and Complete"
**Decision order:** Pay or back out. Every failure path is defined (Phase 2 Part 14.2).

**Season variations:** Only in Registration Open
**Mobile vs Desktop:** Payment gateway UI is provided by the gateway - platform frame adapts

---

### P-11: Confirmation

**CONTENT ZONES (3 zones):**

| Zone | Size | Position | Content objects | Required? | State |
|---|---|---|---|---|---|
| **Zone A: The Stamp** | [MAJOR] | Top, centered | C5 (confirmation record): "You're registered." - event, participants, timestamp - stamped (Phase 1.5 Part 6.4) | Required | S |
| **Zone B: What's Next** | [MINOR] | Below A | Next steps: announcements, schedule timing, preparation (Phase 2 Part 19.2) | Required | S |
| **Zone C: Actions** | [MAJOR] | Bottom | "Go to Your Space" (primary, → P-12); "Register Another Event" (→ P-03); "Print/Share" | Required | I |

**Hierarchy:** A → B → C
**Reading order:** Confirmation stamp → What's next → Actions
**Interaction order:** Read confirmation → Read what's next → Go to Your Space
**Scanning order (5 seconds):** "You're registered" → event name → "Go to Your Space"
**Decision order:** The screen's job is done - the act is complete. The primary action (Your Space) is the next chapter.

**Season variations:** Confirmation is static once created - no season variation
**Mobile vs Desktop differences:**
- **Mobile:** Stamp is centered card. Actions are full-width buttons stacked.
- **Desktop:** Stamp may be wider. Actions may be side-by-side.

---

### P-12: Your Space (Participant Dashboard)

**CONTENT ZONES (4 zones):**

| Zone | Size | Position | Content objects | Required? | State |
|---|---|---|---|---|---|
| **Zone A: Greeting & Delta** | [MAJOR] | Top, full width | C7 (what changed since last visit); G1 (current season context); C6 (participant name/greeting) | Required | D |
| **Zone B: My Registrations** | [MAJOR] | Below A | C5 (registration records: events, status, confirmation details) | Required | D |
| **Zone C: Announcements** | [MINOR] | Below B | D1 (announcements from organizer - source of truth) | Required | D |
| **Zone D: Next Steps** | [MINOR] | Bottom | Season-aware actions: "Register More" (→ P-03); "View Schedule" (→ P-14); "Edit Profile" | Required | I |

**Hierarchy:**
1. Zone A (what changed) - the return engine's heartbeat
2. Zone B (registrations) - the record
3. Zone C (announcements) - what's new
4. Zone D (next steps) - what to do

**Reading order:** Top-down, prioritized by change. If nothing changed, Zone A collapses to a greeting and Zone B becomes primary.
**Interaction order:** Read "what changed" → check announcements → review registrations → take next action
**Scanning order (5 seconds):** "Welcome back, [name]" → "2 announcements" → event status → "Register More" or "View Schedule"
**Decision order:** The screen's purpose is orientation in time. The primary decision is determined by season: register more (R), check schedule (P), check results (E).

**Season variations:**
- **Registration Open:** Zone D includes "Register More Events"
- **Approach:** Zone D includes "View Schedule"; Zone B may include preparation checklist (B9 reminder)
- **Live:** Zone D includes "View Live Schedule"; Zone A shows updates
- **Post-Event:** Zone D may include "View Winners" / "View Gallery" if content exists

**Mobile vs Desktop differences:**
- **Mobile:** All zones stacked. Zone A is a prominent top card (the "what changed" card). Zone B is a scrollable list of registration cards. Zone C is a collapsible announcement list. Zone D is a compact action row at the bottom.
- **Desktop:** Zone A may sit beside Zone B (two-column). Zone C may be a sidebar. Zone D may be a horizontal action bar.

---

### P-13: Your Space - Empty State

**CONTENT ZONES (2 zones):**

| Zone | Size | Position | Content objects | Required? | State |
|---|---|---|---|---|---|
| **Zone A: Waiting Slip** | [MAJOR] | Centered | "This slip is waiting for your name" - negative space as message (Phase 1.5 §11.1.6) | Required | S |
| **Zone B: Action** | [MINOR] | Below A | "Explore Events" → P-03 | Required | I |

**Hierarchy:** A → B
**Mobile vs Desktop:** Same minimal structure

---

### P-14: Schedule

**CONTENT ZONES (3 zones):**

| Zone | Size | Position | Content objects | Required? | State |
|---|---|---|---|---|---|
| **Zone A: Orientation** | [TERTIARY] | Top | "Schedule"; season context (G1) | Required | S |
| **Zone B: Schedule Data** | [MAJOR] | Middle | D2 (per-event timing and venue - TBD content); cluster filters; event detail links | Required (structure) / P (content) | D |
| **Zone C: Status** | [TERTIARY] | Inline with B | TBD posture if schedule is not yet published | Conditional (P-gated) | S |

**Hierarchy:** B → A → C (schedule is the content)
**Reading order:** Top-down, scan by time or cluster
**Interaction order:** Scan/filter → find event → click to Event Detail
**Scanning order (5 seconds):** Date → first event time → cluster labels
**Decision order:** Find timing → plan logistics

**Season variations:**
- **Announcement/Registration:** Zone C shows honest placeholder - schedule not yet published
- **Approach:** Zone B populated with schedule data
- **Live:** Zone B reflects live schedule, may show real-time updates
- **Post-Event:** Archive state

**Mobile vs Desktop differences:**
- **Mobile:** Schedule is a vertical timeline (single column). Cluster filter is a tap toggle.
- **Desktop:** Schedule may be a two-pane view: time column + event details. Cluster filter is a sticky sidebar.

---

### P-15 through P-18: Quiet Corners (About, FAQ, Contact, Privacy)

These four screens share a common structural template - they are reference pages, accessed when a doubt exists.

**Common CONTENT ZONES (3 zones):**

| Zone | Size | Position | Content objects | Required? | State |
|---|---|---|---|---|---|
| **Zone A: Header** | [TERTIARY] | Top | Page title; breadcrumb (← context) | Required | S |
| **Zone B: Content** | [MAJOR] | Middle | Page-specific content (see below) | Required | S/P |
| **Zone C: Related Actions** | [MINOR] | Bottom | Links to related pages (FAQ ↔ Contact, About → Contact) | Required | I |

**Per-screen Zone B content:**

| Screen | Zone B content objects |
|---|---|
| **P-15 About** | A4 (host), A8 (history - F), A1-A3 (identity context - reference, not duplication) |
| **P-16 FAQ** | E1 (global FAQ entries); links to per-event FAQ (B10 - not duplicated) |
| **P-17 Contact** | A7 (contact person), E2 (contact route) |
| **P-18 Privacy** | E3 (privacy note); C4 reference (data collected) |

**Hierarchy:** B → C (read content → take action if needed)
**Reading order:** Top-down linear
**Scanning order (5 seconds):** Title → first content section → related actions
**Decision order:** Each screen is terminal - read → leave satisfied or escalate to Contact

**Mobile vs Desktop:** Minimal difference - these are content pages, read-first

---

### P-19: Quiet Corners Hub

**CONTENT ZONES (2 zones):**

| Zone | Size | Position | Content objects | Required? | State |
|---|---|---|---|---|---|
| **Zone A: Header** | [TERTIARY] | Top | "More about EVOKE"; breadcrumb | Required | S |
| **Zone B: Links** | [MAJOR] | Middle | → P-15 About; → P-16 FAQ; → P-17 Contact; → P-18 Privacy | Required | I |

**Hierarchy:** B → (contextual exit)
**Mobile vs Desktop:**
- **Mobile:** Links stacked as cards
- **Desktop:** Links may be a 2×2 grid

---

### P-20 through P-21: Post-Event (Gallery, Winners)

**CONTENT ZONES (3 zones - both screens share template):**

| Zone | Size | Position | Content objects | Required? | State |
|---|---|---|---|---|---|
| **Zone A: Header** | [TERTIARY] | Top | Page title (Gallery or Winners); edition context | Required | S |
| **Zone B: Content** | [MAJOR] | Middle | D3 (gallery images) or D4 (winner results with Stamp) | Required (structure) / F (content) | D |
| **Zone C: Actions** | [MINOR] | Bottom | "See Winners" ↔ "See Gallery" (cross-link); "Back to Welcome" → P-01 | Required | I |

**P-21 Winners specific:** Zone B displays results as stamped verdicts (Phase 1.5 Part 6.4 - the Stamp gesture for each winner)

---

### P-22: Login

**CONTENT ZONES (2 zones):**

| Zone | Size | Position | Content objects | Required? | State |
|---|---|---|---|---|---|
| **Zone A: Identity** | [MINOR] | Top | "Your Space - Sign in"; C6 (participant identity reference) | Required | S |
| **Zone B: Login Form** | [MAJOR] | Middle/centered | Credentials input (TBD - auth model); "Sign in"; "Forgot credentials" → recovery; "Back to Welcome" → P-01 | Required | I |

**Hierarchy:** B → (recovery path if needed)
**Mobile vs Desktop:** Minimal - centered form

---

### P-23, P-25, P-26, P-27: System & Error Screens

These are brief, overlay, or redirect screens with minimal structure.

| Screen | Zones | Key content | Structure notes |
|---|---|---|---|
| **P-23 Network Error** | 2 zones (overlay) | "We can't reach the server"; "Try again"; "Finish later" | Overlay - does not replace the page. Dismissed on retry success. |
| **P-24 Registration Closed** | 3 zones (full screen) | Honest close message → "View Events" (read) → "Your Space" (if registered) | Brief - redirect-focused |
| **P-25 404 Lost Slip** | 2 zones (full screen) | "This slip got lost" (The Lost Slip - Phase 1.5 §11.1.5) → "Go back" → P-01 | Brief - memorable redirect |
| **P-26 Loading** | 1 zone (overlay) | Skeleton frame - slip outline + amber pulse (Phase 1 §11) | Instant - not user-facing |
| **P-27 Registration Full** | 3 zones (full screen) | Honest "full" message → "View Other Events" → → alternative event | Brief - redirect with alternatives |

---

### Admin Screens (A-01 through A-07)

Admin screens follow standard admin patterns with the constraint that they are invisible to participants. They are functional, not emotional.

| Screen | Zones | Key structure |
|---|---|---|
| **A-01 Admin Login** | 2 zones | Identity + credentials form - no participant-facing chrome |
| **A-02 Admin Dashboard** | 3 zones | Overview cards (season state, registration count, content status); Action grid (→ A-03 through A-07) |
| **A-03 Content Management** | 3 zones | Content list (editable items); Editor panel; Preview/Save actions |
| **A-04 Registration Management** | 3 zones | Registration list (sortable/filterable); Export actions; Individual registration detail |
| **A-05 Announcement Publishing** | 2 zones | Announcement list; Create/Edit form with preview; Publish/Archive actions |
| **A-06 Season & State Control** | 2 zones | Current state display; Season toggle (Announcement → Registration Open → Approach → Live → Post-Event) |
| **A-07 Event Status Management** | 3 zones | Event list with current status; Status toggle per event; Registration count per event |

**Admin design constraint:** Never use the participant-facing signature language (Slips, Stamps, Sweeps) in admin. Admin is functional, calm, operational - Phase 2.5 §2.4 (Admin invariant: invisible).

---

### BLUEPRINT AUDIT

| Screen | Zones defined | Content objects mapped | Season variations | Mobile/Desktop diff |
|---|---|---|---|---|
| P-01 | 3 | 4 | 5 seasons | Yes |
| P-02 | 2 | 3 | Announcement only | Minimal |
| P-03 | 3 | 3 | 5 seasons | Yes |
| P-04 | 7 | 10 | 5 seasons | Yes (sticky CTA) |
| P-05 | 4 | 3 | Stable | Yes |
| P-06 | 3 | 2 | Registration only | Yes |
| P-07 | 3 | 1 | Registration only | Yes |
| P-08 | 3 | 2 | Registration only | Minimal |
| P-09 | 3 | 1 | Registration only | Minimal |
| P-10 | 3 | 1 | Registration only | Gateway-dependent |
| P-11 | 3 | 3 | Stable | Yes |
| P-12 | 4 | 4 | 4 seasons | Yes |
| P-13 | 2 | 1 | Post-auth | Minimal |
| P-14 | 3 | 2 | 5 seasons | Yes (timeline vs table) |
| P-15-P-18 | 3 each | 1 each each | Stable | Minimal |
| P-19 | 2 | 1 | Stable | Yes (grid vs stack) |
| P-20-P-21 | 3 | 1 each | Post-Event | Minimal |
| P-22 | 2 | 1 | Post-Announcement | Minimal |
| P-23/P-25/P-27 | 2-3 each | 1 each | All | Minimal |
| P-26 | 1 | 0 | All | Minimal |
| A-01-A-07 | 2-3 each | Per screen | All | Standard admin |

**Every zone specifies:**
- Content objects (referenced by Phase 2.5 inventory codes: A1, B3, C5, D2, etc.)
- Required or conditional status
- State (S / I / D)

**A wireframe artist can produce wireframes from this document without asking "what goes here?" because every screen's zones, hierarchy, reading order, and content objects are fully specified.**

---

## PART 3 END - SUMMARY AUDIT

### Screens blueprinted: 34
- **25 Primary screens** (P-01 through P-27, less the two System overlays P-23 and P-26)
- **7 Admin screens** (A-01 through A-07)
- **0 screens without Golden Question justification**
- **0 content objects placed without Phase 2.5 inventory reference**

### Constitutional traces verified:
- **Phase 0:** Audience priorities (2.1-2.3), event list (3.1), cognitive load (7.1), success metrics (8), information architecture (6.1-6.2), 14 principles (12)
- **Phase 1:** Brand personality (1.1-1.2), emotional design (2.1-2.3), Color roles (4.4), Typography (5.1-5.2), Motion (9), Blacklist (12), Constitution (13)
- **Phase 1.5:** The Unveiling (Part 3), gestures (Part 3.4), Visual Grammar (Part 4), Motifs (Part 6), EVOKE Test (Part 9), Named Exceptions (Part 11.1), Slip Universality (Part 11.2)
- **Phase 1.75:** Product purpose (§1-§2), Participant Journey (§3), Progressive Confidence (§5), Decision Filter (§6), Placeholders (§7)
- **Phase 2:** Five Acts (Part 2.1), Chapter Map (Part 3.1), Cognitive Load (Part 7), Attention Architecture (Part 8), Information Release (Part 9), Registration Psychology (Part 10), Entry/Exit (Part 12), Mobile Psychology (Part 13), Failure Journeys (Part 14), Trust Architecture (Part 15), Recovery (Part 20)
- **Phase 2.5:** Content Inventory (Part 1), Page Contracts (Part 3), Section Contracts (Part 4), Navigation Logic (Part 6), Timing (Part 8), Duplication (Part 9), Dead End Audit (Part 10), Placeholders (Part 11)

### The 4-Question Decision Filter (Charter §6) applied to all screens:
1. Does it help someone choose an event? → Landscape (P-03), Event Detail (P-04), Rules (P-05)
2. Does it reduce uncertainty before registration? → Event Detail (P-04), Rules (P-05), Registration Step 1 (P-06)
3. Does it improve trust at registration? → Registration Steps (P-06 through P-09), Confirmation (P-11), Privacy (P-18)
4. Does it reinforce identity? → Welcome Beat (P-01), Confirmation (P-11), 404 (P-25)

### EVOKE Test (Phase 1.5 Part 9) gate:
Every screen defined above passes the EVOKE Test at the structural level:
1. Slip composition used on event tiles, registration cards, confirmation (Q5)
2. No generic card-grid or fade (Q2)
3. Identity survives logo removal - reveal grammar is structural, not aesthetic (Q3)
4. Layout is the language - swapping text would break the grammar (Q4)
5. Three screenshots of slips + reveals = recognizable EVOKE (Q5)
6. One coherent identity across all screens (Q6)
7. Loud rationed - logistics screens are hushed (Q7)
8. Blacklist respected - no 60 anti-patterns appear (Q8)
9. Every motion gesture answers "what is it telling?" (Q9) - defined in relationship map
10. Graphic-only fallback exists for screens without photography (Q10)
11. Only adopted motifs used - Slip, Light, Edge, Stamp, Stack, Clock (Q11)
12. Calm is structured, not empty (Q12) - logistics screens have deliberate composition

---

*End of Phase 3 Interface Architecture Specification - Parts 1, 2, and 3.*

---

## PART 4 - COMPONENT INVENTORY

Every interface component the platform requires. Grouped into nine categories. Each component must answer: what user problem does it solve? If nothing, it is removed (the One Last Rule, Phase 1.5 §11.4).

**Inventory notation:**
- **States** listed as: default / hover (desktop only) / focus / active / disabled / error / success (+ conditional variants)
- **Sizes** where multiple exist; single-size components omit this
- **"TBD-aware"** = component has a placeholder variant for Charter §7 unresolved items
- **Replaceable?** = which other component could serve this role; if no replacement is possible, why

---

### CATEGORY A: NAVIGATION & WAYFINDING

#### A-01: Site Header (Sticky Top Bar)

| Field | Specification |
|---|---|
| **Name** | Site Header |
| **Purpose** | Identity anchor + orientation: tells visitor where they are and how to go home. Serves "the path is never lost" principle (Phase 2.5 §PART 6 #3). The header is the quiet presence of EVOKE identity - not a banner, not a selling zone. |
| **Where it appears** | Every public page (P-01 through P-27). **Excluded from:** A-01 through A-07 (admin has its own header). |
| **Where it must NEVER appear** | Over the P-10 Payment screen if payment gateway provides its own chrome - avoid competing headers. Over P-25 404 - the Lost Slip owns its space. |
| **Required variants** | **Surface:** Ink background (identity moments: P-01, P-02, P-11) / Paper background (logistics: P-04 through P-09, P-12 through P-18, P-20 through P-22). **States:** default / scroll-compressed (reduced height after scroll on P-04's long content). |
| **Replaceable?** | No. The header is the only always-visible identity element. Replacing it with a floating logo or bottom bar would break the one-tap-home guarantee (Phase 2.5 §2.5). |
| **Composition** | Contains: Logo Link (A-02); Nav Items (A-03); Mobile Nav Trigger (A-04) |
| **Accessibility** | `role="banner"`; keyboard navigable (Tab through links); skip-link present (Phase 0 §12.7 WCAG AA); touch target ≥44px (Bible blacklist #43). Screen reader: announces "Site navigation" on focus. |
| **Placeholder awareness** | No TBD variant needed - always exists. |

---

#### A-02: Logo Link

| Field | Specification |
|---|---|
| **Name** | Logo Link |
| **Purpose** | One-tap-home guarantee: visitor returns to Welcome Beat from anywhere (Phase 2.5 §2.5: "No screen is more than 1 tap from home"). Also carries identity - the site is unmistakably EVOKE (Phase 1.5 EVOKE Test #3). |
| **Where it appears** | Inside Site Header (A-01), every public page. |
| **Where it must NEVER appear** | As the primary CTA on P-01 (redundant - you're already home). Inside registration forms (distracts from forward motion). |
| **Required variants** | **Surface:** Paper-on-Ink (identity headers) / Ink-on-Paper (logistics headers). **Sizes:** Compact (header height constraint). **States:** default / hover (brightness shift) / focus (amber ring, Bible §11). |
| **Replaceable?** | No. It is the home link - every platform requires exactly one. |
| **Composition** | Text mark: "EVOKE 2K26" (display type, as per Bible §5.1). No separate icon. |
| **Accessibility** | `aria-label="Home"`; link target is P-01. Screen reader reads "Evoke Two Thousand Twenty-Six, Home". Touch target ≥44px minimum height. |
| **Placeholder awareness** | No TBD - edition identity always exists (A3, M). |

---

#### A-03: Nav Items (Main Links)

| Field | Specification |
|---|---|
| **Name** | Nav Items |
| **Purpose** | Essential wayfinding: routes to Landscape, Your Space, Schedule, and Quiet Corners. Implements two-tier navigation (Phase 0 §5.3: main = essential). Never more than 4 items - mobile-first discipline. |
| **Where it appears** | Inside Site Header (A-01) - horizontal on desktop, collapsed menu on mobile. |
| **Where it must NEVER appear** | As a bottom navigation bar (conflicts with content zone layouts; Phase 1.5 §4.4: empty space should not be filled). As a sidebar (Dashboard/corporate signal - Bible blacklist #29). |
| **Required variants** | **States:** default / hover (brightness shift) / focus (amber ring) / active (underlined or highlighted). **Conditional:** Schedule link appears only in Approach/Live/Post seasons (P-gated by G1). Your Space link visible only to registered participants or as login link. |
| **Replaceable?** | No. These are the essential nav items. Could be replaced by a single menu button, but that adds a tap and violates mobile-first thumb-reach (Phase 2 §13.1). |
| **Composition** | 1-3 text links per breakpoint: [Events] [Your Space / Login] [Schedule*] [Info]. Links use body type, small-medium weight, arrow-chevron affordance on identity (Bible §11). |
| **Accessibility** | `role="navigation"`; keyboard focusable; active item indicated with `aria-current="page"`. Touch targets ≥44px. |
| **Placeholder awareness** | No TBD - nav structure is stable. Content behind Schedule link is P-gated by season. |

---

#### A-04: Mobile Nav Trigger (Hamburger / Menu Button)

| Field | Specification |
|---|---|
| **Name** | Mobile Nav Trigger |
| **Purpose** | Compresses navigation to one tap on mobile (65%+ traffic, Phase 0 §11.4). Opens the nav drawer (A-05). |
| **Where it appears** | Inside Site Header, mobile breakpoint only. |
| **Where it must NEVER appear** | On desktop - desktop shows nav items inline. As a floating action button - conflicts with primary CTAs. |
| **Required variants** | **States:** default / focus / active (drawer open). **Conditional:** appears only on mobile breakpoint. |
| **Replaceable?** | Could be replaced by always-explicit nav, but that wastes viewport on mobile (Phase 2 §13.2: navigation is a quiet escape hatch, never competing). |
| **Composition** | Icon only (stroke-based, rounded joins - Bible §6). No text. |
| **Accessibility** | `aria-expanded` toggles; `aria-controls` points to drawer; label = "Menu". Touch target exactly 48px (above 44px minimum). |
| **Placeholder awareness** | No TBD. |

---

#### A-05: Mobile Nav Drawer

| Field | Specification |
|---|---|
| **Name** | Mobile Nav Drawer |
| **Purpose** | Houses all navigation links on mobile when compressed. Implements two-tier navigation on touch devices (Phase 0 §5.3). |
| **Where it appears** | Mobile breakpoint, triggered by A-04. Overlays content (Curtain gesture - Phase 1.5 §3.4). |
| **Where it must NEVER appear** | On desktop - full nav is always visible. As a modal bottom sheet on arrival (blacklist #48). |
| **Required variants** | **States:** closed (hidden) / open (visible). **Conditional:** links vary by season (Schedule in P/L only; Your Space visible differently). |
| **Replaceable?** | No - this is the standard mobile pattern for nav. |
| **Composition** | Full-screen overlay listing nav items as large touch targets (≥48px each). Paper surface (logistics calm). |
| **Accessibility** | `role="dialog"`; focus trap (keyboard cannot escape drawer to content); Escape closes; `aria-hidden=true` on content behind. |
| **Placeholder awareness** | No TBD. |

---

#### A-06: Back Affordance (Breadcrumb / Back Arrow)

| Field | Specification |
|---|---|
| **Name** | Back Affordance |
| **Purpose** | Retreat path: "how do I get back?" - part of the orientation contract (Phase 2.5 §PART 6.2 #2). Every screen beyond P-01 needs an explicit back. The spine is forward, but the retreat must be visible. |
| **Where it appears** | Top of P-03 (← Welcome), P-04 (← Landscape), P-05 (← Landscape), P-06 through P-09 (← previous step), P-12 through P-17 (← context), P-20 through P-21 (← Welcome), A-02 through A-07 (← Dashboard). |
| **Where it must NEVER appear** | On P-01 (no back from home). On P-22 Login (back = Welcome Beat). Inside Zone G sticky bars (G is forward-only). |
| **Required variants** | **States:** default / hover / focus. **Sizes:** Compact (top-line). **Formats:** Arrow-chevron prefix + destination text (e.g., "← Landscape"). |
| **Replaceable?** | Browser back is implicit, but explicit back is required by the orientation contract (Phase 2.5 §PART 6.2). Not replaceable - browser back alone fails on mobile SPA patterns. |
| **Composition** | Arrow-chevron icon + destination label (body type). |
| **Accessibility** | Link with `aria-label="Back to [destination]"`. Keyboard focusable. |
| **Placeholder awareness** | No TBD. |

---

#### A-07: Page Footer

| Field | Specification |
|---|---|
| **Name** | Page Footer |
| **Purpose** | Quiet presence: identity line + doubt-home access (Contact always findable from any page, Phase 2.5 §2.5). The footer is the last resort for navigation - it never competes with page content (Phase 2 §8.2). |
| **Where it appears** | Bottom of every public page (P-01 through P-21). Not in overlays (P-23, P-26). |
| **Where it must NEVER appear** | In admin screens (A-01 through A-07 - isolated). On the 404 Lost Slip (P-25 - the slip owns the space). On Registration Closed screen (P-24 - redirect-focused). |
| **Required variants** | **Surface:** Ink or Paper depending on the page's final zone. **States:** default only (no hover needed - compact). **Conditional:** Registration Closed / Full states suppress footer. |
| **Replaceable?** | No - "every doubt raised anywhere is one hop from their answer" (Phase 2.5 §5.2 #6). The footer is the universal hop. |
| **Composition** | Identity line (A3: "EVOKE 2026 · Host [TBD]") · Info link (→ P-19 Quiet Corners Hub) · Privacy link (→ P-18). Compact, single line on mobile. |
| **Accessibility** | `role="contentinfo"`. Keyboard accessible (Tab to links). |
| **Placeholder awareness** | Host school (A4) is TBD - honest wait posture. Footer shows "EVOKE 2K26 · [Host School]" or "EVOKE 2K26" if unresolved. |

---

### CATEGORY B: EVENT DISPLAY & DISCOVERY

#### B-01: Event Tile (The Slip Card)

| Field | Specification |
|---|---|
| **Name** | Event Tile |
| **Purpose** | The primary discovery unit: presents one event with enough to scan, not enough to decide. Answers "which one is mine?" (Phase 2 Part 3.3: curiosity peak at Landscape). The tile is a Slip - the universal container (Phase 1.5 §3.2 Device 1). |
| **Where it appears** | P-03 Landscape (all 16 events), P-12 Your Space (registered events only), A-07 Event Status Management. |
| **Where it must NEVER appear** | On P-01 (Landscape owns B1). Inside registration forms (the event is already chosen, restatement uses Review Summary - C-09). |
| **Required variants** | **States:** default / hover (desktop: lift + outline, Phase 1 §11) / focus (amber ring) / disabled (closed/full - dimmed, with text explanation, blacklist #57). **Season:** Announcement (preview-only) / Registration Open (status badge visible) / Approach (schedule-aware) / Post-Event (winner tag if available). |
| **Replaceable?** | No. The tile is the Slip manifested - no other component solves "scan 16 events without overwhelm." A list would lose visual chunking (Phase 0 §5.3). |
| **Composition** | Contains: Event Mark (B-05); Event Name (Type-D, Display); Cluster Tag (B-03); Status Badge (B-04); brief descriptor (1 line of body text). |
| **Accessibility** | `role="button"` or link; `aria-label="[Event Name] - [Cluster] - [Status]"`. Touch target ≥44px height. Keyboard-focusable, activates with Enter/Space. |
| **Placeholder awareness** | No TBD - tiles always exist (B1 is M). Content may be TBD in Announcement season, but the tile structure is stable. |

---

#### B-02: Cluster Group Header

| Field | Specification |
|---|---|
| **Name** | Cluster Group Header |
| **Purpose** | Reduces 16 events to 4 worlds, preventing scanning overwhelm (Phase 2 Part 3.3: "The chapter that is not a chapter"). Progressive disclosure: headline → category → details (Phase 0 §5.3). |
| **Where it appears** | P-03 Landscape (4 times: Stage, Mind, Art, Maker). P-04 Event Detail (as the cluster context for the event). |
| **Where it must NEVER appear** | On P-01 (clusters belong to discovery, not arrival). On P-11 Confirmation (one event only). Inside registration forms. |
| **Required variants** | **States:** default only. **Cluster type:** Stage (Amber focus) / Mind (Teal focus) / Art (Graphite focus) / Maker (Clay-warm focus) - per Bible §4.4 cluster tints. **Sizes:** Section header scale (heading type). |
| **Replaceable?** | No. Cluster headers are the "four worlds" narrowing mechanism (Phase 2 Part 3.3). Without them, 16 events = choice paralysis on mobile (Phase 2 §11.4). |
| **Composition** | Heading text (cluster name); cluster icon (B-05); event count (e.g., "4 events"). |
| **Accessibility** | `role="region"` or `aria-labelledby`; heading level H2. Keyboard focusable as landmark. |
| **Placeholder awareness** | No TBD - clusters are structural (B2, M). |

---

#### B-03: Cluster Tag

| Field | Specification |
|---|---|
| **Name** | Cluster Tag |
| **Purpose** | Instant category recognition: a student scans Event Tiles and reads cluster before name - speed of scanning (Phase 0 §2.1: students need to find "what can I do?" quickly). Color differentiation by cluster (Bible §4.4). |
| **Where it appears** | On every Event Tile (B-01); in P-03 Landscape cluster filters; on P-04 Event Detail header. |
| **Where it must NEVER appear** | On P-01 (Landscape owns discovery). As a standalone element - always attached to an event tile or header. |
| **Required variants** | **States:** default / hover / focus. **Cluster type:** Stage (Amber) / Mind (Teal) / Art (Graphite) / Maker (Clay-warm). **Background:** Ink-on-light or Paper-on-dark depending on tile surface. |
| **Replaceable?** | No - cluster tags are the scanning aid. No other component provides instant category recognition at tile density. |
| **Composition** | Short text label (e.g., "Stage") with small accent dot (cluster color). |
| **Accessibility** | `aria-label="Cluster: Stage"`. Not decorative - carries semantic info. Color never sole differentiator (blacklist #51): each tag also has text. |
| **Placeholder awareness** | No TBD. |

---

#### B-04: Status Badge

| Field | Specification |
|---|---|
| **Name** | Status Badge |
| **Purpose** | Decision honesty: tells the student whether they can register for this event RIGHT NOW (Phase 2 Part 14: failure journeys; Phase 2.5 §2.4: "Status honest"). Prevents dead taps and builds Progressive Confidence (Charter §5). |
| **Where it appears** | On Event Tiles (B-01) in P-03 Landscape. On P-04 Event Detail Zone G (decision zone). In A-07 Event Status Management. |
| **Where it must NEVER appear** | On P-01 (status belongs to Landscape/Detail, not arrival). On P-11 Confirmation (you're registered - irrelevant). As a color-only indicator (blacklist #51). |
| **Required variants** | **States:** Open (green/calm) / Closed (neutral, with text) / Full (warm, with text) / Coming Soon (neutral, Announcement season). **Conditional:** derived from B11 (computed, not hand-typed - Phase 2.5 §5.1). |
| **Replaceable?** | No. Honest status is required by failure journeys (Phase 2 Part 14). Without it, a tap on a closed event is a dead end. |
| **Composition** | Short text label + status text ("Registration Open" / "Closed" / "Full"). Never color-only. |
| **Accessibility** | `aria-label="Registration status: Open"`. Screen reader announces status. Text is always present - not decorative. |
| **Placeholder awareness** | Status is derived from admin (P-gated). During Announcement season, shows "Coming Soon" posture (Phase 2.5 §11.1). |

---

#### B-05: Event Mark (Icon)

| Field | Specification |
|---|---|
| **Name** | Event Mark |
| **Purpose** | Visual identity for each of 16 events - drawn from the event's transformation story (Phase 1 §4: personality analysis). A coordinator scanning 16 events reads them by shape before text (Bible §6). Before/after DNA made visible (Phase 1 §1.1). |
| **Where it appears** | On Event Tiles (B-01); P-04 Event Detail header (Zone A); P-12 Your Space (registered event reference). |
| **Where it must NEVER appear** | As a full-page hero image (overkill at 16 × - Phase 1 §6). Inside registration forms (the event is already identified). |
| **Required variants** | **16 unique marks** - one per event. **Sizes:** Tile size (16-24px); Detail size (48-64px). **States:** default only (non-interactive). **Surface:** Ink-on-light or Paper-on-dark. |
| **Replaceable?** | Could theoretically use text-only, but visual scanning speed for 16 events is a real user problem (Phase 0 §2.1: students are mobile-first, quick scanning). Marks are not decoration - they are wayfinding. |
| **Composition** | Filled, chunky form (event identity moments get filled forms, Bible §6). Derived from geometric parents (circle, square, triangle, line - Bible §6). |
| **Accessibility** | Decorative (`aria-hidden="true"`) - event name carries the semantic info. Never relied upon alone. |
| **Placeholder awareness** | Phase 2 deliverable (Phase 1.5 §2.2 item 5, Bible 15.1). Placeholder marks acceptable during early builds. |

---

#### B-06: Event Detail Section Divider

| Field | Specification |
|---|---|
| **Name** | Event Detail Section Divider |
| **Purpose** | Visual chunking within the highest-density screen (P-04). Each section (Personality, Quick Facts, Rules, etc.) needs a scene break (Phase 1.5 §4.1: "sections are scenes"). The divider is the hush between sections. |
| **Where it appears** | P-04 Event Detail only - between Zones B through F. |
| **Where it must NEVER appear** | In registration flows (P-06 through P-09 - linear, no scene breaks needed). On P-01 (minimal screen). |
| **Required variants** | **States:** default only. **Types:** Thin line with cluster color; generous spacing block (the settlement, Phase 1.5 §4.1). |
| **Replaceable?** | Could use cards instead, but P-04 already uses heavy card density for Quick Facts (C-07) and Rules. The divider is lighter - prevents visual overload. |
| **Composition** | 1px warm outline (Bible §7: a single signature frame language) or generous whitespace. |
| **Accessibility** | Decorative - no semantic role. Screen readers ignore. |
| **Placeholder awareness** | No TBD. |

---

### CATEGORY C: FORMS & INPUT

#### C-01: Text Input (The Registration Desk)

| Field | Specification |
|---|---|
| **Name** | Text Input |
| **Purpose** | Collects participant data during registration. Warm, paper-surface feel - the Registration Desk (Bible §11). Clear labels above inputs (Bible §11) - never placeholder-only (accessibility, Phase 0 §12.7). |
| **Where it appears** | P-07 Registration Step 2 (Participant Info); P-22 Login (credentials); A-03 Content Management (admin edits). |
| **Where it must NEVER appear** | On P-01 or P-03 (public discovery - no data collection). On P-11 Confirmation (read-only - C-09 uses Review Summary). |
| **Required variants** | **States:** default / focus (amber ring, visible - Bible §11) / error (danger red + text, never color alone - blacklist #51) / disabled (with explanation - blacklist #57) / filled / readonly. **Types:** text / email / phone. **Sizes:** Full-width (mobile) / Standard (desktop). |
| **Replaceable?** | No. Form data capture requires text inputs. Could be replaced by dropdown for constrained inputs (C-02). |
| **Composition** | Label (above, body type) / Input field (warm paper surface) / Error message (inline, below) / Helper text (optional). |
| **Accessibility** | `aria-describedby` for error/helper text; `aria-invalid` on error; `aria-required` on mandatory. Focus ring: single warm amber (Bible §11). Touch target ≥44px. Screen reader announces label + error + type. |
| **Placeholder awareness** | Field list is TBD (C4, Charter §7). Component exists; which fields appear is deferred. |

---

#### C-02: Select Dropdown

| Field | Specification |
|---|---|
| **Name** | Select Dropdown |
| **Purpose** | Constrained choice: school selection, class selection, or event-type selectors where the answer is a known set (Phase 0 Q22: what fields are needed). More compact than radio buttons on mobile. |
| **Where it appears** | P-07 Registration Step 2 (school, class - TBD). A-07 Event Status Management (status selection). |
| **Where it must NEVER appear** | On P-03 Landscape (filter uses B-07 Cluster Filter Toggle, not a raw select). On P-01 (no inputs). |
| **Required variants** | **States:** default / focus / open / error / disabled. **Sizes:** Full-width (mobile), standard (desktop). |
| **Replaceable?** | Radio buttons for small sets (<5 options). Custom select for large sets - same problem solved differently. |
| **Composition** | Label (above) / Select field / Chevron indicator. |
| **Accessibility** | Native `<select>` or custom with `role="listbox"`. Keyboard: Arrow keys navigate, Enter selects. Screen reader announces options. |
| **Placeholder awareness** | Option lists TBD (school list, class list - depends on organizer data). |

---

#### C-03: Add/Remove Team Member Block

| Field | Specification |
|---|---|
| **Name** | Team Member Block |
| **Purpose** | Handles variable team size (team events: 2-8 members per event, Phase 0 §3.1). Solves "I need to enter my teammates' names" - a coordinator registering a team of 5 faces this 5 times. |
| **Where it appears** | P-07 Registration Step 2 only, for team-format events. |
| **Where it must NEVER appear** | On solo events (Solo Song is solo, Face Painting max 2 - conditional by event type). On P-22 Login. |
| **Required variants** | **States:** default / focus / error on any field. **Conditional:** 1-8 instances per event (enforced by event's team rule from B4, Phase 0 §3.1). Add button appears until max reached. |
| **Replaceable?** | No. Variable-repeat field sets require a repeatable block. |
| **Composition** | Member number label ("Member 1") / Text Input for name (C-01) / Text Input for class (C-01) / Remove button (conditional, never for last member). |
| **Accessibility** | Each member grouped with `aria-labelledby`. Remove button has aria-label "Remove Member [n]". Min member count enforced: cannot remove to zero. |
| **Placeholder awareness** | Team size limits depend on event (B4). Solo events → this component is hidden. |

---

#### C-04: Agreement Checkbox

| Field | Specification |
|---|---|
| **Name** | Agreement Checkbox |
| **Purpose** | Explicit acknowledgement: participant confirms they understood key rules before proceeding (Phase 2 Part 10.2: certainty before the doorway). Builds trust - the act is informed, not assumed. |
| **Where it appears** | P-08 Registration Step 3 (Declaration & Agreement). May appear in P-10 Payment (terms acceptance - if TBD requires). |
| **Where it must NEVER appear** | On P-01 or P-03 (no commitments in discovery). As a pre-checked box (Phase 2 Part 15.4: no hidden terms). |
| **Required variants** | **States:** unchecked / checked / focus. **Conditional:** Required to proceed - CTA disabled if not checked (with visible explanation - blacklist #57). |
| **Replaceable?** | Radio (yes/no) is equivalent but checkbox is the convention for acknowledgement. |
| **Composition** | Checkbox element / Label text ("I agree to the event rules and understanding the judges' decision is final") / Link to full rules (→ P-04). |
| **Accessibility** | `aria-required` when mandatory. `role="checkbox"`. Keyboard: Space to toggle. Screen reader: "agreement checkbox, not checked" / "checked". |
| **Placeholder awareness** | Agreement text content is TBD (rules evolve). Component structure is stable. |

---

#### C-05: Step Progress Indicator

| Field | Specification |
|---|---|
| **Name** | Step Progress Indicator |
| **Purpose** | "Where am I, how much is left?" - reduces anxiety in multi-step registration (Phase 2 Part 10.3: declared steps). Progressive Confidence: visibility of progress builds certainty (Charter §5). |
| **Where it appears** | P-06 through P-09 (top of each registration step - Zone A). Only visible during active registration flow. |
| **Where it must NEVER appear** | On P-01 through P-05 (public - no registration context). On P-11 Confirmation (complete). On P-10 Payment if gateway provides its own progress (avoid duplication, Phase 2.5 §9). |
| **Required variants** | **States:** step-complete (checkmark) / step-current (highlighted) / step-future (dimmed) / step-error (red, if validation failed mid-flow). **Formats:** Numbered dots (mobile, compact) / Horizontal bar with labels (desktop). **Steps:** 4 or 5 (payment step conditional - TBD). |
| **Replaceable?** | Text-only progress ("Step 2 of 4") is equivalent but adds cognitive load without visual cue. The indicator is a visual progress signal, not a text instruction. |
| **Composition** | Dot/step indicator × N (4 or 5) / Optional step labels / Connecting line (current → future). |
| **Accessibility** | `role="progressbar"` or `aria-valuetext="Step 2 of 4"`. Screen reader announces step position on focus. |
| **Placeholder awareness** | Step count depends on whether payment is required (TBD - P-10 may or may not exist). Component supports 4 or 5 steps **and a conditional fifth marker** for the state where fee existence itself is unknown (Amendment AM-05). It must never assert a total it cannot support. |

---

#### C-06: Inline Form Validation Message

| Field | Specification |
|---|---|
| **Name** | Inline Form Validation Message |
| **Purpose** | Answers input errors in-place, in the Ringmaster's honest voice (Phase 2 Part 14.3; Bible §11: errors shown with text, never color alone). Prevents confusion at the form - the form never blames. |
| **Where it appears** | Below any Text Input (C-01) or Select (C-02) in error state. P-07 Registration Step 2 primarily. |
| **Where it must NEVER appear** | On P-01, P-03, P-04 (no forms). As a modal popup (blacklist #48). |
| **Required variants** | **States:** hidden (default) / visible (error). **Content:** Validation-specific ("Please enter a valid email" / "This field is required"). |
| **Replaceable?** | No. In-line validation is required for form UX - no dead-end pattern exists for this. |
| **Composition** | Danger-red text (body type) / Error icon (optional, never sole indicator). |
| **Accessibility** | `role="alert"` for inline errors; `aria-describedby` links input to error text. Screen reader announces error as user tabs to the field. |
| **Placeholder awareness** | No TBD - validation messages are structural. |

---

#### C-07: Quick Fact Card

| Field | Specification |
|---|---|
| **Name** | Quick Fact Card |
| **Purpose** | Scannable decision support: team size, time limit, eligibility - the facts a student checks before committing (Phase 2 Part 10.1: "Can I participate?"). Density is content-typed (Phase 1.5 §11.3: event detail = rich). |
| **Where it appears** | P-04 Event Detail, Zone C (Quick Facts). 3-5 per event in a grid/facts panel. |
| **Where it must NEVER appear** | On P-03 Landscape (tiles carry less detail). Inside registration forms (B-01 Event Tile or review summary used instead). |
| **Required variants** | **States:** default only. **Content types:** Team size ("Solo" / "2-4" / etc.) / Time limit ("Max 2 min" / "1 hour") / Eligibility / Theme (conditional - only where B5 exists). |
| **Replaceable?** | Could be plain text, but the quick-fact question is answered in 3 seconds, not 30 - the card format is speed (Phase 0 §2.1: scanning). |
| **Composition** | Label (small text above, e.g., "Team Size") / Value (body medium, e.g., "2 members") / Optional icon. |
| **Accessibility** | Label + value in a data pair (`role="group"`, or visually structured). Screen reader reads: "Team Size: 2 members." |
| **Placeholder awareness** | Content is M (B4, B6 from Phase 2.5). Theme (B5) conditional - appears only on events with a defined theme. |

---

#### C-08: Rules List Item

| Field | Specification |
|---|---|
| **Name** | Rules List Item |
| **Purpose** | Faithful rule presentation: each rule as a discrete Slip (Phase 1.5 §4.2: "one slip = one thought"). Rules are the contract - readable, scannable, one per item (Phase 0 12.6: content drives design). |
| **Where it appears** | P-04 Event Detail, Zone D (Rules). P-05 Rules & Eligibility, Zone B (General Rules). P-08 Registration Step 3 (summary rules only, not full text). |
| **Where it must NEVER appear** | On P-03 Landscape (too dense for scanning). As images (blacklist #45: rules as images). |
| **Required variants** | **States:** default only. **Format:** Numbered items with clear hierarchy. Sub-bullets where needed (prohibition → detail). |
| **Replaceable?** | Accordion is not allowed here (blacklist #44: infinite accordion nesting of rules). Plain text block is worse (not scannable on mobile). |
| **Composition** | Rule number / Rule text (Body type, readable at small sizes) / Sub-items if nested. |
| **Accessibility** | Ordered list (`<ol>`) or unordered (`<ul>`). Screen reader announces item count. |
| **Placeholder awareness** | No TBD - rules are M (B7). Content evolves from rule book, not invented. |

---

#### C-09: Review Summary Block

| Field | Specification |
|---|---|
| **Name** | Review Summary Block |
| **Purpose** | The final mirror: restates everything the participant chose before they commit (Phase 2 Part 10.2: "the act's punctuation"; Part 10.3: no surprises). Builds certainty - the last thought is "yes." |
| **Where it appears** | P-09 Registration Step 4 (Review & Confirm). P-11 Confirmation (stamped version - success state). Inside P-12 Your Space (registration record). |
| **Where it must NEVER appear** | Mid-registration (P-07 P-08 - premature restatement raises doubt). On P-01, P-03, P-04 (not committed yet). |
| **Required variants** | **States:** default / stamped (P-11, with Stamp gesture - Phase 1.5 Part 6.4). **Content:** Event name, cluster, team members, school, class, agreed rules (summary). |
| **Replaceable?** | No. The review-and-confirm step is required by the psychological contract (Phase 2 Part 10.3). |
| **Composition** | Label-value pairs (Event: X / Participants: Y / Team: Z) / "Edit" links to relevant step. |
| **Accessibility** | Read-only content. `aria-readonly`. Screen reader reads each pair. Edit links are actionable. |
| **Placeholder awareness** | Content is derived from what was entered - no TBD. |

---

#### C-10: Primary CTA Button (The Stage Cue)

| Field | Specification |
|---|---|
| **Name** | Primary CTA Button |
| **Purpose** | The Stage Cue (Bible §11: "Chunky, generous height, amber-on-ink or ink-on-paper"). One primary action per screen (Phase 0 §5.3: one action per screen). The button is the hand-off - it says "your next step." |
| **Where it appears** | Every screen with a primary action: P-01 (Explore Events), P-04 Zone G (Register), P-06 through P-09 (Continue/Confirm), P-11 (Go to Your Space), P-12 (Register More), P-13 (Explore Events), P-24/P-27 (redirect), P-25 P-27 (Go back). |
| **Where it must NEVER appear** | Competing with another CTA on the same screen (Phase 2 §8.1: one primary message). Color-only status (blacklist #51). |
| **Required variants** | **States:** default / hover (brightness shift + 1-unit rise, Bible §11) / focus (amber ring) / pressed (settle down) / disabled (with explanation). **Surfaces:** Amber-on-Ink (identity moments) / Ink-on-Paper (logistics). **Sizes:** Standard (generous height, chunky - Bible §11). Minimum touch target 44px height. |
| **Replaceable?** | No. One primary action per screen is a platform principle. The button is the most used interactive component. |
| **Composition** | Label text (Body, medium weight, uppercase on identity, normal on logistics - Bible §5.2). |
| **Accessibility** | `role="button"` or `<button>`. Keyboard: Enter/Space activates. aria-disabled with explanation. Touch ≥44px. |
| **Placeholder awareness** | Disabled states during Announcement/Live/Post may carry honest text ("Registration opens soon"). |

---

#### C-11: Secondary Action Button

| Field | Specification |
|---|---|
| **Name** | Secondary Action Button |
| **Purpose** | Non-primary exit paths: "Back", "Cancel", "Edit", "Contact" - options that exist but don't compete with the forward motion (Phase 2 §8.1: primary never competes). Visible but not dominant. |
| **Where it appears** | P-04 (Back to Landscape, View Rules), P-06 through P-09 (Back, Cancel), P-11 (Register another, Share), P-14 (Filter, View Detail), P-24/P-27 (alternative exits). |
| **Where it must NEVER appear** | Competing with Primary CTA on the same screen in equal weight. As the only visible action (primary must always lead). |
| **Required variants** | **States:** default / hover / focus / disabled. **Styles:** Outlined (ink outline on paper) / Ghost (text only, subtle). **Sizes:** Compact (less height than Primary). |
| **Replaceable?** | Could be a link (C-16), but buttons for actions (edit, cancel, back) are more explicit about their consequences. |
| **Composition** | Label text (Body, regular weight). |
| **Accessibility** | Same as Primary CTA - same keyboard/screen reader treatment. Touch target ≥44px. |
| **Placeholder awareness** | No TBD. |

---

#### C-12: FAQ Accordion Item

| Field | Specification |
|---|---|
| **Name** | FAQ Accordion Item |
| **Purpose** | Progressive disclosure of answers: one question visible, answer revealed on tap (Phase 0 §5.3). Prevents overwhelming the reader with all FAQ answers at once while keeping the FAQ scannable (question titles visible at a glance). |
| **Where it appears** | P-04 Event Detail, Zone F (per-event FAQ, B10). P-16 FAQ (global FAQ, E1). |
| **Where it must NEVER appear** | For rules (B7) - rules must be always visible, not hidden behind accordion (blacklist #44). On P-01 or P-03. |
| **Required variants** | **States:** collapsed (default) / expanded / focus. **Conditional:** Only rendered for FAQ items that have answers (Phase 2.5 §10.1: no empty FAQ items). |
| **Replaceable?** | No - FAQ items are naturally expandable/collapsible. |
| **Composition** | Question text (always visible, body medium) / Answer text (hidden until expanded, body regular) / Chevron indicator (expand/collapse state). |
| **Accessibility** | `role="button"` on question; `aria-expanded` toggles; `id`/`aria-controls` linking question to answer. Keyboard: Enter/Space expands, Tab skips to next question. |
| **Placeholder awareness** | FAQ content evolves organically - items appear as questions are answered. No empty items rendered. |

---

### CATEGORY D: DASHBOARD (YOUR SPACE)

#### D-01: Dashboard Greeting Card

| Field | Specification |
|---|---|
| **Name** | Dashboard Greeting Card |
| **Purpose** | Personalized orientation: "Welcome back, [Name]" - the participant knows this is their space. Combined with C7 (what changed), it answers "what's different since I was here?" (Phase 2 Part 8.3: returning attention is greeted by change). |
| **Where it appears** | P-12 Your Space, Zone A (top, full-width). |
| **Where it must NEVER appear** | On P-13 Empty State (not registered yet). On public pages. In registration flow. |
| **Required variants** | **States:** default. **Content:** Name (C6 - placeholder auth). **Season-aware greeting:** Contextual text ("Registration is open" / "Schedule is published" / "Festival is live"). |
| **Replaceable?** | No - the greeting + delta (what changed) is the return engine's first impression. |
| **Composition** | Name greeting / Delta indicator (D-03, inline) / Season context text. |
| **Accessibility** | `aria-live="polite"` for the delta count (changes announced to screen reader). |
| **Placeholder awareness** | Name depends on auth model (C6 TBD). Component exists; content is P-gated. |

---

#### D-02: Registration Record Card

| Field | Specification |
|---|---|
| **Name** | Registration Record Card |
| **Purpose** | The persistent receipt in the participant's home: what events they registered for, with current status. "Retrievability: record always reachable via Your Space" (Phase 2 Part 19.2 → Phase 2.5 invariant 2.4). |
| **Where it appears** | P-12 Your Space, Zone B (My Registrations). Scrollable list of records. |
| **Where it must NEVER appear** | On P-13 Empty State. On P-01, P-03, P-04. Unauthenticated. |
| **Required variants** | **States:** default / focus. **Status:** Active / Confirmed / Pending (payment TBD). |
| **Replaceable?** | No - record cards are the dashboard's core content. |
| **Composition** | Event name / Cluster tag (B-03) / Registration status / "View Details" link (→ P-04) / Confirmation reference. |
| **Accessibility** | Each card is a group. Links are keyboard-accessible. `aria-label="Registration for [Event] - Status: [Status]"`. |
| **Placeholder awareness** | Content is C5-derived - always exists after registration. |

---

#### D-03: Delta Indicator ("What Changed")

| Field | Specification |
|---|---|
| **Name** | Delta Indicator |
| **Purpose** | "2 new announcements" / "Your registration status updated" - the heartbeat signal that the platform is alive (Phase 0 12.5: announcements as source of truth). Every visit gives one clear "what now?" (Phase 2 Part 8.3). |
| **Where it appears** | P-12 Your Space, Zone A (inside Dashboard Greeting Card D-01). |
| **Where it must NEVER appear** | On P-01 through P-11 (no return-visit context outside Your Space). On first visit (no delta exists). |
| **Required variants** | **States:** default (no changes) / active (N items changed) / focus. **Content types:** New announcements / Status changes / Schedule updates. |
| **Replaceable?** | No - this is the "return engine" differentiator. Without it, Your Space is just a static list. |
| **Composition** | Count badge + descriptive text ("3 new" / "Status updated"). |
| **Accessibility** | `aria-live="polite"` - screen reader announces change count. |
| **Placeholder awareness** | Delta computed from C7 - stable structure. |

---

#### D-04: Announcement Card

| Field | Specification |
|---|---|
| **Name** | Announcement Card |
| **Purpose** | Source-of-truth updates: replaces WhatsApp notifications (Phase 0 12.5). Every announcement is a Slip - content lives on the container, not chrome (Phase 1.5 §3.2). |
| **Where it appears** | P-12 Your Space, Zone C (Announcements section). P-01 Welcome Beat (latest announcement only, as a display element - single source, Phase 2.5 §9). |
| **Where it must NEVER appear** | On P-03 Landscape or P-04 Event Detail (announcements are Your Space + Welcome). Inside registration forms. |
| **Required variants** | **States:** default / read (visually deprioritized). **Conditional:** newest first; older announcements collapse on mobile (progressive disclosure). |
| **Replaceable?** | No. Announcements are the communication channel. |
| **Composition** | Title / Timestamp / Body text / "Read more" (if truncated). |
| **Accessibility** | `role="article"`. Timestamp is `time` element with `datetime`. |
| **Placeholder awareness** | Published by admin (D1) - always has content after first announcement. |

---

#### D-05: Dashboard Action Group

| Field | Specification |
|---|---|
| **Name** | Dashboard Action Group |
| **Purpose** | Season-aware next steps: "Register More" / "View Schedule" / "View Results" - the dashboard always gives a clear forward action determined by season state G1 (Phase 2.5 §8.1). |
| **Where it appears** | P-12 Your Space, Zone D (bottom). |
| **Where it must NEVER appear** | On P-13 Empty State (no registrations, different CTA). On P-01. |
| **Required variants** | **States:** default / focus. **Conditional actions by season:** Registration Open (Register More) / Approach (View Schedule) / Live (View Live Schedule) / Post-Event (View Winners / View Gallery). |
| **Replaceable?** | Could be links, but button treatment gives them the weight of "next step" - they are decisions. |
| **Composition** | 1-3 secondary action buttons (C-11 or links, depending on action weight). |
| **Accessibility** | Each button/link is keyboard-navigable. `aria-label` describes destination. |
| **Placeholder awareness** | Schedule link is P-gated by season (D2 TBD content). Winners/Gallery links F-gated (D3/D4 TBD). |

---

### CATEGORY E: SCHEDULE

#### E-01: Schedule Day Header

| Field | Specification |
|---|---|
| **Name** | Schedule Day Header |
| **Purpose** | Temporal orientation: groups events by day. Answers "when does my event happen?" - logistics trust for coordinators and participants (Phase 2.5 §3.8, Part 2.2 area map: Schedule = logistics). |
| **Where it appears** | P-14 Schedule, as section headers dividing timeline by day. |
| **Where it must NEVER appear** | On P-01 through P-13. Inside registration flow. |
| **Required variants** | **States:** default. **Content:** Date (tabular numerals - Bible §5.1), day name, optional day number. |
| **Replaceable?** | No. Date grouping is the standard schedule pattern. |
| **Composition** | Date display (Display or Heading type) / Day name (Body). |
| **Accessibility** | `role="heading"` or actual heading element (`<h3>`). Screen reader reads "Day 1 - [Date]." |
| **Placeholder awareness** | Schedule content is D2 TBD. Component exists; dates are P-gated. |

---

#### E-02: Schedule Time Slot Card

| Field | Specification |
|---|---|
| **Name** | Schedule Time Slot Card |
| **Purpose** | "My event's time and venue" - the concrete logistics a participant checks (Phase 2.5 §3.8). The Clock motif is the festival's time language (Phase 1.5 §6.6). |
| **Where it appears** | P-14 Schedule, within each day section. |
| **Where it must NEVER appear** | Inside registration flow. On P-04 Event Detail (links to Schedule, doesn't display slots - single source, Phase 2.5 §5.1/9). |
| **Required variants** | **States:** default / focus / upcoming (highlighted) / in-progress (if Live season, if real-time exists). **Conditional:** Venue (P-gated - Q2 TBD). |
| **Replaceable?** | No - individual time slots require individual cards. |
| **Composition** | Time (tabular numerals, bold) / Event name / Venue (if resolved) / "View Details" link (→ P-04). |
| **Accessibility** | Time element with `datetime`. Screen reader reads "[Event] at [Time], [Venue]." |
| **Placeholder awareness** | Times and venue TBD (Q6, Q2). Component renders honest posture when data is missing. |

---

#### E-03: Schedule Cluster Filter

| Field | Specification |
|---|---|
| **Name** | Schedule Cluster Filter |
| **Purpose** | Reduces schedule scanning to a participant's relevant cluster - "just show my events." Coordinator optimization (Phase 0 §2.2: checklist-driven). |
| **Where it appears** | P-14 Schedule, Zone B (filter area). |
| **Where it must NEVER appear** | On P-03 Landscape (uses I-04 Cluster Filter Toggle there). |
| **Required variants** | **States:** default (All) / active per cluster. **Filter values:** All / Stage / Mind / Art / Maker. |
| **Replaceable?** | No - cluster filtering is essential for coordinator scanning with 16 events. |
| **Composition** | Toggle chips (4 clusters + All). |
| **Accessibility** | `role="group"` with `aria-pressed` on chips. Keyboard: Tab through, Space toggles. |
| **Placeholder awareness** | No TBD - structural. |

---

### CATEGORY F: FEEDBACK & SYSTEM

#### F-01: Skeleton Loading Frame

| Field | Specification |
|---|---|
| **Name** | Skeleton Loading Frame |
| **Purpose** | Instant-over-delight loading (Bible §11). Slip skeleton with amber pulse - the brand holds during wait (Phase 1.5 §11.2: slip universality). No spinners (Bible §11). |
| **Where it appears** | Transitional state on any page (P-01 through P-22, A-01 through A-07). |
| **Where it must NEVER appear** | Beyond first load (Bible §11: "no spinners beyond first load"). For instant operations (<200ms - no loading needed). |
| **Required variants** | **Shapes:** Single slip (one card) / Stack (multiple rows) / Text line (heading shape). Surface: Ink or Paper context. |
| **Replaceable?** | No - loading must be branded (Phase 1.5 slip universality). Spinners are forbidden (Bible §11). |
| **Composition** | Slip outline wireframe + amber pulse animation (150-250ms cycle). |
| **Accessibility** | `role="status"` with `aria-live="polite"` and announcement "Loading content". Reduced motion: static skeleton without pulse (Phase 1.5 §3.5). |
| **Placeholder awareness** | No TBD. |

---

#### F-02: Error Banner (Overlay)

| Field | Specification |
|---|---|
| **Name** | Error Banner |
| **Purpose** | Calm, informed, hopeful recovery (Phase 2 Part 14). Network failure overlay - does not replace the page, the world doesn't reset (Phase 2 §23: "an overlay, not a page"). |
| **Where it appears** | Overlay on any screen (P-01 through P-22) during network failure. Registration flow overlay (especially P-10 Payment). |
| **Where it must NEVER appear** | As a full-page redirect for recoverable errors (network = retry, not dead end). At page load for non-fatal warnings. |
| **Required variants** | **States:** hidden / visible. **Content:** Network error / Generic error / Session expired. **CTA:** "Try Again" primary / "Finish later" secondary. |
| **Replaceable?** | No - inline error banners are the standard for transient failures. |
| **Composition** | Error message text (Ringmaster voice - Phase 2 Part 14.3) / "Try Again" button / "Finish later" link. |
| **Accessibility** | `role="alert"` - announced immediately to screen reader. Focus moves to the banner on appearance (Phase 2 Part 20). |
| **Placeholder awareness** | No TBD. |

---

#### F-03: Success Toast

| Field | Specification |
|---|---|
| **Name** | Success Toast |
| **Purpose** | Micro-feedback: "Registration saved" - progress feedback builds trust (Phase 2 Part 15.1: "every action leaves a visible mark"). Short, dismisses on its own. |
| **Where it appears** | Overlay on P-07/P-08 after save/pause. A-03 after content save. A-05 after publish. |
| **Where it must NEVER appear** | As the confirmation mechanism (P-11 is the confirmation - a toast is micro, not macro). On P-01. |
| **Required variants** | **States:** hidden / visible (auto-dismiss ~3s). **Content:** Saved / Published / Updated. |
| **Replaceable?** | Could use inline status, but toasts are non-intrusive and auto-dismiss - lower cognitive load for micro-feedback. |
| **Composition** | Success text (body, calm green - Bible §4.4) / Auto-dismiss timer. |
| **Accessibility** | `role="status"` with `aria-live="polite"`. Screen reader announces. |
| **Placeholder awareness** | No TBD. |

---

#### F-04: Waiting Slip (Empty State)

| Field | Specification |
|---|---|
| **Name** | Waiting Slip |
| **Purpose** | The negative-space message: "this slip waits for your name" (Phase 1.5 §11.1.6). Negative space IS the message - not decorative emptiness. Turns a dead end into an invitation. |
| **Where it appears** | P-13 Your Space - Empty State. Potentially in P-03 Landscape if no events exist for a cluster (edge case). |
| **Where it must NEVER appear** | As "no results found" in search - that uses a different empty-state language. On P-11 Confirmation (you registered - not empty). |
| **Required variants** | **States:** default only. **Content:** "This slip is waiting for your name" + "Explore Events" CTA. |
| **Replaceable?** | No - the Waiting Slip is a Named Exception (Phase 1.5 §11.1.6) and must use Slip language. |
| **Composition** | Empty Slip frame (large, centered) / Message text / CTA button (C-10). |
| **Accessibility** | `role="main"` for empty state content. Screen reader reads message and CTA. |
| **Placeholder awareness** | No TBD. |

---

#### F-05: Lost Slip (404 Display)

| Field | Specification |
|---|---|
| **Name** | Lost Slip |
| **Purpose** | Named exception: the torn, empty slip (Phase 1.5 §11.1.5). The only page allowed to be offstage - memorable, solves the dead-link problem. |
| **Where it appears** | P-25 (404) only. |
| **Where it must NEVER appear** | Anywhere else - this is the one named exception to the grammar. |
| **Required variants** | **States:** default only. |
| **Replaceable?** | No - the Lost Slip is a Named Exception. |
| **Composition** | Torn/voided Slip visual / "This slip got lost" text / "Go back" CTA (C-10) / Secondary links → P-03 Landscape, P-19 Hub. |
| **Accessibility** | `role="main"`. Screen reader reads message and navigation. |
| **Placeholder awareness** | No TBD. |

---

### CATEGORY G: QUIET CORNERS

#### G-01: Quiet Corners Hub Grid

| Field | Specification |
|---|---|
| **Name** | Quiet Corners Hub Grid |
| **Purpose** | Prevents footer clutter from becoming a menu of decisions (Phase 2.5 §P-19). Single entry into quiet pages - routes to specific doubt area in one tap. |
| **Where it appears** | P-19 Quiet Corners Hub, Zone B. |
| **Where it must NEVER appear** | In the footer itself (footer links to P-19, not to all 4 screens directly). On P-01. |
| **Required variants** | **States:** default / hover / focus. **Layout:** Single-column stack (mobile) / 2×2 grid (desktop). |
| **Replaceable?** | Could be a simple link list, but the hub screen (P-19) is designed to prevent footer overcrowding - the grid gives the links proper weight. |
| **Composition** | 4 link cards: About (→ P-15), FAQ (→ P-16), Contact (→ P-17), Privacy (→ P-18). Each card shows topic + brief descriptor. |
| **Accessibility** | Links are keyboard-accessible. `aria-label` on each. |
| **Placeholder awareness** | No TBD - hub exists whether content exists (honest postures handle TBD content). |

---

#### G-02: Contact Detail Block

| Field | Specification |
|---|---|
| **Name** | Contact Detail Block |
| **Purpose** | The doubt-home: shows organizer contact information - a real path to a human (Phase 2.5 §3.9). Every failure journey eventually leads here (Phase 2 Part 15.2). |
| **Where it appears** | P-17 Contact screen, Zone B. |
| **Where it must NEVER appear** | On P-01 (too dense for arrival). Inside registration forms without doubt context. |
| **Required variants** | **States:** default / TBD (honest posture). **Content variants:** Phone (if resolved) / Email (if resolved) / School admin interim (if real). |
| **Replaceable?** | No. The contact block is the trust anchor for quiet corners. |
| **Composition** | Contact label (e.g., "Phone") / Value (phone number, email) / "Copy"/"Call" actions (if applicable). |
| **Accessibility** | `role="group"`. Phone numbers as `tel:` links. Screen reader reads contact type + value. |
| **Placeholder awareness** | Contact is TBD (Q12). If no real contact exists, the affordance is not published (Phase 2.5 §10.1) - rather than invent one. |

---

#### G-03: Privacy Text Block

| Field | Specification |
|---|---|
| **Name** | Privacy Text Block |
| **Purpose** | Student-data trust: explains how participant data is handled, stored, used (Phase 0 Risk 14). Required - not optional. |
| **Where it appears** | P-18 Privacy screen, Zone B. Link to full policy from registration flow (P-08 or P-07). |
| **Where it must NEVER appear** | As inline text inside registration forms (too long, too important to be skippable). On P-01. |
| **Required variants** | **States:** default. **Content:** Structural (M) but exact wording is P (content TBD). |
| **Replaceable?** | No - privacy is a legal/trust requirement. |
| **Composition** | Heading / Paragraphs / References to data collected (C4 link). |
| **Accessibility** | Readable plain text structure. Headings, paragraphs, links as semantically appropriate. |
| **Placeholder awareness** | Content TBD - structural requirement (Phase 0 Risk 14). Honest posture until official content exists. |

---

### CATEGORY H: ADMIN

#### H-01: Admin Table

| Field | Specification |
|---|---|
| **Name** | Admin Table |
| **Purpose** | Operational data display: registration list, event status list, content inventory. Coordinator's operational necessity (Phase 0 Q22: registration data). |
| **Where it appears** | A-02 Dashboard (summary), A-04 Registrations, A-07 Event Status. |
| **Where it must NEVER appear** | On any participant-facing screen (public uses cards, not tables - blacklist #32: table-heavy homepage - and Phase 0 12.1: never dashboard feel). |
| **Required variants** | **States:** default / sorted (column active) / filtered. **Content:** Registration rows / Event rows / Content rows. |
| **Replaceable?** | For admin only - tables are the appropriate data view. Participant screens never use this. |
| **Composition** | Column headers / Data rows / Row actions (view, edit, export). |
| **Accessibility** | `role="table"` with `scope="col"` and `scope="row"`. Keyboard navigable. Screen reader announces table structure. |
| **Placeholder awareness** | No TBD - admin tools are structural (M/P for content). |

---

#### H-02: Admin Toggle Switch

| Field | Specification |
|---|---|
| **Name** | Admin Toggle Switch |
| **Purpose** | Binary state control: season flip (A-06), event open/closed (A-07), publish/archive (A-05). One toggle controls the entire platform's visibility (Phase 2.5 §A-06). |
| **Where it appears** | A-06 Season & State Control, A-07 Event Status Management, A-05 Announcement Publishing. Admin area only. |
| **Where it must NEVER appear** | On participant-facing screens. As a public-facing toggle - never. |
| **Required variants** | **States:** off / on / focus. **Labels:** Always paired with label text (Announcement ↔ Registration Open ↔ Approach ↔ Live ↔ Post-Event for season). |
| **Replaceable?** | Radio buttons or dropdowns for multi-state; toggle is correct for on/off. |
| **Composition** | Toggle element / Label text / Current state indicator. |
| **Accessibility** | `role="switch"`, `aria-checked` toggles, `aria-label` with full state name. Keyboard: Space or Enter toggles. |
| **Placeholder awareness** | No TBD. |

---

#### H-03: Admin Content Editor

| Field | Specification |
|---|---|
| **Name** | Admin Content Editor |
| **Purpose** | Organizer editable content: rules, descriptions, FAQ entries - without code (Phase 0 Risk 9: forbidden). The organizer's content engine. |
| **Where it appears** | A-03 Content Management only. |
| **Where it must NEVER appear** | On any participant-facing screen. |
| **Required variants** | **States:** editing / preview / saved. **Content types:** Text (rules, descriptions) / List (FAQ entries) / Structured (event facts). |
| **Replaceable?** | Could use inline editing, but a dedicated editor panel prevents accidental edits. |
| **Composition** | Text area or structured form fields / Preview button / Save button / Cancel button. |
| **Accessibility** | `aria-label` on editor area. Save/Cancel are standard buttons. |
| **Placeholder awareness** | No TBD - structural. |

---

#### H-04: Admin Status Summary Card

| Field | Specification |
|---|---|
| **Name** | Admin Status Summary Card |
| **Purpose** | At-a-glance operational status: registration count, current season, content pending. The organizer's control panel (Phase 2.5 §3.11). |
| **Where it appears** | A-02 Admin Dashboard, top zone. |
| **Where it must NEVER appear** | On participant-facing screens - no KPI-card grids (Phase 0 §12.1 / Bible blacklist #30). |
| **Required variants** | **States:** default. **Data:** Season state / Registration count / Content status / Pending items. |
| **Replaceable?** | No - admin needs an overview. |
| **Composition** | Metric label / Value / Trend indicator (up/down, if relevant). |
| **Accessibility** | Screen reader reads label + value. |
| **Placeholder awareness** | No TBD. |

---

#### H-05: Admin Export Button

| Field | Specification |
|---|---|
| **Name** | Admin Export Button |
| **Purpose** | Data export: CSV/Excel dump of registrations - the organizer's operational outpath (Phase 0 Q22, §7.4). |
| **Where it appears** | A-04 Registration Management. |
| **Where it must NEVER appear** | On participant-facing screens. |
| **Required variants** | **States:** default / processing / focus. **Formats:** CSV / Excel (TBD which formats supported). |
| **Replaceable?** | No - export is the operational necessity. |
| **Composition** | "Export" label / Optional format dropdown. |
| **Accessibility** | `aria-label="Export registrations as [format]"`. Keyboard: Enter activates. |
| **Placeholder awareness** | Export format TBD. Component structural. |

---

### CATEGORY I: SYSTEM & SUPPORT

#### I-01: Typography Scale (Type Tokens)

| Field | Specification |
|---|---|
| **Name** | Typography Scale |
| **Purpose** | Three-level hierarchy (Bible §5.1): Display (announce), Heading (direct), Body (explain). "If something cannot fit the three, it is probably decoration." Scale contrast between Display and Body is the visual system's primary tool (Bible §5.1). |
| **Where it appears** | Every screen - every text element uses one of these levels. |
| **Where it must NEVER appear** | A fourth level - forbidden by the three-level discipline (Bible §5.1). |
| **Required variants** | **Display:** Large, tight tracking, for headlines/event names/tagline. **Heading:** Medium, for section titles. **Body:** Standard, for reading. **Special:** Tabular numerals (time, dates, counts - Bible §5.1). |
| **Replaceable?** | No - typography is the brand's second voice (Bible §5.1). |
| **Composition** | Three typefaces (display family, body family) + tabular variant. |
| **Accessibility** | Minimum font sizes for readability at small screen sizes (Phase 0 §12.7). Contrast AA on both Ink and Paper surfaces. |
| **Placeholder awareness** | Specific font families to be selected in Phase 2 (Bible 15.1). Placeholder type acceptable. |

---

#### I-02: Surface (Background Token)

| Field | Specification |
|---|---|
| **Name** | Surface |
| **Purpose** | Two surfaces, no random backgrounds (Bible §4.4: every surface is one of the two). Ink = stage, dark; Paper = workshop, warm. The surface change is a chapter signal (Phase 1.5 §4.7). |
| **Where it appears** | Every zone background. Headers, footers, cards, forms - all sit on Ink or Paper. |
| **Where it must NEVER appear** | A third surface color - forbidden. Random gradients, photos (blacklist #1, #2 - gradient heroes, glass overlays). |
| **Required variants** | **Ink:** Deep warm near-black (charcoal with amber undertone). **Paper:** Warm cream off-white. |
| **Replaceable?** | No - the Ink/Paper duality is foundational (Bible §4.4, §3.4). |
| **Composition** | Solid color fills. |
| **Accessibility** | Both surfaces must support AA contrast with body text. |
| **Placeholder awareness** | Exact colors to be selected in Phase 2. |

---

#### I-03: Cluster Color Accent

| Field | Specification |
|---|---|
| **Name** | Cluster Color Accent |
| **Purpose** | Instant cluster differentiation: Stage = Amber, Mind = Teal, Art = Graphite, Maker = Clay-warm (Bible §4.4 cluster tints). "Color as wayfinding: a distinct treatment per cluster" (Bible §4.4). |
| **Where it appears** | Cluster Tags (B-03), Cluster Headers (B-02), Event Tile accents, Cluster Filters (I-04/E-03). |
| **Where it must NEVER appear** | As a background fill - accents are roles, not surfaces (Bible §4.4). Never more than 2 hues per surface (Phase 1.5 §4.2: two-hue limit). |
| **Required variants** | **Stage:** Amber accent. **Mind:** Teal accent. **Art:** Graphite accent. **Maker:** Clay-warm accent. |
| **Replaceable?** | No - cluster colors are the wayfinding accent system. |
| **Composition** | Small accent elements: dots, outlines, tag backgrounds. |
| **Accessibility** | Never the sole differentiator (blacklist #51): cluster tags always show text. |
| **Placeholder awareness** | Exact hues to be selected in Phase 2. Proportions, not new hues. |

---

#### I-04: Cluster Filter Toggle

| Field | Specification |
|---|---|
| **Name** | Cluster Filter Toggle |
| **Purpose** | Reduces scanning on P-03 Landscape - narrows 16 events to 4 per tap (Phase 0 5.3: filtering and sorting; Phase 0 §2.2: coordinators need scanning). |
| **Where it appears** | P-03 Landscape (top or sticky filter bar). P-14 Schedule (as E-03 - different component, same interaction). |
| **Where it must NEVER appear** | On P-04 Event Detail (one event only). On P-01 (Landscape owns filtering). |
| **Required variants** | **States:** default (All) / active per cluster / focus. **Values:** All / Stage / Mind / Art / Maker. **Layout:** Horizontal chips (desktop) / Tap-to-collapse toggle (mobile, compact). |
| **Replaceable?** | Search bar for large rosters (Phase 2.5 §12: scalability), but cluster filtering is the primary navigation for 16 events. |
| **Composition** | 5 toggle chips (All + 4 clusters). |
| **Accessibility** | `role="group"`, `aria-pressed` on each chip. Keyboard: Tab through, Enter/Space activates. |
| **Placeholder awareness** | No TBD - structural. |

---

#### I-05: Scroll Progress Bar (Identity Pages Only)

| Field | Specification |
|---|---|
| **Name** | Scroll Progress Bar |
| **Purpose** | Progress feedback during long pages (P-04 Event Detail is the highest density - Bible §11: "scroll progress may be shown as a subtle applause bar on identity pages"). On logistics pages, scroll is plain (Phase 1 §11). |
| **Where it appears** | P-04 Event Detail (long scroll), P-05 Rules & Eligibility (if dense). |
| **Where it must NEVER appear** | On P-01 (short), P-03 (scroll is navigation, not reading), P-06 through P-09 (step indicator handles progress). On logistics pages per Phase 1 §11: "on logistics pages, scroll is plain." |
| **Required variants** | **States:** hidden (at top) / visible (on scroll). |
| **Replaceable?** | No - subtle progress bar is the only acceptable scroll indicator on long pages. |
| **Composition** | Thin horizontal bar at top of viewport. Cluster-colored or neutral. |
| **Accessibility** | Decorative - no screen reader announcement needed. Does not convey essential info. |
| **Placeholder awareness** | No TBD. |

---

#### I-06: Sticky Decision Bar

| Field | Specification |
|---|---|
| **Name** | Sticky Decision Bar |
| **Purpose** | Keeps the Register CTA visible while scrolling through long event detail (P-04). The decision is never lost in content density (Phase 2 Part 10.1: "can I?" must always lead to "yes"). |
| **Where it appears** | P-04 Event Detail, Zone G (bottom of viewport during scroll). Mobile only - on desktop, the button is at natural document flow or accessible via scroll-back. |
| **Where it must NEVER appear** | On screens shorter than one viewport (overhead). On P-06 through P-09 (button is already at the bottom of each step). On logistics pages. |
| **Required variants** | **States:** hidden (above content) / visible (during scroll, below fold) / disabled (registration closed - with explanation). **Content:** Event name (truncated) / "Register" CTA (C-10) / Status badge (B-04). |
| **Replaceable?** | Pull-to-refresh pattern, but sticky bar is more purposeful: the Register action is the screen's climax and must be always-reachable. |
| **Composition** | Event name / Status badge / Register button (C-10). Compact bar. |
| **Accessibility** | `role="complementary"`. Button is keyboard-focusable. `aria-label="Register for [Event]"`. |
| **Placeholder awareness** | Status depends on B11 (P-gated during Announcement). |

---

#### I-07: Skip Link

| Field | Specification |
|---|---|
| **Name** | Skip Link |
| **Purpose** | Accessibility: allows keyboard users to bypass navigation and jump to main content (Phase 0 §12.7 WCAG AA; Bible §13.10: accessibility is invisible design). |
| **Where it appears** | First focusable element on every page. Hidden until focused. |
| **Where it must NEVER appear** | Nowhere - it must be on every page (accessibility requirement). |
| **Required variants** | **States:** hidden (default, visually) / visible (on focus). |
| **Replaceable?** | No - skip links are WCAG AA baseline. |
| **Composition** | Link text: "Skip to main content". |
| **Accessibility** | Position: first in tab order. Visually hidden (clip) until focused. Destination: `#main-content`. |
| **Placeholder awareness** | No TBD. |

---

#### I-08: Focus Ring

| Field | Specification |
|---|---|
| **Name** | Focus Ring |
| **Purpose** | Single warm amber visible focus indicator everywhere (Bible §11: "the focus ring is part of the brand, not an apology"). WCAG AA keyboard navigation requirement (Phase 0 §12.7). |
| **Where it appears** | On every focusable element: links, buttons, form fields, nav items, accordion triggers. |
| **Where it must NEVER appear** | Nowhere - it must be everywhere. Never removed for aesthetic reasons. |
| **Required variants** | **Single style:** Warm amber outline, fixed offset. |
| **Replaceable?** | No - keyboard navigation requires visible focus. |
| **Composition** | CSS outline or box-shadow token. |
| **Accessibility** | High contrast against both Ink and Paper surfaces. Minimum 2px visible width. |
| **Placeholder awareness** | No TBD - structural requirement. |

---

## COMPONENT INVENTORY SUMMARY

| Category | Components | Count |
|---|---|---|
| **A: Navigation & Wayfinding** | A-01 through A-07 | 7 |
| **B: Event Display & Discovery** | B-01 through B-06 | 6 |
| **C: Forms & Input** | C-01 through C-12 | 12 |
| **D: Dashboard (Your Space)** | D-01 through D-05 | 5 |
| **E: Schedule** | E-01 through E-03 | 3 |
| **F: Feedback & System** | F-01 through F-05 | 5 |
| **G: Quiet Corners** | G-01 through G-03 | 3 |
| **H: Admin** | H-01 through H-05 | 5 |
| **I: System & Support** | I-01 through I-08 | 8 |
| **TOTAL** | **A-01 through I-08** | **54** |

**Verification:**
- Every component names a user problem it solves.
- Every component traces to at least one constitution (Phase 0 through Phase 2.5).
- No component exists only because "websites usually have it" - all are justified.
- TBD-aware components are flagged (C-01, B-04, C-03, D-01, D-05, E-02, G-02, G-03, I-01).
- EVOKE Test applied: every component uses the Slip language (B-01, D-04, F-04, F-05), gestures (F-01, F-05), or supports the unveiling (B-04, F-02).
- One Last Rule check: no component exists solely for visual appeal.

---

## PART 5 - COMPONENT RELATIONSHIPS

How every component connects, composes, shares state, and maps to platform responsibilities.

---

### 5.1 PARENT-CHILD MAP

Compound components with their children:

| Parent | Children | Composition Rule |
|---|---|---|
| **A-01 Site Header** | A-02 (Logo Link) + A-03 (Nav Items) + A-04 (Mobile Nav Trigger*) | Desktop: Logo + Nav Items. Mobile: Logo + Mobile Trigger. |
| **A-05 Mobile Nav Drawer** | A-03 (Nav Items, expanded) | Overlays content via Curtain gesture. |
| **B-01 Event Tile** | B-05 (Event Mark) + B-03 (Cluster Tag) + B-04 (Status Badge) + Event Name (Type-D) | Always together: event = identity + context + status. |
| **B-02 Cluster Group Header** | Heading + B-05 (cluster icon) + count | Header + icon + event count. |
| **C-01 Text Input** | Label + Field + Error message* | Error message visible only in error state. |
| **C-03 Team Member Block** | Member label + C-01 (name) + C-01 (class) + Remove button* | Repeatable N times. Remove button hidden for last member. |
| **C-05 Step Progress Indicator** | Step dots/labels × N + Connecting line | 4 or 5 steps (payment conditional). |
| **C-09 Review Summary** | Label-value pairs + Edit links | Data pulled from registration steps. |
| **C-12 FAQ Accordion Item** | Question + Answer* + Chevron | Answer hidden until expanded. |
| **D-01 Dashboard Greeting Card** | Name greeting + D-03 (Delta Indicator) + Season text | Delta inline with greeting. |
| **D-02 Registration Record Card** | Event name + B-03 (Cluster Tag) + Status + Link | Compact record for dashboard list. |
| **D-04 Announcement Card** | Title + Timestamp + Body + "Read more"* | Truncated read-more conditional on mobile. |
| **E-02 Schedule Time Slot Card** | Time + Event name + Venue* + Link | Venue only when resolved. |
| **F-02 Error Banner** | Error text + Retry button + Finish later link | Overlay, not page. |
| **G-01 Hub Grid** | 4 link cards (About/FAQ/Contact/Privacy) | 2×2 grid desktop, stack mobile. |
| **I-06 Sticky Decision Bar** | Event name + B-04 (Status) + C-10 (Register) | Compact bottom bar, mobile only. |

---

### 5.2 COMPOSITION GROUPS

Components that always travel together - they are functionally inseparable:

| Group Name | Components | Context |
|---|---|---|
| **Event Tile Unit** | B-01 (Tile) including B-05 + B-03 + B-04 | P-03 Landscape - the primary scanning unit |
| **Quick Facts Panel** | C-07 × 3-5 cards + B-02 (cluster context) | P-04 Zone C - decision support |
| **Registration Step Shell** | C-05 (Progress) + Zone B (content) + C-10 (CTA) + C-11 (Back) | P-06 through P-09 - every step |
| **Decision Zone** | B-04 (Status) + C-10 (Primary CTA) + C-11 (Secondary) | P-04 Zone G - the climax of every event page |
| **Confirmation Stamp** | C-09 (Summary) + Stamp gesture + C-10 (Your Space CTA) | P-11 - the receipt |
| **Return Engine** | D-01 (Greeting) + D-03 (Delta) + D-02 (Records) + D-04 (Announcements) + D-05 (Actions) | P-12 - full dashboard |
| **Footer Unit** | A-07 (Footer: identity line + Info link + Privacy link) | Every public page bottom |
| **Error Recovery** | F-02 (Error Banner) + C-10 (Retry) + C-11 (Exit) | Overlays during failures |
| **Quiet Corner** | G-02 (Contact) or G-03 (Privacy) or FAQ (C-12 × N) | P-15 through P-18 - reference pages |
| **Season State Display** | B-04 (status badges everywhere, derived) | All pages showing registration status |

---

### 5.3 EXCLUSIVE MUTUALS

Components that NEVER appear together - and the constitutional reason:

| Component X | Component Y | Reason They Never Coexist | Constitution |
|---|---|---|---|
| **C-10 Primary CTA** | **C-10 Primary CTA (second one)** | One primary action per screen - two primaries compete for attention | Phase 2 §8.1 (One Primary Message) |
| **A-04 Mobile Nav Trigger** | **A-03 Nav Items (expanded)** | Mobile shows trigger; desktop shows items. Never both | Phase 2.5 breakpoint logic |
| **F-04 Waiting Slip** | **D-02 Registration Record** | You either have registrations or you don't - these are mutually exclusive states | Phase 1.5 §11.1.6 (Waiting Slip) |
| **F-01 Skeleton Loading** | **F-02 Error Banner** | You're either loading or failed. Skeleton resolves to content OR error. Never both simultaneously (though skeleton → error is valid transition). | Phase 1 §11 |
| **I-06 Sticky Decision Bar** | **C-05 Step Progress Indicator** | Sticky bar is for event detail exploration; progress is for active registration. Registration always starts from event detail, but once you enter, the sticky bar yields to step context. | Phase 2.5 §3.5 (Registration contract) |
| **G-02 Contact Block** | **G-03 Privacy Text** | They are separate pages - P-17 vs P-18. Contact page shows G-02. Privacy page shows G-03. Never both on one page (avoid page bloat; one doubt per page). | Phase 2.5 §3.9 |
| **F-05 Lost Slip** | **A-01 Site Header** | 404 owns its space - the Lost Slip is the only page allowed to be offstage (Phase 1.5 §11.1.5). Header chrome is suppressed. | Phase 1.5 §11.1 (Named Exceptions) |

---

### 5.4 OPTIONAL DEPENDENCIES

Components that only exist when triggered by another component or condition:

| Dependent | Triggered By | Condition | Where |
|---|---|---|---|
| **P-10 Payment Screen (all components within)** | C-3 Payment facts resolved | TBD → RESOLVED (organizer provides fees/gateway) | Between P-09 and P-11 |
| **D-05 "View Schedule" action** | D-2 Schedule content published | Season = Approach or Live (G1) | P-12 Zone D |
| **D-05 "View Winners/Gallery" action** | D-3/D-4 Post-event content exists | Season = Post-Event + content (F-gate) | P-12 Zone D |
| **B-04 "Full" status badge** | Registration capacity reached | Admin sets status or auto-computed | P-03 Landscape, P-04 |
| **B-04 "Closed" status badge** | Season ≠ Registration Open | G1 changes (Approach/Live/Post) | P-03 Landscape, P-04 |
| **C-03 Team Member Block** | Event format = team (not solo) | B4 team size > 1 | P-07 only for team events |
| **C-07 Theme card** | Event has a defined theme | B5 exists (Fashion, Veg Carving, Pot, Collage, Sketch) | P-04 Zone C |
| **Zone E judging block** | Event has stated judging criteria | B8 exists (Group Song, Group Dance, Face Painting, Cooking Without Fire, Art and Craft, Best Out of Waste) | P-04 Zone E |
| **E-02 Venue field** | Venue resolved | Q2 TBD → RESOLVED | P-14 Schedule |
| **G-02 Contact detail values** | Contact resolved | Q12 TBD → RESOLVED | P-17 |
| **A-03 "Schedule" nav link** | Season = Approach/Live/Post (or Schedule published) | G1 ≥ Approach | Site Header A-01 |

---

### 5.5 STATE SHARING

Components that must share state - changes to one must reflect in the other:

| Component A | Component B | Shared State | Direction |
|---|---|---|---|
| **I-04 Cluster Filter Toggle** | **B-01 Event Tiles** | Active cluster filter | Toggle → Tiles (shows only matching) |
| **B-04 Status Badge** | **C-10 Register Button** | Registration status (open/closed/full) | Badge state → Button state (enabled/disabled/label) |
| **G1 Season State** (admin) | **All status badges (B-04)** | Season → derived status | Admin → All (one source, computed everywhere) |
| **C-05 Progress Indicator** | **C-01/C-04 Form Fields** | Current step number + validity | Fields valid → Step advances on C-10 click |
| **E-03 Schedule Cluster Filter** | **E-02 Time Slot Cards** | Active cluster filter | Filter → Cards |
| **D-03 Delta Indicator** | **D-04 Announcement Cards** | "New" vs "Read" status | Read announcement → Delta count decrements |
| **C-03 Team Member Count** | **B-04 "Full" check** | Registration capacity | Count approach → Admin can set Full |
| **C-09 Review Summary** | **C-01/C-04 Data Fields** | Entered data values | Fields → Summary (read-only mirror) |

---

### 5.6 OWNERSHIP MAP

Which component owns which Phase 2.5 content object (A1-G3):

| Content Object | Owner Component | Display Components (derived, not owners) |
|---|---|---|
| **A1** Festival description | P-01 Zone A (Identity Statement, uses Type-D) | N/A (Welcome only, single source) |
| **A2** Tagline | P-01 Zone A (uses Type-D, signature setting) | N/A |
| **A3** Edition identity | A-02 Logo Link (every page) | A-07 Footer (reference, not duplication) |
| **A4** Host school | G-02 Contact Detail Block (P-17) | A-07 Footer (short reference), P-15 About |
| **A5** Festival dates | P-19 Zone B → P-15 About | A-07 Footer reference |
| **A6** Venue | E-02 Schedule Time Slot Card (P-14) | P-17 Contact (directions context) |
| **A7** Organizer contact | G-02 Contact Detail Block (P-17) | N/A (all other contacts link to P-17) |
| **A8** History | P-15 About Zone B | N/A (F object) |
| **B1** Event list | B-01 Event Tiles × 16 (P-03) | N/A (Landscape owns B1) |
| **B2** Cluster tags | B-02 Cluster Group Header + B-03 Cluster Tag | B-01 Event Tile (displays within tile) |
| **B3** Event personality | P-04 Zone B (uses Type-D/Type-H) | N/A |
| **B4** Quick facts | C-07 Quick Fact Card × N (P-04) | N/A |
| **B5** Theme | C-07 Quick Fact Card (conditional) | N/A |
| **B6** Eligibility | C-07 Quick Fact Card (P-04); P-05 Zone C | N/A |
| **B7** Rules | C-08 Rules List Item × N (P-04 Zone D) | P-05 Zone B (general rules only, C1) |
| **B8** Judging criteria | P-04 Zone E (structured text block) — **conditional: present for 6 of 16 events** | N/A |
| **B9** Things to bring | P-04 Zone E (structured list) | N/A |
| **B10** Per-event FAQ | C-12 FAQ Accordion Item × N (P-04 Zone F) | P-16 Global FAQ (links, never duplicates) |
| **B11** Registration status | B-04 Status Badge (computed) | C-10 Register Button (state derived) |
| **B12** Registration requirements | P-04 Zone G (summary text) / P-06 Zone B (restated) | N/A |
| **C1** General rules | P-05 Zone B (C-08 Rules List Items) | P-04 Zone D (links to P-05 for general) |
| **C2** Flow steps | C-05 Step Progress Indicator | N/A |
| **C3** Payment facts | P-10 Zone B (TBD) | N/A |
| **C4** Data fields | C-01 Text Input, C-02 Select, C-03 Team Members | C-09 Review Summary (read-only display) |
| **C5** Confirmation | C-09 Review Summary (P-11) | D-02 Registration Record Card (P-12, reference) |
| **C6** Participant identity | D-01 Dashboard Greeting Card | P-22 Login form (input) |
| **C7** Dashboard status | D-03 Delta Indicator | D-01 Dashboard Greeting Card (context) |
| **D1** Announcements | D-04 Announcement Card (P-12) | P-01 (latest only, derived display) |
| **D2** Schedule | E-02 Schedule Time Slot Cards (P-14) | P-04 Event Detail (links during Approach) |
| **D3** Gallery | P-20 Zone B (F) | N/A |
| **D4** Winners | P-21 Zone B (F, Stamp gesture) | N/A |
| **D5** Social channels | P-19 Zone B → quiet corners (F) | N/A |
| **D6** Sponsors | P-19 Zone B → quiet corners (F) | N/A |
| **E1** Global FAQ | C-12 FAQ Accordion Item × N (P-16) | N/A |
| **E2** Contact route | G-02 Contact Detail Block (P-17) | N/A (doubled as A7, single source) |
| **E3** Privacy note | G-03 Privacy Text Block (P-18) | N/A |
| **F1** Content management | H-03 Admin Content Editor (A-03) | N/A |
| **F2** Registration management | H-01 Admin Table (A-04) | N/A |
| **F3** Announcement publishing | D-04 Announcement Card (admin variant, A-05) | N/A |
| **F4** Analytics | A-02 status cards (F) | N/A |
| **G1** Season state | H-02 Admin Toggle (A-06) | B-04 Status Badge (derived, everywhere) |
| **G2** Edition key | A-02 Logo Link (2K26) | P-21 Winners (edition context, F) |
| **G3** Entry state | System - not rendered as component | Affects content display, not a visual component |

---

### 5.7 REUSE SCOPE

| Scope Level | Components | Where Used |
|---|---|---|
| **GLOBAL** (every screen) | A-01 Site Header, A-02 Logo Link, A-07 Footer, I-02 Surface, I-01 Typography Scale, I-08 Focus Ring, I-07 Skip Link | Every page (public) |
| **GLOBAL** (public pages) | A-03 Nav Items, A-06 Back Affordance* | Every screen except P-01 (no back) and overlays |
| **AREA** (event discovery) | B-01 Event Tile, B-03 Cluster Tag, B-04 Status Badge, B-05 Event Mark, B-06 Section Divider | P-03, P-04, P-12, A-07 |
| **AREA** (registration flow) | C-05 Progress Indicator, C-09 Review Summary, C-10 Primary CTA, C-11 Secondary Button | P-06 through P-11 |
| **AREA** (forms) | C-01 Text Input, C-02 Select, C-03 Team Member Block, C-04 Agreement Checkbox, C-06 Validation Message | P-07, P-08, P-22, A-03 |
| **AREA** (dashboard) | D-01 Greeting Card, D-02 Record Card, D-03 Delta, D-04 Announcement, D-05 Actions | P-12, P-13 |
| **AREA** (schedule) | E-01 Day Header, E-02 Time Slot Card, E-03 Cluster Filter | P-14 |
| **AREA** (feedback) | F-01 Skeleton, F-02 Error Banner, F-03 Success Toast, F-04 Waiting Slip, F-05 Lost Slip | P-13, P-23, P-25, + overlays |
| **AREA** (quiet corners) | G-01 Hub Grid, G-02 Contact Block, G-03 Privacy Block, C-12 FAQ Accordion | P-15 through P-19 |
| **AREA** (admin) | H-01 Table, H-02 Toggle, H-03 Editor, H-04 Status Card, H-05 Export | A-01 through A-07 only |
| **AREA** (system utilities) | C-07 Quick Fact Card, C-08 Rules List Item, C-12 FAQ Accordion, I-03 Cluster Color, I-04 Filter Toggle, I-05 Scroll Progress, I-06 Sticky Bar | P-04 through P-18 (various) |
| **SCREEN** (single screen only) | C-09 Review Summary (P-09 specifically), P-11 Confirmation Stamp block, P-22 Login form composition | Single use, specific screen |

*Back Affordance absent only on P-01 (home), P-23 overlay (network), P-26 overlay (loading).*

---

### 5.8 VARIANT SYSTEM

How components vary across dimensions:

#### 5.8.1 By Surface (Ink Background vs Paper Background)

| Surface | Components affected | Variation |
|---|---|---|
| **Ink background** | A-02 Logo Link, C-10 Primary CTA, C-01 Text Input, C-12 FAQ Accordion, F-01 Skeleton | All adapt: light-on-dark text for readability. CTA = Amber-on-Ink. Input = light field on dark surface. Skeleton shows light wireframe on dark. |
| **Paper background** | All same components above | Ink-on-Paper text. CTA = Ink-on-Paper. Input = dark field on light surface. Skeleton shows dark wireframe on light. |

**Rule:** Every component must function on both surfaces. Surface-specific components do not exist - the duality is foundational (Bible §4.4, §3.4).

#### 5.8.2 By Cluster (Stage/Mind/Art/Maker)

| Cluster | Components affected | Variation |
|---|---|---|
| **Stage** | B-03 Cluster Tag, B-02 Header, B-01 Tile accent, I-03 Accent | Amber accent. Higher energy - identity-tinted. |
| **Mind** | Same | Teal accent. Sharp, intellectual. |
| **Art** | Same | Graphite accent. Quiet, gallery-adjacent. |
| **Maker** | Same | Clay-warm accent. Tactile, craft-adjacent. |

**Rule:** Same palette, different proportions (Bible §4.4). Never new hues. Two-hue limit per surface (Phase 1.5 §4.2).

#### 5.8.3 By Season (Available vs Closed vs Future)

| Season | Components affected | Variation |
|---|---|---|
| **Announcement** | B-04 Status ("Coming Soon"), C-10 Register (disabled with explanation), A-03 Schedule link (hidden), D-01 greeting (contextual), E-02 Schedule (honest placeholder), I-06 Sticky Bar (hidden) | Honest wait postures. No registration CTAs. |
| **Registration Open** | B-04 Status ("Open"), C-10 Register (enabled, primary), A-03 Schedule link (hidden unless published), C-05 Progress (active), I-06 Sticky Bar (visible) | Full registration flow. CTAs active. |
| **Approach** | B-04 Status (may still be open or closing), D-05 Schedule action (visible), E-02 Schedule (populated), A-03 Schedule link (visible) | Registration may be open or closing. Schedule visible. |
| **Live** | B-04 Status ("Closed"), C-10 Register (hidden/replaced), D-05 Live actions, E-02 live updates | Registration closed. Schedule is active content. |
| **Post-Event** | B-04 Status ("Finished"), D-05 Winners/Gallery (if F-content exists), P-20/P-21 active | Archive state. No registration. |

#### 5.8.4 By Context (Identity Moment vs Logistics Moment)

| Context | Components affected | Variation |
|---|---|---|
| **Identity moment** (P-01, P-11, P-20, P-21) | C-10 CTA (uppercase label, Display type), A-02 Logo (Display), A-01 Header (Ink surface), C-09 Review Summary (stamped treatment) | Display type for headlines. Amber-on-Ink CTAs. Sweep/Lift/Stamp gestures active (Phase 1.5 §3.4). |
| **Logistics moment** (P-04 through P-09, P-12, P-14, P-15 through P-18) | C-10 CTA (normal label, Body type), A-01 Header (Paper surface), C-07 Facts (compact), C-08 Rules (scannable), E-02 Schedule (data-first), I-05 Scroll Progress (plain or hidden) | Body type dominates. Calm compositions. No signature gestures (rationed loud - Bible 13.5). |

**Rule:** The context boundary is sharp - a visitor knows they've moved from identity to logistics because the surface changes, the type changes, and the energy settles (Phase 1 §2.3, Phase 1.5 §4.1).

---

## PARTS 4-5 AUDIT

### Component coverage verified:
- **54 components** inventoried, every one traced to a constitution
- **0 components** without a user-problem justification
- **0 components** that exist only because "websites usually have it"
- All TBD-aware components flagged with placeholder awareness
- EVOKE Test satisfied: Slip language used (B-01, D-04, F-04, F-05), gestures supported (F-01, F-05), one-hue-per-surface rule enforced (I-03)
- One Last Rule satisfied: no gratuitous components

### Relationship coverage verified:
- **Parent-child map:** 15 compound components with children defined
- **Composition groups:** 10 inseparable groups
- **Exclusive mutuals:** 7 pairs that never coexist, with constitutional justification
- **Optional dependencies:** 10 components that exist only when triggered
- **State sharing:** 8 pairs with shared state and direction
- **Ownership map:** All 43 content objects (A1-A8, B1-B12, C1-C7, D1-D6, E1-E3, F1-F4, G1-G3) mapped to their component owner
- **Reuse scope:** Every component classified as GLOBAL / AREA / SCREEN
- **Variant system:** 4 dimensions (surface, cluster, season, context) mapped

*End of Phase 3 Interface Architecture Specification - Parts 4 and 5.*

---

## PART 6 - RESPONSIVE BEHAVIOUR

How **interface BEHAVIOUR** changes across surfaces - interaction patterns, not visual sizing. This section does not specify pixel dimensions, font sizes, or colour values. It specifies which interaction model applies at each surface class and why that model serves the audience.

**Surface classes:**

| Class | Width range | Primary audience | Interaction model |
|---|---|---|---|
| **MOBILE** | ~375-428px | Students (65%+ traffic) | Thumb-first, single-column, one action per viewport, scroll-native |
| **TABLET** | 768-1024px | Mixed (students browsing, coordinators scanning) | Adaptive - single or dual column, gesture + tap |
| **DESKTOP** | 1024-1440px | Coordinators primarily; parents; returning students | Keyboard-first, scan patterns, multi-zone views |
| **LARGE DESKTOP** | >1440px | Coordinators at workstations; admin | Content-centred; no full-width sprawl |

**Governing rules:**
- Mobile is NOT a smaller desktop (Phase 0 §12.9; Bible Constitution 20)
- Desktop is NOT an afterthought (Phase 0 §12.9)
- Each surface is designed deliberately for its audience's interaction model
- No pinch-zoom required on mobile (Phase 0 §12.8)
- One gesture per viewport max (Phase 1.5 §11.3 - carried into responsive)

---

### 6.A NAVIGATION BEHAVIOUR BY SURFACE

#### Mobile (~375-428px)

**Access pattern:** Compressed - tap-to-reveal drawer (A-05).

- **Hamburger trigger (A-04)** visible in Site Header. Tapping opens full-screen drawer overlay (Curtain gesture).
- **Always-visible nav items:** Logo Link (A-02, home link) only. Nothing else competes for the top zone.
- **Hidden nav items:** Events, Your Space/Login, Schedule, Info - all inside drawer. Drawer lists as large touch targets (≥48px each, Phase 1.5 §11.3; Bible blacklist #43).
- **Bottom-120px zone (thumb-reach critical area):** On P-04 Event Detail, the Sticky Decision Bar (I-06) occupies the bottom zone during scroll: event name + "Register" CTA. On P-06-P-09 (Registration), the Continue/Back buttons sit at natural bottom of step - always in thumb reach without two-thumb stretch.
- **Deep entry handling:** When arriving via QR/WhatsApp link at a specific event, the header compresses further - logo + back affordance only. Navigation drawer still available, but the retreat path (← Landscape) takes priority.
- **Why:** Students browse on phones during recess; navigation is a quiet escape hatch, never competing (Phase 2 Part 8.2; thumb is lazy and honest, Phase 2 §13.1). The primary action must be in the thumb zone without conscious reach.

#### Tablet (768-1024px)

**Access pattern:** Transitional - compressed or partial visibility.

- **Hamburger trigger** present for primary nav, but nav drawer is not full-screen - it slides as a side panel (60% width max), leaving partial page context visible behind. Content not dimmed.
- **Always-visible nav items:** Logo Link (A-02) + 1 nav item ("Events") - the single most-used navigation target.
- **Hidden nav items:** Your Space/Login, Schedule, Info - in compressed nav.
- **Filter bar on Landscape:** Inline horizontal bar (compact toggle chips). Not collapsible - tablet width supports inline.
- **Why:** Tablets serve mixed audiences. Students still tap-first; coordinators may use keyboard. The side panel preserves context awareness while reducing chrome overhead.

#### Desktop (1024-1440px)

**Access pattern:** Persistent - nav items always visible horizontally.

- **No hamburger.** Nav Items (A-03) displayed inline in Site Header: [Events] [Your Space / Login] [Schedule*] [Info].
- **Always-visible nav items:** All 3-4 items. Schedule link appears only in Approach/Live/Post seasons (G1-gated).
- **Deep entry handling:** Breadcrumb visible at top of every screen beyond P-01. QR/deep link entries show re-anchoring context in Zone A header.
- **Why:** Coordinators scan multiple events, check rules, register teams - keyboard-driven, multi-reference workflows (Phase 0 §2.2: coordinator behaviour). Persistent nav supports tabbing and reference jumping without drawer overhead.

#### Large Desktop (>1440px)

**Access pattern:** Same as Desktop - nav items inline.

- No behavioural change from Desktop. Navigation pattern is identical.

**Trace:** Phase 0 §2.1 (students mobile-first), §2.2 (coordinators desktop-first), §5.3 (progressive disclosure); Phase 2 Part 8.2 (navigation as escape hatch, never competing); Bible Constitution 20 (mobile not smaller desktop).

---

### 6.B EVENT BROWSING BEHAVIOUR BY SURFACE

#### Mobile

**Scrolling & scanning model:** Single-column, sequential cluster sections.

- **Clusters:** Displayed sequentially - Stage cards scroll into view, then Mind, then Art, then Maker. Not side-by-side. Natural scroll creates visual pauses between clusters (each Cluster Group Header acts as a breathing break - Phase 1.5 §4.1).
- **Filtering:** Cluster filter is a tap-to-collapse toggle at the bottom of the header zone. Tapping a cluster scrolls to that cluster's section. "All" filter restores full scroll.
- **Scanning:** 16 events × sequential scroll. Each tile (B-01) is one row: mark + name + cluster tag + status badge - scannable in 2 seconds (Phase 0 §2.1: quick scanning). Eye moves down 2-3 tiles per scroll gesture.
- **16 on one phone is not overwhelming** because (a) clusters divide the set into four named groups of uneven size (6 / 2 / 5 / 3), each small enough to hold in mind; (b) each tile carries only scanning density, not decision density; (c) the finger naturally groups tiles into chunks of 3-4 per palm-width. The reduction comes from *naming the groups*, not from their being equal. See Amendment AM-02.

#### Tablet

**Cluster display:** Clusters may be 2×2 grid on wider tablets or sequential on narrower tablets.

- **Filtering:** Inline compact filter bar at top. Tapping a filter immediately narrows - no loading state.
- **Tiles within clusters:** 2-column grid allows 8 tiles in view per screen (vs 4 on mobile). Coordinator scanning speed improves.

#### Desktop

**Coordinator scanning optimisation:**

- **Layout:** Cluster sections stack in the fixed order Stage → Mind → Art → Maker. Tiles inside a section flow into as many columns as the width allows, so a 6-event cluster and a 2-event cluster both look deliberate rather than broken. Total: all 16 events visible in roughly 2 viewports of scanning. A fixed 2×2 cluster grid is **not** used — it assumed equal cluster sizes. See Amendment AM-02.
- **Filtering:** Sticky filter bar at top - remains visible during scroll. Tapping a cluster chip narrows tiles and announces results count.
- **Hover context exists:** Event tiles show slight lift + outline on hover (Bible §11: acknowledgement only, never layout change). This gives coordinators an extra scan cue (is this tile interactive? what cluster?). Hover states double as focus states for keyboard users.
- **Why:** Coordinators need to scan multiple events quickly (Phase 0 §2.2: "checklist-driven"). Desktop gives them parallel scanning; mobile gives them focused scanning. Neither is wrong - they serve different tasks.

#### Filter bar behaviour summary

| Surface | Filter bar | When inline | When hidden |
|---|---|---|---|
| Mobile | Tap-to-collapse toggle | Collapsed behind "Filter" trigger | When scroll pushes past header - reappears as sticky |
| Tablet | Inline compact chips | Always inline | Never hidden |
| Desktop | Sticky horizontal bar | Always inline | Never hidden |

**Trace:** Phase 0 §2.1 (student scanning), §2.2 (coordinator scanning), §5.3 (progressive disclosure); Phase 2 Part 3.3 (guiding choice, not catalogue); Bible §11 (hover as acknowledgement); Phase 1.5 Part 11.3 (beat alternation).

---

### 6.C FORM BEHAVIOUR BY SURFACE

#### Mobile Registration

**Space-constrained flow:**

- **Virtual keyboard:** When a text input receives focus, the on-screen keyboard covers ~40% of viewport. Form fields are full-width, labels sit above inputs (never inline/placeholders only - Phase 0 §12.7; Bible §11).
- **Column layout:** Single-column. Fields stack vertically. Each field is immediately followable by the next via Tab or Enter - no lateral focus movement required.
- **Touch targets:** All inputs ≥48px height (above 44px minimum - Bible blacklist #43). Spacing between fields: generous enough that adjacent fields are not accidentally tapped.
- **Team member fields:** For team events (C-03), each member is a full-width card stack, added one at a time. "Add Member" button at bottom of current member block.
- **Step Progress Indicator:** Compact horizontal dots at top. Numbers omitted (space constraint); dots convey position visually. Label ("Step 2 of 4") rendered as small text above dots.

#### Tablet Registration

**Adaptive flow - progressive disclosure or full-form:**

- **Column layout:** Single-column (fields don't yet justify two-column - no paired logical groups). Fields are standard width (not full-screen).
- **Step Progress Indicator:** Horizontal bar with step labels ("Declare → Info → Agree → Review"). Labels fit on one line.
- **Virtual keyboard:** May or may not appear (tablet users may have physical keyboard). Form must work identically with and without keyboard.

#### Desktop Registration

**Coordinator batch registration affordance:**

- **Column layout:** Single-column remains primary. Two-column only if a natural pair exists (e.g., name + school as a logical row). Never forced two-column for arbitrary field grouping.
- **Tab navigation:** Full keyboard support. Tab order follows visual field order strictly. Select fields (schools, classes) use native dropdowns - keyboard-navigable.
- **Step Progress Indicator:** Full horizontal bar with labels and connecting lines. Active step highlighted. Past steps show checkmarks; future steps are dimmed.
- **Batch registration pathway:** For coordinators, P-07's "Participant Information" step supports multiple-entrant flow: after completing one participant, "Add Another Participant" appears (secondary action). This does not affect the single-participant flow - it is an optional repeat. Coordinator workflow benefit: one registration session covers a team.

#### Step Progress Indicator surface comparison

| Surface | Format | Labels | Visual treatment |
|---|---|---|---|
| Mobile | Dot indicators (compact) | Small text above ("Step 2 of 4") | Minimal chrome |
| Tablet | Horizontal bar | Inline labels | Standard |
| Desktop | Horizontal bar | Inline labels + checkmarks | Full detail |

**Trace:** Phase 0 §12.7 (WCAG AA); Phase 2 Part 10 (registration psychology); Charter §5 (progressive confidence - visibility of progress); Bible blacklist #43 (touch targets), #51 (no colour-only status); Bible §11 (input personality, focus visible).

---

### 6.D EVENT DETAIL BEHAVIOUR BY SURFACE

#### Mobile

**10 sections on one phone - sequential, progressive:**

- **All zones stacked single-column.** A (Orientation) → B (Personality) → C (Quick Facts) → D (Rules) → E (Judging & Materials) → F (FAQ) → G (Decision).
- **Quick Facts (Zone C):** Compact cards, stacked, not grid. Facts readable without zooming.
- **Judging & Materials (Zone E):** Stacked, not side-by-side. Each section (judging, materials) gets its own subheading.
- **FAQ (Zone F):** Accordion (C-12). Questions always visible; answers expand on tap. Accordion on mobile is essential - long FAQ answers would push the Register CTA beyond practical thumb reach.
- **Sticky CTA (Zone G / I-06):** Once the user scrolls past Zone B (Personality), the Sticky Decision Bar appears at bottom of viewport: truncated event name + status badge + "Register" button. Always thumb-reachable.
- **Sticky bar appear/disappear logic:** 
  - Hidden at page top (above fold, CTA in natural position)
  - Appears when user scrolls past first viewport (content density hides CTA)
  - Disappears when user scrolls back to top
  - Disappears when registration is closed (replaced by status message)
- **Rules reading (Zone D):** Scrollable, one rule per visual unit. No two-hands required. Reading width comfortable at small sizes (rules body text never below AA minimum - Phase 0 §12.7).

#### Desktop

**Multi-column where justified by constitution:**

- **Quick Facts (Zone C):** Three-column grid for 3+ facts. Scannable in parallel - coordinator reads team size, time limit, and eligibility simultaneously.
- **Judging & Materials (Zone E):** Two-column **only when both blocks have content** — judging left, materials right. For the 10 of 16 events with no stated judging criteria, Zone E is a single column carrying materials plus one honest line about criteria. An empty second column is forbidden: a hollow box implies information exists and is being withheld. See Amendment AM-03.
- **FAQ (Zone F):** Accordion remains - but items may be taller (more horizontal space for answers). FAQ is not side-by-side with Rules (Zone D) - the reading density of rules absorbs that attention.
- **No side-by-side Rules + FAQ** - justified rejection: Rules are HIGH cognitive load (Phase 2 Part 7.1); splitting attention between Rules and FAQ parallel content would increase, not decrease, cognitive effort.
- **Sticky CTA:** Not used on desktop. The Register button sits at natural document flow bottom of Zone G. Users can scroll back to top to reach it. Desktop users prefer deliberate over persistent chrome.
- **Reading width:** Rules and all body text constrained to maximum comfortable reading width (~65ch characters per line). Wider screens add white space, not wider text.

**Trace:** Phase 0 §5.3 (progressive disclosure); Phase 2 Part 7.1 (cognitive load HIGH at rules); Phase 2 Part 10.1 (can-I gate); Bible Section 7 (one grammar, not generic); Phase 1.5 Part 11.3 (beat alternation - rules are a thinking beat).

---

### 6.E DASHBOARD BEHAVIOUR BY SURFACE

#### Mobile

**Return engine, compressed:**

- **Greeting Card (D-01):** Full-width top card. Name + "What changed" delta inline. Prominent - the return engine's first impression.
- **Registrations (D-02):** Scrollable vertical list of Registration Record Cards. Each card compact.
- **Announcements (D-04):** Collapsible list. Newest announcement expanded by default; older ones collapsed (tap to expand). Prevents announcement bloat from pushing registrations off-screen.
- **Actions (D-05):** Compact horizontal row at bottom: 1-2 action buttons, full-width on mobile.

#### Desktop

**Coordinators and power users:**

- **Greeting + Registrations:** May share two-column layout: D-01 greeting card on left (narrower), D-02 registration records on right (wider). Or stacked if registration count is high.
- **Announcements:** Full-width below registrations. No collapse - desktop users expect to read. Announcements retain date ordering.
- **Actions:** Horizontal bar, side-by-side buttons (not stacked).
- **Admin and participant views share patterns:** Admin Dashboard (A-02) uses the same card-grid pattern as participant dashboard (D-02). Both use Registration Record Cards conceptually - admin sees all, participant sees own. Consistency prevents "two UIs" confusion.

**Trace:** Phase 2 Part 12.2 (Your Space as return engine); Phase 2 Part 8.3 (returning attention greeted by change); Phase 0 §2.1 (students), §2.2 (coordinators); Phase 2.5 §3.7 (dashboard page contract).

---

### 6.F SCHEDULE BEHAVIOUR BY SURFACE

#### Mobile

**Timeline, not table:**

- **Vertical timeline:** Events listed chronologically within each day section (E-01). No table. Each time slot card (E-02) is a full-width card: time (bold), event name, venue, "View Details" link.
- **Day grouping:** Day headers (E-01) act as section dividers. Scroll naturally moves through days.
- **Cluster filtering (E-03):** Tap-to-collapse chip row at top. Tapping narrows timeline to one cluster.

#### Desktop

**Multi-event comparison view:**

- **Two-column view:** Time column on left (tabular numerals, aligned); event details on right (event name + venue + link). Rows are clearly paired. This is effectively a table without the table semantics - more readable, same data.
- **Day grouping:** Same as mobile - day headers divide sections.
- **Cluster filtering (E-03):** Inline chip row at top. Tapping a chip filters rows.
- **Cross-event scanning:** Coordinators can scan multiple events' timing simultaneously. Desktop viewport shows ~8-12 time slots without scrolling.

**Trace:** Phase 2.5 §3.8 (Schedule page contract); Phase 0 §2.2 (coordinator scanning); Phase 2 Part 21 (time architecture).

---

### 6.G READING WIDTH & COMFORT

**Rule text (the highest-density content):**

- **Max comfortable reading width: ~65 characters per line.** This is a well-established typography principle; wider lines lose readability. On desktop Event Detail (P-04), Rules (Zone D) are constrained to this width even on wide monitors. Extra white space fills the gap.
- **Breakpoint logic:** Not by device width - by content width. The rules container is ~65ch wide regardless of screen. On mobile, this equals approximately full-width minus padding. On desktop, this equals a centered column.
- **Paragraph reflow:** No manual line-breaks in rule text. Text wraps naturally to container width. Long lines (e.g., specific prohibitions) do not force horizontal scroll.

**Data behaviour at each width:**

| Content type | Mobile | Tablet | Desktop |
|---|---|---|---|
| Rules text | Full-width minus padding (one column) | Constrained column (~65ch) | Constrained column (~65ch), white space around |
| Quick Facts | Stacked cards | Stacked or 2-col | 3-col grid |
| FAQ | Accordion | Accordion | Accordion (taller) |
| Schedule | Timeline (cards) | Timeline | Two-column (time + event) |
| Admin tables | Card list (not table) | Card list | Full table (H-01) |

**Trace:** Phase 0 §12.8 (no pinch-zoom); Phase 2 Part 7 (cognitive load management); Bible §5.1 (body readability at small sizes); Phase 1.5 Part 4 (sections as scenes).

---

### 6.H THUMB REACH MAP (Mobile Specific)

For every primary screen, interaction hot zones and reach analysis:

| Screen | Primary action location | Zone | Two-thumb required? |
|---|---|---|---|
| **P-01 Welcome Beat** | "Explore Events" CTA (C-10) | Bottom of first viewport - naturally in thumb zone | No |
| **P-03 Landscape** | Event tiles (B-01) | Middle scroll zone - thumb swipes naturally through | No |
| **P-04 Event Detail** | Sticky CTA (I-06) | Bottom-120px fixed during scroll | No |
| **P-05 Rules** | Links to events | Bottom action zone | No |
| **P-06-P-09 Registration** | Continue / Back buttons | Bottom of step - always visible at natural scroll bottom | No |
| **P-11 Confirmation** | "Go to Your Space" CTA | Bottom of confirmation | No |
| **P-12 Your Space** | Action buttons (D-05) | Bottom of dashboard | No |
| **P-14 Schedule** | Time slot tap targets | Middle scroll zone | No |
| **Quiet Corners** | Back link + topic links | Bottom action zone | No |

**Rule: Nothing requires two-handed operation on any screen.** The thumb is lazy and honest (Phase 2 §13.1). Every primary action is placeable without stretching.

**Top-zone actions:** Navigation hamburger (A-04), Logo Link (A-02), Back affordance (A-06) - all in top 60px. These are retreat paths, rarely primary actions. The user's attention reaches for them consciously (they are escape hatches, Phase 2 Part 8.2).

**Trace:** Phase 2 §13.1 (thumb is lazy and honest); Phase 2 §13.3 (every moment finishable in one hand); Phase 0 §11.4 (mobile is primary).

---

### 6.I LANDSCAPE ORIENTATION (Mobile Phone Rotated)

**What changes:**

- **Screen width increases:** Phone now behaves closer to narrow tablet (~568-667px width).
- **Navigation:** Hamburger trigger remains (not switched to full nav - landscape mode is not a reliable indicator of desktop-intent; many students rest their phone on a desk in landscape).
- **Content:** Wider tiles possible on Landscape - may show 2 tiles per row instead of 1. Event Detail: Quick Facts may shift to 2-column.
- **Rule: No behavioural change forced by orientation.** The same single-column flow works in landscape - it just has more horizontal space. No orientation-specific overrides are required (unlike some apps that hide features in landscape).

**Trace:** Phase 0 §11.4 (mobile primary - orientation is variable); Phase 1.5 Part 11.3 (density is content-typed, not viewport-typed).

---

### 6.J LARGE DESKTOP BEHAVIOUR

**Content centering, not full-width sprawl:**

- **Grid max-width:** Content is constrained to a max-width container (~1200-1400px) and centred. White space flanks the content. No content stretches to edges of ultrawide monitors.
- **White space behaviour:** Excess width = margin, not wider text. Rules still max ~65ch. Navigation spans full header width but nav items remain at comfortable reading distance from each other.
- **Admin tables:** Admin Registration table (H-01) uses full available width (up to max container). Data tables need horizontal space; this is one of the few places where width is utilised.
- **Why:** Large desktops are coordinator workstations (Phase 0 §2.2). Excess width should show more data, not bigger cards. The grid max-width prevents the identity from looking stretched or thin.

**Trace:** Phase 0 §2.2 (coordinators at workstations); Phase 1.5 Part 4 (sections as scenes - scene boundaries are meaningful); Bible Section 10 (generous spacing = luxury, not accident).

---

### 6.K BREAKPOINTS SUMMARY

Breakpoints are named **functionally**, not by device pixel width. Each breakpoint answers: what behavioural change triggers here?

| Breakpoint name | Trigger condition | Behavioural change |
|---|---|---|
| **Single-column** | Up to ~428px | Everything stacks. Nav = drawer. Filter = toggle. CTA = sticky. |
| **Dual-scroll** | ~429-768px | Some content may show 2 per row (tiles). Nav = compressed. Filter = may go inline. CTA may drop sticky (content fits more). |
| **Dual-column** | ~769-1024px | Quick Facts = 2-col. Nav = partial inline. Filter = inline. Schedule = wider cards. |
| **Multi-zone** | ~1025-1440px | Nav = full inline. Quick Facts = 3-col. Schedule = two-pane. Dashboard = two-col layout. Tables = full width. |
| **Content-bound** | >1440px | Content = centred in max-width container. White space grows. Tables = wider. No wider text. |

**Rule: There is no hard pixel mapping.** These are behavioural descriptions. The implementation maps them to specific pixel ranges, but the specification does not couple to device pixels. A future device with unusual dimensions will find the nearest behavioural class.

**Trace:** Bible Section 14.2 (breakpoints as behavioural surface classes); Phase 0 §12.9 (equal attention to mobile/desktop); Charter §6 (decision filter - does the breakpoint serve the user's task?).

---

*End of Part 6 - Responsive Behaviour.*

---

## PART 7 - STATE ARCHITECTURE

Complete state machines for every screen and component. Each state is fully specified for: trigger, visible behavior, actions available/blocked, recovery path, transience, confidence preservation, and screen reader treatment.

**State notation:** T = Transient (resolved quickly, seconds), P = Persistent (stays until user action), S = Seasonal (persists across session, driven by G1).

---

### 7.A WELCOME (P-01, P-02)

| # | State Name | Trigger | Visible Behavior | Actions Available | Actions Blocked | Recovery Path | Duration | Confidence | Screen Reader |
|---|---|---|---|---|---|---|---|---|---|
| A1 | Normal (Registration Open) | G1 = Registration Open | Full content: identity, "Registration open" status, "Explore Events" CTA active | Explore Events → P-03; About → P-15; Info → P-19 | Register directly from Welcome (no shortcut) | - (no failure) | Persistent | Certainty: "I know where I am and what to do" | H1 announces festival identity; live region announces registration status |
| A2 | Announcement Season | G1 = Announcement | Identity + "Registration opens soon" + "View Events" (read-only preview) | View Events (read-only) → P-03; About → P-15 | Register, Schedule | - (waiting is the state) | Seasonal (S) | "I know when to return" | "Registration opens soon" announced via aria-live="polite" |
| A3 | Registration Closed | G1 = Approach/Live/Post (registration complete) | Identity + "Registration is closed" + redirected CTA | View Events (read-only); Your Space (if registered); Contact | Register | Honest redirect to next season beat | Seasonal (S) | "Registration is done, I'm not rejected" | "Registration is closed for this season" announced |
| A4 | Approach Season | G1 = Approach | Identity + "Approaching the festival" + "View Schedule" prominent | View Schedule → P-14; Events (may still be open) | - | - | Seasonal (S) | "Festival is coming, I can plan" | "Festival approaching" + schedule link announced |
| A5 | Live Season | G1 = Live | Identity + "Festival is live" + Schedule prominent | View Schedule → P-14; Your Space → P-12 | Register (closed) | - | Seasonal (S) | "Festival happening now" | "Festival is live" announced |
| A6 | Post Season | G1 = Post-Event | Identity + "EVOKE 2K26 has ended" + Gallery/Winners (if content) | Gallery → P-20; Winners → P-21; Events (archive) | Register | Next edition handoff (G2 rollover) | Seasonal (S) | "I know what happened; I'll be back" | "Festival has ended" + archive links announced |
| A7 | Service Unavailable | System: server down | Error overlay: "We're having trouble right now" + "Try again"; world behind dims | Try Again; go back to previous | All actions | Retry → resume; persistent failure → "come back later" | Transient (T) | "Unbothered - temporary issue" (Phase 2 Part 14) | role="alert" announces immediately; polite after retry |

---

### 7.B LANDSCAPE (P-03)

| # | State Name | Trigger | Visible Behavior | Actions Available | Actions Blocked | Recovery Path | Duration | Confidence | Screen Reader |
|---|---|---|---|---|---|---|---|---|---|
| B1 | Normal (all events visible) | Default state; G1 = Registration Open | All 16 event tiles grouped by 4 clusters, status badges visible | Tap event → P-04; Filter by cluster; Back → P-01; Rules → P-05 | - | - (no failure) | Persistent | "I see all my options" | Region: "Events" announced; event count announced per cluster |
| B2 | Filtered by cluster | User taps cluster filter | Only matching tiles visible; results count; active chip highlighted | Tap event → P-04; Clear filter → B1; Switch to different cluster | - | Clear filter button; "All" chip | Transient (T) | "I'm focused on my world" | "Showing 4 Stage events" announced with filter change |
| B3 | Registration Closed (season) | G1 ≠ Registration Open; tiles still visible | All event tiles visible; ALL status badges = "Closed"; CTA on tiles disabled (with text explanation - blacklist #57) | Tap events → P-04 (read-only); Back → P-01 | Register from tile | Honest season state in header reassures | Persistent | "Events exist, just not right now" | "Registration closed" announced at page level |
| B4 | Empty results | Filter applied but no matching events exist (edge: custom filter) | "No events match this filter" + cluster tags remain | Clear filter; select different cluster | - | Clear filter → returns to B1 | Transient (T) | "Easy mistake, one tap to fix" | "No events match the filter" announced |
| B5 | Loading | Initial page load | Skeleton frames: 5-6 slip outlines filling space; amber pulse | Wait | Tap events (tiles not interactive) | Content loads → B1; timeout → A7 | Transient (T, <3s target) | "The world is forming, not broken" | "Loading content" announced once |
| B6 | Partial (some full, some open) | At least one event = Full; at least one = Open | Mixed status badges: some "Open", some "Full", some "Closed" on the same page | Tap Open events → Register; tap Full → see honest message + alternatives | Register for Full events | B-04 Full badge + "View other events" button guides to open events | Persistent | "Some are taken, others are available" | Per-tile status announced (aria-label includes status) |

---

### 7.C EVENT DETAIL (P-04)

| # | State Name | Trigger | Visible Behavior | Actions Available | Actions Blocked | Recovery Path | Duration | Confidence | Screen Reader |
|---|---|---|---|---|---|---|---|---|---|
| C1 | Normal | Default; registration open for this event | All zones visible: personality, facts, rules, judging, materials, FAQ, Register CTA active | Register → P-06; Back → P-03; View general rules → P-05; Contact → P-17 | - | - (no failure) | Persistent | "I know everything about this event" | H1 = event name; all zones announced as sections; sticky CTA announced |
| C2 | Registration Closed (this event) | B11 = Closed for this specific event; G1 may still = Registration Open | All zones visible + "Registration is closed for this event" in Zone G; CTA disabled + text | Back → P-03; other sections readable; Contact → P-17 | Register for this event | Alternative open events linked | Persistent | "This one is done, others may be open" | "Registration closed for [event name]" announced via aria-live="polite" |
| C3 | Event Full | B11 = Full | All zones visible + "This event is full" in Zone G; CTA disabled; "View other events" button | Back → P-03; "View other events" → P-03 (Landscape) | Register | Alternatives shown (events in same cluster still open) | Persistent | "Not me - but there are other stages" (Phase 2 Part 14.2) | "This event is full" announced; "View other events" highlighted |
| C4 | User Already Registered | C5 exists for this event + user | All zones visible + "You're already registered for this event" in Zone G; CTA replaced by → Your Space | Go to Your Space → P-12; review rules; Back → P-03 | Re-register | "You're already registered" reassures; Your Space link provides next step | Persistent | "No need to register again - I'm in" | "Already registered" announced |
| C5 | Loading | Initial page load | Skeleton: personality paragraph shape, facts grid, rules list shape (P-26) | Wait | Interact with content | Content loads → C1; timeout → Error overlay | Transient (T, <3s) | "Content is forming" | "Loading event details" announced |
| C6 | Rules Placeholder (TBD) | B7 content not yet resolved (Q5/Q10 TBD) | All zones visible; Rules section shows honest posture: "Full rules will be announced by [timing]" - NOT "rules TBD" | View available info; Back → P-03 | Can't verify full eligibility | Honest posture maintains trust; rules link updated when published | Persistent until resolved | "Rules are coming, not hidden" | "Rules forthcoming" announced as note |

---

### 7.D REGISTRATION FLOW (P-06 through P-09)

Each step shares these common states:

| # | State Name | Trigger | Visible Behavior | Actions Available | Actions Blocked | Recovery Path | Duration | Confidence | Screen Reader |
|---|---|---|---|---|---|---|---|---|---|
| D1 | Step Active (editing) | User on current step, editing fields | Current step highlighted in progress; fields interactive; Continue enabled (when valid) | Continue → next; Back → previous; Pause & Save (Step 2 only) | Skip steps | - | Transient | "I know what to do" | "Step N of 4: [step name]" announced |
| D2 | Step Complete (review) | All fields valid; user proceeds | Current step checkmarked; next step highlighted; progress bar advances | Continue → next; Back to edit | - | - | Transient | "Step done, more to go" | "Step N complete" announced |
| D3 | Validation Error | User submits step with invalid/missing field(s) | Step stays current (no advance); error messages inline (C-06); first error field focused; Continue stays disabled | Fix fields; Back → previous; Pause & Save | Advance to next step | Inline error messages (C-06) guide fix; form data preserved (Phase 2 Part 20.2) | Transient (T) | "Show me what to fix, don't reset" | Error count announced; first error focused and announced |
| D4 | Network Error | Submit fails due to network failure (P-23 overlay) | Error banner overlay appears; form data preserved behind overlay; world dimmed | Try Again; Finish Later | Submit (offline) | Retry → continue; persistent → "You can finish this later" + auto-save | Transient (T) | "My data is safe, this is temporary" | Error announced assertive; focus moves to banner |
| D5 | Submitting (in-flight) | User taps Confirm; network request in progress | CTA shows "Submitting…"; spinner replaced by slip skeleton in CTA area; step progress shows current | Wait | Edit fields (locked) | Success → Confirmation; failure → D4 | Transient (T, <5s) | "Please wait - almost there" | "Submitting registration" announced via aria-live="polite" |
| D6 | Session Expired | Auth token expired mid-flow | "Your session timed out" overlay; form data preserved; "Resume" button | Resume (restores session); Try Again | Submit without session | Resume → D1 with data intact | Transient (T) | Unfazed - data preserved (Phase 2 Part 14.5) | "Session expired, data saved" announced |
| D7 | Partial Form Saved | User taps "Pause & Save" | Toast: "Progress saved" (F-03); data persisted; user returned to Event Detail | Resume later (via link/email) | Continue with saved partial | Resume link (Phase 2 Part 14) → picks up at saved step | Persistent until resumed | "Nothing lost, I can come back" | "Progress saved" announced |
| D8 | Registration Closed Mid-Flow | G1 changes from Registration Open to closed while user is in flow | Honest close message: "Registration has just closed"; all entered data preserved; alternatives shown | View Events → P-03 (read-only); return to Event Detail | Submit registration | Honest closure (Phase 2 Part 14); data preserved; next path shown | Transient (T) | "Not my fault, I can check back" | "Registration has closed" announced |

---

### 7.E CONFIRMATION (P-11)

| # | State Name | Trigger | Visible Behavior | Actions Available | Actions Blocked | Recovery Path | Duration | Confidence | Screen Reader |
|---|---|---|---|---|---|---|---|---|---|
| E1 | Fresh Confirmation | Registration just submitted | Stamped receipt (C-09 + Phase 1.5 Stamp gesture); "What's next" section; actions | Go to Your Space → P-12; Register another → P-03; Print/Share | Edit registration | - (success state - no recovery needed) | Persistent | "I'm in. Undeniable." (Phase 2 Part 19) | "Registration confirmed for [event]" announced assertive |
| E2 | Retrieved Confirmation | User returns later to view confirmation | Same content as fresh; no Stamp gesture on retrieval (Stamp fires once) | Go to Your Space; Print/Share | - | Record always retrievable (Phase 2.5 invariant 2.4) | Persistent | "My record is safe and accessible" | Same as E1 (content is the same) |
| E3 | Lost Confirmation (recovery) | User lost confirmation link; arrives via recovery path | "We found your registration" + stamped receipt | Go to Your Space; Print/Share | - | Recovery path (Part 2 of Relationship Map) → E2 | Transient (T, one-time) | "Recoverable, not lost forever" | "Registration found" announced |

---

### 7.F YOUR SPACE / DASHBOARD (P-12, P-13)

| # | State Name | Trigger | Visible Behavior | Actions Available | Actions Blocked | Recovery Path | Duration | Confidence | Screen Reader |
|---|---|---|---|---|---|---|---|---|---|
| F1 | Empty (no registrations) | Logged in, C5 = empty set | Waiting Slip (F-04): centered frame, "This slip is waiting for your name" + "Explore Events" CTA | Explore Events → P-03 | View registrations | - (empty is not a failure) | Persistent until first registration | "I'm in the right place, ready to start" (Phase 1.5 §11.1.6) | "No registrations yet. Explore events to get started" |
| F2 | Has Registrations | C5 ≥ 1 registrations | Full dashboard: Greeting (D-01), Registrations (D-02), Announcements (D-04), Actions (D-05) | View registration details → P-04; Register more → P-03; View Schedule → P-14 | - | - | Persistent | "I see my events and what's new" | "Welcome back, [name]. [N] new announcements. [N] registrations." |
| F3 | New Announcements | D1 has new content since last visit | Delta Indicator (D-03) shows count; announcements section highlights new items | Read announcements; mark as read; other actions | - | Marking read decrements delta | Transient (per-announcement) | "I know what changed" (Phase 2 Part 8.3) | "[N] new announcements" announced via aria-live="polite" |
| F4 | Approaching Event | Event date within 7 days (or configurable) | Registration records show preparation checklist (B9 reminder); "Getting ready for [event]" context | View event rules; view materials list; view schedule | - | - | Seasonal (P) | "I'm prepared" | Event approaching announced in record card |
| F5 | Event Day | Event date = today | Registration records show: time, venue, "View Details" prominent | View Details → P-04; View Schedule → P-14 | Edit registration (closed) | "You're all set" reassurance | Transient (1 day) | "Calm and ready, not panic" | "Today is [event] day" announced |
| F6 | Post-Event Results | G1 = Post; results available | Registration records show result (winner status if available); archive context | View Winners → P-21; View Gallery → P-20 | Register | - | Seasonal (S) | "I can see what happened" | "Post-event results available" announced |
| F7 | Auth Required | User not logged in; tries to access Your Space | Login screen (P-22) presented | Login; Back to Welcome Beat | View dashboard | Login → F1 or F2; recovery path on failure | Transient (T) | "I need to sign in - clear requirement" | "Please sign in to access Your Space" |
| F8 | Loading | Dashboard initial load | Skeleton frames for greeting + records + announcements (P-26) | Wait | Interact | Content loads → F1 or F2; timeout → error | Transient (T, <3s) | "Loading, not broken" | "Loading Your Space" announced |

---

### 7.G SCHEDULE (P-14)

| # | State Name | Trigger | Visible Behavior | Actions Available | Actions Blocked | Recovery Path | Duration | Confidence | Screen Reader |
|---|---|---|---|---|---|---|---|---|---|
| G1 | Empty (not published) | G2 = D2 exists but no data yet; G1 < Approach | Honest placeholder: "Schedule will be published during the Approach phase" | View events; return to Your Space | View timings | Honest posture → schedule populated at season flip (Phase 2.5 §8.1) | Persistent until published | "Schedule is coming, not lost" | "Schedule not yet published. Will be available soon." |
| G2 | Partial (some TBD) | Some events have times assigned; some do not | Schedule shows what is known; TBD events show "Time TBD" posture | View published slots; link to event detail for TBD events | View complete schedule | Schedule populated over time; honest postures remain | Persistent until complete | "What's known is visible, unknown is honest" | "Schedule partially available" announced |
| G3 | Complete | All events have times assigned | Full schedule visible; cluster filters functional; event detail links work | Filter by cluster; tap time slot → P-04; share | - | - (healthy state) | Persistent | "I can plan my day" | Full schedule announced via structured landmarks |
| G4 | User's Events Highlighted | Registered user views schedule | User's registered events visually distinguished (not color-only - blacklist #51: outline + text label) | Tap highlighted event → P-04; View all | - | Filter to "My Events" chip | Persistent | "My events are easy to find" | "Your events" group announced separately |
| G5 | Today Highlighted | G1 = Live; current day in schedule | Day header for today prominently marked; events for today sorted first | View today's events; tap slot → P-04 | - | Auto-updates at midnight | Transient (1 day) | "I know what's happening today" | "Today's events" announced first |

---

### 7.H QUIET CORNERS (P-15 through P-18)

All quiet corners share three states:

| State Name | Trigger | Visible Behavior | Actions Available | Actions Blocked | Recovery Path | Duration | Confidence | Screen Reader |
|---|---|---|---|---|---|---|---|---|
| **Normal** | Content resolved | Full content zone; related actions at bottom | Read; related links; back to context | - | - | Persistent | Content answers the doubt | H1 announces topic; content announced in structure |
| **Content Pending** | Content = P (placeholder per Charter §7) | Honest posture: "Details coming from organizer" + related actions | Related page links; back to context | Read full content (not yet available) | Honest posture maintains trust; content published when resolved | Persistent until resolved | "It's coming, not hidden" | "Content forthcoming" announced |
| **Placeholder** | Content = F-gated (social, sponsors, Q15/Q16) | Area not rendered (quiet gap posture - Phase 2.5 §11.1) | - | Access area (not yet available) | Area appears when content exists (F-gate) | Persistent until content | No noise from absent content | Link not rendered - no announcement |

---

### 7.I ADMIN STATES (A-01 through A-07)

#### A-02 Admin Dashboard

| State Name | Trigger | Visible Behavior | Actions Available | Actions Blocked | Recovery Path | Duration | Confidence | Screen Reader |
|---|---|---|---|---|---|---|---|---|
| **Has Data** | Organizers exist; registrations exist | Overview cards: season state, registration count, content status, pending items | Navigate to admin areas; quick actions | - | No failure (internal tool) | Persistent | "I see the full picture" | Dashboard announced with metric summaries |
| **Empty** | Fresh install; no registrations yet | Overview cards with zeroes; "Start by setting the season" context | Change season → A-06; add content → A-03 | Export registrations (none) | Set season first; add content next | Persistent until first data | "New setup, clear first steps" | "Dashboard initialized" announced |

#### A-04 Admin Registrations

| State Name | Trigger | Visible Behavior | Actions Available | Actions Blocked | Recovery Path | Duration | Trust | Screen Reader |
|---|---|---|---|---|---|---|---|---|
| **Has Entries** | Registrations exist | Table (H-01) with all registrations; export button | Filter, sort, view detail, export | - | - | Persistent | "All registrations visible" | Table structure announced |
| **None** | No registrations | "No registrations yet" + link to check season state | Go to Dashboard; change season | Export | Ensure season = Registration Open; wait for registrations | Persistent until data | "Empty, not broken" | "No registrations" announced |

#### A-03 Content Management

| State Name | Trigger | Visible Behavior | Actions Available | Actions Blocked | Recovery Path | Duration | Trust | Screen Reader |
|---|---|---|---|---|---|---|---|---|
| **Editing** | Organizer in content editor | Content area editable; Save/Cancel/Publish visible | Edit, save, cancel | Publish conflicting changes | Save resolves; cancel discards (with undo prompt) | Transient | "I'm in control" | "Content editing mode" announced |
| **Saved** | Content published | Content displays as read-only; last-updated timestamp | Edit (enter editing mode) | - | - | Persistent | "Changes live" | "Content published" announced |
| **Unsaved Changes** | Organizer edited but not saved | Editor dirty state; "You have unsaved changes" indicator | Save, discard | Navigate away (warned) | Save first; or discard with confirmation | Transient | "Work is preserved" | "Unsaved changes" announced |

#### A-05 Announcements

| State Name | Trigger | Visible Behavior | Actions Available | Actions Blocked | Recovery Path | Duration | Trust | Screen Reader |
|---|---|---|---|---|---|---|---|---|
| **Has Drafts** | Drafts exist, not published | Draft list visible; "Publish" button | Publish, edit, delete draft | Preview on public site | Publish → appears in Your Space | Transient per draft | "Drafts don't leak" | "Announcement drafts available" |
| **None** | No announcements | "No announcements yet" + "Create first announcement" | Create new announcement | - | Create draft → publish | Persistent until created | "Starting fresh" | "No announcements" announced |

#### A-06 Season Control

| State Name | Trigger | Visible Behavior | Actions Available | Actions Blocked | Recovery Path | Duration | Trust | Screen Reader |
|---|---|---|---|---|---|---|---|---|
| **Current Visible** | Season is set | Current season displayed prominently; "Switch season" with current → next option | Switch season; view impact preview | Switch to same state (no-op) | Switch → platform updates everywhere | Persistent | "I control the season" | "Current season: [name]" announced |
| **Switching** | Organizer initiates switch | "Changing to [X]…"; confirm; impact summary | Confirm, cancel | Interact with public site (locked briefly) | Confirm → state flips; cancel → reverts | Transient (T, seconds) | "Safe switch" | "Season changing to [name]" announced |

---

### 7.J AUTH (P-22, A-01)

| # | State Name | Trigger | Visible Behavior | Actions Available | Actions Blocked | Recovery Path | Duration | Confidence | Screen Reader |
|---|---|---|---|---|---|---|---|---|---|
| J1 | Not Logged In | User attempts to reach Your Space | Login form presented: credentials input + "Sign in" + "Forgot credentials" + back to Welcome | Login; Back to Welcome Beat | Access Your Space | Login → P-12; Forgot → recovery path | Transient (T) | "Clear requirement - one login" | "Sign in to Your Space" |
| J2 | Login In Progress | User submits credentials | "Signing in…" indicator; form disabled | Wait | Edit credentials | Success → P-12; failure → J3 | Transient (T) | "Please wait" | "Signing in" announced |
| J3 | Login Failed | Wrong credentials submitted | "Incorrect credentials" error inline; recovery path visible ("Reset" or Contact) | Retry; Reset credentials; Contact | Access Your Space | Recovery path (Phase 2 Part 14) → J1 | Transient (T) | Calm, guided, no blame (Phase 2 Part 14.3) | "Login failed, please try again" announced |
| J4 | Session Expired (mid-use) | Auth token expired during active use | "Your session has expired" overlay; "Refresh" button | Refresh (re-authenticates quietly) | Continue without auth | Refresh → restore session | Transient (T) | Unfazed - one-tap recovery (Phase 2 Part 14.5) | "Session expired, refreshing" announced |

**Note on future auth (TBD):** Exact auth model (email? school token? phone?) is TBD (Charter §7). State machine is structural and does not depend on auth mechanism.

---

### 7.K ERROR PAGES

| # | State Name | Trigger | Visible Behavior | Actions Available | Actions Blocked | Recovery Path | Duration | Confidence | Screen Reader |
|---|---|---|---|---|---|---|---|---|---|
| K1 | 404 - Lost Slip | Invalid URL reached | The Lost Slip (F-05): torn empty slip, "This slip got lost"; Go Back, View Events, Contact | Go Back → P-01; Events → P-03; Contact → P-17 | - (404 is not a failure state - it's the recovery) | Named exception (Phase 1.5 §11.1.5): memorable redirect | Transient (T) | "This is a named exception - memorable, not frightening" | "Page not found" announcement + navigation links |
| K2 | 500 - Server Error | Internal server error | Error overlay: "Something went wrong on our end"; Try again; Contact | Try Again; Contact → P-17 | All actions | Retry → healthy state; persistent → come back later | Transient (T) | Calm, informed, hopeful (Phase 2 Part 14) | "Server error" announced via role="alert" |
| K3 | Network Offline | Device has no network connectivity | Error banner overlay (F-02): "No internet connection"; Try Again; Finish Later | Try Again; Finish Later | All network-dependent actions | Network restores → resume at current screen | Transient (T) | Unbothered - temporary (Phase 2 §13.1) | "No internet connection" announced |
| K4 | Service Unavailable | Server returning 503 (maintenance/capacity) | Full-page: "We're doing some maintenance"; ETA if known; Come back later | Come back later; Back to home | All actions | Server restores → resume | Transient (T, minutes to hours) | Calm waiting - honest ETA | "Service unavailable" announced |
| K5 | Maintenance | Planned maintenance window | Full-page: "We'll be back soon"; countdown if ETA known | Back to last healthy page (cached) | All actions | Maintenance window ends → resume | Transient (T) | Informed - planned, not broken | "Maintenance in progress" announced |

---

### 7.L LOADING STATES

| # | State Name | Trigger | Visible Behavior | Actions Available | Actions Blocked | Recovery Path | Duration | Confidence | Screen Reader |
|---|---|---|---|---|---|---|---|---|---|
| L1 | Initial Page Load | Navigation to new page | Skeleton frames (F-01): slip outlines matching expected layout; amber pulse | Wait | Interact with content | Content loads → normal state; timeout → K3 or K2 | Transient (T, target <3s) | "The world is drawing itself" (not a spinner) | "Loading [page name]" announced once |
| L2 | Section Reveal | Scroll-triggered reveal of long content | Slip rises (Lift gesture) as section enters viewport | Scroll, interact with previous sections | Interact with content below fold | Content reveals on scroll (or instantly in reduced-motion) | Transient (T) | Content arrives naturally | No announcement - scroll-driven interaction |
| L3 | Form Submission | Tap Continue/Confirm in registration | CTA shows skeleton state; step progress dims | Wait | Edit fields | Success → next step or Confirmation; failure → error state | Transient (T, 1-5s) | "Almost there" | "Submitting" announced politely |
| L4 | Per-Zone Loading | Dynamic content zone loads (e.g., announcements) | Skeleton within the zone only; rest of page fully interactive | Interact with other zones; scroll | Interact with loading zone | Zone loads → content; timeout → honest placeholder | Transient (T) | Page is responsive, one zone loading | "Loading [zone name]" announced |

---

### 7.M EMPTY STATES

| # | State Name | Trigger | Visible Behavior | Actions Available | Actions Blocked | Recovery Path | Duration | Confidence | Screen Reader |
|---|---|---|---|---|---|---|---|---|---|
| M1 | No Events | Event list = empty (should not happen in normal operation) | "No events available" + link to Welcome Beat | Go to Welcome Beat | Browse events | Events populated by admin → normal state | Persistent until populated | Honest - not a bug, just empty | "No events available" announced |
| M2 | No Matching Events | Filter applied, no results | "No events match this filter" + "Clear filter" button | Clear filter → all events shown | - | Clear filter → B1 state | Transient (T) | "Easy fix" | "No events match" announced |
| M3 | No Registrations | User logged in, C5 = empty | Waiting Slip (P-13): "This slip is waiting for your name" | Explore Events → P-03 | View registrations | Register → P-12 transitions to F2 | Persistent until first registration | "Invitation, not rejection" (Phase 1.5 §11.1.6) | "No registrations yet" announced |
| M4 | No Announcements | D1 = empty | "No announcements yet" within Your Space; not a full screen | Continue with dashboard | Read announcements | Admin publishes → D-04 appears | Persistent until published | "Quiet, not broken" | "No announcements" noted quietly |
| M5 | No Schedule | D2 = empty / not published | Honest placeholder on Schedule page (P-14): "Schedule will be published soon" | View events; return to dashboard | View schedule details | Schedule published at Approach season → G3 | Persistent until published | "Coming, not lost" (Phase 2.5 §8.1) | "Schedule not yet available" announced |
| M6 | No Gallery (future) | D3 = F-gated | Area not rendered (quiet gap - Phase 2.5 §11.1) | Browse other content | View gallery | Gallery content added → P-20 active | Persistent until content | No noise from absence | Link not rendered - no announcement |

---

### 7.N STATE MACHINE AUDIT

**States defined per screen category:**

| Screen | States defined | Coverage |
|---|---|---|
| Welcome (P-01/P-02) | 7 | All seasons + error |
| Landscape (P-03) | 6 | Normal through partial |
| Event Detail (P-04) | 6 | Normal through placeholder |
| Registration Flow (P-06-P-09) | 8 | Active through mid-flow close |
| Confirmation (P-11) | 3 | Fresh through recovery |
| Dashboard (P-12/P-13) | 8 | Empty through loading |
| Schedule (P-14) | 5 | Empty through today |
| Quiet Corners (P-15-P-18) | 3 | Normal through placeholder (per page) |
| Admin (A-01-A-07) | 12 | Per screen: data/empty/editing |
| Auth (P-22, A-01) | 4 | Not logged in through expired |
| Error Pages | 5 | 404 through maintenance |
| Loading States | 4 | Initial through per-zone |
| Empty States | 6 | Events through gallery |
| **Total** | **77** | Every screen, every state fully specified |

**Verification:**
- Every state defines ALL required fields (trigger, visible, available, blocked, recovery, duration, confidence, screen reader).
- Every failure state has a named recovery path (Phase 2 Part 14: no dead ends).
- Every transitional state is marked Transient.
- Every seasonal state is marked Seasonal.
- Confidence preservation follows Phase 2 Part 14.3 (calm, informed, hopeful).
- Screen reader treatment is specified for every state (Phase 0 §12.7).
- No state leaves the user without a next action.

---

*End of Part 7 - State Architecture.*

---

## PART 8 - ACCESSIBILITY ARCHITECTURE

Complete accessibility architecture: behavioural requirements, not code. Every requirement states WHY it is required (constitution clause) and HOW it will be verified (manual test protocol or automated check).

**Governing mandate:** Phase 0 §12.7 - "WCAG AA, keyboard-complete, screen-reader compatible, reduced-motion supported - not a nice-to-have." Bible Constitution 10 - "Accessibility is invisible design."

---

### 8.A KEYBOARD JOURNEYS

For each screen type, complete tab order and shortcut behaviour.

#### P-01 Welcome Beat

| Element | Tab Order | Navigation | Keyboard shortcut |
|---|---|---|---|
| Skip to Main Content link | 1 (I-07) | Jumps to Zone B | - |
| Logo Link "Home" | 2 (A-02) | → P-01 | Alt+Home (optional) |
| Nav Items: Events | 3 (A-03) | → P-03 | - |
| Nav Items: Your Space / Login | 4 (A-03) | → P-12 or P-22 | - |
| Nav Items: Schedule (if active) | 5 (A-03, conditional) | → P-14 | - |
| Nav Items: Info | 6 (A-03) | → P-19 | - |
| "Explore Events" CTA | 7 (C-10) | → P-03 | Enter or Space |
| Footer: Info link | 8 (A-07) | → P-19 | - |
| Footer: Privacy link | 9 (A-07) | → P-18 | - |
| **On Tab reach end:** Wrap to Skip Link (standard WCAG pattern) | | | |
| **ESC:** No modal/overlay - no effect | | | |
| **Why:** Welcome Beat is the simplest screen; linear tab order matches reading order (top-down). No surprises. | | | |

#### P-03 Landscape

| Element | Tab Order | Navigation | Keyboard shortcut |
|---|---|---|---|
| Skip to Main Content | 1 | → Zone B | - |
| Logo Link | 2 | → P-01 | - |
| Nav Items (all) | 3-5 | Varies | - |
| Back Affordance (← Welcome) | 6 | → P-01 | - |
| Cluster Filter Toggle (mobile) or chips (desktop) | 7 - 12 | Filter results | Space toggles; Arrow keys navigate chips |
| Cluster Group Header: Stage | next | - (landmark, not focusable) | - |
| Event Tiles (Stage × 6) | next N | → P-04 | Enter/Space activates |
| Cluster Group Header: Mind | next | - | - |
| Event Tiles (Mind × 2) | next N | → P-04 | Enter/Space |
| Cluster Group Header: Art | next | - | - |
| Event Tiles (Art × 5) | next N | → P-04 | Enter/Space |
| Cluster Group Header: Maker | next | - | - |
| Event Tiles (Maker × 3) | next N | → P-04 | Enter/Space |
| "View Rules & Eligibility" | after last tile | → P-05 | - |
| Footer links | last | Varies | - |
| **Arrow keys within tile list:** Left/Right moves between tiles in same cluster; Up/Down moves between clusters | | | |
| **ESC:** No effect (no modal) | | | |
| **Why:** the event tiles are the primary content. Tab order follows visual order (cluster by cluster, in the fixed cluster order Stage → Mind → Art → Maker). Arrow keys add efficiency without overriding Tab. | | | |

> **Tab order is positional, not numbered.** Absolute tab indices are deliberately not stated, because the number of tiles per cluster is a property of the content, not of the interface. Cluster sizes for the 2K26 event set are **Stage 6 · Mind 2 · Art 5 · Maker 3** (Phase 0 §3.4). Any implementation that hard-codes four tiles per cluster is wrong. See Amendment AM-01.

#### P-04 Event Detail

| Element | Tab Order | Navigation | Keyboard shortcut |
|---|---|---|---|
| Skip to Main Content | 1 | → Zone B | - |
| Logo Link | 2 | → P-01 | - |
| Nav Items | 3-5 | Varies | - |
| Back Affordance (← Landscape) | 6 | → P-03 | - |
| Quick Facts section (landmark, not focusable) | - | - | - |
| FAQ Accordion items (collapsed) | varies by count | Expand/collapse | Enter/Space expands; Tab skips collapsed |
| FAQ Accordion items (expanded answer) | within expanded item | Tab through expanded content | - |
| Sticky CTA "Register" (mobile) | last before footer | → P-06 | Enter/Space |
| Footer links | last | Varies | - |
| **Arrow keys within FAQ:** Up/Down moves between questions (whether collapsed or expanded); Enter/Space expands current | | | |
| **ESC:** No effect (no modal) | | | |
| **Why:** FAQ accordion is the only complex component. Arrow key support means a keyboard user can scan questions without expanding all. | | | |

#### P-06 through P-09 Registration Flow

| Element | Tab Order | Navigation | Keyboard shortcut |
|---|---|---|---|
| Skip to Main Content | 1 | → form fields | - |
| Step Progress Indicator | 2 (landmark) | Visual only | - |
| Form fields (sequential) | 3+ | Follows field order | Tab moves to next; Enter moves to next (if last field → submit) |
| Agreement Checkbox (P-08) | varies | Toggle | Space toggles |
| Select Dropdown (P-07, school/class) | varies | Open/close | Arrow keys navigate options; Enter selects |
| Continue CTA | last in form | → next step / submit | Enter or Space |
| Back CTA | before Continue | → previous step | Enter or Space |
| Pause & Save (P-07) | before Continue | Save and exit | Enter or Space |
| **ESC:** No effect (registration flow is the page, not a modal) | | | |
| **Why:** Form tab order must follow field labels exactly. No field is skipped. Enter as submit shortcut is standard form convention. Agreement checkbox requires Space (standard WCAG). | | | |

#### P-11 Confirmation

| Element | Tab Order | Navigation | Keyboard shortcut |
|---|---|---|---|
| Skip to Main Content | 1 | → Stamp | - |
| Logo Link | 2 | → P-01 | - |
| Nav Items | 3-5 | Varies | - |
| Confirmation content (read-only, landmark) | - | - | - |
| "Go to Your Space" CTA | next | → P-12 | Enter/Space |
| "Register Another" CTA | after | → P-03 | Enter/Space |
| "Print/Share" link | after | Print dialog / share | Enter |
| Footer | last | Varies | - |
| **Why:** Confirmation is read-first. Actions are below the stamp. Linear order. | | | |

#### P-12 Your Space

| Element | Tab Order | Navigation | Keyboard shortcut |
|---|---|---|---|
| Skip to Main Content | 1 | → Greeting | - |
| Logo Link | 2 | → P-01 | - |
| Nav Items | 3-5 | Varies | - |
| Greeting Card (landmark, not focusable) | - | - | - |
| Registration Record Cards | sequential | → P-04 (tap event link) | Enter/Space |
| Announcement Cards | sequential | Expand/collapse (mobile) or read | Enter/Space for expand |
| Action Buttons | after registrations | Varies by season | Enter/Space |
| Footer | last | Varies | - |
| **Arrow keys within records:** Up/Down moves between registration records | | | |
| **Why:** Dashboard is scan-and-act. Arrow keys let users navigate records quickly. | | | |

#### P-14 Schedule

| Element | Tab Order | Navigation | Keyboard shortcut |
|---|---|---|---|
| Skip to Main Content | 1 | → Schedule | - |
| Logo Link | 2 | → P-01 | - |
| Nav Items | 3-5 | Varies | - |
| Cluster Filter chips | 6-10 | Filter events | Space toggles; Arrow keys navigate |
| Day Headers | sequential (landmarks) | - | - |
| Time Slot Cards | sequential within day | → P-04 | Enter/Space |
| Footer | last | - | - |
| **Arrow keys within schedule:** Up/Down moves between time slots; Left/Right moves between days | | | |
| **Why:** Schedule is a two-dimensional data view. Arrow keys match table navigation conventions. | | | |

#### Quiet Corners (P-15 through P-18)

| Element | Tab Order | Navigation |
|---|---|---|
| Skip to Main Content | 1 | → content |
| Back Affordance | 2 | → previous |
| Content (landmark, read-only) | - | Scrolls naturally |
| Related links | last | → related page |

#### Admin Screens (A-01 through A-07)

| Element | Tab Order | Navigation |
|---|---|---|
| Admin nav links | 1+ | Between admin screens |
| Table cells / form fields | In table/field order | Tab, Arrow keys for tables |
| Action buttons | After content | Enter/Space |
| Toggle switches | In visual order | Space or Enter toggles |

---

### 8.B FOCUS ORDER & MANAGEMENT

Per screen, complete focus management specification:

#### First and Last Focusable Elements

| Screen | First focusable | Last focusable |
|---|---|---|
| P-01 Welcome Beat | Skip Link → Logo | Footer Privacy link |
| P-03 Landscape | Skip Link → Logo | Footer link |
| P-04 Event Detail | Skip Link → Logo | Sticky CTA → Footer |
| P-06-P-09 Registration | Skip Link → Step Progress → First Field | Continue → Footer |
| P-11 Confirmation | Skip Link → Logo | Print/Share → Footer |
| P-12 Your Space | Skip Link → Logo | Action Buttons → Footer |
| P-14 Schedule | Skip Link → Logo | Last time slot → Footer |
| P-22 Login | Skip Link → First credential input | Back to Welcome → Footer |
| Error Pages | Skip Link → Primary error action | Secondary action |

#### Focus After Page Transitions

| Transition | Where focus lands |
|---|---|
| Navigation to any page | First focusable element (Skip Link or Logo) |
| Back from Event Detail to Landscape | Back Affordance (contextual return) |
| Back from Landscape to Welcome | Logo / Skip Link (home reorientation) |
| Submit Registration → Confirmation | H1 on Confirmation page (announces success) |
| Form Error occurs | First error field (focus moves to the problem) |
| Filter applied on Landscape | Results count or first result in filtered set |
| Accordion expanded (FAQ) | Expanded answer text |
| Drawer opened (A-05, mobile nav) | First nav item in drawer (focus trap begins) |
| Drawer closed (A-05) | Back to the trigger button (A-04) |

#### Logical Order Rule

**Logical reading order MUST equal DOM order MUST equal visual order.** There is no "visually first but DOM last" pattern anywhere in the platform. Visual stacking (z-index) never changes DOM order. This rule is absolute.

**Verification:** Automated accessibility audit (axe, Lighthouse); manual screen reader walk-through of every screen.

**Trace:** Phase 0 §12.7 (WCAG AA); WCAG 2.1 SC 4.1.2 (Name, Role, Value); Bible Constitution 10.

---

### 8.C READING ORDER

Defined per screen type. Screen reader logical order = DOM order = visual order.

#### P-01 Welcome Beat

1. Skip Link (hidden, first in DOM)
2. Site Header (Logo + Nav Items)
3. H1: Festival Identity
4. p: Festival Description
5. Status text (season state)
6. CTA: "Explore Events"
7. Secondary link: "About"
8. Footer

#### P-03 Landscape

1. Skip Link
2. Site Header
3. H1: "Events"
4. Back Affordance
5. Filter group
6. H2: "Stage" → Tiles → H2: "Mind" → Tiles → H2: "Art" → Tiles → H2: "Maker" → Tiles
7. "View Rules & Eligibility"
8. Footer

#### P-04 Event Detail

1. Skip Link
2. Site Header
3. H1: Event Name
4. Back Affordance
5. Cluster Tag
6. H2: Personality → Paragraph
7. H2: Quick Facts → Fact list
8. H2: Rules → Ordered/Unordered list
9. H2: Judging Criteria → List
10. H2: Things to Bring → List
11. H2: FAQ → Accordion items
12. CTA: Register (Zone G)
13. Footer

**All headings follow a strict H1 → H2 → H3 hierarchy. No skipped levels within any section. H1 exists exactly once per page.**

**Trace:** Phase 0 §12.7; WCAG 2.1 SC 1.3.1 (Info and Relationships).

---

### 8.D SCREEN READER LOGIC

#### Heading Hierarchy Per Screen Type

| Screen | H1 | H2 | H3 |
|---|---|---|---|
| P-01 Welcome Beat | "EVOKE 2K26" (or edition title) | None (one-page, no subsections) | None |
| P-02 Announcement | "EVOKE 2K26" | None | None |
| P-03 Landscape | "Events" | Cluster names: "Stage" / "Mind" / "Art" / "Maker" | None (tiles use role="listitem", not headings) |
| P-04 Event Detail | Event name | "About" / "Quick Facts" / "Rules" / "Judging" / "Materials" / "FAQ" | None (accordion items use button, not headings) |
| P-05 Rules & Eligibility | "Rules & Eligibility" | "General Rules" / "Eligibility" / "Quotas" | None |
| P-06-P-09 Registration | Event name (restated) | Step title ("Declare What You're Registering For", etc.) | Field group labels |
| P-11 Confirmation | "Registration Confirmed" | "What's Next" | None |
| P-12 Your Space | "Your Space" | "What Changed" / "Your Registrations" / "Announcements" | None |
| P-13 Empty Dashboard | "Your Space" | None | None |
| P-14 Schedule | "Schedule" | Day headers (e.g., "Day 1 - [Date]") | None |
| P-15 About | "About EVOKE" | "Host" / "History" (if F-resolved) | None |
| P-16 FAQ | "Frequently Asked Questions" | None (accordion items are buttons) | None |
| P-17 Contact | "Contact" | None | None |
| P-18 Privacy | "Privacy Policy" | None (section headings if long) | None |
| P-19 Quiet Corners Hub | "More About EVOKE" | None | None |
| P-22 Login | "Sign In" | None | None |
| P-25 404 | Lost Slip message | None | None |
| Error Pages | Error type | None | None |
| Admin screens | Page title | Section headers | Column headers in tables |

**Heading rules:**
- H1 exists exactly once per page (WCAG 2.1 best practice).
- No skipped heading levels.
- Headings are semantic HTML, not aria-label fakes.
- Headings match the visual hierarchy a sighted reader sees.

#### ARIA Landmarks Per Screen Type

| Screen | banner | navigation | main | complementary | contentinfo |
|---|---|---|---|---|---|
| P-01 Welcome Beat | ✅ Site Header | ✅ Nav Items | ✅ Identity Zone | - | ✅ Footer |
| P-03 Landscape | ✅ Site Header | ✅ Nav + Filter | ✅ Event Tiles | - | ✅ Footer |
| P-04 Event Detail | ✅ Site Header | ✅ Nav | ✅ Content Zones | ✅ Sticky CTA (mobile) | ✅ Footer |
| P-06-P-09 Registration | ✅ Site Header | ✅ Nav + Progress | ✅ Form | - | ✅ Footer |
| P-12 Your Space | ✅ Site Header | ✅ Nav | ✅ Dashboard | - | ✅ Footer |
| P-14 Schedule | ✅ Site Header | ✅ Nav + Filter | ✅ Schedule | - | ✅ Footer |
| Admin screens | ✅ Admin Header | ✅ Admin Nav | ✅ Content | - | - (no participant footer) |

**Landmark rules:**
- Every page has exactly one `main` landmark (Phase 0 §12.7).
- `banner` is the Site Header on every public page.
- `navigation` is the Nav Items group (plus filters on Landscape/Schedule).
- `complementary` is the Sticky Decision Bar on mobile Event Detail.
- `contentinfo` is the Footer.
- Admin screens omit `contentinfo` (no participant footer).

#### Live Regions - Dynamic Content Updates

| Dynamic Update | Where | aria-live value | Polling/Trigger |
|---|---|---|---|
| Form validation error | P-06-P-09 | `aria-live="assertive"` | Triggered on submit |
| Form success / saved | P-07 | `aria-live="polite"` | Triggered on save |
| Registration submitted | P-09/P-10 | `aria-live="assertive"` | Triggered on submit |
| Filter applied (Landscape) | P-03 | `aria-live="polite"` | Triggered on filter change |
| Filter applied (Schedule) | P-14 | `aria-live="polite"` | Triggered on filter change |
| Delta indicator update | P-12 | `aria-live="polite"` | On page load / new announcement |
| Step changed | P-06-P-09 | `aria-live="polite"` | On step transition |
| Network error appears | Any (overlay) | `aria-live="assertive"` | Triggered on error |
| Network restored | Any (overlay dismissal) | `aria-live="polite"` | Triggered on retry success |
| Announcement read | P-12 | `aria-live="polite"` | On mark-as-read action |

**Live region rules:**
- `assertive` is reserved for critical updates: errors and submission confirmations (immediate attention required).
- `polite` is used for contextual updates: filters, steps, announcements (inform without interrupting).
- No live region announces more than once per event (avoids repeated announcements).
- All live region text is human-readable (no error codes).

#### Alt Text Strategy

| Image type | Alt text | aria-hidden | Screen reader reading |
|---|---|---|---|
| Event Mark (B-05) | `alt=""` | `aria-hidden="true"` | Silenced - event name carries the semantic info. Decorative. |
| Cluster icons | `alt=""` | `aria-hidden="true"` | Silenced - cluster tag text carries the info |
| Pattern/background textures | `alt=""` | `aria-hidden="true"` | Silenced - decorative |
| Photography (P-20, future) | Descriptive alt text (scene content) | - | Read by screen reader |
| Logo | "EVOKE 2K26" | - | Read as home link |
| Stamp gesture graphic | "Stamped" | `aria-hidden="true"` | Silenced - confirmation text carries the meaning |
| Error icon | `alt=""` | `aria-hidden="true"` | Silenced - error text carries the info (blacklist #51: never icon-only) |
| Focus ring visual | - | - | Silenced - focus is a visual state, not a content element |

**Alt text rule:** If there is text next to the image (event name next to mark, cluster label next to icon), the image is decorative and has empty alt. If the image IS the content (photography), it has descriptive alt.

#### Form Labels

**ALL inputs have visible labels. Never placeholder-only labels. Never floating labels.**

- Labels sit above inputs (Phase 1 Bible §11).
- Labels are never hidden, never decorative.
- `aria-label` is used only when visual label is impossible (rare - skip link).
- `aria-describedby` links each input to its error message and/or helper text.
- `aria-required` marks mandatory fields.
- `aria-invalid="true"` marks fields with validation errors.

**Verification:** Automated audit (every input must have associated label); manual check of every form.

**Trace:** Phase 0 §12.7 (WCAG AA); Bible §11 (visible labels, errors with text); WCAG 2.1 SC 3.3.2 (Labels or Instructions); SC 3.3.1 (Error Identification).

#### Error Announcements

Every error:
1. Appears as visible text inline with the form field (C-06 component).
2. Is associated with the input via `aria-describedby` and `aria-invalid`.
3. Is announced to screen readers via an `aria-live="assertive"` live region.
4. Includes error COUNT when multiple errors exist ("3 errors found").
5. Moves focus to the FIRST error field.
6. Never uses error codes, never uses color alone.

#### Status Changes

| Change | Announced as | Priority |
|---|---|---|
| Registration submitted | "Registration confirmed for [event]" | Assertive |
| Registration saved (Pause & Save) | "Progress saved" | Polite |
| Filter applied | "Showing [N] [cluster] events" | Polite |
| Step advanced | "Step [N] of [total]: [step name]" | Polite |
| Agreement checked/unchecked | "Agreement accepted" / "Agreement declined" | Polite |
| Announcement marked read | "Marked as read" | Polite |

#### Status Messages

| Message type | aria-live | Example |
|---|---|---|
| Confirmation (success) | Assertive | "Registration confirmed" |
| Success (micro) | Polite | "Changes saved" |
| Error (form validation) | Assertive | "Please enter a valid email address" |
| Warning (deadline proximity, if real) | Assertive | "Registration closes in 2 days" |
| Information (status update) | Polite | "3 new announcements" |
| Network error | Assertive | "No internet connection" |

**Why:** Different severities require different notification urgency. Assertive interrupts; polite waits.

**Trace:** Phase 0 §12.7; WCAG 4.1.3 (Status Messages); Phase 2 Part 14.3 (Ringmaster's honest voice); Bible §11.

---

### 8.E CONTRAST REQUIREMENTS

#### Minimum Contrast Ratios

| Element | Minimum ratio | Applies when |
|---|---|---|
| Body text < 14px | 4.5:1 (AA) | Always |
| Body text ≥ 14px bold OR ≥ 18px regular | 3:1 (AA) | Always |
| Large Display text (>24px) | 3:1 (AA Large) | Identity moments |
| Interactive elements at rest | 3:1 (AA) | Buttons, links, inputs |
| Interactive elements in focus state | 3:1 (AA) | Focus ring on any element |
| Interactive elements in hover state | 3:1 (AA) | Hover-visible elements |
| Disabled elements | 3:1 (AA) | Disabled state + explanation text |
| Status indicator text | 4.5:1 (AA) | All status text |
| Text on imagery | 4.5:1 (AA) | Always requires scrim |
| Error state text | 4.5:1 (AA) | All error messages |

**ALL interactive elements must be visible at rest AND in all states (hover, focus, active, disabled).** No element should become invisible, indistinguishable, or indistinguishable-from-background in any state.

#### Focus Ring

- **Single warm amber outline on all surfaces** (Phase 1 Bible §11).
- **Minimum 2px visible width.**
- **Contrasts against both Ink and Paper surfaces** at AA minimum.
- **Visible at ALL times when element receives keyboard focus.**
- **Never removed for aesthetic reasons** (Bible Constitution 10: accessibility is invisible design).

#### Color-Only Status Forbidden

**No status indicator uses color alone.** Every status uses text + color (or icon + text).

| Status | Visual implementation | Color use |
|---|---|---|
| Registration Open | Badge: text "Open" + green accent | Color reinforces text |
| Registration Closed | Badge: text "Closed" + neutral tone | Text is primary |
| Registration Full | Badge: text "Full" + warm tone | Text is primary |
| Form Error | Text: "Please enter a valid email" + red accent | Text carries the meaning |
| Form Success | Text: "Saved" + green accent | Text carries the meaning |
| Active Nav Item | Underline or highlight + text | Visual state is perceivable without color |
| Current Step | Number/circle styled + text label | Number and label carry meaning |
| Disabled Element | Text explanation: "Registration is closed" + dimmed | Text explains why (blacklist #57) |

**ALL disabled states show an explanation text.** Silent disabled buttons are forbidden (Bible blacklist #57).

**Verification:** Automated contrast checker (axe, Lighthouse Color Contrast); manual test with color-blindness simulators (Protanopia, Deuteranopia, Tritanopia).

**Trace:** Phase 0 §12.7 (WCAG AA); Bible blacklist #51 (color-only status forbidden); blacklist #57 (disabled without explanation); Bible §11 (focus ring always visible).

---

### 8.F MOTION REDUCTION (prefers-reduced-motion)

Every gesture must have a static equivalent. ALL content must be fully deliverable without motion.

#### Gesture Reduction Map

| Gesture | Normal behavior | Reduced-motion behavior | Content deliverable? |
|---|---|---|---|
| **Sweep** (announcements, headlines) | Light bar sweeps across slip | Static color difference - headline appears at full contrast immediately | YES - headline is fully readable without sweep |
| **Lift** (event tiles, cards) | Slip rises from stack, slight overshoot | Permanent outline - tile has visible border at rest | YES - tile clickable without rise |
| **Stamp** (winners, confirmations) | Result snaps in with hard impact | Permanent bold highlight - result text is bold, no spring animation | YES - result text is readable without stamp |
| **Tear** (Art/Maker reveals) | Corner lifts like torn paper | Static torn corner shape - visible edge detail, no lift | YES - craft edge is visible as shape |
| **Curtain** (page transitions) | Content surfaces part | Instant surface change - new page appears immediately | YES - page content loads instantly |

**Rules:**
1. **No information is hidden behind any animation.** If motion is the only way to access information, the page fails reduced-motion (Bible 21; Phase 1.5 Part 3.5).
2. **Scrolljacking is never used**, regardless of motion preference (Bible blacklist #41).
3. **Reduced motion provides an equivalent experience**, not a degraded one. A user who enables reduced-motion reads the same content, performs the same actions, with the same cognitive load.
4. **All signature gestures are reduced.** No gesture fires when prefers-reduced-motion is active.

**Verification:** Manual test with `prefers-reduced-motion: reduce` enabled in browser; compare content visibility and interaction availability between motion and reduced-motion modes.

**Trace:** Phase 0 §12.7 (reduced-motion supported); Bible Constitution 21 (motion respects reduced preference); Phase 1.5 Part 3.5 (reduced motion static equivalents); Bible §9 (purpose rule).

---

### 8.G ERROR COMMUNICATION

Every error must satisfy ALL six requirements:

| # | Requirement | How it works | Constitution |
|---|---|---|---|
| 1 | **Visible in the visual flow** | Error appears inline below the failing input (C-06 component). Never tooltip-only. Never hidden behind a pop-up. | Bible §11 (visible labels, errors with text) |
| 2 | **Associated with the input** | `aria-describedby` links input to error text. `aria-invalid="true"` marks the field. | WCAG 3.3.1, 4.1.2 |
| 3 | **Uses TEXT, never color alone** | Error message is readable plain text. Red accent reinforces but does not carry the message. | Bible blacklist #51 |
| 4 | **Actionable guidance** | "Please enter a valid email address" not "Invalid". "This field is required" not "Error". | Phase 2 Part 14.3 (Ringmaster voice: warm, precise, no blame) |
| 5 | **Correct reading order** | Error text appears AFTER the input it belongs to, BEFORE the next input. DOM order is preserved. | WCAG 1.3.2 (Meaningful Sequence) |
| 6 | **Summary on validation fail** | Error count announced ("3 errors found"). Focus moves to first error. Error summary visible at top of form. | WCAG 3.3.1 (Error Identification) |

**Error voice rules:**
- Never robotic ("Error 403").
- Never blaming ("You forgot to enter...").
- Always warm and precise ("Please add your name so we know who's registering").
- Always actionable ("Enter a valid email" - tells the user HOW to fix).

**Verification:** Manual walkthrough of every form error scenario; automated audit (axe errors report); screen reader test (error text announced).

**Trace:** Phase 2 Part 14 (Failure Journeys); Phase 1 §1.6 (tone table); Bible §11; WCAG 3.3.1, 3.3.2, 4.1.2.

---

### 8.H FORM ACCESSIBILITY

All forms (Registration, Login, Admin) must satisfy:

| Requirement | How | Constitution |
|---|---|---|
| **All inputs have visible labels** | Labels above inputs, body type, never placeholder substitutes | Bible §11; WCAG 3.3.2 |
| **Required vs optional clearly marked** | `aria-required` + visual "* required" on all fields. Optional fields explicitly marked "optional" | WCAG 3.3.2 |
| **Grouped fields announced as groups** | Team members: `aria-labelledby` links to "Team Members" group label | WCAG 1.3.1 (Info and Relationships) |
| **Field validation: inline + summary** | Inline error below each field (C-06) + error summary at top of form | WCAG 3.3.1 |
| **Success confirmation announced** | `aria-live="polite"` on success toast (F-03) | WCAG 4.1.3 |
| **No time pressure** | No countdown within forms. Deadline information is honest but never urgent (blacklist #13) | Phase 2 Part 15.4; Charter §5 |
| **Autocomplete attributes** | `autocomplete="name"`, `autocomplete="email"`, etc. where applicable | WCAG 1.3.5 (Identify Input Purpose) |
| **Input type hints** | `type="email"`, `type="tel"` - enables proper virtual keyboards on mobile | WCAG 1.4.3 |

**Verification:** Automated audit (all inputs have labels, required marking, autocomplete); manual form walkthrough on mobile (keyboard type matching input type).

**Trace:** Phase 0 §12.7; Phase 2 Part 10 (registration psychology); Charter §5 (progressive confidence); WCAG 3.3 series.

---

### 8.I TOUCH ACCESSIBILITY

| Requirement | Rule | Constitution |
|---|---|---|
| **All targets ≥44px** | Minimum 44px height and width for ALL interactive elements (buttons, links, inputs, checkboxes, toggles, accordion triggers) | Bible blacklist #43; WCAG 2.5.5 |
| **Sufficient spacing** | Minimum 8px gap between any two interactive elements. Touch targets are never touching. | WCAG 2.5.3 (Pointer Gestures) |
| **No two-finger gestures** | No pinch, no two-finger swipe, no multi-touch required for any action. Every function works with a single tap. | Phase 2 §13.3 (one hand) |
| **No swipe-only actions** | Every swipe gesture has a tap/button alternative. No "swipe left to delete" without a visible delete button. | WCAG 2.5.1 (Pointer Gestures); blacklist #42 |
| **Touch targets not crowded** | Interactive elements in dense areas (Landscape tiles, Registration fields) maintain minimum spacing. No two interactive zones within 8px of each other. | WCAG 2.5.5 |

**Verification:** Automated touch target size audit; manual tap test on smallest target device (iPhone SE 375px width).

**Trace:** Phase 0 §12.7; Bible blacklist #42 (hover-only navigation forbidden), #43 (tiny tap targets); Phase 2 §13.1 (thumb is lazy and honest).

---

### 8.J COGNITIVE ACCESSIBILITY

| Requirement | Rule | Constitution |
|---|---|---|
| **Plain language** | All messages use plain, simple English. No jargon, no error codes, no institutional language. Phase 0 audiences include students and parents - the language must be accessible to both. | Phase 0 §2.1 (students), §2.3 (parents) |
| **Predictable navigation** | Navigation pattern is identical across all public screens. Header structure never changes. Back affordance always present beyond P-01. Footer always present. | Bible Constitution 11 (consistency over novelty) |
| **Error prevention** | Confirm before irreversible actions (Submit Registration). Review step (P-09) exists specifically for this purpose. | WCAG 3.3.4 (Error Prevention) |
| **No artificial time pressure** | Deadlines are honest and stated plainly. No manufactured urgency, no "limited seats!" text when real capacity is unknown. No countdown pressure during registration. | Phase 2 Part 15.4 (Trust Architecture); blacklist #13 |
| **Clear section headings** | H1 → H2 → H3 hierarchy is consistent. Section headings match the content they introduce. No generic headings ("Section 1", "Details"). | WCAG 1.3.1 |
| **Content digestible at each cognitive load level** | HIGH load (rules) is chunked and scannable. LOW load (confirmation) is minimal. Load alternates per phase of the journey - never sustained high load. | Phase 2 Part 7 (Cognitive Load Map) |
| **One primary message per moment** | Each screen has one dominant action. Competing CTAs do not exist. The primary action is visually prominent and structurally first. | Phase 2 Part 8.1 (Attention Architecture) |

**Verification:** Manual review of all copy against plain language guidelines; cognitive load map validated against Phase 2 Part 7.

**Trace:** Phase 0 §2.1 (student questions), §2.3 (parent trust); Phase 2 Part 7 (cognitive load), Part 8 (attention), Part 15 (trust); WCAG 3.1 series (Readability).

---

### PART 8 AUDIT

#### Requirement coverage:

| Category | Requirements defined | Constitution traces |
|---|---|---|
| Keyboard Journeys | 10 screen types fully mapped | Phase 0 §12.7; Bible Constitution 10 |
| Focus Order & Management | Per-screen first/last/focus-after defined | WCAG 4.1.2; Bible §11 |
| Reading Order | Per-screen DOM = visual = logical order | WCAG 1.3.1 |
| Heading Hierarchy | 18 screen types mapped | WCAG 1.3.1 |
| ARIA Landmarks | 6 screen types + admin | WCAG 1.3.1 |
| Live Regions | 11 dynamic updates specified | WCAG 4.1.3 |
| Alt Text Strategy | 9 image types specified | WCAG 1.1.1 |
| Form Labels | All inputs covered | WCAG 3.3.2, 4.1.2 |
| Contrast Requirements | 11 element conditions | WCAG 1.4.3 |
| Motion Reduction | 5 gestures → static equivalents | WCAG 2.3.3 |
| Error Communication | 6 requirements | WCAG 3.3.1 |
| Form Accessibility | 8 requirements | WCAG 3.3 series |
| Touch Accessibility | 5 requirements | WCAG 2.5 series; Bible #43 |
| Cognitive Accessibility | 7 requirements | Phase 2 Part 7; WCAG 3.1 series |
| **Total rules defined** | **106** | Every one traced to constitution + WCAG |

#### Verification matrix:

| Requirement type | Verification method | Pass criteria |
|---|---|---|
| Keyboard coverage | Manual tab-through on Chrome | Every element reachable; order matches visual |
| Focus management | Manual page transitions | Focus lands correctly on every navigation action |
| Screen reader | NVDA / VoiceOver walkthrough | All content announced; headings read correctly |
| Contrast | Automated audit (axe, Lighthouse) | Zero contrast failures (AA or higher) |
| Touch targets | Automated audit + manual on iPhone SE | All targets ≥44px; 8px spacing maintained |
| Reduced motion | Browser preference toggle + manual test | All content accessible without motion |
| Error states | Manual form walkthrough (all error scenarios) | All errors visible, associated, actionable |
| Heading hierarchy | Automated heading order check | No skipped levels; exactly one H1 per page |
| ARIA landmarks | Automated landmark check | banner, main, contentinfo present |
| Live regions | Screen reader test of each dynamic update | Updates announced with correct priority |
| Reading order = DOM order | Visual inspection of dev tools | No visual-first-DOM-last patterns |
| Plain language | Copy review against reading level guidelines | No jargon, no codes, clear English |

**Trace:** Phase 0 §12.7 (WCAG AA baseline, non-negotiable); Bible Constitution 10 (accessibility is invisible design); WCAG 2.1 AA success criteria (all applicable).

*End of Part 8 - Accessibility Architecture.*

---

## PART 9 - FORM ARCHITECTURE

Registration is the heart of the platform. This section defines the complete field architecture, validation behaviour, progressive disclosure strategy, and state management for every registration screen (P-06 through P-11). Every field order, every validation trigger, and every conditional branch answers a question from the registration psychology contract (Phase 2 Part 10) and the Progressive Confidence principle (Charter §5).

**Governing principles:**
- **Nothing asked may be a surprise** (Phase 2 Part 10.2): every field on every form must have been announced on a previous screen
- **Certainty BEFORE the doorway** (Phase 2 Part 10.1): rules are released at the event page, never at the form
- **Progressive Confidence** (Charter §5): each step must leave the user more certain than before
- **One action per screen** (Phase 0 §5.3): each registration step has a single forward action
- **No dead ends** (Phase 2 Part 14): every failure preserves data and offers exactly one recovery path
- **The form never blames** (Phase 2 Part 14.3): validation messages in warm, precise language

---

### 9.A REGISTRATION FLOW STRUCTURE

Six steps map to screens P-06 through P-11, in this fixed order: Declare Intent (P-06) → Participant Information (P-07) → Declaration & Agreement (P-08) → Review & Confirm (P-09) → Payment (P-10) → Submission/Confirmation (P-11). Payment (Step 5) is conditional on TBD resolution (Charter §7); when there are no fees the flow is five steps and Step 4 leads directly to Confirmation. **Payment always follows review — never precedes it** (Part 1 P-10; Part 2.8 forbidden paths; Phase 2 Part 15.4).

#### STEP 1: DECLARE INTENT (P-06)

**What exists on screen:**

| Field | Type | Required | Value source | Why it appears | Constitution |
|---|---|---|---|---|---|
| Event name | Display text (read-only) | - | Selected from Event Detail (P-04) | Restates the choice - "here is what you're registering for" (Phase 2 Part 10.2) | Phase 2 Part 10.2 |
| Cluster tag | Label (read-only) | - | Derived from event (B2) | Category context - reinforces the world they chose | Phase 0 §4.17 |
| Team format | Display text (read-only) | - | B4 team size (e.g., "Solo" / "Team of 2-4") | Removes ambiguity about whether they need teammates | Phase 2 Part 10.1 |
| Time limit | Display text (read-only) | - | B4 time limit (e.g., "Max 2 minutes") | Last certainty-check before commitment | Phase 2 Part 10.1 |
| Steps ahead | Visual indicator (C-05) | - | System (4 steps, plus payment if fees apply - see Amendment AM-05) | "Here is what you'll be asked" - progressive disclosure at the doorway (Phase 2 Part 10.3). The count is stated conditionally while fees remain unknown; a fixed number would be an invented fact. | Phase 2 Part 10.3; Charter §5; Amendment AM-05 |
| Requirements summary | Display text (read-only) | - | B12 (if any special requirements exist) | Final eligibility signal | Phase 0 §2.1 |

**Interaction:**
- Primary CTA: "Continue" → P-07
- Secondary: "Go back to event" → P-04 (Phase 2 Part 14: non-punishing retreat)
- No form fields - Step 1 is read-only restatement, not data collection

**Why this order:**
1. Event name first - anchors the choice
2. Cluster + team format - confirms the world and commitment scope
3. Time limit - last practical question before "do I commit?"
4. Steps ahead - transparency about the process (Phase 2 Part 10.3)

**Why this screen exists:**
- The psychological contract (Phase 2 Part 10.2): the participant has said "register" from the Event Detail. Before any data is collected, the platform must restate the exact thing they're registering for. This prevents the "I wasn't expecting that" moment (Charter §5).

**Validation:** None - no user input. Proceeding requires only confirming intent.

---

#### STEP 2: PARTICIPANT INFORMATION (P-07)

**What exists on screen:**

| Field | Type | Required | Placeholder? | Order | Why this position | Inline validation | Constitution trace |
|---|---|---|---|---|---|---|---|
| Full Name | C-01 Text Input | Required | No | 1 | Identity is the minimum commitment - easy to type, establishes who's registering | On blur: presence + alphanumeric | Phase 2 Part 10.3; Charter §5 |
| School | C-02 Select (or C-01 if TBD) | Required | No | 2 | School is the participant's affiliation - answered on Event Detail via eligibility (B6). Not a surprise. | On blur: selection required | Phase 2 Part 10.3; Phase 0 §2.2 |
| Class / Grade | C-02 Select (or C-01 if TBD) | Required | Eligibility TBD (Q5) | 3 | Eligibility narrows by class (Q5). Participant checked eligibility at Event Detail - this is just the data capture. | On blur: selection required | Phase 2 Part 10.3; Phase 0 Q5 |
| Primary Contact (Email OR Phone) | C-01 Text Input | Required | No | 4 | How the platform contacts them - announced at B12. One field, either email or phone (progressive: show email first). | On blur: format check (email regex / phone format) | Phase 2 Part 10.3; Phase 0 §2.1 |
| Team Members (conditional) | C-03 Team Member Block × N | Required (for team events only) | No | 5 | Only for events where B4 specifies team size > 1. Each member: Name + Class. | Per field: same as individual fields | Phase 0 §3.1; Phase 2.5 §5.1 |

**Progressive disclosure:**
1. Name appears first (always required, no conditional logic)
2. School appears after Name (participant is filling their identity)
3. Class appears after School (narrowing context: school → class)
4. Contact appears after academic identity (functional information, comes last before team)
5. Team Members appear only after all individual fields are filled AND the event is team-format (conditional - Phase 0 §3.1)

**Guardian contact (TBD):** Phase 0 §2.3 notes parents as a critical audience. However, the Charter declares team registration rules TBD (§7). A parent/guardian contact field does NOT appear unless the organizer explicitly requires it. The field is TBD-aware: the component structure (C-01) exists, the field is omitted if not needed.

**Why this field order:**

| Position | Field | Why here (registration psychology) |
|---|---|---|
| 1 | Name | Lowest friction - a name is easy. It starts the form with confidence (Phase 2 Part 22.1: low-energy form). The participant immediately feels the form is "about them." |
| 2 | School | Second-identity - confirms institutional participation. Also the first validation gate (invalid school = ineligible). Asked before class because class depends on school context. |
| 3 | Class | Third-identity - eligibility refinement. The participant saw their class eligibility on Event Detail (B6). Not a surprise. Asked after school because some eligibility rules are school-scoped. |
| 4 | Contact | Functional - not identity. Comes after identity is established. Either email OR phone (not both - progressive: show email, phone shown if email not entered). This was announced at B12. |
| 5 | Team Members | Highest friction - entering multiple names. Only for team events (conditional). Comes last because it is the most typing-intensive step. The participant is mentally prepared by Step 1's team format display. |

**Field order principle (Charter §5 - Progressive Confidence):** The form starts with easy identity, moves to eligibility confirmation, then functional data, then the most effort-intensive fields. Each field builds on what came before. Nothing is asked that was not announced.

**Validation behavior:**
- **Inline per-field:** On blur for required fields. On Enter for the current field (moves to next field if valid, shows error if invalid).
- **Step-level:** On "Continue" click: all fields validated. Error summary shown at top if multiple errors. Focus moves to first error.
- **Server validation:** Duplicate check (e.g., same school + class + event = already registered? TBD). Client validates format; server validates business rules.

**Team Member Block (C-03) behavior:**
- **Solo events:** Team Member Block is completely hidden - not just collapsed. Solo events have zero team member fields.
- **Team events:** Initial state shows N member blocks where N = minimum team size from B4 (e.g., 2 for Dumb Charades, 3 for Group Song).
- **Add/Remove:** "Add Member" button appears after all current members are filled. Clicking adds one more block (up to max team size from B4). Remove button on each block (never removable for last member - minimum enforced).
- **Per-member fields:** Name (C-01) + Class (C-02) only. No contact needed per member - the lead participant's contact covers the team.
- **Max visible:** Event's max team size is displayed as text above the team member area ("Team size: 2-4 members"). This is announced at B4.

---

#### STEP 3: DECLARATION & AGREEMENT (P-08)

**What exists on screen:**

| Field | Type | Required | Why it appears | Constitution |
|---|---|---|---|---|
| Originality statement | Display text (read-only) | - | Key rule summary: "Original work only - copying may lead to disqualification" (from B7) | Phase 2 Part 10.2 |
| Decency statement | Display text (read-only) | - | Key rule summary: "Content must be appropriate and respectful" (from B7) | Phase 2 Part 10.2 |
| Time limit statement | Display text (read-only) | - | Restated: "Your event's time limit is [X]" (from B4) | Phase 2 Part 10.2 |
| Judges' decision statement | Display text (read-only) | - | "Judges' decision is final" - universal across all events (Phase 0 3.3.1) | Phase 0 §3.3.1; Phase 1.5 Part 6.4 |
| Privacy reference | Link text | - | "How your data is handled" → P-18 (Privacy screen) | Phase 0 Risk 14 |

- **Checkbox (C-04):** "I have read and agree to the above" - NOT pre-checked (Phase 2 Part 15.4: no hidden terms). Links to full rules (→ P-04 Zone D) exist inline.
- **Interaction:** Primary CTA disabled until checkbox is checked. CTA text: "I understand. Continue." The button text IS the agreement.

**Why this screen exists:**
- Trust requires explicit acknowledgement (Phase 2 Part 10.2). The participant must see the essentials before reaching the final review. This is not a legal wall - it is confirmation that the critical rules are understood.
- Rules summaries are displayed; full rules link to Event Detail (single source, Phase 2.5 §9.1).

**Why this order:**
1. Originality - most consequential rule violation
2. Decency - values signal
3. Time limit - practical reminder
4. Judges' decision - universal, non-negotiable
5. Privacy - legal requirement, lowest emotional priority

**Decline behavior:** If the participant taps "Back" instead of checking the box, they return to P-07 with no penalty (Phase 2 Part 14: non-punishing retreat). If they leave entirely, they return to P-04.

---

#### STEP 4: REVIEW & CONFIRM (P-09)

**What exists on screen:**

| Field | Type | Source | Edit capability | Why | Constitution |
|---|---|---|---|---|---|
| Event name + cluster + format | C-09 Review Summary | From Step 1 (P-06) | Link → P-06 | Restates the choice - final mirror | Phase 2 Part 10.2 |
| Participant name | C-09 Review Summary | From Step 2 (P-07) | Link → P-07 | Identity confirmation | Phase 2 Part 10.3 |
| School + Class | C-09 Review Summary | From Step 2 (P-07) | Link → P-07 | Eligibility confirmation | Phase 2 Part 10.3 |
| Contact method | C-09 Review Summary | From Step 2 (P-07) | Link → P-07 | Functional confirmation | Phase 2 Part 10.3 |
| Team members (if applicable) | C-09 Review Summary | From Step 2 (P-07) | Link → P-07 | Team confirmation | Phase 2 Part 10.3 |
| Agreements acknowledged | C-09 Review Summary | From Step 3 (P-08) | Link → P-08 | Rules confirmation | Phase 2 Part 10.2 |
| Payment amount due (if applicable) | C-09 Review Summary | C3 (payment facts - TBD) | - (paid at Step 5) | The money fact is stated *before* commitment, never after (Phase 2 Part 15.4) | Phase 2 Part 15.4 |

**Last Check message:**
- A single sentence restating the registration: "You're registering for [Event Name] as a [Solo/Team of N] from [School], Class [X]."
- This is the final certainty statement - the last thought before committing should be "yes" (Phase 2 Part 10.2).

**Interaction:**
- Primary CTA: "Confirm Registration" → Step 5 (P-10 Payment) when fees apply; → P-11 Confirmation when they do not
- Secondary: "Edit Details" → returns to P-07 (edit all fields); individual edit links go to relevant step
- Cancel: "Cancel and Return to Event" → P-04 (no penalty)

**Why edit links go to specific steps, not all to P-07:**
- Editing event choice → P-06 (Step 1)
- Editing participant info → P-07 (Step 2)
- Editing agreements → P-08 (Step 3)
- Each edit link preserves the user's position in the flow - they go back to edit one thing, not restart entirely (Phase 2 Part 20.2: nothing lost).
- Payment is not editable here because it has not happened yet - the review states the amount due; the transaction occurs at Step 5.

---

#### STEP 5: PAYMENT (P-10 - TBD PLACEHOLDER)

**IMPORTANT:** This step is P-gated by Charter §7. If TBD resolves to "no fees," this step is omitted and Step 4 (P-09) goes directly to Confirmation (P-11).

**Why payment comes AFTER review (not before):** money follows commitment, never precedes it (Part 1, P-10 Golden Question). The participant confirms *what* they are registering for, and only then transacts. Reversing this order is a forbidden path (Part 2.8: payment before event context).

**What exists on screen (structure only - no payment specifics invented):**

| Field | Type | Required | Placeholder? | Why | Constitution |
|---|---|---|---|---|---|
| Amount display | Display text (read-only) | - | Yes (C3 TBD) | Shows the exact amount when known - never a surprise (Phase 2 Part 15.4) | Charter §7; Phase 2 Part 15.4 |
| Payment method selector | Select / radio group | Conditional | Yes (gateway TBD) | Method selection when multiple options exist | Charter §7 |
| Payment status | Status display (B-04 variant) | - | Yes | Success / Failed / Pending state (Phase 2 Part 14) | Phase 2 Part 14 |
| "No double-charge" assurance | Display text (read-only) | - | No | Money trust message: visible always during payment | Phase 2 Part 15.4 |

**Honest placeholder (when payment details don't exist):**

The payment zone displays:
> "Registration is free of charge. No payment required."

When TBD resolves to charged registration:
> "Registration fee: [AMOUNT] - [PAYMENT DETAILS FROM ORGANIZER]"

**Money trust principle (Phase 2 Part 15.4):**
- The amount is displayed before any payment action
- "No double-charge" is stated in visible text, not fine print
- Payment gateway UI (when it exists) is embedded in the platform's frame - not redirected to a separate domain
- Payment failures are calm: "That didn't go through - no charge was made. Try again or come back."
- Pending state is visible in Your Space (D-02 status: "Pending")

**What it does NOT do (forbidden - Charter §5, Phase 2 Part 15.4):**
- No countdown timers
- No "limited seats" pressure during payment
- No hidden fees
- No redirect that disconnects from the platform

---

#### STEP 6: SUBMISSION (transition between P-09/P-10 and P-11)

**What the user sees:**

| Phase | Visible state | Description | Duration |
|---|---|---|---|
| In-flight | CTA shows "Submitting…" with skeleton (F-01) | Form locked (no edits). Progress indicator dims. | 1-5 seconds |
| Success | Redirect to P-11 (Confirmation) | Navigation happens automatically. User never sees a transient "success" screen. | Instant |
| Failure (retryable) | Error overlay (F-02): "Something went wrong - your data is safe" | "Try Again" button. All form data preserved. | Until retried |
| Failure (fatal) | Error overlay (F-02): specific message + Contact path | E.g., "Registration has just closed" (G1 changed). Data preserved. | Until resolution |

**What is preserved if submission fails:**
- ALL entered data (Phase 2 Part 20.2 - state preservation)
- Checkbox agreements (checked state)
- Step position (user returns to P-09 Review, not Step 1)
- Payment status (if applicable: failed payment not auto-retried)

**Resume capability:**
- User closes browser mid-submission → next visit shows "Resume registration?" overlay directing to Step they were on
- No data loss from browser close (local storage fallback - Phase 2 Part 11.3: state retention)
- Resume link expires after configurable period (TBD organizer setting, suggested: 48 hours)

---

### 9.B VALIDATION ARCHITECTURE

#### When validation fires

| Trigger | What is validated | Result |
|---|---|---|
| **On blur** (user leaves field) | Required fields: presence. Type-specific fields: format (email, phone). | Inline error (C-06) appears below the field if invalid. No error if field is valid. |
| **On Enter key** (within form) | Current field: same rules as blur. | If valid: focus moves to next field. If invalid: inline error appears, focus stays on current field. |
| **On "Continue" click** (step forward) | ALL fields on current step. | Error summary (count + list) shown at top of form. Focus moves to FIRST error field. Individual inline errors shown. Step does NOT advance. |
| **On "Confirm Registration"** (final submit) | ALL fields across ALL steps. | Error summary at top. Focus to first error. User directed to relevant step to fix. |
| **Server-side** | Business rules (duplication, eligibility, capacity). | Error returned as inline text. Client validation does not block retrying. |

#### Error presentation per field

- **Inline (C-06):** Appears immediately below the failing input. Danger-red text body, never icon-only. Associated via `aria-describedby`.
- **Error voice:** Warm, precise, actionable. Never "Error." Never "Invalid." Instead: "Please enter your full name" / "Select your school from the list" / "This email format doesn't look right" (Phase 2 Part 14.3).
- **Error count:** When Continue clicked with N errors: "3 fields need attention" - shown at top of form, `aria-live="assertive"`.

#### Error focus management

1. On Continue click with errors: focus moves to the FIRST error field (DOM order = visual order).
2. Error summary is announced to screen reader (`aria-live="assertive"`).
3. User fixes first error: inline error disappears. Moving to next field triggers its validation on blur.
4. When all errors resolved: error summary disappears. Continue becomes available.

#### Summary errors (before submit)

- On final "Confirm Registration": if any field across any step has an error, an error summary is shown at the top of P-09 with field names and error descriptions. Each error in the summary is a link that scrolls to and focuses the relevant field on the relevant step.

#### Recovery: user leaves and returns

- **Form persisted locally** (localStorage) for up to 48 hours (TBD organizer configurable).
- On return: if draft exists, "Resume registration?" overlay appears.
- Draft includes: all filled fields, checkbox states, step position.
- Draft does NOT persist after successful submission or explicit cancel.
- Draft is cleared on session expiry.

---

### 9.C FIELD ORDER JUSTIFICATION

Every field position justified using Phase 2 Part 10 (certainty before doorway):

| Field | Position in overall flow | Announced before registration at: | Why this position (registration psychology) |
|---|---|---|---|
| Event selection confirmation | Step 1 (P-06) | P-04 Event Detail (the user chose this) | Lowest friction start. Restates what they already decided. No typing needed. |
| Full Name | Step 2, Field 1 | Not explicitly - but identity is implied by "participant" language everywhere | Minimum identity. Easy to type. Builds momentum. |
| School | Step 2, Field 2 | B6 eligibility (school eligibility scope) | Second identity - school affiliation. The participant's context was checked at eligibility. |
| Class | Step 2, Field 3 | B6 eligibility + B4 team rules (class-scoped limits) | Third identity - class narrows. Checked at eligibility. Not surprising. |
| Contact (email/phone) | Step 2, Field 4 | B12 registration requirements | Functional. Comes after identity. Announced at B12. |
| Team Members | Step 2, Field 5 (conditional) | B4 team size + Step 1's team format | Highest friction. Conditional. Mental prep provided by Step 1. |
| Agreements | Step 3 (P-08) | B7 rules (Event Detail, Zone D) - participant READ the rules | Acknowledgement of what they read. Not a surprise. |
| Review | Step 4 (P-09) | - (it IS the summary of everything) | Final restatement. The mirror. Comes before payment so the amount due is seen in full context. |
| Payment | Step 5 (P-10, conditional) | TBD - amount stated at Step 4 review (Phase 2 Part 15.4) | After all commitment. Money comes last. |

**Golden Question check:** Does each field help reduce uncertainty (Charter §6 Q1/Q2)? Yes - each field confirms an identity or commitment already decided. None invents a new requirement.

---

### 9.D PROGRESSIVE DISCLOSURE IN FORMS

#### What appears first vs what appears after

| Appears first | Appears after | Why |
|---|---|---|
| Event name (read-only) | Everything else | Anchors the choice before any data is asked |
| Name | School, Class, Contact | Personal identity comes first (easy); institutional identity second |
| School | Class | School context before class - eligibility was scoped by school |
| Individual fields | Team member fields (conditional) | The participant enters their own data before entering teammates' |
| Agreement text | Agreement checkbox | Read before check - the checkbox is the confirmation, not the introduction |
| Review summary | Submit action | Read everything before committing - the final mirror precedes the final yes |
| "No double-charge" text | Payment action | Money trust before money action (Phase 2 Part 15.4) |

#### Conditional fields

| Condition | Hidden field | Revealed by | Screen |
|---|---|---|---|
| Event is solo (B4 team size = 1) | Team Member Block (C-03) | Event is team (B4 > 1) | P-07 Step 2 |
| Contact email not entered | Phone alternative | Email empty on blur | P-07 Step 2 |
| Payment not required (Charter §7 TBD = no fees) | Entire Step 5 (P-10) | TBD resolution | Flow routing |
| First visit (no draft exists) | Nothing extra | Draft exists in localStorage → "Resume" overlay | P-06 or later |

**Why progressive disclosure matters (Phase 2 Part 10):**
- The participant should never see more fields than necessary. Solo participants don't see team member fields. Team-only logic is hidden from solo events.
- This reduces cognitive load at Step 2 (Phase 2 Part 7.1: forms are LOW cognitive load, but field count increases load).

---

### 9.E TEAM vs SOLO REGISTRATION

#### How the flow differs

| Aspect | Solo Event | Team Event | Why |
|---|---|---|---|
| Step 1 (Declare Intent) | "Solo" shown in team format | "Team of [N]" shown in team format | Different scope (Phase 2 Part 10.2) |
| Step 2 (Participant Info) | Name, School, Class, Contact only | Name, School, Class, Contact + Team Members block | Variable data capture (Phase 0 §3.1) |
| Team Member Block | **Completely hidden** (not shown at all) | **Visible** with N min/max slots (from B4) | Conditional by event type |
| Add/Remove controls | Never appear | Appear per member row | Only when team exists |
| Review (Step 5) | Single participant summary | Team roster in summary | Reflects what was entered |
| Confirmation (P-11) | "You're registered for [Event]" | "[School] Team of N is registered for [Event]" | Accurate record |

#### Team event specifics

**Max members per event:**
- Displayed as text: "Team size: [min]-[max] members" (from B4)
- This text is visible in Step 2 (P-07), above the Team Member Block area
- Adding beyond the max is architecturally prevented (Add button disabled when max reached, with text: "Maximum [N] members reached")
- Removing to below min is architecturally prevented (Remove disabled when min reached)

**Per-member data:**
- Each team member requires: Name + Class only
- No per-member contact needed - lead participant's contact covers the whole team
- No per-member school needed - school is shared

**Why this architecture:**
- Solo events are simpler - fewer fields reduce friction
- Team events are more complex but the participant (often a coordinator) expects batch entry
- The flow accommodates both without either feeling like a compromised version of the other
- Coordinator workflow: one registration session covers the entire team (Phase 0 §2.2: coordinator's operational need)

---

### 9.F ABANDONED & RESUMABLE FORMS

#### When does a partially filled form save?

| Trigger | What is saved | Where |
|---|---|---|
| **On any field change** (typing, selecting) | Current field value ONLY | localStorage (per-event draft) |
| **On "Pause & Save"** (explicit action) | All fields + checkbox states + step position | localStorage + toast confirmation (F-03: "Progress saved") |
| **On "Back" (step retreat)** | All fields up to current step | Persisted (forward navigation retains data) |
| **On browser close** (automatic) | Last "on field change" state | localStorage (survives reload) |

#### Recovery mechanism

1. User returns to platform (any entry point)
2. System checks for existing draft (localStorage + event ID)
3. If draft exists: overlay appears: "Pick up where you left off?" with event name and step number
4. "Resume" → directs to the step the user was on (preserves position)
5. "Start over" → clears draft, starts at P-06

**Why this approach (Phase 2 Part 14):**
- Short mobile sessions mean interruptions are common (Phase 2 Part 13.1)
- "Resume" reduces frustration and abandonment
- Drafts are event-specific (no cross-contamination)
- No data loss from browser close aligns with Phase 2 Part 20.2 (state preservation)

#### Explicit "Save and Return Later"

- **"Pause & Save" button** exists on P-07 (Step 2): secondary action, below Continue/Back
- Tapping saves all current data and returns user to Event Detail (P-04) - not the Welcome page
- **Why P-04 and not P-01:** The user was at the event page when they started. Returning them to the event maintains context and allows them to re-read rules before resuming (Phase 2 Part 11.3: context preservation)
- Toast (F-03) confirms: "Progress saved. You can return anytime."

#### Draft persistence duration

| Duration | Rationale | Configurable? |
|---|---|---|
| **48 hours** (default) | Covers typical gap: student browses in recess, registers later that day or next. Long enough for real-world timing (school days, weekends), short enough to avoid stale data. | Yes (TBD organizer setting) |
| **Cleared immediately on:** | | |
| Successful submission | Registration complete - no need for draft | - |
| Explicit cancel | User chose to stop - respect the decision | - |
| Registration closed (G1 changes) | Flow no longer valid - honest closure message replaces draft | - |
| 48 hours elapsed | Data may be stale (school, class changes) - fresh start is safer | Yes |

#### Draft edge cases

| Edge case | Behavior | Constitution |
|---|---|---|
| Two drafts (two different events) | Each event has its own draft key. Both persist independently. | Phase 2 Part 10 |
| Draft exists but event is now full | Resume overlay: "This event is now full. Your saved info is intact - would you like to register for a different event?" | Phase 2 Part 14.2 |
| Draft exists but registration closed | Resume overlay: "Registration has closed. Your info is saved for next time." | Phase 2 Part 14 |
| Draft corrupted (invalid data) | Fallback: start fresh at P-06. No user-visible error. | Phase 2 Part 20 |

---

## PART 10 - SEARCH & DISCOVERY

How users find events - the discovery system. Governing principle: discovery must answer "what can I do?" quickly (Phase 0 §6.1-6.2) and guide toward narrowing (Phase 2 Part 3.3: clusters prevent choice paralysis with 16 events).

---

### 10.A DISCOVERY METHOD JUSTIFICATION

| Method | Exists? | Justification |
|---|---|---|
| **Category browsing (4 clusters)** | **PRIMARY** | Sixteen events are naturally grouped into Stage/Mind/Art/Maker (Phase 0 §4.17). Clusters reduce choice from 16 to 4 worlds. Progressive disclosure: headline → category → details (Phase 0 §5.3). |
| **Full event list (16 events)** | **ALWAYS AVAILABLE** | All 16 tiles visible by default on P-03 Landscape. Cluster groups provide structure, but all events are present and scannable. No hidden events. |
| **Text search** | **NOT BUILT - justified removal, re-confirmed against real content (Amendment AM-04)** | 16 events is small enough that search adds no value. A student can scan all 16 tiles within 30 seconds (Phase 0 §2.1 mobile scanning). Search implies a catalogue, not a curated festival (Phase 2 Part 3.3: guided choice, not catalogue browsing). **Golden Question:** Does it help someone choose? No - clusters do that better. |
| **Filters (cluster, on/off-stage, status)** | **YES - cluster + status** | Cluster filter (I-04): narrows to 4-at-a-time for focused scanning. Status filter: honest visibility (Phase 2 Part 14). On/off-stage filter: exists implicitly via cluster group headers (Stage cluster = most on-stage, etc.). |
| **Bookmarking** | **NOT BUILT - justified removal** | No "save for later" button exists. Why: the event exists forever until season changes. A returning user sees the same events (Phase 2 Part 8.3: return engine). Bookmarks imply a large catalogue to lose items in. With 16 events, every event is findable in one tap from Landscape. |
| **Recent / Recently Viewed** | **NOT BUILT - justified removal** | 16 events is small enough that a user finds their event by scanning, not by remembering "which one did I look at?" Recency implies a catalogue. The platform guides, it does not recall. |
| **Recommendations** | **NEVER - justified removal** | Personal choice is the festival's core (Phase 0 §1.4: students find THEIR event). Recommendations imply "you might like this" - which undermines the curated discovery of 16 events. No collaborative filtering, no "popular events," no "students like you chose." The festival does not herd. |
| **Favorites / Heart icon** | **NOT BUILT - justified removal** | Adds a micro-interaction that solves nothing: the event tile already carries scanning density. Liking an event is not a useful action; registering is. |

> **Amendment AM-04 — search re-evaluated, still rejected.** Phase 4 Round 1 built the Landscape with all 16 real events and re-tested the question. Text search remains rejected for the current curated 16-event catalogue: cluster grouping reduces the set faster than typing does, and a search field implies a catalogue large enough to get lost in. The Phase 4 brief mentioned "searching" as a discovery capability; that mention does not override this approved architectural decision. If the catalogue grows substantially (Phase 2.5 §12 models 100 events), search is re-opened as a scalability question, not a preference.

**Golden Question filter (Charter §6):**
1. Help someone choose? → Category browsing (yes), Filters (yes), Search (no), Bookmarks (no)
2. Reduce uncertainty? → Cluster headers (narrow context), Status badges (availability)
3. Improve trust? → Transparent filtering (all events visible)
4. Reinforce identity? → Four worlds as discovery (Stage/Mind/Art/Maker)

---

### 10.B EVENT TILE ARCHITECTURE

What information is visible on each B-01 Event Tile:

| Element | Always visible | Purpose | Density role | Scanning speed |
|---|---|---|---|---|
| **Event Mark** (B-05, icon) | Yes | Visual identity - shape before text (Bible §6) | Low (icon, ~24px) | Instant recognition |
| **Event Name** (Display type) | Yes | Name is the primary scan target | Medium | 1-2 seconds |
| **Cluster Tag** (B-03) | Yes | Category context - which world | Low (color accent + text) | Instant |
| **Status Badge** (B-04) | Yes | Can I register right now? | Medium | Instant |
| **Brief Descriptor** (1-line body text) | Yes | One-sentence personality hook | Medium | 2-3 seconds |

**What is NOT visible on a tile:**

| Element | Where it lives | Why not on tile | Constitution |
|---|---|---|---|
| Full rules | P-04 Event Detail, Zone D | Density kill - rules are scan-heavy | Phase 0 §5.3 (progressive disclosure) |
| Team size details | P-04 Event Detail, Zone C | Tiles show scanning, not decisions | Phase 2 Part 10.1 |
| Materials list | P-04 Event Detail, Zone E | Too dense for scanning | Phase 2 Part 7 |
| Judging criteria | P-04 Event Detail, Zone E | Decision support, not scanning | Phase 2 Part 7 |
| Registration requirements | P-04 Event Detail, Zone G | Decision context, not scanning | Phase 2 Part 10.1 |

**Information density per tile:**
- **Scanning (what you read from a tile in 2 seconds):** Name, Mark, Cluster, Status
- **Reading (what you read on a tile to decide to tap):** Descriptor
- **Deciding happens at Event Detail, never at the tile**

**How status is communicated:**
- Open: B-04 shows "Open" → tap → P-04 → Register
- Closed: B-04 shows "Closed" → tap → P-04 (read-only) → no Register button
- Full: B-04 shows "Full" → tap → P-04 → honest message + alternatives
- Coming Soon (Announcement season): B-04 shows "Coming Soon" → tap → P-04 (preview)

**What clicking a tile does:**
- Always navigates to P-04 Event Detail for that event
- Status affects what is available ON the Event Detail, not whether the tile is clickable
- A closed/full tile still opens the Detail page (content is valuable even when registration is closed)

**Secondary actions on a tile:**
- **None.** Tiles have one action: tap → Detail. No secondary buttons, no swipe actions, no long-press menus. Mobile-first discipline (Phase 2 §13.1).

---

### 10.C FILTER BEHAVIOUR

#### What can be filtered?

| Filter | Exists | Values | Always visible? |
|---|---|---|---|
| **Cluster** | Yes | All / Stage / Mind / Art / Maker | Yes (I-04 Cluster Filter Toggle) |
| **On/Off-Stage** | **No** | - | No - cluster grouping subsumes this distinction. Four clusters are more useful than a binary on/off-stage toggle (Phase 0 §4.17). |
| **Registration Status** | **No** | - | No - status is visible per-tile via B-04 badges. Adding a "show only open" filter hides information (closed events are still discoverable and readable). Honest visibility (Phase 2 Part 14). |

**Justification of NO on/off-stage filter:**
- The four clusters (Stage/Mind/Art/Maker) are a more useful grouping than on/off-stage
- "On-stage" and "off-stage" are organizational categories, not user categories (Phase 0 §4.17)
- Students don't think "I want an off-stage event" - they think "I want to paint" or "I want to dance"

**Justification of NO status filter:**
- Status badges per tile (B-04) make filtering redundant
- Hiding closed/full events reduces honesty (Phase 2 Part 14: honest status)
- Coordinators need to see ALL events, including closed ones, for planning

#### How filtering works

- **Toggle chips** (I-04): Horizontal row of chips. "All" is default. Tapping a cluster chip activates it and deactivates others.
- **Instant filtering:** No loading state. Tiles that don't match become hidden (filtered in-place). Tiles that match remain visible.
- **Results count:** Announced after filter change (screen reader only: "Showing 4 Stage events"). Visible count is NOT displayed - tiles speak for themselves.
- **No search-style filter:** The filter is a toggle, not a text input. 5 options = tap, not type.

#### Does filtering affect the layout?

- **Filter in-place:** Cluster headers that have zero visible tiles are hidden (not shown as empty). Cluster headers with 1+ visible tiles remain. The grid structure adapts: 4 clusters with 0 tiles each → those cluster sections disappear, reducing scroll distance.
- **Empty cluster sections are collapsed**, not shown as "no events in this world" (that would be an empty state - M2 in Part 7).

#### What is the empty result state?

- **Cannot happen with current filters:** With 5 cluster chips and always-visible "All", you can always see all 16 events. The only way to get zero tiles is if ALL events in a selected cluster have been removed (admin action - extraordinary).
- **If it does happen:** "No events in this category" + "View all events" → returns to unfiltered. Never dead end.

#### How does the user clear filters?

- **Tap "All" chip:** Immediately shows all events
- **No "clear all" button:** Individual chips are mutually exclusive. Tapping one activates it; tapping "All" clears the filter. Two-state toggle, not multi-select.

#### Mobile vs Desktop filter behavior

| Surface | Filter display | Interaction | Position |
|---|---|---|---|
| **Mobile** | Tap-to-collapse toggle (default: collapsed, showing "Filter" label) | Tap to expand → tap a chip → auto-collapses and scrolls to matching cluster | Below header, above first cluster |
| **Tablet** | Inline compact chips | Tap chip → filter applies immediately | Inline, sticky |
| **Desktop** | Sticky horizontal bar | Tap chip → filter applies immediately | Sticky at top of content zone |

**Why mobile filter is collapsed:**
- Mobile viewport is precious (Phase 2 §13.2). A permanent filter bar wastes 48px for every scroll
- The default ("All") shows everything - the filter is an opt-in, not always-visible
- Mobile users scan all 16 events quickly enough that filtering is optional, not essential

---

### 10.D EVENT DETAIL DISCOVERY

#### How does a user discover RELATED events?

- **Does not exist - justified removal.**
- **Why not:** Phase 2 Part 10.1 asks the participant to become CERTAIN about ONE event. "Related events" or "similar events" dilute that certainty by reopening the choice question ("maybe this other one is better?"). Certainty is earned, not cross-sold.
- **Phase 2.5 §4.3: Removed section** - event lists on event detail pages were explicitly removed in Phase 2.5 structural architecture.

#### Can a user navigate between events from detail view?

- **Yes - via Back → Landscape.** P-04 Event Detail has a Back Affordance (A-06: "← Landscape") that returns to P-03, where all events are visible.
- **No direct event-to-event navigation.** The Landscape is the only hub for event comparison. Event Detail is a focused screen (one event at a time).

#### "Back to Landscape" vs "Continue Browsing"

- **Exists:** "← Landscape" (A-06 Back Affordance)
- **Does NOT exist:** "Continue Browsing" or "Next Event" - these imply a linear sequence through events. Events are not sequenced; they are parallel. The Landscape is the discovery surface; returning there is sufficient.
- **Why:** Events are not chapters in a book - they are stages in a festival (Phase 2 Part 3.3). Linear navigation would impose an artificial ordering (Phase 0 §4.17: clusters, not sequence).

---

### 10.E QUICK DISCOVERY (the 5-second scan)

What a new visitor sees in 5 seconds of landing on P-03 Landscape:

| Second | What they see | What they understand |
|---|---|---|
| 1 | H1: "Events" + Back affordance | "I'm where the events are" |
| 2 | "Stage" cluster header + first 2 event tiles | "There are categories. Stage has [Name], [Name]..." |
| 3 | Scanning more tiles | "Mind, Art, Maker - four worlds" |
| 4 | Status badges on tiles | "Some are open, some are closed" |
| 5 | Pattern recognition: 4 clusters × 4 events each | "I can find what I want. Let me pick." |

**Information hierarchy (what attracts attention first):**

1. **Cluster group headers (B-02)** - largest type in the zone. Eye lands here first. The four cluster names structure the world.
2. **Event names** (on tiles) - within each cluster, names are the highest-contrast text.
3. **Status badges** - color accent draws attention: green (Open) stands out against Paper more than neutral tones.
4. **Event marks** - low contrast, but shape contributes to scanning rhythm.

**What is NOT visible in 5 seconds:**
- Full rules (on Event Detail, not here)
- Event descriptions beyond the 1-line descriptor (on tiles)
- Materials lists (on Event Detail)
- Contact information (on Quiet Corners)

**Golden Question:** Does rapid scanning serve the user? Yes - students need "what can I do?" answered quickly (Phase 0 §2.1). The scan is fast, the decision is deliberate (Event Detail). Scanning speed ≠ decision speed.

---

## PART 11 - NAVIGATION BLUEPRINT

Navigation behaviour for the entire platform. Governing principle: "the path is never lost" (Phase 2.5 §PART 6 #3). One primary action per screen (Phase 0 §5.3). Navigation chrome is minimal and never competes with content (Phase 2 Part 8.2).

---

### 11.A PRIMARY NAVIGATION

#### What items are always visible?

| Item | Always in nav? | Location | Destination |
|---|---|---|---|
| **Logo Link** (A-02) | **Yes** - every public screen | Site Header, left | → P-01 Welcome Beat |
| **Events** | **Yes** | Site Header, right (desktop) / Drawer (mobile) | → P-03 Landscape |
| **Your Space / Login** | **Yes** | Site Header, right (desktop) / Drawer (mobile) | → P-12 Your Space (if logged in) / → P-22 Login (if not) |
| **Info** | **Yes** | Footer (always), Site Header desktop only (optional) | → P-19 Quiet Corners Hub |

**Count: 3-4 items.** Phase 2.5 mandates minimal navigation. Three core items (Home, Events, Your Space) plus one footer-only item (Info). Schedule is seasonal (not always visible).

#### Where does it live?

- **Desktop:** Horizontal row in Site Header (A-01): [Logo] · [Events] · [Your Space / Login] · [Schedule*]
- **Mobile:** Logo visible in header. Hamburger trigger (A-04) opens full-screen drawer (A-05) with all nav items as large touch targets (≥48px).
- **Rationale:** Header-only, never sidebar, never bottom bar, never sticky footer nav. Mobile-first discipline: navigation is an escape hatch, never competing with content (Phase 2 Part 8.2).

#### Active state indicator

- **Current page link has underline** (subtle, same color family, never different color). Visible on desktop and in mobile drawer.
- **Why underline:** Color-only active states are forbidden (Bible blacklist #51). Underline is a structural distinction, perceivable without color.
- **Why not highlight:** Highlight backgrounds compete with content zones. Underline is quiet (Phase 1 §2.3: logistics calm extends to navigation).

#### How does it change by season?

| Season | Nav items | Changes |
|---|---|---|
| **Announcement** | Home · Events · Login · Info | "Events" leads to read-only Landscape (P-03, Announcement state) |
| **Registration Open** | Home · Events · Login · Info | "Events" leads to normal Landscape. Registration flow accessible via Event Detail. |
| **Approach** | Home · Events · Schedule · Login · Info | **Schedule link appears** (G1-gated, visible in Approach+). "Events" still shows all events. |
| **Live** | Home · Events · Schedule · Login · Info | Schedule prominent. Events visible (read-only, registration closed). |
| **Post-Event** | Home · Events · Schedule · Login · Info | Events archive. Schedule archive. Winners/Gallery not in nav (accessed from Welcome Beat). |

**Why Schedule is seasonal (Part 21.1):** Schedule content (D2) does not exist until Approach season. Showing a link to TBD content destroys trust (Phase 2 Part 15.1). The link appears only when the content is actionable.

#### Mobile replacement for persistent nav

- **Full-screen drawer (A-05):** Tap hamburger → overlay with nav items listed as large touch targets. Background dims (Curtain gesture). Tapping a nav item closes drawer and navigates.
- **Not a bottom nav bar:** Bottom navigation bars compete with content (Phase 2 §13.2). Event tiles and primary CTAs need the full viewport.
- **Not floating action buttons:** FABs introduce chrome that competes with the primary action per screen (Phase 0 §5.3).

**Trace:** Phase 2.5 §PART 6 (Navigation Logic); Phase 2 Part 8.2 (attenuation: navigation is escape, not content); Phase 0 §5.3 (minimal).

---

### 11.B SECONDARY NAVIGATION

#### What items go in the footer?

| Item | Always in footer? | Destination | Purpose |
|---|---|---|---|
| **Info link** | **Yes** (every public page) | → P-19 Quiet Corners Hub | Access to About, FAQ, Contact, Privacy - "every doubt is one hop from an answer" (Phase 2.5 §5.2 #6) |
| **Privacy link** | **Yes** | → P-18 Privacy | Trust anchor - always reachable (Phase 0 Risk 14) |

**What is NOT in the footer:**
- **About, FAQ, Contact (individual):** These are inside P-19 Quiet Corners Hub. The footer links to the Hub, not to all 4 screens directly. Why: preventing footer overcrowding. A 4-line footer becomes a decision grid (Phase 2.5 §P-19).
- **Social media links:** Not built (D5 TBD, F-gated). If resolved, they live in P-19, not the footer.
- **Event categories, sitemap, or links to specific events:** Footer is not a navigation surface - it is a doubt-home.

**Footer composition:** Compact, single line on mobile: "EVOKE 2K26 · [Host TBD] · Info · Privacy"
**A-07 component spec:** `role="contentinfo"`. Keyboard accessible.

---

### 11.C CONTEXTUAL NAVIGATION

#### Per-screen navigation

| Screen | What you can navigate to from here | How |
|---|---|---|
| **P-01 Welcome Beat** | P-03 (Events), P-19 (Info), P-22 (Login) | Primary CTA + secondary links + header nav |
| **P-03 Landscape** | P-04 (each event, via tile tap), P-05 (Rules), P-01 (back), P-19 (footer) | Tile tap + Zone C actions + header |
| **P-04 Event Detail** | P-06 (Register), P-03 (back), P-05 (general rules), P-17 (Contact), P-19 (footer) | Primary CTA + Zone A back + Zone D links + footer |
| **P-05 Rules & Eligibility** | P-04 (any event, "view rules" per event), P-06 (Register via event), P-03 (back), P-19 (footer) | Zone D cross-references + back |
| **P-06 Registration Step 1** | P-07 (Continue), P-04 (back to event), P-19 (footer) | Continue + Back |
| **P-07 Registration Step 2** | P-08 (Continue), P-06 (Back), Pause → P-04 | Continue + Back + Pause & Save |
| **P-08 Registration Step 3** | P-09 (Continue), P-07 (Back) | Continue + Back |
| **P-09 Registration Step 4** | P-11 (Submit), P-07 (Edit), P-04 (Cancel) | Submit + Edit links + Cancel |
| **P-10 Payment (TBD)** | P-11 (Pay), P-09 (Back), P-17 (Contact) | Pay + Back + Contact |
| **P-11 Confirmation** | P-12 (Your Space), P-03 (Register more), P-01 (home) | Primary CTA + secondary |
| **P-12 Your Space** | P-03 (Register more), P-14 (Schedule), P-04 (event detail via record), P-01 (home) | D-05 action buttons + record taps |
| **P-14 Schedule** | P-04 (time slot tap), P-01 (back), P-19 (footer) | Time slot links + back + footer |
| **Quiet Corners** | Each other via Zone C related links; P-01 (back) | Content → related links → back |
| **P-25 404** | P-01 (Go back), P-03 (Events), P-17 (Contact) | Primary + secondary CTAs |

#### Breadcrumbs: Do they exist?

**NO breadcrumbs are used - justified removal.**

| Question | Answer | Constitution |
|---|---|---|
| **Do breadcrumbs serve the user?** | No - the platform is flat enough that "one hop to every answer" (Phase 2.5 §PART 6) does not require multi-level breadcrumbs. The deepest navigation is: Home → Events → Event Detail → Registration. That is 4 levels. The back affordance (A-06, "← Landscape") serves the retreat path more clearly than a breadcrumb chain. | Phase 2.5 §PART 6 |
| **What replaces breadcrumbs for orientation?** | **Back Affordance (A-06):** Every screen shows an explicit "← [Destination]" link. The destination name is the screen you came from (not a generic "Back"). This is clearer than breadcrumbs for a 4-level-deep platform. | Phase 2.5 §PART 6.2 #2 |
| **What about mobile?** | Breadcrumbs are especially wasteful on mobile (they take horizontal space). The single "←" link is compact and thumb-reachable. | Phase 2 §13.1 |

#### Decision-aware navigation

- **Registration flow (P-06 through P-09):** Primary nav is visible but de-emphasized. Step Progress Indicator (C-05) provides in-flow orientation. The user is in a focused channel - Landscape, Schedule, and Info links are not distracting because the Continue/Back CTA is dominant and the flow's step indicator is the primary orientation tool.
- **Event Detail → No "Explore More" links.** The Event Detail is a committed screen (Phase 2 Part 10.1: certainty). Secondary nav exists (Rules, Contact, General Rules) but does not encourage "leave and look elsewhere." The primary CTA is Register. Navigation chrome is minimal - the user is focused on deciding, not browsing.

**Trace:** Phase 2.5 §PART 6 (Navigation Logic); Phase 2 Part 8.2 (attention architecture); Charter §5 (progressive confidence - no distraction at decision points).

---

### 11.D BREADCRUMB PHILOSOPHY

**Breadcrumbs do not exist.** Structure:

| Element | What replaces breadcrumbs | Rationale |
|---|---|---|
| **Page title (Zone A header)** | Identifies where you are (e.g., "Rules & Eligibility", event name) | Screen reader + visual orientation |
| **Back Affordance (A-06)** | "← [Destination]" - explicit retreat path | One-hop-back, not a path trace |
| **Step Progress Indicator (C-05)** | "Step 2 of 4" - in-registration orientation | Flow position, not path history |
| **Site Header (A-01)** | Logo (home link) + nav items - always-visible anchors | Global orientation, always present |

**Why not breadcrumbs (Golden Question):**

- **Do breadcrumbs help someone choose an event?** No - they are orientation, not discovery.
- **Do breadcrumbs reduce uncertainty?** No - the back affordance tells you where you'll go. Breadcrumbs tell you where you came from - redundant for a 4-level platform.
- **Do breadcrumbs improve trust?** No - they are generic (Phase 1 blacklist: nothing exists because it looks standard).
- **Do breadcrumbs reinforce identity?** No - they use generic UI language.

**Phase 2.5 §PART 6 justification:** "One hop to every answer." The platform is intentionally flat. Every screen is at most 3 hops from the spine (Welcome → Landscape → Detail → Registration). Breadcrumbs solve a depth problem that this platform does not have.

---

### 11.E RECOVERY NAVIGATION

#### Back button behavior (every screen)

| Screen | Has visible back? | Where it goes | Edge case |
|---|---|---|---|
| **P-01 Welcome Beat** | **No** - you're at home | - | Browser back → previous page (whichever they came from) |
| **P-02 Announcement** | Yes | → P-01 | - |
| **P-03 Landscape** | Yes | → P-01 | Browser back → previous page |
| **P-04 Event Detail** | Yes | → P-03 | - |
| **P-05 Rules** | Yes | → P-03 | - |
| **P-06 through P-09 Registration** | Yes (per step) | → Previous step | Browser back may exit flow - state preserved via draft (see Part 9.F) |
| **P-11 Confirmation** | No - new journey begins | Goes to P-12 or P-03 via CTAs | Browser back may return to Review (P-09) - this is acceptable |
| **P-12 Your Space** | Yes (optional, context-dependent) | → P-03 (Events) | Deep link entry: back goes to entry point |
| **P-14 Schedule** | Yes | → P-12 (Your Space) or P-03 (from Events) | Context-aware: back goes to referring screen |
| **Quiet Corners** | Yes | → Referring page or P-01 | Always back-to-context |
| **P-25 404** | Yes | → P-01 | - |

**Browser back vs In-app back:**
- **Browser back:** Native behavior honored. Platform does not override it. Form state preservation (Part 9.F) ensures data survives back navigation.
- **In-app back (A-06):** Explicit, labeled ("← [Destination]"). Takes priority on screens beyond P-01. Not present on P-01 (no retreat from home).

#### "What changed since last visit?"

- Your Space (P-12) is the return engine. The Delta Indicator (D-03) answers "what changed" at the top of every visit.
- Outside Your Space: the platform does not announce "what changed." Changes are visible in the content itself (status badges refresh, new announcements appear in Your Space).

#### Deep entry re-orientation

| Entry type | Re-orientation strategy | How it works |
|---|---|---|
| **QR code (links to specific event)** | Compressed identity in header | Header shows: "EVOKE 2K26" + event name. Back goes to Landscape (not Welcome) - the user came for this event. |
| **WhatsApp link (deep link to specific page)** | Page title + back affordance re-anchor | Page title answers "where am I?" Back answers "how do I get out?" No extra chrome. |
| **Google search (event name)** | Same as deep entry | Event Detail page serves the search intent. Header nav available for orientation. |
| **Direct URL (manual entry)** | Same | Page loads normally. Navigation is standard. |
| **Shared link (social share)** | "Shared by [name]" context (if implemented in Phase 4) | Content is normal. Context note is optional, not required. |

**Why QR entry goes to Event Detail, not Welcome:**
- Phase 2 Part 12.1: every entry is recognized as a different emotional state. A QR scan means excitement + intent (the user saw the event name on a poster and scanned). Sending them to Welcome is a demotion. Phase 2 Part 12.1: "The event, immediately; identity in a line."

#### Lost in flow

- **Registration flow:** Step Progress Indicator (C-05) is always visible - answers "where am I?"
- **Event Detail:** Back Affordance (A-06) answers "where do I retreat?"
- **Every screen:** Logo link (A-02) answers "how do I go home?" - one tap, from anywhere.
- **No lost-in-flow state exists architecturally** because every screen has at minimum: a back affordance (if not home) + a home link + a footer with Info/Privacy.

---

### 11.F NAVIGATION BY SEASON

| Season | What appears in nav | What changes | What is hidden |
|---|---|---|---|
| **Announcement** | Home · Events · Login · Info | Events → read-only Landscape | Schedule (G1-gated) |
| **Registration Open** | Home · Events · Login · Info | Events → normal Landscape | Schedule (not yet published) |
| **Approach** | Home · Events · **Schedule** · Login · Info | **Schedule appears** (G1-gated). Events link may show "Registration closing" context. | - |
| **Live** | Home · Events · **Schedule** · Login · Info | Schedule is prominent. Events → read-only (registration closed). | - |
| **Post-Event** | Home · Events · **Schedule** · Login · Info | Events → archive. Schedule → archive. Winners/Gallery accessed from Welcome Beat, not nav. | - |

**Rationale for Schedule appearing in Approach:**
- Phase 2 Part 21 (Time Architecture): Schedule is a logistics tool. It becomes relevant when the festival approaches. Showing it in Announcement/Registration is noise (TBD content).
- The link is G1-gated: it appears only when D2 content exists (or the season mandates it).

**Rationale for Winners/Gallery NOT appearing in nav:**
- They are accessible from P-01 Welcome Beat during Post-Event (season state drives CTA)
- Adding them to persistent nav bloats the menu for a single season
- The Welcome Beat is visited first in Post-Event - it routes to Winners/Gallery

---

### 11.G ADMIN NAVIGATION

#### How admin navigation is separated from participant navigation

| Aspect | Participant | Admin |
|---|---|---|
| **Header** | A-01 Site Header (EVOKE identity) | Admin-only header (no EVOKE branding) |
| **URL structure** | `/`, `/events`, `/register`, etc. | `/admin/` - completely separate path |
| **Visibility** | All links public | Admin links never appear in participant navigation |
| **Auth gate** | Content before login (P-01, P-03, P-04) | **Strict gate:** admin URL requires authentication. No admin page is accessible without login (A-01) |
| **Footer** | A-07 (EVOKE identity, Info, Privacy) | **No footer** - admin screens have no participant footer |
| **Branding** | EVOKE identity language | Functional, no signature language (no Slips, no Stamps) |

**What is always visible in admin:**

| Element | Content | Purpose |
|---|---|---|
| **Admin header bar** | "Admin Panel" + dashboard link + organizer name + logout | Orientation + exit |
| **Admin nav links (inline, always visible on desktop)** | Dashboard · Content · Registrations · Announcements · Season · Events | Full admin access |
| **Back to Dashboard** | Present on all admin screens except Dashboard itself | Orienting retreat (like A-06 in public) |

**Can participants access admin?**
- **No - structural gate.** Admin URL path (`/admin/`) is firewalled. Attempting to access admin without credentials redirects to A-01 (admin login) with no participant-facing error or messaging.
- **No participant → admin link exists anywhere.** Not in footer, not in header, not in deep links. Admin is architecturally invisible to participants (Phase 2.5 §2.4: Admin invariant).

**Trace:** Phase 2.5 §2.4 (Admin invariant: invisible to participants); Phase 0 Q21, §7.4 (admin requirements).

---

## PART 12 - ERROR, EMPTY, LOADING STATES

Design for all failure, empty, and loading states. Every state must preserve confidence (Phase 2 Part 15: Trust Architecture). Rule: failure is where trust is made or broken (Phase 2 Part 14.4).

---

### 12.A ERROR STATES (5 types)

#### 1. 404 - The Lost Slip (P-25)

**Trigger:** Invalid URL reached (direct entry, dead link, bookmark from previous season)

| Aspect | Specification |
|---|---|
| **Visual** | The Lost Slip (F-05): torn empty slip - the only page allowed to break the visual grammar (Phase 1.5 §11.1.5). No Site Header, no Site Footer - the Lost Slip owns its space. |
| **Message** | "This slip got lost." (Ringmaster voice: memorable, not frightening - Phase 2 Part 14.3) |
| **Actions available** | → P-01 (Go back, primary); → P-03 (View Events, secondary); → P-17 (Contact, tertiary) |
| **Recovery path** | Named exception (Phase 1.5 §11.1.5): memorable redirect. Every action leads to real content. |
| **Tone** | Calm, slightly playful. The Lost Slip is a moment, not a wall. |
| **Screen reader** | "Page not found. Here are some places you can go." Navigation links announced. |
| **Constitution** | Phase 1.5 §11.1.5 (Named Exception: The Lost Slip); Phase 2 Part 14 (no dead ends) |

---

#### 2. 500 - Server Error (K2 in Part 7)

**Trigger:** Internal server error (HTTP 500) on any screen or during any action

| Aspect | Specification |
|---|---|
| **Visual** | Error banner overlay (F-02) - NOT a full-page redirect. The page behind is dimmed but not destroyed. World doesn't reset (Phase 2 Part 20.2: state preservation). |
| **Message** | "Something went wrong on our end. Try again." (Ringmaster voice: honest, not blaming - Phase 2 Part 14.3) |
| **Actions available** | → Try Again (primary) → Resume at current screen; → Contact (secondary) → P-17 |
| **Recovery path** | Retry → healthy state. Persistent failure → "come back later" message. Data behind overlay is preserved. |
| **Tone** | Calm, uninflammatory. The platform took the blame, not the user. |
| **Screen reader** | `role="alert"`: "Something went wrong. Try again." |
| **Constitution** | Phase 2 Part 14; Phase 1 §1.6 (Ringmaster voice) |

---

#### 3. Network Offline (K3 in Part 7)

**Trigger:** Device loses internet connectivity during any interaction

| Aspect | Specification |
|---|---|
| **Visual** | Error banner overlay (F-02): "No internet connection." |
| **Message** | "No internet connection. When you're back online, you can try again." (Calm, uninflammatory - Phase 2 Part 14) |
| **Actions available** | → Try Again (primary) - auto-retries when network restores; → Finish Later (secondary) - saves state, returns to previous safe screen |
| **Recovery path** | Network restores → overlay dismisses, session continues. Data preserved behind overlay. |
| **Tone** | Unbothered - temporary, not catastrophic (Phase 2 Part 14.1) |
| **Screen reader** | `role="alert"`: "No internet connection." |
| **Constitution** | Phase 2 Part 14; Phase 0 Risk 8 (network failures) |

---

#### 4. Service Unavailable (K4 in Part 7)

**Trigger:** Server returning HTTP 503 (deployment, capacity, or planned downtime)

| Aspect | Specification |
|---|---|
| **Visual** | Full-page message (not overlay - server is genuinely unavailable for content). Minimal layout. Paper surface (logistics calm). |
| **Message** | "We're doing some maintenance. We'll be back soon." + ETA if known (never fake ETA). |
| **Actions available** | → Home (if cached) → P-01; → Back later |
| **Recovery path** | Maintenance ends → resume normally. No user-visible countdown (blacklist #13: no fake urgency). |
| **Tone** | Calm waiting - planned, not broken. Honest about what's happening. |
| **Screen reader** | `role="alert"`: "Service temporarily unavailable." |
| **Constitution** | Phase 2 Part 14; Bible blacklist #13 |

---

#### 5. Maintenance Mode (K5 in Part 7)

**Trigger:** Planned maintenance window set by organizer via A-06 (admin)

| Aspect | Specification |
|---|---|
| **Visual** | Same as Service Unavailable (K4): full-page, minimal, calm. |
| **Message** | "We'll be back soon. Your registrations are safe." + countdown if ETA known. "Your registrations are safe" preserves trust (Phase 2 Part 15.1). |
| **Actions available** | → Home (cached) or back to previous page |
| **Recovery path** | Maintenance window ends → normal operation resumes |
| **Tone** | Reassuring - planned, announced, safe |
| **Screen reader** | `role="alert"`: "Maintenance in progress. We will be back shortly." |
| **Constitution** | Phase 2 Part 15.1 (trust preservation) |

---

### 12.B EMPTY STATES (6 types)

#### 1. No Events (M1 in Part 7)

**When this happens:** Event list is empty - should not occur in normal operation (admin has not populated events).

| Aspect | Specification |
|---|---|
| **What user sees** | "No events are available right now. Check back soon." + link to Welcome Beat (P-01) |
| **Where it appears** | P-03 Landscape (Zone B would be empty) |
| **Tone** | Honest, not alarming. This is a system state, not a user failure. |
| **Actions** | → P-01 (Welcome Beat) |
| **Intentional?** | **No** - this should not happen. But it is architecturally handled (Phase 2 Part 14: no dead ends). |

---

#### 2. No Matching Events - Filtered to Nothing (M2 in Part 7)

**When this happens:** User applies a filter and no events match (edge case: could happen if all events in a cluster are removed by admin).

| Aspect | Specification |
|---|---|
| **What user sees** | "No events match this filter." + "View all events" button |
| **Where it appears** | P-03 Landscape (Zone B, in the filtered cluster area) |
| **Tone** | Calm - it's an easy fix. |
| **Actions** | → Clear filter (returns to all 16 events) |
| **Intentional?** | **No** - with current filter design (5 mutually-exclusive clusters + always-visible "All"), this cannot happen. But architected defensively. |

---

#### 3. No Registrations - New User (M3 in Part 7; P-13)

**When this happens:** Logged-in user has no registrations (first login, or registration was cancelled).

| Aspect | Specification |
|---|---|
| **What user sees** | Waiting Slip (F-04): centered empty Slip frame. "This slip is waiting for your name" + "Explore Events" CTA (P-13) |
| **Where it appears** | P-13 (Your Space - Empty State) |
| **Tone** | Invitation, not rejection (Phase 1.5 §11.1.6: negative space is the message). The Slip waits. |
| **Actions** | → P-03 (Explore Events) |
| **Intentional?** | **Yes** - first login before registration is a designed state. The Waiting Slip is a Named Exception (Phase 1.5 §11.1.6). |

---

#### 4. No Announcements - Before Any Exist (M4 in Part 7)

**When this happens:** D1 = empty set (no announcements published yet).

| Aspect | Specification |
|---|---|
| **What user sees** | "No announcements yet" - inline within Your Space dashboard (P-12, Zone C). Not a full screen. Not an overlay. |
| **Where it appears** | P-12 Your Space, Zone C (Announcements section) |
| **Tone** | Quiet - the section exists but is empty. Not alarming. |
| **Actions** | - - The announcement section is not actionable. User continues with other dashboard content. |
| **Intentional?** | **Yes** - before first announcement, the section is honest. Admin publishes → D-04 cards appear. |

---

#### 5. No Schedule - Not Yet Published (M5 in Part 7)

**When this happens:** D2 = empty; G1 < Approach (schedule not yet relevant).

| Aspect | Specification |
|---|---|
| **What user sees** | "Schedule will be published during the Approach phase." (Honest posture, Phase 2.5 §11.1) |
| **Where it appears** | P-14 Schedule, Zone B |
| **Tone** | Informed - the schedule IS coming, just not now. No fake dates. |
| **Actions** | → P-03 (View Events) or P-12 (Your Space) |
| **Intentional?** | **Yes** - schedule is P-gated by season (Phase 2 Part 21.1). |

---

#### 6. No Gallery - Content Does Not Exist Yet (M6 in Part 7)

**When this happens:** D3 = F-gated; photography does not exist yet (post-event, but no photos uploaded).

| Aspect | Specification |
|---|---|
| **What user sees** | **Nothing** - the Gallery area (P-20) is not rendered at all. No "no gallery" message. No link to Gallery from nav. This is a "quiet gap" posture (Phase 2.5 §11.1). |
| **Where it appears** | Nowhere - F-gated areas are invisible, not empty |
| **Tone** | Absence of noise (phase 2.5 §11.1: no dead links) |
| **Actions** | - - Area not accessible until content exists |
| **Intentional?** | **Yes** - F-gate: the area does not exist until content exists (Phase 2.5 §8.1) |

---

### 12.C LOADING STATES (4 types)

#### 1. Initial Page Load (L1 in Part 7)

| Aspect | Specification |
|---|---|
| **How long before user notices** | **0.1 seconds** - skeleton appears instantly on page load, before any content exists. Skeleton is part of first paint. |
| **What is shown** | Skeleton Loading Frame (F-01): slip outlines matching expected layout zones. Amber pulse (150-250ms cycle). Zone-by-zone skeleton (P-04: personality outline, facts grid outline, rules list outline). |
| **Is it calm?** | **Yes** - skeleton is structural (brand-holding). Not a spinner. The brand is present during the wait (Phase 1.5 §11.2). |
| **Maximum wait before timeout** | **5 seconds** - after 5s, transition to error state (K2: "Something went wrong") with retry. **3-second target** for mid-range mobile (Phase 0 metric: ≤3s). |
| **Screen reader** | `aria-live="polite"`: "Loading [page name]." Announced once, not repeatedly. |
| **Constitution** | Phase 1 §11 (skeleton frames, no spinners beyond first load); Phase 1.5 §11.2 (slip universality); Phase 0 §8 (Lighthouse ≥90) |

---

#### 2. Section Reveal (L2 in Part 7)

| Aspect | Specification |
|---|---|
| **How long before user notices** | **0ms** - triggered by scroll. Section enters viewport → content loads → Slip rises (Lift gesture). User expects scroll-driven loading. |
| **What is shown** | Skeleton within the zone only. Rest of page fully interactive. Amber pulse in the loading zone. |
| **Is it calm?** | **Yes** - localized. The rest of the page remains interactive. |
| **Maximum wait before timeout** | **5 seconds** - content loads or honest placeholder appears. |
| **Screen reader** | No announcement (scroll-driven interaction). |
| **Constitution** | Phase 1.5 §3.4 (Lift gesture); Phase 2 Part 7 (cognitive load: section-by-section delivery) |

---

#### 3. Form Submission - In-Flight (L3 in Part 7; Part 9 Step 6)

| Aspect | Specification |
|---|---|
| **How long before user notices** | **0ms** - CTA changes to "Submitting…" immediately on tap |
| **What is shown** | CTA text: "Submitting…" with skeleton in the button area. Fields locked (no edits). Step progress indicator dims. |
| **Is it calm?** | **Yes** - "almost there" messaging. User's effort is acknowledged. |
| **Maximum wait before timeout** | **10 seconds** - after 10s, transition to error state with "Try again." (Longer than page load because form submission depends on network round-trip.) |
| **Screen reader** | `aria-live="polite"`: "Submitting registration." |
| **Constitution** | Phase 2 Part 20 (recovery: state preserved); Phase 2 Part 15.4 (trust during submission) |

---

#### 4. Per-Action Loading (L4 in Part 7)

| Aspect | Specification |
|---|---|
| **How long before user notices** | **0ms** - action button changes state immediately |
| **What is shown** | Localized skeleton within the action's component. E.g., "Add Member" button shows skeleton for 200-500ms while the new team member block renders. |
| **Is it calm?** | **Yes** - sub-second operation. Skeleton exists for visual continuity, not because the wait is long. |
| **Maximum wait before timeout** | **3 seconds** - per-action operations should be fast. Timeout → inline error: "Couldn't add member. Try again." |
| **Screen reader** | No announcement for sub-second operations. `aria-live="polite"` if >1s. |
| **Constitution** | Phase 1 §11 (loading is branded, minimal overhead for fast operations) |

---

### 12.D WAITING STATES (3 types)

#### 1. Registration Pending

**When this exists:** Between submission (P-09/P-10) and confirmation (P-11) - the server has received data but not yet confirmed. RARE - the normal flow is: submit → redirect to Confirmation.

| Aspect | Specification |
|---|---|
| **How it manifests** | If the redirect fails or the user loses connection mid-confirmation, your Space (P-12) may show a "Pending" registration card (D-02 variant). Message: "Your registration is being processed. We'll confirm shortly." |
| **Duration** | Transient - should resolve within seconds. If >5 minutes, user sees: "We're verifying your registration. Check back or contact us if this persists." |
| **Actions** | → Contact organizer; → Wait (passive - no retry mechanism for pending, it auto-resolves) |
| **Recovery** | Status updates → Confirmation received. User notified via announcement (D-01 Delta). |
| **Tone** | Secure, not anxious (Phase 2 Part 14.2) |

---

#### 2. Payment Pending (TBD Placeholder)

**When this exists:** TBD - only if payment flow is implemented (Charter §7).

| Aspect | Specification |
|---|---|
| **How it manifests** | User's registration status = "Payment Pending" in Your Space (D-02). Visible, not hidden. Message: "Your registration is pending payment completion." + timeline if known. |
| **Actions** | → Complete Payment (if the pending payment can be retried); → Contact (if payment failed and retry is not possible) |
| **Trust messaging** | "No charge has been applied" OR "Payment is processing - you will be charged [amount] once confirmed." |
| **Duration** | TBD - organizer-configurable window. Expired pending → registration cancelled (honest message, not silent). |
| **Tone** | Secure, unhurried (Phase 2 Part 15.4: money trust) |
| **Constitution** | Charter §7 (payment TBD); Phase 2 Part 15.4 (money trust) |

---

#### 3. Season Transition (Announcement → Registration Open)

**When this exists:** The window between the announcement being published and registration opening.

| Aspect | Specification |
|---|---|
| **How it manifests** | Welcome Beat (P-01) shows: "Registration opens soon." Landscape (P-03) shows events with "Coming Soon" status badges. No Register button. |
| **What the user can do** | Explore events (read-only). Build anticipation. Return for registration. |
| **Tone** | Anticipatory, not urgent. No countdown timers (blacklist #13). No "don't miss out" pressure. |
| **Duration** | Depends on organizer timeline. Handled by G1 season state (A-06). |
| **Recovery** | Season flip → Registration CTA activates automatically. No user action needed. |
| **Constitution** | Phase 2 Part 21 (Time Architecture); Phase 2.5 §8.1 (season timing); Chapter 2 (Bible §13: no urgency without real deadline) |

---

## PART 13 - INTERACTION BLUEPRINT

Interaction behaviour for the entire platform - what happens when the user does an action. This section defines INTERACTION LOGIC, not animation (which is Phase 4). Every interaction pattern answers: what user problem does this solve? If nothing, it is removed.

---

### 13.A PRIMARY INTERACTIONS

| Interaction | What happens | Context | Constitution |
|---|---|---|---|
| **Tap/Click** | Primary: navigates to destination (link) or performs action (button). Context determines behavior - tap on tile = Detail, tap on CTA = forward step. | Every interactive element | Phase 0 §5.3 (one action per screen) |
| **Scroll** | **Section reveals** (Lift gesture on content zones) on desktop. **Sticky CTA appearance** on P-04 mobile (below fold). **No scrolljacking** (Phase 1 blacklist #41) - natural scroll only. | P-04 (long scroll), P-03 (tile scrolling), all scrollable pages | Phase 1 blacklist #41; Phase 1.5 §3.4 (Lift gesture) |
| **Keyboard Enter** | Activates primary action in current context: submits form (if on CTA), activates button, follows link (if on link). In form fields: moves to next field (if valid), or shows error on current field (if invalid). | Everywhere keyboard is active | Phase 0 §12.7 (WCAG AA); Bible §11 |
| **Keyboard Escape** | Closes: mobile nav drawer (A-05), expanded FAQ accordion items, dropdown menus. Does NOT close full-page modals (we don't use them - blacklist #48). | Wherever overlays or expanded content exist | WCAG 2.1; Phase 1 blacklist #48 (no arrival modals) |

---

### 13.B EVENT TILE INTERACTIONS

| Interaction | What happens | Platform | Constitution |
|---|---|---|---|
| **Tap event tile** | Navigates to P-04 Event Detail for that event | All platforms | Phase 2 Part 3.3 (guided choice) |
| **Focus event tile (keyboard)** | Amber ring appears. Press Enter/Space → navigates to Detail | Keyboard / Screen reader | Phase 0 §12.7; WCAG 2.1 |
| **Hover event tile (desktop only)** | Acknowledgement only: slight lift + outline (Bible §11). NO content change. NO extra info revealed. | Desktop only | Phase 1 §11 (hover = acknowledgement only); Bible blacklist #42 (no hover-only info) |
| **Tap tile when event is Closed** | Navigates to P-04 Event Detail (read-only). Register button disabled on Detail. Honest status shown. | All | Phase 2 Part 14 (honest closure) |
| **Tap tile when event is Full** | Navigates to P-04 Event Detail. Honest full message + "View other events" on Detail. | All | Phase 2 Part 14.2 (no dead ends) |
| **Touch target size** | Tile minimum height: ≥44px (Bible blacklist #43). Tile height is typically 80-100px (comfortable tap zone). | Mobile primary | Bible blacklist #43; WCAG 2.5.5 |
| **Long press (mobile)** | **Nothing.** No context menu, no quick-action shortcut. One action per tile. | All platforms | Phase 0 §5.3 (one action per screen); Bible §11 |

**Why no hover-dependent info (Bible blacklist #42):**
- 65%+ traffic is mobile - hover doesn't exist (Phase 0 §11.4)
- Hover-revealed info fails the equity test: mobile users see less information
- All information must be visible at rest

---

### 13.C FORM INTERACTIONS

| Interaction | What happens | Details | Constitution |
|---|---|---|---|
| **Focus (input receives focus)** | Single warm amber focus ring appears (Bible §11). Label remains above field (never hidden). Virtual keyboard appears on mobile (correct type for input: email → email keyboard, phone → number pad). | Focus ring is part of the brand, not an apology (Bible §11) | Phase 0 §12.7; Bible §11 |
| **Blur (input loses focus)** | Required field validated. If invalid: inline error (C-06) appears below field. If valid: no change. Form does NOT auto-advance. | On blur for required fields only. Optional fields validated on submit. | Phase 2 Part 10.3 (inline validation) |
| **Typing** | No debounce (immediate rendering). No auto-save per keystroke (save is per-field-change, see Part 9.F). Progressive disclosure: conditional fields appear based on input value (e.g., phone field appears if email left blank). | - | Phase 2 Part 10.3 |
| **Enter key (within input)** | If field has no validation errors: focus moves to next field. If last field in step: activates "Continue" (submits step). If field has validation errors: error appears, focus stays. | Standard form convention. Enter-as-submit only on last field or CTA. | WCAG 4.1.2 |
| **Enter key (on CTA)** | Submits current step / performs action. | - | WCAG 4.1.2 |
| **Tab** | Moves focus following visual reading order. DOM order = visual order = logical order (absolute rule - Part 8). | - | WCAG 1.3.2 |
| **Select dropdown (school/class)** | Opens native dropdown. Arrow keys navigate options. Enter selects. Space opens. Tab closes dropdown and moves to next field. | - | WCAG 4.1.2 |
| **Agreement checkbox (P-08)** | **Space** toggles checkbox. If checked: "I understand. Continue" CTA becomes enabled (amber-on-ink). If unchecked: CTA remains disabled (with text: "Agree to continue"). | CTA text IS the agreement (Phase 2 Part 10.2) | WCAG 4.1.2; Phase 2 Part 15.4 (no pre-checked boxes) |

---

### 13.D CONFIRMATION PATTERNS

| Action | Requires confirmation? | How | Where | Constitution |
|---|---|---|---|---|
| **Submission (Register)** | **Yes** - Step 4 (P-09 Review & Confirm) IS the confirmation pattern. User reviews all data + clicks "Confirm Registration." | Review → Confirm (two actions: read all, click confirm) | P-09 → P-11 | WCAG 3.3.4 (Error Prevention); Phase 2 Part 10.2 |
| **Submission (Payment)** | **Yes** - CTA: "Pay and Complete" is explicit. No "Pay Now" without review. | Review → Pay (payment details always visible before action) | P-10 (if exists) | Phase 2 Part 15.4 (money trust) |
| **Leaving mid-flow** | **Yes** - "Save progress?" prompt IF user has entered data and attempts to navigate away (browser back, URL change, or explicit navigation to non-flow page). | "You're mid-registration. Save progress?" → Saves draft → "Progress saved" toast → Returns to event detail. | P-06 through P-09 | Phase 2 Part 20.2 (state preservation); Part 13.1 (resumable) |
| **Cancel registration** | **Yes** - "Cancel and Return to Event" is visible on Review step (P-09). Tapping shows: "Canceling won't affect anything. Return to the event?" → Returns to P-04. | Honest, non-punishing. | P-09 | Phase 2 Part 14 (non-punishing retreat) |
| **Delete team member** | **Yes** - "Remove Member [N]" asks: "Remove this member?" on confirmation. | Inline confirmation, not a modal. | P-07 Step 2 | WCAG 3.3.4 (Error Prevention) |
| **Season change (admin)** | **Yes** - "Changing to [Season] will affect all users. What changes:" + impact summary. | Impact preview before confirmation. | A-06 | Phase 2.5 §PART 6 |

**Why confirmation before leaving mid-flow (Part 13.1):**
- Mobile context switching is constant (WhatsApp → platform → back, Phase 2 Part 13.1)
- Accidental navigation away destroys effort
- Draft preservation (Part 9.F) handles this, but the save prompt gives the user **agency** - they choose to save or leave (Phase 2 Part 20: confidence preservation)

---

### 13.E SECONDARY INTERACTIONS

| Interaction | What happens | Screen | Constitution |
|---|---|---|---|
| **Expand FAQ (accordion)** | Tap question → answer expands with Lift gesture. Expanded answer fully visible. Tap question again → answer collapses. On mobile: only one item open at a time (closed accordion). On desktop: multiple items may be open. | P-04 (Zone F), P-16 | Phase 0 §5.3 (progressive disclosure); Phase 1.5 §3.4 |
| **Filter chips (add)** | Tap cluster chip → tiles filter immediately. Active chip highlighted. Results count announced to screen reader. | P-03 Landscape | Phase 0 §5.3 |
| **Filter chips (remove)** | Tap "All" chip → all tiles visible. Other chips deactivated. | P-03 Landscape | - |
| **Step navigation (back)** | Tap "Back" → previous step. All data preserved. Progress indicator updates. | P-06 through P-09 | Phase 2 Part 10.3 |
| **Step navigation (skip forward)** | **Not available.** Steps cannot be skipped. Every step must be completed in order. Step indicators (C-05) are informational, not clickable jumps. | P-06 through P-09 | Phase 2 Part 10.3 (certainty is built step by step) |
| **"Save and Return Later"** | Saves draft + toast confirmation + returns to P-04 Event Detail. | P-07 Step 2 | Phase 2 Part 20.2; Part 9.F |
| **"Add Member" (team events)** | Renders new Team Member Block with empty fields. Focus moves to first field of new block. | P-07 Step 2 | Phase 0 §3.1 |
| **"Remove Member"** | Inline confirmation → removes block. Focus moves to previous member's last field (or last remaining member). Min count enforced. | P-07 Step 2 | - |

---

### 13.F GESTURE INTERACTIONS (Mobile)

| Gesture | Exists? | If yes: what? | If no: why? | Constitution |
|---|---|---|---|---|
| **Swipe (horizontal)** | **No** | - | Swipe is ambiguous: users associate it with carousels (banned, Phase 1 #45) and infinite-scroll feeds. No carousel, no feed exists on this platform. Swipe gestures serve discovery patterns this platform does not have. | Blacklist #45 (carousels); Phase 2 Part 3.3 (guided choice, not swipe-through) |
| **Swipe (vertical)** | **No** - vertical scroll is natural scroll, not a gesture. | - | Vertical scroll is the native scroll. It is not treated as a distinct "gesture" and does not trigger actions. | Phase 1 blacklist #41 (no scrolljacking) |
| **Pull to refresh** | **No** | - | Pull-to-refresh is for infinite-content feeds and real-time updates. This platform has static content (events, rules) that doesn't change per-pull. Announcements update per-visit, not per-pull. | Phase 0 §6.4 (content states, not real-time feed) |
| **Context menus (long press)** | **No** | - | Context menus imply multiple actions per item. Tiles have one action (tap → Detail). Forms have explicit buttons. No element on this platform offers more than one primary action. | Phase 0 §5.3 (one action per screen) |
| **Two-finger pinch** | **No** | - | No pinch-to-zoom, no pinch-to-scroll. Everything is touchable at single-finger scale. Touch targets ≥44px. | WCAG 2.5.3; Phase 2 §13.3 (one hand) |
| **Edge swipe (back navigation)** | **System default** - not controlled by platform | Browser back | Mobile OS gesture (iOS swipe-from-edge, Android nav bar). Platform honors the native gesture - does not override it. Form state is preserved via draft (Part 9.F). | - |

**Why no custom gestures:**
- The platform must be immediately usable (Phase 2 Part 8.2: no learning curve for navigation)
- Custom gestures conflict with OS-native expectations
- Touch targets and tap-based interactions serve all audiences equally (Phase 0 §12.7 accessibility)
- Gestures that hide functionality fail the equity test: a returning user doesn't remember what to swipe

---

### 13.G KEYBOARD INTERACTION MAP

Per component, complete keyboard interaction specification:

| Component | Tab | Enter | Space | Escape | Arrow Up/Down | Arrow Left/Right | Home | End |
|---|---|---|---|---|---|---|---|---|
| **A-02 Logo Link** | Receives focus | Follows link (→ P-01) | No effect | No effect | No effect | No effect | No effect | No effect |
| **A-03 Nav Items** | Focuses next link | Follows link | No effect | No effect | No effect | No effect | No effect | No effect |
| **A-04 Mobile Nav Trigger** | Receives focus | Opens drawer (A-05) | Opens drawer | No effect | No effect | No effect | No effect | No effect |
| **A-05 Mobile Nav Drawer** | Focus trap: moves through nav items | Follows link, closes drawer | Follows link, closes drawer | Closes drawer | No effect | No effect | First item | Last item |
| **B-01 Event Tile** | Receives focus | Navigates to Detail | Navigates to Detail | No effect | No effect | No effect | No effect | No effect |
| **B-02 Cluster Header** | Landmark (not focusable) | - | - | - | - | - | - | - |
| **C-01 Text Input** | Receives focus | If valid → next field; if last field → submit step | No effect | No effect | No effect | No effect | No effect | No effect |
| **C-02 Select Dropdown** | Receives focus | Opens dropdown | Opens dropdown | Closes dropdown | Navigate options | Navigate options | First option | Last option |
| **C-03 Team Member Block** | Focus moves to first field | Depends on field | Depends on field | No effect | No effect | No effect | No effect | No effect |
| **C-04 Agreement Checkbox** | Receives focus | Toggles | Toggles | No effect | No effect | No effect | No effect | No effect |
| **C-10 Primary CTA** | Receives focus | Activates action | Activates action | No effect | No effect | No effect | No effect | No effect |
| **C-11 Secondary CTA** | Receives focus | Activates action | Activates action | No effect | No effect | No effect | No effect | No effect |
| **C-12 FAQ Accordion** | Focuses question button | Expands/collapses | Expands/collapses | No effect | Move between questions | Move between questions | First question | Last question |
| **I-04 Filter Chips** | Moves between chips | Activates filter | Activates filter | No effect | No effect | Move between chips | First chip | Last chip |
| **I-06 Sticky Decision Bar** | Focuses Register button | Activates Register | Activates Register | No effect | No effect | No effect | No effect | No effect |
| **E-03 Schedule Filter** | Moves between chips | Activates filter | Activates filter | No effect | No effect | Move between chips | First chip | Last chip |
| **E-02 Time Slot Card** | Receives focus | Navigates to Event Detail | Navigates to Detail | No effect | Move between slots | Move between days | First slot | Last slot |

**Keyboard rules:**
- **Tab order always follows visual reading order** (Phase 0 §12.7; Part 8 absolute rule)
- **Escape closes overlays only** (drawer, dropdown, expanded content). On a static page, Escape has no effect.
- **Home/End jump to first/last** only within interactive component groups (tile sets, filter chips, FAQ questions, time slots). Not on full-page navigation.
- **Arrow keys supplement, not replace, Tab.** Tab moves between logical groups. Arrows move within groups.

---

### 13.H ERROR RECOVERY INTERACTIONS

| Error type | What happens | How user recovers | Data preservation | Constitution |
|---|---|---|---|---|
| **Form validation error** | Inline error (C-06) appears below field. Error count announced. Focus moves to first error. | Fix field → error disappears. Retap "Continue" → re-validated. | All fields preserved | Phase 2 Part 14.3; WCAG 3.3.1 |
| **Network failure during action** | Error overlay (F-02) appears. Page behind preserved. | "Try Again" → retries action. "Finish Later" → saves state, leaves flow. | All data preserved behind overlay | Phase 2 Part 20.2 |
| **Submission failure** | Error overlay. Step position retained. | "Try Again" → resubmits. "Contact" → P-17. | All data preserved. User at Review step (P-09). | Phase 2 Part 20.2 |
| **Payment failure (TBD)** | Honest failure: "That didn't go through - no charge was made." | "Try Again" → retry payment. "Contact" → P-17. Data visible in Your Space as "Pending." | All data preserved. Registration in "Pending" state. | Phase 2 Part 15.4 (money trust) |
| **Session expired mid-flow** | "Session expired" overlay. "Resume" button. | "Resume" → restores session → returns to same step with data intact. | All data preserved | Phase 2 Part 14.5 |
| **Registration closed mid-flow** | Honest close: "Registration has just closed." | "View Events" → P-03 (read-only). Data preserved but cannot submit. | All data preserved. Cannot re-enter flow until season changes. | Phase 2 Part 14 |

**Recovery rules:**
1. **One action to recover** - every error offers a single clear retry or exit
2. **Nothing is reset** - state is always preserved (Phase 2 Part 20.2)
3. **Voice is calm** - Ringmaster's honest voice (Phase 2 Part 14.3)
4. **No hidden state** - the user always sees what happened and what they can do next

---

### 13.I BACK NAVIGATION BEHAVIOUR

#### Pressing browser back

| Context | What happens | Data preserved? | Reason |
|---|---|---|---|
| **On Welcome Beat (P-01)** | Browser back → previous page (whichever they came from: search results, social, etc.) | - | Home has no platform-level back |
| **On Landscape (P-03)** | Browser back → Welcome Beat (if arrived from Welcome) or → entry source | - | Standard navigation |
| **On Event Detail (P-04)** | Browser back → Landscape (if arrived from Landscape) or → entry source | - | Standard navigation |
| **On Registration (P-06-P-09)** | Browser back → Previous step (P-06 ← P-05, etc.) - **IF within the flow**. → Event Detail (if browser back exits the flow entirely). | **Yes** - all form data preserved via draft (Part 9.F). Draft survives browser navigation. | Phase 2 Part 20.2 (state preservation); Part 13.1 (resumable) |
| **On Confirmation (P-11)** | Browser back may return to Review (P-09) - acceptable behavior. Data is confirmed, so no risk. | - | Confirmation is final |
| **On Your Space (P-12)** | Browser back → whatever led you here (Registration, Event Detail, direct URL) | - | Standard navigation |
| **Deep link entry (first back goes where)** | First back → entry source (the page they shared/linked from). If deep-linked to Event Detail: back goes to Landscape (A-06). If deep-linked to Registration: back goes to Event Detail. | **Yes** - draft persists | Part 12.1 (entry states) |

#### In-app back button (A-06) vs Browser back

| | In-app back (A-06) | Browser back |
|---|---|---|
| **Destination** | Explicit: "← [Named Destination]" | Implicit: browser history stack |
| **Control** | Platform controls what it points to | Browser controls history |
| **Label** | Named destination (e.g., "← Landscape") | Browser shows no label |
| **On Registration steps** | Goes to previous step | May exit flow entirely |
| **Data preservation** | Always preserves form data | Depends on browser behavior - platform uses draft as fallback |

**Why A-06 exists when browser back works:**
- **Named destination:** "← Landscape" tells the user exactly where they'll go. Browser back is implicit and unreliable (Phase 2 Part 8.2: orientation).
- **SPA pattern:** In single-page apps, browser back may not behave as users expect. In-app back provides a reliable retreat (Phase 2 §13.1: consistency).
- **Context-aware:** A-06 destination adapts to context (e.g., back from Event Detail goes to Landscape; back from Quiet Corner goes to referring page).

---

## PART 14 — DEVELOPER CONTRACT

Everything a developer must know **before touching code**. This part translates the interface architecture into implementation mandates. Every decision here traces to a constitution. No code appears here — only patterns, contracts, and boundaries.

### 14.A NAMING PHILOSOPHY

Consistent naming prevents ambiguity across the team. Every screen, component, content object, state, and system value has a canonical name derived from its spec code.

#### Screen names

**Pattern:** `P-NN: [Name]` (primary) or `A-NN: [Name]` (admin) or `S-NN: [Name]` (system).

The prefix determines the category. The number is globally unique across the platform.

| Prefix range | Category | Example |
|---|---|---|
| **P-01 to P-27** | Participant-facing screens. Two of these — **P-23 (Network Error)** and **P-26 (Loading)** — are *categorised* as System overlays in Part 1 but keep their P numbers. | P-04: Event Detail |
| **A-01 to A-07** | Admin screens (organizer-facing) | A-06: Admin — Season & State Control |

Screen names in code, documentation, and comments always use the P-NN/A-NN code. Informal references ("event page", "dashboard") must always be traceable to the code. New screens follow the next available number in sequence.

**There is no `S-` prefix.** An earlier draft of this section proposed `S-01 to S-04` for system screens; that scheme was never applied in Part 1 and would collide with the existing P-numbers for the same screens. System status is a **category**, not a prefix — P-23 and P-26 are System screens with P numbers. Any code, comment, or document referring to `S-01`–`S-04` is referring to a naming scheme that does not exist.

#### Component names

**Pattern:** `[CATEGORY]-[NN]: [Name]`

The category letter determines the domain. The number is unique within the category.

| Category | Domain | Range | Example |
|---|---|---|---|
| **A-** | Navigation & Wayfinding | 01–07 | A-03: Nav Items |
| **B-** | Event Display & Discovery | 01–06 | B-01: Event Tile |
| **C-** | Forms & Input | 01–12 | C-01: Text Input |
| **D-** | Dashboard (Your Space) | 01–05 | D-02: Registration Record Card |
| **E-** | Schedule | 01–03 | E-02: Schedule Time Slot Card |
| **F-** | Feedback & System | 01–05 | F-02: Error Banner |
| **G-** | Quiet Corners | 01–03 | G-01: Hub Grid |
| **H-** | Admin | 01–05 | H-01: Admin Table |
| **I-** | System & Support | 01–08 | I-08: Focus Ring |

In code, components may use kebab-case filenames but the spec reference is always `CATEGORY-NN`.

#### Content object names

Content objects follow the Phase 2.5 inventory codes — never renamed, never renumbered:

| Code range | Domain | Example |
|---|---|---|
| **A1–A8** | Identity & orientation | A1: Festival description |
| **B1–B12** | Events domain | B7: Rules (faithful wording) |
| **C1–C7** | Participation & commitment | C4: Data fields (TBD) |
| **D1–D6** | Communication | D1: Announcements |
| **E1–E3** | Support | E2: Contact route |
| **F1–F4** | Administrative | F1: Content management |
| **G1–G3** | System objects | G1: Season state |

In code, spec comments must include the inventory code: `// B7 — Rules`.

#### State name patterns

**Pattern:** `[entity].[state]` — dot notation for machine readability.

| Entity type | Pattern | Examples |
|---|---|---|
| **Registration flow** | `registration.step-NN` | `registration.step-active`, `registration.submitting`, `registration.submitted`, `registration.error` |
| **Registration status** | `registration.status` | `registration.open`, `registration.closed`, `registration.full`, `registration.pending` |
| **Season** | `season.[name]` | `season.announcement`, `season.registration-open`, `season.approach`, `season.live`, `season.post` |

State names are lowercase, hyphen-separated, never camelCase.

#### Season names

Five seasons, singular and canonical:

| Display name | Code name | Single-letter | Description |
|---|---|---|---|
| **Announcement** | `announcement` | A | Pre-registration. Platform exists, details coming. |
| **Registration Open** | `registration-open` | R | Registration is active. CTAs enabled. |
| **Approach** | `approach` | P | Registration closing or closed. Schedule visible. |
| **Live** | `live` | L | Festival is happening. Schedule prominent. |
| **Post** | `post` | E | Festival complete. Archive mode. |

Season is stored as a single global value (G1). All screens derive their posture from G1. No screen hardcodes a season check — every screen reads G1. Season transitions occur via A-06 (admin toggle).

#### Cluster names

Four clusters, canonical and fixed-order:

| Cluster | Canonical name | Canonical order |
|---|---|---|
| **Stage** | Stage | 1 |
| **Mind** | Mind | 2 |
| **Art** | Art | 3 |
| **Maker** | Maker | 4 |

Never abbreviated. Never reordered in display. Code values match display names exactly. New clusters (future editions, 20+ events) follow the same pattern.

#### URL pattern convention

URLs follow RESTful, human-readable patterns — never cryptic IDs:

| Route pattern | Example | Screen |
|---|---|---|
| `/` | Homepage | P-01 |
| `/events` | `/events` | P-03 |
| `/events/[slug]` | `/events/dumb-charades` | P-04 |
| `/rules` | `/rules` | P-05 |
| `/register/[slug]` | `/register/dumb-charades` | P-06 (Registration flow) |
| `/register/[slug]/confirm` | `/register/dumb-charades/confirm` | P-09 |
| `/confirmation` | `/confirmation` | P-11 |
| `/dashboard` | `/dashboard` | P-12 |
| `/schedule` | `/schedule` | P-14 |
| `/about` | `/about` | P-15 |
| `/faq` | `/faq` | P-16 |
| `/contact` | `/contact` | P-17 |
| `/privacy` | `/privacy` | P-18 |
| `/admin/*` | `/admin/dashboard` | A-01+ (admin area, isolated) |

Event slugs are lowercase, hyphen-separated, derived from event names: `dumb-charades`, `g-k-quiz`, `fashion-show`, `group-song`, `solo-song`, `group-dance`, `solo-dance`, `instrumental-music`, `face-painting`, `cooking-without-fire`, `vegetable-carving`, `pot-painting`, `art-and-craft`, `collage-competition`, `pencil-sketch`, `best-out-of-waste`.

### 14.B COMPONENT OWNERSHIP

Each component is responsible for specific behaviours. Ambiguity in ownership causes inconsistent implementation.

| Responsibility | Owner | Why |
|---|---|---|
| **Navigation rendering** | A-01 (Site Header) | A-01 composites A-02, A-03, A-04. A-01 is the sole renderer. |
| **Navigation links (which exist)** | A-01 reads G1 | Links appear/disappear based on season. |
| **Season state (source of truth)** | G1 (system object, set by A-06) | Admin sets season. Every screen reads G1. |
| **Season state display** | Every public screen | Each screen adapts its content based on G1. |
| **Form validation** | C-06 (Inline Validation) on behalf of the form container | Validation renders below each field. The screen orchestrates; C-06 owns display. |
| **Form submission** | The screen component owning the form (e.g., P-09) | The screen coordinates: gather data, validate, submit, show result. |
| **Registration status per event (B11)** | G1 + event data (derived) | Status is computed from registration count vs quota. |
| **Accessibility** | **Every component, individually** | Each component must work with assistive technology in isolation. No delegation. |
| **Loading display** | F-01 (Skeleton Loading) | F-01 renders the skeleton; the screen signals loading state. |
| **Error display** | F-02 (Error Banner) | F-02 renders overlay; the system triggers it. |
| **Content rendering** | Component defined in Part 5 ownership map | B7 (rules) renders via C-08. B4 (facts) via C-07. |
| **Filter (cluster chips)** | I-04 (Cluster Filter Toggle) | I-04 owns chip rendering, toggle logic, and filtered state. |
| **Step progress** | C-05 (Step Progress Indicator) | C-05 owns the visualization. Screen passes step count/current. |
| **Confirmation record rendering** | C-09 (Confirmation Record) | C-09 renders all confirmation data. P-11 provides source. |

**Accessibility ownership — the iron rule:**

Every component must:
1. Carry correct `role`, `aria-*`, and `aria-label` attributes for its type
2. Be keyboard-focusable and handle focus traps/cycles correctly
3. Announce dynamic content changes via `aria-live` regions
4. Work with NVDA, VoiceOver, and TalkBack
5. Meet WCAG AA contrast (4.5:1 text, 3:1 UI) on both Ink and Paper surfaces

No component delegates its accessibility to a parent. No component relies on a wrapper for a11y.

### 14.C RESPONSIBLE PATTERNS

Patterns that must remain flexible for future editions (2K26, 2K27...).

| What must remain flexible | How the spec ensures it | Constraint |
|---|---|---|
| **New events (17+ to 100)** | B-01 Event Tiles are data-driven. Tiles render in cluster groups. Landscape adapts density via breakpoints. | 20+ events may trigger new clusters. Breakpoints handle density. |
| **New clusters (5+)** | B-02/B-03 accept any name. I-04 generates chips from event data. No hardcoded cluster count. | New order is admin-defined. Visual treatments per cluster are Phase 4. |
| **Registration flow steps** | C-05 supports 4–8 steps. Each step is a P-NN screen. Add a step = insert a new screen in the chain. | Step declaration (P-06 Zone B) lists expected steps. |
| **Season state transitions** | G1 is configurable enum. Admin toggles. Unknown states handled gracefully. | All 34 screens must respond to any G1 value. |
| **TBD placeholder replacement** | Placeholder postures share the same component shape as real content. Swapping = swapping data source. | See §14.F — placeholder implementation pattern. |
| **Edition reuse (2K27+)** | G2 is the edition key. All content edition-scoped in Supabase. Admin resets per edition. | Phase 2.5 §12 scalability. |
| **Payment flow (TBD)** | P-10 is structural. Payment component accepts a config object. When TBD resolves, config is populated. | Never invent payment amounts or gateway names. |

### 14.D FIXED vs FLEXIBLE

What implementation **CANNOT change** vs what **MAY vary** by developer choice.

#### LOCKED — cannot be changed by implementation

| Locked item | Why | Source |
|---|---|---|
| **Screen contracts** (Part 1) | Purpose, audience, entry/exit are structural | Part 1, Golden Question |
| **Content zones per screen** (Part 3) | Zone hierarchy = reading order = journey beat | Part 3, Charter §5 |
| **Content object inventory** (Phase 2.5) | 43 objects, single-source ownership | Phase 2.5 Part 1 |
| **Component inventory** (Part 4) | 54 components, justified, EVOKE-Tested | Part 4 |
| **State machines** (Part 7) | Every state triggered by known condition | Part 7 |
| **Season state machine** (G1) | Time Architecture backbone | Phase 2.5 G1 |
| **Accessibility requirements** (Part 8) | WCAG AA is legal, non-negotiable | Part 8, Phase 0 §12.7 |
| **Screen relationships** (Part 2) | 7 types, 12 forbidden paths, 11 recovery paths | Part 2 |
| **1 primary action per screen** | Competing CTAs destroy Progressive Confidence | Phase 2 §8.1 |
| **No login before browsing** | Gate-before-value destroys trust | Phase 2.5 §2.3 |
| **EVOKE Test** (Phase 1.5 Part 9) | Identity gate — every screen must pass | Phase 1.5 Part 9 |
| **Blacklist** (Phase 1, 60 items) | Each banned for constitutional reason | Phase 1 Part 12 |
| **4 recovery routes** | Back, Around, Out, Later — no dead ends | Phase 2.5 §PART 6 |
| **Registration status is derived** (B11) | Manual status always stale | Phase 2.5 §5.1 |
| **One Last Rule** | Nothing exists because it looks good | Phase 1.5 §11.4 |

#### FLEXIBLE — may vary by implementation

| Flexible item | Why | Boundary |
|---|---|---|
| **Exact field names in forms** (C4) | TBD (Charter §7) | Must follow form architecture (Part 9). Validation rules fixed. |
| **Payment flow mechanics** | TBD (Charter §7) | Must fit within P-10 structural contract and 9-step journey. |
| **Visual styling** | Phase 4+ deliverable | Must respect Bible colour roles, typography levels, button/shape rules. |
| **Motion implementation** | Phase 4 deliverable | Must respect gesture grammar, motion laws, reduced-motion. |
| **Admin UI patterns** | Utility-first, functional | Must not use signature language. Must remain invisible. |
| **Exact breakpoint pixel values** | Device-agnostic specification | Must match 4 surface classes and Part 6 behavioural descriptions. |
| **Third-party library choices** | Implementation detail | Must not violate Blacklist or accessibility. No heavy bundles. |
| **Routing pattern** | Implementation detail | Must support all defined routes. SSR or SPA acceptable. |
| **State management pattern** | Implementation detail | Must support G1 global state + per-component state. |

### 14.E DATA FLOWS

Data moves through the platform via well-defined channels. No circular flows.

#### Content object → screen → component mapping

| Content object | Flows to | Via component | Direction |
|---|---|---|---|
| A1–A3 (Identity) | P-01 (Welcome Beat) | Typography, B-03 | Admin → P-01 (read) |
| B1 (Event list) | P-03 (Landscape) | B-01 Event Tiles | Admin → P-03 (read) |
| B2 (Cluster tags) | P-03, P-04 (Event Detail) | B-02, B-03 | Admin → P-03, P-04 (read) |
| B3–B12 (Event data) | P-04 (Event Detail) | C-07, C-08, C-12, others | Admin → P-04 (read) |
| C1 (General rules) | P-05 (Rules & Eligibility) | C-08 (Rules List Item) | Admin → P-05 (read) |
| C4 (Registration data) | P-07, P-09 (Reg steps) | C-01, C-02 | User input → Supabase (write) |
| C5 (Confirmation) | P-11, P-12 (Confirmation, Your Space) | C-09, D-02 | Supabase → Display (read) |
| C7 (Dashboard status) | P-12 (Your Space) | D-03 (Delta Indicator) | Computed → P-12 (read) |
| D1 (Announcements) | P-12, P-01 (latest only) | D-04 | Admin → Display (read) |
| D2 (Schedule) | P-14 (Schedule) | E-02 (Time Slot Cards) | Admin → P-14 (read) |
| G1 (Season state) | **All public screens** | B-04, A-03, others | Admin → All (broadcast) |
| G2 (Edition key) | A-02, A-01 (Header elements) | System → All (read) |

#### Registration form data flow

```
P-06 (Declare Intent)
    ↓  event selected (B1), step count declared (C2)
P-07 (Participant Info)
    ↓  user enters data → C4 fields → session storage (draft)
P-08 (Declaration & Agreement)
    ↓  agreement checked → rules acknowledged (B7 reference)
P-09 (Review & Confirm)
    ↓  ALL data displayed (C4 contents) → user confirms
    ↓  Supabase write → confirmation record (C5)
P-11 (Confirmation)
    ↓  C5 displayed → participant sees what they registered for
P-12 (Your Space)
    ↓  C5 retrievable → D-02 card in dashboard
```

Form data persists in session storage (draft) until confirmation. Survives: browser back, tab close, network blip. Lost only if: user explicitly cancels or session expires.

#### Confirmation data structure

What is stored and retrievable after registration:

```
Confirmation Record (C5):
├── event_name          (from B1, resolved at P-09)
├── event_slug          (from URL, resolved at P-06)
├── cluster             (from B2, resolved at P-06)
├── participant_names   (from C4, collected at P-07)
├── school              (from C4, collected at P-07)
├── contact_info        (from C4, TBD fields)
├── agreed_rules        (from P-08, boolean: true)
├── registration_status (confirmed / pending / cancelled)
├── confirmation_timestamp
└── payment_status      (TBD — only if payment exists)
```

This record is retrieved by: P-11 (immediate), P-12 (dashboard), A-04 (admin registrations).

### 14.F PLACEHOLDER IMPLEMENTATION PATTERN

TBD items (Charter §7) follow a strict architectural pattern. Placeholders are **structural**, not temporary hacks.

| Rule | Specification | Consequence of violation |
|---|---|---|
| **Every TBD has a placeholder posture** | Honest wait, honest deferred, structure-only, or quiet gap. Defined before content exists. | Inventing content breaks trust. |
| **A placeholder never leaks a promise** | No fake deadlines, invented amounts, or guessed contacts. | Trust Architecture collapses. |
| **When real value arrives, component is REPLACED, never patched** | Same component shape, different data source. No conditional branches around placeholders. | Code complexity balloons. |
| **Placeholder architecture must not increase code complexity** | Placeholder and real content share the same component API. | Placeholder scaffolding becomes permanent dead code. |
| **No placeholder content committed as final** | Pre-launch: automated TBD marker search + manual review. | TBD text in production destroys credibility. |
| **TBD markers are machine-searchable** | Prefix format: `[TBD: C4]`, `[TBD: C3]`. Pattern: `\[\w+:\s*[A-Z]\d+\]`. | Impossible to audit placeholder state. |

### 14.G INTENDED STACK

Reference only. Intended stack: **HTML, CSS, JavaScript, Python, Supabase** — set in `docs/ROADMAP.md`. (The Product Charter does not specify a stack; §6 there is the 4-question decision filter.)

| Spec concept | Maps to stack | How |
|---|---|---|
| **Screens (P-01–P-27, A-01–A-07)** | HTML pages or SPA routes | Each screen = a route with defined zones |
| **Components (A-01 through I-08)** | Reusable UI modules | React, Svelte, Web Components, or plain JS |
| **States (Part 7)** | Data flow + conditional rendering | Same component, different DOM |
| **Forms (Part 9)** | Native HTML forms + validation | Native forms preferred (a11y, keyboard) |
| **Navigation (Parts 2, 11)** | Client router or server navigation | SSR or SPA either works |
| **Content objects (A1–G3)** | Supabase tables + queries | Dynamic data, edition-scoped |
| **Admin (A-01–A-07)** | Supabase Auth + RLS policies | Isolated admin routes |
| **Season state (G1)** | Supabase single row + client cache | Global state, read everywhere |
| **Skeleton loading (F-01)** | CSS `@keyframes` on wireframe shapes | No JS spinner needed |
| **Accessibility (Part 8)** | Semantic HTML + ARIA + focus management | Per-component, verified by tooling |

**Supabase guidance:** `events` (B1–B12), `clusters` (B2), `registrations` (C4/C5), `announcements` (D1), `schedule` (D2), `season` (G1), `settings` (G2).

### 14.H PERFORMANCE CONTRACT

Performance is a feature (Phase 0 §8). Hard metrics:

| Metric | Target | How to achieve |
|---|---|---|
| **Load time** (mobile, mid-range 4G) | ≤3 seconds | Skeleton loading, minimal JS, lazy content |
| **Lighthouse Performance** | ≥90 | Inline critical CSS, deferred JS |
| **Lighthouse Accessibility** | ≥90 | Part 8 requirements |
| **Lighthouse Best Practices** | ≥90 | No console errors, HTTPS |
| **Lighthouse SEO** | ≥90 | Semantic HTML, meta tags |
| **CLS** (Cumulative Layout Shift) | <0.1 | Skeleton frames reserve exact space |
| **INP** (Interaction to Next Paint) | <200ms | Minimal JS on critical path |
| **No layout shift after render** | 0 shifts | Skeleton provides exact dimensions |

**Verification:** Lighthouse CI in pipeline; real-user monitoring post-launch.

---

*End of Part 14 — Developer Contract.*

---

## PART 15 — DESIGNER CONTRACT

Everything a UI designer must know **before opening Figma**.

### 15.A WHAT CANNOT CHANGE

Immutable structural decisions. Changing any of these changes the product, not the visuals.

| Immutable decision | Source | Consequence of change |
|---|---|---|
| **Screen contracts** (Part 1) | Purpose, Audience, Entry/Exit | Screen solves wrong problem → wrong product |
| **Content zones per screen** (Part 3) | Zone hierarchy, density | Zone order = reading order. Reorder = wrong beat |
| **Component inventory** (Part 4) | 54 components, 9 categories | Adding = Blacklist risk. Removing = unsolved problem |
| **State machines** (Part 7) | Every screen, every component | Missing state = unknown behavior |
| **Accessibility rules** (Part 8) | 106 requirements, WCAG AA | Excludes users → violates Phase 0 §12.7 |
| **Season states** (Phase 2.5 G1) | 5 states, global | Wrong season → wrong CTAs → dead ends |
| **60-item Blacklist** (Phase 1 Part 12) | Each banned for constitutional reason | Re-enabling undoes that reason |
| **EVOKE Test** (Phase 1.5 Part 9) | 12 questions | Platform identity fractures if screens fail |
| **24 Constitution principles** (Phase 1) | Govern every visual decision | Ignoring one weakens the grammar |
| **Progressive Confidence** (Charter §5) | Each step makes user more certain | Reverse → lost trust |
| **4-question decision filter** (Charter §6) | Choice, uncertainty, trust, identity | Failing = decoration |
| **1 primary action per screen** (Phase 2 §8.1) | One CTA per screen | Competing CTAs destroy the beat |
| **No login before browsing** (Phase 2.5 §2.3) | Value before gate | Gate-before-value destroys trust |
| **4 recovery routes** (Phase 2.5) | Back, Around, Out, Later | Missing recovery = dead end |
| **Slip universality** (Phase 1.5 §11.2) | Universal container | Competing container breaks identity |
| **One Last Rule** (Phase 1.5 §11.4) | Nothing exists because it looks good | Decoration replaces purpose |

**No exceptions.** If a designer finds one blocking a better idea: write why the rule causes a problem, trace to constitution, propose alternative, get written approval.

### 15.B WHAT MAY CHANGE

Designer freedom within constitutional bounds:

| Design dimension | Designer decides | Boundary |
|---|---|---|
| **Color palette** | Exact hex values | Ink/Paper/Amber/Rose/Teal roles. Two surfaces. Two-hue per surface. |
| **Typography** | Font families | Display sans + humanist sans. 3 levels. Tabular numerals. |
| **Spacing** | Base unit, values | Generous = luxury. 12/6/4 grid. |
| **Iconography** | Icons, event marks (16) | Geometric-parent discipline. From personality analysis. |
| **Illustration** | Style, composition | Documentary-real only. No stock. |
| **Button shape** | Radius, proportions, details | Chunky, generous height. Amber-on-ink or ink-on-paper. |
| **Card design** | Exact treatment | "The Slip" — rectangular frame, handmade edge. |
| **Motion curves** | Easing, duration | 2 speeds, 2 characters. 5 gestures only. |
| **Pattern vocabulary** | Motif drawings | 6 motifs only: Slip, Light, Edge, Stamp, Stack, Clock. |
| **Loading pattern** | Skeleton details | Skeleton frames, amber pulse. No spinners. |
| **Logo/wordmark** | Create the mark | Phase 2 deliverable. Survives EVOKE Test #3. |

### 15.C VISUAL FREEDOM MAP

| Item | Designer creates (freedom) | Spec defines (constraint) |
|---|---|---|
| **Color palette** | Exact hex values | Roles: Ink, Paper, Amber, Rose, Teal. Two surfaces. |
| **Typography** | Font families (display + body) | Display sans + humanist sans. 3 levels. |
| **Spacing** | Base unit, values | Generous = luxury. 12/6/4 grid. |
| **Motion library** | Curves, durations, choreography | 2 speeds, 2 characters. 5 gestures. Reduced motion. |
| **Pattern vocabulary** | Motif drawings | 6 motifs only. |
| **Event marks (16)** | Shape, stroke, style | Geometric-parent discipline. |
| **Logo/wordmark** | Drawing, composition | Phase 2 deliverable. Survives EVOKE Test #3. |
| **Error page (404)** | Torn slip visual | Named exception §11.1.5 — Lost Slip. |
| **Hover/focus states** | Exact treatment | Amber focus ring. Brightness shift + rise. |

### 15.D STRUCTURAL CONSTRAINTS

Hard constraints:

| Constraint | What it means |
|---|---|
| **Every component exists** (Part 4) | No new components. No removed components. All 54 must be designed. |
| **Every screen has its zones** (Part 3) | Zone order, hierarchy, density. Cannot reorder or skip. |
| **Every state exists** (Part 7) | All screen and component states designed. No state optional. |
| **No inventing screens** | 34 screens total. No extras without constitution trace. |
| **No removing screens** | All 34 exist. Removal requires written justification. |
| **Blacklist is HARD** (60 items) | No exceptions. Forbidden everywhere. |
| **EVOKE Test passes** (12 questions) | All must pass. Failing requires redesign. |
| **One Last Rule** | Every element solves a problem. Nothing because it looks good. |

### 15.E FREEDOM BOUNDARIES

#### MAY do:

- Design exact "Slip" treatment — within: rectangular frame, handmade edge
- Choose exact typefaces — within: display sans + humanist sans, 3 levels
- Create exact color palette — within: Ink/Paper duality, accent roles
- Design exact hover/focus — within: amber ring, brightness shift + rise
- Create exact skeleton shapes — within: slip outlines, amber pulse
- Design Clock motif — within: Clock rules (§6.6)
- Illustrate Lost Slip (404) — within: §11.1.5 language
- Design event marks (16) — within: geometric-parent discipline
- Decide exact spacing — within: generous philosophy, 12/6/4 grid
- Choose exact easing/durations — within: 2 speeds, 2 characters

#### MUST NOT do:

- Change screen zone hierarchy (structural, not aesthetic)
- Remove required accessibility (Part 8: 106 requirements)
- Use any Blacklist anti-pattern (60 items, no exceptions)
- Create >1 primary action per screen
- Invent a new container type besides The Slip
- Violate the One Last Rule (nothing exists because it looks good)
- Apply signature gestures to logistics moments
- Add decorative elements outside the 6 motifs
- Use gradients, glassmorphism, carousels, scrolljacking
- Design color-only status (always text + color)
- Design hover-dependent information (mobile equity)
- Place logo above tagline (tagline is first anchor)

### 15.F REVIEW CRITERIA

 Designer's deliverable checked. **ALL must be YES.**

| # | Question | Validates |
|---|---|---|
| 1 | **Does every screen pass the EVOKE Test?** | Coherent identity across 34 screens |
| 2 | **Does every element pass the One Last Rule?** | Nothing exists because it looks good |
| 3 | **Does every state machine have visual representations?** | All Part 7 states designed |
| 4 | **Does every screen exist on all 4 surfaces?** | Part 6 responsive fulfilled |
| 5 | **Does every screen exist in every required state?** | Part 7 states covered everywhere |
| 6 | **Does every motion have a reduced-motion equivalent?** | Part 8 §8.F: static equivalents |
| 7 | **Does the design survive the logo being removed?** | Identity is structural, not decorative |
| 8 | **Are all 60 Blacklist items absent?** | No anti-patterns |
| 9 | **Is the primary CTA visually dominant on every screen?** | Phase 2 §8.1: one action |
| 10 | **Do all disabled states carry an explanation?** | Blacklist #57: disabled without explanation forbidden |
| 11 | **Are ALL status indicators text + color?** | Blacklist #51: color-only status forbidden |
| 12 | **Do both Ink and Paper surfaces work?** | Bible §4.4: two-surface duality |
| 13 | **Is the focus ring visible on both surfaces?** | Part 8 §8.E: AA contrast both surfaces |
| 14 | **Is Admin UI functional, not emotional?** | Phase 2.5 §2.4: Admin invariant |
| 15 | **Does the Lost Slip (404) use the exception grammar?** | Phase 1.5 §11.1.5 |

**Review process:**
1. Designer produces all 34 screens × 4 surfaces × all states
2. Each screen checked against its Golden Question (Part 1)
3. Each screen checked against its content zones (Part 3)
4. Each component checked against its spec (Part 4)
5. EVOKE Test applied to every screen
6. One Last Rule applied to every element
7. Blacklist audit (60 items)
8. Accessibility audit (Part 8 + automated tooling)
9. Reviewer signs off OR returns with specific violations

---

*End of Part 15 — Designer Contract.*

---

## PART 16 — VALIDATION

Final validation before Phase 4. Proves the spec is structurally unambiguous.

### 16.A THE 10-DESIGNER TEST

If 10 different designers receive this document, would they produce the same product with different visuals?

#### P-01 Welcome Beat

| MUST be identical | CAN differ |
|---|---|
| 3 zones: Identity / Status / CTA | Exact hex values (within Ink/Paper roles) |
| Tagline is first visual anchor | Typeface families (within display/humanist sans) |
| Status line honest about G1 | Spacing (within generous philosophy) |
| One primary CTA: "Explore Events" | Weight, tracking, stacking |
| No login wall — value before gate | Button shape (within chunky rule) |
| ≤1 screen of reading | Pattern (within 6 motifs) |

**Verdict:** Same structure. Tagline first. CTA singular. Status honest.

#### P-03 Landscape

| MUST be identical | CAN differ |
|---|---|
| 4 clusters: Stage → Mind → Art → Maker | Tile details (within Slip frame) |
| 16 tiles (mark + name + cluster + status) | Cluster header treatment |
| Cluster filter toggle present | Tile hover/focus states |
| Status badge: text + color per tile | Cluster accent within roles |
| No search — discovery via structure | Event mark iconography |

**Verdict:** Same scanning experience. Structure fixed. Content fixed.

#### P-04 Event Detail

| MUST be identical | CAN differ |
|---|---|
| 7 zones: A (Personality) → G (Decision) | Section dividers |
| Rules always visible (not accordion) | Quick Fact styling (within C-07) |
| Sticky CTA on mobile below fold | Rules list styling (within C-08) |
| Reading width ~65ch for body text | Card styling, spacing |
| FAQ is accordion (C-12) | Accordion treatment |

**Verdict:** Same reading journey. Zone order fixed. Sticky CTA mandatory mobile.

#### Registration (P-07 through P-09)

| MUST be identical | CAN differ |
|---|---|
| Linear 4–5 step flow (no skipping) | Input styling (within paper + labels above) |
| Step progress indicator at top (C-05) | Input focus (within amber ring) |
| Labels above inputs (never placeholder-only) | Button styling (within chunky rule) |
| Inline validation below fields (C-06) | Error visual treatment |
| Full review Step 4 before submit | Progress indicator format |
| Pause & Save available | Slip treatment for sections |

**Verdict:** Same flow. Linear fixed. Validation fixed. Review mandatory.

#### P-11 Confirmation

| MUST be identical | CAN differ |
|---|---|
| Stamp gesture present | Stamp visual treatment |
| Confirmation record restated (C-09) | Card within Slip frame |
| "What's next" + next step | Spacing around stamp |
| Primary CTA: "Go to Your Space" | Typography |

**Verdict:** Same celebration. Stamp mandatory. Record restated.

#### P-12 Your Space

| MUST be identical | CAN differ |
|---|---|
| Greeting + Delta at top | Dashboard card design |
| Registration records scrollable | Announcement card design |
| Announcements below records | Season-aware button styling |
| Season-aware next steps | Layout within Part 3 zones |

**Verdict:** Same return engine. Delta signal at top. Record retrievable.

#### Resolved ambiguities:

| Ambiguity | Resolution | Where |
|---|---|---|
| Max nav items? | 4 (Schedule conditional) | Part 4 §A-03 |
| Filter sticky on mobile? | No — collapse only | Part 6.B |
| 2 equal-prominence CTAs? | No — one primary | Part 4 §C-10 |
| Rules behind accordion? | No — always visible | Part 4 §C-08 |
| Color-only status? | No — always text + color | Part 8 §8.E |
| Logo on 404? | No — Lost Slip owns space | Part 4 §A-01 |

### 16.B AMBIGUITY AUDIT

| Part | Coverage | Ambiguity | Scope |
|---|---|---|---|
| **Part 1 – Screens** | 34 screens, full metadata | **Very low** | Only TBD content varies |
| **Part 2 – Relationships** | 7 types, 12 forbidden, 11 recovery | **Very low** | Deterministic |
| **Part 3 – Wireframes** | 34 screens, zones | **Low** | Visual treatment within zones |
| **Part 4 – Components** | 54 components, 9 categories | **Very low** | Implementation flexible |
| **Part 5 – Relationships** | Parent-child, composition | **Very low** | Styling flexible |
| **Part 6 – Responsive** | 4 surfaces, per-screen | **Low** | Pixel breakpoints flexible |
| **Part 7 – States** | All screens, components | **Low** | Visual state representation |
| **Part 8 – Accessibility** | 106 requirements | **Very low** | Implementation flexible |
| **Part 9 – Forms** | 5 steps, validation, model | **Low** | Field names TBD |
| **Part 10 – Discovery** | No search, 3 mechanisms | **Very low** | Structure only |
| **Part 11 – Navigation** | 7 components, 2 tiers | **Low** | Pixel budget flexible |
| **Part 12 – Error/Empty** | 5 errors, 6 empty, 4 loading, 3 waiting | **Very low** | Visual treatment flexible |
| **Part 13 – Interactions** | 5 gestures, keyboard | **Low** | Curves/durations flexible |
| **Part 14 – Dev Contract** | Full developer guidance | **Very low** | Implementation bounded |
| **Part 15 – Design Contract** | Freedom boundaries | **Very low** | Visuals within bounds free |

**Over-specification:** None found. Visual freedom preserved.
**Under-specification:** 2 intentional — field names (TBD) and motion curves (Phase 4). Both have placeholder postures.

**Verdict:** 10 designers → 10 visually distinct versions of the same structural product.

### 16.C CONSTITUTION CROSS-CHECKLIST

#### Phase 0 Discovery

| Requirement | Satisfied by | Evidence |
|---|---|---|
| **Students** (§2.1) | P-03, P-04, C-10 | Part 1; Part 4 |
| **Coordinators** (§2.2) | P-05, P-14 | Part 1; Part 6.C |
| **Parents** (§2.3) | P-15, P-17, P-18 | Part 1 |
| **16 events** (§3.1) | P-03: 16 tiles, 4 clusters | Part 1 |
| **4 clusters** (§4.17) | B-02, B-03, I-04 | Part 4 |
| **One screen of reading** (§6.1) | P-01: 3 zones | Part 3 |
| **Performance** (§8) | ≤3s, LHS ≥90, CLS<0.1 | Part 14.H |
| **WCAG AA** (§12.7) | 106 requirements | Part 8 |
| **Mobile = Desktop** (§12.9) | 4-surface design | Part 6 |
| **14 principles** (§12) | Traced throughout | Golden Questions |

#### Phase 1 Brand Bible

| Requirement | Evidence |
|---|---|
| **Blacklist (60)** | No item used in any screen/component |
| **24 principles** | Traced in specs and blueprints |
| **Button = chunky** | C-10 (Part 4) |
| **Input = labels above, focus ring** | C-01 (Part 4) |
| **Card = The Slip** | B-01 (Part 4) |
| **Loading = skeleton, pulse** | F-01 (Part 4) |

#### Phase 1.5 Creative Review

| Requirement | Evidence |
|---|---|
| **EVOKE Test (12)** | Applied to every screen (Parts 3, 15.F) |
| **5 gestures** | Mapped in Part 13 |
| **Slip universality** | B-01, D-04, F-04, F-05 |
| **Named exceptions** | Lost Slip, Waiting Slip |
| **6 motifs only** | Enforced (Part 4 I-01 through I-08) |

#### Product Charter

| Requirement | Evidence |
|---|---|
| **9-step journey** (§3) | P-01 → P-03 → P-04 → Reg → P-11 → P-12 → P-14 |
| **Progressive Confidence** (§5) | Every step builds certainty |
| **4-question filter** (§6) | Applied to all screens |
| **TBD placeholders** (§7) | Honest postures for all TBD (Part 14.F) |

#### Phase 2

| Requirement | Evidence |
|---|---|
| **5 Acts** | Welcome → Landscape/Detail → Rules/Reg → Decision → Afterglow |
| **Cognitive load** | Low → Medium → HIGH → Medium → Low |
| **Failure journeys** | 11 recovery paths, 4 waiting states |
| **Trust** | Honest status, no invented content |

#### Phase 2.5

| Requirement | Evidence |
|---|---|
| **11 page contracts** | All fulfilled (Part 3) |
| **43 content objects** | All mapped (Part 5 §5.6) |
| **Single-source** | Each object one owner |
| **Season states (5)** | G1 defined, consumed everywhere |
| **4 recovery routes** | Back, Around, Out, Later |
| **Scalability** | Data-driven tiles, extensible clusters |

### 16.D CONSISTENCY CHECK

| Dimension | Result |
|---|---|
| **Naming** | ✅ Cluster, Season, Screen, Component codes consistent throughout |
| **Terminology** | ✅ Slip, Progressive Confidence, Golden Question, One Last Rule — same everywhere |
| **Contracts vs wireframes** | ✅ Part 1 purpose matches Part 3 zones |
| **Inventory vs ownership** | ✅ Part 4 matches Part 5 map |
| **States vs a11y** | ✅ Part 7 states have Part 8 definitions |
| **Responsive vs components** | ✅ Part 6 surfaces match Part 4 variants |
| **Blacklist vs components** | ✅ No component uses any Blacklist item |
| **Season vs screens** | ✅ Part 7 matches Part 1 availability |
| **Objects vs zones** | ✅ Part 3 zones reference correct objects |
| **Nav vs footer** | ✅ A-03 matches A-07 per 2-tier model |
| **Contradictions** | ✅ None found across 17 parts |

**Verdict:** No contradictions. All consistent.

### 16.E THE GOLDEN QUESTION (applied to entire spec)

| Question | Answer |
|---|---|
| **WHY does this exist?** | Bridge experience direction to implementation. Without it, 10 designers produce 10 different products. |
| **WHY now?** | Before visual design or coding. Structure locked before aesthetics. |
| **WHY not less?** | Less = ambiguous. Every screen needs zones, every component states, every state triggers. |
| **WHY not more?** | More = implementation. Visual design (Phase 4), pixels, curves belong elsewhere. This spec defines WHAT and HOW it behaves. |

**Verdict:** Right reason, right time, right detail.

---

*End of Part 16 — Validation.*

---

## PART 17 — PHASE 3 READINESS

### 17.A DIMENSION SCORECARD

| Dimension | Score (1-5) | Rationale |
|---|---|---|
| **Interface Architecture overall** | **5** | 17 parts. Every structural dimension covered. |
| **Screen Inventory** (Part 1) | **5** | 34 screens. Full metadata per screen. |
| **Screen Relationships** (Part 2) | **5** | 7 types, 12 forbidden, 11 recovery. Deterministic map. |
| **Wireframe Blueprint** (Part 3) | **5** | 34 screens blueprinted. Wireframe artist can build from this. |
| **Component Inventory** (Part 4) | **5** | 54 components. Every one specified with Purpose/Where/Never/States. |
| **Component Relationships** (Part 5) | **5** | Parent-child, composition, ownership, reuse. Complete. |
| **Responsive Behaviour** (Part 6) | **5** | 4 surfaces. Per-screen behavioural design. Thumb reach. |
| **State Architecture** (Part 7) | **5** | Machines for all screens + components. Every state defined. |
| **Accessibility** (Part 8) | **5** | 106 requirements, 14 categories. WCAG AA traced. |
| **Form Architecture** (Part 9) | **4** | 5 steps, validation, data model, draft. Minus 1: field names TBD (Charter §7). |
| **Search & Discovery** (Part 10) | **5** | No search (justified). 3 discovery mechanisms. |
| **Navigation Blueprint** (Part 11) | **5** | 7 components, 2 tiers. Season-aware. Admin separated. |
| **Error/Empty/Loading** (Part 12) | **5** | 5 errors, 6 empty, 4 loading, 3 waiting. All defined. |
| **Interaction Blueprint** (Part 13) | **4** | 5 gestures, keyboard map, mobile audit. Minus 1: exact curves TBD (Phase 4). |
| **Developer Contract** (Part 14) | **5** | Naming, ownership, patterns, fixed/flexible, data flows, placeholder, stack, performance. |
| **Designer Contract** (Part 15) | **5** | Immutable, changeable, freedom map, constraints, boundaries, review (15Q). |
| **Validation** (Part 16) | **5** | 10-Designer Test, Ambiguity Audit, Cross-checks, Consistency, Golden Question. |

**Score summary:**
- **5 (Complete):** 14 dimensions
- **4 (Minor documented gap):** 2 dimensions (Forms — TBD field names; Interactions — TBD motion curves)
- **3, 2, 1:** None

**Overall: 4.88 / 5.00** — Ready for Phase 4.

### 17.B PHASE 4 READINESS

**Ready for Phase 4 (Motion & Interaction Blueprint)?**

**YES.**

**What Phase 4 inherits:**
- 34 screens with zones, hierarchy, content objects
- 54 components with states, variants, composition rules
- All state machines with triggers, visibility, recovery
- All accessibility (106 requirements, reduced-motion equivalents)
- All form architecture (structure fixed, field names TBD)
- Developer Contract (naming, ownership, performance)
- Designer Contract (immutable vs changeable, review criteria)
- Validation (10-Designer Test passed, all constitutions verified)

**Phase 4's work:**
- Visual styling (colors, typography, spacing)
- Motion implementation (curves, durations, choreography)
- Gesture visual design (Sweep, Lift, Stamp, Tear, Curtain)
- Event marks (16 icons)
- Logo/wordmark

**Phase 4's constraints:**
- Preserve all structure (Part 15.A)
- Pass EVOKE Test (15.F)
- No Blacklist violations (60 items)
- No zone hierarchy changes (Part 3)

### 17.C IMPLEMENTATION READINESS

**Ready for Phase 5 scaffolding?**

**YES — Phase 4 is the visual gate.**

**Buildable now (structural):**
- Screen routing (34 routes defined)
- Component skeletons (54 shapes defined)
- Data flow layer (Supabase schema draft)
- Season state management (G1 global)
- Accessibility layer (106 structural requirements)
- Form validation architecture (rules defined, fields TBD)
- Error/recovery infrastructure (F-01, F-02; screens P-23, P-24, P-25, P-26, P-27)
- Placeholder components (§14.F)

**Must wait for Phase 4:**
- Exact visual styling
- Motion implementation
- Gesture visual design
- State visual treatments
- Event marks
- Logo/wordmark

### 17.D KNOWN GAPS

| Gap | Status | Why TBD | Resolution blocker |
|---|---|---|---|
| **Registration field names** (C4) | TBD | Organizer not declared | Charter §7 |
| **Payment flow** (P-10, C3) | TBD | Fees/gateway unknown | Charter §7 |
| **Contact details** (A7, E2) | TBD | Real contact not available | Q12 — must be real |
| **Host school** (A4) | TBD | Not confirmed | Q19 — must be real |
| **Festival dates** (A5) | TBD | Not announced | Q1 — must be real |
| **Venue** (A6) | TBD | Not booked | Q2 — must be real |
| **Quota policy** (Q10) | TBD | Not decided | Organizer |
| **Eligibility** (Q5) | TBD | Not decided | Organizer |
| **Schedule** (D2) | TBD | Not created | Approach season |
| **Auth model** (C6) | TBD | Not decided | Implementation |
| **Supabase schema** | TBD | Not designed | Implementation |
| **Payment gateway** | TBD | Not selected | Implementation + organizer |
| **Breakpoints** (pixels) | TBD | Device-agnostic | Phase 4 or implementation |
| **Event marks** | TBD | Phase 2 deliverable | Designer |
| **Logo/wordmark** | TBD | Phase 2 deliverable | Designer |
| **Gallery** (D3, P-20) | Future | No photography yet | Event must occur |
| **Winners** (D4, P-21) | Future | Event not complete | Event must occur |
| **Analytics** (F4) | Future | Not needed for MVP | Future decision |

All gaps follow placeholder pattern (Part 14.F). None block structural work.

### 17.E RISK ASSESSMENT

| Risk | Likelihood | Impact | Mitigation |
|---|---|---|---|
| **TBD changes structure** | Low | High | Placeholder architecture (§14.F): replace, never patch |
| **TBD adds many fields** | Medium | Medium | Form architecture supports configurable fields (§14.C) |
| **Designer violates Blacklist** | Medium | High | Review criteria (15.F). Blacklist audit mandatory. |
| **Developer ignores spec** | Medium | High | Developer Contract (§14). Every boundary defined. |
| **Accessibility audit fails** | Medium | High | Part 8: 106 requirements + axe + NVDA/VoiceOver. |
| **Performance missed** | Medium | Medium | Performance Contract (§14.H). LHS CI. Skeleton loading. |
| **New events break structure** | Low | Medium | Extensibility (§14.C): 16→100. Data-driven. Scales. |
| **Season needs new state** | Low | Low | G1 configurable. New states via A-06. Graceful fallback. |
| **Admin UI leaks** | Low | High | Admin invariant (Phase 2.5 §2.4). Firewall. Separate auth. |
| **Content duplication** | Low | Medium | Single-source (Part 5 §5.6). One owner per object. |
| **Placeholder shipped as final** | Medium | High | Automated TBD marker search. Manual pre-launch review. |
| **Mobile performance degrades** | Medium | High | Skeleton (F-01). Lazy loading. Minimal JS. Perf contract. |

**Risk verdict:** All known. All mitigated. No risk unmanaged.

---

*End of Part 17 — Phase 3 Readiness.*

---

*End of Phase 3 Interface Architecture Specification — Parts 1–17. Specification complete.*
