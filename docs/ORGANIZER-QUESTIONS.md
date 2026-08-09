# EVOKE 2K26 — Questions for the organizing committee

*The single live list of what we need from you. Written to be sent as-is.*

| | |
|---|---|
| **Purpose** | Every question here blocks something concrete. Each one says what it blocks and what happens if it stays unanswered. |
| **Status** | Section A blocks work happening right now. Sections B and C can arrive later without stalling design. |
| **Source** | Phase 0 §10 (Q1–Q22) plus questions discovered by building the prototypes in Phase 4. |
| **Rule** | Nothing on this list will be guessed. Where an answer is missing, the platform says so plainly rather than inventing one. |

---

## Section A — blocking us now

Three questions. Everything else can wait; these cannot.

### A1. Is the person filling in the registration form always one of the participants?

**Plainly:** when a team of eight registers for Group Dance, is the person typing one of those eight — or could it be a teacher or coordinator who is *not* competing?

**Why it matters:** it changes what we collect. If the registrant is always a participant, the form asks for their details and then seven more. If a coordinator can register on a team's behalf, the form asks for the coordinator's contact details *and* eight participants — a different data model, not a different screen.

**What happens without it:** we may silently record a coordinator as a competitor, or lose one real participant from a roster. We have stopped work on the registration flow rather than guess.

*(Extends Phase 0 Q4. This is the one blocker.)*

---

### A2. How should a participant find their registration again later?

**Plainly:** a student registers today. In three weeks they want to check what they signed up for. What do they do?

**Options worth considering:**

| Option | What the participant does | Trade-off |
|---|---|---|
| **Reference number lookup** | Enters the reference we gave them, sees their registration | Simplest. No accounts, no passwords, nothing to forget beyond one code |
| **Contact lookup** | Enters the email or phone they registered with | No code to keep, but anyone with that contact detail can look it up |
| **Account with password** | Signs in | Most control, most friction, most to build and support |
| **No retrieval at all** | Relies on a confirmation message we send them | Least to build; participants who lose the message have nowhere to go |

**Our observation, not a decision:** the reference-number route would remove a large dependency from the build. It is your call, not ours.

**What happens without it:** we can issue a reference number at confirmation, but we cannot yet build the screen where someone uses it.

---

### A3. Can one student — or one team — enter more than one event?

**Plainly:** can a student do both Solo Song and Pencil Sketch? Can the same six people enter Group Dance and Group Song? Is there a cap per student or per school?

**Why it matters:** this is the single most common question a participant asks, and today the platform cannot answer it anywhere. It also affects whether registration is repeatable and how schedule clashes are handled.

**What happens without it:** the FAQ answers this with "to be announced", which is honest but unsatisfying at exactly the moment a student is deciding.

---

## Section B — needed before we build the database

Not urgent this week. Needed before implementation begins.

| # | Question | Blocks |
|---|---|---|
| **B1** | Which classes or grades may take part? Is there an age range? | Eligibility checks; the class field on every registration *(Phase 0 Q5)* |
| **B2** | The rulebook says "maximum 2 teams per class" for Group Dance and "maximum 2 teams per school" for G.K. Quiz. Do these still apply, and are there other limits? | Quota enforcement at registration *(Phase 0 Q10)* |
| **B3** | What information do you need recorded for each participant? Name and class, or more? | The registration form's field list *(Phase 0 Q22)* |
| **B4** | Is there a registration fee? If so, how should it be paid? | The payment step. Built as a placeholder that can accept your answer without redesign *(Phase 0 Q8, Charter §7)* |
| **B5** | Who is the official contact for participant questions? | Every "contact us" route. Currently unpublished, because a contact link with nothing behind it is worse than none *(Phase 0 Q12)* |

---

## Section C — needed before the platform goes public

Content, not architecture. The structure exists and is waiting.

| # | Question | Blocks |
|---|---|---|
| **C1** | **Are the 2K26 rules the same as the 2K25 rulebook we are working from?** If any event's rules, themes or team sizes have changed, we need the current version. | Everything. All 16 event pages are built from the previous edition's rulebook *(Charter §9)* |
| **C2** | Festival dates | Countdown, schedule, "registration closes" messaging *(Phase 0 Q1)* |
| **C3** | Venue | Logistics and directions *(Phase 0 Q2)* |
| **C4** | Which school or college is hosting | The About page and the footer *(Phase 0 Q19)* |
| **C5** | Four gaps in the rulebook: **Fashion Show** team size, and time limits for **Instrumental Music**, **Cooking Without Fire** and **G.K. Quiz** | Those four event pages show "not stated" where participants most want a number |
| **C6** | Judging criteria are given for only 6 of the 16 events. Are the others deliberately unpublished, or simply missing? | Ten event pages currently say criteria are not stated. If they are deliberately withheld, we will word it that way instead |
| **C7** | Do you have a logo, colours or photographs from previous editions? | Visual design (Phase 5) and the gallery *(Phase 0 Q13, Q14)* |
| **C8** | Are there sponsors, and social media channels to link to? | Sponsor and social areas, currently not built *(Phase 0 Q15, Q16)* |

---

## How answers get used

An answer arrives → it replaces a placeholder → the structure does not change. That is the point of the placeholder architecture: the platform is built to receive these answers, not to be rebuilt around them.

The only exception is **A1**, which affects the registration data model itself. That is why it is the one item blocking work.

## Log

| Date | Question | Answer | Recorded in |
|---|---|---|---|
| — | — | *No answers received yet.* | — |
