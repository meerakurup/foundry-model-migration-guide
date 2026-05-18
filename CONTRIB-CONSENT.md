# Contributor consent tracker

This repo consolidates content from 7 source IPs into a single Azure AI Foundry model-migration guide. Five of those IPs live in personal GitHub accounts. **No content imports (Phase 2 onward of [docs/internal/consolidation-plan.md](docs/internal/consolidation-plan.md)) land in this repo until every row below is green.**

## What each owner is being asked to confirm

1. **MIT relicense** — they agree their content can be redistributed here under the MIT license that governs this repo.
2. **CLA** — where the destination is `Azure-Samples` or `microsoft`, they sign the [Microsoft CLA](https://cla.opensource.microsoft.com/) before content lands.
3. **Attribution mechanics** — they're comfortable with attribution via (a) `git subtree` history preservation, (b) a row in [`CREDITS.md`](CREDITS.md), and (c) a consolidation banner PR back to their source repo at archive time (Phase 10).
4. **Security scan acknowledgement** — they're aware the source repo will be scanned with `gitleaks` / `trufflehog` prior to import, and any sensitive findings will be raised with them privately.

## Tracker

| # | IP | Source repo | Owner(s) | License today | Outreach sent | MIT relicense ack | CLA signed (if needed) | Gitleaks/trufflehog scan | Cleared for import |
|---|---|---|---|---|---|---|---|---|---|
| IP2 | GenAI Model Migration Approach | [saurabhvartak1982/modelmigration](https://github.com/saurabhvartak1982/modelmigration) | Saurabh Vartak | _TBD_ | ☐ | ☐ | ☐ | ☐ | ☐ |
| IP3 | Azure AI Deployments Scanner | [ElisaPiccin/azure-ai-deployment-scanner](https://github.com/ElisaPiccin/azure-ai-deployment-scanner) | Elisa Piccin | _TBD_ | ☐ | ☐ | ☐ | ☐ | ☐ |
| IP4 | Azure OpenAI Models Migration Guide | [aiappsgbb/AOAI-models-migration](https://github.com/aiappsgbb/AOAI-models-migration) | Angel + GBBs (`aiappsgbb` org; fork of `felattaoui/...`) | _TBD_ | ☐ | ☐ | ☐ | ☐ | ☐ |
| IP5 | GPT-4o → GPT-5.1 Migration Guide | [fatimataayeb/azure-openai-migration-guide](https://github.com/fatimataayeb/azure-openai-migration-guide) | Fatima Taayeb | _TBD_ | ☐ | ☐ | ☐ | ☐ | ☐ |
| IP6 | Foundry Model Availability Tracker | [JinLee794/foundry-model-availability-notifications](https://github.com/JinLee794/foundry-model-availability-notifications) | Jin Lee | _TBD_ | ☐ | ☐ | ☐ | ☐ | ☐ |
| IP7 | azure-openai-to-responses | [Azure-Samples/azure-openai-to-responses](https://github.com/Azure-Samples/azure-openai-to-responses) | Arun + Pamela (already `Azure-Samples`) | MIT | ☐ | ☐ (lower friction — repo already MIT) | n/a (already Azure-Samples) | ☐ | ☐ |
| _ref_ | Model IQ (internal companion) | [microsoft/model-iq](https://github.com/microsoft/model-iq) | Narendra | private | n/a — **link-only**, no content imports | n/a | n/a | n/a | n/a |

Update each row in-place as outreach progresses. Replace `☐` with `✅` + a short note (e.g., the date + a link to the consent email/PR).

## Outreach template

> Hi <name>,
>
> We're consolidating the Azure AI Foundry model-migration IPs into a single staging repo ([foundry-model-migration-guide](https://github.com/meerakurup/foundry-model-migration-guide)) that's designed to move to `Azure-Samples` once content is complete. Your repo (`<repo-url>`) is one of the seven IPs we'd like to fold in (see [docs/internal/existing-ips.md](docs/internal/existing-ips.md) for the rationale).
>
> Before we touch any of your code, we want your explicit ack on four things:
>
> 1. You agree to relicense your contributions under MIT for use in this repo.
> 2. You're willing to sign the Microsoft CLA when the repo moves to `Azure-Samples`.
> 3. You're OK with attribution via `git subtree` history + a `CREDITS.md` row + a consolidation-banner PR back to your repo at archival.
> 4. You're OK with us running `gitleaks` / `trufflehog` against your repo before import (any sensitive findings come back to you privately).
>
> Reply to this thread with a yes/no on each, and we'll log it in [CONTRIB-CONSENT.md](CONTRIB-CONSENT.md). Happy to hop on a quick call if any of this needs more context.

## Security scan procedure (per IP, before subtree import)

```pwsh
# Run from a clean clone of the source repo
gitleaks detect --source . --report-path ../scans/<ip-name>-gitleaks.json --redact
trufflehog filesystem --no-update . > ../scans/<ip-name>-trufflehog.txt
```

Attach the scan output paths in the tracker row. Any non-empty findings → resolve with the owner before import.
