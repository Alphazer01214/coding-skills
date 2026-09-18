---
name: change
description: 把功能修改收成可验证的最小变更：先边界与 seam，再切片实现，双轴评审结构与规格后收尾。
disable-model-invocation: true
---

# Change

功能修改的门禁流，抑制屎山。**最小变更**：边界 → seam → 切片；**Structure ∥ Spec** 分轴；不合格退回，禁止补丁盖补丁。

**何时**：修改/增强已有功能。新建→`to-project`；故障→`debug`。

**前置**：先读 `CONSTRAINT/PLAN/PROJECT`（若有）。**证据优先级**：seam/落点以**代码与调用链**为第一依据，文档只作辅助；冲突时以代码为准并在方案里写明（AGENTS.md #7）。

## Phase 0 — Intake

**Change brief**：Goal · Now · Acceptance · In/Out · Constraints · Non-goals（详 [CHANGE-BRIEF.md](CHANGE-BRIEF.md)）。

**完成**：Goal/Now/Acceptance 齐全。  
**门禁**：无用户可确认的 Acceptance → 不实现。

## Phase 1 — Bound

In/Out；允许触碰路径（未列入=默认不动）；验收=行为信号（非「更优雅」）。

**完成**：用户确认 In/Out + 范围 + Done when。

## Phase 2 — Recon（只读）

找 **seam**；估计爆炸半径；标风险（重复/浅接口/散落/空抽象）；列**改动落点**（扩大须说明）。检查项：[STRUCTURE-CHECK.md](STRUCTURE-CHECK.md)。**以代码为准**：文档描述与真实调用不一致时，按代码判断。

**完成**：首选 seam + 落点 + 爆炸半径一句话。大范围机械变更→expand–contract/另切片。  
**门禁**：说不清 seam 或落点散开无理由 → 先补齐，不写码。

## Phase 3 — Shape

≤2 方案（A 偏简：现有 seam 最小扩展；B 可选深化：收敛重复）。原则：公开边界可验收；无投机扩展点；收成**一个垂直切片**。

**完成**：用户选定方案 + slice 验收一句。  
**门禁**：未要的「以后可能」扩展 → 删后再确认。

## Phase 4 — Implement

验证入口先能对**本次行为**变红（无测试设施则先约定命令）→ 只改落点 → 跑约定命令 → 不夹带无关重构 → 会话变长/切片边界到则停。

**完成**：验证通过或标 PRE-EXISTING；diff=落点（扩大有理由）；无投机 API。

**门禁**：未过却称完成→退回；连续失败→回 Phase 2 看 seam，禁盲改。

## Phase 5 — Review（双轴，不混分）

- **Spec**：Acceptance？Non-goals？对称路径漏改？
- **Structure**：按 [STRUCTURE-CHECK.md](STRUCTURE-CHECK.md)（重复/投机/浅接口/双变更原因/是否打在公开 seam）。

**完成**：两轴有结论；Critical（验收未满足或结构明确恶化）须修复或用户明确接受。  
**门禁**：仅 Structure 挂 → 回 Shape/Implement，不是加文件。

## Phase 6 — Exit

摘要：改了什么/没改什么/验证结果/风险。PLAN 同步提示 `/to-plan`。不自动大重构。不擅自 commit/push。

**完成**：用户确认摘要。

## 边界

User-invoked；细小改动勿跑满门禁。未落地 `codebase-design/tdd/code-review` 时用本目录附属文件。
