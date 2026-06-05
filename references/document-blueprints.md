# Document Blueprints

Generate the eight files below from user-confirmed answers. Use `待确认项` for unresolved assumptions. Cross-reference documents so each file plays a distinct role.

## `PRD.md` - Algorithm Research Requirements

Purpose: define the research contract.

Required sections:

- `研究问题定义`: exact problem, motivation, target users, and task boundary.
- `任务输入与输出`: input schema, output schema, valid examples, invalid examples.
- `核心 Claim`: main claim, secondary claims, forbidden claims.
- `Claim 到实验映射`: each claim mapped to required experiments and metrics.
- `方法目标与边界`: what failure mode the method addresses, assumptions, dependencies.
- `版本范围`: MVP, standard version, enhanced version.
- `In Scope`: included tasks, datasets, baselines, experiments, artifacts.
- `Out of Scope`: excluded tasks, claims, datasets, deployment settings.
- `成功标准`: metric thresholds, artifact completeness, reproducibility gates.
- `失败标准`: conditions that invalidate the claim or block progress.
- `指标定义`: primary and secondary metrics with formulas or exact computation rules.
- `风险与缓解`: data, method, compute, reproducibility, evaluation, leakage risks.
- `Open Questions / 待确认项`: unresolved choices.

## `APP_FLOW.md` - Algorithm and Experiment Flow

Purpose: define how experiments move from data to artifacts.

Required sections:

- `Top-Level Pipeline`: full lifecycle from data ingestion to report generation.
- `数据准备流程`: trigger, inputs, steps, outputs, success state, error state.
- `数据清洗与划分流程`: split strategy, leakage checks, invalid data handling.
- `Baseline 训练流程`: per-baseline config, training, checkpoint, outputs.
- `核心算法训练流程`: proposed method stages and failure handling.
- `推理流程`: inputs, model loading, batch behavior, outputs.
- `评估流程`: metric computation, aggregation, artifacts.
- `消融实验流程`: what each ablation removes or changes, expected artifact.
- `鲁棒性实验流程`: stress conditions, perturbations, distribution shifts.
- `结果聚合流程`: merge per-run artifacts into tables and figures.
- `报告生成流程`: map artifacts to report sections.
- `异常处理`: corrupted data, OOM, non-convergence, failed run, missing artifact.

For each flow, include trigger, input, output, stage steps, success condition, error condition, and artifact path.

## `TECH_STACK.md` - Technology Stack and Environment

Purpose: make the environment reproducible.

Required sections:

- `Languages`: Python/Julia/C++/R versions.
- `Training Framework`: PyTorch, JAX, TensorFlow, Lightning, or other framework and version.
- `Model Libraries`: Transformers, Diffusers, TRL, domain libraries, candidate versions.
- `Scientific Computing`: NumPy, SciPy, Pandas, Polars, scikit-learn, etc.
- `Domain Tools`: RDKit, OpenMM, Qiskit, PyBaMM, QuTiP, NetworkX, or project-specific tools.
- `Configuration`: Hydra, OmegaConf, YAML, CLI conventions.
- `Experiment Tracking`: local JSONL, MLflow, W&B, TensorBoard, or disabled.
- `Data Versioning`: DVC, git-lfs, checksums, manual manifest.
- `Testing`: pytest and smoke-test commands.
- `Hardware`: CPU/GPU/CUDA/driver/memory/storage expectations.
- `Install Commands`: environment creation and package installation.
- `Smoke Test`: commands that prove imports, GPU, data load, minimal train, minimal eval.
- `Version Change Rules`: how dependency changes are proposed and recorded.

## `FRONTEND_GUIDELINES.md` - Result Presentation and Reporting

Purpose: prevent misleading, inconsistent, or unreproducible result presentation. This is not a web frontend guide unless the project truly has a UI.

Required sections:

- `主结果表`: columns, metric order, dataset order, method order, seed display.
- `Baseline Comparison Table`: baseline names, fairness controls, metric display.
- `Ablation Table`: one change per row, contribution isolated.
- `Robustness Table`: stress condition, perturbation level, metric change.
- `Dataset Statistics Table`: split sizes, label distribution, missing data, filters.
- `Failure Case Table`: input id, failure type, model output, expected output, diagnosis.
- `Metric Naming`: canonical names, units, directionality.
- `Figure Rules`: when to use line, bar, box, scatter, heatmap, or calibration plot.
- `Axes and Legends`: labels, units, scales, sorting, legend placement.
- `Uncertainty`: error bars, confidence intervals, seed aggregation.
- `Artifact Mapping`: which JSON/CSV/NPY/log files create each table or figure.
- `Report Structure`: main text sections and appendix sections.
- `Forbidden Displays`: decorative charts, inconsistent metric names, missing seeds, cherry-picked examples.

