# MASTER PROMPT — paste once at the start of the OpenHands session

You are building **Startup Singam**, a season-based startup–investor program platform, end to end. You will work through 15 phases defined in `prompts/P01…P15`. Do not skip ahead.

## Before writing code
1. Read, in order: `AGENTS.md`, `docs/01_PRODUCT_OVERVIEW.md` … `docs/09_OPEN_QUESTIONS.md`.
2. If `docs/source/Startup_Singam_2__1_.xlsx` exists, treat it as the source of truth over the docs.
3. Write `docs/PROGRESS.md` with: phase list (unchecked), decisions log, assumptions, open items.

## Product in one paragraph
Two external personas (Founder, Investor) and eleven internal roles (SR RM, Analyst, IR Manager, Finance + lead, Production coordinator + head, Legal, Marketing, Community, Super admin) operate on **one PostgreSQL database**. Internal actions update what external users see, and external actions update internal queues, in real time, filtered by a server-side visibility layer. Founder and investor stage names are **derived** from internal stages.

## Operating rules
- Build in vertical slices: schema → domain command → policy view → API → UI → realtime → tests.
- All writes via `packages/domain`; all reads via `packages/policy` views.
- Colours/typography are out of scope: reuse existing tokens/components.
- Every phase must finish with: green tests, updated seed data, updated `docs/PROGRESS.md`, and a short "acceptance report" listing each acceptance item as ✅/❌ with evidence.
- If blocked by an ambiguity, use the assumption in `docs/09_OPEN_QUESTIONS.md`, record it, and continue.
- Never weaken a visibility rule to make a test pass. Fix the test or the code.

## Definition of done for the whole project
- Every stage in the Founder journey (0–19) and Investor journey (0–15) works end to end with seeded demo data.
- Every workflow in each department sheet works, including all auto-triggers T1–T19 and clocks.
- All 20 two-way sync scenarios (S1–S20 in `docs/05`) pass as integration tests.
- All dashboards in `docs/07` exist with drill-down.
- Redaction/visibility test suite passes for every role pair.

Start with `prompts/P01_FOUNDATION.md`.
