# DevMap

DevMap v1.1 是一个零代码开发地图 Skill。用户只需显式调用 /devmap；Skill 从 Issue / PRD 整理 Task，结合实际文件变化、验证与仓库自动检查事实，生成面向负责人和非技术人员的简洁中文看板。开工前输出一张“负责人数据看板 + 四列 Task 地图”；开发过程中仅在 Task 完成、确认阻塞或重新打开时输出该 Task 地图；所有 Task 与最终 L3 验收完成、阻塞清零后输出计划与实际摘要。

DevMap 是独立 Skill，可由开发 Harness 显式调用；它不属于 G-lite、cmux 或任何开发 Harness，也不开发代码、编排 Agent 或监督流程。产品由文本规则、两个模板和验收样例组成，不含运行代码、外部模型接口、仓库配置或自有持久状态。需要保存时，仅在用户指定路径后保存。

## Product files

- [devmap/SKILL.md](devmap/SKILL.md)：/devmap 唯一入口、Task 状态、事件触发、路径树 / 目录折叠、中文用户可见规则和统一测试摘要。
- [devmap/templates/prd.md](devmap/templates/prd.md)：可选需求素材与内部 Task 整理模板；已有 Issue / PRD 不需要改写。
- [devmap/templates/map.md](devmap/templates/map.md)：开工总地图、最终总地图和三类 Task 事件地图的固定呈现模板。
- [devmap/fixtures/report-protocol.md](devmap/fixtures/report-protocol.md)：14 项语义验收、6 项视觉验收，以及五类地图的固定 Mock 实际渲染样例。

地图默认只显示负责人需要的信息。Task 预期结果、完成条件和依赖保留在内部结构化数据中，不铺成用户可见明细表。小文件集合优先显示目录树；大文件集合按目录折叠，同时保留真实文件总数。

## G-lite v3.4 collaboration

G-lite is this repository's GitHub-native collaboration protocol. It governs Issues, independent approval, CI, review, and human-owned merge; it is not a DevMap runtime dependency. Follow [AGENTS.md](AGENTS.md) and the [task template](.github/ISSUE_TEMPLATE/task.md). New work starts only while the Issue is OPEN and the independent Reviewer's approved event is fresh for the current Issue body.

Developer opens a PR; jev-docs checks this documentation-only repository; an independent Reviewer reviews the current PR HEAD. Human Authority owns governance and final squash merge after the gates pass. This documentation check does not claim to test Jev or DevMap code; the v1.1 product has no runtime code.
