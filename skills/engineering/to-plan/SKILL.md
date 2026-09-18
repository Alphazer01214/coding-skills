---
name: to-plan
description: 创建或对齐项目执行层活文档 PLAN.md：阶段、可验收任务、进展、阻塞与下一步。
disable-model-invocation: true
---

# To Plan

维护 **`PLAN.md`**（怎么走 / 到哪了）。**不**重写 `PROJECT.md`（引用即可）；变更须让用户看清偏差与 Next。

**何时**：落阶段任务；刷新进展；计划与现实偏离；用户问「到哪了」。

**前置**：可写目录；已有 `PROJECT/CONSTRAINT/PLAN` 则先读。

## Phase 0 — Explore

来源：`PROJECT.md` 目标（无则用对话目标）· `CONSTRAINT.md` 边界 · git/任务/对话中的**已发生事实**。**第一依据是代码与 git 实况**（分支、提交、测试是否真绿）；`PROJECT/PLAN` 正文作辅助，冲突以代码/事实为准并记入偏差（AGENTS.md #7）。

**完成**：3–6 行「目标、约束、已发生、不确定」。不确定≠已完成。

## Phase 1 — Align

| 状态 | 做法 |
|------|------|
| 无 PLAN | 阶段+任务草案，确认粒度顺序 |
| 有 PLAN | 刷新事实 → 指出偏差 → 确认是否修订 |
| 仅同步 | 只改勾选/阻塞/Next |

原则：任务可验收；一片一可独立完成切片；取舍由用户拍板。

**完成**：用户确认阶段/任务/优先级（或确认进展与阻塞）。  
**门禁**：覆盖已有 PLAN 必须确认。

## Phase 2 — Write

路径：`<项目根>/PLAN.md`。模板：[PLAN-TEMPLATE.md](PLAN-TEMPLATE.md)。

规则：文首链到 PROJECT；Current status 3–5 行；任务 `[ ]/[x]/[!]` + 验收信号；Next≤3；Log 追加一行事实；作废任务进「已废弃」。

**完成**：能回答「到哪、卡哪、下一步」；无 TBD。

## Phase 3 — Confirm

路径 + 阶段 + 完成/剩余/阻塞 + Next；标出可能与预期不一致处；改后落盘。

**完成**：用户确认快照。

## 边界

不写码；不改 PROJECT/CONSTRAINT 正文（过时则提醒重跑对应 skill）。实现后同步进展由用户跑 `/to-plan`。
