<p align="center">
  <img src="./assets/readme-skill-hero.png" alt="readme-skill: Evidence before prose">
</p>

<h1 align="center">readme-skill</h1>

<p align="center">A Claude Code skill that builds GitHub README files from repository evidence.</p>

<p align="center">
  <a href="./README.md">English</a> | <a href="./README.zh-CN.md">简体中文</a>
</p>

<p align="center">
  <a href="https://github.com/ZardLi1115/readme-skill"><img src="https://img.shields.io/badge/GitHub-ZardLi1115%2Freadme--skill-181717?style=flat-square" alt="GitHub repository"></a>
  <a href="./LICENSE"><img src="https://img.shields.io/badge/License-MIT-22C55E?style=flat-square" alt="License: MIT"></a>
</p>

A Claude Code skill for creating accurate, readable GitHub README files from repository evidence and explicit user confirmation.

## Highlights

| Capability | Why it matters |
|---|---|
| Bounded repository discovery | Reviews project structure, metadata, documentation, and configuration before drafting. |
| Evidence-led writing | Separates verified facts, user-confirmed details, uncertain claims, and missing information. |
| Existing README choices | Offers explicit replace, selective-reuse, or extend modes before drafting. |
| Bilingual README support | Provides English, Simplified Chinese, and bilingual README layouts. |
| Safe publication rules | Avoids unsupported commands, links, compatibility claims, release details, and license statements. |
| Quality checklist | Validates factual accuracy, executable examples, links, badges, images, diagrams, and bilingual consistency before writing. |

## Architecture

```text
┌──────────────────┐  request  ┌──────────────────┐
│   User request   │──────────▶│   readme-skill   │
└──────────────────┘           └──────────────────┘
                          repository facts + user choices
                                         │
                                         ▼
                               ┌──────────────────┐
                               │ Bounded discovery│
                               │ and fact ledger  │
                               └────────┬─────────┘
                                        │
                                        ▼
┌──────────────────┐  confirmed  ┌──────────────────┐
│ README.md /      │◀────────────│ Draft, checklist,│
│ README.zh-CN.md  │             │ and write gate   │
└──────────────────┘             └──────────────────┘
```

The skill scans only the files needed to support public claims, records the evidence state, asks for decisions that cannot be verified, and writes only after explicit confirmation.

## Usage Example

The following is a summary of the process of generating a project README. For the result, see the [Long Horizon Pi Extension README](https://github.com/ZardLi1115/long-horizon-pi-extension).

> A `README.md` already exists in the repository. How should it be handled? → Replace completely\
> Which language layout should the new README use? → English + Simplified Chinese\
> Should the README include Shields.io badges? → Include verified badges\
> Does the README need a project image or visual asset? → Generate a new image\
> Generating a new image requires specific service information. Which option do you choose? → Provide service information\
> Which README visual should be generated with `gpt-image-2`? → Icon + short line\
> Choose the text in the icon; image models may not render text accurately. → Project name + recommended short line\
> Should a Star History chart be included? → Do not include a chart\
> The README project visual was generated and its file validation completed.

## Quick Start

1. Tell any agent: `Download this skill for me: https://github.com/ZardLi1115/readme-skill`
2. Call `readme-skill` and ask it to modify a repository README or create a new README for a named repository, for example: `Use readme-skill to update the README for <repository>, or create one for <repository>.`

## Workflow

The skill uses a bounded documentation workflow:

1. Discover repository facts and existing documentation.
2. If a README already exists, ask whether to replace it completely, replace it while selectively retaining approved information, or extend it in place.
3. Read only the applicable README guidance, templates, and quality checks.
4. Ask for unverifiable public choices through explicit options where possible.
5. Ask whether to include a source-backed ASCII architecture diagram; never use Mermaid.
6. Ask whether to include a usage example. If requested, collect confirmed text, image/assets, code or commands, expected result, placement, and language.
7. Compose a complete draft with a fact ledger, an optional Architecture section, an optional Usage Example, a verified Quick Start, and explicit handling of existing README content.
8. Write README files only after the target files and changes are confirmed, then run the quality checklist against the resulting files.

When a user chooses an OpenAI image service, the skill requests the API URL and key and uses [`scripts/generate-image.py`](./scripts/generate-image.py) to create and verify a local asset without publishing credentials.

## Repository structure

| Path | Purpose |
|---|---|
| [`SKILL.md`](./SKILL.md) | Skill definition, workflow, ASCII architecture rules, and documentation safeguards |
| [`scripts/generate-image.py`](./scripts/generate-image.py) | Generates local images through an OpenAI-compatible Images API |
| [`references/readme-structure.md`](./references/readme-structure.md) | README information architecture, architecture, and usage-example guidance |
| [`references/quality-checklist.md`](./references/quality-checklist.md) | Pre-draft and pre-write quality checks |
| [`references/badge-style.md`](./references/badge-style.md) | Evidence requirements and style guidance for badges |
| [`references/image-generation.md`](./references/image-generation.md) | Guidance for README visuals and image generation |
| [`templates/README.en.md`](./templates/README.en.md) | English README template |
| [`templates/README.zh-CN.md`](./templates/README.zh-CN.md) | Simplified Chinese README template |
| [`templates/README.bilingual.md`](./templates/README.bilingual.md) | Bilingual README layout template |

## Design principles

- **Evidence before prose:** document only what repository files or the user support.
- **Useful before exhaustive:** help readers understand the project and reach a first useful result quickly.
- **Restrained visual language:** no emoji; rely on verified image assets, badges, and source-backed ASCII diagrams.
- **Source-backed architecture:** draw optional architecture only as aligned ASCII Art in a `text` block; Mermaid is never used.
- **Confirmed examples:** add Usage Examples only from user-supplied or verified prose, assets, code, commands, and outcomes.
- **Verified Quick Start:** every generated README keeps a verified path to a first useful result; missing evidence prompts a question instead of an invented or omitted section.
- **Safe publication:** never place API keys or other secrets in README content.
- **Consistent bilingual docs:** keep commands, paths, URLs, versions, and other technical identifiers aligned across language files.

## Documentation

Start with [`SKILL.md`](./SKILL.md) for the complete workflow. Supporting guidance and templates are available in the [`references/`](./references/) and [`templates/`](./templates/) directories.

## License

This project is licensed under the [MIT License](./LICENSE).

## Acknowledgments

Thanks to the [Linux.do](https://linux.do) community.
