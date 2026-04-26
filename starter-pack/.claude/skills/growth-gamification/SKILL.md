---
name: growth-gamification
description: Use when the user asks for gamification mechanics, achievements design, internal currency, ranks, retention loops, engagement features, or growth metrics for the productivity + social/PvP/PvE product. Wave-5 of the 20-agent catalog. Produces Growth/Gamification V2 artifact.
---

# Growth / Gamification Skill

Catalog position: **#7 of 20** (Official Agent Catalog, Master-Prompt-V4 `MP-V4-2026-04-25`).
Source of Truth: `improved/Growth-Gamification-Agent-V2.md`.

## Activation Triggers
- "Gamification", "achievements", "internal currency", "ranks", "rewards".
- "Retention loops", "engagement metrics", "habit formation hooks".
- Orchestrator delegates Wave-5.

## Required Upstream (Stop-Condition)
- Product Analyst V2 (segments + metrics).
- Solution Architect V2 (module boundaries).

If missing → STOP, ask 1 question. Не выдумывать gamification без user context.

## Execution Protocol
1. Read `improved/Growth-Gamification-Agent-V2.md` in full.
2. Verify Contract Hash `MP-V4-2026-04-25`.
3. Output Header.
4. Decomposition по секциям из V2 + confidence-суффикс.
5. Format Templates: Mechanic Spec, Reward Tier, Retention Loop, KPI.
6. Pre-Output Gate ПЕРЕД выводом.
7. Tags Glossary строгие.
8. Reasoning только в Specialist sub-persona блоках.

## Critical Constraints
- **Productivity core НЕ подменяется gamification**: gamification усиливает, не заменяет.
- Внутренняя валюта без anti-abuse signals → `[Risk]`. Координация с Fair-Play / Social-Game-Economy обязательна.
- Currency / monetization-adjacent decisions → Mandatory Human Approval.
- Никаких dark patterns / манипуляций с достижениями.
- Метрики retention — реалистичные, без `[Assumption]` со ссылкой на источник.

## Output Artifact
- Reviewer-persona: Founder/CTO Review Agent.
- Mandatory Human Approval: yes (currency / monetization-adjacent).
- Status: `NOT-MERGED`; `PRELIMINARY` без approval для currency-related частей.
