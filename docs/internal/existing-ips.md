## Model Upgrade Playbook IPs

## IP 1: Model IQ

Who built: Narendra
GitHub: https://github.com/microsoft/model-iq

Summary:
- This repo is a Copilot-native Azure OpenAI model lifecycle management toolkit built around MCP servers. Its goal is to let CSAs and CSAMs ask natural-language questions in VS Code about model retirements, migration feasibility, replacement options, customer impact, PTU sizing, pricing, and account-team coordination.
- The README shows that Model IQ is not just a guide; it is an operational system made up of multiple MCP servers: `model-data` for model catalog and migration intelligence, `ptu-sizing` for PTU and pricing analysis, `customer-models` for deployment inventory, `migration-advisor` for AI-generated migration recommendations, and `msx-crm` for CSA/CSAM and ACR context.
- Its model-upgrade features are very specific: live retirement tracking from Microsoft Docs, ranked replacement suggestions, a 0-100 migration feasibility score, benchmark comparison, regional capacity checks, severity-tagged migration best practices, ACR impact calculation, PTU sizing, customer-impact analysis, blast-radius and director scorecards, and full migration report generation in `.md` and `.pdf`.
- The README also shows end-to-end workflow support for the field: refresh live retirement/model/capacity data, pull or import customer deployment data from Power BI, generate customer-level migration reports, identify impacted CSAs/CSAMs, and even email retirement or migration recommendations directly through Microsoft 365 tools.

Value of this repo:
- This repo provides the strongest "action layer" of the set. Instead of only describing how to migrate, it helps field teams operationalize migration work across discovery, prioritization, recommendation, reporting, and customer communication.
- Its biggest value to users is that it brings scattered lifecycle tasks into one Copilot workflow: identify what is retiring, determine which customers are exposed, score the migration path, compare quality/cost/capacity tradeoffs, and produce a report or outreach motion without leaving chat.
- For the master playbook and migration agent vision, this repo is especially valuable because it shows what an agentized migration experience can look like in practice: grounded data access, reusable tools, orchestration across internal and external systems, customer-specific recommendations, and communication outputs that help convert analysis into action.


## IP 2: GenAI Model Migration Approach (Microsoft Foundry)

Who built: Saurabh 
GitHub: https://github.com/saurabhvartak1982/modelmigration

Summary:
- This repo is a migration methodology rather than a software tool. The README lays out a full end-to-end approach for moving an application from one model to another in Microsoft Foundry.
- The repo's core feature set is the migration framework itself: discovery of the current app and model usage, source-vs-target model delta analysis, deployment strategy for parallel testing, repeatable evaluation and regression gating, performance and cost validation, and production rollout with rollback conditions.
- The README is especially strong on what customers should inspect before migrating: workload type and modality, RAG vs non-RAG behavior, tool calling, token profile, output schema assumptions, API surface differences, quota posture, and rollout feasibility.
- It also calls out concrete evaluation practices customers can operationalize: golden datasets, Foundry Evaluations, Q&A/RAG metrics, tool-call accuracy checks, JSON/schema validation, and ongoing post-cutover monitoring.

Value of this repo:
- This repo provides a reusable decision framework that helps customers de-risk migrations before touching code. It is valuable because it gives teams a structured checklist for what must be understood, tested, and observed when a model changes.
- For a master migration playbook, this is strong "method backbone" IP: it contributes the operating model, evaluation gates, rollout sequencing, and rollback thinking that should sit above any model-specific migration guide.
- It is especially useful for enterprise customers with complex apps, agentic workflows, or multiple stakeholders because it frames migration as a product and operations exercise, not just an SDK update.


## IP 3: Azure AI Deployments Scanner

Who built: Elisa 
GitHub: https://github.com/ElisaPiccin/azure-ai-deployment-scanner

Summary:
- This repo is a PowerShell-based inventory and audit tool for Azure AI / Azure OpenAI / Foundry deployments. Its purpose is to help customers discover what is deployed across subscriptions and resource groups before planning model upgrades.
- The README highlights several specific features: scanning all accessible subscriptions or a selected subscription/resource group, filtering by model name, exporting results to Excel or CSV, and running read-only from Azure Cloud Shell with Reader permissions.
- The newest README features focus directly on migration readiness. The script pulls retirement data from Microsoft's documentation, identifies replacement models, and collects Azure Monitor usage metrics per deployment such as total requests, prompt tokens, and generated tokens over a configurable lookback window.
- The output is designed for operational use: timestamped Excel exports with filters, frozen headers, styling, retirement columns, replacement-model recommendations, and deployment-level metrics that make it easy to sort by urgency and impact.

