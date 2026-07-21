# 06 — Style Guide

> Methodology version: **1.0.0** · Repository standard · 2026-07-21

---

## Purpose

This guide defines the editorial standard for all files in `hosting-research`.
Follow it precisely. Consistency across 150–200 provider profiles makes the repository
usable by humans and machines alike.

---

## 1. Headings

Use ATX-style headings (`#` prefix). Never use Setext-style (`===` underlines).

```markdown
# Level 1 — document title only (one per file)
## Level 2 — major sections
### Level 3 — subsections
#### Level 4 — sub-subsections (use sparingly)
```

- Never skip heading levels (no `##` followed immediately by `####`).
- Heading text uses **Title Case** for Level 1 and Level 2.
- Heading text uses **Sentence case** for Level 3 and below.
- No punctuation at end of headings.

---

## 2. Tables

- All tables must have a header row.
- Use pipe syntax (`|`). Align pipes for readability (optional but preferred).
- Column count must be consistent across all rows.
- Use `—` (em dash) for empty cells that are intentionally missing.
- Use `N/A` only when the concept does not apply (different from unknown).
- Use `Unknown` when the value exists but has not been verified.

```markdown
| Field      | Value       | Source     |
|------------|-------------|------------|
| CPU        | AMD EPYC 7763 | YABS 2026-07-10 |
| RAM        | 32 GB ECC   | Official docs |
| IPv6       | Unknown     | —          |
```

---

## 3. Terminology

Use the canonical form below. Do not alternate between synonyms.

| Canonical | Avoid |
|---|---|
| VPS | vps, virtual server, virtual machine (unless technically precise) |
| Bare Metal | bare-metal, baremetal, dedicated server (only if no VPS layer) |
| Dedicated Server | dedi, dedicated, DS |
| Object Storage | object store, S3-compatible storage (use only when describing compatibility) |
| IPv4 | ipv4, IP v4, v4 |
| IPv6 | ipv6, IP v6, v6 |
| Anycast | anycast, any-cast |
| BGP | bgp, Border Gateway Protocol (spell out only in glossary) |
| ASN | asn, Autonomous System Number (spell out only in glossary) |
| YABS | yabs (always uppercase) |
| fio | FIO, Fio (always lowercase) |
| iperf3 | iPerf3, Iperf3, iperf (always lowercase with 3) |
| Geekbench | geekbench, GeekBench |
| NVMe | NVME, nvme |
| SSD | ssd |
| HDD | hdd |
| RAID | Raid, raid |
| KVM | kvm |
| LXC | lxc |
| OpenVZ | Openvz, openvz |

---

## 4. Capitalization

- Cloud provider names: match official branding exactly.
  - `Hetzner Online` not `Hetzner online`
  - `DigitalOcean` not `Digital Ocean`
  - `OVHcloud` not `OVH Cloud` or `OVH`
  - `Vultr` not `VULTR`
  - `Linode` (historical name; use `Akamai Cloud` for current branding, note alias)
- Technology names: follow `§ 3. Terminology` above.
- Region names: capitalize properly (`Western Europe`, `North America`).
- Product names: capitalize as the provider does (`Hetzner Cloud`, `Vultr High Frequency`).

---

## 5. Markdown Style

- Use `**bold**` for emphasis of key terms (first occurrence in a section, warnings).
- Use `_italic_` for technical terms being defined for the first time.
- Use `inline code` for: provider IDs, field names, file paths, command names, version strings.
- Use fenced code blocks (triple backtick) for: JSON/YAML/Markdown examples, terminal output.
- Never use raw HTML except for: `<br>` in table cells where a newline is required.
- No trailing spaces on any line.
- Single blank line between paragraphs.
- Single blank line before and after every heading, table, and code block.
- File ends with exactly one newline.

---

## 6. Lists

- Use `-` for unordered lists (not `*` or `+`).
- Use `1.` for ordered lists (auto-numbered by renderer).
- Do not mix list styles within a single list.
- Capitalize the first word of each list item.
- No period at the end of short list items (< 10 words). Use a period for full sentences.

---

## 7. Notes and Warnings

```markdown
> **Note:** Use for supplementary information that does not affect the primary content.

> **Warning:** Use for data that is uncertain, contested, or potentially misleading.

> **Stale:** Use when a field has not been verified within the freshness threshold.
```

---

## 8. References and Cross-Links

- Link to other repository files using relative Markdown links:
  `[Provider Schema](02_PROVIDER_SCHEMA.md)`
- Link to other provider profiles using the provider ID format:
  `[Hetzner](providers/hetzner.md)`
- External links must include the scheme, for example `https://example.com`.
- Do not use bare URLs in prose — always wrap them in Markdown link syntax.
- Citation format in provider profiles:
  `[Source title — example.com](https://example.com/source) · accessed YYYY-MM-DD`

---

## 9. Date and Time Format

- All dates: ISO 8601 `YYYY-MM-DD`.
- All timestamps: ISO 8601 `YYYY-MM-DDTHH:MM:SSZ` (UTC).
- Never use locale-specific formats (`07/21/2026`, `21.07.2026`).
- Never use relative dates (`last month`, `recently`) in data fields.

---

## 10. Units and Numbers

- Storage: always specify unit. Use `GB`, `TB`, `PB`. Not `Gb`, `gig`.
- Network speed: use `Gbps`, `Mbps`, `Kbps`. Not `GB/s` for network throughput.
- CPU cores: `vCPU` for virtual, `CPU` or `core` for physical.
- RAM: `GB` unless < 1 GB, then `MB`.
- Prices: always include currency code (ISO 4217) and billing period.
  Example: `€4.51/month (excl. VAT)` or `$12.00/month (incl. VAT)`.
- Percentages: `CPU steal: 0.3%` — always include `%` symbol.
- Latency: `ms` always lowercase.

---

## 11. Currency Handling

- Use ISO 4217 currency codes: `EUR`, `USD`, `GBP`, `CHF`, `SEK`, `DKK`, `NOK`, `PLN`.
- Always state whether VAT is included: `(excl. VAT)` or `(incl. VAT)`.
- If a provider bills in multiple currencies, document the primary billing currency first.
- Do not convert between currencies — document the price in the provider's billing currency.
- Record the exchange rate only if the provider pegs to another currency.
