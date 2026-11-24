# CSE590 Assignment Mapping — Revised 2026-11-23

**Source:** CSTU CSE590 *AI & Software Test Automation — Project Assignment*, posted Nov 8, 2026. **Deadline: Dec 20, 2026. Team: 2–3 members.**

**Proposed project option:** (c) Testing GenAI Apps. **SUT:** SDRIS AI failure-analysis module, pending instructor approval. The course evaluates an AI application; it does not require developing the full SDRIS product.

| Assignment requirement | Proposed evidence | Current status |
| --- | --- | --- |
| App name, URL, AI features, members and roles | README, bilingual overviews, [report outline](final-report-outline.md) | Draft; roles and SUT URL to confirm |
| AI test modeling, **3D AI test decision tables**, complexity | [Proposed modeling design](test-modeling-design.md), reviewed model and decision table | Draft; professor's formal 3D approach unconfirmed |
| AI test cases and datasets | Model-linked cases, reviewed ground truth, synthetic logs | Planned |
| Data collection, generation and augmentation | Synthetic generator, transformation/provenance log | Planned |
| Generated test scripts **using instructor-provided AI test tool** | Tool-generated scripts and usage evidence | Tool not yet confirmed |
| Test execution and results | Versioned real SUT input/output, evaluation scores | Not yet executed |
| Bug reports | Reproduction details, expected/actual, evidence | Planned |
| Final quality report | Test outcomes, project **costs and budget**, **complexity**, **coverage** | Planned |
| Optional QoS report (**extra 10%**) | Performance, reliability, availability, accuracy, correctness | Stretch |

**Exactly stated deliverables:** AI Test Modeling and Analysis and 3D AI test decision tables; AI test cases and test data sets; AI test results; AI bug reports and quality report.

## Questions for Professor Gao
1. May we test an in-development team-built GenAI application such as SDRIS? Is API-based testing acceptable?
2. What are the professor's **3D AI test model** axes, decision-table conventions, adequacy and complexity methods?
3. How do we access and document the professor-provided **agentic AI test tool**?
4. Are there minimum test cases, coverage criteria or tool-specific evidence requirements?
5. Is a presentation date set separately? The supplied assignment only states the submission deadline.

## Scope and safety
Prioritize AI classification, evidence-grounded reasoning and uncertainty; keep ordinary parser/UI checks secondary. Use **synthetic or explicitly public/authorized** data only. Do not commit real production logs, IP addresses, serials, credentials or customer data. Never describe proposed or mocked outputs as actual SDRIS test measurements.

See: [Course Realignment](course-realignment.md) · [Test Modeling Draft](test-modeling-design.md) · [Final Report Outline](final-report-outline.md).
