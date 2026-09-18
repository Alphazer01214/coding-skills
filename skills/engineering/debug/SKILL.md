---
name: debug
description: 引导描述 bug 现象，用反馈回路逐步定位原因，再与用户对齐修改诉求后才动手改。Use when the user reports something broken, failing, wrong, or slow, or says "debug" / "有个 bug" / "不对".
---

# Debug

现象引导 → **red-capable 回路**定位 → 对齐修改诉求再改。

**三禁**：现象不清不定假设；无红回路不猜因；未对齐 fix intent 不写修复。

**何时**：坏/不对/失败/变慢/抛错。新建需求不走本 skill。

**证据优先级**：**可运行复现与代码第一**，文档/注释里的「本应如何」只作 Expected 参考（AGENTS.md #7）。

## Phase 0 — Intake

先读日志/环境，再补问缺口。最小 Symptom brief：**Expected · Actual · Trigger · Environment · Frequency**（详表 [DEBUG-INTAKE.md](DEBUG-INTAKE.md)）。

**完成**：brief 可写；未知项已标注。无法形成可验证现象 → 要日志/复现/权限，**停止**猜测。

## Phase 1 — Red loop（核心）

目标：一条 **tight** 命令/步骤，能对**本 bug** 变红。

顺序：失败测试 → curl → CLI+夹具 → 无头浏览器 → 重放 → 最小 harness/property/bisect。  
Tighten：更快、信号更尖、更确定。偶发：先提高复现率。

**完成**（须**已运行过**）：

- [ ] Red-capable（对准用户症状）
- [ ] Deterministic（或复现率足够）
- [ ] Fast
- [ ] Agent-runnable

**门禁**：无 red 命令禁止假设/修补。建不出→停，说明已试项，要环境/脱敏产物/埋点许可。输出先脱敏。

## Phase 2 — Locate

1. **Minimise**：症状须=用户所述；缩到仍变红的最小场景（每删一次重跑）。剩余元素均 load-bearing。
2. **Hypotheses**：3–5 条可证伪预测；给用户排序列表。
3. **Probe**：一次一个变量；调试器→打点→日志；日志前缀 `[DEBUG-…]`；性能先基线再 bisect。

**完成**：根因有证据（哪条假设被 red/green/测量证实）。

## Phase 3 — Align fix

对齐：**Fix goal**（验收信号）· **Scope**（只修根因/止血/周边）· **Constraints** · **Seam**（回归测哪里）· **现在改 or 只要报告** · Non-goals。

**完成**：用户确认 goal+scope+是否现在改。只分析→交付结论，**不改代码**。

## Phase 4 — Act

仅当确认「现在改」：回归测试先红→修→绿；重跑 Phase 1 原场景；清 `[DEBUG-…]`；写清证实的根因。无合适 seam→如实记录，不假装已锁定。

## 边界

Model-invoked；需求扩大不属本 skill。PLAN 同步不静默改，提示用户 `/to-plan`。
