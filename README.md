# 🛠️ lihuaqiang-agentic-armory

> 我的智能体工程装备库 —— 专为自主 Agent 打造的可复用提示词、Harness 脚本与技能模块

<p align="left">
  <a href="https://github.com/lihuaqiang/lihuaqiang-agentic-armory/blob/main/LICENSE"><img src="https://img.shields.io/badge/License-MIT-yellow.svg" alt="License: MIT"></a>
  <img src="https://img.shields.io/badge/Status-Evolving-blue" alt="Status: Evolving">
  <img src="https://img.shields.io/badge/Maintenance-Active-green" alt="Maintenance: Active">
  <img src="https://img.shields.io/badge/Agent--Ready-orange" alt="Agent Ready">
</p>

<p align="center">
  <strong><a href="#english">English</a></strong> | <strong><a href="#中文">中文</a></strong>
</p>

---

## 📛 名称由来

| 部分 | 含义 |
| :--- | :--- |
| **lihuaqiang** | 我的身份标识。确保每一件装备都承载我个人的工程哲学与使用习惯。 |
| **Agentic** | 聚焦**自主智能体（Autonomous Agents）**，而非简单对话机器人。强调 Agent 的主动性、工具调用能力和任务编排能力。 |
| **Armory** | 军械库、装备库。意味着这里的每一个文件都是经过实战打磨、反复迭代、随时可取用的"武器"。 |

> ⚔️ **"Armory"不是仓库，而是兵工厂。** 这里存放的不是半成品，而是经过真实场景验证、持续优化的工程化资产。

---

## 🎯 仓库目的

这个仓库是我在日常使用各类 AI 编程助手和智能体产品过程中，积累下来的**工程化资产集合**。

我在使用 **Claude Code**、**OpenAI Codex**、**Workbuddy** 等产品的过程中发现：
- 同一个任务（比如写博客、Code Review、生成文档），每次手动写提示词效率很低
- 好的提示词需要反复打磨，但散落在各处难以管理和复用
- 不同产品的 Skill/Agent 配置格式各异，但底层逻辑是相通的
- 缺少一套可以跨平台复用的"Harness"层（即包裹 Agent 的执行逻辑）

所以这个仓库的核心目的是：

1. **沉淀** —— 把我验证过的提示词、脚本、技能定义集中管理
2. **迭代** —— 基于真实使用体验持续优化，而不是纸上谈兵
3. **复用** —— 设计成跨平台兼容的格式，在 Claude Code、Codex、Workbuddy 等不同产品间可迁移
4. **开源** —— 接受社区反馈，让这套装备不断进化

---

## 🧩 Agent / Skill / Harness / MCP —— 我该用什么格式？

这是我反复思考的问题。结论是：**分层设计，各取所需**。

| 层级 | 形式 | 说明 | 跨平台性 |
| :--- | :--- | :--- | :--- |
| **Prompts** | 纯 Markdown 文本 | 最基础的 System Prompt，不依赖任何平台 | ✅ 完全通用 |
| **Harness** | Python / Shell 脚本 | 包裹 Agent 的执行逻辑（输入处理、调用、输出解析、重试等） | ✅ 脚本通用，需适配调用方式 |
| **Skills** | 平台特定格式（JSON/YAML + 提示词） | Claude Code Skills、Cursor Rules 等平台原生格式 | ⚠️ 平台绑定，但底层提示词可复用 |
| **MCP Servers** | 独立服务进程 | Model Context Protocol 服务器，提供工具能力 | ✅ 标准协议，理论上通用 |

**设计原则：Prompt 是核心资产，Harness 是工程化封装，Skills 和 MCP 是平台适配层。**

---

## 📂 仓库结构

