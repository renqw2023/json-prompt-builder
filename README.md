[中文](README.zh-CN.md)

# json-prompt-builder

Generate Nano Banana Pro style JSON prompts from text or image references.

## What's inside

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

## Installation

### Claude

Use the `skills/claude-json-prompt-builder` folder as a Claude skill.

- Place the skill folder in the global directory: `~/.claude/skills/` so Claude can discover it in any project.
- Or, provide the repository URL to Claude Code and let it install the skill for you.

### Codex

Copy the `skills/json-prompt-builder` folder into your Codex skills directory:

- Windows: `C:\Users\<you>\.codex\skills\json-prompt-builder`
- macOS/Linux: `~/.codex/skills/json-prompt-builder`

## Usage

Invoke the skill by name or ask for a JSON prompt from text or image references.

Example inputs:
- A product shot description
- A local image path
- An image URL

Output:
- Short explanation
- A single valid JSON object with constraints and negative_prompt

## References

- `skills/claude-json-prompt-builder/SKILL.md`
- `skills/claude-json-prompt-builder/references/nano-banana-json-guidelines.md`
- `skills/json-prompt-builder/SKILL.md`
- `skills/json-prompt-builder/references/nano-banana-json-guidelines.md`

## License

GPL-3.0
