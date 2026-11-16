# Startup Singam — OpenHands Build Pack

Everything needed to have OpenHands build the complete Startup Singam platform from `Startup_Singam_2__1_.xlsx`.

## Contents
| Folder | What |
|---|---|
| `docs/` | Nine spec files: overview, personas & permissions, domain model, workflows, shared data & live sync, UX, dashboards, architecture, assumptions/open questions |
| `prompts/` | A master prompt + 15 phase prompts, each self-contained with goal, scope, tasks, acceptance criteria and tests |
| `AGENTS.md` / `.openhands/microagents/repo.md` | Always-on rules OpenHands loads for the repo |

## How to run it
1. Create an empty repo. Copy this pack in (keep `docs/`, `prompts/`, `AGENTS.md`, `.openhands/`). Also add `Startup_Singam_2__1_.xlsx` under `docs/source/`.
2. Add your design tokens/components to the repo (or tell phase 0 where they are). This pack never specifies colours/typography.
3. In OpenHands, paste `prompts/00_MASTER_PROMPT.md` once.
4. Then run phase prompts **in order**, one OpenHands session each (or sequentially in one): `P01 → P15`. Do not start a phase until the previous phase's acceptance checklist passes.
5. After every phase, review `docs/PROGRESS.md` the agent maintains.

## Phase map and dependencies
| Phase | Prompt | Depends on | Delivers |
|---|---|---|---|
| P01 | Foundation | — | Monorepo, DB, auth shell, CI |
| P02 | Identity, RBAC, policy engine, audit | P01 | Roles, visibility layer, redaction, label_map |
| P03 | Domain schema + state machines | P02 | Full schema, commands, seed |
| P04 | Workflow engine, clocks, events, realtime, notifications | P03 | T1–T19 triggers, SSE, working days |
| P05 | Super admin: policies, season, users, approvals | P04 | Approvals inbox, reassignment |
| P06 | Founder portal A + SR (stages 0–5) | P05 | Profile → fit check, SR workspace, Analyst workspace |
| P07 | MoU, Legal, IRR/Finance | P06 | Stages 6–7 end to end |
| P08 | Investor portal A + IR (onboarding) | P05 | Stages 0–4, verification, grading, allocation |
| P09 | Matching, pitches, Pitch Day, committee | P07, P08 | Stages 5–9 (investor), 8–10 (founder) |
| P10 | Upfront fee, Finance, Production handover & shoots | P09 | Stages 11–14 |
| P11 | Deals, DD, tranches, success fee, reconciliation | P10 | Stages 16–18 / investor 12–13 |
| P12 | Marketing & Community | P10, P11 | Telecast, announcements, community |
| P13 | Dashboards | P12 | All role dashboards |
| P14 | Cross-cutting UX, notifications, search, a11y | P13 | Polish |
| P15 | Hardening, e2e, security, release | P14 | Release candidate |

## Ground rules baked into every prompt
- Shared database, projections not copies, live two-way updates governed by permissions.
- Spreadsheet is the source of truth; gaps follow `docs/09_OPEN_QUESTIONS.md`.
- Each prompt ends with an acceptance checklist the agent must self-verify and report.
