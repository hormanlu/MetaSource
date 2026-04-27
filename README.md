# MetaSource

`MetaSource` 是一个以代码仓库方式管理的原创中文科幻 IP 项目。

当前目标不是直接“开写一切”，而是先建立一套适合长篇小说、世界观管理、章节续写、设定审校和衍生内容生产的 AI 工作流，让后续创作尽量不跑偏。

## 仓库目标

- 为 `MetaSource / EarthOL / 源码宇宙` 维护长期可复用的世界观资产
- 用结构化文件替代口头记忆，降低 AI 长文失忆、设定漂移和人物跑偏
- 为小说、短视频、人物外传、设定解读等衍生内容提供统一真源
- 把“创作”拆成可追踪的阶段：规划、写作、审校、回填、迭代

## 从哪里开始

每次开始一个新会话或新任务，先读：

1. `AGENTS.md`
2. `canon/00_project/project-brief.md`
3. `canon/01_world/rules.md`
4. `ops/state/current-focus.md`

如果是章节任务，再读对应的 `manuscript/vol-xx/ch-xxx/` 文件。

## 目录说明

- `canon/`
  - 永久真源。世界观、人物、主线、时间线、事实账本都在这里维护。
- `manuscript/`
  - 写作工作区。每章单独维护简报、章纲、草稿和审校。
- `voice/`
  - 文风约束。包括中文小说文风、去 AI 味规则、禁用表达。
- `ops/prompts/`
  - 对话前置模板。用于启动会话、写章前简报、审校门禁。
- `ops/skills/`
  - 仓库内的角色化工作技能说明，如设定师、章纲师、续写师、一致性审校员。
- `ops/orchestration/`
  - `v2` 多智能体编排层。定义中控、agent 清单、上下文装配和单章流水线。
- `ops/state/`
  - 当前项目焦点、最近会话摘要和下一步行动。
- `.trae/rules/`
  - Trae 项目规则，支持“始终生效”上下文召回与行为约束。
- `docs/`
  - 工作流、上下文加载顺序、目录设计说明。

## 推荐工作流

1. 明确任务类型：设定 / 人物 / 剧情 / 正文 / 审校 / 精修
2. 按 `AGENTS.md` 加载必要上下文
3. 如果任务较复杂，按 `ops/orchestration/` 里的 `v2` 编排链执行
4. 在 `canon/` 或 `manuscript/` 对应位置工作
5. 用 `ops/prompts/review-gate.md` 做自检
6. 把新增事实回填到 `canon/04_continuity/`
7. 更新 `ops/state/current-focus.md`

## v2 编排入口

如果任务涉及多步创作或需要多人格分工，优先读取：

1. `ops/orchestration/orchestrator.md`
2. `ops/orchestration/agent-manifest.md`
3. `ops/orchestration/context-assembly.md`
4. `ops/orchestration/chapter-pipeline.md`

默认建议：

- 设定任务：`Orchestrator -> WorldBuilder -> ConsistencyReviewer`
- 人物任务：`Orchestrator -> CharacterArchitect -> ConsistencyReviewer`
- 章节任务：`Orchestrator -> Outliner -> Drafter -> ConsistencyReviewer -> StylePolisher -> FactKeeper`

## 当前起点

- 世界观初稿已落在 `canon/01_world/world-bible.md`
- 本仓库当前重点是先把结构和工作流搭稳，再逐步推进卷纲、人物和第一章


