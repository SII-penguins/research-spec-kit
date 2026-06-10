# Hard Rules

Apply these rules before drafting docs, writing code, running experiments, reviewing evidence, or summarizing project status.

## One Fact, One Owner

- Every project fact must have exactly one canonical owner.
- Other documents may link or summarize, but must not copy the full state, task queue, run history, diagnostic analysis, or contract.
- If two docs conflict, do not average them. Use the conflict priority below.
- If a fact has no owner, assign one before creating or updating it.
- For Codex-first projects, `AGENTS.md` is the canonical agent entrypoint. `CLAUDE.md`, if present, must be a thin compatibility shim pointing to `AGENTS.md`.

## Conflict Priority

Use this priority whenever documents disagree:

- `PROGRESS.md` wins for current live state.
- `TODO.md` wins for current task order.
- `doc/RUN_REGISTRY.md` wins for factual run/root/parser/table history.
- `doc/IMPLEMENTATION_PLAN.md` wins for roadmap and phase interpretation.
- `doc/PRD.md` wins for product/research claim narrative.
- `doc/FRONTEND_GUIDELINES.md` wins for math/interface/result presentation definitions.
- `doc/BACKEND_STRUCTURE.md` wins for schema/evidence/parser/accounting/runtime contracts.
- `doc/APP_FLOW.md` wins for runtime sequence.
- `doc/TEAM.md` wins for agent coordination.
- `AGENTS.md` wins for document reading order and AI behavior rules.
- `CLAUDE.md` must not override `AGENTS.md`; it only exists for Claude Code compatibility when needed.
- `lessons.md` wins only for recorded mistakes and remediation.

## Update Protocol

Update the owner document when the fact changes:

| Event | Must update |
| --- | --- |
| Current blocker or next action changes | `PROGRESS.md`, `TODO.md` |
| Code module completed | `PROGRESS.md`, `TODO.md`; if phase meaning changes, `doc/IMPLEMENTATION_PLAN.md` |
| Root/run starts | `PROGRESS.md`, `doc/RUN_REGISTRY.md` |
| Root/run terminates | `PROGRESS.md`, `doc/RUN_REGISTRY.md`; diagnostics if needed |
| Reviewer accounting completes | `PROGRESS.md`, `doc/RUN_REGISTRY.md`, `TODO.md`; diagnostics on failure |
| Parser runs | `PROGRESS.md`, `doc/RUN_REGISTRY.md`, `TODO.md` |
| CSV/table/figure/report generated | `PROGRESS.md`, `doc/RUN_REGISTRY.md`, `TODO.md`; roadmap if phase gate changes |
| Stage changes | `PROGRESS.md`, `TODO.md`, `doc/IMPLEMENTATION_PLAN.md` |
| Stable contract changes | Relevant `PRD` / `FRONTEND_GUIDELINES` / `BACKEND_STRUCTURE` / `APP_FLOW` doc |
| Real mistake is found | `lessons.md` |
| Multi-agent workflow changes | `doc/TEAM.md` |

## Do Not Guess

- Do not assume project state, claim, data, baseline, metric, compute budget, task order, or conclusion boundary.
- Mark unresolved items as `待确认项`.
- Ask follow-up questions only when the missing answer changes an irreversible or high-cost decision.

## Keep Docs Narrow

- `AGENTS.md` is an entrypoint, not a project encyclopedia.
- `PROGRESS.md` is live state, not a historical log.
- `TODO.md` is the active queue, not progress history.
- `IMPLEMENTATION_PLAN.md` is roadmap, not today's command list.
- `RUN_REGISTRY.md` is a factual ledger, not long diagnosis.
- Diagnostics are long analysis, not live state.
- Stable contracts must not absorb current blockers or stale TODOs.

## Evidence and Claim Rules

- Every claim must map to evidence, experiment, validation, or acceptance criteria.
- Every run/result statement must cite an artifact path or state that no artifact exists.
- Do not treat smoke outputs as formal results.
- Every run must have a trust level.
- Parser/formal result eligibility must be explicit when relevant.
- Do not write conclusions without generated artifacts.

## Task Rules

- Every active task must have an owner, dependency status, acceptance gate, and forbidden actions.
- Do not resurrect old TODOs without checking `PROGRESS.md`.
- Do not expand the task queue with nice-to-have work unless it supports the current phase or claim.
- If a task uncovers a semantic/evidence blocker, stop and route to diagnostics instead of burying the issue in TODO text.

## Team Rules

- User-facing project content must flow through the designated `leader` when a team model is active.
- `leader` coordinates, assigns, integrates, reports, and updates canonical docs; it does not become the default production-code owner once implementation lanes are active.
- Split work by context boundary, file ownership, and mental model, not by desire to use more agents.
- Parallel work requires a no-overlap declaration before assignment.
- Reviewer is read-only by default. Reviewer may challenge claims and request evidence, but must not implement fixes unless explicitly reassigned.
- Direct cross-agent coordination is a technical fast path, not a project-decision path. It must not expand scope, change architecture/contracts, authorize new files, approve risky verification, or decide final completion.
- User approval of a tool permission prompt is execution authorization only. It is not scope approval, claim approval, new-run approval, dependency approval, or permission to mutate shared state beyond the assignment boundary.
- No stale teammate, stale task owner, stale pane, stale inbox, or old assignment may block progress. Normalize or recreate the team before the next staged task.
- Do not create long-lived `TEAM_LOG.md`, `AGENT_LOG.md`, or `SCRATCH.md` as alternate memory. Promote durable facts into canonical docs and discard or archive temporary coordination notes.
- Do not split work when agents would edit the same file/function, infer the same evolving failure mode, or force the reviewer to rediscover the whole implementation context.

## Research/Experiment Rules

Use these when the project includes algorithm research, benchmarks, model training, or experiments:

- Do not write "baseline" without names, configs, fairness controls, and output artifacts.
- Do not write "evaluate" without metrics, formulas/procedures, aggregation, directionality, and artifact paths.
- Do not write "train model" without model, data, loss, optimizer, scheduler, seed, batch size, epoch/step budget, checkpoint rules, and failure handling.
- Put model names, paths, thresholds, weights, budgets, random seeds, batch sizes, and learning rates in config.
- Keep `smoke`, `dev`, `report`, and `full` modes explicitly separate.
- Notebook work is allowed for exploration, visualization, and failure analysis, not as the only reproduction path.

## Final Review Gate

Before handing off generated or migrated docs, verify:

- Each file states `Canonical For`.
- The read order and conflict priority are present.
- Current state appears in `PROGRESS.md`, not scattered through docs.
- Active tasks appear in `TODO.md`, not scattered through docs.
- Runs/results appear in `RUN_REGISTRY.md` with trust levels.
- Long failures are in `doc/diagnostics/*.md` when needed.
- Stable contracts do not contain live status pollution.
- Changed facts were updated only in their owner documents.
- Active team work, if any, has a leader-routed handoff and no unresolved owner overlap.
