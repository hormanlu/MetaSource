# Workflow Router (Internal)

本文件是内部路由表：把“意图”映射到具体工作流，并规定默认调用链。用户不需要选择，系统自动执行。

## 1. 固定前置

每次任务开始前默认读取（由 `AGENTS.md` 强制）：

- `README.md`
- `AGENTS.md`
- `canon/00_project/project-brief.md`
- `canon/01_world/rules.md`
- `ops/state/current-focus.md`

## 2. 路由表

| intent | workflow | 默认调用链（最小） | 产物落点 |
| --- | --- | --- | --- |
| `write.chapter` | `ops/workflows/chapter-write.md` | Outliner -> Drafter -> ConsistencyReviewer -> StylePolisher -> FactKeeper | `manuscript/**` + `canon/04_continuity/**` |
| `plan.chapter` | `ops/workflows/chapter-plan.md` | Outliner -> ConsistencyReviewer | `manuscript/**/brief.md` + `manuscript/**/outline.md` |
| `review.chapter` | `ops/workflows/chapter-review.md` | ConsistencyReviewer -> StylePolisher -> FactKeeper | `work/critiques/**` + `canon/04_continuity/**`（必要时） |
| `design.world` | `ops/workflows/world-design.md` | WorldBuilder -> ConsistencyReviewer | `work/proposals/**`（默认提案） |
| `design.character` | `ops/workflows/character-design.md` | CharacterArchitect -> ConsistencyReviewer | `work/proposals/**`（默认提案） |
| `design.plot` | `ops/workflows/plot-design.md` | Outliner -> ConsistencyReviewer | `work/proposals/**`（默认提案） |
| `record.idea` | `ops/workflows/idea-capture.md` | (no agent) | `work/ideas/**` |
| `record.research` | `ops/workflows/research-capture.md` | (no agent) | `work/research/**` |
| `critique.asset` | `ops/workflows/asset-critique.md` | ConsistencyReviewer | `work/critiques/**` |
| `propose.canon` | `ops/workflows/proposal.md` | Orchestrator -> ConsistencyReviewer | `work/proposals/**` |
| `merge.canon` | `ops/workflows/canon-merge.md` | Orchestrator -> ConsistencyReviewer -> FactKeeper | `canon/**`（受限写入） |

## 3. 升级触发（不一次性全跑）

默认只跑“最小链路”。只有在出现以下情况时，才升级流程（增加步骤或回退重做）：

- 审校发现硬冲突：短路回退到章纲或提案阶段
- 章节结构失败：退回 Outliner，不让 Drafter 硬补
- 仅文风问题：只跑 StylePolisher，不重跑审校
- 需要改动真源：先进入 proposal，再 merge

## 4. 写入权限（简表）

- 默认允许写入：`manuscript/**`、`work/**`、`ops/state/**`
- 受限允许写入：`canon/04_continuity/**`（FactKeeper 回填）
- 禁止直接写入：`canon/01_world/**`、`canon/02_characters/**`、`canon/03_plot/**`（必须走提案与门禁）

