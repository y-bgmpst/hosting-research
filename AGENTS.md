# AGENTS.md

## Role

AI agents working in this repository are research assistants, technical editors, validators, and automation maintainers. They are not independent sources of truth.

## Mandatory First Read

Before making changes, read:

1. [README.md](README.md)
2. [00_PROJECT.md](00_PROJECT.md)
3. [01_RESEARCH_SPEC.md](01_RESEARCH_SPEC.md)
4. [02_PROVIDER_SCHEMA.md](02_PROVIDER_SCHEMA.md)
5. [03_PROVIDER_LIST.md](03_PROVIDER_LIST.md)
6. [04_BATCHES.md](04_BATCHES.md)
7. [05_VALIDATION_RULES.md](05_VALIDATION_RULES.md)
8. [06_STYLE_GUIDE.md](06_STYLE_GUIDE.md)
9. [07_OUTPUT_SPEC.md](07_OUTPUT_SPEC.md)
10. [08_QA_CHECKLIST.md](08_QA_CHECKLIST.md)
11. [09_CONTRIBUTING.md](09_CONTRIBUTING.md)
12. [10_GLOSSARY.md](10_GLOSSARY.md)
13. [11_SOURCE_POLICY.md](11_SOURCE_POLICY.md)
14. [12_CHANGELOG.md](12_CHANGELOG.md)

Tool-specific prompts are maintained in [CODEX.md](CODEX.md), [CLAUDE.md](CLAUDE.md), [GEMINI.md](GEMINI.md), [CHATGPT.md](CHATGPT.md), and [DEEP_RESEARCH.md](DEEP_RESEARCH.md).

## Non-Negotiable Rules

- Do not invent provider facts.
- Do not cite AI-generated text as evidence.
- Do not treat search snippets as sources.
- Do not remove citations or uncertainty notes.
- Do not change verified facts unless a better source supports the change.
- Do not research providers unless the user explicitly asks for provider research.
- Do not work outside the requested provider, batch, or methodology scope.
- Use ISO 8601 dates (`YYYY-MM-DD`) everywhere.
- Record missing data in `missing_information`.
- Record unresolved contradictions in `potential_inconsistencies`.
- Keep historical benchmark, pricing, and incident records unless a documented correction is required.

## Provider Research Workflow

When asked to research providers:

1. Identify the assigned provider or batch from [03_PROVIDER_LIST.md](03_PROVIDER_LIST.md) and [04_BATCHES.md](04_BATCHES.md).
2. Read the target provider profile.
3. Collect evidence according to [11_SOURCE_POLICY.md](11_SOURCE_POLICY.md).
4. Populate the profile using [02_PROVIDER_SCHEMA.md](02_PROVIDER_SCHEMA.md) and [07_OUTPUT_SPEC.md](07_OUTPUT_SPEC.md).
5. Apply validation rules from [05_VALIDATION_RULES.md](05_VALIDATION_RULES.md).
6. Complete [08_QA_CHECKLIST.md](08_QA_CHECKLIST.md).
7. Update [12_CHANGELOG.md](12_CHANGELOG.md) when the change requires it.

## Documentation Maintenance Workflow

When asked to improve repository documentation:

1. Preserve existing intent where usable.
2. Improve structure, cross-links, and consistency.
3. Keep documents self-contained enough for future agents.
4. Ensure all framework documents reference related documents where appropriate.
5. Avoid provider claims unless already sourced in the repository.

## Source Handling

Every source entry must include:

- Title
- URL
- Source tier
- Accessed date
- Archive URL for T1/T2 sources when required
- Claim scope

When source quality is insufficient, record the gap rather than filling the field.

## Output Standards

Follow [06_STYLE_GUIDE.md](06_STYLE_GUIDE.md). Markdown must have:

- One H1 per file
- No skipped heading levels
- Consistent tables
- Relative links for repository files
- Explicit unknowns
- One final newline

## Commit and PR Expectations

Use [09_CONTRIBUTING.md](09_CONTRIBUTING.md) and [.github/PULL_REQUEST_TEMPLATE.md](.github/PULL_REQUEST_TEMPLATE.md). Pull requests must clearly state scope, sources, validation status, and unresolved risks.
