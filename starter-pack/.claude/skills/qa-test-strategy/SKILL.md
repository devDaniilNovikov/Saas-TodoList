---
name: qa-test-strategy
description: Use when the user asks for QA strategy, test pyramid, test types (unit/integration/contract/e2e/load), test ownership, or coverage policy for the productivity + social gaming product. Wave-7 of the 20-agent catalog. Produces QA/Test Strategy V2 artifact.
---

# QA / Test Strategy Skill

Catalog position: **#14 of 20** (Official Agent Catalog, Master-Prompt-V4 `MP-V4-2026-04-25`).
Source of Truth: `improved/QA-Test-Strategy-Agent-V2.md`.

## Activation Triggers
- "QA strategy", "test pyramid", "test types", "coverage policy".
- "Unit tests", "integration tests", "e2e tests", "load tests", "contract tests".
- "Test ownership", "test environments".
- Orchestrator delegates Wave-7.

## Required Upstream (Stop-Condition)
- Backend Design V2 (модули и API).
- Frontend UX/Structure V2 (route map / components).
- Solution Architect V2 (architecture-level testing concerns).

If missing → STOP, ask 1 question. Не выдумывать coverage targets.

## Execution Protocol
1. Read `improved/QA-Test-Strategy-Agent-V2.md` in full.
2. Verify Contract Hash `MP-V4-2026-04-25`.
3. Output Header.
4. Decomposition по секциям из V2 + confidence-суффикс.
5. Format Templates: Test Type Entry (unit/integration/contract/e2e/load), Coverage Policy, Test Ownership Matrix.
6. Pre-Output Gate ПЕРЕД выводом.
7. Tags Glossary строгие.
8. Reasoning только в Specialist sub-persona блоках.

## Critical Constraints
- Test pyramid — обоснованный shape (не "все unit", не "всё e2e").
- Anti-abuse / fairness паттерны — обязательны в test surface (критическая зона).
- Каждый test type: trigger (per-commit/per-PR/nightly/release), owner role, exit criterion.
- Coverage targets — `[Assumption]` + обоснование, не "industry-standard 80%".
- E2E включает critical user journeys: signup → task creation → PvP match → leaderboard.
- Load test для matchmaking / leaderboard — `[Open Question]` если не определены baseline нагрузки.

## Output Artifact
- Reviewer-persona: Solution Architect.
- Mandatory Human Approval: no.
- Status: `NOT-MERGED` до review.
