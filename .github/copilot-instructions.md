# GitHub Copilot Instructions

## Repository Role

This repository is a research documentation framework. Copilot suggestions must preserve source traceability, schema consistency, and explicit uncertainty.

## Required References

Before suggesting changes to provider files, align with:

- [../AGENTS.md](../AGENTS.md)
- [../02_PROVIDER_SCHEMA.md](../02_PROVIDER_SCHEMA.md)
- [../06_STYLE_GUIDE.md](../06_STYLE_GUIDE.md)
- [../07_OUTPUT_SPEC.md](../07_OUTPUT_SPEC.md)
- [../11_SOURCE_POLICY.md](../11_SOURCE_POLICY.md)

## Rules

- Do not generate uncited provider facts.
- Do not infer pricing, locations, ASN data, benchmarks, or compliance claims.
- Use `Unknown`, `null`, or `missing_information` when evidence is absent.
- Preserve citation IDs and source tables.
- Keep provider profile section order aligned with [../07_OUTPUT_SPEC.md](../07_OUTPUT_SPEC.md).
- Use canonical terminology from [../10_GLOSSARY.md](../10_GLOSSARY.md).
- Do not mark a profile as `published` unless hard gates in [../05_VALIDATION_RULES.md](../05_VALIDATION_RULES.md) pass.

## Preferred Patterns

- Relative links for repository files
- ISO 8601 dates
- Markdown tables with explicit source columns
- Append-only benchmark, pricing, and incident history
- Clear distinction between missing information and not-applicable fields
