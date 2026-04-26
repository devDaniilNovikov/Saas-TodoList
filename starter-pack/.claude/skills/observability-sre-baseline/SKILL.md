---
name: observability-sre-baseline
description: Use when the user asks for observability strategy, logging/metrics/tracing baseline, SLOs/SLIs definition, alert design, incident response, or SRE practices for the productivity + social gaming product. Wave-7 of the 20-agent catalog. Produces Observability/SRE Baseline V2 artifact.
---

# Observability / SRE Baseline Skill

Catalog position: **#16 of 20** (Official Agent Catalog, Master-Prompt-V4 `MP-V4-2026-04-25`).
Source of Truth: `improved/Observability-SRE-Baseline-Agent-V2.md`.

## Activation Triggers
- "Observability", "logging", "metrics", "tracing".
- "SLO", "SLI", "error budget", "alerts".
- "Incident response", "on-call", "runbook".
- Orchestrator delegates Wave-7.

## Required Upstream (Stop-Condition)
- Solution Architect V2 (modules / boundaries — где смотреть).
- Backend Design V2 (per-module surface).
- Product Analyst V2 (critical user journeys → SLO targets).

If missing → STOP, ask 1 question. Не выдумывать SLO targets.

## Execution Protocol
1. Read `improved/Observability-SRE-Baseline-Agent-V2.md` in full.
2. Verify Contract Hash `MP-V4-2026-04-25`.
3. Output Header.
4. Decomposition по секциям из V2 + confidence-суффикс.
5. Format Templates: SLO Entry, Alert Rule, Log Class, Trace Span Definition, Runbook.
6. Pre-Output Gate ПЕРЕД выводом.
7. Tags Glossary строгие.
8. Reasoning только в Specialist sub-persona блоках.

## Critical Constraints
- Modular monolith — observability на per-module уровне, не per-microservice.
- SLO/SLI per critical user journey: signup, task create, PvP match, leaderboard view.
- Alerts — actionable (runbook на каждый), не спам.
- Logs / metrics не содержат PII (координация с Security/Privacy).
- Tracing — sampled, не 100% (баланс cost / coverage).
- Никаких "industry-standard 99.9% SLO" без обоснования через Product Analyst metrics.
- Incident response: severity tiers, escalation path, post-mortem обязателен.

## Output Artifact
- Reviewer-persona: Solution Architect.
- Mandatory Human Approval: no.
- Status: `NOT-MERGED` до review.
