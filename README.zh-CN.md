<p align="center">
  <img src="./assets/readme-skill-hero.png" alt="readme-skill：先验证事实，再组织文字">
</p>

# readme-skill

[English](./README.md) | [简体中文](./README.zh-CN.md)

[![GitHub repository](https://img.shields.io/badge/GitHub-ZardLi1115%2Freadme--skill-181717?style=flat-square)](https://github.com/ZardLi1115/readme-skill)

一个用于根据仓库证据和用户明确确认信息，生成准确、易读 GitHub README 的 Claude Code skill。

## ✨ 核心亮点

| 能力 | 对使用者的价值 |
|---|---|
| ⚡ 有边界的仓库发现 | 在写作前检查项目结构、元数据、文档和配置。 |
| 🔍 事实驱动的写作 | 区分已验证信息、用户确认信息、不确定信息和缺失信息。 |
| 🧩 现有 README 处理选项 | 起草前明确提供完全覆盖、选择性保留或原文扩展三种方式。 |
| 🌐 双语 README 支持 | 提供英文、简体中文和中英双语 README 布局。 |
| 🛡️ 谨慎的公开规则 | 避免发布缺乏依据的命令、链接、兼容性声明、发布信息和许可证说明。 |
| 🧪 质量检查清单 | 在写入前检查事实准确性、可执行示例、链接、徽章、图片、架构图和双语一致性。 |

## 🏗️ 架构

```text
┌──────────────────┐  request  ┌──────────────────┐
│   User request   │──────────▶│   readme-skill   │
└──────────────────┘           └──────────────────┘
                          repository facts + user choices
                                         │
                                         ▼
                               ┌──────────────────┐
                               │ Bounded discovery│
                               │ and fact ledger  │
                               └────────┬─────────┘
                                        │
                                        ▼
┌──────────────────┐  confirmed  ┌──────────────────┐
│ README.md /      │◀────────────│ Draft, checklist,│
│ README.zh-CN.md  │             │ and write gate   │
└──────────────────┘             └──────────────────┘
```

skill 只扫描支撑公开说明所需的文件，记录证据状态，询问无法验证的选择，并且只在获得明确确认后写入文件。

## 💡 使用示例

`readme-skill` 曾用于为 [Long Horizon Pi Extension](https://github.com/ZardLi1115/long-horizon-pi-extension) 编写文档；该项目是一个面向可恢复、按章节执行工作流的 Pi Coding Agent 扩展。

用户提供仓库 URL，并请求生成专业 README。发现已有 README 后，用户选择完全重写，并确认以英文 `README.md` 为主、提供简体中文版本、加入已验证徽章和新生成的本地项目视觉；用户未选择 Star History 图表。

最终生成了 `README.md`、`README.zh-CN.md`，并验证了本地资源 `assets/long-horizon-pi-extension-icon.png`。过程还发现该仓库的 Pi 运行时包声明在 `devDependencies` 中；Pi 从 Git 安装包时只安装生产依赖，因此 README 不会声称支持直接包安装，而是记录了有证据支持的本地检出路径：

```bash
git clone https://github.com/ZardLi1115/long-horizon-pi-extension.git
cd long-horizon-pi-extension
npm install

cd /absolute/path/to/your-git-project
pi --extension /absolute/path/to/long-horizon-pi-extension/index.ts
```

目标仓库的 `npm test` 通过了 126 个测试，`npm run typecheck` 通过；发布前还检查了 README 链接、图片路径、许可证路径和快速开始。这些验证结果属于 Long Horizon 示例仓库，而不是 `readme-skill` 自身运行的测试。

## 🚀 快速开始

1. 告诉任意 agent：`替我下载这个 skill：https://github.com/ZardLi1115/readme-skill`
2. 调用 `readme-skill`，让它修改指定仓库的 README 或为指定仓库新建 README，例如：`调用 readme-skill，帮我修改 <仓库> 的 README，或帮我为 <仓库> 新建 README。`

## 🔄 工作流程

该 skill 遵循有边界的文档生成流程：

1. 发现仓库事实和现有文档。
2. 如果已有 README，先询问是完全覆盖、覆盖但选择性保留已批准的信息，还是在原文基础上扩展。
3. 只读取适用的 README 指南、模板和质量检查规则。
4. 除非用户明确要求不用 emoji，否则默认按语义使用 emoji；其他无法验证的公开信息尽可能通过明确选项询问。
5. 询问是否加入基于证据的 ASCII 架构图；绝不使用 Mermaid。
6. 询问是否加入使用示例。若需要，则收集经确认的文字、图片/资源、代码或命令、预期结果、位置和语言。
7. 生成完整草稿，提供事实清单、可选架构图、可选使用示例、已验证的快速开始流程及现有 README 的处理说明。
8. 只有在目标文件和变更内容确认后，才写入 README，并针对生成后的文件执行质量检查清单。

当用户选择 OpenAI 生图服务时，该 skill 会先索取 API URL 和密钥，再通过 [`scripts/generate-image.py`](./scripts/generate-image.py) 生成并验证本地图片，同时避免公开凭据。

## 📦 仓库结构

| 路径 | 用途 |
|---|---|
| [`SKILL.md`](./SKILL.md) | Skill 定义、工作流程、Emoji 资源库、ASCII 架构图规则和文档安全规则 |
| [`scripts/generate-image.py`](./scripts/generate-image.py) | 通过 OpenAI 兼容的 Images API 生成本地图片 |
| [`references/readme-structure.md`](./references/readme-structure.md) | README 信息架构、emoji、架构图和使用示例指南 |
| [`references/quality-checklist.md`](./references/quality-checklist.md) | 写作前和写入前的质量检查 |
| [`references/badge-style.md`](./references/badge-style.md) | 徽章的证据要求和样式指南 |
| [`references/image-generation.md`](./references/image-generation.md) | README 视觉元素和图片生成指南 |
| [`templates/README.en.md`](./templates/README.en.md) | 英文 README 模板 |
| [`templates/README.zh-CN.md`](./templates/README.zh-CN.md) | 简体中文 README 模板 |
| [`templates/README.bilingual.md`](./templates/README.bilingual.md) | 双语 README 布局模板 |

## 🎯 设计原则

- **先验证事实，再组织文字：** 只记录仓库文件或用户支持的信息。
- **先提供价值，再追求完整：** 帮助读者快速理解项目，并尽快获得首次可用结果。
- **语义化视觉语言：** 默认使用内置 Emoji 资源库，按语义选择符号，并保持整体克制。
- **有证据支持的架构：** 仅用 `text` 代码块中的对齐 ASCII Art 绘制可选架构图；绝不使用 Mermaid。
- **经过确认的示例：** 仅使用用户提供或已验证的文字、资源、代码、命令和结果来添加使用示例。
- **必需的已验证快速开始：** 每份生成的 README 都保留一条通往首次可用结果的验证路径；缺少证据时应提问，而不是臆造或省略章节。
- **安全地公开内容：** 不将 API 密钥或其他机密写入 README。
- **保持双语文档一致：** 两种语言文件中的命令、路径、URL、版本号和其他技术标识保持一致。

## 📖 文档

完整的工作流程和规则请从 [`SKILL.md`](./SKILL.md) 开始阅读。补充指南和模板位于 [`references/`](./references/) 与 [`templates/`](./templates/) 目录中。

## 📄 许可证

本项目基于 [MIT 许可证](./LICENSE) 发布。
