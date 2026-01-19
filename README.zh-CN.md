[English](README.md)

# json-prompt-builder

根据文本或图片参考，生成 Nano Banana Pro 风格的 JSON 提示词。

## 包含内容

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

## 安装

### Claude

使用 `skills/claude-json-prompt-builder` 作为 Claude 技能目录。

- 放置到全局目录：将 Skill 文件夹移动到 `~/.claude/skills/`，这样 Claude 在任何项目中都能发现它
- 或直接将仓库链接提交给 Claude Code，让它自动安装

### Codex

将 `skills/json-prompt-builder` 文件夹复制到 Codex 的技能目录：

- Windows: `C:\Users\<you>\.codex\skills\json-prompt-builder`
- macOS/Linux: `~/.codex/skills/json-prompt-builder`

## 使用

直接按技能名称调用，或提交文本/图片参考以生成 JSON 提示词。

示例输入：
- 商品图描述
- 本地图片路径
- 图片 URL

输出包含：
- 简短说明
- 单个有效的 JSON 对象（含 constraints 和 negative_prompt）

## 参考

- `skills/claude-json-prompt-builder/SKILL.md`
- `skills/claude-json-prompt-builder/references/nano-banana-json-guidelines.md`
- `skills/json-prompt-builder/SKILL.md`
- `skills/json-prompt-builder/references/nano-banana-json-guidelines.md`

## 许可证

GPL-3.0
