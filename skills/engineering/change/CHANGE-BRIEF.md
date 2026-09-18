# CHANGE-BRIEF — 功能修改简报

供 `change` Phase 0–1 使用。

## 必填

| 项 | 用户侧问题 | 合格标准 |
|----|------------|----------|
| Goal | 改完之后行为应当如何？ | 可观察，不是「更清晰」 |
| Now | 现在实际如何？ | 与 Goal 可对比 |
| Acceptance | 怎样算这次改完？ | 命令 / 接口结果 / 界面步骤 |
| In scope | 本次必须动到的行为面 | 一句话以上 |
| Out of scope | 看起来相关但本次不动 | 至少一条或写「无」 |

## 应填

| 项 | 说明 |
|----|------|
| Why | 用户问题或 PLAN 任务编号 |
| Constraints | 兼容、性能、路径禁区、`CONSTRAINT.md` 引用 |
| Callers known | 已知会受影响的调用方 |
| Prefer | 偏简单或偏一次做对 |

## Brief 模板

```text
## Change brief
- Goal:
- Now:
- Acceptance:
- In:
- Out:
- Constraints:
- Prefer: simple | deepen
```

## 反模式

- 只有「优化一下登录」没有 Now/Out。
- Acceptance 写成「代码结构更好」（属于 Structure 轴，不是 Spec）。
- 用大版本愿景代替本次切片目标。
- 用户未确认 In/Out 就让模型「看着改」。
