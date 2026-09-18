---
name: to-constraints
description: 生成或修订项目的 agent 行为约束文档（CONSTRAINT.md），经确认后落盘。
disable-model-invocation: true
---

# To Constraints

从**仓库证据**提炼项目 agent 边界 → 对齐高代价决策 → **`CONSTRAINT.md`**（非通用须知、不改代码、不装 hooks）。

**何时**：新项目立规矩；agent 越界；规则陈旧。已有有效文件时走**修订**。

**前置**：可写项目目录；用户能定「禁止/必须/可自动」。

## Phase 0 — Evidence

读：`CONSTRAINT/AGENTS/CLAUDE/CONTRIBUTING`、README/锁文件/CI/测试命令、gitignore/部署、只读区。

**证据优先级**：**锁文件、CI、脚本、目录结构等代码/可运行配置为第一依据**；文档中的承诺只作辅助。文档写「有测试」但 CI 未跑 → 按 CI 实况写条目（AGENTS.md #7）。

**完成**：证据摘要（已有规则 | 可验证命令 | 禁区 | 空白）。不捏造项目事实。

## Phase 1 — Constraint map

每类至少一条草案或 `N/A+原因`（示例形态见模板）：

Scope · Git · Destructive · Dependencies · Secrets · Quality · Autonomy · Toolchain · Output · 项目特有。

规则必须**可检查**（路径/命令/yes-no）；删「要细心」类 no-op。

**完成**：地图覆盖上述类。

## Phase 2 — Align

只问：证据答不了且**选错代价高**的项。先给推荐答案。口头惯例与文档冲突 → 让用户选定唯一真相。

**完成**：高代价歧义关闭。  
**门禁**：未确认不覆盖已有 `CONSTRAINT.md`。

## Phase 3 — Write

路径：`<项目根>/CONSTRAINT.md`（用户指定则从用户）。模板：[CONSTRAINT-TEMPLATE.md](CONSTRAINT-TEMPLATE.md)。

规则：条目编号（`G1`…）；正向优先；命令可粘贴；密钥用占位符；与 `AGENTS.md` 并存时后者一行指针即可。

**完成**：无 TBD；与证据无矛盾。

## Phase 4 — Confirm

路径 + 分类计数 + 1–3 条高风险边界；改后落盘；可选 AGENTS 指针。

**完成**：用户确认交付。

## 边界

只写约束文档。与 `to-project` 互补：项目是什么 vs agent 能怎么动。
