# Interrogation Checklist

Use this checklist before writing code, experiment scripts, or final documents. Ask only the highest-impact unanswered questions first. Keep asking until all critical assumptions are answered or explicitly marked as `待确认项`.

## Research Problem

- What exact research problem is being studied?
- Why is this problem worth solving now?
- What existing failure mode, bottleneck, or limitation motivates the work?
- Is this a new algorithm, a modified algorithm, a benchmark study, an ablation study, or an engineering reproduction?
- Who will use the result: researchers, experiment operators, downstream developers, or domain experts?

## Core Claim

- What is the main claim the project must prove?
- What secondary claims are allowed?
- Which claims are explicitly not allowed?
- What evidence would make the main claim credible?
- What evidence would falsify or weaken the claim?
- Does every claim map to at least one required experiment?

## Task Definition

- What is the task input?
- What is the task output?
- What is the unit of prediction, generation, decision, ranking, planning, simulation, or optimization?
- What are valid and invalid examples?
- What constraints must outputs satisfy?
- What is the expected inference-time interface?

## Data

- Where does the data come from?
- Is it public, private, synthetic, simulated, or manually curated?
- What is the raw data format?
- What schema should raw, interim, processed, and split data follow?
- What fields are mandatory, optional, derived, or forbidden?
- How are train/dev/test splits created?
- What leakage risks exist?
- What data cleaning is allowed?
- What data cleaning is forbidden?
- How should missing, corrupted, duplicate, outlier, or adversarial data be handled?

## Method

- What is the proposed method?
- Which part is novel, and which part is standard engineering?
- What baseline failure mode is the method intended to fix?
- What assumptions does the method make?
- What loss, reward, oracle, simulator, planner, searcher, or evaluator does the method need?
- What hyperparameters control the method?
- Which settings must live in config files instead of code?

## Baselines

- What baseline names must be included?
- Which baseline is the minimum fair baseline?
- Which baseline is the strongest expected comparison?
- What baseline configuration makes the comparison fair?
- Which data, budget, seed, preprocessing, and evaluation conditions must be shared?
- What baseline outputs and artifact paths are required?

## Training, Inference, Evaluation

- What triggers training?
- What triggers inference?
- What triggers oracle, simulation, search, or external evaluation?
- What optimizer, scheduler, seed, batch size, epoch/step budget, checkpoint rule, and early stopping rule are expected?
- What happens when metrics do not converge?
- What happens when GPU OOM occurs?
- What happens when a run fails halfway?
- Which results count as smoke, dev, report, and full?

## Metrics

- What is the primary metric?
- What are secondary metrics?
- What metric formulas or exact computation procedures are required?
- How are metrics aggregated across samples, datasets, seeds, folds, or scenarios?
- Are higher values better or lower values better?
- What confidence intervals, standard deviations, standard errors, or significance tests are required?
- What metric names must appear in tables and artifacts?

## Experiments

- Which experiments are required to prove the main claim?
- Which experiments are required for baseline comparison?
- Which ablations isolate the claimed contribution?
- Which robustness tests are required?
- Which failure analysis is required?
- Which experiments are optional nice-to-haves?
- What is the exact artifact path for each result?
- What minimum evidence allows the project to move from MVP to standard to full?

## Compute and Operations

- What CPU, GPU, memory, storage, runtime, and budget limits apply?
- What is the maximum acceptable run time for smoke, dev, report, and full modes?
- Are remote clusters, cloud jobs, local workstations, or notebooks allowed?
- What environment constraints are fixed?
- What reproducibility constraints apply to random seeds and deterministic kernels?

## Scope Boundaries

- What is explicitly in scope?
- What is explicitly out of scope?
- What dependencies are not allowed?
- What datasets, domains, user groups, or deployment settings are not covered?
- What conclusions cannot be claimed from the planned experiments?

## Handoff State

- What has already been implemented?
- What experiments have already run?
- Which results are trusted?
- Which results are smoke tests only?
- Which failures are known?
- What should the next session read first?
