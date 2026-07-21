# 11 — Source Policy

> Methodology version: **1.0.0** · Repository standard · 2026-07-21

---

## Purpose

This document defines which sources are acceptable as evidence in provider profiles,
how sources are ranked by trust, and how conflicts between sources are resolved.
All researchers must read this before beginning work. See also `01_RESEARCH_SPEC.md`.

---

## Source Trust Hierarchy

Sources are ranked **T1 (highest)** to **T5 (lowest)**.
Every factual claim must cite at least one source at T3 or above.
Pricing claims require T1 or T2. Infrastructure claims require T2 or above.

### T1 — Primary Official Sources

- Provider's own pricing page (direct URL, dated screenshot)
- Provider's own technical documentation or whitepaper
- Provider's own status page (for uptime/incident data)
- Provider's official API response (dated, reproducible)
- Provider's official ASN registration (PeeringDB, RIPE, ARIN, APNIC)
- Official compliance certifications from issuing bodies (ISO, SOC auditors)

### T2 — Verified Independent Measurement

- YABS, Geekbench, fio, iperf3 results with full raw output, dated, reproducible
- BGP.tools, Hurricane Electric BGP Toolkit, RIPE Stat (routing/ASN)
- PeeringDB (peering policy, IXP presence)
- Shodan, Censys (network exposure — for security research context only)
- Traceroute data with timestamps and source node identified
- Wayback Machine snapshots of T1 sources (for historical pricing)

### T3 — Established Technical Community

- LowEndTalk (LET) threads with ≥ 10 replies and reproducible reports
- ServeTheHome forums and articles
- Reddit r/selfhosted, r/webhosting, r/sysadmin threads (≥ 6 months old, ≥ 20 upvotes)
- Hacker News threads with provider employees or verified technical staff responding
- ServerBear, HostingDiscussion, WebHostingTalk (long-standing threads only)
- Independently published benchmarks by named researchers with methodology disclosed

### T4 — Review Aggregators and Journalism

- G2, Trustpilot (for support quality signals only — never for technical specs)
- TechRadar, PCMag, The Register (for product announcements and general positioning)
- CloudSpectator, Cockpit.io (for benchmark comparisons — treat as T3 if raw data disclosed)
- Provider blog posts and case studies (treat as T1 only for feature announcements, not performance claims)

### T5 — Low-Trust / Informational Only

- Anonymous forum posts without corroboration
- Reseller testimonials
- Wikipedia (use only to locate primary sources)
- ChatGPT, AI-generated summaries (never cite directly — use only to locate primary sources)
- Undated or non-archived web pages that may change without notice

---

## Mandatory Source Requirements by Field

| Field category | Minimum source tier | Additional requirement |
|---|---|---|
| Pricing | T1 | Direct URL + date |
| ASN / BGP | T1 (PeeringDB/RIPE) | ASN number must be verifiable |
| Datacenter locations | T1 or T2 | Cross-reference with PeeringDB |
| Benchmark results | T2 | Full raw output required |
| Uptime / SLA | T1 | Link to official SLA document |
| Compliance certifications | T1 | Certificate number or issuing body |
| CPU model | T1 or T2 | Reproducible from API or benchmark |
| IPv6 support | T1 or T2 | Test result acceptable |
| DDoS protection | T1 (product page) | Note: marketing claims require T2 corroboration |
| Support response time | T3+ | Community data acceptable |
| Overselling / CPU steal | T2 | Benchmark with steal% reported |

---

## Handling Source Conflicts

When two sources contradict each other:

1. Higher-tier source wins unless the lower-tier source is more recent and the higher-tier source is stale (> 90 days for pricing, > 180 days for infrastructure).
2. Record both values in `potential_inconsistencies` with source citations.
3. If both sources are T1 and conflict (e.g., pricing page vs. API), flag as `open_question` and do not publish either until resolved.
4. Never silently discard a conflicting source. Document it.

---

## Unacceptable Sources

The following may **never** be cited as evidence:

- Anonymous Pastebin/GitHub Gist without attributed author
- Affiliate review sites (detectable by referral links to the provider)
- Sources older than 24 months without archival (Wayback Machine)
- AI-generated summaries presented as fact
- Provider's own marketing collateral for performance claims (T4 max)
- Screenshots without URL, timestamp, and resolution metadata
- Hearsay or paraphrased quotes without linked original

---

## Archival Requirement

All T1 and T2 sources must be archived via the Wayback Machine or a local screenshot at the time of research.
Store archive URLs in the `sources` array using the `archive_url` field.
See `02_PROVIDER_SCHEMA.md` → `sources` section for the field definition.
