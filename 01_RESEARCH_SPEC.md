# 01 — Research Specification

> Methodology version: **1.0.0** · Repository standard · 2026-07-21

## Purpose

This specification defines how provider research is performed, recorded, reviewed, and updated. Use it together with [02_PROVIDER_SCHEMA.md](02_PROVIDER_SCHEMA.md), [05_VALIDATION_RULES.md](05_VALIDATION_RULES.md), [07_OUTPUT_SPEC.md](07_OUTPUT_SPEC.md), and [11_SOURCE_POLICY.md](11_SOURCE_POLICY.md).

## Research Lifecycle

| Phase | Output | Required references |
|---|---|---|
| Intake | Provider entry in [03_PROVIDER_LIST.md](03_PROVIDER_LIST.md) | [04_BATCHES.md](04_BATCHES.md) |
| Evidence capture | Source records and archived links | [11_SOURCE_POLICY.md](11_SOURCE_POLICY.md) |
| Profile drafting | Provider Markdown file | [02_PROVIDER_SCHEMA.md](02_PROVIDER_SCHEMA.md), [07_OUTPUT_SPEC.md](07_OUTPUT_SPEC.md) |
| Validation | Completed QA checklist | [05_VALIDATION_RULES.md](05_VALIDATION_RULES.md), [08_QA_CHECKLIST.md](08_QA_CHECKLIST.md) |
| Review | Pull request | [09_CONTRIBUTING.md](09_CONTRIBUTING.md) |
| Maintenance | Changelog and refreshed verification dates | [12_CHANGELOG.md](12_CHANGELOG.md) |

## Research Boundaries

Researchers may collect:

- Official provider identity, product, pricing, location, SLA, and documentation data
- Independent benchmark results with raw output
- Routing and ASN evidence from accepted network sources
- Incident data from official status pages and postmortems
- Community reports when the source policy allows them

Researchers must not:

- Guess unavailable values
- Convert currencies unless the provider itself bills that way
- Treat marketing claims as performance facts
- Use affiliate review pages as evidence
- Collapse conflicting sources into a single unqualified value
- Remove historical benchmark or pricing entries without replacement history

## Evidence Capture Workflow

1. Identify the exact claim being researched.
2. Collect the highest available source tier from [11_SOURCE_POLICY.md](11_SOURCE_POLICY.md).
3. Record the source title, URL, source tier, accessed date, and archive URL.
4. Capture supporting artifacts where appropriate:
   - Pricing screenshot or archived page
   - Raw benchmark output
   - API response excerpt with timestamp
   - Status page incident URL
5. Enter data into the provider profile using [02_PROVIDER_SCHEMA.md](02_PROVIDER_SCHEMA.md).
6. Record unresolved gaps in `missing_information`.
7. Record contradictory evidence in `potential_inconsistencies`.

## Required Provider Sections

Every provider profile must include the sections defined in [07_OUTPUT_SPEC.md](07_OUTPUT_SPEC.md):

- Status and metadata
- Executive summary
- Provider identity
- Products and pricing
- Infrastructure and regions
- Network and ASN
- Benchmarks
- Reliability and incidents
- Security and compliance
- Support and operations
- Sources
- Missing information
- Open questions
- Potential inconsistencies
- QA status

## Confidence Scoring

Use a 1–5 scale for confidence fields.

| Score | Meaning | Allowed use |
|---|---|---|
| 1 | Unverified or single weak source | Draft only |
| 2 | Partially verified with gaps | Draft only |
| 3 | Minimally verified; mergeable if all hard gates pass | Publishable |
| 4 | Strongly verified by recent primary or independent sources | Publishable |
| 5 | Reproducible, current, independently corroborated | Publishable |

The `confidence.overall` score must not exceed the lowest confidence score of any critical category unless the exception is explained in `missing_information`.

## Freshness Windows

| Data category | Freshness window | Rationale |
|---|---|---|
| Pricing | 30 days | Prices change frequently |
| Product specifications | 90 days | Plans and hardware change regularly |
| Network and ASN | 180 days | Routing changes less frequently but still matters |
| Datacenter locations | 180 days | Facility availability can change |
| Benchmarks | 365 days | Useful historically, but must be dated |
| Incidents | Continuous append-only record | Reliability requires history |
| Compliance certifications | Certification validity period | Expiry date controls freshness |

Profiles may retain stale data if clearly marked. Stale data does not satisfy freshness gates in [05_VALIDATION_RULES.md](05_VALIDATION_RULES.md).

## Benchmark Research Rules

Benchmark data must include:

- Provider ID
- Plan tested
- Location
- Test date
- Tool name and version when available
- Raw output reference
- Normalized summary fields
- Statement of whether the result is representative, anecdotal, or repeated

At minimum, YABS output is accepted for baseline CPU, disk, and network context. Specialized benchmark suites may be added under `benchmarks/` when documented in the provider profile.

## Conflict Handling

When sources disagree:

1. Prefer the higher-tier source.
2. Prefer the newer source only when the tier difference does not make the newer source unsuitable.
3. Record both claims in `potential_inconsistencies`.
4. Do not publish a critical value when two current T1 sources conflict.
5. Use `open_questions` when the conflict requires provider clarification.

## AI Research Agent Rules

AI agents must:

- Read [AGENTS.md](AGENTS.md) before acting
- Read this file and the relevant schema and source policy before researching
- Use direct sources, not summaries of sources
- Include enough source metadata for a human reviewer to verify the claim
- Stop at the assigned batch boundary from [04_BATCHES.md](04_BATCHES.md)
- Leave uncertainty explicit

## Completion Definition

A research task is complete when:

- The provider profile follows [07_OUTPUT_SPEC.md](07_OUTPUT_SPEC.md)
- Data conforms to [02_PROVIDER_SCHEMA.md](02_PROVIDER_SCHEMA.md)
- Hard validation gates pass under [05_VALIDATION_RULES.md](05_VALIDATION_RULES.md)
- Blocking QA items in [08_QA_CHECKLIST.md](08_QA_CHECKLIST.md) are cleared
- [12_CHANGELOG.md](12_CHANGELOG.md) has the required entry
