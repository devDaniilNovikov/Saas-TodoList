---
name: frontend-ux-structure
description: Use when the user asks for frontend information architecture, route map, page hierarchy, UI states, React+TypeScript structure, shared components, or feature folder layout for the productivity + social gaming web product. Wave-4 of the 20-agent catalog. Produces Frontend UX/Structure V2 artifact.
---

# Frontend UX / Structure Skill

Catalog position: **#6 of 20** (Official Agent Catalog, Master-Prompt-V4 `MP-V4-2026-04-25`).
Source of Truth: `improved/Frontend-UX-Structure-Agent-V2.md`.

## Activation Triggers
- "Information architecture", "IA", "route map", "page hierarchy".
- "Frontend structure", "feature folders", "shared components", "UI states".
- "React + TypeScript layout".
- Orchestrator delegates Wave-4.

## Required Upstream (Stop-Condition)
- Solution Architect V2 (module boundaries).
- Product Analyst V2 (user flows / segments).

If missing → STOP, ask 1 question. Не выдумывать routes / features.

## Execution Protocol
1. Read `improved/Frontend-UX-Structure-Agent-V2.md` in full.
2. Verify Contract Hash `MP-V4-2026-04-25`.
3. Output Header (Peer Cross-Check vs Solution Architect + Product Analyst).
4. Decomposition по секциям из V2 + confidence-суффикс.
5. Format Templates: Route Entry, Feature Folder, Shared Component, UI State.
6. Pre-Output Gate ПЕРЕД выводом.
7. Tags Glossary строгие.
8. Reasoning только в Specialist sub-persona блоках.

## Critical Constraints
- React + TypeScript baseline — не предлагать Vue/Svelte/etc.
- **Web-first**, mobile-later — но IA не должна делать responsive невозможным.
- Table-centric planning UX — не подменять карточками/канбаном без явного `[Recommendation]`.
- Feature-folder structure отражает module boundaries из Solution Architect.
- Game layer не подавляет productivity core в IA.
- Не выдумывать имена screens — только из Product Analyst flows.

## Output Artifact
- Reviewer-persona: Solution Architect.
- Mandatory Human Approval: no.
- Status: `NOT-MERGED` до review.
