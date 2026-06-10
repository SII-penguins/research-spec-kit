# Example Output Skeleton

Use this as a compact scaffold only. Replace placeholders with user-confirmed project details. Do not invent project-specific state.

## `CLAUDE.md`

~~~markdown
# CLAUDE.md

Status: Active
Canonical For: AI operating rules and document routing

## Purpose
This is the first entrypoint for AI work in this repo.

## Minimal doc map
- Live state / session bootstrap: `PROGRESS.md`
- Active task queue: `TODO.md`
- Run / experiment / parser ledger: `doc/RUN_REGISTRY.md`
- Roadmap / phase history / exit criteria: `doc/IMPLEMENTATION_PLAN.md`
- Product / claim / scope: `doc/PRD.md`
- Math / interface / result presentation: `doc/FRONTEND_GUIDELINES.md`
- Backend / evidence / schema: `doc/BACKEND_STRUCTURE.md`
- Runtime flow: `doc/APP_FLOW.md`
- Team coordination: `doc/TEAM.md`
- Mistakes: `lessons.md`

## Read order
1. Read `PROGRESS.md` first before non-trivial work.
2. Read `TODO.md` for current queue.
3. Read `doc/RUN_REGISTRY.md` when runs/results are involved.
4. Read `doc/IMPLEMENTATION_PLAN.md` when roadmap/phase decisions are involved.
5. Read stable contract docs only as needed.

## Conflict rule
- `PROGRESS.md` wins for current live state.
- `TODO.md` wins for current task order.
- `doc/RUN_REGISTRY.md` wins for run facts.
- `doc/IMPLEMENTATION_PLAN.md` wins for roadmap interpretation.
- Stable contract docs win for their declared contracts.

## Documentation ownership
Update the document that owns the changed fact.

## Completion standard
Do not claim completion until code/tests/artifacts are verified and owner docs are updated.
~~~

## `PROGRESS.md`

~~~markdown
# PROGRESS.md

Status: Active
Last Updated: 待确认
Canonical For: live project state, next action, session bootstrap

## 0. Read-first rule
Every non-trivial session must read this file first.

## 1. Current phase
- Phase: 待确认
- Meaning: 待确认

## 2. Current live status
- Current blocker: 待确认
- Current allowed next action: 待确认
- Current forbidden actions: 待确认
- Stop-loss: 待确认

## 3. Current artifacts / roots / outputs
| Item | Path | Status | Notes |
| --- | --- | --- | --- |
| 待确认 | 待确认 | 待确认 | 待确认 |

## 4. Evidence trust summary
- Formal / parser-backed:
- Diagnostic only:
- Smoke only:
- Untrusted:

## 5. Active next queue summary
See `TODO.md`; summary: 待确认

## 6. Update protocol
Update this file whenever live state, blocker, next action, trusted evidence, or active artifact path changes.
~~~

## `TODO.md`

~~~markdown
# TODO.md

Status: Active
Canonical For: active task queue and task claiming

## 1. Operating rule
Claim the first unblocked task unless the user redirects.

## 2. Current active queue
| ID | Status | Owner | Scope | Dependencies | Acceptance | Forbidden |
| --- | --- | --- | --- | --- | --- | --- |
| T-001 | Pending | 待确认 | 待确认 | 待确认 | 待确认 | 待确认 |

## 3. Task-claiming minimum checks
- Read `PROGRESS.md`.
- Confirm task is unblocked.
- Confirm no owner overlap.

## 4. Hard stop conditions
- Contract conflict.
- Missing artifact required for a claim.
- Semantic/evidence blocker.

## 5. Handoff template
- Completed:
- Evidence:
- Docs updated:
- Next:

## 6. Archive note
Completed historical tasks should be archived outside this active queue.
~~~

## `doc/RUN_REGISTRY.md`

~~~markdown
# RUN_REGISTRY.md

Status: Active
Canonical For: experiment/run/result factual ledger

## 1. Purpose
This file records run facts only. Long analysis belongs in `doc/diagnostics/`.

## 2. Trust levels
| Trust level | Meaning |
| --- | --- |
| implementation_smoke | Pipeline/import/minimal behavior only; not formal evidence. |
| diagnostic_probe | Run performed to inspect a failure or hypothesis. |
| parser_produced_formal_result | Parser generated formal aggregate artifacts. |

## 3. Run registry
| Date | ID | Commit | Output | Scope | Status | Trust | Eligible? | Blocker | Report |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 待确认 | 待确认 | 待确认 | 待确认 | 待确认 | 待确认 | 待确认 | 待确认 | 待确认 | 待确认 |

## 4. Generated artifacts
| Artifact | Source run | Trust | Path |
| --- | --- | --- | --- |

## 5. Update rule
Append or update rows when runs start, terminate, fail, parse, or become claim-eligible.
~~~

## `doc/IMPLEMENTATION_PLAN.md`

