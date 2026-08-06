# EVOKE 2K26 — Phase 2.5: Structural Architecture

*Final planning phase — validating that every page, section, interaction, path, and content object has a justified place.*

| | |
|---|---|
| **Project** | EVOKE 2K26 — Participant & Registration Platform (Inter-School Festival) |
| **Phase** | 2.5 — Structural Architecture / Information Architecture Validation (NOT UI design, NOT wireframing, NOT coding) |
| **Documents in force** | Phase 0 Discovery · Phase 1 Brand Bible · Phase 1.5 Creative Review + Appendix A · Phase 1.75 Product Charter · Phase 2 Experience Direction (all immutable) |
| **Status** | Draft for review — approval gates Phase 3 (Wireframe Architecture) |
| **Role** | Systems Architect · Information Architect · Product Architect · Service Designer · UX Auditor · Technical Product Manager · Experience Reviewer · Product Strategist |

> This phase does **not** design. It **validates**. Every future page, section, interaction, navigation path, piece of content, and user decision must already have a justified place — traceable to the five constitutions. Nothing unnecessary survives this phase; nothing important is missing.
>
> **The Golden Question,** asked of everything: *Why does this exist? Why now? Why here? Why not somewhere else? Why should the user care?*
>
> **The One Last Rule (this phase's reading):** nothing exists because it looks good. Everything exists because it improves **clarity, confidence, trust, or progress**.
>
> **After approval, documentation stops leading. Implementation begins.**

---

## PART 1 — Master Content Inventory

Every content object the platform requires, with its justification. Status codes: **M** = mandatory (this edition), **O** = optional, **P** = placeholder (structure exists, content gated — Charter §7), **F** = future (not this edition, area reserved).

### A. Identity & orientation

| # | Content object | Why it exists | Who needs it | When | Status |
|---|---|---|---|---|---|
| A1 | Festival description ("what EVOKE is") | Answers the first question of every journey (Phase 2 Part 1) | First-time visitors | Arrival / identity beat | M |
| A2 | Tagline — "Bring out the best in You." | Memory Anchor #1; the promise (Phase 2 Part 18.2) | Everyone | Arrival | M |
| A3 | Edition identity — EVOKE 2K26 | Annual-institution feel; prevents stale-edition confusion (Phase 0 5.2.8) | Everyone | Always visible | M |
| A4 | Host school / college | Trust Architecture: official presence (Phase 2 Part 15.1) | Parents, coordinators, media | Quiet corners | P (Q19) |
| A5 | Festival dates | Removes the #1 uncertainty (Phase 0 Q1; Phase 2 Part 15.3) | Everyone | Welcome + quiet corners + Your Space | P |
| A6 | Venue | Logistics trust (Phase 0 Q2) | Coordinators, parents | Quiet corners + Schedule | P |
| A7 | Organizer contact | The doubt-home; trust requirement (Phase 0 Q12; Phase 2 Part 15.2) | Everyone | Quiet corners, always findable | P |
| A8 | Festival history / editions | Credibility for parents; future-participant pipeline (Phase 0 Q20) | Parents, future participants | About | F |

### B. Events domain

| # | Content object | Why it exists | Who needs it | When | Status |
|---|---|---|---|---|---|
| B1 | Event list (16 events) | The landscape store — single source of the festival's choices (Phase 0 3.1) | Students, coordinators | Landscape + event detail | M |
| B2 | Cluster tags (Stage/Mind/Art/Maker; On/Off-Stage) | Guided choice — four worlds narrow 16 options (Phase 2 Part 3.3) | Students | Landscape | M (Q3 inference flagged) |
| B3 | Event personality description | "Is this me?" — event as mini-experience (Phase 0 §4, §6.5) | Students | Event detail, intro | M |
| B4 | Quick facts (team size, time limit, duration) | Decision support; time is the festival's scarcest resource (Phase 0 3.3.5) | Students, coordinators | Event detail | M |
| B5 | Theme (only where one exists) | Expectation-setting (Phase 0 3.1 — Fashion, Veg Carving, Pot, Collage, Sketch) | Students | Event detail | M (conditional) |
| B6 | Participation / eligibility | The "can I participate?" gate before the doorway (Phase 2 Part 10.1) | Students, coordinators | Event detail | M (class/age part P — Q5) |
| B7 | Rules (faithful wording) | The contract; confidence is earned from rules (Bible 19; Phase 2 Part 10) | All | Event detail only | M |
| B8 | Judging criteria | Fairness transparency — "Judges' decision is final" as promise (Phase 0 3.3.1) | Students, coordinators, judges | Event detail | M |
| B9 | Things to bring / materials | The single most repeated question (Phase 0 3.3.2) | Students, parents, coordinators | Event detail + Your Space (approach) | M |
| B10 | Per-event FAQ | Absorbs recurring questions before they reach the doorway (Phase 2 Part 10.1) | Students, coordinators | Event detail | M (content evolves) |
| B11 | Registration status (open / closed / full) | Decision honesty; failure journeys depend on it (Phase 2 Part 14) | Students | Event detail + landscape | Derived — P until flows |
| B12 | Registration requirements | The surprise-free doorway (Phase 2 Part 10.2) | Students | Decision moment | P (Charter §7) |

### C. Participation & commitment

| # | Content object | Why it exists | Who needs it | When | Status |
|---|---|---|---|---|---|
| C1 | General rules & quota policy | The coordinator contract (Phase 0 2.2; Q10 team caps) | Coordinators | Rules & Eligibility | M (Q10 part P) |
| C2 | Registration flow steps | The doorway — structural now, details gated (Phase 2 Part 10) | Students, coordinators | Registration | P |
| C3 | Payment facts | Money trust — never invented, released at the money moment (Phase 2 Part 15.4) | Students | Decision / payment | P |
| C4 | Team / participant data fields | What will be asked is announced before asking (Phase 2 Part 10.3; Q22) | Organizers | Registration | P |
| C5 | Confirmation record | The receipt; anticipation begins here (Phase 2 Part 19.2) | Registered students, coordinators | Confirmation + Your Space | M (derived; flow P) |
| C6 | Participant identity / profile | The return engine (Phase 2 Part 12.2) | Registered students | Your Space | P (auth model TBD) |
| C7 | Dashboard status lines | "What changed since last visit" (Phase 2 Part 8.3) | Registered students | Your Space | M (structure) / P (contents) |

### D. Communication

| # | Content object | Why it exists | Who needs it | When | Status |
|---|---|---|---|---|---|
| D1 | Announcements | Source of truth over WhatsApp (Phase 0 12.5) | Everyone | Your Space + Welcome (latest) | M (publishing admin; content organic) |
| D2 | Schedule | Logistics — when and where each event runs (Phase 0 Q6) | Coordinators, parents | Schedule area | P |
| D3 | Gallery / photos | Social proof; future-participant magnet (Phase 0 Q14, 5.5) | Future participants, parents | Gallery area | F |
| D4 | Winners / results | The verdict (Stamp) and the memorial beat (Phase 2 Part 18.2; Phase 0 5.5) | Everyone, post-event | Post-event area | F |
| D5 | Social channels | Sharing exits have a place to go (Phase 0 Q16; Phase 2 Part 12.2) | Everyone | Quiet corners | F |
| D6 | Sponsors | Credibility only if they exist (Phase 0 Q15) | Public | Quiet corners | F |

### E. Support

| # | Content object | Why it exists | Who needs it | When | Status |
|---|---|---|---|---|---|
| E1 | Global FAQ | Cross-event, cross-audience questions (Phase 0 6.2) | Parents, coordinators | FAQ | M |
| E2 | Contact route | The doubt-home (Phase 2 Part 15.2) | Everyone | Contact | P |
| E3 | Privacy & data handling note | Student-data trust (Phase 0 risk 14) | Parents, organizers | Quiet corners | M (structural) / P (content) |

### F. Administrative

| # | Content object | Why it exists | Who needs it | When | Status |
|---|---|---|---|---|---|
| F1 | Admin content management | Organizer maintenance without developer dependency (Phase 0 Q21, risk 9) | Organizers | Admin area | M (structural) |
| F2 | Registration management & export | Operational necessity (Phase 0 Q4, Q22, 7.4) | Organizers | Admin area | P |
| F3 | Announcement publishing | Source-of-truth upkeep (Phase 0 12.5) | Organizers | Admin area | M (structural) |
| F4 | Analytics / metrics | Success measurement (Phase 0 §8) | Organizers | Admin area | F |

### G. System objects (not user-facing content, still justified)

| # | Object | Why it exists | Who needs it | When | Status |
|---|---|---|---|---|---|
| G1 | Season state (announcement / registration window / approach / live / post) | The Time Architecture engine — the platform always knows its season (Phase 2 Part 21) | The platform itself | Always | M (structural) |
| G2 | Edition key (2K26 → 2K27…) | Annual reuse without redesign (Phase 0 5.2.12, 12.13) | Organizers | Always | M (structural) |
| G3 | Entry-state (Google / QR / direct / social / registered) | Every entry is a different emotional state (Phase 2 Part 12.1) | The platform itself | On arrival | M (structural) |

**Inventory audit verdict:** 46 objects; 25 mandatory, 1 optional-free (none used), 15 placeholder, 5 future. Nothing present lacks a Phase 0/Phase 2 trace. No object was found that fails the Golden Question.

**Trace:** Phase 0 §3.1, §6.1–6.2, §10; Phase 2 Parts 3, 9, 10, 12, 15, 18–21; Charter §7.

---

## PART 2 — Product Structure

The platform's structure — what it contains and why — organized by area. **Structure is not design:** nothing here prescribes layout, color, or motion. It prescribes what must exist and what must NOT exist, so the platform stays thin by constitution.

### 2.1 Structural principle — a thin shell around one act

Phase 2's architecture (Parts 1–4, 12) defines **one decisive act**: the student choosing and registering for events. The whole platform exists to make that act **confident and repeatable**. Every structural decision below is tested against that act: does it strengthen the act (keep), weaken it (remove), or exist for after-the-act (reserve, minimal)?

### 2.2 Area map

| Area | Contains (inventory refs) | Exists because | Where it lives in the journey |
|---|---|---|---|
| **Identity** | A1–A3 (festival description, tagline, edition) | The promise and the answer to "what is this?" (Phase 0 5.1–5.3; Phase 2 Part 1) | Arrival, always present (quiet presence, not banners) |
| **Landscape** | B1, B2, B11-derived (event list + cluster tags + status) | The store of choices — where the student builds intent (Phase 2 Part 3.3) | Pre-decision |
| **Event Detail** | B3–B12 (personality, quick facts, theme, eligibility, rules, judging, materials, FAQ, requirements) | Decision support — where doubt is removed and intent becomes choice (Phase 2 Parts 9–10) | Pre-decision → decision |
| **Rules & Eligibility** | C1, B6 (general rules, quota, eligibility) | The coordinator contract; the "can I?" gate (Phase 0 2.2, Q10) | Pre-decision (coordinators) |
| **Registration** | C2, C3, C4, B12 (flow, payment, data fields, requirements) | The doorway itself (Phase 2 Part 10.2) | Decision |
| **Confirmation** | C5 (confirmation record) | The receipt; the promise kept; anticipation begins (Phase 2 Part 19) | Post-decision |
| **Your Space** | C6, C7, D1 (profile, dashboard, announcements) | The return engine — the platform's second act (Phase 2 Part 12.2) | Return visits |
| **Schedule** | D2 (schedule) | Logistics — the festival's time layout (Phase 0 Q6) | Approach + live (registered audience) |
| **About / Quiet corners** | A4–A7, E1–E3 (host, dates, venue, contact, global FAQ, privacy) | Trust — the answers to quiet doubts (Phase 2 Part 15; Phase 0 §6.2) | Any moment (quiet presence) |
| **Post-event** | D3–D6 (gallery, winners, social, sponsors) | The memorial and the magnet for next edition (Phase 2 Part 18.2) | Post-event (reserved, minimal now) |
| **Admin** | F1–F4, G1–G3 (content management, registration export, announcements, analytics, season/edition state) | The organizer's quiet engine room (Phase 0 Q21, §7.4, §8) | Always, invisible to participants |

### 2.3 What must NOT exist (structural blacklist)

Checked against the EVOKE Test (Phase 1.5 Part 9) and the Blacklist (Phase 1 Part 12):

1. **Promotional home page with rotating banners.** The platform is a registration platform, not a poster (Charter §1, Phase 2 Part 12.1). Identity presence is quiet.
2. **News/blog section.** Announcements (D1) absorb this need; a blog adds authorial noise (duplication risk — see Part 9).
3. **Exhaustive event gallery pre-event.** Gallery (D3) is post-event only (Phase 0 5.5).
4. **Public schedule pre-registration.** Schedule (D2) is for registered participants approaching the festival; public schedule is a TBD decision (Q6), not invented here.
5. **General-purpose "Explore more" content walls.** Every element must serve a journey beat (Part 4 Golden Question).
6. **Anything requiring a login before browsing.** Browse is free (Phase 2 Part 10.1); login belongs to registration and Your Space only (Charter: no auth invented — structural, not UI).
7. **Countdown timers, confetti, auto-playing media, chat widgets.** Emotional pressure and noise — violate Phase 2 Part 20 (Silence) and Part 17 (Trust).
8. **"Coming soon" dead links.** A dead end — forbidden by Part 10 (Dead End Audit).

### 2.4 Area invariants (each area, always)

| Area | Invariant |
|---|---|
| Identity | Never blocks progress; never asks for anything |
| Landscape | Every event visible; status honest; no dead event tiles |
| Event Detail | Answers every B-item or visibly defers to placeholders (never silence) |
| Rules & Eligibility | Faithful to the rulebook; no editorializing (Bible 19) |
| Registration | Every step declared in advance; no surprise fields (Phase 2 Part 10.3) |
| Confirmation | Must be reachable and retrievable (C5); never a dead end |
| Your Space | Every visit shows "what changed since last visit" (C7) |
| Schedule | Registered users' logistics; honest about TBD parts |
| Quiet corners | Contact always findable; no "contact us" without a contact (Q12 — placeholder-aware) |
| Admin | Invisible; no participant-facing footprint |

### 2.5 Structural test — the thin shell

The platform is "thin": it contains nothing that does not serve the act or the trust. If the organizer's TBD answers (Charter §7) change nothing about the areas above, the structure is stable. **Structure verdict: stable under all TBD outcomes.**

**Trace:** Phase 0 §3, §5, §6, §7, §12; Phase 2 Parts 1, 3, 9, 10, 12, 15, 17–21; Charter §1, §7; Phase 1 Part 12 (blacklist); Phase 1.5 Part 9 (EVOKE Test).

---

## PART 3 — Page Contracts

Every future page, with its single purpose, its audience, what it must answer, what it must NOT do, and its entry/exit states. This is the contract Phase 3 (wireframes) must obey. **Contract format:** Purpose → Audience → Answers (must) → Intentionally leaves unanswered → Entry states → Exit states → Success / Failure states.

### 3.1 The Welcome Beat (Landing page)

- **Purpose:** answer "what is EVOKE 2K26?" and hand the visitor forward — without selling (Phase 2 Part 1, Part 12.1). One screen of reading (Phase 2 Part 6: cognitive load).
- **Audience:** first-time visitors; parents arriving skeptical; returning students re-entering.
- **Answers (must):** What this is (A1); why now — the season state (G1) stated honestly (announcement / registration open / closed / approach); the promise (A2); that registration is open or not, plainly (B11-derived, honest — Phase 2 Part 14 failure journeys).
- **Intentionally leaves unanswered:** rules, fees, judging, schedule details — later beats (Phase 2 Part 7: release by WHEN not WHERE).
- **Entry states:** direct link (print / WhatsApp / QR); search (A3 edition key); social share; return visit (G3 entry-state detection).
- **Exit states:** forward to Landscape (all healthy journeys); exit to search / share (healthy, brief).
- **Success:** visitor knows what EVOKE is and where the doors are, within one screen. **Failure:** visitor does not know what it is, or believes registration is open when it is not (honesty — Part 14).

### 3.2 The Landscape (Event list page)

- **Purpose:** display the full store of choices so the student can find "their" events (Phase 2 Part 3.3). Choice, not browse-for-browse's-sake.
- **Audience:** students at intent-building; coordinators scanning clusters.
- **Answers (must):** every event (B1), its cluster (B2), its honest status (B11-derived), and a clear path to its detail page (B3).
- **Intentionally leaves unanswered:** rules and details — the detail page answers them (Part 3.3).
- **Entry states:** from Welcome; from search; from social; from a returning student's Your Space (cross-entry).
- **Exit states:** into Event Detail; back to Welcome; into Rules & Eligibility (coordinators).
- **Success:** the student narrows 16 events to a shortlist. **Failure:** the landscape overwhelms (mitigation: clusters, Phase 2 Part 3.3) or hides an event (forbidden — no dead tiles, invariant 2.4).

### 3.3 Event Detail page

- **Purpose:** remove doubt about ONE event so the student can choose it with confidence (Phase 2 Part 10.1). The highest-stakes page in the platform.
- **Audience:** students deciding; coordinators verifying; parents checking.
- **Answers (must):** personality (B3); quick facts (B4); theme where it exists (B5); eligibility / can-I-participate (B6); rules, faithfully (B7); judging criteria (B8); things to bring (B9); event FAQ (B10); registration status and requirements (B11, B12); and the explicit next step (register — or why not, honestly).
- **Intentionally leaves unanswered:** festival-wide logistics (dates/venue — quiet corners); payment mechanics (C3 — released at the money moment, Phase 2 Part 15.4).
- **Entry states:** from Landscape; from search; from Your Space shortlist; from direct share.
- **Exit states:** to Registration (decision made); back to Landscape (more options); to Rules & Eligibility (coordinator context).
- **Success:** the student can answer "do I want this, and can I do it?" **Failure:** the page raises questions it cannot answer (silence forbidden — invariant 2.4), or the register path is invisible (doubt wins).

### 3.4 Rules & Eligibility page

- **Purpose:** the coordinator contract — general rules, quota policy, eligibility (C1, B6). One place, faithful wording (Bible 19: rules are the contract).
- **Audience:** coordinators primarily; parents; students cross-checking.
- **Answers (must):** general rules (C1); quota policy (Q10 — placeholder); eligibility baseline (Q5 — placeholder); where per-event rules live (link back to Event Detail — duplication audit, Part 9).
- **Intentionally leaves unanswered:** per-event detail (delegated to 3.3).
- **Entry states:** from Welcome; from Landscape (coordinator path); from Event Detail.
- **Exit states:** back to the referencing page; into a specific Event Detail.
- **Success:** a coordinator can confirm "we may participate, and under which quotas." **Failure:** contradictions with Event Detail (forbidden — single source, Part 9) or TBD presented as fact.

### 3.5 Registration flow (multi-step doorway)

- **Purpose:** the decisive act — collect the commitment, declare every step in advance, ask nothing surprising (Phase 2 Part 10.2–10.3).
- **Audience:** the student (with coordinator when team events).
- **Answers (must):** current step; steps remaining (always — Phase 2 Part 10.3); what is being asked and why (C4); payment facts when the money moment arrives (C3 — placeholder); the review-and-confirm beat before the final step.
- **Intentionally leaves unanswered:** nothing mid-flow — each step answers itself before asking.
- **Entry states:** from Event Detail (register call); re-entry for an abandoned flow (resume — Phase 2 Part 14 recovery).
- **Exit states:** to Confirmation (success); graceful save-and-return (recovery, not loss — Part 10 Dead End Audit); to Contact (doubt-home).
- **Success:** a completed, confirmed registration. **Failure:** abandonment without a recovery path (Part 14: recovery, not error pages) — every interrupted flow must be resumable.
- **Note:** all mechanics (flow steps, fields, payment) remain **placeholder** until Charter §7 resolves (C2, C3, C4). The structural contract — declare, ask, confirm — is fixed now.

### 3.6 Confirmation page

- **Purpose:** the receipt — the promise kept, the beginning of anticipation (Phase 2 Part 19.2). Memory Anchor: the record of the act.
- **Audience:** the registered student and coordinator.
- **Answers (must):** what was registered (events, names, team, payments recorded); the retrieval path (C5 — how to find this again); what happens next (the honest next beat — announcements, schedule, approach).
- **Intentionally leaves unanswered:** nothing that was already promised.
- **Entry states:** end of Registration flow; retrieval from Your Space or recovery link.
- **Exit states:** to Your Space; to Landscape (register more — the repeatable act); to print/share the record.
- **Success:** the student holds a record and knows the next beat. **Failure:** confirmation unreachable or non-retrievable (forbidden — invariant 2.4).

### 3.7 Your Space (participant dashboard)

- **Purpose:** the return engine — everything a registered participant needs across the season, always showing what changed since the last visit (Phase 2 Part 12.2; C6, C7, D1).
- **Audience:** registered students and coordinators only.
- **Answers (must):** their registrations (C5); announcements (D1); what changed since last visit (C7); the honest next beat per season (G1 — register more / approach / schedule / results); their profile (C6 — placeholder auth).
- **Intentionally leaves unanswered:** public content (lives in the public areas; single source — Part 9).
- **Entry states:** login (placeholder auth); post-registration hand-off; recovery from email/WhatsApp link.
- **Exit states:** to Landscape; to Schedule; to post-event areas.
- **Success:** every visit gives one clear "what now?" **Failure:** a login wall before any value (violates trust — gate behind value, not before it), or a dashboard that repeats public content (duplication — Part 9).

### 3.8 Schedule page

- **Purpose:** logistics for the approach and live seasons — when and where each event runs (Phase 2 Part 21: time architecture; D2).
- **Audience:** registered participants, coordinators, parents (logistics trust).
- **Answers (must):** per-event timing and venue (D2 — placeholder); links to event details; what is TBD stated plainly (Q6 — never invented).
- **Intentionally leaves unanswered:** judging detail, results (post-event area).
- **Entry states:** from Your Space; from Event Detail (approach season); from quiet corners.
- **Exit states:** back to the referencing page.
- **Success:** a participant can plan their day. **Failure:** schedule presented as final when TBD (honesty violation) or unreachable for the registered audience.

### 3.9 Quiet corners (About / FAQ / Contact / Privacy)

- **Purpose:** the doubt-home — answers to quiet questions asked at any moment, without demanding attention (Phase 2 Part 15; Phase 0 §6.2).
- **Audience:** everyone, especially parents and coordinators.
- **Answers (must):** host (A4), dates (A5), venue (A6), contact (A7, E2), global FAQ (E1), privacy note (E3) — all placeholder-aware (never invented).
- **Intentionally leaves unanswered:** event-specific detail (delegated to 3.3).
- **Entry states:** from any page (quiet presence — footer-level, always findable, never intrusive).
- **Exit states:** back to the referencing context.
- **Success:** a doubt raised anywhere can be answered here. **Failure:** contact present without a real contact (Q12 — a "contact us" with nothing behind it is a dead end) or privacy absent for student data (risk 14).

### 3.10 Post-event areas (Gallery / Winners / Sponsors)

- **Purpose:** the memorial and the next-edition magnet — evidence that EVOKE keeps its promises (Phase 2 Part 18.2; Phase 0 5.5, Q14–Q16).
- **Audience:** past participants; future participants; parents; sponsors.
- **Answers (must):** what happened (winners, D4); what it looked like (gallery, D3); who supported it (sponsors, D6); where the conversation continues (social, D5).
- **Intentionally leaves unanswered:** nothing for this season; everything for the next is a future structure.
- **Entry states:** from post-event Your Space; from quiet corners; from social.
- **Exit states:** back to identity; forward to next edition's registration (F: season rollover, G2).
- **Success:** a post-event visitor feels "I was part of this" or "I want to be." **Failure:** dead links to empty areas (forbidden — Part 10) — these areas remain **reserved (F), not built**, until content exists.

### 3.11 Admin area

- **Purpose:** the organizer's engine room — content management, registration export, announcement publishing, season/edition state (F1–F4, G1–G3) — invisible to participants (Phase 0 Q21, §7.4, §8).
- **Audience:** organizers only.
- **Answers (must):** how to change a fact, publish an announcement, flip the season state, export registrations.
- **Intentionally leaves unanswered:** everything participant-facing (single source — admin edits, platform displays).
- **Entry states:** organizer authentication (placeholder — not participant auth).
- **Exit states:** back into the platform's public face.
- **Success:** the organizer can run the season without a developer. **Failure:** content that can only change by editing code (risk 9 — forbidden).

**Page contract verdict:** 11 contracts, every one traceable to Parts 1–2 and the constitutions. No page exists without a journey beat; no journey beat lacks a page. (Contact = E2 doubled as A7 — single source rule applies; see Part 9.)

---

## PART 4 — Section Contracts

For every page, the sections that compose it — each section must answer **why it is here** and **what survives if removed**. Sections that fail the removal test are absorbed or removed. This is the anti-bloat gate before any wireframe exists.

**Test applied to every section:** *Why is this section here, on this page, at this moment? If it vanished, what user problem goes unsolved?* If the answer is "nothing" → the section is absorbed elsewhere or deleted.

### 4.1 Welcome Beat sections

| Section | Why it exists | Removed-test verdict |
|---|---|---|
| Identity statement (what EVOKE is, in one beat) | First question of every journey (A1) | **Keep** — nothing answers "what is this?" |
| Season honesty (registration open/closed — stated plainly) | Trust; failure journeys (G1, B11) | **Keep** — silence here is a lie |
| The promise (tagline) | Memory Anchor #1 (A2) | **Keep** — the promise is the anchor |
| Forward hand (the one visible next step) | Journey propulsion (Part 3.1 exit) | **Keep** — a landing that dead-ends is a dead end |
| Carousel / rotating banners | Poster logic (2.3 #1) | **Remove** — violates Charter §1 |
| Stats wall ("X events, Y participants") | Number-noise before identity | **Remove** — no user question answered at arrival |
| Full event list on the landing | Premature overload | **Absorb** — Landscape owns it (single source, Part 9) |

### 4.2 Landscape sections

| Section | Why it exists | Removed-test verdict |
|---|---|---|
| Cluster grouping (Stage/Mind/Art/Maker) | Guided choice, 16→4 narrowing (B2) | **Keep** — the choice engine |
| Event entries (name, cluster, status, link) | The store of choices (B1, B11) | **Keep** — the page's reason to exist |
| Status honesty (open/closed/full) | Decision honesty (B11) | **Keep** — dead-end prevention |
| Search/filter by cluster | Reduction for larger rosters | **Keep** (scalability — Part 12; minimal now) |
| Random "featured event" | Choice noise | **Remove** — unearned spotlight (One Last Rule) |
| Hero slogan repetition | Duplication of Welcome (Part 9) | **Absorb** — identity lives in Welcome |

### 4.3 Event Detail sections

| Section | Why it exists | Removed-test verdict |
|---|---|---|
| Personality intro (B3) | "Is this me?" | **Keep** — the emotional gate |
| Quick facts (B4) | Time-aware decisions | **Keep** — scannable truth |
| Eligibility (B6) | Can-I gate | **Keep** — doubt removal |
| Rules, faithful (B7) | The contract | **Keep** — never summarized away |
| Judging criteria (B8) | Fairness promise | **Keep** — trust |
| Things to bring (B9) | The #1 repeated question | **Keep** — parent/coordinator logistics |
| Event FAQ (B10) | Absorbed questions | **Keep** — content evolves, structure fixed |
| Register action + status (B11, B12) | The doorway | **Keep** — the page's climax |
| Share buttons (D5) | Exit for sharing | **Absorb** into quiet corners — one share presence, not per-page noise |
| "Similar events" suggestions | Choice noise after decision | **Remove** — dilutes confidence (Part 17) |

### 4.4 Registration sections (structure only — mechanics placeholder)

| Section | Why it exists | Removed-test verdict |
|---|---|---|
| Step declaration (where am I, what remains) | Surprise-free (10.3) | **Keep** — the doorway's promise |
| Ask-and-why (each field explained) | Trust at the ask | **Keep** — no silent asks |
| Review & confirm beat | The final mirror | **Keep** — the act's punctuation |
| Payment block | Money moment (C3) | **Keep (placeholder)** — released only when payment exists (15.4) |
| Live "why this is being asked" tooltips | Declared steps make them redundant | **Absorb** — into Ask-and-why |

### 4.5 Your Space sections

| Section | Why it exists | Removed-test verdict |
|---|---|---|
| What changed since last visit (C7) | The return engine (12.2) | **Keep** — the page's reason to exist |
| My registrations (C5) | The record | **Keep** — the receipt lives here |
| Announcements (D1) | Source of truth | **Keep** — WhatsApp alternative |
| Next beat per season (G1) | Orientation in time | **Keep** — time architecture (Part 21) |
| Public content mirror (event lists, rules) | The platform repeats itself | **Remove** — single source; link to public areas instead (Part 9) |

### 4.6 Quiet corners sections

| Section | Why it exists | Removed-test verdict |
|---|---|---|
| Host / dates / venue (A4–A6) | Logistics trust | **Keep** |
| Contact route (A7, E2) | The doubt-home | **Keep** — only if real (Q12); else honest placeholder |
| Global FAQ (E1) | Cross-event questions | **Keep** |
| Privacy note (E3) | Student-data trust | **Keep** |
| Sponsors block (D6) | Credibility | **Keep as future (F)** — only when sponsors exist (Q15) |
| Social links (D5) | Conversation exits | **Keep as future (F)** — only when channels exist (Q16) |

**Section verdict:** 28 sections reviewed; 21 kept, 7 removed or absorbed. Every survivor names a user problem it solves; every removal names the constitution it violated.

**Trace:** Phase 1 Part 12 (blacklist); Phase 1.5 Part 9 (EVOKE Test) + One Last Rule; Phase 2 Parts 7, 10, 12, 15, 17, 20, 21.

---

## PART 5 — Content Relationships

How content objects connect — the single-source rules that prevent contradiction, duplication, and drift. **One fact, one home; everything else links.**

### 5.1 Ownership map (one fact → one owner)

| Fact | Owner | Everyone else |
|---|---|---|
| Festival dates (A5) | Quiet corners (3.9) | Welcome states them (derived), Your Space links |
| Event list (B1) | Landscape (3.2) | Everywhere else links to it |
| Event rules (B7) | Event Detail (3.3) | Rules & Eligibility summarizes general rules only (C1), never repeats per-event text |
| Registration status (B11) | Derived from admin state (F2/G1) | Displayed in Landscape + Detail, computed — never hand-typed |
| Announcements (D1) | Admin publishes (F3) | Your Space + Welcome (latest) display, never restate |
| Schedule (D2) | Schedule page (3.8) | Event Detail links during approach season |
| Contact (A7/E2) | Quiet corners | Every "contact" affordance links here |
| Per-event FAQ (B10) | Event Detail | Global FAQ (E1) links, never duplicates answers |
| Gallery/Winners (D3/D4) | Post-event areas (3.10) | Silent until content exists (F) |

### 5.2 Relationship rules

1. **One fact, one home.** No fact is restated with independent wording. Derived displays (status, dates) are computed or clearly secondary.
2. **Links over copies.** Where two pages need the same truth, one owns it and the other links. (Welcome→Landscape→Detail is the spine; quiet corners are the branches.)
3. **No sibling contradictions.** Event Detail's rules and Rules & Eligibility's general rules must never disagree — Rules & Eligibility covers only C1 and points to B7.
4. **Season-aware edges.** Relationships change by season (G1): pre-event, Detail links to Registration; approach, Detail links to Schedule; live, Detail links to post-event results. The link edges move, the owners do not.
5. **Placeholder edges.** Where a relationship target is TBD (payment, schedule), the edge exists with an honest "coming from the organizer" posture (Part 11) — never a fake value.
6. **The chain of trust.** Doubts raised at any beat are one hop from their answer: Detail → FAQ/Contact; Landscape → Detail; Welcome → Landscape or Quiet corners. No doubt is more than one hop away (Part 10 Dead End Audit).

**Trace:** Phase 2 Parts 7, 12, 15; Phase 0 6.2, 12.5; Charter §7.

---

## PART 6 — Navigation Logic

Not navigation *design* (that is Phase 3) — the **philosophy of movement**: how a visitor finds their way, never panics, never dead-ends, and always knows their next beat. Conformance to Phase 2 Parts 8 (attention), 12 (entry/exit/re-entry), 14 (recovery).

### 6.1 Movement principles

1. **Progress before breadth.** The platform's only imperative is forward progress toward the act. Privileged edges are the spine edges (Welcome→Landscape→Detail→Registration→Confirmation).
2. **One hop to every answer.** Every doubt a visitor can raise is at most one hop from where it was raised (5.2 #6). Breadth exists only as *branches of truth*, never as parallel worlds.
3. **The path is never lost.** At every beat, the visitor knows: where they are, where they came from, where they can go, and why they would. Orientation is a feeling — Phase 2 Part 8.1 — not a widget count.
4. **Recovery over error.** Interruption is normal; loss is not. Abandoned registrations resume; tucked pages are reachable from the chain of trust (Part 10).
5. **No traps, no tricks.** No dark patterns, no pressure (Phase 2 Part 17, Part 20). The platform never hides its status, never makes "leave" hard.
6. **Placeholders are honest doors.** A TBD area links to its own honest posture (Part 11) or is not a link at all (Part 10).

### 6.2 The orientation contract (per beat)

Recalculated from the same principles at every beat (Phase 2 Part 8.1):

- **What is this place?** (area identity, always present)
- **Where did I come from / how do I get back?** (one quiet retreat edge, always available; the Back beat)
- **What is my next step?** (the forward motion; never two competing "primary" steps)
- **What happened since I was here?** (return visits — season-aware, Part 21)

### 6.3 Kindergarten/simple-side support

- **Primary rails:** one primary forward rail per area; forward beats exist in exactly one place each page.
- **The doubt brake:** any doubt stops forward motion; the next natural beat is a circle of trust (Events / Rules / FAQ / Contact).
- **Exits:** every page has exactly one graceful exit for its audience (back, or leave-to-context; never a dead stop).

### Conformance audit (Phase 2 tracing)

| Principle | Phase 2 authority |
|---|---|
| Progress before | 7 (release), 9 (decision tree) |
| One hop out | 15 (trust architecture) |
| Path never lost | 8.1, 8.3 (attention, status) |
| Recovery | 14 (failure journeys) |
| No traps | 17 (trust), 20 (silence) |

**Navigation verdict:** satisfied; every principle names the calm, confident, non-anxious move. No principle has been invented beyond Phase 2.

**Trace:** Phase 2 Parts 7, 8, 9, 14, 15, 20, 21.

---

## PART 7 — Progressive Confidence Validation

The core of the product (Charter §4, Phase 2 Parts 7, 10, 15): every page and every step exists to move the participant up the confidence curve — **Uncertainty → Orientation → Understanding → Decision → Commitment → Anticipation → Fulfillment/Recovery.** Each beat must validate the curve, and if it fails the validation the beat is a defect.

### 7.1 Confidence-curve validation table

| Curve stage | Stage question ("I...") | Validating beats | Structural validation |
|---|---|---|---|
| Uncertainty | "...don't know what this is" | Welcome identity beat (3.1) | Answers "what is EVOKE, what can I do here" → PASS |
| Orientation | "know what I can do" | Landscape (3.2) + cluster tags | Offers all 16, reduces choice — PASS |
| Structure | "know my options well enough" | Event Detail (3.3) | Answers B3–B12 = the full doubt catalog → PASS |
| Decision | "feel I can choose" | Registration doorway (3.5) | Declares steps, asks nothing surprising → PASS |
| Commitment | "I trust this enough to do it" | Review-after act (money beat, C3) | Trust placed at keeping guarantees (15.1–15.4) → PASS |
| Anticipation | "I'm part of this, I know what happens next" | Confirmation (3.6) + Your Space (3.7) | Record + next beat → PASS |
| Fulfillment | "this kept its promise" | Post-event (3.10 — future) | Memorial + magnet → PASS (structure; content F) |

Every stage is validated by structure: the visitor is always shown the next beat that moves confidence upward — the platform never asks for commitment before it has paid out orientation and understanding.

### 7.2 Where confidence can DROP (and how the structure defends)

| Drop point | Threat | Defense |
|---|---|---|
| Status silence (reg closed but page silent) | Trust | Season honesty beat (4.1) |
| Rules contradiction (Detail vs Rules page) | Trust | Single-source ownership (5.1) |
| Surprise field mid-registration | Confidence | Declared steps (10.3) |
| Dead-end ("contact us" with nothing) | Trust | Part 10 audit + honest placeholder |
| Registration flow loss on interrupt | Confidence/commitment | Recovery edges (6.1 #4) |

Fundamental safety note: no process can build confidence while the facts it promises remain unknown — every TBD placeholder is an honest reason for the *structure* to exist now and the *fact* to appear later (Part 11).

### 7.3 Result

- Progressive confidence contract fulfilled.
- All seven curve stages name a validating beat pair — no empty stage.
- Failure points covered by the drop-defense table.
- Nothing in this part exceeds the Charter/Phase 2 contract — validation, not design.

**Trace:** Charter §4; Phase 2 Parts 6, 7, 9, 10, 15, 18, 21.

---

## PART 8 — Content Timing Audit

Release-by-**when**, not by *where* (Phase 2 Part 7): every content object is audited for *when in the season* and *when in the journey* it may first appear. Early release costs trust (promises before structure); late release costs confidence (a doubt answered too late).

### 8.1 Season timing table (what may exist when)

| Season (G1) | May exist (public) | May exist (registered) | Must NOT exist yet |
|---|---|---|---|
| Announcement | Identity (A1–A3), Landscape (B1–B2), Event Detail (B3–B10 for all), Rules & Eligibility (C1), Quiet corners static, honest season state | — (no auth yet) | Status, Schedule, Registration, Gallery/D4 |
| Registration open | + per-event status (B11), Registration doorway (B12, C2–C5) as resolved | Your Space identity, Confirmation (C5), Announcements (D1) | Schedule with times, judging outcomes |
| Approach | + Schedule (D2) as resolved | + full Your Space, approach checklist (B9 reconfirmation) | Unreleased judging results |
| Live | + (nothing new public) | Changes-to-what (C7), reminders | Off-season duplication |
| Post | Gallery (D3), Winners (D4) — only with content (F) | + Memorial beat | Anything from "next edition" (F/G2) |

### 8.2 Journey-position table (first appearance)

| Object | First appears at | Late if... | Early if... |
|---|---|---|---|
| Festival identity (A1–A3) | Welcome | absent at arrival | — |
| All 16 events (B1–B10) | Landscape/Detail | closings before details | Events public before platform exists |
| Status (B11) | Once registration exists (or honest "opening soon") | silent when flows open | Status implied without truth |
| Registration steps (C2–C4) | Event Detail → doorway | steps discovered mid-flow | steps detailed before readiness |
| Payment facts (C3) | Money beat only | unanswered at payment | fees published before (15.4) |
| Schedule (D2) | Approach season | approach without schedule | calendar promises pre-announcement |
| Results/Gallery | Post-event | memorial silenced | promo-before-evidence |

### 8.3 What "too early" and "too late" each cost

- **Early:** promise without structure (Phase 2 Part 7) — trust deficit, "this is vaporware," deadline pressure.
- **Late:** a doubt asked and not answered at the moment it's cheap to answer — confidence cost, preventable contact/support load.

### 8.4 Timing verdict

- No object is scheduled for release before its beat; placeholders (Part 11) hold the space without leaking the promise.
- The only content with complete freedom is Identity — permitted to speak first and always (it is the honest minimum).
- Every "must NOT exist yet" cell is enforced structurally by Season state (G1) + Phase (M/O/P/F), not by discipline.

**Trace:** Phase 2 Part 7 (WHEN not WHERE), Part 21 (time architecture), Part 15.4 (money moment); Phase 0 5.5, 12.5.

---

## PART 9 — Duplication Audit

Every object's home is unique; wherever a fact could appear twice, ownership decides and links replace copies (Part 5). This audit walks each duplication risk we know can appear and rules on the copy.

### 9.1 Known duplication risks → verdict

| Risk | Where | Verdict |
|---|---|---|
| Event list on Landscape AND Welcome | Welcome hero | Welcome links to Landscape; Landscape owns B1 |
| Rules on Event Detail AND Rules page AND FAQ | B7 | Detail owns per-event text; Rules page owns C1 general; FAQ never restates rules |
| Registration status typed by hand | Landscape, Detail, Your Space | Computed from admin state (F2/G1) — one source |
| Contact A7 in footer AND Contact page AND FAQ | Any | One owner (Quiet corners/A7); every affordance links |
| Announcements on Welcome AND Your Space AND WhatsApp | 3 surfaces | Announcements owned by admin (D1); pages display, never restate (distinct: display of the same fact is fine; paraphrased retype is duplication) |
| FAQ: event-level (B10) vs global (E1) overlap | Detail, FAQ | Rule: event-specific → B10; cross-event/parent → E1; E1 links to B10, no re-answer |
| Schedule shown in Detail AND its own page | Detail, Schedule | Ownership at Schedule (3.8); Detail links during approach — only link, no re-layout of data |
| Sponsor/social links everywhere | Quiet corners vs. pages | Single social block lives in Quiet corners (F); no per-page repeats |
| Per-event judging criteria restated in Landscape tiles | tiles | Landscape tiles carry only name/cluster/status (Part 4.2) — no criteria |

### 9.2 The display rule
"Displaying the same single-source fact in a second place is not duplication — hand-restating it is." The platform computes or pulls; it never types a second copy (risk list — only those two forms above are safe).

### 9.3 Checklist gate for any future copy
For any new content prompt: 1) Which inventory object owns this fact? 2) Is the new copy a pull of that fact or a restatement? 3) If restatement — delete it, link instead. Pass all three → allowed. Else → not.

**Duplication verdict:** single-source rule with a named owner per fact; 8 risks reviewed, no copy currently duplicated.

**Trace:** Phase 2 Part 7 (single-source under concentration), Part 12.2; Phase 0 6.2.

---

## PART 10 — Dead End Audit

A dead end is any point where a visitor cannot proceed, cannot retreat, or reaches a link whose destination has no value. Phase 2 Part 14 (failure journeys) demands recovery; Part 10 of this document enforces it structurally — every dead end has a named recovery, and any dead end without one is removed.

### 10.1 Dead-end candidates → recovery verdict

| Candidate dead end | When it happens | Recovery (named) | Verdict |
|---|---|---|---|
| "Contact us" with no contact | Q12 unresolved | Honest placeholder: "Contact details from organizer shortly — reachable via [school admin] meanwhile" only if real; else the affordance is not published | **Recovered if honest, else removed** |
| Registration door when closed | Post-closing visit | Honest season state + the next reality ("closed for this edition") + path to Your Space if registered | Recovered |
| Login door (Your Space) for anyone | Auth unresolved (C6 placeholder) | Structure gates Your Space behind value, not before; no auth link until value exists | Recovered by timing |
| Interrupted registration flow | Session break | Resume path (recovery key, Phase 2 Part 14); the lost-flow error is never the final screen | Recovered |
| Schedule during announcement | Too early timing | Not published (Part 8) — timing, not dead end | Removed by timing |
| Gallery/Winners/Sponsors before content | F objects | Not built until content (F-gate); no empty "coming soon" | Removed by gate |
| Dead tab / empty FAQ | Content not written | FAQ hides unanswered (no empty headers); unanswered questions fold into Contact route | Recovered |
| Wrong-selection corner (student on wrong event page) | Choice doubt | Back-to-list + "which cluster is mine" re-orientation | Recovered |
| Payment failure mid-flow | Money event drops | Named recovery: honest failure state + resume + Contact (doubt-home) | Recovered |
| Confirmation lost (browser close) | Post-payment | Retrievability contract (3.6): record reachable/printable/redo-able | Recovered |

### 10.2 The four recovery routes — one of them is triggered at any dead end

1. **Route back** — to the referencing context (the Back beat).
2. **Route around** — to the honest next reality (season state / status) instead of a static wall.
3. **Route out** — to the doubt-home (Contact / Global FAQ).
4. **Route later** — the deferred reality is postponed honestly (Part 11), never faked.

### 10.3 Survivor rule

A destination survives Phase 2.5 only if: real content (M), honest placeholder (P), or a real future object (F) with an honest door. Anything else is a dead end and is *removed* before Phase ∞.

**Dead end verdict:** 10 candidates, 8 named recoveries, 2 removed by timing/gate, none survivorless.

**Trace:** Phase 2 Part 8.3, 12, 14; Phase 0 12.5; Charter §7.

---

## PART 11 — Placeholder Strategy

The platform must be buildable **now** with facts that arrive **later** (Charter §7: registration flow, payment flow, gateway, fees, team rules, confirmation; Phase 0: Q1 dates, Q2 venue, Q4 registration model, Q5 eligibility, Q8 fees, Q12 contact, Q13 logo, Q14 gallery, Q15 sponsors, Q19 host). The rule: **never invent a value; never ship a fake.** Every placeholder has a posture and a state.

### 11.1 Placeholder postures (what a TBD fact looks like to the user)

| Posture | When used | Example |
|---|---|---|
| **Honest wait** | Fact expected, timing open | "Venue: announced with the schedule — soon after registration opens" (Q2) |
| **Honest deferred** | Fact gated by a later beat | Fees: no fee text until the payment beat (15.4); "Fees, if any, will be stated at registration" (Q8) |
| **Structure-only** | The fact's *shape* is real, value TBD | Schedule exists as area; times appear at approach (D2) |
| **Quiet gap** | Object not yet due; no link, no noise | Gallery (D3) — absent, not "coming soon" |
| **Interim authority** | A real interim answer exists | Contact = organizer's WhatsApp if given; otherwise quiet gap, never invented (Q12) |
| **Prohibited: fake value** | Any time | "Starts at 9 AM" with no source — forbidden |

### 11.2 Placeholder states machine

```
TBD ──organizer answers──▶ RESOLVED (M, replaces posture)
TBD ──season arrives─────▶ REMAINS TBD ──▶ surface honestly (posture), never fake
TBD ──object not due─────▶ QUIET GAP (F)
```

### 11.3 The anti-invention checklist (every TBD, every time)

1. Is this fact in the MISSING list (Q1–Q22) or Charter §7? If yes → placeholder.
2. Is a posture chosen (11.1)? If no posture can be named, the object is Quiet Gap — remove from view.
3. Does any copy state the value as fact? Rewrite to posture.
4. Does the structure depend on the value? If yes → refactor (structure is value-independent by design, Part 2.5).
5. After release: does the placeholder leak a promise ("shortly", "very soon")? Strip time promises — honest wait ≠ committed wait.

### 11.4 Placeholder register (current, as of this phase)

| Object | Placeholder | Posture |
|---|---|---|
| A4 host, A5 dates, A6 venue, A7 contact, E2 contact route | Q19, Q1, Q2, Q12 | Honest wait / interim authority (if real) / quiet gap (if none) |
| B6 eligibility, B12 requirements, C1 quota | Q5, Q10 | Honest wait; rules faithful where rulebook already speaks |
| C2 flow, C3 payment, C4 fields | Charter §7 | Honest deferred; declared-steps contract stands (3.5) |
| C5 confirmation, C6 identity, C7 dashboard | Charter §7 (auth TBD) | Structure-only; gates by value (10.1) |
| D2 schedule | Q6 | Structure-only; approach-timed (8.1) |
| D3–D6 gallery/winners/social/sponsors | Q14–Q16 | Quiet gap until content (F-gate) |

**Placeholder verdict:** every TBD has a named posture; no fake value exists in the architecture; the structure is value-independent by test (Part 2.5).

**Trace:** Charter §7; Phase 0 Q-list; Phase 2 Parts 7, 14, 15.4.

---

## PART 12 — Scalability Review

The architecture must survive three realistic growth axes without redesign (Phase 0 §12.13: 100 events · 1000 participants · 50 schools — and editions 2K27+).

### 12.1 Growth axes → structural answer

| Axis | Today | Growth | Structural answer |
|---|---|---|---|
| Events | 16 | 100 | Clusters generalize (4→N tags); Landscape paginates/derives filters (search is already structurally present, 4.2); Event Detail contract is per-event — scale-free |
| Participants | 100s | 1000+ | Registration is data capture, not UX novelty; Your Space renders per-participant — contracts scale; performance is an implementation concern, not structural |
| Schools | dozens | 50+ | Coordinator path (Rules & Eligibility, quotas) is a stable contract; school-level grouping is admin-domain (F2 export), not participant-facing |
| Editions | 2K26 | 2K27+ | Season state (G1) + edition key (G2) mean the platform rolls over by configuration, not by rebuild; post-event area re-arms for the new season (3.10) |
| Languages/accessibility | 1 | 2+ | Content contracts are single-fact-per-home — localization swaps values, not structure (note for Phase 3, not new design) |

### 12.2 What grows by repetition, what by hierarchy

- **Repetition:** event tiles, FAQ items, announcements, schedule rows, gallery items — contracts are per-item; N items cost nothing structurally.
- **Hierarchy:** clusters (B2), admin areas (F1–F4), season states (G1) — these are enumerated, not per-item; any growth is configuration, not architecture.

### 12.3 Stress test: the three numbers

- **100 events:** landscape filters + cluster tags keep choice reduction intact (4.2 keep-set holds).
- **1000 participants:** registration is the same declared-steps flow per participant; admin export scales; no participant-facing list ever renders 1000 rows.
- **50 schools:** coordinator content is static contracts (C1); per-school data lives only in admin exports (F2).

### 12.4 What does NOT scale and why it's fine

- The 11-page set is deliberately small and fixed — scale lives in *content volume* (lists, FAQs), not *page count*. If a future need adds a page, the Page Contract process (Part 3) applies with the Golden Question gate.

**Scalability verdict:** PASS under 100/1000/50 and edition rollover, by configuration not redesign.

**Trace:** Phase 0 5.2.12, 12.13; Phase 2 Part 21 (time), Part 3.3 (reduction).

---

## PART 13 — Developer Handoff (pre-wireframe knowledge base)

What a developer must know *before* Phase 3 (wireframes) — so that no assumption is imported from outside the constitutions. Intended stack (Charter §6): HTML, CSS, JavaScript, Python, Supabase.

### 13.1 The knowledge package (all settled here, not by the developer)

| Area | Settled knowledge |
|---|---|
| Product | It is a **participant & registration platform**, not a promotional site (Charter §1). One decisive act: choose + register (Part 2.1). |
| Pages | Exactly 11 public/admin contracts (Part 3). No new page without the Part 3 process. |
| Facts | One home per fact (Part 5); display-only vs restatement rule (Part 9.2). |
| States | Season state (G1) drives what may exist when (Part 8); status is computed, never typed (F2/G1). |
| Auth | Participant auth = placeholder (C6); admin auth separate (3.11); nothing gates browsing (2.3 #6). |
| Placeholders | Value-independent structure (Part 11); postures over fake values. |
| Data model | Content objects = inventory A–G (Part 1); relationships = ownership map (5.1); admin export (F2). |
| Errors | Recovery routes (10.2), never error-dead-ends (Part 14 Phase 2). |
| Stack | HTML/CSS/JS (front), Python (logic/backend), Supabase (data/auth — admin at minimum) — per Charter §6. |

### 13.2 Explicit non-assumptions (the developer must NOT assume)

1. No fees/payment amounts — payment beat is a placeholder (C3).
2. No registration model (individual/team quota) — placeholder (C4, Q4).
3. No dates/venue/contact as facts — placeholders (Q1, Q2, Q12).
4. No visual design decisions — this phase decides nothing visual (Phase 3 owns it).
5. No per-school custom flows — coordinator content is static contracts (12.3).
6. No "login to see anything" — browsing is free (2.3 #6).
7. No 2K25/2K26 conflation — 2K25 appears only in rulebook quotations (Charter §2).

### 13.3 What the developer CAN build today, without any TBD

- All 11 page shells per contracts (empty-state safe by Part 8 timing).
- The season-state machine (G1) + computed status (B11).
- The single-source content structure (A–F objects) with placeholder postures (11.4).
- Admin content management + announcement publishing (F1, F3).
- The confirmation record structure with retrievability (C5, 3.6).

**Handoff verdict:** a developer holding only this document + the constitutions has everything needed to start Phase 3 without inventing a single value.

**Trace:** Charter §6; Phase 0 Q21, risk 9; Phase 2 Part 14.

---

## PART 14 — Final Gatekeeper Review (the owner's acceptance)

The constitution-owner (human + ChatGPT) reviews the structural architecture before any wireframe. Five questions gate Phase 3 — each must be answered with evidence from this document, not from memory.

### Gate questions (owner must pass all five)

1. **Does every page exist because a user need is unanswered without it?** Evidence: Part 3 contracts — 11 pages, each with a named Purpose and audience; Part 4 removal tests.
2. **Does every user question have a home that is reachable in one hop?** Evidence: Part 6.1 #2 (one hop rule) + Part 5.2 #6 (chain of trust) + Part 10 recovery routes.
3. **Is nothing invented that the constitutions did not already warrant?** Evidence: every Part traces to Phase 0/1/1.5/1.75/2 lines; Part 7.3, Part 6 verdicts explicitly state "no new concept".
4. **Does the structure survive all TBD outcomes without redesign?** Evidence: Part 2.5 (thin-shell test), Part 11.3 #4 (value-independence), Part 12 (scalability).
5. **Is the platform still thin?** Evidence: Part 2.3 structural blacklist (8 removals), Part 4 (7 sections removed/absorbed), Part 10 (2 removed by gate) — removal is this phase's favorite verdict.

### Review protocol

- Owner reads Parts 1–13 once, in order, against the five constitutions.
- Any "no" → the offending structure is named, removed or re-justified in writing, and this phase is re-committed (not silently amended).
- All "yes" → the Readiness Report (Part 15) is signed and Phase 3 (Wireframe Architecture) may begin.

---

## PART 15 — Readiness Report

### 15.1 Part-by-part scorecard

| Part | Verdict | Evidence |
|---|---|---|
| 1 Master Content Inventory | PASS | 46 objects, every one traced; no orphan, no unjustified |
| 2 Product Structure | PASS | 12 areas, 8-item structural blacklist, thin-shell stable under TBD (2.5) |
| 3 Page Contracts | PASS | 11 contracts with purposes, audiences, states, exits |
| 4 Section Contracts | PASS | 28 sections: 21 kept / 7 removed-or-absorbed, each with a named problem |
| 5 Content Relationships | PASS | Ownership map (one fact one home), 6 relationship rules |
| 6 Navigation Logic | PASS | 5 principles + orientation contract, all Phase 2-traced |
| 7 Progressive Confidence Validation | PASS | 7 curve stages × validating beats; drop-defense table |
| 8 Content Timing Audit | PASS | Season + journey timing tables; early/late costs named |
| 9 Duplication Audit | PASS | 8 risks ruled, single-source display rule stated |
| 10 Dead End Audit | PASS | 10 candidates, 8 recoveries, 2 removed; survivor rule |
| 11 Placeholder Strategy | PASS | 6 postures, state machine, anti-invention checklist, register |
| 12 Scalability Review | PASS | 100 events / 1000 participants / 50 schools / editions |
| 13 Developer Handoff | PASS | Knowledge package + 7 non-assumptions + buildable-now list |
| 14 Gatekeeper Review | PENDING | Owner's five questions — this report awaits signature |

### 15.2 The verdict this phase asks of the owner

**Is the structural architecture ready for Phase 3 (Wireframe Architecture)?**

- Recommended answer: **YES** — with evidence: 13/14 parts PASS with trace to constitutions; the 14th (Gatekeeper Review) is the owner's signature, and the only open items are TBD facts that the architecture is built to survive (Part 11.4).
- **NO** — would be returned with the naming of the offending structure (review protocol, Part 14).

### 15.3 Final word — the thinness guarantee

The single most important outcome of this phase is not what the platform *contains*, but what it *does not*: no promotional banners, no news blog, no login walls, no fake values, no dead ends, no duplicated facts, no unearned pages. What remains is a thin, honest, confident structure — the exact shape the participant journey promised in Phase 2.

*End of Phase 2.5 — Structural Architecture. On approval, Phase 3 (Wireframe Architecture) begins with this document as its only map.*
