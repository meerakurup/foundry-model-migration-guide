# 05 · Roll out

> **Goal:** Ship the migrated app to production safely — with canary deployments, observability gates, and a tested rollback path.

## Status

🚧 **Placeholder.** Content lands here in **Phase 7** of the consolidation rollout. See [`docs/internal/`](../docs/internal/) for sequencing.

## What will live here

- `README.md` — rollout strategy overview: canary % thresholds, success metrics, abort criteria.
- `llm-upgrade-lifecycle-best-practices.md` — lifecycle best practices.
- `observability-and-rollback.md` — dashboards to wire up, alerts to define, conditions that trigger rollback, and the rollback procedure itself.

## Where the output goes next

After cutover, continuous evaluation continues via:

- [`../04-evaluate/`](../04-evaluate/) — same golden datasets re-run on a schedule to catch drift.
- [`../02-plan/availability-tracker/`](../02-plan/) — watch for upstream changes that might affect your now-deployed target model.
