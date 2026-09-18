# AGENTS.md

## Repo

`coding-skills`：一组针对真实工程失败模式的 agent skills（对齐、边界、计划、防屎山、排障、代码地图）。

- 用法与场景：[README.md](README.md)
- Skill 清单：[skills/README.md](skills/README.md)

## Skill 不变量

1. **User-invoked**：`disable-model-invocation: true` + 人类一句话 description；**其他 skill 不得**经 Skill tool 调用。
2. **Model-invoked**：description 含触发分支；用户或其他 skill 均可调用。
3. 操作性依赖写 `Call the Skill tool with "<name>"`；前置若是 user-invoked，写「请用户运行 `/name`」。
4. 流程 skill 必须有 **defining constraint** 与 **completion criterion**（门禁）。
5. 新增 user-reachable skill → 同步 `skills/README.md` 与 `skills/engineering/ask/SKILL.md`。
6. 实现类 skill **不静默**改 `PLAN.md` / 不擅自 `commit`/`push`（除非项目 `CONSTRAINT.md` 或用户明确要求）。
7. **既有项目证据优先级**：**代码与可运行命令是第一依据**；README/PLAN/架构文档只作辅助。冲突时以代码为准，标出冲突并提醒改文档。

## 编写规范（摘要）

- 目录：`skills/<bucket>/<skill-id>/SKILL.md` + 可选附属模板
- 门禁型 Phase + completion criterion；示例/长清单下沉附属文件
- User-invoked 主文保持短；共享不变量只写在本文件

## Install

- 项目级：`skills/engineering/<id>/` → `<project>/.mimocode/skills/<id>/`
- 全局：`~/.config/mimocode/skills/<id>/`
- 新会话生效。
