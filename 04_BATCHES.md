# 04 — Research Batches

> Methodology version: **1.0.0** · Repository standard · 2026-07-21

## Purpose

Batches group provider research into reviewable units. A batch exists to limit scope, coordinate ownership, and make AI-assisted research auditable. Research agents must stop at the assigned batch boundary unless explicitly instructed otherwise.

## Batch Rules

- One provider profile per pull request unless a batch-wide metadata change is being made.
- Each provider in a batch must have a corresponding entry in [03_PROVIDER_LIST.md](03_PROVIDER_LIST.md).
- Batch status is derived from provider statuses, not from assumptions.
- A batch is complete only when all providers are `published` or intentionally `archived`.
- Methodology changes belong on `meta/{slug}` branches, not research batch branches.

## Batch Status Values

| Status | Meaning |
|---|---|
| `planned` | Batch exists but no provider research has started |
| `active` | At least one provider is in draft or review |
| `complete` | All providers are published or archived |
| `paused` | Work intentionally stopped with reason recorded |

## Current Batches

### B01 — Initial European Infrastructure Providers

Status: `planned`

Scope: Normalize the existing provider stubs into canonical profiles, then research each provider independently under [01_RESEARCH_SPEC.md](01_RESEARCH_SPEC.md).

| Provider ID | Display name | Profile | Status |
|---|---|---|---|
| `de-hetzner` | Hetzner | [providers/hetzner.md](providers/hetzner.md) | `intake` |
| `fr-ovhcloud` | OVHcloud | [providers/ovh.md](providers/ovh.md) | `intake` |
| `de-netcup` | netcup | [providers/netcup.md](providers/netcup.md) | `intake` |
| `de-ionos` | IONOS | [providers/ionos.md](providers/ionos.md) | `intake` |
| `nl-leaseweb` | Leaseweb | [providers/leaseweb.md](providers/leaseweb.md) | `intake` |

## Future Batch Design

Future batches should be created by market segment rather than arbitrary list size:

- Regional VPS and cloud providers
- Dedicated and Bare Metal providers
- GPU-primary providers
- Object Storage providers
- Edge and specialized infrastructure providers
- Hyperscale cloud providers

Each new batch must include:

- Batch ID
- Research scope
- Inclusion criteria
- Provider table
- Explicit exclusions
- Reviewer expectations

## Agent Batch Selection

When an AI agent is asked to research the next unfinished batch:

1. Read [AGENTS.md](AGENTS.md).
2. Read this file and [03_PROVIDER_LIST.md](03_PROVIDER_LIST.md).
3. Select the first batch whose status is not `complete`.
4. Work only on providers assigned to that batch.
5. Stop after the batch or provider requested by the user is complete.
