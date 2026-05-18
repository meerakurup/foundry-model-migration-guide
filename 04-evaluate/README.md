# 04 · Evaluate

> **Goal:** Prove the migrated app behaves at least as well as the original — and catch regressions before they hit production — with reusable golden datasets, an evaluator SDK, and Azure AI Foundry result tracking.

## Status

🚧 **Placeholder.** Content lands here in **Phase 2** (seed) and **Phase 6** (reconciliation) of the consolidation rollout. See [`docs/internal/`](../docs/internal/) for sequencing.

## What will live here

- `README.md` — evaluation methodology, LLM-as-Judge patterns, Foundry result tracking.
- `data/` — 54 pre-built golden test cases spanning 7 scenarios (RAG, classification, tool calling, structured output, multi-turn, etc.).
  - `data/templates/` — dataset starter templates for teams building their own.
- `src/evaluate/` — the `MigrationEvaluator` Python SDK.
- `samples/rag_pipeline/` — self-contained RAG demo with swappable model stages, dual-layer evaluation, A/B comparison, drift analysis.
- `notebooks/` — `azure_openai_migration_technical.ipynb`, `azure_openai_evaluation_guide.ipynb`.
- `docs/` — `building-golden-datasets.md`, `evaluation-guide.md`, `migrating-multi-step-apps.md`, `cloud-eval-tracking-across-models.md`.

## CI integration

Nightly evaluation runs land in [`../.github/workflows/eval-on-schedule.yml`](../.github/workflows/), wired to publish results to Azure AI Foundry for trend tracking across migrations.

## Where the output goes next

A green evaluation gate hands off to:

- [`../05-rollout/`](../05-rollout/) — canary, observability, and rollback for the production cutover.
