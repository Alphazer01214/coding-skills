---
name: to-project
description: 把用户的抽象想法，经多轮访谈对齐，落成项目设计文档包。
disable-model-invocation: true
---

# To Project

抽象想法 → **多轮对齐** → 项目设计文档包（非实现、非问答纪要；非 ticket/spec）。

**何时**：想法模糊、各方对「在做什么」未共识时。

**前置**：可写 cwd；用户能拍板决策（事实自己查）。

## Phase 0 — Facts

查：现有代码/README/AGENTS、消息里的约束。

**完成**：列出「已知事实 | 待决策（及为何环境答不了）」。无关 frontier 的问题可并行开问。

## Phase 1 — Design tree

决策域（每域至少一节点，或 `N/A+原因`）：Why / Who / Success / Scope / Shape / Tech / Constraints / Risks / Next。

**完成**：域覆盖完毕。

## Phase 2 — Grill rounds

- **Frontier** = 前置已定、现在就能问的决策；一轮问完并给**推荐答案**。
- 事实→自己查；决策→用户；否决推荐后重算 frontier。

```text
Q{n} — {标题}
{选项与后果}
→ 推荐：{答案 + 一句理由}
```

**完成**：frontier 空；无静默假设（未议项写入文档「假设」）。  
**门禁**：用户确认对齐前不写文件。

## Phase 3 — Synthesize

产出：`docs/project/PROJECT.md`（无 `docs/` 则根目录 `PROJECT.md`）。模板：[PROJECT-TEMPLATE.md](PROJECT-TEMPLATE.md)。

规则：术语一致；成功/里程碑/风险可检查；选型=结论+理由或「未定+决策点」；不贴长纪要；短而锋利。

**完成**：保留章节无 TBD；开放问题=真实未决。

## Phase 4 — Confirm

展示路径 + 摘要（定位/成功/边界/下一步）+ 1–3 个开放问题；修订后落盘。**不**自动建代码脚手架。

**完成**：用户确认；文件已写入。

## 边界

对话已成熟可跳过访谈进 Phase 3（须说明）。实现走后续 implement/tdd，本 skill 不写码。
