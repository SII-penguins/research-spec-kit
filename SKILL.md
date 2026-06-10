---
name: research-spec-kit
description: Create and maintain canonical specification documents for complex AI-assisted projects, algorithm research, experiments, and multi-agent engineering work. Use when the user wants a repo documentation system with CLAUDE.md, PROGRESS.md, TODO.md, doc/IMPLEMENTATION_PLAN.md, doc/RUN_REGISTRY.md, diagnostics, PRD, FRONTEND_GUIDELINES, BACKEND_STRUCTURE, APP_FLOW, TEAM.md, lessons.md, canonical owners, conflict priority, update protocols, run ledgers, evidence gates, or assumption interrogation before coding.
---

# Research Spec Kit

Use this skill to turn a complex project idea into a maintainable AI collaboration documentation system. The current Chinese working name is "复杂项目文档中枢"; the earlier "研究八件套" remains a useful alias for algorithm/research projects.

## Core Rule

Every project fact must have exactly one canonical owner. Other documents may link or summarize, but must not copy the same live state, run history, task queue, contract, or diagnostic analysis.

Before writing non-trivial code, experiments, reports, or project docs, identify the canonical owner for each fact you are about to create or change. If critical assumptions are unresolved, ask targeted questions or mark them as `待确认项`.

## Workflow

1. Read `references/interrogation-checklist.md`.
2. Determine whether the user needs a new documentation system, a migration of stale docs, or an update to an existing project.
3. Ask only high-impact missing questions about current state, task queue, roadmap, run history, contracts, team workflow, and evidence/claim boundaries.
4. Read `references/document-blueprints.md` before generating or refactoring documents.
5. Apply `references/hard-rules.md` as the final quality gate.
6. Use `references/example-output-skeleton.md` only as a scaffold; never invent project-specific state from it.
7. Update the document that owns the changed fact. Do not spread the same update across unrelated docs.

## Standard Outputs

Generate or update this structure unless the user specifies a smaller scope:

- `CLAUDE.md`
- `PROGRESS.md`
- `TODO.md`
- `doc/IMPLEMENTATION_PLAN.md`
- `doc/RUN_REGISTRY.md`
- `doc/diagnostics/*.md` as needed
- `doc/PRD.md`
- `doc/FRONTEND_GUIDELINES.md`
- `doc/BACKEND_STRUCTURE.md`
- `doc/APP_FLOW.md`
- `doc/TEAM.md`
- `lessons.md`

For smaller projects, keep the same ownership model and omit only documents whose responsibilities truly do not exist.

## Quality Gate

Reject documentation systems where one file tries to be live state, task queue, roadmap, run log, failure diagnosis, and stable contract at the same time.

Every generated or updated document must state its canonical responsibility. Every current fact must have a single owner. Every run/result must have a trust level. Every task must have an acceptance gate. Every claim must have evidence boundaries.

## Reference Files

- `references/interrogation-checklist.md`: question bank for project setup, migration, and research scoping.
- `references/document-blueprints.md`: required responsibilities and sections for the canonical document set.
- `references/team-blueprint.md`: concise rules for building `doc/TEAM.md` from a heavy multi-agent example.
- `references/hard-rules.md`: conflict priority, update protocol, and forbidden shortcuts.
- `references/example-output-skeleton.md`: compact scaffold for the output files.
