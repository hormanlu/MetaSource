# Sources (Open Source Survey)

本目录用于记录外部开源项目/工作流/插件的来源、许可、可借鉴点、冲突点与迁移方案。\n
原则：仓库是真源。外部工具/工作台只做参考、迁移或生成辅助产物，不能成为事实权威。\n
## 候选清单（首批）

| 项目 | 类型 | 主要能力 | 适合迁移什么 | 冲突/注意 | 链接 |
| --- | --- | --- | --- | --- | --- |
| Fiction Kit | repo 模板 | spec-driven 写作工件、prompts、review agents | 工作流阶段化与模板组织 | 结构不同，建议只借 SOP | https://github.com/keberle/fiction-kit |
| SpecKit Fiction Preset | 命令/模板 | 以命令驱动写作阶段，模板齐全 | workflow 文档与模板字段 | 依赖其命令体系，建议借模板 | https://github.com/adaumann/speckit-preset-fiction-book-writing/ |
| GOAT-Storytelling-Agent | agent | 分尺度规划->写作，强调长篇一致性 | 路由分层/多尺度规划思路 | 有自己的模型/流程，建议借思路 | https://github.com/GOAT-AI-lab/GOAT-Storytelling-Agent |
| novel-copilot | 工作台（全栈） | 三层记忆、人物关系图、Plot Graph、Timeline、QC、修订循环 | 数据模型/审计维度/修订循环 | 平台耦合强，仓库真源需做适配层 | https://github.com/doctoroyy/novel-copilot/ |
| Kindling | 写作软件（无AI） | 大纲可见写作、导入导出、实体识别 | 导入导出/字段模型/可视化交互借鉴 | 使用本地 SQLite，建议作为外部工具 | https://github.com/smith-and-web/kindling |
| Obsidian StoryLine | Obsidian 插件 | 角色视图、关系图、scene board、timeline | 关系图/场景元数据字段 | 需要 Obsidian vault 结构，建议导出/映射 | https://github.com/PixeroJan/obsidian-storyline |
| Novalist | Obsidian 工作台 | 关系图、plot board、导出 | UI/字段与视图设计 | 同上，建议做迁移适配 | https://github.com/Drommedhar/novalist/wiki/Home/a587596040ea0b72bcb395e55145c508be2d697c |
| Radial Timeline | Obsidian 插件 | 场景多时间线可视化 | 时间线字段/视图概念 | 同上，建议做迁移适配 | https://github.com/EricRhysTaylor/Obsidian-Manuscript-Timeline |

## 下一步怎么用

- 对每个候选建立一页：记录 `license`（需要确认时标记 TODO）、采纳点、落地位置（ops/qa、ops/workflows、canon 字段等）。\n