```
lihuaqiang-agentic-armory/
├── prompts/                    # 核心提示词库
│   ├── blog-writer/            #   写博客专用提示词
│   │   └── system.md
│   ├── code-reviewer/          #   Code Review 提示词
│   │   └── system.md
│   └── README.md               #   提示词索引与使用说明
│
├── harness/                    # 执行层脚本（通用）
│   ├── runners/                #   Agent 调用 Runner
│   │   ├── base.py             #     抽象基类
│   │   ├── claude_code.py      #     Claude Code 适配
│   │   └── codex.py            #     Codex 适配
│   ├── utils/                  #   工具函数
│   └── README.md
│
├── skills/                     # 平台特定 Skills
│   ├── claude-code/            #   Claude Code Skills
│   │   └── blog-writer/
│   │       ├── SKILL.md
│   │       └── scripts/
│   ├── cursor/                 #   Cursor Rules
│   └── README.md
│
├── mcp_servers/                # MCP 服务器
│   └── README.md
│
├── docs/                       # 文档
│   ├── architecture.md         #   架构设计说明
│   └── contributing.md         #   贡献指南
│
├── tests/                      # 测试
│
├── .github/                    # GitHub 配置
│   └── ISSUE_TEMPLATE/
│
├── CHANGELOG.md                # 更新日志
├── CONTRIBUTING.md             # 贡献指南
├── LICENSE                     # MIT 许可证
└── README.md
```

---

## 🚀 快速开始

### 1. 克隆仓库

```bash
git clone https://github.com/lihuaqiang/lihuaqiang-agentic-armory.git
cd lihuaqiang-agentic-armory
```

### 2. 使用提示词（最简单的方式）

直接复制 `prompts/` 目录下的 `.md` 文件内容到你的 AI 工具中：

```bash
# 比如用博客写作提示词
cat prompts/blog-writer/system.md
# 复制输出内容到你的 ChatGPT / Claude / Codex 对话框
```

### 3. 配置 Claude Code Skills

```bash
# 在 Claude Code 中引用本仓库的 Skills
# 编辑 ~/.claude/settings.json，添加：
{
  "skills": ["path/to/lihuaqiang-agentic-armory/skills/claude-code"]
}
```

### 4. 运行 Harness 脚本

```bash
cd harness
pip install -r requirements.txt
python runners/claude_code.py --skill blog-writer --input "写一篇关于 Rust 所有权的文章"
```

---

## 📋 当前装备清单

| 装备 | 类型 | 状态 | 说明 |
| :--- | :--- | :--- | :--- |
| blog-writer | Prompt + Skill | 🟡 迭代中 | 技术博客写作提示词，持续优化以减少技术幻觉 |
| code-reviewer | Prompt | 🟡 迭代中 | 代码审查提示词 |

> 🟢 成熟可用 · 🟡 迭代优化中 · 🔴 实验阶段

---

## 🧠 设计理念

1. **实战驱动** —— 每一件装备都来自真实使用场景，不用就删掉
2. **最小可用** —— 不追求大而全，追求精而准
3. **跨平台复用** —— 核心逻辑与平台解耦，Prompt 是最大公约数
4. **持续迭代** —— 每次使用都是验证和优化机会，broken tools get fixed immediately
5. **开源共建** —— 欢迎 Fork、Issue、PR，让装备库在反馈中进化

---

## 🤝 参与贡献

