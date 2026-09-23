# g-jev

轻量的 Jev Semantic 工具，供脚本和 Agent 按需调用。

## G-lite v3.4 collaboration

Jev remains its own product; G-lite supplies a GitHub-native collaboration protocol, not a Jev runtime or local task database.

For a new task, open an Issue with **Original Intent** (the user's words or a fixed PRD reference) before the **Contract** (Goal, Acceptance, Out of scope, Authorization). Follow [AGENTS.md](AGENTS.md) and the [task template](.github/ISSUE_TEMPLATE/task.md). Work starts only while the Issue is OPEN and the independent Reviewer's `approved` event is fresh for the current Issue body.

Developer opens a PR; `jev-docs` checks the documentation-only repository; an independent Reviewer reviews the current PR HEAD. Human Authority owns governance and final squash merge after the gates pass. No Jev code tests are claimed by this docs check; add real tests under a separately approved task when code exists.
