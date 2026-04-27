# AI 创作工作流

## 目标

建立一个适合中文长篇小说和 IP 母体创作的最小可用流程，让 AI 输出尽可能稳定、不跑偏、可复盘。

## 总流程

1. 冷启动
- 冻结项目简述
- 冻结世界硬规则
- 建立世界说明书
- 建立模板和账本

2. 规划
- 建人物卡
- 建系列主线
- 建卷纲
- 建章纲

3. 写作
- 先写章节前置简报
- 再写章纲
- 最后写草稿

4. 审校
- 检查设定一致性
- 检查人物一致性
- 检查剧情推进
- 检查文风与 AI 腔

5. 回填
- 更新时间线
- 更新事实账本
- 更新伏笔账本
- 更新当前焦点和会话摘要

## v2 多智能体编排

当任务复杂度上升，或者需要显式防跑偏时，默认启用 `v2` 编排层：

- 中控：`ops/orchestration/orchestrator.md`
- 角色清单：`ops/orchestration/agent-manifest.md`
- 上下文装配：`ops/orchestration/context-assembly.md`
- 单章流水线：`ops/orchestration/chapter-pipeline.md`

### 推荐调用链

- 设定任务：`Orchestrator -> WorldBuilder -> ConsistencyReviewer -> FactKeeper`
- 人物任务：`Orchestrator -> CharacterArchitect -> ConsistencyReviewer -> FactKeeper`
- 剧情任务：`Orchestrator -> Outliner -> ConsistencyReviewer`
- 章节任务：`Orchestrator -> Outliner -> Drafter -> ConsistencyReviewer -> StylePolisher -> FactKeeper`

### 为什么要加编排层

- 把创作和裁判拆开，避免模型自说自话
- 把最小上下文装配写死，减少无关信息污染
- 把每轮产出都变成可回填、可追踪的工件
- 把“是否通过”从主观感觉，变成显式门禁

## 为什么这样设计

- `canon/` 负责真相与约束
- `manuscript/` 负责生产与试错
- `voice/` 负责风格统一
- `ops/state/` 负责最近任务与上下文压缩

## 防跑偏机制

- 每次对话都有统一入口文件 `AGENTS.md`
- 每次写章都必须有 `chapter-brief`
- 每次产出后都要走 `review-gate`
- 任何新增正式事实都要回填账本
- 复杂任务默认走 `Orchestrator`，不让单个 agent 独占全流程
- 审校发现硬冲突时，禁止直接进入精修
- 用户不选择工作流：系统按 `ops/routing/intent-taxonomy.md` 自动识别意图，并按 `ops/workflows/router.md` 自动路由

## 推荐习惯

- 一次只处理一个明确任务
- 没有章纲，不写正文
- 没有回填，不进入下一章
- 不让 AI 同时扮演作者、编辑、裁判三个角色
- 多智能体数量控制在最小必要规模，不为了“高级感”滥加 agent


