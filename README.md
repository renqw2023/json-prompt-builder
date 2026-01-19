[English](README.md) | [简体中文](README.zh-CN.md)

# json-prompt-builder

Generate Nano Banana Pro style JSON prompts from text or image references.

License: GPL-3.0  |  Claude Skill / Codex Skill

## Highlights

- Structured JSON output with `constraints.must_keep`, `constraints.avoid`, and `negative_prompt`
- Supports text prompts or image references (local paths or URLs)
- Adapts fields for people, objects, scenes, and other subjects
- Handles collage/grid layouts with explicit panel constraints
- Accepts Chinese or English input; JSON keys are in English

## Installation

### Claude

Use `skills/claude-json-prompt-builder` as the Claude skill folder.

- Place the skill folder in the global directory: `~/.claude/skills/`
- Or provide the repository URL to Claude Code and let it install the skill

### Codex

Copy `skills/json-prompt-builder` into your Codex skills directory:

- Windows: `C:\Users\<you>\.codex\skills\json-prompt-builder`
- macOS/Linux: `~/.codex/skills/json-prompt-builder`

## Usage

Ask the skill to turn a text description or image reference into a JSON prompt.

Example input:
- "Create a JSON prompt for a matte 3D toy robot on a clean studio background."

Output:
- A short explanation (1-3 sentences)
- A single valid JSON object with subject-specific fields and constraints

## Project Structure

```
skills/
  json-prompt-builder/
    SKILL.md
    references/
      nano-banana-json-guidelines.md
  claude-json-prompt-builder/
    SKILL.md
    references/
      nano-banana-json-guidelines.md
```

## Notes

- If an image path or URL cannot be accessed, the skill asks for a description.
- Camera/gear fields are included only for photorealistic outputs.
- This repo contains prompt instructions only; no runtime scripts are included.

## License

GPL-3.0
