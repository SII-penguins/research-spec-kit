# TEAM.md Blueprint

Use this when drafting or refactoring `doc/TEAM.md`. The goal is not to create bureaucracy. The goal is to prevent multi-agent work from turning into duplicated exploration, stale owners, hidden scope changes, and unverifiable handoffs.

## Core Positioning

`doc/TEAM.md` is the canonical contract for how humans and agents collaborate. It owns:

- role boundaries,
- user-facing communication routing,
- concurrency limits,
- no-overlap declarations,
- permission routing,
- evidence handoff,
- reviewer authority,
- long-running team continuity.

It does not own current project status, active task queue, run history, stable product claims, math/interface definitions, or backend/schema contracts. Those belong to `PROGRESS.md`, `TODO.md`, `RUN_REGISTRY.md`, and the stable contract docs.

## Non-Negotiable Team Rules

Use these as the compact heart of most `TEAM.md` files:

1. User-facing project content flows through `leader`.
2. `leader` coordinates, assigns, integrates, reports, and updates canonical docs.
3. `leader` does not become the default production-code/test owner once implementation lanes are active.
4. Implementation lanes own bounded edit contexts.
5. Reviewer owns independent verification and is read-only by default.
6. Parallel work requires a no-overlap declaration.
7. Work is split by context boundary, not by role title or available concurrency.
8. Permission approval is not scope approval.
9. Durable facts go to canonical docs, not team chat, panes, or scratch logs.
10. Every non-trivial assignment ends with a structured handoff.

## Recommended Roles

Adapt names to the project. Keep responsibilities crisp.

| Role | Main function | User-facing? | Default boundary |
| --- | --- | --- | --- |
| `leader` | Coordination, task framing, risk control, assignment, integration, final reporting | yes | Does not default to production code/tests |
| implementation lane | Code, model, system, or core method implementation | no | Edits only assigned files/modules |
| experiment/product lane | Experiments, artifacts, launchers, parser/report pipeline, or product-output preparation | no | Does not assume unstable interfaces |
| `reviewer` | Independent review, tests, regression checks, evidence assessment, claim audit | no | Read-only unless reassigned |
| elastic worker | Bounded short task: grep, log triage, artifact check, focused test, doc sync | no | Short-lived and subordinate to a stable owner |

The role names are coordination handles. They are not a reason to split work.

## Communication Rule

Define the communication graph explicitly:

- User gives requirements, corrections, and decisions to `leader`.
- `leader` translates user intent into bounded assignments.
- Non-leader agents report findings, blockers, evidence, and completion status to `leader`.
- Direct cross-agent coordination is allowed only for concrete technical alignment inside the leader-authorized boundary.
- Direct coordination must not expand scope, change architecture/schema/contracts, authorize risky verification, or decide final completion.
- If a user gives project-content guidance in a non-leader window, that agent routes it to `leader`.
- User approval of a permission prompt in a subagent window is only tool execution approval.

## Concurrency Tiers

Use tiers so "more agents" does not quietly become "less ownership".

| Tier | Active workers | Use when | Required guardrail |
| --- | ---: | --- | --- |
| Default | 1-4 | Normal implementation, focused review, doc sync | Prefer one edit owner plus reviewer |
| Heavy | 5-8 | Independent modules, tests, docs, artifact checks | Leader writes no-overlap declaration |
| Burst | 10-20 | Short read-only sweeps, log triage, inventory, claim-specific review shards | Short-lived, rate-limited, retry-capped, mostly read-only |

If API, runtime, quota, permissions, or user preference impose a lower limit, reduce active work instead of creating hidden parallelism.

## Context-Boundary First Rule

Before assigning parallel work, leader classifies the context:

| Context shape | Recommended shape |
| --- | --- |
| One bug, one local path, one mental model | One implementation owner; review after patch |
| Implementation plus independent regression surface | Implementation owner plus reviewer |
| Core implementation plus independent artifact/report preparation | Separate owners only if interface boundary is stable |
| Experiment/report pipeline plus artifact checks | Experiment/product owner plus reviewer or artifact worker |
| Architecture decision spanning contracts | Leader coordinates; review after stable proposal |
| Same files or same evolving failure mode | Do not parallelize |
| Independent modules with clear contracts | Parallelize only after no-overlap declaration |
| Read-only sweep or artifact inventory | Elastic workers allowed with timeout/backoff/retry cap |

## No-Overlap Declaration

Require this before parallel work:

```text
Context boundary:
Concurrency tier:
Active roles:
Role A may edit:
Role A may inspect:
Role B may edit:
Role B may inspect:
Reviewer may inspect/run:
Files/functions nobody may touch without renewed leader approval:
Canonical docs to read:
Allowed commands/resources:
Request spacing / backoff / timeout / retry cap if burst:
Stop conditions:
Handoff required:
```

## Role Protocols

Leader:

