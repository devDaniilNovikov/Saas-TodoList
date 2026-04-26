---
name: repository-devex
description: Use when the user asks for repository structure, monorepo/polyrepo layout, CODEOWNERS rules, naming conventions, testing layout, or DevEx priorities (P0/P1/P2) for the productivity + social gaming product. Wave-8 of the 20-agent catalog. Produces Repository/DevEx V2 artifact.
---

# Repository / DevEx Skill

Catalog position: **#18 of 20** (Official Agent Catalog, Master-Prompt-V4 `MP-V4-2026-04-25`).
Source of Truth: `improved/Repository-DevEx-Agent-V2.md`.

## Activation Triggers
- "Repository structure", "monorepo", "polyrepo", "repo layout".
- "CODEOWNERS", "naming conventions", "ownership rules".
- "DevEx", "developer experience", "pre-commit hooks", "testing layout".
- Orchestrator delegates Wave-8.

## Required Upstream (Stop-Condition)
- Solution Architect V2 (dependency rules + module boundaries).
- Backend Design V2 (backend module list).
- Frontend UX/Structure V2 (frontend feature list).

If missing → STOP, ask 1 question. Не выдумывать module structure.

## Execution Protocol
1. Read `improved/Repository-DevEx-Agent-V2.md` in full.
2. Verify Contract Hash `MP-V4-2026-04-25`.
3. Output Header.
4. Decomposition по секциям из V2 + confidence-суффикс.
5. Format Templates: Naming/Ownership Entry (path + owner + CODEOWNERS pattern + naming convention + forbidden patterns), DevEx Recommendation (P0/P1/P2 обязательно), Test Layout Entry.
6. Pre-Output Gate ПЕРЕД выводом.
7. Tags Glossary строгие.
8. Reasoning только в Specialist sub-persona блоках.

## Critical Constraints
- Каждая директория имеет owner role + CODEOWNERS pattern + naming convention.
- DevEx без priority (P0/P1/P2) → `[Open Question]`.
- Repo structure отражает modular monolith boundaries (не нарушает dependency rules).
- Никаких имён конкретных tools (Nx/Turborepo/Lerna/Gradle) как требований без `[Recommendation]` + `[Assumption]`.
- Никаких выдуманных module / feature names — только из Backend Design / Frontend IA.
- Monorepo vs polyrepo — `Specialist: Repo Topology` если возникает trade-off.

## Output Artifact
- Reviewer-persona: Delivery Manager Agent.
- Mandatory Human Approval: no.
- Status: `NOT-MERGED` до review.
