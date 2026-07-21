# 00 — Project Charter

> Methodology version: **1.0.0** · Repository standard · 2026-07-21

## Purpose

`hosting-research` is a long-lived research repository for evaluating hosting, cloud, infrastructure, and adjacent compute providers with reproducible methods, explicit sources, and machine-readable outputs.

The repository is designed for human researchers and AI agents working together. It prioritizes traceability over speed: every published claim must be attributable, current enough for its use, and represented in a consistent schema.

## Non-Goals

This repository is not:

- A live pricing scraper
- An affiliate marketing site
- A provider recommendation engine without cited evidence
- A place to store uncited opinions
- A benchmark leaderboard without raw data

## Operating Principles

1. **Evidence first:** Claims are accepted only when supported by the source tiers in [11_SOURCE_POLICY.md](11_SOURCE_POLICY.md).
2. **Schema first:** Provider profiles follow [02_PROVIDER_SCHEMA.md](02_PROVIDER_SCHEMA.md) and render according to [07_OUTPUT_SPEC.md](07_OUTPUT_SPEC.md).
3. **Freshness is explicit:** Dates use ISO 8601 and verification windows are defined in [05_VALIDATION_RULES.md](05_VALIDATION_RULES.md).
4. **Unknown is allowed:** Missing data is recorded in `missing_information`; invented data is never allowed.
5. **History is retained:** Pricing, benchmarks, incidents, and methodology changes remain auditable through [12_CHANGELOG.md](12_CHANGELOG.md).
6. **AI work is reviewable:** Agents must follow [AGENTS.md](AGENTS.md) and tool-specific prompt files before editing.

## Repository Map

| Path | Purpose |
|---|---|
| [README.md](README.md) | Entry point and orientation |
| [AGENTS.md](AGENTS.md) | Mandatory instructions for AI agents |
| [00_PROJECT.md](00_PROJECT.md) | Project scope, principles, and governance |
| [01_RESEARCH_SPEC.md](01_RESEARCH_SPEC.md) | Research workflow and evidence capture process |
| [02_PROVIDER_SCHEMA.md](02_PROVIDER_SCHEMA.md) | Canonical provider data model |
| [03_PROVIDER_LIST.md](03_PROVIDER_LIST.md) | Provider inventory and status tracking |
| [04_BATCHES.md](04_BATCHES.md) | Batch planning and execution order |
| [05_VALIDATION_RULES.md](05_VALIDATION_RULES.md) | Merge gates and field validation rules |
| [06_STYLE_GUIDE.md](06_STYLE_GUIDE.md) | Editorial and Markdown conventions |
| [07_OUTPUT_SPEC.md](07_OUTPUT_SPEC.md) | Provider profile output template |
| [08_QA_CHECKLIST.md](08_QA_CHECKLIST.md) | Pre-PR checklist |
| [09_CONTRIBUTING.md](09_CONTRIBUTING.md) | Contribution workflow |
| [10_GLOSSARY.md](10_GLOSSARY.md) | Canonical terms and definitions |
| [11_SOURCE_POLICY.md](11_SOURCE_POLICY.md) | Source trust hierarchy |
| [12_CHANGELOG.md](12_CHANGELOG.md) | Versioning and changelog rules |
| `providers/` | Provider research profiles |
| `benchmarks/` | Raw benchmark outputs and normalized summaries |
| `pricing/` | Pricing snapshots and history files |
| `incidents/` | Incident timelines and postmortem notes |
| `sources/` | Archived source metadata and local evidence references |
| `comparisons/` | Cross-provider comparisons derived from profiles |
| `rankings/` | Criteria-based rankings with reproducible scoring |
| `appendices/` | Supporting notes, methodology extensions, and references |

## Research Object Model

The central unit is a **provider profile** under `providers/`. A provider profile contains:

- YAML frontmatter for automation
- A human-readable Markdown report
- Source entries that satisfy [11_SOURCE_POLICY.md](11_SOURCE_POLICY.md)
- Explicit verification dates
- Confidence scoring
- Missing information and open questions

Supporting artifacts such as raw benchmark output, pricing snapshots, and incident records must be linked from the profile rather than duplicated in prose.

## Quality Bar

A provider profile is publishable only when it passes the hard gates in [05_VALIDATION_RULES.md](05_VALIDATION_RULES.md) and all blocking items in [08_QA_CHECKLIST.md](08_QA_CHECKLIST.md). Draft profiles may exist, but their status must be explicit in frontmatter and in [03_PROVIDER_LIST.md](03_PROVIDER_LIST.md).

## Governance

Methodology changes use semantic versioning as defined in [12_CHANGELOG.md](12_CHANGELOG.md). Breaking schema changes require:

1. A changelog entry
2. A migration note
3. Updates to validation rules, output templates, and agent instructions
4. Review of affected provider profiles

## AI Automation Expectations

AI agents may draft, normalize, validate, and cross-link documentation. They must not invent provider facts, cite AI-generated text as evidence, or silently remove uncertain data. Tool-specific instructions are maintained in [CODEX.md](CODEX.md), [CLAUDE.md](CLAUDE.md), [GEMINI.md](GEMINI.md), [CHATGPT.md](CHATGPT.md), and [DEEP_RESEARCH.md](DEEP_RESEARCH.md).
