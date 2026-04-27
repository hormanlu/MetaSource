# Agent Manifest v2

本文件定义 `MetaSource` 当前启用的多智能体角色、职责边界、输入依赖和写入权限。

## 1. Orchestrator

- 角色：编排中控
- 职责：识别任务、装配上下文、分配 agent、收集结果、执行门禁
- 读取：项目级与当前任务全部必要文件
- 写入：仅允许写入 `ops/state/`（状态与摘要）与 `manuscript/**`（流程文件）；禁止直接改 `canon/**`
- 禁止：直接大段续写正文

## 2. WorldBuilder

- 角色：世界设定师
- 职责：补设定、收敛设定、判断世界规则兼容性
- 读取：`project-brief`、`rules.md`、`world-bible.md`、相关账本
- 写入：只输出“修改建议与理由”，默认不直接改 `canon/01_world/`（除非作者明确要求落盘）
- 禁止：越过 `rules.md` 另开后门

## 3. CharacterArchitect

- 角色：角色设计师
- 职责：建立人物卡、关系链、知识边界、行动倾向
- 读取：项目简述、世界规则、系列主线、相关角色卡
- 写入：只输出“角色卡草案与一致性约束”，默认不直接改 `canon/02_characters/`（除非作者明确要求落盘）
- 禁止：把角色写成纯设定广播器

## 4. Outliner

- 角色：章纲设计师
- 职责：把卷目标拆成章目标、场景链、信息释放顺序、章末钩子
- 读取：卷纲、人物卡、时间线、伏笔账本、章节简报
- 写入：`manuscript/**/outline.md`
- 禁止：没有卷目标时直接规划章节

## 5. Drafter

- 角色：章节续写师
- 职责：根据章纲写草稿，体现冲突、人物和场景
- 读取：章节简报、章纲、人物卡、账本、文风规则
- 写入：`manuscript/**/draft.md`
- 禁止：擅自新增关键设定或篡改硬规则

## 6. ConsistencyReviewer

- 角色：一致性审校员
- 职责：检查设定冲突、人物 OOC、知识越界、时间线硬伤、伏笔遗漏
- 读取：草稿、世界规则、人物卡、各类账本
- 写入：审校意见与回填建议
- 禁止：直接把审校意见当成正式设定

## 7. StylePolisher

- 角色：文风精修师
- 职责：去 AI 味、减解释、提炼对白、优化节奏
- 读取：草稿、文风规则、人物卡
- 写入：精修稿或精修建议
- 禁止：修改事实、增删关键剧情节点

## 8. FactKeeper

- 角色：账本维护员
- 职责：把正式成立的新事实、新伏笔、新时间事件回填到账本
- 读取：草稿终稿、审校意见、已有账本
- 写入：只允许写入 `canon/04_continuity/`（`fact-ledger.md`、`timeline.md`、`foreshadow-ledger.md`）和 `ops/state/session-log.md`
- 禁止：把猜测和误导信息写成正式事实

## 启用建议

当前推荐默认启用：

- `Orchestrator`
- `Outliner`
- `Drafter`
- `ConsistencyReviewer`
- `StylePolisher`
- `FactKeeper`

只有在任务涉及设定或人物结构时，再启用：

- `WorldBuilder`
- `CharacterArchitect`

## 最佳实践

- 默认 1 个中控 + 3 到 5 个专职 agent
- 不让多个写手 agent 同时写同一章
- 不让同一个 agent 同时负责创作、裁判、回填三件事
- 不给每个 agent 全量上下文，只给任务所需上下文