- Reads the project agent entrypoint (`AGENTS.md` by default), `PROGRESS.md`, `TODO.md`, and relevant owner docs before non-trivial assignment.
- Defines context boundary, concurrency tier, active slots, allowed/forbidden files, verification expectations, and stop conditions.
- Integrates handoffs and decides whether evidence supports the user-facing claim.
- Updates canonical docs owned by changed facts.
- Inspects git status or requires the edit owner to report it before implementation assignments.

Implementation or experiment lane:

- Works only from leader assignment.
- Diagnoses before editing.
- Edits only inside assigned boundary.
- Runs the smallest meaningful verification.
- Stops if work requires contract, architecture, scope, resource, or file-boundary changes.
- Reports files changed, commands run, results, not-run reasons, risks, and doc-impacting facts to leader.

Reviewer:

- Starts from the assigned claim, diff summary, and evidence.
- Verifies against relevant canonical docs and acceptance gates.
- Reports pass/fail by claim, files inspected, commands run, blocking issues, missing evidence, and suggested doc updates.
- Does not implement fixes unless leader explicitly reassigns implementation ownership.

## Permission Behavior

TEAM.md must separate execution permission from project scope:

- Permission prompt approval lets the assigned action run inside the existing boundary.
- It does not approve new requirements, new output roots, long-running jobs, destructive operations, dependency changes, schema/contract changes, or positive claims.
- Destructive git actions, file deletion, force push, broad cleanup, dependency downgrade/removal, shared-state mutation, and expensive formal runs require explicit user approval through leader.
- If permission routing points to an old team, missing leader, stale inbox, or dead pane, stop and normalize team ownership.

## Documentation Ownership

Canonical doc updates are leader-routed by default:

- Non-leader agents report doc-impacting facts in handoff.
- Leader promotes only durable facts into canonical docs.
- Team chat, tmux panes, task messages, and transcripts are temporary coordination state.
- Do not create long-lived `TEAM_LOG.md`, `AGENT_LOG.md`, or `SCRATCH.md` unless explicitly required; if used, mark it temporary and summarize durable facts into canonical docs.

## Structured Handoffs

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

## Long-Running Continuity

For long work, preserve continuity through canonical docs and handoffs, not through panes or chat history.

Leader should normalize the team before the next staged task, after a long pause, after resume, or after meaningful completion:

- Re-read `PROGRESS.md`, `TODO.md`, and relevant owner docs.
- Inspect active team members, prompts, owners, dead panes, and stale task IDs.
- Decide whether to re-brief, clean up, or recreate the team.
- Reset stale ownership.
- Reissue no-overlap declarations.
- Verify git status and active file state before trusting old handoff notes.

## Verification Thresholds

Define minimum evidence by claim type. Example:

| Claim type | Minimum evidence |
| --- | --- |
| Documentation-only update | Relevant diff reviewed; no canonical-owner conflict introduced |
| Small code bugfix | Focused test, reproduction check, or direct behavior check |
| Runtime path change | Focused regression plus smoke run when feasible |
| Training/profiling claim | Command, environment, resource assumptions, log path, observed output |
| Formal experiment claim | Standard workflow, retained logs/artifacts, run-registry update, reviewer/accounting evidence |
| Architecture/method claim | Canonical docs checked; implementation drift stated; no smoke result presented as full proof |

## When Not to Split

Do not split work when:

- one causal chain is needed from symptom to fix,
- multiple agents would edit the same file/function,
- reviewers would have to rediscover the whole implementation context,
- the work is mostly wording and extra agents would only bikeshed,
- architecture/contracts are still changing,
- the split would reduce ownership clarity, review quality, or verification strength.

## Compact TEAM.md Template

```markdown
# TEAM.md

Status: Active
Canonical For: Agent team coordination, role boundaries, concurrency limits, permission routing, and evidence handoff.

## 1. Purpose

Define how humans and agents collaborate on this project.

## 2. Non-negotiable rules

1. User-facing project content goes through `leader`.
2. `leader` coordinates; implementation lanes edit.
3. Reviewer is read-only unless reassigned.
4. Parallel work requires a no-overlap declaration.
5. Permission approval is not scope approval.
6. Durable facts go to canonical docs.

## 3. Roles

| Role | Responsibility | Boundary |
| --- | --- | --- |
| leader | Coordinate, assign, integrate, report | Not default code owner |
| implementer | Assigned implementation context | Assigned files only |
| reviewer | Independent verification | Read-only by default |

## 4. Communication rule

User <-> leader <-> agents. Direct agent alignment is technical only and must be summarized to leader.

## 5. Concurrency and no-overlap

State tier, active roles, editable/inspectable files, forbidden files, allowed commands, and stop conditions before parallel work.

## 6. Role protocols

Define leader, implementer, reviewer responsibilities and hard stops.

## 7. Permission behavior

Permission prompts authorize execution only inside the assigned boundary.

## 8. Documentation ownership

Leader promotes durable facts to canonical docs; temporary team context is not durable memory.

## 9. Handoff templates

Include implementer, reviewer, and leader finalization handoffs.

## 10. Completion standard

Task completes only when owner finishes/stops, reviewer evidence matches the claim, blockers are documented, and canonical docs are updated when needed.
```
