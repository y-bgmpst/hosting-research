# 08 — QA Checklist

> Methodology version: **1.0.0** · Repository standard · 2026-07-21

---

## Purpose

Run this checklist on every provider profile before opening a pull request.
All items marked **[BLOCK]** are hard blockers for profiles that publish provider claims.
Intake profiles may leave research-specific blocks incomplete only when they publish no claims and clearly state `status: "intake"`.
Items marked **[WARN]** are warnings — document the gap in `missing_information` if unavoidable.

---

## 1. Research Completeness

- [ ] **[BLOCK]** Provider ID is correctly formatted (`{region}-{slug}`, all lowercase, no spaces)
- [ ] **[BLOCK]** All mandatory fields for the profile status are populated (see [05_VALIDATION_RULES.md](05_VALIDATION_RULES.md))
- [ ] **[BLOCK]** `confidence.overall` score calculated and justified
- [ ] **[BLOCK]** `last_verified.pricing` is within 30 days of PR date
- [ ] **[WARN]** `last_verified.infrastructure` is within 180 days
- [ ] **[WARN]** `last_verified.network` is within 180 days
- [ ] **[WARN]** All `missing_information` entries explain *why* the data is missing, not just that it is

---

## 2. Source Quality

- [ ] **[BLOCK]** Every pricing claim has a T1 source with direct URL and date
- [ ] **[BLOCK]** ASN number verified via PeeringDB, RIPE, ARIN, or APNIC
- [ ] **[BLOCK]** At least 3 sources total, minimum 2 at T1 or T2 (see `11_SOURCE_POLICY.md`)
- [ ] **[BLOCK]** No AI-generated summaries cited as sources
- [ ] **[WARN]** T1 and T2 sources archived via Wayback Machine or local screenshot
- [ ] **[WARN]** No sources older than 24 months without archival

---

## 3. Broken References

- [ ] **[BLOCK]** All URLs in `sources` array return HTTP 200 (or have valid archive URL)
- [ ] **[WARN]** All cross-links to other provider files use correct provider IDs
- [ ] **[WARN]** Benchmark result files referenced in JSON exist on disk

---

## 4. Duplicate Providers

- [ ] **[BLOCK]** Provider ID does not already exist in `03_PROVIDER_LIST.md`
- [ ] **[BLOCK]** No other file in `providers/` has the same slug
- [ ] **[WARN]** Provider is not a reseller of another already-profiled provider (document relationship if so)

---

## 5. Pricing

- [ ] **[BLOCK]** Pricing table uses the correct currency code (ISO 4217)
- [ ] **[BLOCK]** All prices state whether VAT is included (`vat_included: true/false`)
- [ ] **[BLOCK]** At least one pricing tier is fully documented
- [ ] **[WARN]** Pricing history entry added if pricing changed since last profile version
- [ ] **[WARN]** Billing cycle documented (hourly / monthly / annual)

---

## 6. Benchmarks

- [ ] **[WARN]** At least one YABS result present
- [ ] **[WARN]** Benchmark result includes: date, node location, plan tested, raw output URL or paste
- [ ] **[WARN]** `cpu_steal_pct` documented if benchmark tool reports it
- [ ] **[WARN]** Old benchmark results marked `superseded: true` if replaced

---

## 7. Networking

- [ ] **[BLOCK]** ASN field is populated and numeric
- [ ] **[WARN]** IPv6 support documented (`supported`, `allocation`, `deployment_method`)
- [ ] **[WARN]** Network tier documented (tier1_transit / tier2_transit / eyeball)
- [ ] **[WARN]** At least one IXP listed if provider is present at any

---

## 8. Schema Compliance

- [ ] **[BLOCK]** JSON file validates against schema in `02_PROVIDER_SCHEMA.md`
- [ ] **[BLOCK]** Markdown file follows template in [07_OUTPUT_SPEC.md](07_OUTPUT_SPEC.md)
- [ ] **[BLOCK]** Frontmatter fields are all present and correctly typed
- [ ] **[WARN]** No extra fields not defined in schema (use `extra` object for non-standard data)

---

## 9. Markdown Compliance

- [ ] **[BLOCK]** No raw HTML except where explicitly permitted by `06_STYLE_GUIDE.md`
- [ ] **[BLOCK]** All tables have header rows and consistent column counts
- [ ] **[WARN]** Headings use the correct hierarchy (no skipped levels)
- [ ] **[WARN]** No trailing whitespace on any line
- [ ] **[WARN]** File ends with a single newline

---

## 10. Editorial Consistency

- [ ] **[WARN]** Provider name matches the official name in `03_PROVIDER_LIST.md`
- [ ] **[WARN]** Technology names capitalized per `06_STYLE_GUIDE.md` § Terminology
- [ ] **[WARN]** No first-person language ("I tested", "we found")
- [ ] **[WARN]** No opinion language without attribution ("their support is great")
- [ ] **[WARN]** Dates are ISO 8601 (`YYYY-MM-DD`) throughout

---

## Sign-Off

Researcher: ________________
Date: ________________
Batch: ________________
Provider ID: ________________

All [BLOCK] items cleared: ☐ Yes
All [WARN] items resolved or documented: ☐ Yes / ☐ Documented in `missing_information`
