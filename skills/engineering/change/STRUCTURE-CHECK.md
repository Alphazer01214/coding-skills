# STRUCTURE-CHECK — 结构检查清单

供 `change` Phase 2（侦察）与 Phase 5（Structure 轴）使用。
每条：发现位置（file:line 或模块名）→ 证据一句话 → 判定（ok / risk / critical）。

**依据**：只认**代码里的真实关系**（import/调用/重复实现）；设计文档与代码不一致时以代码为准。

## 侦察时先看

| ID | 检查 | 说明 |
|----|------|------|
| R1 | 行为落在哪条 **seam** 上？ | 公开接口/命令/路由；验证应落在此 |
| R2 | **爆炸半径** 多大？ | 直接调用方数量级；过大则考虑 expand–contract 或拆片 |
| R3 | 同一行为是否已散落多处？ | 改一处漏 N 处 = 屎山前兆 |
| R4 | 附近是否有「未来用」空壳？ | 抽象、配置、插件点无人调用 |

## 评审 Structure 轴

| ID | 检查 | 屎山信号 |
|----|------|----------|
| S1 | **Duplicated logic** | 本次 diff 内复制粘贴或第三次重复形状 |
| S2 | **Shotgun surgery** | 一个逻辑变更打散在大量文件 |
| S3 | **Speculative generality** | 新参数/接口/钩子当前行为用不到 |
| S4 | **Shallow module** | 新增大量薄包装，调用方仍要知道细节 |
| S5 | **Feature envy / 挪数据** | 新代码大量伸手进他模块数据 |
| S6 | **Divergent change** | 一个文件同时为多个不相关原因改 |
| S7 | **Middle man** | 仅为转发而新增的层 |
| S8 | **Interface as test surface** | 测试绕过公开接口查库/ mock 内部 |
| S9 | **Depth** | 新行为藏在接口后，还是散在 UI/调用方分支里 |
| S10 | **One reason per change** | 本次是否在给模块叠加第二个变更原因 |

## 实现纪律（Phase 4）

| ID | 检查 |
|----|------|
| I1 | diff 是否超出已确认落点？超出是否有理由？ |
| I2 | 是否夹带无关 rename/重构/格式？ |
| I3 | 验证命令是否在本次行为上真的曾失败再通过？ |
| I4 | 是否在未确认的 seam 上写了实现耦合测试？ |

## 处置

- **risk**：写入交付摘要「可选后续」，不阻塞（用户接受时）。
- **critical**（重复加剧、验收因结构问题走歪、无 seam 可测、扩散且不可验证）：退回 Phase 3/4 或拆片。
- Structure 与 Spec **分列**，禁止用「能跑」掩盖结构 critical。
