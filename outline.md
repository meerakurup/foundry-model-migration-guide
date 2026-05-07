## Microsoft Foundry Model Migration Guide

This is the guide for transition your existing LLM application built with Foundry models to a newer model. 
The underlying build shape across all three phases should stay consistent even as the delivery surface changes. The eventual master repo should have four parts:

- **Playbook**: the canonical upgrade method, decision framework, and rollout checklist
- **Toolkit**: scanners, compatibility checks, availability and inventory utilities, and eval helpers
- **Migration packs**: scenario-specific upgrade packs with exact code and parameter deltas
- **Advisor**: optional skills or agent layer that helps users navigate and run the workflow

The same four parts should exist in crawl, walk, and run, but with very different maturity. Crawl is a thin slice of the future repo, walk is the first real public repo, and run productizes the highest-value pieces inside Foundry.

### Crawl: GPT-4o Migration Playbook

#### Deliverable type
- Documentation package
- Sample repo
- Eval starter pack

#### What it is
One opinionated migration guide for a single upgrade path centered on GPT-4o, focused on helping developers understand what needs to change in their app and how to validate the upgrade safely. This should be a narrow slice of the future master repo, not the full repo itself.

#### What it includes
- **Playbook**: one canonical GPT-4o upgrade journey using the method backbone from GenAI Model Migration Approach. This is where discovery, target selection, evaluation, rollout, and rollback are defined.
- **Toolkit**: a narrow set of customer-safe helpers, not a full platform. This should include API migration guidance and scanning from `azure-openai-to-responses`, plus selective evaluation starter assets from `AOAI-models-migration`.
- **Migration packs**: one polished migration pack, or at most two, for the most important path. The best starting pattern is `GPT-4o -> GPT-5.1` from Fatima's repo, optionally paired with Chat Completions -> Responses API migration from Arun and Pamela's repo.
- **Advisor**: lightweight prompts or skills only. This phase should not try to ship a full Model IQ-style agent experience yet.
- concrete guidance on code changes, prompt and parameter mapping, light prompt optimization guidance for the target path, tool call compatibility, JSON and structured output validation, and rollout and regression checks before production cutover

#### Why this is the right crawl
This is narrow enough to ship quickly and specific enough to test whether better migration guidance actually improves upgrade success. It avoids turning the crawl stage into a broad documentation program with weak proof value, and it also avoids overbuilding a large toolkit or agent experience before the core upgrade workflow is proven.

### Walk: Model Upgrade Guide

#### Deliverable type
- Public-facing GitHub repo

#### What it is
A public-facing repo-based guide that helps developers run upgrades end to end across more model paths, not only GPT-4o. This is the first full version of the master repo shape: playbook, toolkit, migration packs, and advisor.

#### What it includes
- **Playbook**: a generalized upgrade method across multiple model paths, based on the framework from GenAI Model Migration Approach.
- **Toolkit**: reusable upgrade helpers that make the workflow repeatable. This should combine deployment inventory and prioritization from Azure AI Deployments Scanner, region and SKU availability checks from the Foundry Model Availability Tracker, API compatibility and migration checks from `azure-openai-to-responses`, reusable prompt optimization patterns, and reusable evaluation scaffolds and datasets from `AOAI-models-migration`.
- **Migration packs**: a growing library of model-pair-specific packs following the pattern established by Fatima's repo, with exact code deltas, parameter mappings, rollout guidance, and validation steps.
- **Advisor**: repo-native skills, templates, or Copilot workflows inspired by Model IQ, but grounded only in customer-safe data and repo artifacts rather than Microsoft-internal systems. This is also where prompt optimization guidance starts to become reusable rather than path-specific.
- support for multiple upgrade paths across models, generated migration steps and checklists, reusable eval flows for quality/tool use/structured output, compatibility checks for prompts and parameters, and sample artifacts that teams can adapt in their own repos

