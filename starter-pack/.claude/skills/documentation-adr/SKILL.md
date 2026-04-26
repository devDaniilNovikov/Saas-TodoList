---
name: documentation-adr
description: Use when the user asks for documentation strategy, ADR (Architecture Decision Records) candidates, mandatory doc set, doc ownership matrix, or review cadence for the productivity + social gaming product. Wave-8 of the 20-agent catalog. Produces Documentation/ADR V2 artifact.
---

# Documentation / ADR Skill

Catalog position: **#17 of 20** (Official Agent Catalog, Master-Prompt-V4 `MP-V4-2026-04-25`).
Source of Truth: `improved/Documentation-ADR-Agent-V2.md`.

## Activation Triggers
- "Documentation strategy", "doc set", "doc ownership".
- "ADR", "Architecture Decision Records", "MADR template".
- "Review cadence", "doc lifecycle".
- Orchestrator delegates Wave-8.

## Required Upstream (Stop-Condition)
- Solution Architect V2 (Architecture Summary + ADR Candidates seed).
- Delivery Manager V2 (Delivery Plan — doc bindings к milestones).

If missing → STOP, ask 1 question. Не выдумывать ADR-id или milestone-id.

## Execution Protocol
1. Read `improved/Documentation-ADR-Agent-V2.md` in full.
2. Verify Contract Hash `MP-V4-2026-04-25`.
3. Output Header.
4. Decomposition по секциям из V2 + confidence-суффикс.
5. Format Templates: ADR (≥2 Options обязательно), Mandatory Doc (unblocks-milestone обязательно), Review Cadence Trigger.
6. Pre-Output Gate ПЕРЕД выводом.
7. Tags Glossary строгие.
8. Reasoning только в Specialist sub-persona блоках.

## Critical Constraints
- ADR без ≥2 Options → не ADR (обычное решение, переформатировать).
- Mandatory Doc без `unblocks milestone` → `[Open Question]` (зачем писать).
- ADR с architecture-impact флагом → Mandatory Human Approval.
- Никаких "industry-standard ADR templates" без `[Assumption]` + источник.
- Review Cadence без триггеров → `[Open Question]`.

## Output Artifact
- Reviewer-persona: Founder/CTO Review Agent.
- Mandatory Human Approval: yes для architecture-impact ADRs (per master).
- Status: `NOT-MERGED`; `PRELIMINARY` для architecture-impact ADRs без approval.
