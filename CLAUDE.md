# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Repository Is

This is a **prompt engineering / AI agent design repository** — not a software codebase. It contains a collection of structured AI agent prompt files for orchestrating the design and development of a production-ready productivity + social gaming web product.

There is no code to build, test, or run. All files are Markdown prompt documents.

## Product Being Designed

A productivity tracker (goals / tasks / habits / day-week-month planning) with a social/game layer:
- Table-centric planning UX, achievements, internal currency, premium/subscription
- Friends, teams, PvP 1v1 and team battles (up to 3 players), sync/async PvP
- Matchmaking (±50 rating spread), rating from achievements/tasks/wins/placement
- PvE solo/co-op/global events, leaderboards, leagues (seasonal/permanent/hybrid)
- Anti-abuse/anti-fraud in MVP, seasons/events, admin/moderation
- Integrations: Google Calendar, Telegram, email, push, Notion
- **Tech stack**: React + TypeScript (frontend), Java + Spring Boot (backend), PostgreSQL, Redis
- **Architecture**: modular monolith — no microservices, no Kubernetes, no complex billing
- **Platform**: web first, mobile later; target market: СНГ

## Repository Structure

| Path | Role |
|------|------|
| `Master-Prompt-V4.md` | **Single source of truth** — full product blueprint, agent system, governance rules, constraints. Always V4. |
| `Master-Prompt-V3.md` | **Superseded.** Kept for diff/reference only. Do not use, do not edit, do not extend. |
| `AI-Agents-Constructor.md` | Operating model for the multi-agent system — orchestration, handoffs, governance. |
| `*-Agent.md` (root) | **V1** agent prompts, one per role from the Official Agent Catalog. |
| `improved/` | **V2** agent prompts (active migration target — see "V1 → V2 Migration" below). |
| `improved/_Agent-Base-Template.md` | Canonical V2 contract structure. All V2 agents must conform. |
| `agent_pipeline_waves.svg` | Visual diagram of agent execution waves/pipeline. |

## No Build / Test / Run

This is a Markdown-only repository. There is no package manager, no build tool, no test runner, no dev server. Do not look for `package.json`, `Makefile`, `pom.xml`, etc. — they don't exist and shouldn't be added. Validation of agent prompts is a **content review**, not a code check.

## V1 → V2 Migration (active)

`improved/` holds V2 versions that fix 10 systemic V1 problems documented in `improved/_Agent-Base-Template.md`. The most important shifts:

1. `Self-Check` moved to a **Pre-Output Gate** (runs *before* the final output, not after).
2. `Mandatory Artifact Header` is **instantiated locally** in each agent, not implicit-from-master.
3. `Peer Cross-Check` has a procedural output format: `MATCH | CONFLICT | NOT-CHECKED-MISSING-ARTIFACT`.
4. `Format` and `Decomposition` merged — single source of truth for output structure.
5. Local Context section dropped; agents reference master via **delta-only**.
6. The "3 critically important instructions" V1 trailer removed — its role is filled by `Stop-Condition` + `Constraints`.
7. Confidence labels have explicit placement — suffix in section heading: `## 3. <Title> *[confidence: high|medium|low]*`.
8. `Stop-Condition` synchronized with `Peer Cross-Check` (critical upstream missing → STOP; non-critical → `NOT-CHECKED-MISSING-ARTIFACT`).
9. Reasoning visibility rule lives only in master — not duplicated per-agent.
10. Specialist sub-persona has a **mandatory output block** format.

**Migration status (as of 2026-04-25):** all 20 catalog agents + `AI-Agents-Constructor` have V2 in `improved/`. When producing new V2 files (e.g. for a newly added agent), mirror the structure of any existing V2 (e.g. `Solution-Architect-Agent-V2.md`, `Backend-Design-Agent-V2.md`) and the rules in `_Agent-Base-Template.md` — do not invent new sections.

**When asked to edit an agent:** prefer editing the V2 in `improved/` if it exists. Edit the V1 only if explicitly asked, or if no V2 exists yet (and flag that V2 is missing).

## Agent System Rules (enforced by Master-Prompt-V4)

**Contract Hash**: `MP-V4-2026-04-25` — every agent must verify this before starting. Mismatch → STOP + `[Risk]`.

**Every agent output must include** (V1 contract — V2 reorders these into an `Output Header` block followed by a `Pre-Output Gate` that runs before final output):
- `Context Reference` header (master version, hash match, upstream inputs, local scope, out-of-scope, inherited assumptions, new assumptions, open questions, conflicts)
- `Peer Cross-Check Output` table — V2 only, status per peer artifact
- `Self-Check` / `Pre-Output Gate` (formal contract verification, not quality review)
- `Independent Review Hook` (reviewer agent, status, human approval status)

**Tags Glossary** (use these exactly — no silent assumptions):
- `[Assumption]` — unverified claim; must include what is assumed and how to validate
- `[Recommendation]` — must include: subject + action + owner-role + observable criterion
- `[Risk]` — must include: trigger + impact + mitigation owner
- `[Later]` — deferred; must include trigger condition for return
- `[Open Question]` — must include owner and deadline

**Stop-Condition Protocol**: If required upstream artifacts are missing or Contract Hash doesn't match → STOP, ask exactly 1 clarifying question, do not fabricate peer-artifact content.

**Independent Review**: Self-review is forbidden as quality check. Each agent has an assigned Reviewer-agent. Artifacts are `NOT-MERGED` until reviewer issues PASS / PASS-WITH-ISSUES / FAIL.

**Mandatory Human Approval** required for: fairness/anti-abuse decisions, monetization/pricing, architecture-impact ADRs, any FAIL or SCOPE-CREEP signal. Without approval → `Status: PRELIMINARY`.

## Official Agent Catalog (from Master-Prompt-V4)

20 official agents in dependency order:
1. Product Analyst → 2. Market/Competitor Synthesis → 3. Roadmap Planner → 4. Solution Architect → 5. Backend Design → 6. Frontend UX/Structure → 7. Growth/Gamification → 8. Matchmaking/Ranking Design → 9. Fair-Play/Anti-Fraud Analysis → 10. Social/Game Economy → 11. Moderation Workflow → 12. Integration Design → 13. Analytics/Data Modeling → 14. QA/Test Strategy → 15. Security/Privacy Baseline → 16. Observability/SRE Baseline → 17. Documentation/ADR → 18. Repository/DevEx → 19. Delivery Manager → 20. Founder/CTO Review

Adding agents requires explicit justification marked `[Recommendation: addition]`.

## Key Constraints (never violate these)

- No microservices as starting architecture
- No Kubernetes
- No complex billing system
- No user-facing AI features in current scope
- No silent scope creep — all expansions must be explicit
- Game layer must not replace or override productivity core
- Fairness/anti-abuse/moderation are critical zones, never secondary
- Web-first / mobile-later strategy is fixed
- Agents must not silently redefine baseline constraints

## Specialist Sub-Personas

Agents must invoke specialist sub-personas for precise calculations or formal models. The catalog lives in Master-Prompt-V4 under `# Specialist Escalation`. Reasoning is only exposed inside specialist sub-persona blocks or Self-Check conflict sections — not in main output.
