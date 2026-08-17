<p align="center">
  <img src="./assets/readme-skill-hero.png" alt="readme-skill: Evidence before prose">
</p>

# readme-skill

[English](./README.md) | [简体中文](./README.zh-CN.md)

[![GitHub repository](https://img.shields.io/badge/GitHub-ZardLi1115%2Freadme--skill-181717?style=flat-square)](https://github.com/ZardLi1115/readme-skill)

A Claude Code skill for creating accurate, readable GitHub README files from repository evidence and explicit user confirmation.

## Highlights

| Capability | Why it matters |
|---|---|
| Bounded repository discovery | Reviews project structure, metadata, documentation, and configuration before drafting. |
| Evidence-led writing | Separates verified facts, user-confirmed details, uncertain claims, and missing information. |
| Bilingual README support | Provides English, Simplified Chinese, and bilingual README layouts. |
| Conservative publication rules | Avoids unsupported commands, links, compatibility claims, release details, and license statements. |
| Quality checklist | Validates factual accuracy, executable examples, links, badges, images, and bilingual consistency before writing. |

## Workflow

The skill uses a bounded documentation workflow:

1. Discover repository facts and available documentation.
2. Read only the applicable README guidance, templates, and quality checks.
3. Ask about language layout and optional public elements that cannot be verified locally.
4. Compose a complete draft with a fact ledger and explicit handling of existing README content.
5. Write README files only after the target files and changes are confirmed.
6. Run the quality checklist against the resulting files.

When a user chooses an OpenAI image service, the skill requests the API URL and key and uses [`scripts/generate-image.py`](./scripts/generate-image.py) to create and verify a local asset without publishing credentials.

## Repository structure

| Path | Purpose |
|---|---|
| [`SKILL.md`](./SKILL.md) | Skill definition, workflow, and documentation rules |
| [`scripts/generate-image.py`](./scripts/generate-image.py) | Generates local images through an OpenAI-compatible Images API |
| [`references/readme-structure.md`](./references/readme-structure.md) | README information architecture and section guidance |
| [`references/quality-checklist.md`](./references/quality-checklist.md) | Pre-draft and pre-write quality checks |
| [`references/badge-style.md`](./references/badge-style.md) | Evidence requirements and style guidance for badges |
| [`references/image-generation.md`](./references/image-generation.md) | Guidance for README visuals and image generation |
| [`templates/README.en.md`](./templates/README.en.md) | English README template |
| [`templates/README.zh-CN.md`](./templates/README.zh-CN.md) | Simplified Chinese README template |
| [`templates/README.bilingual.md`](./templates/README.bilingual.md) | Bilingual README layout template |

## Design principles

- **Evidence before prose:** document only what repository files or the user support.
- **Useful before exhaustive:** help readers understand the project and reach a first useful result quickly.
- **Explicit uncertainty:** omit or request confirmation for claims that cannot be verified.
- **Safe publication:** never place API keys or other secrets in README content.
- **Consistent bilingual docs:** keep commands, paths, URLs, versions, and other technical identifiers aligned across language files.

## Documentation

Start with [`SKILL.md`](./SKILL.md) for the complete workflow. Supporting guidance and templates are available in the [`references/`](./references/) and [`templates/`](./templates/) directories.

## License

No license file was found in the repository.
