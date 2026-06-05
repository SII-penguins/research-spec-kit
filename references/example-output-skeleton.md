# Example Output Skeleton

Use this as a compact scaffold only. Replace placeholders with user-confirmed project details. Do not invent algorithm-specific content.

## `PRD.md`

~~~markdown
# PRD

## 研究问题定义

- Problem:
- Motivation:
- Target user:
- Boundary:
- 待确认项:

## 任务输入与输出

- Input:
- Output:
- Valid examples:
- Invalid examples:

## 核心 Claim

| Claim | Required experiment | Primary metric | Artifact |
| --- | --- | --- | --- |
| 待确认 | 待确认 | 待确认 | 待确认 |

## 成功标准

- Metric gate:
- Artifact gate:
- Reproducibility gate:

## Out of Scope

- 待确认
~~~

## `APP_FLOW.md`

~~~markdown
# APP_FLOW

## Top-Level Pipeline

1. Ingest data:
2. Validate data:
3. Build splits:
4. Train baselines:
5. Train proposed method:
6. Run inference:
7. Evaluate:
8. Aggregate artifacts:
9. Generate report:

## Flow Template

| Flow | Trigger | Input | Output | Success | Error State | Artifact |
| --- | --- | --- | --- | --- | --- | --- |
| 待确认 | 待确认 | 待确认 | 待确认 | 待确认 | 待确认 | 待确认 |
~~~

## `TECH_STACK.md`

~~~markdown
# TECH_STACK

## Runtime

- Language:
- Python version:
- CUDA / driver:
- Hardware:

## Packages

| Package | Version | Purpose | Change rule |
| --- | --- | --- | --- |
| 待确认 | 待确认 | 待确认 | 待确认 |

## Smoke Test

```bash
# 待确认
```
~~~

## `FRONTEND_GUIDELINES.md`

~~~markdown
# FRONTEND_GUIDELINES

## Main Result Table

| Column | Meaning | Source artifact |
| --- | --- | --- |
| Method | Canonical method name | config |
| 待确认 | 待确认 | 待确认 |

## Figure Rules

- Line chart:
- Bar chart:
- Box plot:
- Scatter plot:
- Heatmap:
~~~

## `BACKEND_STRUCTURE.md`

~~~markdown
# BACKEND_STRUCTURE

## Repository Layout

```text
project/
  configs/
  data/
    raw/
    interim/
    processed/
    splits/
  src/
  tests/
  artifacts/
```

## Schema Template

| Schema | Field | Type | Required | Meaning |
| --- | --- | --- | --- | --- |
| raw_record | 待确认 | 待确认 | 待确认 | 待确认 |
~~~

## `IMPLEMENTATION_PLAN.md`

~~~markdown
# IMPLEMENTATION_PLAN

## Milestone 1: Project Skeleton

| Task | Input | Output | Files | Command | Acceptance |
| --- | --- | --- | --- | --- | --- |
| 1.1 | 待确认 | 待确认 | 待确认 | 待确认 | 待确认 |

## No-Skip Gates

- Gate 1:
- Gate 2:
~~~

## `CLAUDE.md`

~~~markdown
# CLAUDE.md

## Must Read First

1. progress.txt
2. PRD.md
3. APP_FLOW.md
4. TECH_STACK.md
5. BACKEND_STRUCTURE.md
6. IMPLEMENTATION_PLAN.md
7. FRONTEND_GUIDELINES.md

## Non-Negotiable Rules

- Do not guess unresolved research assumptions.
- Do not claim results without artifact paths.
- Do not treat smoke tests as formal results.
~~~

## `progress.txt`

~~~text
Current Status
- 待确认

Completed
- None yet.

In Progress
- Specification drafting.

Next Actions
1. Resolve open questions.

Experiments Run
- None yet.

Trusted Results
- None yet.

Smoke Only Results
- None yet.

Failures
- None yet.

Open Questions
- 待确认

Last Updated
- 待确认
~~~
