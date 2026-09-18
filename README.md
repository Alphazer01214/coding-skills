# coding-skills

**把真实的工程失败模式，收成 agent 能反复执行的 skill。**

写代码的模型不缺「聪明」，缺的是**边界、反馈和对齐**：需求说不清就瞎写、改一处烂一片、文档骗人、bug 只能靠猜。本仓库是一组小而可组合的 agent skills，针对这些具体问题，而不是再包一层厚重流程。

| 真实问题 | Skill | 管什么 |
|----------|-------|--------|
| 想法还是一团雾，就开写 | [`to-project`](skills/engineering/to-project/SKILL.md) | 多轮对齐 → `PROJECT.md` 项目框架 |
| Agent 越界：乱提交、乱改路径 | [`to-constraints`](skills/engineering/to-constraints/SKILL.md) | 从仓库证据提炼 → `CONSTRAINT.md` |
| 计划与现实脱节 | [`to-plan`](skills/engineering/to-plan/SKILL.md) | 执行层活文档 `PLAN.md` |
| 改个功能变成屎山 | [`change`](skills/engineering/change/SKILL.md) | 边界→seam→切片→**Structure∥Spec** 双轴评审 |
| 排障靠猜，越改越花 | [`debug`](skills/engineering/debug/SKILL.md) | 现象引导→**red loop**→对齐 fix intent 再动手 |
| 陌生仓库讲不清、图画不对 | [`explain-project`](skills/engineering/explain-project/SKILL.md) | 讲解 + Mermaid 依赖图（可到函数/结构体） |
| 不知道该用哪个 | [`ask`](skills/engineering/ask/SKILL.md) | Router：按场景选型 |

## 设计原则

1. **失败模式驱动**：每个 skill 对应一种可观察的翻车方式，不为「流程完整」而存在。
2. **门禁 > 鼓励**：未对齐范围、没有 red 回路、结构评审不过 → 不前进。
3. **代码第一，文档为辅**：既有项目上，入口/调用/CI/锁文件是第一依据；文档冲突时以代码为准。
4. **User vs Model 调用**：重编排仅用户点名；排障类 `debug` 可在报障时进入。
5. **小文件 + progressive disclosure**：主 `SKILL.md` 保持短；模板与检查清单旁挂，指针命中再读。
6. **可改写**：Hack 它们，改成你自己的工程习惯。

## 30 秒上手

在项目里安装（目录即 skill ID）：

```text
# 项目级（推荐）
复制/链接 skills/engineering/<id>/  →  <你的项目>/.mimocode/skills/<id>/

# 或全局
→  ~/.config/mimocode/skills/<id>/
```

新会话生效。不确定用哪个：

```text
/ask
```

新项目建议顺序：

```text
/to-project  →  /to-constraints  →  /to-plan
```

之后：改功能 `/change`，排错 `/debug`，读仓库 `/explain-project`。

## 仓库结构

```text
coding-skills/
├── AGENTS.md                 # skill 写法与证据优先级等不变量
├── skills/
│   ├── README.md             # 清单
│   └── engineering/
│       ├── ask/
│       ├── to-project/
│       ├── to-constraints/
│       ├── to-plan/
│       ├── change/
│       ├── debug/
│       └── explain-project/
└── README.md
```

## 哲学（一句话版）

> 不是替模型包办流程，而是给模型**可检查的门**，给人**可打断的决策点**。

对标问题来自日常协作：对齐失败、无反馈回路、改动熵增、文档与代码漂移。Skill 不能消灭屎山，但能**抬高制造屎山的成本**。

## License

MIT
