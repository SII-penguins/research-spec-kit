# Interrogation Checklist

Use this checklist before creating, migrating, or substantially updating a complex project documentation system. Ask only the highest-impact unanswered questions first. If an answer is not yet knowable, mark it as `待确认项` in the canonical owner document instead of guessing.

## Documentation System Intent

- Is this a new project, an existing project migration, or a repair of stale/conflicting docs?
- Is the project primarily algorithm research, product engineering, data/ML experimentation, paper writing, multi-agent execution, or a hybrid?
- What is the minimum document set needed now, and which responsibilities do not exist yet?
- Should the docs be created in the repo root, under `doc/`, or in another project-specific location?
- Is backward compatibility with existing filenames required?

## Canonical Ownership

- What facts currently have multiple conflicting homes?
- Which file owns current live state?
- Which file owns active task order?
- Which file owns run/result history?
- Which file owns roadmap and phase interpretation?
- Which files own stable contracts such as claim, math/interface, runtime, schema, evidence, or user-facing behavior?
- What facts should only be summarized or linked from other docs?

## Live State and Resume Point

- What phase is the project in right now?
- What is the current blocker?
- What is the next allowed action?
- What actions are currently forbidden?
- What stop-loss rule should prevent endless debugging or over-auditing?
- What paths, branches, roots, artifacts, or environments are active right now?
- Which state belongs in `PROGRESS.md` and should not be duplicated elsewhere?

## Task Queue

- What concrete tasks are active?
- What is the ordering and dependency chain?
- Who owns each task: user, main agent, subagent, reviewer, external system, or unassigned?
- What acceptance gate proves each task is done?
- What is forbidden for each task?
- Which tasks are blocked, and what unblocks them?
- Which old TODOs should be archived instead of carried forward?

## Roadmap

- What are the project stages from start to final delivery?
- What are the entry and exit criteria for each stage?
- Which stage is current?
- Which gates have already passed, and what do they mean?
- What high-level blockers affect roadmap direction?
- What fallback or scope reduction applies if a stage fails?
- Which historical phase notes belong in `IMPLEMENTATION_PLAN.md`, not `PROGRESS.md` or `TODO.md`?

## Run and Evidence Ledger

- What counts as a run/root/experiment/parser/table/report event in this project?
- What trust levels are needed: smoke, diagnostic, complete-but-not-promotable, parser-backed, audited, formal result, etc.?
- Which runs have already happened?
- Which runs are trusted, smoke-only, diagnostic-only, failed, or parser-eligible?
- What artifact paths prove each run's status?
- Which long explanations belong in diagnostics instead of the run registry table?

## Diagnostics and Lessons

- Which failures need a long diagnostic report?
- Is the failure a small metadata/stale-path issue or a semantic/runtime/evidence/process blocker?
- What diagnostic filename convention should be used?
- Which mistake should become a durable `lessons.md` entry?
- Which analysis should be linked rather than copied into live state or task docs?

## Stable Contracts

- What is the project goal and claim boundary?
- What is in scope and out of scope?
- What user-facing, math/interface, data, schema, runtime, evidence, parser, or accounting contracts exist?
- Which contracts are stable enough to live in PRD/FRONTEND/BACKEND/APP_FLOW?
- What changes to stable contracts require explicit user confirmation?
- Which claims cannot be made from current evidence?

## Team and Multi-Agent Work

- Will multiple agents, reviewers, or humans work concurrently?
- What roles exist: leader, researcher-core, researcher-exp, reviewer, implementer, operator?
- Which roles can edit code, run experiments, review, or update docs?
- What files or subsystems must not be touched concurrently?
- What handoff template is required?
- What are the GPU/CPU/cloud/local resource boundaries?
- Who is the only user-facing project-content interface?
- Is leader allowed to edit production code/tests, or is leader coordination-only?
- Which roles are stable resident roles, and which are elastic short-task workers?
- What concurrency tiers are allowed for daily, heavy, and burst work?
- What no-overlap declaration fields are mandatory before parallel assignments?
- What does permission approval authorize, and what does it explicitly not authorize?
- When should reviewer remain read-only, and what evidence must reviewer check before completion?
- What stale team state must be normalized before the next staged task?
- What claim types need distinct verification thresholds?
- When should work not be split even if extra agents are available?

## Algorithm/Experiment Specifics

Ask these when the project involves research claims, model training, benchmarks, or reproducible experiments:

- What exact research problem is being studied?
- What is the main claim, and what evidence would falsify it?
- What are the task input, output, and valid/invalid examples?
- Where does data come from, and what schema/split/leakage rules apply?
- What baselines are required, and what makes them fair?
- What metrics are primary/secondary, how are they computed, and how are they aggregated?
- What run modes exist: smoke, dev, report, full?
- What compute budget and failure-handling rules apply?
- Which conclusions are explicitly forbidden?

## Update Ownership

Before editing, identify which file owns the fact being changed:

- Current blocker or next action: `PROGRESS.md`, `TODO.md`
- Task status or acceptance gate: `TODO.md`
- Run/root/parser/table/figure facts: `doc/RUN_REGISTRY.md`
- Long failure diagnosis: `doc/diagnostics/*.md`
- Roadmap stage or exit criteria: `doc/IMPLEMENTATION_PLAN.md`
- Stable claim/interface/schema/runtime/team contract: the relevant contract doc
- Real mistake and future prevention rule: `lessons.md`