#### Why this is the right walk
This stage expands coverage beyond one migration guide without committing yet to a full Foundry-native feature. It also creates reusable artifacts, a clearer signal on which upgrade paths and checks matter most, and a real public repo that can later feed the productized experience.

### Run: Guided Model Upgrade

#### Deliverable type
- Built-into-Foundry feature

#### What it is
A Foundry-native, project-aware upgrade workflow that helps a developer choose a target model, understand migration risk, run side-by-side validation, and move to production with more confidence. At this stage, the four parts of the repo become product surfaces inside Foundry.

#### How it should be built into Foundry
- the **playbook** becomes the in-product upgrade workflow launched from a project, deployment, or upgrade recommendation surface
- the **toolkit** becomes Foundry-native services that use current models, deployments, prompts, evals, usage signals, and availability context where available
- the **migration packs** become built-in scenario templates and checks for common upgrade paths
- the **advisor** becomes a project-aware guide that explains risk, recommends targets, creates upgrade reports, and walks users through validation and rollout inside the project workflow rather than acting as a separate opaque tool

#### What it includes
- recommended target models based on quality, cost, latency, capability, and regional availability tradeoffs
- prompt and parameter translation help between models, including API migration where needed
- prompt optimization assist that flags likely prompt incompatibilities, suggests rewrites where needed, and validates original versus adjusted prompts side by side
- migration risk checks for tool use, structured outputs, and other common incompatibilities
- guided evaluation flows and rollout support
- project-aware inventory, prioritization, compatibility, and rollout guidance
- more domain-specific guidance once the highest-value patterns are understood from crawl and walk

#### What to avoid calling it
- Not a fully autonomous API that silently upgrades customer projects
- Not a migration playbook with a nicer UI

### Why this staged approach is the right deliverable
This bet is fundamentally about making model change feel like normal lifecycle management instead of a bespoke migration project. A crawl/walk/run sequence makes the ambition more credible: crawl proves the migration problem is real and solvable, walk scales that guidance across more upgrade paths through a real public repo, and run productizes the highest-value workflow inside Foundry. The repo remains the proving ground and reusable asset source even after the run-stage experience moves into product.

### Additional Thoughts

#### Suggested Guide Steps 
1. Discovery
    - Models deployed and which to retire (Elisa)
    - Models API retiring models (Jin)
    - Delta between Model A and B - consider what changes
5. Deployment Strategy
    - Quota checks for user 
    - Do new deployment
7. Code Changes (API / SDK migration)
    - CAPI --> RAPI (Arun & Pamela)
    - Prompt Optimization 
10. Evaluation
    - Use own or Foundry Eval testing
    - Select eval scenario depending on app you are building (RAG, Tool calling, Translation, Classification)
    - Golden (test) Dataset for your domain
    - Performance and Cost Validation
15. Production Roll-out
    - Moving only some traffic to this model not all
    - Monitoring success/failures with real data 
17. Post-migration / New Models


### Notes
* Customer maturity level - need to encourage them to keep going through process, waiting for perfect golden dataset is not effective.
* Goal = practice
* Start ASAP -
* Model migration + API migration - separate the two 
* Typical embellishments
* Decision tree to ask questions and guide them - adoption framework - ex diff assets and repos

#### Unified Resources used by repo

Deployment inventory --> Scanner 
Model lifecycle and retirement data. --> Models API
Region and SKU availability data. --> Models API
Evaluation dataset and evaluation results --> TODO
Migration recommendation and rollout plan --> TODO (Reivew Above) 

### Resources

- https://github.com/saurabhvartak1982/modelmigration
- https://github.com/aiappsgbb/AOAI-models-migration/blob/main/docs/getting-started.md
- https://github.com/Azure-Samples/azure-openai-to-responses
- https://github.com/fatimataayeb/azure-openai-migration-guide
- https://github.com/ElisaPiccin/azure-ai-deployment-scanner
