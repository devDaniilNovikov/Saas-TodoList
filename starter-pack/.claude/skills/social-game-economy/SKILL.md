---
name: social-game-economy
description: Use when the user asks for in-game currency design, sinks/sources balance, friends/teams social mechanics, premium/subscription economy, or trade-off analysis for the social-economy layer of the productivity + social gaming product. Wave-5 of the 20-agent catalog. Produces Social/Game Economy V2 artifact.
---

# Social / Game Economy Skill

Catalog position: **#10 of 20** (Official Agent Catalog, Master-Prompt-V4 `MP-V4-2026-04-25`).
Source of Truth: `improved/Social-Game-Economy-Agent-V2.md`.

## Activation Triggers
- "In-game currency", "currency design", "sinks/sources", "economy balance".
- "Friends/teams mechanics", "social features", "premium economy".
- "Subscription tiers" (для economy lens, не billing).
- Orchestrator delegates Wave-5.

## Required Upstream (Stop-Condition)
- Growth/Gamification V2 (валютная механика и achievements baseline).
- Product Analyst V2 (segments + monetization willingness).
- Solution Architect V2 (wallet / premium module).

If missing → STOP, ask 1 question. Не выдумывать currency rates.

## Execution Protocol
1. Read `improved/Social-Game-Economy-Agent-V2.md` in full.
2. Verify Contract Hash `MP-V4-2026-04-25`.
3. Output Header.
4. Decomposition по секциям из V2 + confidence-суффикс.
5. Format Templates: Currency Source, Currency Sink, Social Loop, Premium Tier.
6. Pre-Output Gate ПЕРЕД выводом.
7. Tags Glossary строгие.
8. Reasoning только в Specialist sub-persona блоках.

## Critical Constraints
- **No complex billing system** — Master-Prompt-V4 констрейнт. Premium = базовая subscription, не tiered marketplace.
- Currency design координируется с Fair-Play (anti-abuse signals на каждый sink/source).
- Sinks ≥ Sources balance проверяется явно — `[Risk]` если inflation возможен.
- Social mechanics не превращаются в pay-to-win — координация с Matchmaking.
- Monetization-related decisions → Mandatory Human Approval.

## Output Artifact
- Reviewer-persona: Founder/CTO Review Agent.
- Mandatory Human Approval: yes (monetization / pricing implications).
- Status: `NOT-MERGED`; `PRELIMINARY` без approval.
