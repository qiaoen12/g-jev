---
name: devmap
description: Create or update a concise, evidence-backed development map from the current task PRD, repository changes, tests, and CI. The only user-facing entry is /devmap.
---

# DevMap v1.1

Use this Skill only when the user explicitly invokes `/devmap`. `/devmap` is the single entry point. Do not require or teach subcommands such as `preflight`, `checkpoint`, or `final`.

DevMap observes and summarizes a task. It does not implement changes, orchestrate Agents, enforce a workflow, or change development authorization. Use the current Harness model for semantic judgments. This version has no Jev API, TypeSafe SDK, MCP, provider abstraction, model router, or runtime integration.

## 1. Identify the stage

Read the current conversation and available task artifacts, then choose one stage:

- **Kickoff**: implementation has not started and the user needs an opening map.
- **Progress**: implementation is underway and the user needs Expected vs Current.
- **Final**: implementation is complete or the user asks for delivery status.

Infer the stage from context. If it remains unclear, ask one short question about whether the user wants a kickoff, progress, or final map. Do not ask the user to choose a subcommand.

## 2. Align with the PRD

Look for a PRD or fixed product brief already supplied in the conversation or project. If one exists, read it in place and preserve its format. Do not rewrite it merely to match the template.

Extract these fields, preserving the source's wording where useful:

- Goal
- Why
- In Scope
- Out of Scope
- Expected Modules / Files
- Expected Size
- Expected Complexity
- Verification Plan
- Acceptance Criteria
- Open Decisions

If an existing PRD is missing information, ask only for the missing fields that affect the requested map. Do not repeat fields already answered or start discussing an implementation design. If no PRD exists, use one brief clarification only to establish the product brief; infer only what is explicit in the request, ask about remaining gaps, and leave unresolved details as Open Decisions. Do not enter an implementation-plan discussion.

If the user wants a PRD or map saved, use the path they gave. If they requested saving or updating but gave no path, ask for the path before writing. Otherwise keep the PRD and map in the current conversation. Never invent a fixed directory, create `.devmap/`, or create repository-local state, configuration, history, or session files.

## 3. Kickoff: establish Test Baseline first

Before emitting a kickoff map, inspect the available project facts and the PRD's Verification Plan and Acceptance Criteria. Read, when available:

- Existing test directories and test files.
- Tests related to this task.
- Test commands and framework configuration.
- `.github/workflows/` and current GitHub CI/check results for the relevant base or PR HEAD.

Report unavailable evidence as `UNKNOWN` or `not accessible`; do not infer a passing result. Count existing tests using a stated, repeatable unit (at minimum, test files; also count test cases only when they can be enumerated reliably). Give both the project-wide total and the task-relevant count. Preserve project test names. Map them to the optional observation levels only when useful:

- L0 Static
- L1 Unit
- L2 Integration
- L3 Acceptance / Contract / Semantic
- L4 E2E / Pilot

A test may also be labeled Permanent, Stage, or Pilot. These are observations, not a required project taxonomy.

The kickoff map separates **Existing** from **Expected**. Existing reports test totals, task-related tests, reusable tests, and what current CI covers. Expected reports a reasonable range for added tests and whether test-first is recommended, with a short reason. Estimate ranges only when evidence supports them; otherwise use `UNKNOWN` and say why. Do not tell the project to change its test system.

## 4. Build the map from evidence

Use `templates/map.md` as the output structure. Keep the map compact and retain these core fields:

- **ATTENTION**: GREEN, YELLOW, RED, or UNKNOWN.
- **SIZE**: SMALL, MEDIUM, LARGE, REFACTOR, or UNKNOWN.
- **SCOPE**: compare the requested scope with actual changes; mark drift or UNKNOWN when evidence is incomplete.
- **COMPLEXITY**: LOW, MEDIUM, HIGH, or UNKNOWN.
- **TEST**: baseline, expected verification, actual runs/results, and CI status.

At kickoff, provide Expected Size, Complexity, modules, an estimated file-count range, verification levels, and an added-test range. At progress and final stages, show **Expected vs Current** directly. Include the key evidence behind each state: PRD section, file path and diff status, named test and result, workflow/check name, or CI link/head when available. Separate facts that can be verified from semantic judgments made from the evidence. Use `UNKNOWN` instead of forcing a conclusion when evidence is insufficient.

For file changes, include every changed path and its A/M/D status when the total is 40 or fewer. Above 40, group ordinary files by directory and report file count plus additions/deletions. Always list clearly out-of-scope or unusual files individually, even in folded groups. Include untracked files in the count when visible.

For progress, prefer the current stage, modules, and countable Plan Items. Calculate completed/total only when the PRD already defines explicit work items; derive any percentage only from that count. Never produce a subjective completion percentage.

In a final map, report only tests actually run and CI results actually observed. Distinguish “not run,” “not configured,” “not accessible,” and “passed”; do not claim a check passed just because it is expected to run.

## 5. Natural checkpoints

Optionally suggest at most about five short lines for a user to call `/devmap` after natural events such as a module finishing, scope or dependencies changing, local verification ending, or before delivery. Suggestions are advisory. Do not add timers, hooks, observers, background polling, automatic blocks, or compliance tracking.
