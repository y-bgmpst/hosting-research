# 12 — Changelog

> Methodology version: **1.0.0** · Repository standard · 2026-07-21

## Purpose

This file records methodology and repository framework changes. It also defines the versioning rules used by provider profiles and supporting artifacts.

## Current Release

## [1.0.0] — 2026-07-21

### Methodology Changes

- [MAJOR] Established the production documentation framework and cross-linked specification set.
- [MAJOR] Defined provider schema, output format, validation rules, source policy, QA checklist, and contribution workflow.
- [MAJOR] Added AI-agent operating instructions for Codex, Claude, Gemini, ChatGPT, Deep Research, and GitHub Copilot.

### Provider Updates

- Converted existing provider stubs into intake records without publishing provider claims.

### Additions

- Added [07_OUTPUT_SPEC.md](07_OUTPUT_SPEC.md) for provider profile rendering.
- Added [10_GLOSSARY.md](10_GLOSSARY.md) for canonical terminology.
- Added GitHub pull request and issue templates under `.github/`.

### Removals

- No provider records removed.

### Fixes

- Replaced incomplete framework stubs with complete methodology documents.

## Versioning Rules

The repository uses two parallel versioning tracks.

### Track 1 — Methodology

Applied to:

- [00_PROJECT.md](00_PROJECT.md)
- [01_RESEARCH_SPEC.md](01_RESEARCH_SPEC.md)
- [02_PROVIDER_SCHEMA.md](02_PROVIDER_SCHEMA.md)
- [05_VALIDATION_RULES.md](05_VALIDATION_RULES.md)
- [06_STYLE_GUIDE.md](06_STYLE_GUIDE.md)
- [07_OUTPUT_SPEC.md](07_OUTPUT_SPEC.md)
- [08_QA_CHECKLIST.md](08_QA_CHECKLIST.md)
- [09_CONTRIBUTING.md](09_CONTRIBUTING.md)
- [10_GLOSSARY.md](10_GLOSSARY.md)
- [11_SOURCE_POLICY.md](11_SOURCE_POLICY.md)
- [12_CHANGELOG.md](12_CHANGELOG.md)

Format: `MAJOR.MINOR.PATCH`

| Increment | Trigger |
|---|---|
| MAJOR | Breaking schema change, renamed or removed fields, type changes, or validation gates requiring provider migrations |
| MINOR | Additive optional fields, new validation rules, new source categories, or new workflow sections |
| PATCH | Clarification, correction, typo fix, or editorial improvement with no structural effect |

Current methodology version: `1.0.0`

### Track 2 — Provider Data

Provider profiles under `providers/` use `last_updated` and `last_verified` dates rather than separate semantic versions.

Provider updates are recorded under the nearest active release entry when they affect published or review-stage data.

## Changelog Entry Format

Use newest-first order.

```markdown
## [MAJOR.MINOR.PATCH] — YYYY-MM-DD

### Methodology Changes

- [MAJOR/MINOR/PATCH] Description · Affects: file list

### Provider Updates

- `{provider-id}` — what changed

### Additions

- New provider: `{provider-id}` — provider name

### Removals

- Removed: `{provider-id}` — reason

### Fixes

- `{provider-id}` — corrected field · Source: source ID or URL
```

## Rules

- Every pull request that changes methodology must add or update an entry in this file.
- Every breaking methodology change must describe migration impact.
- Provider data corrections must cite source evidence.
- Do not skip semantic version numbers.
- If MAJOR increments, reset MINOR and PATCH to zero.
- Dates must use ISO 8601 `YYYY-MM-DD`.
- Methodology entries appear before provider entries within a release block.
