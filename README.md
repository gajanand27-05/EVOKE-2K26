# EVOKE 2K26 — Participant & Registration Platform

Repository for the EVOKE 2K26 registration and participant experience platform — the annual inter-school festival.

**Tagline:** *"Bring out the best in You."*

> Work in progress — planning phases are complete through Phase 3; no implementation code exists yet. Tasks are delivered via ChatGPT-generated prompts and executed step by step by agents (see `docs/ROADMAP.md` for the phase roadmap).

## What this platform is

A **registration and participant experience platform** for an inter-school festival of 16 events — not a promotional website. Its job is to help a participant discover events, understand the rules, register with confidence, and stay informed. See `docs/PHASE-1-75-PRODUCT-CHARTER.md`.

## Documentation

**The constitutions** (immutable — later phases may not contradict them without written justification and approval):

| Document | What it fixes |
|---|---|
| [`docs/PHASE-0-DISCOVERY.md`](docs/PHASE-0-DISCOVERY.md) | Discovery: audiences, all 16 events, risks, open questions, 14 non-negotiable principles |
| [`docs/PHASE-1-BRAND-BIBLE.md`](docs/PHASE-1-BRAND-BIBLE.md) | Brand identity, colour and typography roles, the 60-item Blacklist, 24-principle Design Constitution |
| [`docs/PHASE-1-5-CREATIVE-REVIEW.md`](docs/PHASE-1-5-CREATIVE-REVIEW.md) | The signature language ("The Unveiling"), visual grammar, motifs, motion architecture, the EVOKE Test |
| [`docs/PHASE-1-75-PRODUCT-CHARTER.md`](docs/PHASE-1-75-PRODUCT-CHARTER.md) | Product purpose, the 9-step participant journey, Progressive Confidence, the 4-question decision filter |

**The working specifications:**

| Document | What it fixes |
|---|---|
| [`docs/PHASE-2-EXPERIENCE-DIRECTION.md`](docs/PHASE-2-EXPERIENCE-DIRECTION.md) | How a participant *experiences* the platform: five acts, curiosity curve, cognitive load, registration psychology, failure and recovery, trust |
| [`docs/PHASE-2-5-STRUCTURAL-ARCHITECTURE.md`](docs/PHASE-2-5-STRUCTURAL-ARCHITECTURE.md) | Content inventory (43 objects), 11 page contracts, section contracts, single-source ownership, dead-end audit, placeholder strategy |
| [`docs/PHASE-3-INTERFACE-ARCHITECTURE.md`](docs/PHASE-3-INTERFACE-ARCHITECTURE.md) | 34 screens, 54 components, responsive behaviour, state machines, 106 accessibility rules, form architecture, developer and designer contracts |

**Process:**

| Document | Purpose |
|---|---|
| [`docs/ROADMAP.md`](docs/ROADMAP.md) | Canonical phase roadmap, constitutions, intended stack |
| [`docs/APPROVALS.md`](docs/APPROVALS.md) | Which phase gates have been signed — all currently open |

## Status

| Phase | State |
|---|---|
| 0 · 1 · 1.5 · 1.75 — Constitutions | Complete |
| 2 — Experience Direction | Complete, owner gate open |
| 2.5 — Structural Architecture | Complete, owner gate open |
| 3 — Interface Architecture | Complete, owner gate open |
| 4 — Visual & Motion Design | Not started |
| 5 — Implementation | Not started |

**Intended stack (Phase 5):** HTML, CSS, JavaScript, Python, Supabase.

**Blocked on organizer information:** dates, venue, host school, contact, eligibility, quotas, fees, registration and payment model. These are held as honest placeholders throughout — never invented.
