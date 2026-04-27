# Context Assembly v2

本文件规定不同任务下的最小上下文装配策略，目标是减少 AI 跑偏和上下文污染。

## 总原则

- 只读取必要文件，不全量灌仓库
- 永久真源优先于临时草稿
- 先读规则，再读任务文件
- 同层文件优先局部读取，避免无关信息干扰

## 基础上下文

所有任务默认读取：

- `README.md`
- `AGENTS.md`
- `canon/00_project/project-brief.md`
- `canon/01_world/rules.md`
- `ops/state/current-focus.md`

## 世界观任务

额外读取：

- `canon/01_world/world-bible.md`
- `canon/04_continuity/fact-ledger.md`

## 人物任务

额外读取：

- 相关角色卡
- `canon/03_plot/series-arc.md`
- `canon/04_continuity/fact-ledger.md`

## 剧情规划任务

额外读取：

- `canon/03_plot/series-arc.md`
- `canon/03_plot/volume-outline.md`
- `canon/04_continuity/timeline.md`
- `canon/04_continuity/foreshadow-ledger.md`

## 章节写作任务

额外读取：

- 本章 `brief.md`
- 本章 `outline.md`
- 本章 `draft.md`（若存在）
- 相关人物卡
- `timeline.md`
- `fact-ledger.md`
- `foreshadow-ledger.md`
- `voice/prose-style.md`
- `voice/anti-ai-style.md`

## 审校任务

额外读取：

- 本章草稿
- 本章章纲
- 相关人物卡
- 相关账本

## 禁止事项

- 不要把整本 `world-bible`、所有角色卡、全部章节一起塞进单次写作任务
- 不要让文风任务读取无关设定目录
- 不要让回填任务读取无关长篇正文


