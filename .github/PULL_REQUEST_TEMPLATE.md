# Pull request

## Summary

<!-- One-sentence description of the change. -->

## Journey section(s) affected

- [ ] `01-discover/`
- [ ] `02-plan/`
- [ ] `03-migrate-code/`
- [ ] `04-evaluate/`
- [ ] `05-rollout/`
- [ ] `tools/`
- [ ] Repo-wide (hygiene, CI, structure, docs)

## Type of change

- [ ] Bug fix
- [ ] New content / sample / doc
- [ ] Content import from a source IP (link the row in [CONTRIB-CONSENT.md](../CONTRIB-CONSENT.md))
- [ ] De-duplication / canonicalization
- [ ] Portability hardening (Azure-Samples readiness)
- [ ] Other (describe)

## Verification

<!-- Show the commands you ran and their result. Example: -->
<!-- - [x] `pytest 04-evaluate/` — 23 passed -->
<!-- - [x] Manual: opened `04-evaluate/notebooks/azure_openai_migration_technical.ipynb`, ran top-to-bottom, all cells green -->
<!-- - [x] Link check: `scripts/check-links.sh` — 0 broken -->

- [ ]
- [ ]

## Source IP attribution (if importing)

<!-- Required for any content sourced from one of the 7 IPs in docs/internal/existing-ips.md. -->

- Source IP:
- Source repo + commit SHA:
- `CONTRIB-CONSENT.md` row marked cleared: [ ] yes
- `CREDITS.md` updated: [ ] yes

## Checklist

- [ ] Single source of truth preserved (no duplicated retirement dates, API tables, or narrative)
- [ ] No owner/repo-name hardcoding (workflows use `${{ github.repository }}`, docs use relative links)
- [ ] No content sourced from `microsoft/model-iq` (link-only here)
- [ ] CLA signed (if applicable)
