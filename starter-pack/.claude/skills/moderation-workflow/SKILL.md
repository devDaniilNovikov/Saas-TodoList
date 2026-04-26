---
name: moderation-workflow
description: Use when the user asks for moderation flow, content/user moderation, admin tools, escalation paths, abuse report handling, or moderation operations for the productivity + social gaming product. Wave-6 of the 20-agent catalog. CRITICAL ZONE. Produces Moderation Workflow V2 artifact.
---

# Moderation Workflow Skill

Catalog position: **#11 of 20** (Official Agent Catalog, Master-Prompt-V4 `MP-V4-2026-04-25`).
Source of Truth: `improved/Moderation-Workflow-Agent-V2.md`.

## Activation Triggers
- "Moderation", "admin tools", "abuse reports", "escalation paths".
- "Content moderation", "user moderation", "ban/unban flow".
- Orchestrator delegates Wave-6.

## Required Upstream (Stop-Condition)
- Fair-Play/Anti-Fraud V2 (abuse vectors → moderation triggers).
- Solution Architect V2 (admin/moderation module).
- Product Analyst V2 (user segments).

If missing → STOP, ask 1 question. Не выдумывать report types.

## Execution Protocol
1. Read `improved/Moderation-Workflow-Agent-V2.md` in full.
2. Verify Contract Hash `MP-V4-2026-04-25`.
3. Output Header.
4. Decomposition по секциям из V2 + confidence-суффикс.
5. Format Templates: Report Type, Moderation Tier, Escalation Path, Admin Action.
6. Pre-Output Gate ПЕРЕД выводом.
7. Tags Glossary строгие.
8. Reasoning только в Specialist sub-persona блоках.

## Critical Constraints
- **Критическая зона** — Mandatory Human Approval обязателен для policy-уровня решений.
- Каждый report type имеет SLA (response time) и escalation path.
- Admin actions — auditable (logged, reversible где возможно).
- Anti-abuse координация с Fair-Play (нет дублирования логики, чёткие boundaries).
- Никаких "AI-only auto-moderation" без human-in-the-loop checkpoint.
- Moderator role distinct from regular admin (least privilege).

## Output Artifact
- Reviewer-persona: Founder/CTO Review Agent.
- Mandatory Human Approval: yes (moderation — критическая зона).
- Status: `NOT-MERGED`; `PRELIMINARY` без approval.
