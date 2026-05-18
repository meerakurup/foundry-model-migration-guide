# Contributing

Thanks for your interest in contributing to the Foundry Model Migration Guide. This repo consolidates seven source IPs into a single end-to-end migration toolkit organized by journey: **Discover → Plan → Migrate → Evaluate → Roll out**.

## Before you contribute

Most large-scale contributions come from one of the seven source IPs being folded in. If that's your situation, the consolidation flow and consent gate are tracked in [CONTRIB-CONSENT.md](CONTRIB-CONSENT.md) and the phased plan in [docs/internal/consolidation-plan.md](docs/internal/consolidation-plan.md).

For everyday contributions (bug fixes, doc improvements, new examples), follow the steps below.

## Contributor License Agreement (CLA)

This project will require contributors to sign the Microsoft CLA once it moves to `Azure-Samples` / `microsoft`. While the repo is still in staging, the CLA is not yet enforced, but please assume it will be — keep your contributions MIT-licensable and original.

When you submit a pull request, a CLA bot will determine whether you need to provide a CLA. Follow the bot's instructions. You only need to do this once across all Microsoft repos.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/). For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.

## How to contribute

1. **Open an issue first** for non-trivial changes. Describe the problem and your proposed approach so we can align before code is written.
2. **Fork** the repo and create a topic branch from `main`.
3. **Match the journey structure.** Code and docs live under one of `01-discover/`, `02-plan/`, `03-migrate-code/`, `04-evaluate/`, `05-rollout/`, `tools/`, or `presentation/`. Don't add new top-level folders without a discussion.
4. **Single source of truth.** Retirement dates, API change tables, golden datasets, and migration narrative each live in exactly one canonical file. Link to the canonical file rather than duplicating content.
5. **Test what you change.**
   - Python: `pytest 04-evaluate/`
   - Notebooks: confirm they execute end-to-end with `jupyter nbconvert --to notebook --execute`
   - Workflows: open the PR and confirm the eval CI workflow is green
6. **Run a link check** (`scripts/check-links.sh` once it exists) before submitting.
7. **Submit a PR** using the template. Describe the journey section affected, the change, and the verification you ran.

## Style

- Markdown: prefer reference-style links for repeated targets; use sentence-case headings; wrap commands in fenced blocks with the right language tag.
- Python: PEP 8, type hints on public functions, docstrings on modules and public APIs.
- Don't break the journey metaphor (Discover → Plan → Migrate → Evaluate → Roll out) in docs.

## What to avoid

- Duplicating content that already lives in another section (link instead).
- Owner-specific or repo-name-hardcoded paths in workflows or docs (this repo is designed to be portable to `Azure-Samples`).
- Adding content sourced from a personal repo without first checking [CONTRIB-CONSENT.md](CONTRIB-CONSENT.md).
- Importing anything from `microsoft/model-iq` — that repo is private and stays link-only here.
