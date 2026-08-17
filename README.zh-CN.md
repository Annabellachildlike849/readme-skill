<p align="center">
  <img src="./assets/readme-skill-hero.png" alt="readme-skill：先验证事实，再组织文字">
</p>

# readme-skill

[English](./README.md) | [简体中文](./README.zh-CN.md)

[![GitHub repository](https://img.shields.io/badge/GitHub-ZardLi1115%2Freadme--skill-181717?style=flat-square)](https://github.com/ZardLi1115/readme-skill)

一个用于根据仓库证据和用户明确确认信息，生成准确、易读 GitHub README 的 Claude Code skill。

## 核心亮点

| 能力 | 对使用者的价值 |
|---|---|
| 有边界的仓库发现 | 在写作前检查项目结构、元数据、文档和配置。 |
| 事实驱动的写作 | 区分已验证信息、用户确认信息、不确定信息和缺失信息。 |
| 现有 README 处理选项 | 起草前明确提供完全覆盖、选择性保留或原文扩展三种方式。 |
| 双语 README 支持 | 提供英文、简体中文和中英双语 README 布局。 |
| 谨慎的公开规则 | 避免发布缺乏依据的命令、链接、兼容性声明、发布信息和许可证说明。 |
| 必需的已验证快速开始 | 确保每份生成的 README 都有一条基于证据、通往首次有效结果的简短路径。 |
| 质量检查清单 | 在写入前检查事实准确性、可执行示例、链接、徽章、图片和双语一致性。 |

## 快速开始

在 Claude Code 中启用 `readme-skill` 后，可以向它请求为当前仓库生成 README 草稿：

```text
为这个仓库生成中英双语 README 草稿。所有公开说明都必须基于仓库证据。在我确认目标路径和变更内容前，不要写入文件。
```

skill 会在对话中返回草稿和事实清单。只有在获得明确确认后，才会写入 `README.md` 和 `README.zh-CN.md`。

## 工作流程

该 skill 遵循有边界的文档生成流程：

1. 发现仓库事实和现有文档。
2. 如果已有 README，先询问是完全覆盖、覆盖但选择性保留已批准的信息，还是在原文基础上扩展。
3. 只读取适用的 README 指南、模板和质量检查规则。
4. 对语言布局及其他无法验证的公开信息，尽可能提供明确选项供用户选择。
5. 生成完整草稿，提供事实清单、已验证的快速开始流程及现有 README 的处理说明。
6. 只有在目标文件和变更内容确认后，才写入 README。
7. 针对生成后的文件执行质量检查清单。

当用户选择 OpenAI 生图服务时，该 skill 会先索取 API URL 和密钥，再通过 [`scripts/generate-image.py`](./scripts/generate-image.py) 生成并验证本地图片，同时避免公开凭据。

## 仓库结构

| 路径 | 用途 |
|---|---|
| [`SKILL.md`](./SKILL.md) | Skill 定义、工作流程和文档规则 |
| [`scripts/generate-image.py`](./scripts/generate-image.py) | 通过 OpenAI 兼容的 Images API 生成本地图片 |
| [`references/readme-structure.md`](./references/readme-structure.md) | README 信息架构和章节指南 |
| [`references/quality-checklist.md`](./references/quality-checklist.md) | 写作前和写入前的质量检查 |
| [`references/badge-style.md`](./references/badge-style.md) | 徽章的证据要求和样式指南 |
| [`references/image-generation.md`](./references/image-generation.md) | README 视觉元素和图片生成指南 |
| [`templates/README.en.md`](./templates/README.en.md) | 英文 README 模板 |
| [`templates/README.zh-CN.md`](./templates/README.zh-CN.md) | 简体中文 README 模板 |
| [`templates/README.bilingual.md`](./templates/README.bilingual.md) | 双语 README 布局模板 |

## 设计原则

- **先验证事实，再组织文字：** 只记录仓库文件或用户支持的信息。
- **先提供价值，再追求完整：** 帮助读者快速理解项目，并尽快获得首次可用结果。
- **必需的已验证快速开始：** 每份生成的 README 都保留一条通往首次可用结果的验证路径；缺少证据时应提问，而不是臆造或省略章节。
- **明确处理不确定性：** 无法验证的信息应省略或请求确认。
- **安全地公开内容：** 不将 API 密钥或其他机密写入 README。
- **保持双语文档一致：** 两种语言文件中的命令、路径、URL、版本号和其他技术标识保持一致。

## 文档

完整的工作流程和规则请从 [`SKILL.md`](./SKILL.md) 开始阅读。补充指南和模板位于 [`references/`](./references/) 与 [`templates/`](./templates/) 目录中。

## 许可证

本项目基于 [MIT 许可证](./LICENSE) 发布。
