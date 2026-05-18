# Credits

This repo is a consolidation of seven existing Azure OpenAI / Azure AI Foundry model-migration IPs. Each contribution remains attributed to its original author through (a) `git subtree` history, (b) the row(s) below, and (c) a consolidation banner on the source repo once archived (see Phase 10 of [`docs/internal/consolidation-plan.md`](docs/internal/consolidation-plan.md)).

A separate operational tracker, [`CONTRIB-CONSENT.md`](CONTRIB-CONSENT.md), tracks relicense / CLA / scan status per source IP.

## Source IPs

### GenAI Model Migration Approach

- **Author:** Saurabh Vartak
- **Source:** [github.com/saurabhvartak1982/modelmigration](https://github.com/saurabhvartak1982/modelmigration)
- **Lives in this repo at:** [`02-plan/README.md`](02-plan/) (planning narrative), rollout phases of [`05-rollout/`](05-rollout/)
- **What it brings:** 6-phase migration playbook (Discovery → Delta → Deployment → Eval → Perf → Rollout), evaluation gates, rollout sequencing, and rollback thinking.

### Azure AI Deployments Scanner

- **Author:** Elisa Piccin
- **Source:** [github.com/ElisaPiccin/azure-ai-deployment-scanner](https://github.com/ElisaPiccin/azure-ai-deployment-scanner)
- **Lives in this repo at:** [`01-discover/`](01-discover/)
- **What it brings:** `Get-AzureAIDeployments.ps1` — PowerShell scanner that walks subscriptions, joins deployments with retirement dates and Azure Monitor usage metrics, and exports a styled Excel report.

### Azure OpenAI Models Migration Guide

- **Authors:** Angel + GBBs (`aiappsgbb` org; fork of `felattaoui/AOAI-models-migration`)
- **Source:** [github.com/aiappsgbb/AOAI-models-migration](https://github.com/aiappsgbb/AOAI-models-migration)
- **Lives in this repo at:** [`02-plan/migration-paths.md`](02-plan/), [`02-plan/retirement-timeline.md`](02-plan/), [`03-migrate-code/api-changes-by-model.md`](03-migrate-code/), [`03-migrate-code/skills/`](03-migrate-code/), [`04-evaluate/`](04-evaluate/) (canonical), [`05-rollout/llm-upgrade-lifecycle-best-practices.md`](05-rollout/), [`tools/model-migration-eval/`](tools/), [`.github/workflows/eval-on-schedule.yml`](.github/workflows/)
- **What it brings:** the richest of the seven IPs — deep-dive docs, 54-case golden datasets across 7 scenarios, `MigrationEvaluator` SDK, RAG pipeline sample, Copilot Skills, Flask web UI with Bicep/azd, and the nightly evaluation CI workflow.

### GPT-4o → GPT-5.1 Migration Guide

- **Author:** Fatima Taayeb
- **Source:** [github.com/fatimataayeb/azure-openai-migration-guide](https://github.com/fatimataayeb/azure-openai-migration-guide)
- **Lives in this repo at:** [`03-migrate-code/audit_codebase.py`](03-migrate-code/), [`03-migrate-code/examples/before/`](03-migrate-code/) and [`examples/after/`](03-migrate-code/), [`04-evaluate/data/templates/`](04-evaluate/), [`presentation/migration_deck.pptx`](presentation/)
- **What it brings:** opinionated migration-pack pattern (business justification + exact API deltas + scripts + evaluation guidance + stakeholder collateral) for a single high-volume source → target pair. Generalized in this repo from 4o-only to any source → any target.

### Foundry Model Availability Tracker

- **Author:** Jin Lee
- **Source:** [github.com/JinLee794/foundry-model-availability-notifications](https://github.com/JinLee794/foundry-model-availability-notifications)
- **Lives in this repo at:** [`02-plan/availability-tracker/`](02-plan/)
- **What it brings:** automated model/region/SKU availability monitor with 6-hour GitHub Actions snapshots, historical diffs, an issue-bot for changes, and a generated static dashboard. Pairs with the retirement timeline to answer *"is my preferred target model actually available in my target region and deployment type yet?"*

### azure-openai-to-responses

- **Authors:** Arun + Pamela
- **Source:** [github.com/Azure-Samples/azure-openai-to-responses](https://github.com/Azure-Samples/azure-openai-to-responses)
- **Lives in this repo at:** [`03-migrate-code/api-migration-responses/`](03-migrate-code/), referenced from [`03-migrate-code/skills/`](03-migrate-code/)
- **What it brings:** the canonical API-surface migration accelerator — Chat Completions → Responses API — including a Copilot Skill, `migrate.py` scanner, fully migrated sample app, before/after mappings, and a Responses API support matrix by model/version.

## Internal companion (link only — no content imports)

### Model IQ

- **Author:** Narendra
- **Source:** [github.com/microsoft/model-iq](https://github.com/microsoft/model-iq) _(private)_
- **Relationship to this repo:** Microsoft-internal Copilot-native control tower for the same domain. Depends on internal data sources (MSX CRM, Power BI, customer deployment records, org hierarchy) that cannot ship publicly. This repo is its open companion; field teams use Model IQ alongside it.

## How to add yourself

If you contribute new content (not a wholesale IP import), add a row under a new **## Individual contributions** heading with your name, the file(s) you authored or substantially edited, and the date.
