# CSE590 Assignment Mapping — Working Checklist

This is a planning checklist based on the existing project README and prior course discussion. Verify all items against the instructor's authoritative assignment and grading rubric.

| Course deliverable | Proposed evidence | Status |
|---|---|---|
| Project scope and SUT | README + bilingual project overview | Documented / needs instructor confirmation |
| AI test modeling | `docs/test-modeling.md` | Planned |
| 3D test decision tables | `docs/3d-decision-tables.md` | Planned; dimensions require instructor confirmation |
| Test cases and datasets | `datasets/synthetic/`, ground-truth labels | Planned |
| Data generation / augmentation | Synthetic generator and transformation log | Planned |
| Automated test scripts | Python, pytest, httpx | Planned; actual API contract unconfirmed |
| AI testing tool usage | Tool usage log and screenshots | Pending instructor tool access |
| Execution results | Versioned reports and run metadata | Planned |
| Bug reports | GitHub Issues + reproducible evidence | Planned |
| Quality evaluation | Correctness, evidence validity, uncertainty, robustness | Planned |
| Coverage and complexity | Test matrix and analysis | Planned |
| Project costs | Effort and resource-cost table | Planned |
| Final report and presentation | Final report + demo | Planned |

## Instructor confirmations needed
1. Is SDRIS, a team member's own GenAI application, an acceptable SUT?
2. What are the formal requirements for the 3D test model and decision tables?
3. How should the instructor-provided agentic AI test tool be used and documented?
4. Which course number should appear on submission materials? The team identifies the project as **CSE590**; the repository URL still includes CSE599.

## Minimum viable demonstration
A small synthetic dataset, a reviewed ground-truth table, at least one real SDRIS testing interface, executable checks, and an evidence-backed evaluation report. If the SDRIS API is not ready, clearly distinguish mock-based framework demonstrations from actual SUT evaluation.
