# 🧩 技能定义 (Skills)

本目录存放抽象的技能定义，与具体平台无关。每个技能包含提示词、脚本和元数据。

## 结构

```
skills/
├── blog-writer/       #   博客写作技能
│   ├── SKILL.md       #     技能描述与元数据
│   └── scripts/       #     配套脚本
└── README.md
```

## 使用方式

各平台适配器（见 `harness/runners/`）会读取本目录的技能定义，转换为目标平台所需格式。

# skill 收集

- [ui-ux-pro-max-skill](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill)
  - https://www.uupm.cc/demo/educational-platform
    - 这种风格颜色再简单一点就好了，黑白加上这种拟态的按钮，感觉效果会很好，后续自己改造一下这个skill的这种风格。
- [shadcn-ui](https://github.com/shadcn-ui/ui)
  - 简约的黑白风格，很不错。
- [taste-skill](https://github.com/Leonxlnx/taste-skill)
  - 听说好用，但是还没实际试用过效果。
