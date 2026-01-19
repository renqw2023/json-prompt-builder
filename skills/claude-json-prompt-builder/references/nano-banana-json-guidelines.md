# Nano Banana Pro JSON Prompting Guidelines

Use this as a compact reference for JSON prompt generation and automation.

## Core Rules

- Use JSON when prompts are complex or need repeatable structure.
- Add dynamic fields that match the subject (objects, scenes, people).
- Remove irrelevant fields entirely rather than setting them to "N/A".
- Always include `constraints` with `must_keep` and `avoid`, and a `negative_prompt` list.
- If the reference image is a multi-panel collage/grid, add explicit layout fields (e.g., `composition.layout`, `composition.panel_count`) and constrain the panel count.
- For grids, include `composition.panels` to describe each panel's intent and add `constraints.avoid` for wrong grid sizes.
- Include camera/gear details only for photorealistic outputs.
- If material texture is ambiguous, force a choice:
  - Felt/knit/plush: describe fibers and stitches; avoid smooth/plastic.
  - Smooth stylized 3D: specify matte smooth surface; add negative prompts for felt/knit/plush/wool.
- For reference images, prioritize matching geometry, proportions, and materials before style or mood changes.

## Detail Extraction Checklist (use for text or image inputs)

- **Identity/shape**: silhouette, proportions, dominant geometry, unique marks.
- **Materials/surfaces**: texture, gloss, roughness, fabric weave, metal finish.
- **Color/palette**: main colors, accent colors, gradients.
- **Composition**: camera angle, framing, symmetry, subject placement.
- **Environment**: background elements, props, spatial context.
- **Text/typography**: exact wording, language, font style, placement.

## Reference Image Emphasis

- Convert key details into `constraints.must_keep` (shape, proportions, materials, text).
- Use `constraints.avoid` for common misreads (wrong materials, wrong panel count, missing text).

## System-Prompt Style Template (condensed)

You are an expert prompt engineer for Nano Banana Pro. Convert the user's input into a detailed JSON prompt. Output a single valid JSON object. Add subject-specific fields, remove irrelevant fields, and always include `constraints` and `negative_prompt`. Be precise about lighting and medium. Use camera settings only for photorealism.

## Base Schema Skeleton

```json
{
  "subject": {
    "main": ""
  },
  "background": {
    "type": "",
    "color": "",
    "texture": ""
  },
  "style": {
    "medium": "",
    "references": "",
    "palette": ""
  },
  "lighting": {
    "type": "",
    "source": "",
    "details": ""
  },
  "photography": {
    "style": "",
    "camera_gear": {
      "lens": "",
      "aperture": ""
    }
  },
  "aesthetic_fidelity": {
    "vibe": "",
    "visual_qualities": []
  },
  "constraints": {
    "must_keep": [],
    "avoid": []
  },
  "negative_prompt": []
}
```

## People-Specific Additions (use when subject is a person)

- `subject.demographics` (age, gender)
- `face.skin`, `face.eyes`, `face.mouth`, `face.details`
- `hair` (style, color, texture, accessories)
- `pose` (body_position, head_position, energy)
- `attire` (items, materials, fit, embellishments)

## Non-Human Adaptations (examples)

- **Vehicle**: `chassis`, `paint_finish`, `wheels`, `interior`.
- **Architecture**: `architecture_era`, `materials`, `facade_details`.
- **Food**: `plating_style`, `ingredients`, `garnish`.
