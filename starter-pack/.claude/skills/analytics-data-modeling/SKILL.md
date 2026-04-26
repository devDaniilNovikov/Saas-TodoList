---
name: analytics-data-modeling
description: Use when the user asks for analytics events taxonomy, instrumentation plan, metrics definitions, data warehouse model, or product/funnel analytics for the productivity + social gaming product. Wave-6 of the 20-agent catalog. Produces Analytics/Data Modeling V2 artifact.
---

# Analytics / Data Modeling Skill

Catalog position: **#13 of 20** (Official Agent Catalog, Master-Prompt-V4 `MP-V4-2026-04-25`).
Source of Truth: `improved/Analytics-Data-Modeling-Agent-V2.md`.

## Activation Triggers
- "Analytics events", "event taxonomy", "instrumentation".
- "Metrics definitions", "funnel analytics", "data model", "DWH schema".
- Orchestrator delegates Wave-6.

## Required Upstream (Stop-Condition)
- Product Analyst V2 (metrics / OKRs — что именно мерим).
- Solution Architect V2 (где живут события / какие модули генерируют).

If missing → STOP, ask 1 question. Не выдумывать event names.

## Execution Protocol
1. Read `improved/Analytics-Data-Modeling-Agent-V2.md` in full.
2. Verify Contract Hash `MP-V4-2026-04-25`.
3. Output Header.
4. Decomposition по секциям из V2 + confidence-суффикс.
5. Format Templates: Event Spec (name, owner, schema, trigger, retention), Metric Definition, Data Model Entity.
6. Pre-Output Gate ПЕРЕД выводом.
7. Tags Glossary строгие.
8. Reasoning только в Specialist sub-persona блоках.

## Critical Constraints
- Event naming convention строгая (e.g., `domain.action.subject` или эквивалент — фиксировать в V2).
- Каждый event имеет owner role и retention policy.
- PII в events — никогда без явного `[Risk]` + Security/Privacy approval.
- Метрики из Product Analyst — каждая mapped к ≥1 instrumented event.
- Никаких "вычислимых из существующих" метрик без явного computation rule.
- Data model — нормализованный baseline, denormalization → `[Recommendation]` + обоснование.

## Output Artifact
- Reviewer-persona: Solution Architect.
- Mandatory Human Approval: no (если нет PII implications).
- Status: `NOT-MERGED` до review.
