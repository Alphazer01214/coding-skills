# PROJECT-MAP 模板

供 `explain-project` 产出使用。

---

# OVERVIEW.md

> 项目：<名称>  
> 深度：L0–L<n>  
> 更新：<YYYY-MM-DD>  
> 入口：<入口符号或路径>  
> 图：[DEPENDENCY.md](DEPENDENCY.md) · [INDEX.md](INDEX.md)

## 这个项目是什么

<1 段：领域问题与解决方式>

## 怎么分层

与 L0/L1 图对应；每层职责 1–2 句。

| 层/模块 | 职责 | 代表路径 |
|---------|------|----------|
|  |  |  |

## 主流程

1. 入口 `<符号>` @ `path:line` → …
2. …

## 关键符号

| 符号 | Kind | 职责 | 位置 |
|------|------|------|------|
|  | struct/fn/module |  |  |

## 如何自己读

- 从 `…` 开始
- 建议命令：`…`

## 未核实与局限

- …

---

# DEPENDENCY.md

> 分层：<L0/L1/L2/L3>  
> 范围：<全库 / 子系统>  
> 证据：符号表见 [INDEX.md](INDEX.md)；边均由代码 import/call 核实  

## 图例

| 边 | 含义 |
|----|------|
| imports | 模块依赖 |
| calls | 函数调用 |
| owns | 包含/组合 |
| implements | 实现接口 |
| unverified | 推断，未核实 |

## L0 — 子系统

```mermaid
flowchart TB
  %% 标题：…
```

## L1 — 模块依赖

```mermaid
flowchart LR
```

## L2 — 类型/结构体（可选）

```mermaid
classDiagram
```

## L3 — 核心函数调用（可选）

范围：<入口符号链>

```mermaid
flowchart LR
```

## 抽查记录

| 边 | 证据 | 结果 |
|----|------|------|
| A --> B | path:line | ok |

---

# INDEX.md

> 符号速查；路径相对仓库根  

| 符号 | Kind | 职责摘要 | 出现于图 |
|------|------|----------|----------|
| `Checkout` | fn | 主结账入口 | L3 |
| `Order` | struct | 订单聚合根 | L2 |

| 边 | From | To | Kind | 证据 |
|----|------|-----|------|------|
| 1 |  |  |  | path:line |