欢迎任何形式的贡献：
- 🐛 报告 Bug 或提出改进建议 → [提交 Issue](https://github.com/lihuaqiang/lihuaqiang-agentic-armory/issues)
- 🔧 提交 Pull Request → 详见 [CONTRIBUTING.md](CONTRIBUTING.md)
- 💬 讨论使用体验或新想法 → [Discussions](https://github.com/lihuaqiang/lihuaqiang-agentic-armory/discussions)

---

## 📜 许可证

本项目采用 [MIT License](LICENSE) 开源。

---

<p align="center">
  <i>由 Lihuaqiang 用 ❤️ 和 ☕ 打造</i><br>
  <i>最后更新：2026-06-13</i>
</p>

---

<a name="english"></a>

## 🇬🇧 English Version

# 🛠️ lihuaqiang-agentic-armory

> My Agentic Engineering Arsenal — Reusable prompts, harness scripts, and skill modules for autonomous AI agents

---

## 📛 Why the Name?

| Part | Meaning |
| :--- | :--- |
| **lihuaqiang** | My identity. Every asset carries my personal engineering philosophy. |
| **Agentic** | Focused on **Autonomous Agents**, not simple chatbots. Emphasizes proactive behavior, tool usage, and task orchestration. |
| **Armory** | A place for tools forged through real-world usage, tested and ready for deployment. |

> ⚔️ **An "Armory" is not just a warehouse — it's a forge.** Every piece here has been battle-tested and iterated upon.

---

## 🎯 Purpose

This repository is a curated collection of my **engineering assets** accumulated while working with AI coding assistants and agent products like **Claude Code**, **OpenAI Codex**, and **Workbuddy**.

Core objectives:

1. **Accumulate** — Centralize battle-tested prompts, scripts, and skill definitions
2. **Iterate** — Continuously improve based on real usage, not theory
3. **Reuse** — Design for cross-platform compatibility across different agent products
4. **Open Source** — Accept community feedback to keep the armory evolving

---

## 🧩 Architecture: Prompt / Skill / Harness / MCP

| Layer | Format | Description | Cross-Platform |
| :--- | :--- | :--- | :--- |
| **Prompts** | Pure Markdown | Core System Prompts, no platform dependency | ✅ Universal |
| **Harness** | Python / Shell | Execution logic wrapping agents (input handling, invocation, output parsing, retry) | ✅ Scripts are portable |
| **Skills** | Platform-specific | Claude Code Skills, Cursor Rules, etc. | ⚠️ Platform-bound, but core prompts are reusable |
| **MCP Servers** | Standalone services | Model Context Protocol servers for tool capabilities | ✅ Standard protocol |

**Design principle: Prompts are the core asset. Harness is the engineering wrapper. Skills and MCP are the platform adaptation layer.**

---

## 📂 Repository Structure

```
lihuaqiang-agentic-armory/
├── prompts/          # Core Prompt Library
├── harness/          # Execution Scripts (Platform-agnostic)
├── skills/           # Platform-specific Skills
├── mcp_servers/      # MCP Servers
├── docs/             # Documentation
├── tests/            # Tests
├── CHANGELOG.md      # Version history
├── CONTRIBUTING.md   # Contributing Guide
├── LICENSE           # MIT License
└── README.md
```

---

## 🚀 Quick Start

### 1. Clone

```bash
git clone https://github.com/lihuaqiang/lihuaqiang-agentic-armory.git
cd lihuaqiang-agentic-armory
```

### 2. Use Prompts (Simplest)

Copy any `.md` from `prompts/` into your AI tool.

### 3. Configure Claude Code Skills

```json
// ~/.claude/settings.json
{
  "skills": ["path/to/lihuaqiang-agentic-armory/skills/claude-code"]
}
```

### 4. Run Harness Scripts

```bash
cd harness
pip install -r requirements.txt
python runners/claude_code.py --skill blog-writer --input "Write about Rust ownership"
```

---

## 📋 Current Arsenal

| Asset | Type | Status | Description |
| :--- | :--- | :--- | :--- |
| blog-writer | Prompt + Skill | 🟡 Iterating | Tech blog writing prompt, optimized to reduce technical hallucinations |
| code-reviewer | Prompt | 🟡 Iterating | Code review prompt |

---

## 🧠 Design Philosophy

1. **Battle-Tested** — Every asset comes from real usage
2. **Minimal & Effective** — Precision over breadth
3. **Cross-Platform** — Decoupled from specific products
4. **Continuous Iteration** — Every usage is a chance to improve
5. **Open & Collaborative** — Fork, Issues, PRs welcome

---

## 🤝 Contributing

- 🐛 Report bugs or suggest improvements → [Open an Issue](https://github.com/lihuaqiang/lihuaqiang-agentic-armory/issues)
- 🔧 Submit a Pull Request → See [CONTRIBUTING.md](CONTRIBUTING.md)
- 💬 Discuss experiences or ideas → [Discussions](https://github.com/lihuaqiang/lihuaqiang-agentic-armory/discussions)

---

## 📜 License

This project is licensed under the [MIT License](LICENSE).

---

<p align="center">
  <i>Built with ❤️ and ☕ by Lihuaqiang.</i><br>
  <i>Last Updated: 2026-06-13</i>
</p>