Value of this repo:
- This repo delivers the inventory layer that many migration efforts are missing. Before customers can upgrade anything, they need to know which models are deployed, where they live, how much they are used, and which ones are approaching retirement.
- Its value to the master playbook is high because it solves the first practical question in any migration program: "What do I have, and what should I prioritize first?"
- It also adds a strong operational pattern to the combined IP: pair retirement risk with usage metrics so customers can rank migrations by both urgency and business impact.

## IP 4: Azure OpenAI Models Migration Guide

Who built: Angel & GBBs
GitHub: https://github.com/aiappsgbb/AOAI-models-migration/ 

Summary:
- This repo is the most complete end-to-end migration package of the set. The README positions it as a full guide for moving from GPT-4o / GPT-4o-mini to newer Azure OpenAI models such as GPT-4.1, GPT-5.1, and the o-series, with evaluation tooling and pre-built golden datasets.
- The README gives customers a concrete migration sequence: choose the target model, check retirement timelines, update code for API and parameter changes, build a golden dataset, evaluate before deploying, and roll out progressively.
- The repo includes a large set of practical migration assets beyond docs: deep-dive guides, notebooks, reusable Python modules, a model comparison/evaluation framework, pre-built golden datasets across seven scenarios, a web UI for side-by-side model comparison, and GitHub Copilot / agent skills for guided migration assistance.
- It is especially strong for complex applications. The README calls out sample coverage for RAG pipelines and multi-step workflows, including a self-contained RAG demo with swappable model stages, dual-layer evaluation, A/B migration comparison, drift analysis, and Azure AI Foundry result tracking.
- The README also shows strong lifecycle thinking: retirement timeline guidance, CI/CD evaluation workflows, cloud evaluation tracking, multi-region and fine-tuned-model considerations, and FAQs covering regression handling, automation, and continuous quality tracking.

Value of this repo:
- This repo contributes the richest "master IP" foundation because it combines guidance, code, evaluation assets, datasets, lifecycle operations, and agentic assistance in one place.
- For customers, its biggest value is reducing migration ambiguity. It does not just tell them to change model names; it gives them a path to choose a target, adapt code safely, validate quality with reusable test sets, and operationalize repeated migrations over time.
- For the combined playbook, this repo is the strongest source of reusable accelerators: golden datasets, evaluation framework, migration steps, RAG/agent patterns, CI/CD hooks, and agent skills that could be turned into a migration copilot or agent.

## IP 5: Azure OpenAI GPT-4o to GPT-5.1 Migration Guide


Who built: Fatima 
GitHub: https://github.com/fatimataayeb/azure-openai-migration-guide/tree/master 

Summary:
- This repo is a focused migration kit for one specific, high-value transition: GPT-4o to GPT-5.1 on Azure OpenAI. The README is explicit about the customer motivation: lower input token cost, fewer hallucinations, better reasoning, and better instruction following.
- The repo packages the migration into concrete customer-facing assets: a step-by-step migration guide, a migration plan template with architecture scenarios, API-change documentation, golden-dataset guidance, an Azure AI Foundry evaluation guide, FAQ content, before/after code examples, evaluation examples, dataset templates, and a presentation deck.
- The README also includes practical automation helpers. It calls out scripts to audit a codebase for parameters that need updating and to run model comparison evaluations.
- The README is specific about what customers need to change in code: update API versions, change the model name, replace the `system` role with `developer`, move from `max_tokens` to `max_completion_tokens`, remove `temperature`, and use `reasoning_effort` for reasoning depth.
- It also includes migration timing and rollout guidance: key retirement dates, a checklist for pre-upgrade inventory and dataset prep, test-phase evaluation steps, and a production rollout path that recommends canary deployment and continuous evaluation.

