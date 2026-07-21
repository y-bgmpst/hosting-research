# 07 — Output Specification

> Methodology version: **1.0.0** · Repository standard · 2026-07-21

## Purpose

This file defines the required Markdown structure for provider profiles. The data model is defined in [02_PROVIDER_SCHEMA.md](02_PROVIDER_SCHEMA.md), source quality is defined in [11_SOURCE_POLICY.md](11_SOURCE_POLICY.md), and validation is defined in [05_VALIDATION_RULES.md](05_VALIDATION_RULES.md).

## Provider Profile Template

Use this exact section order for provider profiles.

```markdown
---
schema_version: "1.0.0"
provider_id: "de-example"
name: "Example Provider"
aliases: []
status: "intake"
region: "de"
headquarters_country: null
founded_year: null
website: null
research_batch: "B01"
last_updated: "2026-07-21"
last_verified:
  pricing: null
  infrastructure: null
  network: null
  compliance: null
confidence:
  overall: 1
  pricing: 1
  infrastructure: 1
  network: 1
  reliability: 1
  support: 1
  compliance: 1
tags: []
---

# Example Provider

## Status

| Field | Value |
|---|---|
| Provider ID | `de-example` |
| Status | `intake` |
| Research batch | `B01` |
| Last updated | `2026-07-21` |
| Overall confidence | `1/5` |

## Executive Summary

This profile is an intake record. No provider claims are published until research is completed under `01_RESEARCH_SPEC.md`.

## Provider Identity

| Field | Value | Source |
|---|---|---|
| Official name | Unknown | — |
| Legal entity | Unknown | — |
| Headquarters | Unknown | — |
| Founded | Unknown | — |
| Website | Unknown | — |

## Products and Pricing

No pricing claims are published in intake status.

## Infrastructure and Regions

No infrastructure claims are published in intake status.

## Network and ASN

No network claims are published in intake status.

## Benchmarks

No benchmark data is published in intake status.

## Reliability and Incidents

No reliability or incident claims are published in intake status.

## Security and Compliance

No security or compliance claims are published in intake status.

## Support and Operations

No support claims are published in intake status.

## Sources

No sources recorded.

## Missing Information

| Category | Missing information | Required before publication |
|---|---|---|
| Pricing | Current plans and billing terms | Yes |
| Infrastructure | Datacenter locations and hardware notes | Yes |
| Network | ASN, IPv4, IPv6, peering | Yes |
| Benchmarks | Raw benchmark output | Yes |
| Reliability | SLA, status history, incidents | Yes |
| Compliance | Certifications and security posture | If claimed |

## Open Questions

No open questions recorded beyond standard intake research requirements.

## Potential Inconsistencies

No conflicting sources recorded.

## QA Status

This profile is not publishable until it passes `08_QA_CHECKLIST.md`.
```

## Published Profile Requirements

Before a profile can move to `published`, replace intake statements with sourced content in every applicable section and preserve empty sections only when the field is explicitly not applicable.

## Section Rules

### Status

The status table must match frontmatter exactly. If values differ, frontmatter is authoritative and the table must be corrected.

### Executive Summary

Summarize what the evidence supports. Do not include uncited claims. Keep the summary to three short paragraphs or fewer.

### Provider Identity

Identity fields require source references. The official provider website is acceptable for branding; legal entity claims require a stronger source when available.

### Products and Pricing

Pricing tables must include:

- Plan name
- Product category
- vCPU or core count
- RAM
- Storage amount and type
- Transfer or bandwidth
- Price
- Billing period
- VAT status
- Source reference

### Infrastructure and Regions

Document provider region names as the provider publishes them, then normalize location names in a separate column if needed.

### Network and ASN

ASN values must be verified against accepted network sources from [11_SOURCE_POLICY.md](11_SOURCE_POLICY.md). IPv6 support must distinguish between available, default, optional, and unavailable.

### Benchmarks

Benchmark summaries must link to raw output in `benchmarks/`. Do not paste long raw benchmark output into provider profiles.

### Reliability and Incidents

Reliability claims require source dates. Incident entries should include start time, end time when available, affected services, and postmortem link.

### Security and Compliance

Compliance claims require issuer, certificate or report identifier when available, validity period, and source.

### Sources

Sources must be listed in a table or structured list with `id`, title, tier, URL, archive URL, accessed date, and claim scope.

### Missing Information

Every missing item must explain why it is missing and what source would resolve it.

### Open Questions

Open questions are for unresolved research questions that require later investigation or provider clarification.

### Potential Inconsistencies

Conflicts between sources must include both source IDs and a recommended resolution path.

### QA Status

Record whether blocking checklist items are cleared. Do not mark a profile publishable unless [08_QA_CHECKLIST.md](08_QA_CHECKLIST.md) passes.
