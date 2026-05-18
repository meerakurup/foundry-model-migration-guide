# 03 · Migrate code

> **Goal:** Translate the plan from [02-plan](../02-plan/) into precise code changes — parameter-level, API-surface, and SDK-level — with automation to scan, edit, and verify your codebase.

## Status

🚧 **Placeholder.** Content lands here in **Phase 5** of the consolidation rollout. See [`docs/internal/`](../docs/internal/) for sequencing.

## What will live here

- `README.md` — decision tree: *Param-level change only? → API-change table. API-surface change (Chat Completions → Responses)? → Responses API skill. Need automated edits? → Copilot Skill.*
- `api-changes-by-model.md` — **single canonical source** for parameter changes across model families (`max_tokens` → `max_completion_tokens`, `system` → `developer`, `temperature` handling, `reasoning_effort`, etc.).
- `audit_codebase.py` — generalized scanner (any source → any target) that flags code paths needing updates.
- `examples/before/` and `examples/after/` — paired code snippets for common migration patterns.
- `examples/sdks/` — C#, JavaScript, and Java SDK migration examples.
- `api-migration-responses/` — Chat Completions → Responses API accelerator (scanner, sample migrated app, Copilot Skill).
- `skills/` — indexed Copilot Skills covering model migration, migration evaluation, model lifecycle, and Responses API migration.

## Where the output goes next

Once code changes are applied, validate them in:

- [`../04-evaluate/`](../04-evaluate/) — run golden datasets and side-by-side comparisons.
