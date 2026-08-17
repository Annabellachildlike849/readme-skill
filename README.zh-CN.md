# readme-skill

[English](./README.md) | [简体中文](./README.zh-CN.md)

[![GitHub repository](https://img.shields.io/badge/GitHub-ZardLi1115%2Freadme--skill-181717?style=flat-square)](https://github.com/ZardLi1115/readme-skill)

一个用于撰写、改进、重构、翻译和审查事实驱动型 GitHub README 的 Claude Code skill。

## 功能

`readme-skill` 通过仓库证据或用户明确确认的信息，帮助生成清晰易读的 GitHub README。

它主要用于：

- 在写作前检查仓库文件、元数据、文档和配置；
- 区分已验证信息、用户确认信息、不确定信息和缺失信息；
- 围绕项目价值、安装、首次使用和深入文档组织 README 内容；
- 支持英文、简体中文和中英双语 README 布局；
- 以谨慎方式评估徽章、图片和 Star History 图表；
- 避免发布缺乏依据的命令、链接、兼容性声明、发布信息和许可证说明。

## 工作流程

该 skill 遵循有边界的文档生成流程：

1. 发现仓库事实和现有文档。
2. 只读取适用的 README 结构、徽章、图片、模板和质量检查指南。
3. 就语言布局以及仓库无法验证的可选公开信息询问用户。
4. 生成完整草稿，同时提供事实清单，并明确说明现有 README 的处理方式。
5. 只有在用户明确确认目标文件和变更内容后，才写入 README 文件。
6. 针对生成后的文件执行质量检查清单。

## 仓库结构

| 路径 | 用途 |
|---|---|
| [`SKILL.md`](./SKILL.md) | Skill 定义、工作流程和文档规则 |
| [`references/readme-structure.md`](./references/readme-structure.md) | README 信息架构和章节指南 |
| [`references/quality-checklist.md`](./references/quality-checklist.md) | 草稿展示前和写入前的质量检查 |
| [`references/badge-style.md`](./references/badge-style.md) | 徽章的证据要求和样式指南 |
| [`references/image-generation.md`](./references/image-generation.md) | README 视觉元素和图片生成指南 |
| [`templates/README.en.md`](./templates/README.en.md) | 英文 README 模板 |
| [`templates/README.zh-CN.md`](./templates/README.zh-CN.md) | 简体中文 README 模板 |
| [`templates/README.bilingual.md`](./templates/README.bilingual.md) | 双语 README 布局模板 |

## 设计原则

- **先验证事实，再组织文字：** 只记录仓库文件或用户支持的信息。
- **先提供价值，再追求完整：** 让读者快速理解项目，并尽快获得首次可用结果。
- **明确处理不确定性：** 无法验证的信息应省略或请求确认。
- **安全地公开内容：** 不将 API 密钥或其他机密写入 README。
- **保持双语文档一致：** 两种语言文件中的命令、路径、URL、版本号和其他技术标识保持一致。

## 文档

完整的工作流程和规则请从 [`SKILL.md`](./SKILL.md) 开始阅读。补充指南和模板位于 [`references/`](./references/) 与 [`templates/`](./templates/) 目录中。

## 许可证

仓库中未发现许可证文件。
