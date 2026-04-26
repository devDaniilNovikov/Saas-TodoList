---
name: security-privacy-baseline
description: Use when the user asks for threat model, AuthN/AuthZ design, PII handling, GDPR-like privacy compliance, secrets management, or security baseline for the productivity + social gaming product. Wave-7 of the 20-agent catalog. Produces Security/Privacy Baseline V2 artifact.
---

# Security / Privacy Baseline Skill

Catalog position: **#15 of 20** (Official Agent Catalog, Master-Prompt-V4 `MP-V4-2026-04-25`).
Source of Truth: `improved/Security-Privacy-Baseline-Agent-V2.md`.

## Activation Triggers
- "Threat model", "STRIDE analysis", "security baseline".
- "AuthN", "AuthZ", "RBAC", "session management".
- "PII handling", "GDPR", "data subject rights", "privacy".
- "Secrets management", "encryption at rest / in transit".
- Orchestrator delegates Wave-7.

## Required Upstream (Stop-Condition)
- Solution Architect V2 (модули и trust boundaries).
- Backend Design V2 (persistence / API surface).
- Frontend UX/Structure V2 (auth flows / data inputs).

If missing → STOP, ask 1 question. Не выдумывать threats.

## Execution Protocol
1. Read `improved/Security-Privacy-Baseline-Agent-V2.md` in full.
2. Verify Contract Hash `MP-V4-2026-04-25`.
3. Output Header.
4. Decomposition по секциям из V2 + confidence-суффикс.
5. Format Templates: Threat Entry (STRIDE-like), AuthZ Rule, PII Class, Secret Policy.
6. Pre-Output Gate ПЕРЕД выводом.
7. Tags Glossary строгие.
8. Reasoning только в Specialist sub-persona блоках.

## Critical Constraints
- Threat model покрывает: account takeover, multi-account abuse, PvP score manipulation, payment fraud, data exfiltration.
- AuthZ — RBAC baseline; admin/moderator/user — least privilege.
- PII классификация явная (email / phone / device-id / behavioral) и retention policy per class.
- Secrets management: никаких credentials в repo / в plaintext logs.
- GDPR-like: data subject rights (export / delete) — обязательны для РФ + EU users.
- Anti-abuse координация с Fair-Play (общие сигналы, не дублирование).
- Никаких "secure by default" утверждений без observable verification.

## Output Artifact
- Reviewer-persona: Founder/CTO Review Agent.
- Mandatory Human Approval: no (но privacy-impact решения → Founder/CTO sign).
- Status: `NOT-MERGED` до review.
