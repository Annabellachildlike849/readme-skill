# README Image Guidance

Read this guide only when the user wants a visual in the README.

## Ask before proposing or generating imagery

Determine:

1. whether the user wants a logo/icon, hero banner, product screenshot, architecture diagram, or demo GIF;
2. whether approved assets already exist;
3. whether the image should contain no text, an icon plus one short line, or an icon plus project name and one short line; and
4. where it will appear in the README.

Prefer approved existing assets. Verify local paths before referencing them, and never insert a speculative image URL. Product screenshots should show an actual UI or output. Architecture diagrams require source-backed components and data flow.

Default recommendation: a concise icon plus no more than one or two short lines. Avoid dense, poster-like graphics, full feature lists, and UI mockups that claim nonexistent functionality.

| Asset type | Suitable placement |
|---|---|
| Logo / icon | Above or beside the title |
| Hero banner | Before the positioning statement |
| Product screenshot | After Quick Start or in a features section |
| Architecture diagram | Architecture or advanced use section |
| Demo GIF | After the related command or workflow |

## Concise prompt formula

Use confirmed project facts only. Keep the prompt short:

```text
Create a clean GitHub README visual for [project type].
Visual metaphor: [one core idea].
Style: [two or three adjectives]. Palette: [two or three colors].
Composition: [icon-centered or wide banner].
Text: [none, or exact short text under 12 words]. No dense UI, feature lists, paragraphs, logos of unrelated brands, or watermarks.
```

Image-model typography can be inaccurate. An icon-only image with a Markdown title is the most reliable option. If text is desired, use only confirmed wording and warn the user that they may need to replace rendered text in a design tool.

## OpenAI Images API

Use this route only when the user chooses it and has access. Do not run it automatically. Keep credentials in the user’s shell environment; never copy the key into a README or repository file.

### curl

```bash
export OPENAI_API_KEY='replace-with-your-key'

curl https://api.openai.com/v1/images/generations \
  -H "Authorization: Bearer $OPENAI_API_KEY" \
  -H 'Content-Type: application/json' \
  -d '{
    "model": "gpt-image-1",
    "prompt": "Create a clean GitHub README visual for a developer CLI. Visual metaphor: a precise compass. Style: minimal, technical, calm. Palette: midnight blue, cyan, white. Composition: wide banner. Text: none. No dense UI, feature lists, paragraphs, logos of unrelated brands, or watermarks.",
    "size": "1536x1024"
  }'
```

### Python

```python
import os
from openai import OpenAI

client = OpenAI(api_key=os.environ["OPENAI_API_KEY"])
response = client.images.generate(
    model="gpt-image-1",
    prompt=(
        "Create a clean GitHub README visual for a developer CLI. "
        "Visual metaphor: a precise compass. Style: minimal, technical, calm. "
        "Palette: midnight blue, cyan, white. Composition: wide banner. "
        "Text: none. No dense UI, feature lists, paragraphs, logos of unrelated brands, or watermarks."
    ),
    size="1536x1024",
)
print(response)
```

### Node.js

```js
import OpenAI from "openai";

const client = new OpenAI({ apiKey: process.env.OPENAI_API_KEY });
const response = await client.images.generate({
  model: "gpt-image-1",
  prompt: "Create a clean GitHub README visual for a developer CLI. Visual metaphor: a precise compass. Style: minimal, technical, calm. Palette: midnight blue, cyan, white. Composition: wide banner. Text: none. No dense UI, feature lists, paragraphs, logos of unrelated brands, or watermarks.",
  size: "1536x1024",
});
console.log(response);
```

SDK response formats and image-saving code may vary by installed SDK version. Verify those details against the SDK documentation installed in the user’s environment before adding image-save logic to a project.

## If OpenAI API access is unavailable

Offer the provider-neutral concise prompt first. Ask which image tool or provider the user already uses. Do not assume an account, API key, model, endpoint, output format, or pricing. Provide provider-specific commands only after the user names the provider or explicitly asks for an alternative.
