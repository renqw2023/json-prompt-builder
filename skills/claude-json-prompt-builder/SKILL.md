---
name: claude-json-prompt-builder
description: Generate Nano Banana Pro style JSON prompts from text or image references. Use when a user provides a prompt or image and needs a structured JSON prompt with constraints, negative_prompt, and a short explanation.
---

# Claude JSON Prompt Builder

## Overview

Turn user text or image references into a detailed, valid JSON prompt for Nano Banana Pro. Always produce a short explanation plus the final JSON.

## Workflow Decision Tree

### 1) Identify input type

- **Local image path**: If accessible, analyze the image. If not accessible, ask the user to upload or describe the image.
- **Image URL**: If accessible, analyze the image. If not accessible, ask for a description.
- **Text prompt**: Use it directly.

### 2) Extract critical details (especially from reference images)

- Capture **identity details** first: silhouette, proportions, dominant shapes, and any unique marks.
- Record **materials and surface**: texture, glossiness/roughness, fabric weave, metal finish, plastic vs matte.
- Record **color and palette**: primary/secondary colors, gradients, and accent colors.
- Record **composition**: camera angle, framing, subject placement, symmetry/asymmetry, depth of field.
- Record **environmental cues**: background elements, props, signage, and spatial context.
- Record **text/typography**: exact wording, language, font style, and placement if visible.

### 3) Classify the subject

- **People**: Use the people schema (face, skin, hair, pose, attire).
- **Non-humans/objects/scenes**: Create a subject-specific structure (e.g., vehicle parts, architecture, food plating). Remove irrelevant fields entirely.

### 4) Build the JSON

- Add dynamic fields that capture subject-specific details.
- Always include `constraints.must_keep`, `constraints.avoid`, and `negative_prompt`.
- Include `lighting`, `background`, `style`/`aesthetic_fidelity` as needed.
- Include camera/gear only for photorealistic outputs.
- Preserve precise facial features and structure when an image reference exists; add explicit must_keep constraints.
- Keep sign text or typography in the original language when present in the input.
- When the reference image is a collage/grid, explicitly encode the layout and the number of panels (e.g., `composition.layout: "3x3 grid collage"` and `composition.panel_count: 9`), and add a must_keep constraint to match the panel count.
- For collages/grids, define per-panel intent with a `composition.panels` list (e.g., overview, close-up texture, multi-pack layout). Also add `constraints.avoid` entries for common mismatches like "2x2 grid", "8 panels", or "single image".
- Disambiguate material style explicitly:
  - If the reference shows fabric/felt/knit texture, include it in `style.materials` and avoid smooth/plastic.
  - If the reference is smooth stylized 3D, set `style.materials` to "smooth matte surface" and add negative prompts for felt/knit/plush/wool.
- For reference images, add constraints that lock **shape, proportions, material, and key text** before style tweaks.

### 5) Language and clarity

- Accept English or Chinese input.
- Use English keys. Values can be English; preserve proper nouns or on-image text in the original language.

### 6) Output format (always)

1. Short explanation (1-3 sentences) of the subject/style/lighting choices and how constraints were derived.
2. A single valid JSON object only (no trailing comments).

## Prompting Rules (load references when needed)

- Use the reference file for the baseline schema and system-prompt style rules: `references/nano-banana-json-guidelines.md`.
- If the user asks for variations, keep the existing JSON structure and modify only the requested attributes.
- When the user provides a reference image, prioritize matching visual geometry and materials over creative embellishments.

## Quality Checklist

- JSON is valid and minimal (no irrelevant keys).
- Constraints reflect critical identity details (face/pose/clothing/background/signage).
- Negative prompt removes common failures for the scene.
- Lighting/style/medium are explicit.
