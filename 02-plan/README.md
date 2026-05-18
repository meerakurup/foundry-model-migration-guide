# 02 · Plan

> **Goal:** With your inventory in hand from [01-discover](../01-discover/), decide **what to migrate**, **what to migrate it to**, **when**, and **in what order** — before you touch code.

## Status

🚧 **Placeholder.** Content lands here in **Phase 4** of the consolidation rollout. See [`docs/internal/`](../docs/internal/) for sequencing.

## What will live here

- `README.md` — the 6-phase planning narrative (Discovery → Delta → Deployment → Eval → Perf → Rollout).
- `migration-paths.md` — model-pair migration guidance (e.g., 4o → 4.1, 4o → 5.x, 4o → o-series).
- `retirement-timeline.md` — **single canonical source** for retirement dates across the repo.
- `decision-matrix.md` — synthesized chooser (4o / 4.1 / 5.x / o-series) factoring quality, cost, latency, capability, capacity.
- `availability-tracker/` — automated availability monitor: snapshot pipeline, GitHub Actions, region/SKU dashboard. Pair with `retirement-timeline.md` to see *what's retiring* alongside *what's available right now*.

## Where the output goes next

A finalized plan from this section hands off to:

- [`../03-migrate-code/`](../03-migrate-code/) — apply the API and parameter changes the plan calls for.
- [`../04-evaluate/`](../04-evaluate/) — build golden datasets for the chosen source → target pairs.
