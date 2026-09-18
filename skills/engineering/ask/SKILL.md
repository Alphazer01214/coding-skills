---
name: ask
description: 不知道该用哪个 skill 时问这里：按场景路由到 to-project / to-constraints / to-plan / change / explain-project / debug。
disable-model-invocation: true
---

# Ask

只**选型**，不执行工程步骤。读完本图后，由用户运行选中的 skill。

涉及**既有项目**的 skill（`change` / `debug` / `explain-project` / `to-plan` / `to-constraints`）：**代码第一，文档为辅**（AGENTS.md #7）。

## 选型

| 你的处境 | 运行 |
|----------|------|
| 想法还抽象，要做成项目 | `/to-project` → 产出 `PROJECT.md` |
| 项目要立 agent 边界 / agent 总越界 | `/to-constraints` → `CONSTRAINT.md` |
| 要阶段任务、进度、下一步 | `/to-plan` → `PLAN.md` |
| 要改/增强**已有功能** | `/change` |
| 要讲解仓库 / 画依赖图（到结构体/函数） | `/explain-project` |
| 东西坏了、不对、变慢 | `/debug`（模型也会在报障时进入） |

## 主流程（新项目）

```
/to-project → /to-constraints → /to-plan
                （之后）改功能 /change；排错 /debug；看地图 /explain-project
```

## 分界（易混）

- **做什么项目** vs **agent 能怎么动**：`to-project` vs `to-constraints`
- **计划与进展** vs **单次功能修改**：`to-plan` vs `change`
- **讲解/画图** vs **改代码**：`explain-project` 不改码；改码走 `change`
- **坏了** vs **新功能**：`debug` vs `change`
- 文档已齐、只差实现：不要空跑 `to-project`；任务进 `PLAN.md` 后用 `change` 或实现流程

## 规则

- Router 不改文件、不跑分析。选好后：用户输入 `/name`。
- 新增 user-invoked skill 时同步本表（见 AGENTS.md 不变量）。
