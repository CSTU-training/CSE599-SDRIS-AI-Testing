# CSE590 Project Realignment — 2026-11-23

> **Status: Proposed course project scope; instructor approval and actual SDRIS integration remain pending.** Source of truth: *CSTU CSE590 — AI & Software Test Automation, Project Assignment*, posted 2026-11-08, due **2026-12-20**.

## Decision / 核心定位

**EN:** The course assignment asks a team of **2–3** to **test an AI application**, not to build a full server failure-analysis product. We propose **Option (c): Testing GenAI Apps**, using the **SDRIS AI analysis module as the System Under Test (SUT)**, subject to instructor approval. The standalone SDRIS product roadmap remains in [the SDRIS repository](https://github.com/telliex/SDRIS).

**中文：** CSE590 的核心是「測試 AI 應用」，而非交付完整 SDRIS 產品。建議選擇作業的 **(c) Testing GenAI Apps**，以 SDRIS 的 AI 診斷分析功能作為受測系統（SUT）。此選題及其介面形式仍需教授確認。

**Proposed title:** *AI Testing and Quality Evaluation of a Generative AI-Based Server Failure Analysis System (SDRIS)*.

## Assignment requirements versus our plan

| Assignment requirement (required unless noted) | Planned evidence | Status |
| --- | --- | --- |
| Choose an AI app and describe its name, URL, features, team, roles | README and bilingual overviews | Scope proposed |
| AI test modeling and analysis, **3D AI test models/decision tables**, complexity | [Test modeling design](test-modeling-design.md), reviewed decision table | Candidate axes only; professor methodology pending |
| AI test cases, collection/generation/augmentation of test data | Versioned test matrix, synthetic logs, ground-truth labels, augmentation provenance | Not implemented |
| AI test scripting and execution (using instructor-provided agentic AI test tool) | Generated scripts, tool provenance and run records | Tool access/workflow unconfirmed |
| AI test results | Actual outputs, versioned evaluation records | Not yet measured |
| AI bug reports and final quality report | Reproduction steps, expected/actual, severity, coverage, test complexity, project costs/budget | Not yet produced |
| **Optional** QoS reporting (10% additional project score) | Performance, reliability, availability, accuracy, correctness | Stretch goal |

The assignment calls the final report's first section "Project induction" (app name/URL, features, members, roles). We will use **Project Introduction** in our draft while preserving those required fields.

## Minimum viable SUT and exclusions

**Required for the proposed demonstration:** a *real*, callable SDRIS AI analysis interface accepting a synthetic server failure log and returning diagnostic output that can be evaluated. Its actual API route/schema must be confirmed from the SDRIS implementation. A mock or simulated AI result must **not** be labeled as a real SUT test result.

**Prioritized AI features:** (1) fault classification; (2) evidence-grounded diagnostic reasoning and uncertainty handling. Log understanding and troubleshooting recommendations are useful extensions only if ready. Prefer a small, reviewed scenario set (e.g., DIMM ECC and NVMe/FIO; normal/incomplete/noisy/conflicting variants) over covering every hardware component prematurely.

**Not required by the course project:** email ingestion, full case/repair workflow, fleet analytics, production BMC access, rack control, complete SDRIS UI, real company log integration. General parser/API/UI regression tests may support the project but should not replace testing the AI features.

## Proposed workflow

1. Analyze selected GenAI capabilities and define test scope.
2. Define the instructor-aligned 3D model and decision table, complexity, coverage targets, and evaluation rules **before** execution.
3. Create wholly synthetic logs and reviewed ground truth; generate and augment data with recorded transformations.
4. Generate tests/scripts with the **instructor-provided agentic AI test tool**, recording tool name/version/configuration and human changes. Python/pytest are **optional supporting infrastructure**, not a substitute for the required tool.
5. Execute against the actual SDRIS SUT; save prompt/input, output, model/app/tool versions when available, expected vs actual, scores and evidence.
6. Report bugs, measured coverage, complexity, effort and budget/cost, and results; optionally assess QoS. **Do not invent measured outcomes.**

## Timebox and checkpoints

- **Nov 23–29:** confirm SUT acceptance, professor's 3D method and tool; freeze small AI feature scope and roles.
- **Nov 30–Dec 6:** model, decision tables, ground truth, controlled synthetic/augmented dataset.
- **Dec 7–13:** connect real SUT, generate and run tests using professor's tool, log results.
- **Dec 14–20:** defect/coverage/complexity/cost/QoS reporting, final review and submission by **Dec 20, 2026**.

**Open confirmation items:** (1) self-developed SDRIS acceptable as the app? (2) 3D model dimensions and adequacy rules? (3) instructor tool access/integration and evidence needed? (4) minimum cases/coverage and grading rubric? (5) whether any presentation date applies separately (the provided assignment specifies the submission date, not a presentation date).

## Security and reproducibility

Public repository data must be wholly synthetic or explicitly approved for public use. Do **not** commit internal MiTAC/Oracle logs, serials, internal IP addresses, credentials, proprietary diagnostics, customer identifiers or confidential screenshots. Preserve synthetic generation provenance and human-reviewed ground truth. Always distinguish **proposed**, **implemented**, **executed**, and **measured** statuses.

## Possible future research (not a course requirement)

The evaluated framework may later inform an IEEE AITest-style research project, but an academic submission is **not** part of CSE590 deliverables. Research questions, baselines and experimental comparisons are separate follow-up work.
