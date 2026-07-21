# 10 — Glossary

> Methodology version: **1.0.0** · Repository standard · 2026-07-21

## Purpose

This glossary defines canonical terminology for provider profiles, comparisons, rankings, and AI agent output. Style rules are maintained in [06_STYLE_GUIDE.md](06_STYLE_GUIDE.md).

## Terms

| Term | Definition |
|---|---|
| ARM | CPU architecture commonly used for power-efficient cloud instances and specialized compute products |
| ASN | Autonomous System Number; a numeric identifier for an independently routed network |
| Availability Zone | Provider-defined isolated location within a region, usually intended for fault separation |
| Bare Metal | Physical server where the customer receives direct access without a shared hypervisor layer |
| BGP | Border Gateway Protocol; routing protocol used to exchange reachability information between autonomous systems |
| Cloud | Elastic infrastructure service with API-driven provisioning and usually hourly or monthly billing |
| Core | Physical CPU core, used when documenting dedicated or Bare Metal hardware |
| Dedicated Server | Physical server leased to one customer, often with fixed monthly billing |
| DDoS Protection | Filtering or mitigation service intended to reduce denial-of-service attack impact |
| fio | Flexible I/O tester used for disk benchmark measurements |
| Geekbench | Benchmark suite commonly reported by YABS for CPU performance |
| GPU | Graphics Processing Unit, used for accelerated compute and AI workloads |
| HDD | Hard Disk Drive storage |
| IOPS | Input/output operations per second |
| IPv4 | Internet Protocol version 4 address support |
| IPv6 | Internet Protocol version 6 address support |
| IXP | Internet Exchange Point where networks interconnect |
| KVM | Kernel-based Virtual Machine virtualization |
| LXC | Linux Containers operating-system-level virtualization |
| NVMe | Non-Volatile Memory Express storage interface |
| Object Storage | API-addressable object-based storage, often S3-compatible |
| OpenVZ | Container-based virtualization technology |
| Peering | Direct network interconnection between autonomous systems |
| Region | Provider-defined geography for deploying services |
| SLA | Service Level Agreement |
| SSD | Solid State Drive storage |
| T1–T5 | Source trust tiers defined in [11_SOURCE_POLICY.md](11_SOURCE_POLICY.md) |
| Transfer | Data volume included in a billing period |
| vCPU | Virtual CPU assigned to a virtual machine or cloud instance |
| VPS | Virtual Private Server, usually a fixed-size virtual server product |
| YABS | Yet-Another-Bench-Script, a common server benchmark script |

## Usage Notes

- Use canonical capitalization from this glossary and [06_STYLE_GUIDE.md](06_STYLE_GUIDE.md).
- Spell out specialized abbreviations only when clarity requires it.
- Do not use marketing category names as schema values unless mapped to canonical categories in [02_PROVIDER_SCHEMA.md](02_PROVIDER_SCHEMA.md).
