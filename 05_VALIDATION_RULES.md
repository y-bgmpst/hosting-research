# 05 — Validation Rules

> Methodology version: **1.0.0** · Repository standard · 2026-07-21

---

## Purpose

These rules define the minimum quality bar for every provider profile in the repository.
Rules are either **hard** (published or review-stage profile must not merge without passing) or **soft** (documented exception allowed in `missing_information`). Intake profiles may merge with explicit `intake` status when they publish no provider claims. See [08_QA_CHECKLIST.md](08_QA_CHECKLIST.md) for the operational checklist.

---

## 1. Mandatory Fields

Every published or review-stage provider profile must populate the following fields before merge. Intake profiles must include frontmatter required by [02_PROVIDER_SCHEMA.md](02_PROVIDER_SCHEMA.md), but may use `null`, `Unknown`, or empty arrays for unverified facts.

| Field | Type | Hard/Soft |
|---|---|---|
| `id` | string — `{region}-{slug}` | Hard |
| `name` | string — official provider name | Hard |
| `region` | string — canonical region code | Hard |
| `headquarters_country` | string — ISO 3166-1 alpha-2, or null for intake | Hard for published/review |
| `founded_year` | integer or null for intake | Soft |
| `asn` | integer or array of integers | Hard for published/review |
| `datacenter_locations` | array of strings | Hard for published/review |
| `product_types` | array: one or more of `vps`, `cloud`, `bare_metal`, `dedicated`, `gpu`, `arm`, `storage` | Hard for published/review |
| `pricing.currency` | ISO 4217 code | Hard for published/review |
| `pricing.vat_included` | boolean | Hard for published/review |
| `pricing.plans` | array, minimum one entry | Hard for published/review |
| `confidence.overall` | integer 1–5 | Hard |
| `last_verified.pricing` | ISO 8601 date | Hard for published/review |
| `sources` | array, minimum 3 entries, minimum 2 at T1/T2 | Hard for published/review |
| `schema_version` | string matching current methodology version | Hard |
| `last_updated` | ISO 8601 date | Hard |

---

## 2. Required Sources

| Claim type | Minimum source tier | Count |
|---|---|---|
| Any pricing claim | T1 | 1 |
| ASN / BGP routing | T1 (PeeringDB / RIR) | 1 |
| Datacenter location | T1 or T2 | 1 |
| CPU model | T1 or T2 | 1 |
| Benchmark result | T2 (raw output required) | 1 |
| SLA / uptime commitment | T1 (official SLA doc) | 1 |
| Compliance certification | T1 (issuing body) | 1 |
| Overall profile | Any tier | 3 minimum |

---

## 3. Minimum Verification Requirements

A profile is considered minimally verified and eligible for `published` status when all of the following are true:

- `confidence.overall` ≥ 3
- `last_verified.pricing` is within 30 days of the PR merge date
- At least one benchmark result present (YABS minimum)
- ASN verified via PeeringDB, RIPE, ARIN, or APNIC
- All T1/T2 sources have an `archive_url` or local screenshot reference

---

## 4. Citation Rules

- Every source entry must include: `title`, `url`, `tier`, `accessed_date`.
- `archive_url` required for all T1 and T2 sources.
- Sources older than 24 months without archival are not accepted.
- No AI-generated summaries may be cited as sources.
- Affiliate review sites (detectable by referral links) are not accepted.
- URLs must return HTTP 200 or have a valid `archive_url`.

Source entry format (JSON):
```json
{
  "title": "Hetzner Cloud — Pricing",
  "url": "https://www.hetzner.com/cloud",
  "archive_url": "https://web.archive.org/web/20260715/https://www.hetzner.com/cloud",
  "tier": "T1",
  "accessed_date": "2026-07-15",
  "notes": ""
}
```

---

## 5. Table Validation

- All Markdown tables must have a header row.
- Column count must be consistent across all rows (including separator row).
- No merged cells.
- Empty cells: use `—` (em dash) for unknown/missing, `N/A` only when concept does not apply.
- Pricing tables must include: plan name, vCPU count, RAM, storage, bandwidth/transfer, price, billing period.

---

## 6. Markdown Validation

- One `# Level 1` heading per file (the document title).
- No skipped heading levels.
- No trailing whitespace.
- No raw HTML except `<br>` inside table cells.
- File ends with exactly one trailing newline (`\n`).
- Fenced code blocks must specify a language identifier.
- All links must be syntactically valid (`[text](https://example.com)` or `[text](README.md)`).

---

## 7. Consistency Rules

- Provider name in frontmatter must match `03_PROVIDER_LIST.md` exactly.
- Provider ID must follow `{region}-{slug}` format, all lowercase, hyphens only.
- Region code must be one of the canonical codes defined in `§ 8. Naming Conventions`.
- All dates must be ISO 8601 (`YYYY-MM-DD`). No locale-specific formats.
- Currency codes must be ISO 4217 (`EUR`, `USD`, `GBP`, etc.).
- Storage units: `GB`, `TB`, `PB` (uppercase). Never `Gb`, `gig`, `gigabyte`.
- Network speed units: `Gbps`, `Mbps` (mixed case as shown).
- CPU counts: `vCPU` for virtual, `core` for physical.

---

## 8. Naming Conventions

### Provider ID slug rules

- Lowercase ASCII only.
- Hyphens as word separators. No underscores, no spaces.
- No version numbers or dates in slug.
- Examples: `de-hetzner`, `nl-transip`, `us-digitalocean`, `fr-ovhcloud`

### Region codes

| Code | Region |
|---|---|
| `de` | Germany |
| `nl` | Netherlands |
| `fr` | France |
| `gb` | United Kingdom |
| `nordics` | Denmark, Finland, Norway, Sweden, Iceland |
| `eastern-eu` | Poland, Czech Republic, Hungary, Romania, Bulgaria, Baltic states, Ukraine |
| `southern-eu` | Spain, Italy, Portugal, Greece, Turkey |
| `na` | North America (USA, Canada, Mexico) |
| `sa` | South America |
| `asia` | Asia-Pacific (excl. Australia) |
| `au` | Australia and New Zealand |
| `af` | Africa |
| `me` | Middle East |
| `cloud` | Hyperscale cloud (no single geographic HQ applies) |
| `gpu` | GPU-primary providers |
| `arm` | ARM-primary providers |
| `storage` | Object storage primary providers |
| `specialized` | Edge, Kubernetes-native, niche compute |

---

## 9. Quality Gates

A provider profile must pass all quality gates before merge when it publishes provider claims. Intake profiles that publish no claims must still pass Markdown, schema-frontmatter, and cross-link checks.

| Gate | Requirement |
|---|---|
| **Source gate** | ≥ 3 sources, ≥ 2 at T1/T2 |
| **Freshness gate** | `last_verified.pricing` within 30 days |
| **Benchmark gate** | ≥ 1 benchmark result present |
| **ASN gate** | ASN verified via RIR or PeeringDB |
| **Schema gate** | JSON validates against `02_PROVIDER_SCHEMA.md` |
| **Markdown gate** | No Markdown violations (see `§ 6`) |
| **Confidence gate** | `confidence.overall` ≥ 3 |
| **QA gate** | All `[BLOCK]` items in `08_QA_CHECKLIST.md` cleared |
