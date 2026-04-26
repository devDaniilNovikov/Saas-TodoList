# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Repository Is

This is a **prompt engineering / AI agent design repository** — not a software codebase. It contains a collection of structured AI agent prompt files for orchestrating the design and development of a production-ready productivity + social gaming web product.

There is no code to build, test, or run. All files are Markdown prompt documents.

## Model Assignment

Жёсткое разделение ролей по моделям — переключение модели обязательно перед сменой типа работы:

| Тип работы | Модель | Зачем |
|------------|--------|-------|
| Анализ, планирование, проектирование агентных контрактов, ревью артефактов, разрешение конфликтов между агентами, severity-калибровка, любые governance-решения | **claude-opus-4-7** | Глубина рассуждения и удержание контракта по `Master-Prompt-V4` приоритетнее скорости. |
| Написание кода (когда проект перейдёт в имплементационную фазу: React/TypeScript frontend, Java/Spring Boot backend, миграции, тесты, конфиги) | **claude-sonnet-4-6** | Скорость и стоимость для рутинной кодогенерации; контракт уже зафиксирован на этапе анализа. |

Правила:
- Если задача смешанная (план + код) — сначала Opus 4.7 фиксирует план/контракт артефактом, затем Sonnet 4.6 пишет код по этому артефакту. Не наоборот.
- Если работа с агентными prompt-файлами (`improved/*.md`, `Master-Prompt-V*.md`, `Orchestrator.md`) — это **анализ и проектирование контрактов**, не «код». Использовать **Opus 4.7**, даже если правка выглядит как «просто текст».
- Переключение модели в Claude Code: `/model claude-opus-4-7` или `/model claude-sonnet-4-6`.
- Несоответствие модели типу работы → остановиться и попросить пользователя переключить модель, а не «дотянуть на текущей».

## Product Being Designed

A productivity tracker (goals / tasks / habits / day-week-month planning) with a social/game layer:
- Table-centric planning UX, achievements, internal currency, premium/subscription
- Friends, teams, PvP 1v1 and team battles (up to 3 players), sync/async PvP
- Matchmaking (±50 rating spread), rating from achievements/tasks/wins/placement
- PvE solo/co-op/global events, leaderboards, leagues (seasonal/permanent/hybrid)
- Anti-abuse/anti-fraud in MVP, seasons/events, admin/moderation
- Integrations: Google Calendar, Telegram, email, push, Notion
- **Tech stack**: React + TypeScript (frontend), Java + Spring Boot (backend), PostgreSQL, Redis
- **Architecture**: modular monolith — no microservices, no Kubernetes, no complex billing
- **Platform**: web first, mobile later; target market: СНГ

## Repository Structure

| Path | Role |
|------|------|
| `Master-Prompt-V4.md` | **Single source of truth** — full product blueprint, agent system, governance rules, constraints. Always V4. |
| `Orchestrator.md` | Runtime-conductor: координирует порядок волн, handoff, конфликты и human approval gates для 20-агентного каталога. |
| `improved/` | **Единственное активное расположение** всех 20 агентов + `AI-Agents-Constructor-V2.md`. Все правки — только здесь. |
| `improved/_Agent-Base-Template.md` | Canonical V2 contract structure. All V2 agents must conform. |
| `agent_pipeline_waves.svg` | Visual diagram of agent execution waves/pipeline (5 волн, визуальный контракт). |

## No Build / Test / Run

This is a Markdown-only repository. There is no package manager, no build tool, no test runner, no dev server. Do not look for `package.json`, `Makefile`, `pom.xml`, etc. — they don't exist and shouldn't be added. Validation of agent prompts is a **content review**, not a code check.

## V2 Agent Contract — Design Principles

Все 20 агентов каталога + `AI-Agents-Constructor` живут в `improved/` и соответствуют V2-контракту, задокументированному в `improved/_Agent-Base-Template.md`. Ключевые принципы V2:

