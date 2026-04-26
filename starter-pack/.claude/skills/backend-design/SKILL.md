---
name: backend-design
description: Use when the user asks for backend module design, Java/Spring Boot package layout, persistence strategy (PostgreSQL/Redis), API contracts, or per-module backend specs for the productivity + social gaming product. Wave-4 of the 20-agent catalog. Produces Backend Design V2 artifact.
---

# Backend Design Skill

Catalog position: **#5 of 20** (Official Agent Catalog, Master-Prompt-V4 `MP-V4-2026-04-25`).
Source of Truth: `improved/Backend-Design-Agent-V2.md`.

## Activation Triggers
- "Backend modules", "Spring Boot packages", "persistence design", "API contracts".
- "PostgreSQL schema", "Redis usage", "module API surface".
- Orchestrator delegates Wave-4.

## Required Upstream (Stop-Condition)
- Solution Architect V2 (Architecture Summary + module boundaries + dependency rules).

If missing → STOP, ask 1 question. Не выдумывать module list.

## Execution Protocol
1. Read `improved/Backend-Design-Agent-V2.md` in full.
2. Verify Contract Hash `MP-V4-2026-04-25`.
3. Output Header (Peer Cross-Check vs Solution Architect — обязательно MATCH).
4. Decomposition по секциям из V2 + confidence-суффикс.
5. Format Templates: Module Spec (responsibilities, persistence, API, dependencies).
6. Pre-Output Gate ПЕРЕД выводом.
7. Tags Glossary строгие.
8. Reasoning только в Specialist sub-persona блоках.

## Critical Constraints
- Java + Spring Boot (стек фиксирован — не предлагать Kotlin/Go/etc. без `[Recommendation]` + обоснование).
- PostgreSQL primary, Redis для cache/state — без дополнительных stores без явного обоснования.
- Modular monolith package layout: НЕ микросервисы, общая deployment unit.
- API стиль (REST/GraphQL/RPC) — наследовать из Solution Architect; конфликт → `[Risk]` или `[Open Question]`.
- Каждый module имеет owner role, persistence strategy, dependency list.

## Output Artifact
- Reviewer-persona: Solution Architect (peer-review, не self-review).
- Mandatory Human Approval: no (если нет architecture-impact deviation от Solution Architect).
- Status: `NOT-MERGED` до review.
