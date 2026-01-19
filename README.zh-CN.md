[English](README.md) | [简体中文](README.zh-CN.md)

# json-prompt-builder

根据文本或图片参考生成 Nano Banana Pro 风格的 JSON 提示词。

许可证：GPL-3.0  |  Claude 技能 / Codex 技能

## 亮点

- 结构化 JSON 输出，包含 `constraints.must_keep`、`constraints.avoid` 和 `negative_prompt`
- 支持文本提示词或图片参考（本地路径或 URL）
- 按人物、物体、场景等主题自适应字段
- 支持拼图/网格布局，明确面板数量与约束
- 支持中文或英文输入，JSON 键使用英文

## 安装

### Claude

使用 `skills/claude-json-prompt-builder` 作为 Claude 技能目录。

- 放置到全局目录：`~/.claude/skills/`
- 或将仓库链接交给 Claude Code 自动安装

### Codex

将 `skills/json-prompt-builder` 复制到 Codex 的技能目录：

- Windows: `C:\Users\<you>\.codex\skills\json-prompt-builder`
- macOS/Linux: `~/.codex/skills/json-prompt-builder`

## 使用

让技能把文本描述或图片参考转换为 JSON 提示词。

示例输入：
- “为一个磨砂 3D 玩具机器人生成 JSON 提示词，背景是干净的棚拍。”

输出包含：
- 简短说明（1-3 句）
- 单个有效的 JSON 对象（含主题字段与约束）

## 项目结构

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

## 备注

- 如果无法访问图片路径或 URL，会提示用户补充描述。
- 仅在写实摄影场景下包含相机/镜头字段。
- 本仓库仅包含提示词规则，没有运行脚本。

## 许可证

GPL-3.0
