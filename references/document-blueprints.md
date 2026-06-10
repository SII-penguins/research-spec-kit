# Document Blueprints

Generate or refactor the canonical document set below from user-confirmed facts. Every file must state `Canonical For:` near the top. Use `待确认项` for unresolved assumptions. Do not copy a whole status, task list, run log, or contract into a non-owner document.

## Standard Layout

```text
AGENTS.md
PROGRESS.md
TODO.md
doc/IMPLEMENTATION_PLAN.md
doc/RUN_REGISTRY.md
doc/diagnostics/*.md
doc/PRD.md
doc/FRONTEND_GUIDELINES.md
doc/BACKEND_STRUCTURE.md
doc/APP_FLOW.md
doc/TEAM.md
lessons.md
```

For smaller projects, omit documents only when their responsibility truly does not exist. Preserve the ownership model even when combining files temporarily.

Codex-first projects should use `AGENTS.md` as the canonical agent entrypoint. If the repo also needs Claude Code compatibility, create a thin `CLAUDE.md` shim that points to `AGENTS.md`; do not duplicate the rules.

## `AGENTS.md` - Entry Point and Routing Rules

Canonical for: AI operating rules, document map, read order, conflict priority, completion standard.

Update frequency: low.

Must not own: project history, long roadmap, run logs, task details, experiment diagnostics.

Required sections:

- `Status` and `Canonical For`
- `Purpose`: first entry point for AI work in the repo.
- `Minimal doc map`: one-line owner map for live state, active queue, run ledger, roadmap, stable contracts, team, lessons.
- `Read order`: usually `PROGRESS.md`, then `TODO.md`, then run/roadmap/contracts as needed.
- `Conflict rule`: cite the priority table from `hard-rules.md` in project-local form.
- `Documentation ownership`: update the document that owns the changed fact.
- `Completion standard`: tests/artifacts plus required doc updates before claiming done.
- `Forbidden actions`: no guessing, no stale TODO resurrection, no duplicate canonical state.

Optional Claude Code compatibility shim:

```markdown
# CLAUDE.md

This repo's canonical agent entrypoint is `AGENTS.md`.
Read `AGENTS.md` first and do not duplicate its routing rules here.
```

## `PROGRESS.md` - Live State and Session Bootstrap

Canonical for: live project state, resume point, current blocker, trusted evidence summary, allowed next action.

Update frequency: high.

Must not own: long history, complete run registry, long diagnostics, full roadmap, complete task queue.

Recommended size: 150-250 lines when possible.

Required sections:

- `Status`, `Last Updated`, `Canonical For`
- `0. Read-first rule`: every non-trivial session reads this first.
- `1. Current phase`: current stage and short meaning.
- `2. Current live status`: blocker, allowed next action, forbidden actions, stop-loss.
- `3. Current artifacts / roots / outputs`: concise active paths and active root summary.
- `4. Evidence trust summary`: formal, parser-backed, diagnostic, smoke-only, untrusted.
- `5. Active next queue summary`: summary pointer to `TODO.md`, not a duplicate queue.
- `6. Update protocol`: when this file must change.

## `TODO.md` - Active Queue

Canonical for: current active task queue, dependencies, ownership, blocked/unblocked state, acceptance gates.

Update frequency: medium-high.

Must not own: long project history, full run log, root registry, failure analysis, stable contracts.

Required sections:

- `Status` and `Canonical For`
- `1. Operating rule`: how to claim tasks and update state.
- `2. Current active queue`: table with ID, status, owner, scope, dependencies, acceptance, forbidden actions.
- `3. Task-claiming minimum checks`: docs/tests/artifacts to inspect before starting.
- `4. Hard stop conditions`: when to stop and ask or write diagnostics.
- `5. Handoff template`: compact end-of-task handoff.
- `6. Archive note`: where completed/old tasks go.

## `doc/IMPLEMENTATION_PLAN.md` - Master Roadmap

Canonical for: roadmap, phase history, accepted engineering record, exit criteria, stage-level blockers.

Update frequency: medium.

Must not own: current PID/path/log line, next shell command, detailed run history, active task queue.

Required sections:

- `Status` and `Canonical For`
- `0. Master roadmap`: table with Stage, Goal, Entry, Exit, Artifacts, Boundary, Status.
- `1. Current roadmap position`: stage-level explanation.
- `2. Phase history`: accepted phase transitions and what they proved.
- `3. Accepted gates`: gates passed and their meaning.
- `4. Current high-level blockers`: only blockers that affect roadmap direction.
- `5. Exit criteria`: how current stage ends.
- `6. Stop-loss / fallback`: downgrade, scope reduction, or claim change rules.
- `7. Archive index`: links to `RUN_REGISTRY.md` and diagnostics.

## `doc/RUN_REGISTRY.md` - Factual Run Ledger

Canonical for: experiment/root/smoke/parser/table/figure factual ledger and trust classification.

Update frequency: after each run/result event.

Must not own: long diagnosis, current next action, task queue, claim contract.

Required sections:

- `Status` and `Canonical For`
- `1. Purpose`: fact ledger only, not analysis.
- `2. Trust levels`: project-specific trust taxonomy.
- `3. Root / run registry`: append-oriented table.
- `4. Parser / aggregate artifacts`: table or pointers for generated formal artifacts.
- `5. Update rule`: when a run starts, ends, fails, gets parsed, or becomes formal.

Suggested registry columns:

| Date | ID | Commit | Root/output | Scope | Methods | Classification | Trust | Parser eligible? | Failure/blocker | Report |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

Suggested trust levels:

