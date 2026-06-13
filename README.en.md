# 🛠️ lihuaqiang-agentic-armory

> My Agentic Engineering Arsenal — Reusable prompts, harness scripts, and skill modules for autonomous AI agents

<p align="left">
  <a href="https://github.com/lihuaqiang/lihuaqiang-agentic-armory/blob/main/LICENSE"><img src="https://img.shields.io/badge/License-MIT-yellow.svg" alt="License: MIT"></a>
  <img src="https://img.shields.io/badge/Status-Evolving-blue" alt="Status: Evolving">
  <img src="https://img.shields.io/badge/Maintenance-Active-green" alt="Maintenance: Active">
  <img src="https://img.shields.io/badge/Agent--Ready-orange" alt="Agent Ready">
</p>

<p align="center">
  <strong>English</strong> | <a href="README.md">中文</a>
</p>

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