Value of this repo:
- This repo is valuable because it turns a broad model-upgrade problem into an opinionated, easy-to-execute package for a single migration scenario customers are likely to face.
- It contributes a strong template for scenario-specific playbooks: lead with business justification, show exact API deltas, provide scripts and examples, include evaluation guidance, and package stakeholder-ready collateral like a migration plan template and presentation deck.
- For the master playbook, this repo is a good pattern for how to create "migration packs" for important source-to-target model pairs, especially when customers need precise code changes and a simple narrative for why the migration is worth doing.


## IP 6: Azure AI Foundry Model Availability Tracker

Who Built: Jin 
GitHub: https://github.com/JinLee794/foundry-model-availability-notifications

Summary:
- This repo is an automated Azure AI Foundry model and region availability monitoring system. Its goal is to help customers and field teams know when target models become available, when availability changes by region or SKU, and when retirements create migration pressure.
- The README shows a simple but useful workflow: GitHub Actions runs every 6 hours, fetches current model availability data, compares it to the prior snapshot, stores the new JSON snapshot and historical diffs, opens GitHub issues when something changes, and rebuilds a static website that exposes the latest state.
- The repo's key customer-facing features are the generated outputs: an interactive website with overview stats, searchable "All Models" pages, region views, SKU-type views, change history, and individual model pages that show availability matrices, deployment options, and retirement notices.
- It also supports broad Azure AI coverage rather than only Azure OpenAI. The README calls out tracked OpenAI models, o-series, embeddings, Whisper, DALL-E, and Foundry catalog families such as Phi, Mistral, Qwen, and gpt-oss. That makes it useful for customers choosing both replacement models and viable deployment regions.
- From a model-upgrade perspective, this repo helps customers answer a practical migration question that most playbooks miss: "Is my preferred replacement model actually available in my target region and deployment type yet, and when did that change?"

Value of this repo:
- This repo provides the availability-intelligence layer for migration planning. Even if a team knows which model they want to move to, they still need to know whether it is live in the right regions, under the right SKU types, and whether that picture is changing over time.
- Its biggest value is reducing timing and rollout risk. By turning raw availability changes into issues, historical diffs, and a dashboard, it helps teams catch when a target model becomes deployable or when regional support changes in ways that affect migration plans.
- For the master playbook, this repo contributes an important missing signal: pair retirement guidance with real-time model availability and deployment-type visibility. That would make the combined playbook more actionable by helping customers choose not just the right replacement model, but the right moment and region to roll it out.

## IP 7: azure-openai-to-responses

Who made it: Arun and Pamela 
Github: https://github.com/Azure-Samples/azure-openai-to-responses

Summary:
- This repo is a focused migration accelerator for Python applications moving from the Azure OpenAI `AzureOpenAI` client and Chat Completions API to the OpenAI client and Responses API. The README positions it as a future-proofing migration because GPT-5 and newer models require the Responses API, and the move unlocks deeper tool integration, structured output support, and a stable `/openai/v1/` endpoint without `api_version` management.
- The repo supports both agent-assisted and manual migration workflows. Its primary experience is an open Agent Skill that can be installed into GitHub Copilot and other coding agents, then used to scan a codebase, plan edits, migrate files, and verify the migration automatically.
- The README also highlights practical migration assets beyond the skill itself: a `migrate.py` scanner, a fully migrated sample app in `demo/openai-chat-app-quickstart`, verification guidance, and explicit before/after mappings for the major API changes such as `chat.completions.create(...) -> responses.create(...)`, `messages -> input`, and `resp.choices[0].message.content -> resp.output_text`.
- It is especially useful because it covers compatibility details that customers will trip over in real migrations. The README includes a Responses API support matrix by model/version, commands to check live regional support, known limitations for older models, special handling for reasoning and o-series parameters, framework-specific guidance, and frontend guidance explaining when the UI does or does not need to change.

Value of this repo:
- This repo provides the strongest API-migration layer across the set. While several other IPs help with lifecycle planning, evaluation, and rollout, this one directly addresses the low-level application change required when customers move from Chat Completions to the Responses API.
- Its biggest value to users is reducing implementation risk. Instead of leaving teams to manually reinterpret SDK and wire-format differences, it gives them concrete mappings, scanning and verification tooling, a sample migrated app, and guardrails around model compatibility and older-model limitations.
- For the master playbook, this repo should become the canonical execution asset for the "API migration" step. It fills a critical gap in the combined IP by translating a strategic model-upgrade decision into precise code changes teams can actually apply and test.