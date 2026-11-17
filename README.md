# 开工先问（requirement-check-first）

一个给 AI Agent 用的 Skill。核心规则一句话：**动手前先判断需求够不够明确——只在有「方向级不确定性」时提问，需求明确就直接干。**

## 解决什么问题

- 需求没对齐就动手，做错方向再返工。
- 为了「显得严谨」机械提问、走流程，浪费用户时间。
- 该问的不问，闷头做完才发现不是用户要的。

## 适用 / 不适用

**触发（属于任务）**：要产出文档 / 表格 / PPT / 代码 / 网页 / 报告、要改文件、要多步操作、要访问外部数据或登录态。

**不触发（直接做）**：纯知识问答、概念解释、闲聊、单句级微调（改错别字 / 调颜色 / 换措辞）、需求已完整交代。

## 安装

这是 DeepSeek Harness（DSH）的 Skill，以 `SKILL.md` 文件形式加载。

把本仓库的 `requirement-check-first` 文件夹（含 `SKILL.md`）复制到你的 skill 目录：

- 用户级（推荐）：`~/.agents/skills/`（Windows：`C:\Users\<你>\.agents\skills\`）
- 用户级（备选）：`~/.dsh/skills/`
- 项目级：项目根目录的 `.dsh/skills/` 或 `.agents/skills/`

目录名必须保持 `requirement-check-first`（与 `SKILL.md` frontmatter 里的 `name` 一致）。放好后重启或刷新会话即生效。

## 使用

放进 skill 目录后，DSH 会按 `SKILL.md` frontmatter 里的 `description` 自动判断何时触发；也可以直接点名加载这个 skill。

## 核心规则

1. **任务判定**：先判断是不是「任务」。不是任务直接做。
2. **五维自检**：产物形态 / 受众与用途 / 范围与口径 / 硬约束 / 验收标准。
3. **判定线**：五维都能复述完整、剩余不确定项都是「选错也能低成本改」的细节，才开工；存在「选错就要重做」的分叉点，必须提问。
4. **提问规范**：一次 1–4 题，每题 2–4 个选项、标推荐项并说明影响；问完即停，等回答再动手。
5. **豁免**：用户说「你看着办 / 别问了 / 赶时间」时，记下默认假设、一句话列出后直接开工。

完整规则见 `SKILL.md`。

## 目录结构

```
requirement-check-first/
├── SKILL.md   # Skill 本体（frontmatter + 规则）
├── README.md  # 本文件
└── LICENSE    # MIT
```

## License

[MIT](./LICENSE) © 2026 YNCJDXTHN
