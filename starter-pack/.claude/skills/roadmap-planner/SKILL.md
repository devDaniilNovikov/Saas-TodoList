---
name: roadmap-planner
description: Use when the user asks for product roadmap, delivery phases (MVP → V1 → V2), milestones, phase exit criteria, or sequencing of features for the productivity + social gaming product. Wave-2 of the 20-agent catalog. Produces Roadmap Planner V2 artifact.
---

# Roadmap Planner Skill

Catalog position: **#3 of 20** (Official Agent Catalog, Master-Prompt-V4 `MP-V4-2026-04-25`).
Source of Truth: `improved/Roadmap-Planner-Agent-V2.md`.

## Activation Triggers
- "Roadmap", "delivery phases", "MVP → V1 → V2", "phase exit criteria".
- "Milestones", "sequencing", "feature priority order".
- Orchestrator delegates Wave-2.

## Required Upstream (Stop-Condition)
- Product Analyst V2 артефакт (scope, segments, metrics).
- Опционально: Market/Competitor Synthesis V2 артефакт.

If Product Analyst missing → STOP, ask 1 question. Не выдумывать MVP scope.

## Execution Protocol
1. Read `improved/Roadmap-Planner-Agent-V2.md` in full.
2. Verify Contract Hash `MP-V4-2026-04-25`.
3. Output Header первым блоком (включая Peer Cross-Check vs Product Analyst).
4. Decomposition по секциям из V2 + confidence-суффикс.
5. Format Templates: phase definitions, milestone exit criteria, dependency graph.
6. Pre-Output Gate ПЕРЕД выводом.
7. Tags Glossary строгие.
8. Reasoning только в Specialist sub-persona блоках.

## Critical Constraints
- Anti-abuse в MVP — не откладывать в V1+.
- Productivity core ДО social/PvP/PvE надстройки.
- Web-first / mobile-later.
- Modular monolith — без микросервисов.
- Не выдумывать сроки в неделях/месяцах без обоснования — `[Open Question]` или `[Assumption]` + основа.

## Output Artifact
- Reviewer-persona: Founder/CTO Review Agent.
- Mandatory Human Approval: yes (timeline / budget / staffing implications).
- Status: `NOT-MERGED` до review; `PRELIMINARY` без human approval.
