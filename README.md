# DevMap

DevMap v1.1 是一个零代码开发地图 Skill。用户只需显式调用 `/devmap`；Skill 根据上下文判断当前处于开工前、开发中或完成后，并把 PRD、实际文件变化、测试与 GitHub CI 事实整理成 Expected vs Current 地图。

DevMap 是独立 Skill，可由开发 Harness 显式调用；它不属于 G-lite、cmux 或任何开发 Harness，也不开发代码、编排 Agent 或监督流程。产品只有文本规则和两个模板，不含运行代码、外部模型接口、仓库配置或自有持久状态。需要保存时，仅在用户指定路径后保存。

## Product files

- [devmap/SKILL.md](devmap/SKILL.md)：`/devmap` 唯一入口、阶段判断、PRD 对齐、Test Baseline 和地图生成规则。
- [devmap/templates/prd.md](devmap/templates/prd.md)：可选 PRD 信息模板；已有 PRD 不需要改写。
- [devmap/templates/map.md](devmap/templates/map.md)：开工、过程和最终地图模板。

## G-lite v3.4 collaboration

G-lite is this repository's GitHub-native collaboration protocol. It governs Issues, independent approval, CI, review, and human-owned merge; it is not a DevMap runtime dependency. Follow [AGENTS.md](AGENTS.md) and the [task template](.github/ISSUE_TEMPLATE/task.md). New work starts only while the Issue is OPEN and the independent Reviewer's `approved` event is fresh for the current Issue body.

Developer opens a PR; `jev-docs` checks this documentation-only repository; an independent Reviewer reviews the current PR HEAD. Human Authority owns governance and final squash merge after the gates pass. This documentation check does not claim to test Jev or DevMap code; the v1.1 product has no runtime code.
