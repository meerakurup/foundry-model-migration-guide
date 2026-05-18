# Foundry Model Migration Guide

> **End-to-end toolkit for migrating Azure OpenAI / Azure AI Foundry models — from inventory through rollout.** Discover what you have, plan the move, change the code, prove it works, and roll out safely.

![status](https://img.shields.io/badge/status-staging-orange) ![license](https://img.shields.io/badge/license-MIT-blue) ![scope](https://img.shields.io/badge/scope-Azure%20OpenAI%20%2B%20Azure%20AI%20Foundry-0078d4)

**Topics:** `azure-openai` · `azure-ai-foundry` · `model-migration` · `llm-evaluation` · `gpt-5` · `mcp` · `copilot-skills`

> ⚠️ **Staging repo.** This is a consolidation of multiple existing migration assets being prepared for promotion to `Azure-Samples`. Attribution and source-asset details live in [`CREDITS.md`](CREDITS.md); the rollout plan lives in [`docs/internal/`](docs/internal/).

---

## Pick your entry point

### 🧑‍💻 I'm migrating my own app

You own (or build for) an application running on Azure OpenAI or an Azure AI Foundry model and you need to move to a newer model — for cost, capability, retirement pressure, or all three. Start at **[01 · Discover](01-discover/)** and walk the journey end to end.

### 🛟 I'm helping a customer migrate (Microsoft field team)

You're a CSA / CSAM / GBB running a migration motion with a customer. Use the same journey, but you have a few extras:

- The **inventory + retirement urgency** pattern in [01 · Discover](01-discover/) plus the **availability tracker** in [02 · Plan](02-plan/) cover most pre-engagement diligence.
- The opinionated **migration packs** (e.g., 4o → 5.1, Chat Completions → Responses API) in [03 · Migrate code](03-migrate-code/) work as drop-in customer assets.
- The **customer pitch deck** in [presentation/](presentation/) is ready to brand and send.
- For internal-only tooling (PTU sizing, MSX/CRM context, blast-radius scoring), use the private internal companion repo. This public repo is its open counterpart — and what you should hand to the customer.

---

## The journey

| Step | Section | What it answers |
|------|---------|-----------------|
| 1 | **[01 · Discover](01-discover/)** | What models do I have deployed, where, how heavily are they used, and which are retiring? |
| 2 | **[02 · Plan](02-plan/)** | Given my inventory, which migrations matter most, what do I migrate to, and is the target model actually available where I need it? |
| 3 | **[03 · Migrate code](03-migrate-code/)** | What exactly changes in my code — parameters, API surface, SDK — and what can be automated? |
| 4 | **[04 · Evaluate](04-evaluate/)** | Does the migrated app behave at least as well as the original on my real workloads? |
| 5 | **[05 · Roll out](05-rollout/)** | How do I cut over safely with canary, observability, and a tested rollback? |

Supporting:

- **[tools/](tools/)** — repo-wide tooling (web UI for side-by-side comparison).
- **[presentation/](presentation/)** — stakeholder-ready collateral.
- **[docs/internal/](docs/internal/)** — planning record (consolidation plan, source asset catalog).

---

## Contributing

See [`CONTRIBUTING.md`](CONTRIBUTING.md). Attribution for upstream content is tracked in [`CREDITS.md`](CREDITS.md).

## Code of Conduct

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/). See [`CODE_OF_CONDUCT.md`](CODE_OF_CONDUCT.md).

## Security

Report security issues via the process in [`SECURITY.md`](SECURITY.md) — **not** via public GitHub Issues.

## Support

This is a sample / reference implementation, not covered by Microsoft Support. See [`SUPPORT.md`](SUPPORT.md).

## License

[MIT](LICENSE).

## Trademarks

This project may contain trademarks or logos for projects, products, or services. Authorized use of Microsoft trademarks or logos is subject to and must follow [Microsoft's Trademark & Brand Guidelines](https://www.microsoft.com/en-us/legal/intellectualproperty/trademarks/usage/general). Use of Microsoft trademarks or logos in modified versions of this project must not cause confusion or imply Microsoft sponsorship. Any use of third-party trademarks or logos are subject to those third-party's policies.

