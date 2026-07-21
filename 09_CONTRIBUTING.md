# 09 — Contributing

> Methodology version: **1.0.0** · Repository standard · 2026-07-21

---

## Quick Start

1. Read `00_PROJECT.md` (scope and philosophy).
2. Read `01_RESEARCH_SPEC.md` (how to research).
3. Read `02_PROVIDER_SCHEMA.md` (what to document).
4. Read `06_STYLE_GUIDE.md` (how to write it).
5. Read `11_SOURCE_POLICY.md` (which sources to use).
6. Pick an unassigned provider from `04_BATCHES.md`.
7. Open an issue claiming the provider before starting work.
8. Follow the research checklist in `01_RESEARCH_SPEC.md`.
9. Use the templates in `07_OUTPUT_SPEC.md`.
10. Run the QA checklist in `08_QA_CHECKLIST.md` before opening a PR.

---

## Repository Workflow

```
main
 └── research/{provider-id}       ← all provider research work
 └── fix/{provider-id}-{field}    ← targeted corrections
 └── meta/{description}           ← methodology / framework changes
```

Never commit directly to `main`. All changes go through pull requests.

---

## Branch Strategy

| Branch prefix | Purpose |
|---|---|
| `research/{provider-id}` | New provider profile or major update |
| `fix/{provider-id}-{field}` | Single-field correction (pricing, ASN, etc.) |
| `benchmark/{provider-id}-{date}` | New benchmark run |
| `meta/{slug}` | Changes to methodology, schema, or framework files |
| `batch/{batch-id}` | Coordinated batch research (multiple providers) |

---

## Commit Messages

Format: `{type}({scope}): {description}`

| Type | Use |
|---|---|
| `research` | New or substantially updated provider profile |
| `fix` | Correction to existing data |
| `benchmark` | New benchmark results added |
| `meta` | Framework / methodology change |
| `docs` | Non-data documentation update |
| `remove` | Provider removed (with reason) |

Examples:
```
research(de-hetzner): add initial provider profile
fix(nl-transip): correct IPv6 /48 allocation to /64
benchmark(us-vultr): add YABS results 2026-07-15 from NYC node
meta(02_PROVIDER_SCHEMA): add gpu_passthrough field (v1.1.0)
```

---

## Pull Request Requirements

Every PR must include:

- **Summary**: What changed and why.
- **Sources**: At minimum one T1/T2 source per new factual claim (see `11_SOURCE_POLICY.md`).
- **QA**: Confirmation that `08_QA_CHECKLIST.md` was completed.
- **Schema compliance**: Provider files must validate against `02_PROVIDER_SCHEMA.md`.
- **Changelog entry**: Added to [12_CHANGELOG.md](12_CHANGELOG.md) when required.

PR title format: `[{type}] {Provider Name} — {summary}` (max 72 chars)

Example: `[research] Hetzner — initial profile with YABS 2026-07`

---

## Review Process

PRs require at least **one reviewer approval** before merge.

Reviewers check:
1. Source quality (per `11_SOURCE_POLICY.md`)
2. Schema compliance (per `02_PROVIDER_SCHEMA.md`)
3. Validation rules (per `05_VALIDATION_RULES.md`)
4. Style compliance (per `06_STYLE_GUIDE.md`)
5. QA checklist complete (per `08_QA_CHECKLIST.md`)

Reviewers may request changes if confidence scores appear inflated, sources are missing, or data conflicts with known public information.

---

## Updating Existing Providers

When updating a provider profile:

- **Pricing update**: Requires T1 source, update `last_verified.pricing` and `pricing_history`.
- **Benchmark update**: Add new result to `benchmarks` array (do not replace old results — keep history).
- **ASN / network update**: Verify against PeeringDB and update `last_verified.network`.
- **Incident update**: Append to `incidents` array with postmortem URL if available.
- **Schema migration**: Follow migration notes in [12_CHANGELOG.md](12_CHANGELOG.md) when MAJOR version bumps.

Do not delete old benchmark results. Mark superseded entries with `superseded: true`.

---

## Claiming a Provider

Before starting research:
1. Open a GitHub issue titled `[Claim] {Provider Name} ({provider-id})`.
2. Reference the batch ID from `04_BATCHES.md`.
3. Set a self-imposed deadline (recommended: 14 days).
4. If not completed within the deadline, the claim is released.

---

## Quality Requirements

A provider profile is ready for merge when:

- Confidence score ≥ 3 across all mandatory published-profile fields (see [05_VALIDATION_RULES.md](05_VALIDATION_RULES.md)).
- At least 3 sources cited, with at least 2 at T1 or T2.
- Pricing table is complete and dated within 30 days.
- At least one benchmark run present (YABS minimum).
- ASN verified via PeeringDB or equivalent.
- No unresolved editorial markers remaining.
- [08_QA_CHECKLIST.md](08_QA_CHECKLIST.md) fully passed.
