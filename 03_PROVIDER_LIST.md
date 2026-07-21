# 03 — Provider List

> Methodology version: **1.0.0** · Repository standard · 2026-07-21

## Purpose

This file is the canonical inventory for providers tracked by the repository. It is not a source of provider facts; it is an operational index used for batching, assignment, status tracking, and duplicate prevention.

Provider facts belong in `providers/{provider-id}.md` and must follow [02_PROVIDER_SCHEMA.md](02_PROVIDER_SCHEMA.md), [07_OUTPUT_SPEC.md](07_OUTPUT_SPEC.md), and [11_SOURCE_POLICY.md](11_SOURCE_POLICY.md).

## Status Values

| Status | Meaning |
|---|---|
| `intake` | Provider is listed but not researched |
| `draft` | Research is underway |
| `review` | Profile is ready for reviewer validation |
| `published` | Profile passed hard gates |
| `stale` | Published profile needs refresh |
| `archived` | Provider no longer active or no longer in scope |

## Current Inventory

The current repository contains intake records only. These entries preserve the existing provider stubs without adding new provider research.

| Provider ID | Display name | Region | Batch | Status | Profile | Notes |
|---|---|---|---|---|---|---|
| `de-hetzner` | Hetzner | `de` | `B01` | `intake` | [providers/hetzner.md](providers/hetzner.md) | Existing stub normalized as intake |
| `fr-ovhcloud` | OVHcloud | `fr` | `B01` | `intake` | [providers/ovh.md](providers/ovh.md) | Existing stub normalized as intake |
| `de-netcup` | netcup | `de` | `B01` | `intake` | [providers/netcup.md](providers/netcup.md) | Existing stub normalized as intake |
| `de-ionos` | IONOS | `de` | `B01` | `intake` | [providers/ionos.md](providers/ionos.md) | Existing stub normalized as intake |
| `nl-leaseweb` | Leaseweb | `nl` | `B01` | `intake` | [providers/leaseweb.md](providers/leaseweb.md) | Existing stub normalized as intake |

## Adding Providers

To add a provider:

1. Confirm the provider is in scope under [00_PROJECT.md](00_PROJECT.md).
2. Assign a canonical provider ID using [05_VALIDATION_RULES.md](05_VALIDATION_RULES.md).
3. Add the provider to the appropriate batch in [04_BATCHES.md](04_BATCHES.md).
4. Create `providers/{provider-id}.md` using [07_OUTPUT_SPEC.md](07_OUTPUT_SPEC.md).
5. Open a claim issue using `.github/ISSUE_TEMPLATE/provider-research.yml`.

## Duplicate Prevention

Before adding a provider, check:

- Existing canonical IDs
- Brand aliases
- Parent/subsidiary relationships
- Acquisitions or rebrands
- Reseller relationships

If a provider operates under multiple brands, create one canonical profile and list aliases in frontmatter unless each brand has materially distinct infrastructure, pricing, and support operations.
