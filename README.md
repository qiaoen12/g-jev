# DevMap

DevMap v1.1 是一个零代码开发地图 Skill。用户只需显式调用 `/devmap`；Skill 从 Issue / PRD 整理 Task，结合实际文件变化、测试与 GitHub CI 事实，生成面向负责人和非技术人员的简洁中文看板。开工前一张总地图；开发过程中只在 Task 完成、确认阻塞或重新打开时报告；全部 Task 与最终 L3 验收完成、阻塞清零后再生成一张最终总地图。

DevMap 是独立 Skill，可由开发 Harness 显式调用；它不属于 G-lite、cmux 或任何开发 Harness，也不开发代码、编排 Agent 或监督流程。产品只有文本规则和两个模板，不含运行代码、外部模型接口、仓库配置或自有持久状态。需要保存时，仅在用户指定路径后保存。

## Product files

- [devmap/SKILL.md](devmap/SKILL.md)：`/devmap` 唯一入口、Task 状态、事件触发、文件折叠和测试摘要规则。
- [devmap/templates/prd.md](devmap/templates/prd.md)：可选需求素材与 Task 整理模板；已有 Issue / PRD 不需要改写。
- [devmap/templates/map.md](devmap/templates/map.md)：开工 / 最终总地图与完成 / 阻塞 / 重开 Task 地图模板。

[Mock 验收样例](devmap/fixtures/report-protocol.md) 覆盖 14 个协议场景；样例仅用于文本规则验收。启用后的观察使用当前 Harness 上下文，不引入后台监听或自有持久状态。普通开发、测试失败与修复不生成 DevMap 地图。

## G-lite v3.4 collaboration

G-lite is this repository's GitHub-native collaboration protocol. It governs Issues, independent approval, CI, review, and human-owned merge; it is not a DevMap runtime dependency. Follow [AGENTS.md](AGENTS.md) and the [task template](.github/ISSUE_TEMPLATE/task.md). New work starts only while the Issue is OPEN and the independent Reviewer's `approved` event is fresh for the current Issue body.

Developer opens a PR; `jev-docs` checks this documentation-only repository; an independent Reviewer reviews the current PR HEAD. Human Authority owns governance and final squash merge after the gates pass. This documentation check does not claim to test Jev or DevMap code; the v1.1 product has no runtime code.
