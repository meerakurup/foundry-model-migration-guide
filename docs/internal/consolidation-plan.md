Consolidation Analysis: Azure OpenAI / Foundry Model Migration Repos 

 

1. What each repo is (at a glance) 

Repo 

Owner 

Type 

Primary artifact 

Audience 

Maturity 

saurabhvartak1982/modelmigration 

Individual 

Methodology / framework doc 

Single README — 6-phase migration playbook (Discovery → Delta → Deployment → Eval → Perf → Rollout) 

Architects, TPMs 

Concept doc (1 file) 

fatimataayeb/azure-openai-migration-guide 

Individual 

Guide + light tooling 

Docs (migration-guide, api-changes, golden-datasets, evaluation-guide, faq), audit_codebase.py, run_evaluation.py, dataset templates, customer pitch deck 

Devs migrating GPT-4o → GPT-5.1 

Early (Python, 72 KB) 

aiappsgbb/AOAI-models-migration 

aiappsgbb (GBB org, fork of felattaoui/...) 

Hands-on toolkit 

10 deep-dive docs, 54-case golden datasets across 7 scenarios, MigrationEvaluator SDK (src/evaluate/...), RAG pipeline sample, Copilot Skills (npx skills add ...), web UI (model_migration_eval/) with multi-user auth, Bicep IaC, CI workflows 

Devs + GBB-led customer engagements 

Most mature (~74 MB) 

ElisaPiccin/azure-ai-deployment-scanner 

Individual 

Inventory / discovery tool 

Single PowerShell script Get-AzureAIDeployments.ps1 — scans subscriptions for AOAI/Foundry deployments, joins with retirement dates + Azure Monitor metrics, emits Excel 

Cloud admins, FinOps, anyone planning a migration 

Active v3.0, 10 ⭐ 

microsoft/model-iq 

Microsoft (currently private) 

Copilot-native lifecycle platform 

5 local + 3 remote MCP servers, 22 Copilot skills, knowledge graph, PTU sizing, ACR impact, MSX CRM, customer impact (39K records), live data refresh, AI-powered recommendations 

Microsoft field (CSAs/CSAMs), internal 

Most ambitious; internal data 

 

2. Functional overlap map 

 

Key duplications: 

Migration narrative / playbook appears in 3 places (modelmigration, azure-openai-migration-guide/docs, AOAI-models-migration/docs). 

Golden datasets + evaluation appears in 2 places (azure-openai-migration-guide lightly; AOAI-models-migration deeply with 54 cases + SDK + UI). 

API change tables (4o → 4.1/5.x, max_tokens → max_completion_tokens, system → developer, reasoning_effort) appears in 3 places. 

Retirement timeline appears in 4 places (scanner pulls it live; AOAI-models-migration documents it; model-iq scrapes it; fatimataayeb hardcodes it). 

Discovery / inventory is unique to azure-ai-deployment-scanner and (internally) model-iq. 

CSA/CSAM/ACR/MSX integrations are unique to model-iq and must stay private — they contain Microsoft-internal customer data hooks. 

 

3. Recommended target: a single public customer-facing repo 

Suggested name: Azure-Samples/foundry-model-migration (or microsoft/ foundry-model-migration or azure/ foundry-model-migration) License: MIT Owner org: Azure-Samples (best customer discoverability) or microsoft Audience framing: "Everything a customer needs to inventory, plan, code, evaluate, and roll out an Azure OpenAI / Foundry model migration — end-to-end." 

 

Proposed structure 

PROPOSED-STRUCTURE.md 

azure-openai-model-migration/ 

├── README.md                          # Top-level: "Discover → Plan → Migrate → Evaluate → Roll out" 

├── LICENSE                            # MIT 

├── CODE_OF_CONDUCT.md / SECURITY.md   # Microsoft OSS standard files 

│ 

├── 01-discover/                       # ⬅ from ElisaPiccin/azure-ai-deployment-scanner 

