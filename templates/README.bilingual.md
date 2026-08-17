# Bilingual README Layout

Use two files for a bilingual repository rather than duplicating every section in one long document:

```text
README.md        English primary GitHub landing page
README.zh-CN.md  Simplified Chinese technical rewrite
```

Put this near the top of both files:

```markdown
[English](./README.md) | [简体中文](./README.zh-CN.md)
```

## Parity rules

- Write the English README first so the GitHub landing page is complete on its own.
- Rewrite the Chinese version naturally; do not translate sentence by sentence when that harms clarity.
- Keep commands, code blocks, environment variables, URLs, paths, version numbers, badge destinations, Star History owner/repo identifiers, and license identifiers factually identical.
- Keep section order aligned where possible, but remove sections absent from both files rather than adding empty headings.
- Verify both language-switch links after files are written.
- Do not create either file until the user explicitly asks to write or update the README.
