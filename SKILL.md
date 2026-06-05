---
name: research-spec-kit
description: Create rigorous specification documents for algorithm design and experimental research projects. Use when the user wants to plan a reproducible research system, write PRD/APP_FLOW/TECH_STACK/FRONTEND_GUIDELINES/BACKEND_STRUCTURE/IMPLEMENTATION_PLAN/CLAUDE.md/progress.txt, define claims, baselines, metrics, artifacts, experiment gates, or force assumption interrogation before coding.
---

# Research Spec Kit

Use this skill to turn an algorithm or experimental research idea into a reproducible project documentation system. The Chinese working name is "研究八件套": six project specification documents plus `CLAUDE.md` and `progress.txt`.

## Core Rule

Before writing code, training scripts, experiment scripts, or final specification documents, interrogate the user's research idea until no critical assumption remains unresolved. Do not fill gaps with plausible guesses.

If the user asks to create the document set immediately, first identify missing assumptions and ask the highest-impact questions. Draft only when enough answers exist; otherwise create explicit `待确认项` entries.

## Workflow

1. Read `references/interrogation-checklist.md`.
2. Ask grouped, high-signal questions about the research problem, claim, task definition, data, baseline, method, metrics, experiments, compute budget, boundaries, and forbidden conclusions.
3. Continue questioning until critical assumptions are answered or explicitly marked as `待确认项`.
4. Read `references/document-blueprints.md` before generating the eight files.
5. Apply `references/hard-rules.md` as a final quality gate.
6. Use `references/example-output-skeleton.md` only as an output scaffold; never invent project-specific content from it.
7. Write or update `progress.txt` as the cross-session handoff layer.

## Required Outputs

Generate or update these files in the project root unless the user specifies another location:

- `PRD.md`
- `APP_FLOW.md`
- `TECH_STACK.md`
- `FRONTEND_GUIDELINES.md`
- `BACKEND_STRUCTURE.md`
- `IMPLEMENTATION_PLAN.md`
- `CLAUDE.md`
- `progress.txt`

## Quality Gate

Every generated document must be concrete enough for another agent to continue without guessing. Each module, experiment, and task must include responsibilities, inputs, outputs, acceptance criteria, and unresolved items where applicable.

Reject vague sections such as "train model", "evaluate", "compare with baseline", or "generate report" unless they define configuration, metrics, artifacts, paths, and success/failure states.

## Reference Files

- `references/interrogation-checklist.md`: question bank for Planning mode.
- `references/document-blueprints.md`: required sections for the eight documents.
- `references/hard-rules.md`: non-negotiable constraints and forbidden shortcuts.
- `references/example-output-skeleton.md`: compact skeleton for the output files.