│   ├── README.md 

│   ├── Get-AzureAIDeployments.ps1     # the v3 PowerShell scanner (verbatim) 

│   ├── TROUBLESHOOTING.md 

│   └── demos/*.gif 

│ 

├── 02-plan/                           # ⬅ from saurabhvartak1982/modelmigration 

│   ├── README.md                      # Discovery questions, delta sheet, rollout strategy 

│   ├── migration-paths.md             # ⬅ from AOAI-models-migration/docs 

│   ├── retirement-timeline.md         # ⬅ from AOAI-models-migration/docs (single source of truth) 

│   └── decision-matrix.md             # consolidated 4o/4.1/5.x/o-series decision table 

│ 

├── 03-migrate-code/                   # ⬅ merged: AOAI + fatimataayeb + saurabh 

│   ├── README.md 

│   ├── api-changes-by-model.md        # ⬅ AOAI (canonical, most complete) 

│   ├── audit_codebase.py              # ⬅ fatimataayeb (move + harden) 

│   ├── examples/ 

│   │   ├── before/                    # ⬅ fatimataayeb GPT-4o snippets 

│   │   ├── after/                     # ⬅ fatimataayeb GPT-5.x snippets 

│   │   └── sdks/                      # ⬅ AOAI's C#/JS/Java SDK examples 

│   └── skills/                        # ⬅ AOAI Copilot Skills (npx skills add) 

│       ├── aoai-model-migration/ 

│       ├── aoai-migration-evaluation/ 

│       └── aoai-model-lifecycle/ 

│ 

├── 04-evaluate/                       # ⬅ AOAI is canonical; absorb fatimataayeb's 

│   ├── README.md                      # Evaluation guide, LLM-as-Judge, Foundry tracking 

│   ├── data/                          # 54 golden test cases (RAG, classification, tools, …) 

│   │   ├── golden_rag.jsonl           # + merge fatimataayeb dataset templates 

│   │   └── ... 

│   ├── src/evaluate/                  # MigrationEvaluator SDK (AOAI) 

│   ├── samples/rag_pipeline/          # RAG multi-step migration sample (AOAI) 

│   ├── notebooks/ 

│   │   ├── azure_openai_migration_technical.ipynb 

│   │   └── azure_openai_evaluation_guide.ipynb 

│   └── docs/ 

│       ├── building-golden-datasets.md 

│       ├── evaluation-guide.md 

│       ├── migrating-multi-step-apps.md 

│       └── cloud-eval-tracking-across-models.md 

│ 

├── 05-rollout/                        # ⬅ from AOAI + saurabh 

│   ├── README.md 

│   ├── llm-upgrade-lifecycle-best-practices.md 

│   └── observability-and-rollback.md 

│ 

├── tools/ 

│   └── model_migration_eval/          # ⬅ AOAI web UI (Flask + Bicep/azd) 

│ 

├── presentation/ 

│   └── migration_deck.pptx            # ⬅ fatimataayeb (sanitized) 

│ 

└── .github/ 

    ├── workflows/eval-on-schedule.yml # ⬅ AOAI nightly eval CI 

    ├── copilot-instructions.md        # ⬅ AOAI repo conventions 

    └── ISSUE_TEMPLATE/ 

 

What stays out of the public repo 

microsoft/model-iq is the private internal "control tower" built on top of all the above. Don't merge it directly. Instead: 

Keep model-iq private (it depends on Power BI, MSX CRM, 39K customer deployment records, internal org hierarchy — none of which can ship publicly). 

Refactor model-iq so its public-safe modules consume the new public repo as a dependency: 

The "model lifecycle data" MCP server (retirements, benchmarks, model catalog) → could become a public sub-package under tools/mcp-model-data/ in the new repo. 

The model-data scraper (npm run refresh of MS Docs retirements) → publishable. 

customer-models, msx-crm, mail, powerbi-remote, migration-advisor (Foundry agent with internal grounding) → stay in microsoft/model-iq (private). 

From model-iq, link to the new public repo as the canonical "do it yourself" toolkit; from the public repo, link to model-iq as "Microsoft field teams use this internally." 

 

4. Consolidation plan (suggested sequence) 

Create the empty target repo under Azure-Samples (or microsoft), MIT, with CoC/SECURITY/SUPPORT files. 

Seed with aiappsgbb/AOAI-models-migration as the base (it has the richest structure, CI, skills, IaC, golden datasets, web UI). Preserve git history with git subtree add. 

Fold in ElisaPiccin/azure-ai-deployment-scanner under 01-discover/ (subtree merge to keep history + the 10 ⭐ social proof in commit log). 

Fold in saurabhvartak1982/modelmigration as 02-plan/README.md — it's the cleanest narrative playbook and complements AOAI's more code-heavy docs. 

Fold in fatimataayeb/azure-openai-migration-guide: move audit_codebase.py to 03-migrate-code/, merge docs/api-changes.md content into AOAI's api-changes-by-model.md, move dataset templates into 04-evaluate/data/templates/, move pitch deck to presentation/. Drop the 4o→5.1-only framing — generalize to "any source → any target." 

De-duplicate: pick one canonical doc per topic (single source of truth for retirement timeline, API change table, evaluation methodology). 

Archive the 4 source repos with a README pointer to the new repo (don't delete — preserves stars, forks, and inbound links). Suggested archive note: 

📦 This repo has been consolidated into Azure-Samples/azure-openai-model-migration. Please open new issues there. 

Keep microsoft/model-iq private but update its README to cite the new public repo as the "open companion." 

Announce via Azure AI Foundry blog + a "What's New in Azure OpenAI" link. 

 

5. Branding / naming considerations 

"AOAI" branding is being phased out in favor of "Azure OpenAI in Azure AI Foundry." Use foundry- model-migration or azure-ai-model-migration (broader — covers Foundry/Marketplace models like Mistral, Phi, Gemini that AOAI's framework already supports). 

Add topics: azure-openai, azure-ai-foundry, model-migration, llm-evaluation, gpt-5, mcp, copilot-skills. 

Pin the repo under Azure-Samples for SEO; cross-list in the Azure AI Foundry samples gallery. 

 

6. Risks & call-outs 

Ownership / CLA: 3 of the 5 repos are personal accounts. Each contributor (Saurabh, Fatima, Elisa, Felix Attaoui, Naren) needs to agree to relicense under MIT and sign Microsoft's CLA before code lands in Azure-Samples/microsoft. 

Disclaimers: 3 repos carry "not an official Microsoft solution" disclaimers. Once consolidated under Azure-Samples/microsoft, decide whether to (a) make it official with a support statement or (b) keep a uniform "sample / reference implementation, not covered by Microsoft Support" notice. 

Internal data leakage from model-iq: be extremely careful when extracting any code from model-iq into the public repo — its .gitignore protects customer/org data, but always do a gitleaks/trufflehog scan before publishing. 

Versioning of model lists: GPT-4.1 / 5.x / o-series move fast. Centralize the model catalog + retirements in one generated file (driven by the scanner + npm run refresh script) so docs don't drift. 

PowerShell vs Python: the scanner is PowerShell, the rest is Python/TS — that's fine; document it as a one-shot CLI tool rather than rewriting it. 

7. TL;DR 

Build one public Azure-Samples/azure-openai-model-migration repo organized around the migration journey Discover → Plan → Migrate → Evaluate → Roll out, using aiappsgbb/AOAI-models-migration as the base, plugging in azure-ai-deployment-scanner for discovery, modelmigration for the planning narrative, and azure-openai-migration-guide for extra examples + the customer deck. Keep microsoft/model-iq private as the internal control tower that consumes (and contributes back to) the public repo. 