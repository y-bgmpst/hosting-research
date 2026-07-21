# Hosting Research

`hosting-research` is a production-grade documentation framework for AI-assisted research into hosting and infrastructure providers. It is built around explicit methodology, source quality rules, repeatable validation, and long-term maintainability.

This repository currently contains the framework and intake provider records. It does not publish verified provider research until a profile passes the required gates.

## Start Here

Read these in order:

1. [00_PROJECT.md](00_PROJECT.md) — scope, principles, and repository map
2. [01_RESEARCH_SPEC.md](01_RESEARCH_SPEC.md) — research process
3. [02_PROVIDER_SCHEMA.md](02_PROVIDER_SCHEMA.md) — provider data model
4. [11_SOURCE_POLICY.md](11_SOURCE_POLICY.md) — acceptable evidence
5. [07_OUTPUT_SPEC.md](07_OUTPUT_SPEC.md) — provider profile format
6. [08_QA_CHECKLIST.md](08_QA_CHECKLIST.md) — pre-merge checklist

## Repository Structure

| Path | Purpose |
|---|---|
| `providers/` | Provider profile Markdown files |
| `benchmarks/` | Raw benchmark outputs and normalized benchmark artifacts |
| `pricing/` | Pricing snapshots and pricing history records |
| `incidents/` | Incident timelines and postmortem evidence |
| `sources/` | Source metadata, archival references, and screenshot manifests |
| `comparisons/` | Derived cross-provider comparisons |
| `rankings/` | Reproducible scoring outputs |
| `appendices/` | Supporting methodology notes |
| `.github/` | PR templates, issue templates, and Copilot instructions |

## Framework Documents

| Document | Purpose |
|---|---|
| [AGENTS.md](AGENTS.md) | Mandatory rules for AI agents |
| [CLAUDE.md](CLAUDE.md) | Claude-specific operating prompt |
| [CODEX.md](CODEX.md) | Codex-specific operating prompt |
| [GEMINI.md](GEMINI.md) | Gemini-specific operating prompt |
| [CHATGPT.md](CHATGPT.md) | ChatGPT-specific operating prompt |
| [DEEP_RESEARCH.md](DEEP_RESEARCH.md) | Deep research prompt and evidence protocol |
| [00_PROJECT.md](00_PROJECT.md) | Project charter |
| [01_RESEARCH_SPEC.md](01_RESEARCH_SPEC.md) | Research methodology |
| [02_PROVIDER_SCHEMA.md](02_PROVIDER_SCHEMA.md) | Provider schema |
| [03_PROVIDER_LIST.md](03_PROVIDER_LIST.md) | Provider inventory |
| [04_BATCHES.md](04_BATCHES.md) | Batch planning |
| [05_VALIDATION_RULES.md](05_VALIDATION_RULES.md) | Validation gates |
| [06_STYLE_GUIDE.md](06_STYLE_GUIDE.md) | Editorial rules |
| [07_OUTPUT_SPEC.md](07_OUTPUT_SPEC.md) | Profile output template |
| [08_QA_CHECKLIST.md](08_QA_CHECKLIST.md) | QA checklist |
| [09_CONTRIBUTING.md](09_CONTRIBUTING.md) | Contribution workflow |
| [10_GLOSSARY.md](10_GLOSSARY.md) | Canonical terminology |
| [11_SOURCE_POLICY.md](11_SOURCE_POLICY.md) | Source policy |
| [12_CHANGELOG.md](12_CHANGELOG.md) | Versioning and changelog rules |

## Current Research State

All current provider files are `intake` records. They are intentionally non-factual until provider-specific research is performed under [01_RESEARCH_SPEC.md](01_RESEARCH_SPEC.md).

The current inventory is maintained in [03_PROVIDER_LIST.md](03_PROVIDER_LIST.md), and the initial batch is defined in [04_BATCHES.md](04_BATCHES.md).

## Contribution Workflow

1. Read [09_CONTRIBUTING.md](09_CONTRIBUTING.md).
2. Claim a provider with `.github/ISSUE_TEMPLATE/provider-research.yml`.
3. Research only the claimed scope.
4. Use [02_PROVIDER_SCHEMA.md](02_PROVIDER_SCHEMA.md) and [07_OUTPUT_SPEC.md](07_OUTPUT_SPEC.md).
5. Cite sources according to [11_SOURCE_POLICY.md](11_SOURCE_POLICY.md).
6. Validate against [05_VALIDATION_RULES.md](05_VALIDATION_RULES.md).
7. Complete [08_QA_CHECKLIST.md](08_QA_CHECKLIST.md).
8. Open a pull request using [.github/PULL_REQUEST_TEMPLATE.md](.github/PULL_REQUEST_TEMPLATE.md).

## AI Agent Use

AI agents must read [AGENTS.md](AGENTS.md) before making changes. Tool-specific prompts are provided for Codex, Claude, Gemini, ChatGPT, and Deep Research workflows.

Agents may improve structure, normalize formatting, and draft research outputs from cited evidence. Agents must not invent data or cite generated summaries as evidence.
