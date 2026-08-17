# README Quality Checklist

Use this checklist before showing a final draft and again before any file write.

## Facts and executability

- [ ] Project name, short description, installation command, runtime requirements, API/CLI syntax, configuration keys, paths, and license terms are verified from the repository or confirmed by the user.
- [ ] Uncertain claims are explicitly marked for confirmation or omitted.
- [ ] Quick Install uses an actual supported package manager, installer, or source-build route.
- [ ] Quick Start uses real entry points, flags, imports, environment variables, and expected behavior.
- [ ] Code fences have the appropriate language label.
- [ ] README URLs, local document links, image paths, package references, and community links exist or are user-confirmed.
- [ ] API keys are represented only by environment variable names; no secret is embedded in text, code, URL, or asset.

## Badges and Star History

- [ ] Every badge has a verified source and accurately represents it.
- [ ] Static badge labels are percent-encoded and palette choices match the badge guide.
- [ ] Dynamic badges use a verified endpoint; no endpoint was guessed.
- [ ] Star History is included only after user approval and verification of a public GitHub `owner/repo`.
- [ ] The Star History section comes after Community & support and immediately before License.
- [ ] The Star History code uses the verified identifier and is omitted for private or uncertain repositories.

## Presentation and language layout

- [ ] Heading hierarchy is logical; no empty sections remain.
- [ ] Tables are short and remain understandable on narrow screens.
- [ ] Each image has meaningful alt text; no key information exists only inside an image.
- [ ] HTML is limited to GitHub-compatible structural elements; no JavaScript, CSS, or `iframe` is used.
- [ ] The README links to detailed docs rather than repeating a complete manual.
- [ ] In bilingual mode, language-switch links are reciprocal and correct.
- [ ] Commands, URLs, paths, versions, and license identifiers match across `README.md` and `README.zh-CN.md`.

## Existing README and write gate

When an existing README is present, produce an explicit list of content to **keep**, **move**, **merge**, and **remove**, with reasons tied to current repository facts.

Before writing any file, verify all of the following:

- [ ] The user explicitly asked for a write or update.
- [ ] Every target path is named.
- [ ] The user can see what is being replaced or reorganized.
- [ ] No image references point to absent assets.
- [ ] Dynamic badges use a verified endpoint.
- [ ] Any Star History chart uses a verified public owner/repo identifier.

If any checkbox fails, keep the output as an in-conversation draft and state what blocks writing.

## Exceptions

| Situation | Required response |
|---|---|
| Directory is not a Git repository or remote is unavailable | State the reduced verification scope; continue from local files and user input. |
| Conflicting manifests or configurations | Identify the conflicting files and ask which public behavior to document. |
| Absent license | Omit the license section and badge; invite the user to choose or add one. |
| No verified docs, community, or demo | Omit the corresponding section and badge instead of creating a placeholder. |
| Code-versus-README contradiction | Show the conflict, treat code/configuration as the stronger source, and ask before making an external claim. |
| Image unavailable or path unknown | Give placement guidance only; do not add an image reference. |
| Star History owner/repo unavailable or repository private | Omit the chart and explain why. |

## Completion report

Report the result in exactly these categories:

```text
Files changed:
- <path and purpose, or “None — draft shown in conversation only”>

Verified:
- <facts, commands, paths, links, badge sources, or owner/repo>

Needs confirmation:
- <unverified public information or manual checks>

Not included:
- <sections, badges, images, or charts omitted because they were unverified or declined>
```
