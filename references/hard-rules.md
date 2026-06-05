# Hard Rules

Apply these rules before drafting docs, writing code, running experiments, or summarizing results.

## Do Not Guess

- Do not assume the research problem, claim, data, baseline, metric, compute budget, or conclusion boundary.
- Mark unresolved items as `待确认项`.
- Ask follow-up questions before creating final docs when a missing assumption changes project direction.

## Bind Claims to Evidence

- Every claim must map to at least one required experiment.
- Every required experiment must define inputs, config, metrics, artifacts, and acceptance criteria.
- Every result statement must cite an artifact path.
- Do not write conclusions without generated artifacts.

## Define Baselines Precisely

- Do not write "baseline" without names.
- For each baseline, define config, data, budget, seed, preprocessing, training/inference mode, output artifact, and fairness control.
- Compare methods under shared evaluation code unless the user explicitly accepts a different protocol.

## Define Evaluation Precisely

- Do not write "evaluate" without metrics.
- Define metric formula or exact computation process.
- Define aggregation across samples, seeds, folds, datasets, and scenarios.
- Define whether higher or lower is better.
- Define table/figure names and artifact paths.

## Define Training Precisely

- Do not write "train model" without model, data, loss, optimizer, scheduler, seed, batch size, epoch/step budget, checkpoint rules, and failure handling.
- Put model names, paths, thresholds, weights, budgets, random seeds, batch sizes, and learning rates in config.
- Do not hardcode experiment settings in source code.

## Separate Run Modes

- Label `smoke`, `dev`, `report`, and `full` modes explicitly.
- Do not treat smoke-test outputs as formal results.
- Require no-skip gates before scaling experiments.

## Preserve Reproducibility

- Notebook work is allowed only for exploration, visualization, or failure analysis.
- Notebook output cannot be the only reproduction path.
- Use CLI commands, config groups, and artifact paths as the reproducible interface.
- Track progress in `progress.txt`, not conversation memory.

## Control Scope

- Do not add dependencies to look sophisticated.
- Do not expand experiments unless they support a claim.
- Do not invent directory structures, filenames, or module boundaries after `BACKEND_STRUCTURE.md` exists.
- Do not claim generalization to datasets, domains, users, or deployment settings outside the agreed scope.

## Final Review Gate

Before handing off generated docs, verify:

- All eight files exist or are explicitly planned.
- Critical unknowns are marked as `待确认项`.
- Each module has input, output, responsibility, and acceptance criteria.
- Each experiment serves a claim.
- Each metric has computation and aggregation rules.
- Each result path is an artifact path, not a prose promise.
- `progress.txt` names current status, next action, trusted results, smoke-only results, failures, and open questions.
