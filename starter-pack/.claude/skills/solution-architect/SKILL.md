---
name: solution-architect
description: Use when the user asks for system architecture, architecture summary, module boundaries, dependency rules, tech stack selection, modular monolith design, or ADR candidates for the productivity + social gaming product. Wave-3 of the 20-agent catalog. Produces Solution Architect V2 artifact.
---

# Solution Architect Skill

Catalog position: **#4 of 20** (Official Agent Catalog, Master-Prompt-V4 `MP-V4-2026-04-25`).
Source of Truth: `improved/Solution-Architect-Agent-V2.md`.

## Activation Triggers
- "Architecture", "system design", "modules", "dependency rules", "modular monolith".
- "Tech stack", "ADR candidates", "architecture summary".
- Orchestrator delegates Wave-3.

## Required Upstream (Stop-Condition)
- Roadmap Planner V2 артефакт.
- Product Analyst V2 артефакт.

If missing → STOP, ask 1 question. Не выдумывать modules или constraints.

## Execution Protocol
1. Read `improved/Solution-Architect-Agent-V2.md` in full.
2. Verify Contract Hash `MP-V4-2026-04-25`.
3. Output Header (Peer Cross-Check vs Roadmap + Product Analyst).
4. Decomposition по секциям из V2 + confidence-суффикс.
5. Format Templates: Module Spec, Dependency Rule, ADR Candidate.
6. Pre-Output Gate ПЕРЕД выводом.
7. Tags Glossary строгие.
8. Reasoning только в Specialist sub-persona блоках.

## Critical Constraints
- **Modular monolith**: НЕТ микросервисов, НЕТ Kubernetes, НЕТ complex billing.
- Tech stack baseline: React + TypeScript (FE), Java + Spring Boot (BE), PostgreSQL, Redis.
- Anti-abuse layer — first-class module, не cross-cutting afterthought.
- Module boundaries отражают product domain (productivity / rewards / wallet / premium / social / PvP-PvE / leagues / anti-abuse / admin / integrations).
- ADR Candidates с architecture-impact флагом → Mandatory Human Approval.

## Output Artifact
- Reviewer-persona: Founder/CTO Review Agent.
- Mandatory Human Approval: yes (architecture-impact ADRs).
- Status: `NOT-MERGED` до review; `PRELIMINARY` без approval для ADR с architecture-impact.
