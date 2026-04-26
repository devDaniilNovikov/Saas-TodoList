---
name: matchmaking-ranking
description: Use when the user asks for matchmaking algorithm, rating system (±50 spread), ELO-like calculation, leagues/leaderboards design, seasonal/permanent/hybrid league structure, or PvP pairing logic for the productivity + social gaming product. Wave-5 of the 20-agent catalog. Produces Matchmaking/Ranking Design V2 artifact.
---

# Matchmaking / Ranking Design Skill

Catalog position: **#8 of 20** (Official Agent Catalog, Master-Prompt-V4 `MP-V4-2026-04-25`).
Source of Truth: `improved/Matchmaking-Ranking-Design-Agent-V2.md`.

## Activation Triggers
- "Matchmaking", "rating system", "ELO", "rating spread ±50".
- "Leagues", "leaderboards", "seasons", "PvP pairing".
- Orchestrator delegates Wave-5.

## Required Upstream (Stop-Condition)
- Solution Architect V2 (module boundaries).
- Growth/Gamification V2 (рейтинг — продолжение прогрессии).
- Product Analyst V2 (PvP/PvE сегменты и motivations).

If missing → STOP, ask 1 question. Не выдумывать формулы рейтинга.

## Execution Protocol
1. Read `improved/Matchmaking-Ranking-Design-Agent-V2.md` in full.
2. Verify Contract Hash `MP-V4-2026-04-25`.
3. Output Header.
4. Decomposition по секциям из V2 + confidence-суффикс.
5. Format Templates: Rating Source, Pairing Rule, League Tier.
6. Pre-Output Gate ПЕРЕД выводом.
7. Tags Glossary строгие.
8. Reasoning только в Specialist sub-persona блоках.

## Critical Constraints
- Rating spread **±50** — фиксированный констрейнт из Master-Prompt-V4. Изменение → `[Recommendation]` + обоснование + Founder/CTO sign.
- PvP типы: 1v1, team battles до 3 игроков, sync + async — все должны быть покрыты.
- Rating источники: achievements, tasks, wins, placement — баланс не должен поощрять griefing.
- League типы: seasonal / permanent / hybrid — должны быть определены явно.
- Anti-abuse hook обязателен (координация с Fair-Play).
- Никаких "industry-standard ELO constants" без `[Assumption]` + источник.

## Output Artifact
- Reviewer-persona: Founder/CTO Review Agent.
- Mandatory Human Approval: yes (fairness — критическая зона).
- Status: `NOT-MERGED`; `PRELIMINARY` без approval.