1. `Self-Check` реализован как **Pre-Output Gate** (выполняется *до* финального вывода, не после).
2. `Mandatory Artifact Header` **инстанцируется локально** в каждом агенте, а не наследуется молча из мастера.
3. `Peer Cross-Check` имеет процедурный формат вывода: `MATCH | CONFLICT | NOT-CHECKED-MISSING-ARTIFACT`.
4. `Format` и `Decomposition` объединены — единый источник истины для структуры вывода.
5. Local Context section удалён; агенты ссылаются на мастер через **delta-only**.
6. Трейлер "3 critically important instructions" удалён — его роль выполняют `Stop-Condition` + `Constraints`.
7. Confidence labels имеют явное размещение — суффикс заголовка секции: `## 3. <Title> *[confidence: high|medium|low]*`.
8. `Stop-Condition` синхронизирован с `Peer Cross-Check` (critical upstream missing → STOP; non-critical → `NOT-CHECKED-MISSING-ARTIFACT`).
9. Reasoning visibility rule живёт только в мастере — не дублируется в агентах.
10. Specialist sub-persona имеет **обязательный output block** формат.

**При создании нового агента:** зеркалировать структуру любого существующего V2 (например, `Solution-Architect-Agent-V2.md`, `Backend-Design-Agent-V2.md`) и правила в `_Agent-Base-Template.md` — не изобретать новые секции.

## Agent System Rules (enforced by Master-Prompt-V4)

**Contract Hash**: `MP-V4-2026-04-25` — every agent must verify this before starting. Mismatch → STOP + `[Risk]`.

**Every agent output must include** (V2 contract — `Output Header` block first, then `Pre-Output Gate` before final output):
- `Context Reference` header (master version, hash match, upstream inputs, local scope, out-of-scope, inherited assumptions, new assumptions, open questions, conflicts)
- `Peer Cross-Check Output` table — status per peer artifact
- `Pre-Output Gate` (formal contract verification, not quality review)
- `Independent Review Hook` (reviewer agent, status, human approval status)

**Tags Glossary** (use these exactly — no silent assumptions):
- `[Assumption]` — unverified claim; must include what is assumed and how to validate
- `[Recommendation]` — must include: subject + action + owner-role + observable criterion
- `[Risk]` — must include: trigger + impact + mitigation owner
- `[Later]` — deferred; must include trigger condition for return
- `[Open Question]` — must include owner and deadline

**Stop-Condition Protocol**: If required upstream artifacts are missing or Contract Hash doesn't match → STOP, ask exactly 1 clarifying question, do not fabricate peer-artifact content.

**Independent Review**: Self-review is forbidden as quality check. Each agent has an assigned Reviewer-agent. Artifacts are `NOT-MERGED` until reviewer issues PASS / PASS-WITH-ISSUES / FAIL.

**Mandatory Human Approval** required for: fairness/anti-abuse decisions, monetization/pricing, architecture-impact ADRs, any FAIL or SCOPE-CREEP signal. Without approval → `Status: PRELIMINARY`.

## Official Agent Catalog (from Master-Prompt-V4)

20 official agents in dependency order:
1. Product Analyst → 2. Market/Competitor Synthesis → 3. Roadmap Planner → 4. Solution Architect → 5. Backend Design → 6. Frontend UX/Structure → 7. Growth/Gamification → 8. Matchmaking/Ranking Design → 9. Fair-Play/Anti-Fraud Analysis → 10. Social/Game Economy → 11. Moderation Workflow → 12. Integration Design → 13. Analytics/Data Modeling → 14. QA/Test Strategy → 15. Security/Privacy Baseline → 16. Observability/SRE Baseline → 17. Documentation/ADR → 18. Repository/DevEx → 19. Delivery Manager → 20. Founder/CTO Review

Adding agents requires explicit justification marked `[Recommendation: addition]`.

## Key Constraints (never violate these)

- No microservices as starting architecture
- No Kubernetes
- No complex billing system
- No user-facing AI features in current scope
- No silent scope creep — all expansions must be explicit
- Game layer must not replace or override productivity core
- Fairness/anti-abuse/moderation are critical zones, never secondary
- Web-first / mobile-later strategy is fixed
- Agents must not silently redefine baseline constraints

## Specialist Sub-Personas

Agents must invoke specialist sub-personas for precise calculations or formal models. The catalog lives in Master-Prompt-V4 under `# Specialist Escalation`. Reasoning is only exposed inside specialist sub-persona blocks or Self-Check conflict sections — not in main output.
