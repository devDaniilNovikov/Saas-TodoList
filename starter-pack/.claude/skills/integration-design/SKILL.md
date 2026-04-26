---
name: integration-design
description: Use when the user asks for external integrations design — Google Calendar, Telegram, Notion, email, push notifications — including OAuth flow, webhook handling, sync strategy, or rate limit handling for the productivity + social gaming product. Wave-6 of the 20-agent catalog. Produces Integration Design V2 artifact.
---

# Integration Design Skill

Catalog position: **#12 of 20** (Official Agent Catalog, Master-Prompt-V4 `MP-V4-2026-04-25`).
Source of Truth: `improved/Integration-Design-Agent-V2.md`.

## Activation Triggers
- "Integrations", "Google Calendar", "Telegram bot", "Notion sync", "email/push".
- "OAuth flow", "webhooks", "external API", "sync strategy".
- Orchestrator delegates Wave-6.

## Required Upstream (Stop-Condition)
- Solution Architect V2 (integrations module).
- Backend Design V2 (per-module API surface).
- Product Analyst V2 (which integrations are MVP-priority).

If missing → STOP, ask 1 question. Не выдумывать API endpoints внешних сервисов.

## Execution Protocol
1. Read `improved/Integration-Design-Agent-V2.md` in full.
2. Verify Contract Hash `MP-V4-2026-04-25`.
3. Output Header.
4. Decomposition по секциям из V2 + confidence-суффикс.
5. Format Templates: Integration Spec (auth, scope, sync model, rate limits, failure mode).
6. Pre-Output Gate ПЕРЕД выводом.
7. Tags Glossary строгие.
8. Reasoning только в Specialist sub-persona блоках.

## Critical Constraints
- Integrations baseline: Google Calendar, Telegram, email, push, Notion.
- OAuth flow — стандартный (PKCE для public clients), но конкретные scopes требуют `[Assumption]` + проверка в provider docs.
- Rate limits / quotas — `[Open Question]` если не уверен в конкретных лимитах (актуальная версия provider docs).
- Failure mode per integration: degraded mode (без integration → app продолжает работать).
- Нет хранения third-party credentials в plaintext — координация с Security/Privacy.
- Webhooks — verifiable (signature check), idempotent.

## Output Artifact
- Reviewer-persona: Solution Architect.
- Mandatory Human Approval: no (если нет PII / monetization implications).
- Status: `NOT-MERGED` до review.
