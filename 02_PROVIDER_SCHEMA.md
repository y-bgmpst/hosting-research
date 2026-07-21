# 02 — Provider Schema

> Methodology version: **1.0.0** · Repository standard · 2026-07-21

## Purpose

This file defines the canonical provider profile data model. Provider Markdown files render the model using [07_OUTPUT_SPEC.md](07_OUTPUT_SPEC.md), and validation is governed by [05_VALIDATION_RULES.md](05_VALIDATION_RULES.md).

## File Location and Naming

Provider profiles live in `providers/{provider-id}.md`.

Provider IDs use `{region}-{slug}`:

- `de-hetzner`
- `fr-ovhcloud`
- `nl-transip`
- `us-digitalocean`

The current repository contains intake profiles with shorter filenames. When a profile becomes active research, rename it to the canonical provider ID and update [03_PROVIDER_LIST.md](03_PROVIDER_LIST.md).

## Frontmatter Schema

Every provider profile begins with YAML frontmatter.

```yaml
---
schema_version: "1.0.0"
provider_id: "de-example"
name: "Example Hosting GmbH"
aliases: []
status: "draft"
region: "de"
headquarters_country: "DE"
founded_year: 2000
website: "https://example.com"
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
```

## Field Definitions

| Field | Type | Required | Description |
|---|---|---:|---|
| `schema_version` | string | Yes | Must match current methodology version unless migration notes permit otherwise |
| `provider_id` | string | Yes | Canonical `{region}-{slug}` identifier |
| `name` | string | Yes | Official provider name |
| `aliases` | array of strings | Yes | Former names, common abbreviations, acquired brands |
| `status` | enum | Yes | `intake`, `draft`, `review`, `published`, `stale`, `archived` |
| `region` | string | Yes | Region code from [05_VALIDATION_RULES.md](05_VALIDATION_RULES.md) |
| `headquarters_country` | string or null | Yes | ISO 3166-1 alpha-2 country code, or null for unverified intake |
| `founded_year` | integer or null | Yes | Year founded when verified |
| `website` | URL or null | Yes | Official website |
| `research_batch` | string | Yes | Batch ID from [04_BATCHES.md](04_BATCHES.md) |
| `last_updated` | date | Yes | Last repository edit date |
| `last_verified` | object | Yes | Category-level verification dates |
| `confidence` | object | Yes | 1–5 confidence scores |
| `tags` | array of strings | Yes | Search and classification labels |

## Profile Body Data Model

The Markdown body must represent the following logical objects.

### Provider Identity

| Field | Type | Description |
|---|---|---|
| `legal_name` | string or null | Registered legal entity |
| `brand_name` | string | Public brand |
| `ownership` | string or null | Parent company or ownership notes |
| `headquarters` | string or null | City and country |
| `founded_year` | integer or null | Verified founding year |
| `primary_markets` | array | Market geography |

### Products

| Field | Type | Description |
|---|---|---|
| `product_types` | array | One or more canonical product types |
| `virtualization` | array | KVM, LXC, OpenVZ, VMware, proprietary, unknown |
| `managed_services` | array | Managed databases, Kubernetes, support tiers, backups |
| `special_capabilities` | array | GPU, ARM, object storage, edge, high-memory, high-frequency CPU |

Canonical product types:

- `vps`
- `cloud`
- `bare_metal`
- `dedicated`
- `gpu`
- `arm`
- `storage`
- `managed`
- `network`

### Pricing

```yaml
pricing:
  currency: "EUR"
  vat_included: false
  billing_periods: ["hourly", "monthly"]
  plans:
    - name: "Example 2 GB"
      category: "vps"
      vcpu: 1
      ram_gb: 2
      storage:
        amount: 40
        unit: "GB"
        type: "NVMe"
      transfer:
        amount: 20
        unit: "TB"
      price:
        amount: 4.50
        currency: "EUR"
        period: "month"
        vat_included: false
      source_id: "src-001"
```

### Infrastructure

| Field | Type | Description |
|---|---|---|
| `datacenter_locations` | array | City/region/country entries |
| `availability_zones` | array | Provider-defined zones |
| `hardware_notes` | array | CPU, storage, and platform notes |
| `backup_options` | array | Snapshot and backup features |

### Network

| Field | Type | Description |
|---|---|---|
| `asn` | integer or array | Autonomous System Number |
| `peeringdb_url` | URL or null | PeeringDB page |
| `ixp_presence` | array | Internet exchange points |
| `ipv4` | object | Allocation, included addresses, extra cost |
| `ipv6` | object | Support, prefix size, deployment method |
| `ddos_protection` | object | Availability and limitations |

### Benchmarks

```yaml
benchmarks:
  - id: "bench-de-example-2026-07-21-yabs"
    date: "2026-07-21"
    plan: "Example 2 GB"
    location: "Falkenstein, DE"
    tool: "YABS"
    raw_output: "../benchmarks/de-example/2026-07-21-yabs.txt"
    summary:
      geekbench_single: null
      geekbench_multi: null
      disk_read_mb_s: null
      disk_write_mb_s: null
      network_notes: ""
    superseded: false
```

### Sources

```yaml
sources:
  - id: "src-001"
    title: "Example Hosting — Cloud Pricing"
    url: "https://example.com/pricing"
    archive_url: "https://web.archive.org/example"
    tier: "T1"
    accessed_date: "2026-07-21"
    claim_scope: ["pricing"]
    notes: ""
```

## Status Values

| Status | Meaning | Mergeable |
|---|---|---:|
| `intake` | Provider exists in inventory; no research claims published | Yes |
| `draft` | Research in progress; hard gates may be incomplete | No |
| `review` | Research complete and awaiting review | No |
| `published` | Meets all publication gates | Yes |
| `stale` | Previously published but freshness window expired | Yes with stale warning |
| `archived` | Out of scope, acquired, shut down, or superseded | Yes |

## Required Null Semantics

- Use `null` in frontmatter for not-yet-verified scalar values.
- Use `[]` for verified empty lists.
- Use `Unknown` in tables when the field exists but has not been verified.
- Use `N/A` only when the concept does not apply.

## Schema Change Policy

Schema changes require updates to:

- [05_VALIDATION_RULES.md](05_VALIDATION_RULES.md)
- [07_OUTPUT_SPEC.md](07_OUTPUT_SPEC.md)
- [08_QA_CHECKLIST.md](08_QA_CHECKLIST.md)
- [12_CHANGELOG.md](12_CHANGELOG.md)
- AI prompt files when instructions change
