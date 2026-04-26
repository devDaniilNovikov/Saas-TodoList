---
name: market-competitor-synthesis
description: Use when the user asks for competitor analysis, market landscape, positioning, differentiators, СНГ market specifics, or competitive synthesis for the productivity + social gaming product. Wave-1 of the 20-agent catalog (parallel with Product Analyst). Produces Market/Competitor Synthesis V2 artifact.
---

# Market / Competitor Synthesis Skill

Catalog position: **#2 of 20** (Official Agent Catalog, Master-Prompt-V4 `MP-V4-2026-04-25`).
Source of Truth: `improved/Market-or-Competitor-Synthesis-Agent-V2.md`.

## Activation Triggers
- "Competitor analysis", "market landscape", "positioning", "differentiators".
- "СНГ-specific players", "comparable products", "competitive moat".
- Orchestrator delegates Wave-1 (parallel with Product Analyst).

## Required Upstream (Stop-Condition)
- `Master-Prompt-V4.md` (baseline).
- Product Analyst V2 артефакт (для domain-anchor; см. V2 Stop-Condition).

If missing → STOP, ask 1 question. Не выдумывать competitors / market data.

## Execution Protocol
1. Read `improved/Market-or-Competitor-Synthesis-Agent-V2.md` in full.
2. Verify Contract Hash `MP-V4-2026-04-25`.
3. Output Header первым блоком.
4. Decomposition по секциям из V2 + confidence-суффикс заголовка.
5. Format Templates из V2 заполнены.
6. Pre-Output Gate ПЕРЕД выводом.
7. Tags Glossary строгие; внешние факты → `[Assumption]` + источник или `[Open Question]`.
8. Reasoning только в Specialist sub-persona блоках.

## Critical Constraints
- Никаких выдуманных competitor-имён / market-share чисел — `[Assumption]` + источник или `[Open Question: requires external research]`.
- Не подменять Product Analyst — фокус на market/competitor lens.
- СНГ-рынок — приоритетный, но не единственный аспект.
- Web-first контекст (mobile-later — не competitor disqualifier).

## Output Artifact
- Reviewer-persona: Founder/CTO Review Agent.
- Mandatory Human Approval: no (но competitive claims → проверка через Founder/CTO).
- Status: `NOT-MERGED` до review.
