# 01 · Discover

> **Goal:** Inventory every Azure OpenAI / Azure AI Foundry deployment across your tenant so you know **what you have**, **how it's used**, and **what's at risk** before you plan a single code change.

## Status

🚧 **Placeholder.** Content lands here in **Phase 3** of the consolidation rollout. See [`docs/internal/`](../docs/internal/) for sequencing.

## What will live here

- `Get-AzureAIDeployments.ps1` — PowerShell scanner that walks accessible subscriptions, joins deployments with retirement dates and Azure Monitor usage metrics, exports a styled Excel report.
- `README.md` — prerequisites (Cloud Shell, Reader role, lookback window), step-by-step usage, sample output.
- `TROUBLESHOOTING.md` — common errors (permissions, throttling, missing metrics).
- `demos/` — short GIFs of the scanner in action.

## Where the output goes next

The scanner's Excel output feeds directly into:

- [`../02-plan/decision-matrix.md`](../02-plan/) — prioritize by retirement urgency × usage volume.
- [`../02-plan/availability-tracker/`](../02-plan/) — cross-check target-model availability for the regions/SKUs you actually use.
