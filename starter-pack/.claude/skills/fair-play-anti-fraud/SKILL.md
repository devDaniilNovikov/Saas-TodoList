---
name: fair-play-anti-fraud
description: Use when the user asks for anti-cheat, anti-abuse, fairness signals, fraud detection, multi-account detection, automation/bot detection, or response policies for the productivity + social/PvP/PvE product. Wave-5 of the 20-agent catalog. CRITICAL ZONE — anti-abuse mandatory in MVP. Produces Fair-Play/Anti-Fraud V2 artifact.
---

# Fair-Play / Anti-Fraud Skill

Catalog position: **#9 of 20** (Official Agent Catalog, Master-Prompt-V4 `MP-V4-2026-04-25`).
Source of Truth: `improved/Fair-Play-Anti-Fraud-Analysis-Agent-V2.md`.

## Activation Triggers
- "Anti-cheat", "anti-abuse", "fraud detection", "multi-account".
- "Bot detection", "automation detection", "fairness signals".
- "Response policy", "graduated sanctions".
- Orchestrator delegates Wave-5.

## Required Upstream (Stop-Condition)
- Solution Architect V2 (module boundaries).
- Matchmaking/Ranking V2 (rating sources — surface для абуза).
- Growth/Gamification V2 (currency / achievements — surface для абуза).
- Product Analyst V2 (segments).

If missing → STOP, ask 1 question. Не выдумывать abuse vectors.

## Execution Protocol
1. Read `improved/Fair-Play-Anti-Fraud-Analysis-Agent-V2.md` in full.
2. Verify Contract Hash `MP-V4-2026-04-25`.
3. Output Header.
4. Decomposition по секциям из V2 + confidence-суффикс.
5. Format Templates: Abuse Vector, Detection Signal, Response Tier.
6. Pre-Output Gate ПЕРЕД выводом.
7. Tags Glossary строгие.
8. Reasoning только в Specialist sub-persona блоках.

## Critical Constraints
- **Anti-abuse в MVP — не V1+.** Это зафиксированный констрейнт Master-Prompt-V4.
- **Критическая зона** — `Mandatory Human Approval: yes` обязательно.
- Abuse vectors покрывают минимум: multi-account, automation/bots, collusion, score manipulation, content abuse.
- Detection signals — falsifiable (binary check или metric threshold), не "feeling".
- Response policy — graduated (warn → soft cap → hard ban), per vector.
- Никаких "ML detect everything" без `[Open Question]` про training data, baseline, false-positive rate.

## Output Artifact
- Reviewer-persona: Founder/CTO Review Agent.
- Mandatory Human Approval: **yes** (critical zone — fairness/anti-abuse).
- Status: `NOT-MERGED`; `PRELIMINARY` без approval — обязательно.
