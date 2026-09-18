# DEBUG-INTAKE — 现象描述清单

供 `debug` Phase 0 使用。能从日志/仓库读到的先读，再向用户补缺。

## 必问（缺则无法验证现象）

| 项 | 问题（对用户） |
|----|----------------|
| Actual | 你实际看到什么？（报错原文 / 错误输出 / 空白） |
| Expected | 本应发生什么？ |
| Trigger | 具体怎么触发？（命令、点击路径、输入样例） |
| Environment | 在哪发生？（本地/测试/生产，分支/版本，OS/浏览器） |

## 应问（影响定位）

| 项 | 问题 |
|----|------|
| When started | 哪次改动/发版之后？还是一直如此？ |
| Frequency | 必现还是偶发？约几分之几？ |
| Scope | 只某个用户/数据，还是所有人？ |
| Tried | 你已经试过什么？结果？ |
| Impact | 现在挡住什么？有临时绕法吗？ |
| Artifacts | 可否提供：完整堆栈、日志片段、HAR、录屏、失败用例？ |

## Symptom brief 模板

```text
## Symptom brief
- Expected:
- Actual:
- Trigger:
- Environment:
- Frequency:
- Started:
- Impact:
- Tried:
- Open gaps: <影响定位的未知>
```

## 反模式（Intake）

- 用户只说「挂了」就直接猜架构原因。
- 用实现细节问题代替现象问题（先问 stack 再问触发顺序）。
- 把「已知未知」写成已完成。
- 在缺口很大时承诺「应该是 XX 问题」。
