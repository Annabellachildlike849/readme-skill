# readme-skill

[English](./README.md) | [简体中文](./README.zh-CN.md)

[![GitHub repository](https://img.shields.io/badge/GitHub-ZardLi1115%2Freadme--skill-181717?style=flat-square)](https://github.com/ZardLi1115/readme-skill)

A Claude Code skill for drafting, improving, restructuring, translating, and auditing fact-based GitHub README files.

## What it does

`readme-skill` helps create readable GitHub README files while grounding public claims in repository evidence or explicit user confirmation.

It is designed to:

- inspect repository files, metadata, documentation, and configuration before writing;
- separate verified, user-confirmed, uncertain, and missing information;
- organize README content around project value, installation, first use, and deeper documentation;
- support English, Simplified Chinese, and bilingual README layouts;
- evaluate badges, images, and Star History charts conservatively;
- prevent unsupported commands, links, compatibility claims, release details, and license statements from being published.

## Workflow

The skill follows a bounded documentation workflow:

1. Discover repository facts and available documentation.
2. Read only the applicable README structure, badge, image, template, and quality guidance.
3. Ask the user about language layout and any optional public elements that cannot be verified from the repository.
4. Compose a complete draft with a fact ledger and explicit handling of existing README content.
5. Write README files only after the user explicitly confirms the target files and changes.
6. Run the quality checklist against the resulting files.

## Repository structure

| Path | Purpose |
|---|---|
| [`SKILL.md`](./SKILL.md) | Skill definition, workflow, and documentation rules |
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

Start with [`SKILL.md`](./SKILL.md) for the complete workflow and rules. The supporting guidance and templates are available in the [`references/`](./references/) and [`templates/`](./templates/) directories.

## License

No license file was found in the repository.
