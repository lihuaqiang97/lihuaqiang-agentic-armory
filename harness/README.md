# ⚙️ 执行层 (Harness)

本目录存放通用的执行脚本和工具函数，用于包裹 Agent 的调用逻辑。

## 结构

```
harness/
├── runners/    # Agent 调用 Runner（各平台适配层）
├── utils/      # 通用工具函数
└── README.md
```

## 使用方式

```bash
cd harness
pip install -r requirements.txt
python runners/claude_code.py --skill blog-writer --input "你的任务描述"
```

# 系统提示词收集
- [system_prompts_leaks](https://github.com/asgeirtj/system_prompts_leaks)
