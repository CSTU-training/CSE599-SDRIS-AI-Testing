# Team 3 — Getting Started

Welcome to the CSE590 SDRIS AI Testing project. You do **not** need server hardware experience to contribute.

## What are we testing?
SDRIS is an in-development tool for analyzing server test logs and suggesting possible fault causes. Our course project evaluates whether its results are correct, supported by evidence, and appropriately cautious when information is incomplete.

## Key terms
- **SUT:** System Under Test — the SDRIS MVP.
- **Test case:** An input scenario with expected behavior.
- **Ground truth:** A reviewed description of what a test case should show.
- **Evidence grounding:** Whether an AI finding cites actual relevant log content.
- **Decision table:** A systematic way to map input conditions to expected outcomes.

## First collaborative tasks
1. Read the [English](project-overview.en.md) or [Chinese](project-overview.zh-TW.md) project overview.
2. Review the existing [README](../README.md), especially sections 7–10 and 14–15.
3. Propose test scenarios: normal logs, clear failures, incomplete evidence, and conflicting evidence.
4. Help turn scenarios into a decision table with expected and forbidden conclusions.
5. Record uncertainties and questions as GitHub Issues.

## Suggested task ownership (to confirm together)
- Technical lead: clarify SDRIS behavior, review expected diagnostic results, and integrate test automation.
- Test/documentation contributor: help design test cases, decision tables, bug templates, and evaluation reports.
- Both: review ground truth, execute tests, interpret outcomes, and prepare the presentation.

## Collaboration rules
- Open an Issue for each bounded task.
- Use a feature branch and Pull Request; do not commit directly to main for substantial changes.
- Keep test data synthetic or explicitly authorized for public release.
- Clearly mark proposed features versus implemented features.
- Ask questions early; no prior server validation expertise is assumed.

## Schedule
Planning and contract: Nov 14–21; modeling: Nov 22–30; automation: Dec 1–7; evaluation: Dec 8–14; final report/demo preparation: Dec 15–20. Dates are planning targets, not evidence of completion.