- `implementation_smoke`
- `diagnostic_probe`
- `frozen_non_promotable`
- `complete_accounting_failed_no_parser`
- `reviewer_accounting_pass_pending_parser`
- `parser_produced_formal_result`
- `paper_claim_audited`

Adapt names to the project; keep meanings crisp.

## `doc/diagnostics/*.md` - Long Failure Analysis

Canonical for: failure analysis, reviewer accounting, process audit, complex evidence diagnosis.

Update frequency: only when needed.

Must not own: current status entry point, active task queue, run ledger table.

Use diagnostics for:

- Tier 2 semantic runtime blockers.
- Tier 3 evidence/claim blockers.
- Complex reviewer accounting failures.
- Process audits or workflow failures.

Avoid diagnostics for:

- Metadata typos.
- Stale paths.
- Wrong commit hashes.
- Stale readiness text.

Recommended names:

- `doc/diagnostics/<date>_<topic>_diagnosis.md`
- `doc/diagnostics/<date>_reviewer_accounting.md`
- `doc/diagnostics/<date>_process_audit.md`

Required sections:

- `Status` and `Canonical For`
- `Summary`
- `Observed facts`
- `Root cause`
- `Impact`
- `Correction`
- `Evidence / logs / artifacts`
- `Follow-up doc updates`

## `doc/PRD.md` - Product or Research Contract

Canonical for: project goal, problem framing, core claims, scope, success metrics, narrative boundaries.

Update frequency: low.

Must not own: current root status, TODOs, logs, detailed run results, diagnostics.

Required sections:

- `Status` and `Canonical For`
- `1. Project goal`
- `2. Problem framing`
- `3. Core claims`
- `4. In scope`
- `5. Out of scope`
- `6. Success metrics`
- `7. Experiment or validation families`
- `8. Claim boundaries`
- `9. Document boundary`

For algorithm work, map every claim to an experiment family and evidence standard.

## `doc/FRONTEND_GUIDELINES.md` - Interface, Result, or Math Contract

Canonical for: user-facing behavior, result presentation, mathematical interface, state/action/objective/metric definitions. The exact meaning depends on project type.

Update frequency: low.

Must not own: progress, run failures, active tasks.

For algorithm/research projects, required sections:

- `1. Purpose`
- `2. State representation`
- `3. Conditioning interface`
- `4. Action interface`
- `5. Legality oracle`
- `6. Objective`
- `7. Evaluation metric interface`
- `8. Reporting/table/figure contract`
- `9. Document boundary`

For product/frontend projects, use the same owner principle for UI states, actions, result displays, tables, figures, and user-facing copy rules.

## `doc/BACKEND_STRUCTURE.md` - Runtime, Schema, and Evidence Contract

Canonical for: data, schema, runtime, parser, evidence, accounting, artifact contracts, backend/module boundaries.

Update frequency: low.

Must not own: active task queue, current run status, historical run table.

Required sections:

- `Status` and `Canonical For`
- `1. Contract ownership`
- `2. Repository / module layout`
- `3. Dataset / task contract`
- `4. Runtime / replay contract`
- `5. Formal accounting contract`
- `6. Artifact schema`
- `7. Parser / fail-closed rules`
- `8. Environment and reliability constraints`
- `9. Archive note`

For non-research projects, replace dataset/replay/parser with API/storage/domain evidence contracts while preserving schema ownership.

## `doc/APP_FLOW.md` - Runtime Flow

Canonical for: system operating sequence, component interaction order, data/control flow, pipeline stage order.

Update frequency: low.

Must not own: current root, blocker, task queue, claim changes.

Required sections:

- `Status` and `Canonical For`
- `1. Scope`
- `2. Canonical end-to-end flow`
- `3. Startup flow`
- `4. Runtime / training / execution flow`
- `5. Method or feature variant flow`
- `6. Evidence / output flow`
- `7. Failure and retry flow`
- `8. Reader guide`

## `doc/TEAM.md` - Multi-Agent Collaboration Protocol

Canonical for: team roles, user-facing communication routing, context boundaries, concurrency limits, permission routing, no-overlap declarations, evidence handoff, and multi-agent completion standards.

Update frequency: medium.

Must not own: project state, root history, claims, math interface, run facts, or a long-lived team log.

Read `references/team-blueprint.md` before drafting a serious `TEAM.md`.

Required sections:

- `Status` and `Canonical For`
- `1. Purpose`
- `2. Operating model`: leader, implementation/research lanes, reviewer, optional elastic workers.
- `3. Communication rule`: user-facing project content flows through leader; direct cross-agent alignment is technical only.
- `4. Concurrency tiers`: default, heavy, and burst limits with rules for when each is allowed.
- `5. Context-boundary first rule`: split by ownership and mental model, not by role title.
- `6. No-overlap declaration`: required fields before parallel work.
- `7. Role protocols`: leader coordinates; implementation lanes edit; reviewer is read-only by default.
- `8. Permission behavior`: permission approval is execution authorization, not scope approval.
- `9. Documentation update ownership`: team messages are transient; stable facts go to canonical docs.
- `10. Structured handoffs`: researcher, reviewer, and leader finalization templates.
- `11. Long-running continuity`: normalization before the next staged task and after resume.
- `12. Verification thresholds by claim type`
- `13. When not to split`
- `14. Completion standard`

## `lessons.md` - Real Mistakes and Corrections

Canonical for: real mistakes, causes, corrections, future prevention rules.

Update frequency: low.

Must not own: roadmap, task queue, experiment history, rule encyclopedia.

Entry format:

```markdown
## YYYY-MM-DD - Short title

Mistake:
Cause:
Correction:
Future rule:
```