## `BACKEND_STRUCTURE.md` - Algorithm System Structure

Purpose: define the reproducible algorithm system, not a web backend.

Required sections:

- `Repository Layout`: directories and ownership.
- `Data Directories`: `data/raw`, `data/interim`, `data/processed`, `data/splits`.
- `Data Schema`: raw record, processed record, split manifest.
- `Training Sample Schema`: fields consumed by model/trainer.
- `Prediction Output Schema`: per-sample output fields and metadata.
- `Evaluation Result Schema`: metrics, aggregation, run metadata.
- `Artifact Schema`: checkpoints, predictions, metrics, plots, reports, logs.
- `Model Modules`: model construction and forward/inference responsibilities.
- `Dataset Loader`: parsing, validation, batching, transforms.
- `Preprocessing`: cleaning, feature construction, split creation.
- `Trainer`: loop, optimization, checkpoint, seed, failure handling.
- `Loss / Reward / Oracle`: formulas, interfaces, caching if applicable.
- `Evaluator`: metric computation and aggregation.
- `Reporting`: table/figure generation from artifacts only.
- `Config Groups`: model, data, train, eval, baseline, experiment, report, paths.
- `Logging Rules`: JSONL fields, console logs, error logs.
- `Checkpoint Rules`: naming, save frequency, best/latest, retention.
- `Testing Structure`: unit, integration, smoke, regression.
- `Dependency Boundaries`: modules that must not import each other.

## `IMPLEMENTATION_PLAN.md` - Build and Experiment Plan

Purpose: define execution order and gates.

Required sections:

- `Milestones`: numbered phases from project skeleton to full experiments.
- `Task Breakdown`: each task has inputs, outputs, files touched, commands, acceptance criteria.
- `Smoke Test Plan`: smallest commands that verify environment, data load, train, eval, report.
- `MVP Experiment Plan`: minimal credible run proving pipeline connectivity.
- `Standard Experiment Plan`: required baseline, core method, ablation, robustness experiments.
- `Full Experiment Plan`: multi-seed or full-scale runs after gates pass.
- `Baseline Order`: simplest baseline first, strongest baseline later.
- `Ablation Order`: isolate claimed contribution before optional variants.
- `Robustness Order`: cheapest stress tests before expensive ones.
- `Result Generation Order`: metrics first, tables second, figures third, report last.
- `Fallbacks`: what to do after OOM, non-convergence, bad data, failed baseline.
- `No-Skip Gates`: tests or artifacts required before moving to the next milestone.

Avoid vague tasks. Prefer concrete tasks like: implement `src/project/algorithms/foo.py`; input `ProcessedBatch`; output `PredictionBatch`; test `tests/test_foo.py`; run `python -m project.train experiment=foo_smoke`; artifact `artifacts/runs/foo_smoke/metrics.json`.

## `CLAUDE.md` - AI Operation Manual

Purpose: tell every AI session how to work in this project.

Required sections:

- `Project Summary`: concise research goal and boundary.
- `Must Read First`: ordered list of project docs and `progress.txt`.
- `Non-Negotiable Rules`: no guessing, no code before docs/gates, no unverified claims.
- `Algorithm Boundary`: what the method may and may not do.
- `Tech Stack Summary`: versions and config rules.
- `Naming Conventions`: experiment ids, config names, artifact names.
- `Artifact Rules`: every conclusion must cite an artifact path.
- `Baseline Rules`: allowed baselines and fairness controls.
- `Testing Rules`: commands required before claiming completion.
- `Reporting Rules`: table/figure conventions.
- `Forbidden Actions`: hardcoding experiment settings, notebook-only reproduction, deleting artifacts, claiming smoke results as formal results.
- `Session Start Checklist`: read docs, read progress, inspect git status, identify next gate.
- `Session End Checklist`: update progress, list artifacts, record failures.

## `progress.txt` - Progress Memory and Handoff

Purpose: preserve cross-session state.

Required sections:

- `Current Status`: one-paragraph state of the project.
- `Completed`: modules, docs, tests, experiments finished.
- `In Progress`: active task and current blocker.
- `Next Actions`: ordered next steps.
- `Experiments Run`: id, mode, command, date, seed, artifact path, status.
- `Trusted Results`: results that passed gates.
- `Smoke Only Results`: results not eligible for formal claims.
- `Failures`: failed runs, cause, mitigation, retry plan.
- `Open Questions`: unresolved assumptions.
- `Environment Notes`: machine, dependency, data, compute notes.
- `Last Updated`: timestamp and author/session note.
