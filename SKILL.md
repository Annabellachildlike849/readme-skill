---
name: readme-skill
description: Draft, improve, restructure, translate, or audit fact-based GitHub README files. Use when the user wants a README for an open-source repository, bilingual README documentation, badges, README visuals, Star History charts, or a safe README rewrite.
---

# README Skill

Create an accurate, readable GitHub README by grounding every external claim in repository evidence or explicit user confirmation. Use a concise, product-oriented information flow: establish value first, provide a fast path to use, then route readers to deeper documentation.

## Non-negotiable rules

- **Drafts are shown in the conversation by default; do not create a draft file automatically.**
- **Do not create or modify `README.md`, `README.zh-CN.md`, or any other README until the user explicitly asks to write or update it.**
- If the user wants a saved draft, use the exact target path they provide; otherwise ask for one. Do not invent a draft filename.
- Never invent commands, APIs, links, badges, performance claims, compatibility promises, release data, community locations, license terms, or repository ownership.
- Never expose API keys in README content, commands committed to a repository, source files, or image URLs. Examples may reference environment variables only.
- Every README draft must include a **Quick Start** section that shows the shortest verified path from availability or installation to a useful result. If that path cannot be verified from repository evidence or user confirmation, ask for the missing first-use details; do not invent, leave empty, or omit the section.
- When the first discovery scan finds an existing README, stop and ask the user to choose one of these handling modes before drafting: **1) Replace completely** — ignore all existing README information; **2) Replace with selected existing information** — rewrite the README while retaining only user-approved accurate content; **3) Extend existing README** — preserve the existing README and add or improve content in place. Do not infer the mode from the original request.
- Prefer questions with multiple explicit options. Use a selectable list whenever the decision can be reasonably anticipated; offer a free-form “Other” choice only when the available options cannot cover the user’s intent.
- Keep a clear separation between **Verified from repository**, **Confirmed by user**, **Uncertain**, and **Missing** information.
- Do not copy another repository's wording, project-specific commands, branding, or content. Use only general information architecture and writing principles.

## Workflow

### 1. Discover repository facts first

Perform a bounded scan. Do not read the entire codebase without a README-specific reason.

1. Determine whether the directory is a Git repository; inspect the root file list and, when available, the configured remote URL.
2. Read existing README variants, `LICENSE*`, contribution and security files, plus the docs index.
3. Read only manifests that are present, such as `package.json`, `pyproject.toml`, `Cargo.toml`, `go.mod`, `pom.xml`, or language-equivalent metadata.
4. Inspect CI, release/publishing, deployment configuration, examples, and public entry points only when needed to verify installation, first use, platform support, or documentation links.
5. If any README variant exists, ask the user to choose its handling mode before drafting:
   - **1) Replace completely:** write a new README without using any information from the existing README.
   - **2) Replace with selected existing information:** write a new README, retaining only accurate existing content that the user approves.
   - **3) Extend existing README:** preserve the existing README structure and accurate content, then add or improve content in place.
6. Build a fact ledger before drafting:

| Status | Meaning |
|---|---|
| Verified from repository | Directly supported by a local file, manifest, CI configuration, or configured remote. |
| Confirmed by user | Explicitly supplied or approved by the user. |
| Uncertain | Plausible but not safe to state publicly without confirmation. |
| Missing | Needed for a desired section but not discoverable. |

If no remote repository can be verified, say so. Do not assume an owner, repository URL, public demo, release page, community, or hosting provider.

### 2. Load only applicable guidance

- Before selecting sections or composing prose, read [README structure guidance](references/readme-structure.md).
- When badges are requested or evaluated, read [badge guidance](references/badge-style.md).
- When images are requested, read [image guidance](references/image-generation.md).
- Before presenting a final draft and again before writing files, read [quality checklist](references/quality-checklist.md).
- After project type and language layout are known, read only the relevant template(s) in `templates/`.

### 3. Ask only for decisions that evidence cannot answer

Ask **one question at a time**. Present the decision as a list of explicit options whenever practical; include a free-form “Other” option only when necessary. Do not repeat information already verified or answered.

1. If an existing README was found during discovery, ask the user to choose the handling mode described above before asking later content preferences.
2. Ask for the language layout: English, English plus Simplified Chinese, or Chinese.
   - For bilingual output, `README.md` is the English primary GitHub landing page and `README.zh-CN.md` is the Chinese version.
   - For Chinese-only output, explain that GitHub displays root `README.md` by default and ask whether Chinese should be the primary page.
3. Ask whether the user wants Shields.io badge recommendations.
   - Offer explicit choices such as **include verified recommendations**, **omit badges**, or **Other**.
   - If yes, recommend only badges whose claims and destinations are verifiable, then let the user approve, remove, or add items.
4. Ask whether imagery is wanted.
   - Offer explicit choices such as **no image**, **use an existing asset**, or **generate a new image**.
   - If yes, ask whether existing assets are available.
   - If no assets are available, ask whether the visual should be icon only, icon plus one short line, or icon plus project name and one short line.
   - If the user chooses an OpenAI image service, ask for the API URL and API key (or the names of environment variables that already contain them) before generating anything. Do not guess an endpoint, model, response format, or output location.
   - Use [`scripts/generate-image.py`](./scripts/generate-image.py) for the generation request. Pass credentials through environment variables or process arguments only; never write them to the repository, README, prompt, image URL, or command committed to Git.
   - Verify the generated local asset before adding its path to a README. If generation fails, show the provider-neutral prompt and report the failure rather than inventing an image reference.
5. Ask whether to add a Star History chart.
   - Offer **include it**, **omit it**, or **Other**.
   - Include it only after user confirmation **and** only when a public GitHub `owner/repo` identifier can be verified from the remote URL or supplied by the user.
   - Place it after **Community & support** and immediately before **License**.
   - State that it embeds a third-party dynamic SVG for a public GitHub repository; omit it if the repository is private, the owner/repo is uncertain, or the user declines.
6. Ask only for remaining public information that cannot be verified: target audience, key emphasis, documentation site, demo, community, contribution route, FAQ, roadmap, citation, or security policy.

### 4. Compose the draft

Use the relevant structure and template, then remove every inapplicable section **except Quick Start**. A Quick Start must remain in every draft and use the shortest verified first-use path; if no such path exists, ask the user for it before presenting a final draft. Prefer short, evidence-led prose and a useful first-run experience over exhaustive feature lists.

Before any file write, present:

1. A concise structural recommendation.
2. Complete Markdown draft(s) for each selected language file.
3. The fact ledger and list of user-confirmed details.
4. Proposed badges and each badge's data source.
5. Image placement and generation recommendations, when requested.
6. Star History placement and the verified `owner/repo`, when requested.
7. If a README already exists, an explicit **keep / move / merge / remove** summary.

### 5. Write only after explicit confirmation

A request to draft, improve, review, or show a README is **not** permission to write files. Write only after the user explicitly asks to write, update, replace, or save to named target paths.

Immediately before writing, state every target file and what will change:

- English: `README.md`.
- Bilingual: `README.md` and `README.zh-CN.md`.
- Chinese: use the user-confirmed primary path.
- Saved draft: only the user-specified path.

For existing files, retain useful, still-accurate content where possible. Do not silently discard content; explain material moves, merges, or removals. After writing, run the quality checklist against the actual files.

## Final report

Use this compact outcome format:

```text
Files changed:
- <path and purpose, or “None — draft shown in conversation only”>

Verified:
- <facts, commands, paths, links, or badge sources>

Needs confirmation:
- <unverified public information or manual checks>

Not included:
- <sections, badges, images, or charts omitted because they could not be verified or were declined>
```
