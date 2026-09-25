# DevMap

- **Stage:** Kickoff / Progress / Final
- **Task / PRD:** <reference or conversation context>
- **Evidence checked:** <diff/base or PR head, tests, CI check and run/head where available>
- **Current stage / Plan Items:** <countable items and states; percentage only for PRD-defined items>

## Map

| Field | Expected | Current | Status and evidence |
|---|---|---|---|
| ATTENTION | — | GREEN / YELLOW / RED / UNKNOWN | <key evidence; mark semantic judgment> |
| SIZE | SMALL / MEDIUM / LARGE / REFACTOR / UNKNOWN | <actual size or not started> | <basis> |
| SCOPE | <PRD scope> | <observed scope> | MATCH / DRIFT / UNKNOWN; <changed paths or evidence> |
| COMPLEXITY | LOW / MEDIUM / HIGH / UNKNOWN | <observed level or not started> | <basis> |
| TEST | <verification levels and new-test range> | <baseline, tests actually run, and CI actually observed> | <reused tests, results, or UNKNOWN> |

## Test Baseline

**Existing**

- Test files / cases: <project total and counting unit>
- Task-related tests: <count and names, or none found>
- Current CI covers: <checks and observed scope/result, or UNKNOWN>

**Expected**

- Reusable tests: <names and levels, or none identified>
- Added tests: <range and scope, or UNKNOWN>
- Test-first: <yes/no and short reason, or UNKNOWN>
- Verification levels: <project names, optionally mapped L0–L4>

## Expected vs Current

- Modules: <expected> → <current>
- Files: <expected count/range> → <actual count and A/M/D paths>
- Verification: <planned> → <actually run / observed>
- Complexity / scope changes: <evidence or none observed>

For at most 40 changed files, list every path with A/M/D. Above 40, fold ordinary paths by directory with file count and additions/deletions, but list each clearly out-of-scope or unusual file separately.

## Evidence and judgment

- **Verified facts:** <source path/section, diff status, test result, or CI link/head>
- **Semantic judgments:** <interpretation of scope, size, complexity, or attention and the evidence used>
- **Unknown / not checked:** <missing evidence; do not present as a result>

## Natural checkpoints (optional; about five lines maximum)

- <Optional advisory moments to call `/devmap` again; omit if not useful.>
