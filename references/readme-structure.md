# README Structure and Writing Guide

Use this guide before choosing README sections or writing prose. It defines a flexible reading flow, not a mandatory checklist. Delete every section that is unsupported by repository facts or user confirmation.

## Reading flow

Use this order when the corresponding information genuinely exists:

```text
optional visual
→ project name and one-sentence positioning
→ language links and verified badges
→ concise value proposition
→ 3–6 benefit-led highlights
→ Quick Install
→ Quick Start
→ commands or API example
→ configuration, integrations, or architecture when applicable
→ task-organized documentation links
→ contributing when supported
→ community when verified
→ optional Star History chart when confirmed and owner/repo is verified
→ license when present
```

Readers should understand the project before being asked to configure it. They should be able to reach a first useful result before being sent to advanced documentation.

## Section rules

### Positioning and value

A one-sentence positioning statement says:

1. what the project is;
2. who it serves or what situation it addresses; and
3. one factual differentiator.

Avoid unverified superlatives such as “best,” “fastest,” “production-ready,” or “industry-leading.” Prefer concrete language over slogans.

### Highlights table

Use a table only when it makes comparison easier. Keep it to 3–6 rows. Each row leads with a user outcome and follows with a verified technical basis or relevant use case.

```markdown
| Highlight | Why it matters |
|---|---|
| <Verified capability> | <Reader benefit grounded in evidence> |
```

Do not make a long feature inventory masquerade as highlights.

### Quick Install

Provide the lowest-friction **verified** installation route. Use a copyable command and state prerequisites, supported platform constraints, or required runtime immediately after it. Do not publish a package-manager command merely because the project uses a language commonly distributed that way.

### Quick Start

Show the shortest verified path from installation to a useful result. Keep code/commands small, label fences correctly, and explain the expected result without inventing output. Link to the full guide rather than embedding every configuration option.

### Commands, APIs, and deployment

Choose content based on the project type:

| Project type | Include | Exclude unless verified |
|---|---|---|
| CLI or agent tool | Command table or slash-command table with real command syntax | SDK/API snippets not supplied by the repository |
| Library or SDK | Minimal import and call example based on public API | CLI command section |
| Web service | Verified local run path or documented deployment route | Deployment/support claims without documentation |
| General application | Supported installation or launch path | Architecture diagrams without source facts |

Never force every project into every category.

### Documentation navigation

Use a task-organized table, not a raw list of folders:

```markdown
| Topic | What it covers | Link |
|---|---|---|
| <Reader task> | <Short, factual description> | [Open documentation](./docs/<verified-path>.md) |
```

Order items by the likely reader journey: start, use, configure, integrate, contribute, then reference. Link to detailed docs instead of attempting to duplicate a full manual.

### Community, Star History, and license

Include community only when a functioning public channel is verified or confirmed. If the user confirms a Star History chart and an `owner/repo` identifier is verified, place this section after community and before license:

```markdown
## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=OWNER%2FREPOSITORY&type=Date)](https://star-history.com/#OWNER/REPOSITORY&Date)
```

Replace `OWNER/REPOSITORY` with the verified public identifier. Explain only when relevant that the chart is a third-party dynamic SVG. Do not include the chart for a private repository or an uncertain identifier.

Keep the license ending concise: name the actual license only when a license file or user confirmation supports it, and link to that real file.

## Bilingual layout

For bilingual projects, English is the primary GitHub landing page:

```text
README.md        English primary GitHub landing page
README.zh-CN.md  Simplified Chinese technical rewrite
```

Put a reciprocal language switch near the top of both files:

```markdown
[English](./README.md) | [简体中文](./README.zh-CN.md)
```

The Chinese version is natural technical writing, not sentence-by-sentence translation. However, commands, code blocks, environment variable names, URLs, file paths, version numbers, and license identifiers must remain factually identical across language versions.

## GitHub-compatible layout

Markdown is the default. Minimal HTML is permitted only when it improves the header and remains readable without special rendering:

```html
<p align="center">
  <img src="./assets/<verified-image>.png" alt="<meaningful description>">
</p>

<h1 align="center">Project name</h1>
```

Near the header, limited use of centered `<p>`, `<img>`, `<a>`, and `<h1>` is acceptable. Do not use JavaScript, embedded CSS, `iframe`, scripted widgets, or visual-only essential information. Every image needs meaningful alt text, and core explanations must exist in text.