~~~markdown
# IMPLEMENTATION_PLAN.md

Status: Active
Canonical For: roadmap, phase history, exit criteria

## 0. Master roadmap
| Stage | Goal | Entry | Exit | Artifacts | Boundary | Status |
| --- | --- | --- | --- | --- | --- | --- |
| S0 | 待确认 | 待确认 | 待确认 | 待确认 | 待确认 | 待确认 |

## 1. Current roadmap position
待确认

## 2. Phase history
待确认

## 3. Accepted gates
待确认

## 4. Current high-level blockers
待确认

## 5. Exit criteria
待确认

## 6. Stop-loss / fallback
待确认

## 7. Archive index
- Run ledger: `doc/RUN_REGISTRY.md`
- Diagnostics: `doc/diagnostics/`
~~~

## Stable Contract Docs

Use the same header pattern for `doc/PRD.md`, `doc/FRONTEND_GUIDELINES.md`, `doc/BACKEND_STRUCTURE.md`, and `doc/APP_FLOW.md`:

~~~markdown
# <DOCUMENT_NAME>

Status: Active
Canonical For: <single owner responsibility>

## 1. Purpose
待确认

## 2. Contract / Protocol
待确认

## 3. Boundaries
待确认

## 4. Update rule
待确认
~~~

## `lessons.md`

~~~markdown
# lessons.md

## YYYY-MM-DD - Short title

Mistake:
Cause:
Correction:
Future rule:
~~~

## `doc/TEAM.md`

~~~markdown
# TEAM.md

Status: Active
Canonical For: Agent team coordination, role boundaries, concurrency limits, permission routing, no-overlap declarations, and evidence handoff.

## 1. Purpose

Define how humans and agents collaborate on this project without duplicating state or creating hidden scope changes.

## 2. Non-negotiable rules

1. User-facing project content goes through `leader`.
2. `leader` coordinates, assigns, integrates, reports, and updates canonical docs.
3. Implementation lanes own bounded edit contexts.
4. Reviewer is read-only unless explicitly reassigned.
5. Parallel work requires a no-overlap declaration.
6. Permission approval is execution authorization, not scope approval.
7. Durable facts go to canonical docs, not team chat or scratch logs.

## 3. Roles

| Role | Responsibility | User-facing? | Boundary |
| --- | --- | --- | --- |
| leader | Coordinate, assign, integrate, report | yes | Not default production-code owner |
| implementer | Assigned implementation context | no | Assigned files/modules only |
| reviewer | Independent verification | no | Read-only by default |
| elastic worker | Bounded short task | no | Short-lived and subordinate to stable owner |

## 4. Communication rule

- User <-> leader <-> agents.
- Direct agent alignment is technical only and must be summarized to leader.
- Non-leader agents do not make project-content decisions.

## 5. Concurrency tiers

| Tier | Active workers | Use case | Guardrail |
| --- | ---: | --- | --- |
| Default | 1-4 | Normal implementation and focused review | One edit owner plus reviewer |
| Heavy | 5-8 | Independent modules/tests/docs/artifacts | No-overlap declaration required |
| Burst | 10-20 | Short read-only sweeps/log triage/inventory | Timeout/backoff/retry cap; mostly read-only |

## 6. No-overlap declaration

```text
Context boundary:
Concurrency tier:
Active roles:
Each role may edit:
Each role may inspect:
Reviewer may inspect/run:
Nobody may touch:
Canonical docs to read:
Allowed commands/resources:
Stop conditions:
Handoff required:
```

## 7. Role protocols

- Leader:
- Implementer:
- Reviewer:

## 8. Permission behavior

Permission prompts authorize execution only inside the assigned boundary. They do not authorize new scope, new runs, destructive actions, dependency changes, or positive claims.

## 9. Documentation ownership

Leader promotes durable facts into canonical owner docs. Team chat, panes, transcripts, and scratch notes are transient.

## 10. Handoff templates

Researcher / implementer handoff:

```text
Assignment:
Files changed:
Behavior changed:
Verification commands:
Verification results:
Not run and why:
Risks/blockers:
Suggested doc updates:
Next suggested action:
```

Reviewer handoff:

```text
Claims reviewed:
Files inspected:
Commands run:
Pass/fail by claim:
Blocking issues:
Missing evidence:
Suggested doc updates:
Next suggested action:
```

Leader finalization:

```text
Accepted changes:
Evidence accepted:
Disagreements or unresolved risks:
Canonical docs updated/to update:
Transient context not promoted:
Next action:
User-facing summary:
```

## 11. When not to split

- Same file/function.
- Same evolving failure mode.
- Reviewer would need to rediscover the whole implementation context.
- Mostly wording/bikeshedding.
- Architecture/contracts are still changing.

## 12. Completion standard

Complete only when owner finished or stopped, reviewer evidence matches the claim, blockers are documented, and canonical docs are updated when needed.
~~~
