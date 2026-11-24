# CSE590 — SDRIS AI Testing & Quality Evaluation

> **2026-11-23 course scope update:** This repository is the **CSE590 AI testing/evaluation project**, not the full SDRIS application. We propose **Option (c) — Testing GenAI Apps** with the SDRIS AI analysis module as the **System Under Test**, pending Professor Gao's approval. The course requires **3D AI test modeling and decision tables**, test cases and synthetic/augmented datasets, **scripts generated with the instructor-provided agentic AI test tool**, actual test results, bug reports, and a quality report covering **costs/budget, complexity and coverage**. Optional QoS testing may earn **10% extra**. Due **2026-12-20**. No implementation or measurements should be inferred from these planning documents. See [course realignment](docs/course-realignment.md), [model draft](docs/test-modeling-design.md), [assignment mapping](docs/assignment-mapping.md), and [report outline](docs/final-report-outline.md). The existing CSE599 repository name is a legacy URL; course identity here is CSE590. The presentation date mentioned below is an existing team plan and is **not specified in the supplied assignment PDF**.

**Course:** CSE590 — AI & Software Test Automation  
**Institution:** California Science and Technology University (CSTU)  
**Instructor:** Professor Jerry Gao  
**Members:** Chienyu Chiu, Lijun Li
**Project Due Date:** December 20, 2026  
**Presentation:** December 21, 2026  
**Status:** Planning / Initial Implementation

## 1. Project Overview

This project applies software testing and AI quality evaluation techniques to [**SDRIS (Server Diagnostic & Reliability Intelligence System)**](https://github.com/telliex/SDRIS), a Next.js-based application designed to assist engineers with server test log analysis and failure diagnosis.

SDRIS serves as the **System Under Test (SUT)**.

The objective of this course project is not to develop another server diagnostic platform, but to systematically evaluate the functional correctness, reliability, and diagnostic quality of the SDRIS MVP.

The project combines:

- Conventional software testing
- Black-box and white-box testing
- API and UI test automation
- AI test modeling and test case design
- AI test data generation and augmentation
- Automated AI response evaluation
- Test coverage and quality reporting

### Project Title

**AI-Based Test Modeling and Automated Quality Evaluation of SDRIS Server Log Diagnosis**

### Research Question

How can systematic software testing and AI evaluation techniques measure the correctness, reliability, and evidence-grounding quality of an AI-assisted server log diagnosis system?

---

## 2. Relationship to SDRIS

SDRIS is the primary application under development.

This course project provides an independent testing and evaluation framework for its MVP.

| SDRIS MVP | CSE599 Testing Project |
|---|---|
| Server log ingestion | Input validation testing |
| Log parsing | Parser correctness testing |
| Rule-based detection | Rule coverage and boundary testing |
| AI failure analysis | Diagnostic accuracy evaluation |
| Evidence extraction | Evidence-grounding evaluation |
| Diagnosis report | API and UI testing |
| Application workflow | End-to-end testing |

Existing development tests should be reused whenever possible.

The CSE599 project focuses on additional testing models, AI-specific evaluation, test evidence, and quality reports.

---

## 3. System Architecture

```text
                  SERVER TEST LOGS
              (Synthetic / Authorized)
                          |
                          v
              +-----------------------+
              |       SDRIS MVP       |
              |        Next.js        |
              +-----------------------+
                          |
          +---------------+---------------+
          |               |               |
          v               v               v
     Log Parser      Rule Engine      AI Analysis
          |               |               |
          +---------------+---------------+
                          |
                          v
                Diagnosis Result
                          |
                +---------+---------+
                |                   |
                v                   v
              REST API          Web UI
                |                   |
                v                   v
       +----------------------------------+
       |      CSE599 Test Framework       |
       +----------------------------------+
       |                                  |
       |  Python / pytest                 |
       |  API Testing                     |
       |  AI Response Evaluation          |
       |  Test Data Generation            |
       |  Robustness Testing              |
       |  UI / E2E Test Result Integration|
       |                                  |
       +----------------------------------+
                          |
                          v
                 Quality Metrics
                          |
                          v
                 Final Test Report
```

### Architectural Principles

1. Keep the SDRIS application and course testing framework logically separated.
2. Use public application APIs for black-box testing.
3. Reuse existing development tests instead of duplicating equivalent tests.
4. Keep AI evaluation datasets independent from implementation logic.
5. Maintain traceability between test requirements, cases, executions, and results.
6. Use synthetic or explicitly authorized test data only.

---

## 4. SDRIS MVP Scope

The MVP is expected to provide three primary capabilities.

### 4.1 Log Upload and Parsing

The system accepts server diagnostic logs and extracts structured information.

Potential supported log types include:

- IPMI System Event Log (SEL)
- BMC diagnostic logs
- Test execution summaries
- Linux system logs
- Test-specific diagnostic logs

Expected extracted fields may include:

- Test section
- Timestamp
- Component
- Event type
- Severity
- PASS/FAIL status
- Source log reference

### 4.2 AI-Assisted Failure Analysis

The AI analysis module evaluates structured diagnostic information and identifies potential causes of server test failures.

Expected outputs include:

- Suspected issue category
- Supporting evidence
- Possible root causes
- Recommended troubleshooting actions
- Uncertainty or insufficient-evidence indicators

The system must distinguish observed facts from diagnostic hypotheses.

### 4.3 Diagnosis Report

The application displays analysis results for engineering review.

Reports should include:

- Diagnostic summary
- Identified findings
- Source log references
- Suggested next steps
- Analysis status

The MVP does not automatically approve hardware replacement or declare that a server is safe to release.

### Out of Scope

The following capabilities are excluded from the initial course project:

- Real-time server hardware control
- Automated hardware repair
- Multi-agent orchestration
- Production BMC/IPMI access
- Rack-level validation
- SAT execution-time optimization
- Production failure-risk prediction
- Full-scale cross-server statistical anomaly detection

These may be considered for future SDRIS development.

---

## 5. Technology Stack

| Layer | Technology | Purpose |
|---|---|---|
| Application | Next.js / TypeScript | SDRIS MVP |
| Unit testing | Vitest | Functional correctness |
| Component testing | React Testing Library | UI component behavior |
| E2E testing | Playwright | User workflows |
| Course automation | Python | Independent test framework |
| Test execution | pytest | Automated testing |
| HTTP client | httpx | API testing |
| Test data | JSON / JSONL | Fixtures and expected results |
| Data analysis | pandas | Test result analysis |
| Quality reporting | pytest reports / custom scripts | Evaluation metrics |
| Version control | Git / GitHub | Source and test artifact management |

These are proposed technologies and may be adjusted based on the SDRIS implementation and course tools.

---

## 6. Repository Structure

```text
CSE599-SDRIS-AI-Testing/
|
├── README.md
├── pyproject.toml
├── .env.example
├── .gitignore
|
├── docs/
│   ├── project-proposal.md
│   ├── requirements.md
│   ├── test-strategy.md
│   ├── test-modeling.md
│   ├── 3d-decision-tables.md
│   ├── evaluation-criteria.md
│   └── presentation-outline.md
|
├── config/
│   └── evaluation.yaml
|
├── datasets/
│   ├── synthetic/
│   │   ├── normal/
│   │   ├── memory/
│   │   ├── storage/
│   │   └── network/
│   |
│   ├── augmented/
│   └── ground_truth.jsonl
|
├── src/
│   └── cse599_testing/
│       ├── api_client.py
│       ├── dataset_loader.py
│       ├── evaluator.py
│       ├── metrics.py
│       └── report_generator.py
|
├── tests/
│   ├── functional/
│   │   ├── test_api.py
│   │   └── test_input_validation.py
│   |
│   ├── ai_evaluation/
│   │   ├── test_diagnosis.py
│   │   ├── test_evidence.py
│   │   ├── test_uncertainty.py
│   │   └── test_consistency.py
│   |
│   └── robustness/
│       ├── test_missing_logs.py
│       ├── test_conflicting_logs.py
│       └── test_noisy_inputs.py
|
├── scripts/
│   ├── generate_synthetic_data.py
│   ├── run_evaluation.py
│   └── generate_report.py
|
├── reports/
│   ├── test-results/
│   ├── bug-reports/
│   └── final/
|
└── .github/
    └── workflows/
        └── tests.yml
```

### Repository Responsibilities

**SDRIS repository**

Contains the application source code, components, application services, and development tests.

**CSE599 repository**

Contains the independent testing framework, AI test models, datasets, evaluation scripts, test reports, and course deliverables.

---

## 7. Testing Strategy

The testing strategy is divided into four layers.

### Layer 1 — Functional Testing

Objective: Verify that SDRIS functions correctly under defined input conditions.

Test areas:

- Valid and invalid log uploads
- Missing required fields
- Unsupported log formats
- Parser correctness
- API response validation
- Rule-based detection behavior
- Error handling

Existing SDRIS unit and integration tests may provide supporting evidence.

### Layer 2 — UI and End-to-End Testing

Objective: Verify user-facing application workflows.

Example scenario:

1. Open SDRIS.
2. Upload a synthetic server diagnostic log.
3. Start AI analysis.
4. Wait for the result.
5. Review the diagnosis report.
6. Confirm that supporting evidence is displayed.

Playwright is the proposed automation tool.

### Layer 3 — AI Functional Evaluation

Objective: Evaluate whether the AI produces accurate, evidence-supported diagnoses.

Primary evaluation dimensions:

- Diagnostic correctness
- Evidence grounding
- Completeness
- Uncertainty handling
- Unsupported-claim rate

### Layer 4 — AI Robustness Testing

Objective: Determine whether the AI behaves appropriately under incomplete, noisy, or conflicting inputs.

Example scenarios:

- Missing SEL logs
- Incomplete timestamps
- Repeated events
- Conflicting status indicators
- Unrelated diagnostic messages
- Normal logs without actual faults
- Multiple simultaneous fault indicators

---

## 8. Proposed 3D AI Test Model

The course requires AI test modeling and 3D decision tables.

The following model is a preliminary proposal and must be aligned with the instructor's formal 3D modeling methodology.

### Dimension 1 — Diagnostic Scenario

- Normal / PASS
- Memory error
- Storage error
- Network error
- Boot or connection failure
- Multiple related anomalies

### Dimension 2 — Input Data Quality

- Complete
- Partial
- Missing critical information
- Noisy
- Conflicting

### Dimension 3 — Expected AI Behavior

- Identify supported diagnostic findings
- Provide valid evidence references
- Recommend appropriate next steps
- Express uncertainty when necessary
- Avoid unsupported conclusions

### Example Decision Table

| Test ID | Scenario | Input Quality | Expected Behavior |
|---|---|---|---|
| TC-001 | Uncorrectable ECC | Complete | Identify serious memory error and cite evidence |
| TC-002 | Correctable ECC | Complete | Avoid unsupported hardware-failure conclusion |
| TC-003 | SSH timeout | Partial | Identify possible causes and acknowledge uncertainty |
| TC-004 | Normal PASS | Complete | Do not fabricate a failure |
| TC-005 | Memory error | Missing SEL | Identify insufficient supporting evidence |
| TC-006 | Boot failure | Conflicting | Report conflicting observations |
| TC-007 | Multiple anomalies | Noisy | Separate relevant and irrelevant evidence |

A full decision table and test complexity analysis will be developed during the AI test modeling phase.

---

## 9. Test Data Design

All public repository datasets must be synthetic or explicitly approved for release.

### Data Categories

**Normal Cases**

Logs containing no known diagnostic failures.

**Explicit Failure Cases**

Logs containing clearly defined errors such as uncorrectable ECC events, storage failures, or connection timeouts.

**Ambiguous Cases**

Logs containing observations that support multiple possible explanations.

**Incomplete Cases**

Logs with missing sections, truncated messages, or unavailable evidence.

**Augmented Cases**

Controlled variations of existing synthetic cases, including:

- Timestamp changes
- Event reordering where semantically valid
- Additional irrelevant log messages
- Repeated events
- Missing fields
- Formatting variations

Data augmentation must preserve the intended ground truth unless a new label is explicitly assigned.

### Ground Truth

Each test case should define:

- Case ID
- Input log files
- Expected finding categories
- Required evidence
- Forbidden conclusions
- Acceptable uncertainty behavior
- Severity, when supported

Ground-truth labels should be reviewed before use in final quality evaluation.

---

## 10. AI Evaluation Metrics

The project will evaluate AI behavior using predefined criteria.

| Metric | Description |
|---|---|
| Diagnostic Precision | Proportion of predicted findings that are correct |
| Diagnostic Recall | Proportion of expected findings detected |
| Evidence Validity Rate | Proportion of cited evidence references that are valid |
| Unsupported Claim Rate | Proportion of evaluated claims lacking sufficient evidence |
| False Positive Rate | Proportion of negative cases incorrectly flagged |
| Abstention Appropriateness | Correct handling of insufficient evidence |
| Response Latency | Time required to complete an analysis |
| Test Coverage | Coverage of defined test conditions |

Not all metrics need to be included in the initial implementation.

The first evaluation will prioritize diagnostic correctness, evidence validity, and uncertainty handling.

### Rule-Based Baseline

Where applicable, AI results will be compared against a deterministic rule-based baseline.

This helps determine whether AI provides additional value beyond explicit error matching and predefined thresholds.

### Repeated Evaluation

Selected cases may be executed multiple times to assess response variability.

Evaluation must account for the possibility that generative AI responses are nondeterministic.

---

## 11. Proposed API Contract

The testing framework will interact with SDRIS through a stable API.

The following is a proposed contract, not a confirmed SDRIS implementation.

### Request

`POST /api/analyze`

```json
{
  "case_id": "TC-001",
  "logs": [
    {
      "type": "sel",
      "content": "Synthetic diagnostic log content"
    }
  ]
}
```

### Response

```json
{
  "analysis_id": "analysis-001",
  "status": "completed",
  "findings": [
    {
      "category": "MEMORY_ERROR",
      "summary": "Uncorrectable ECC event detected",
      "evidence": [
        {
          "log_type": "sel",
          "line": 12
        }
      ],
      "recommended_actions": [
        "Review the affected memory channel"
      ]
    }
  ],
  "uncertainty": "Further hardware validation is required"
}
```

The actual API contract must be finalized against the SDRIS MVP before implementing integration tests.

---

## 12. Test Automation Workflow

```text
Load Test Dataset
        |
        v
Select Test Cases
        |
        v
Submit Logs to SDRIS API
        |
        v
Collect AI Responses
        |
        v
Validate Response Schema
        |
        v
Evaluate Diagnosis and Evidence
        |
        v
Calculate Quality Metrics
        |
        v
Generate Test Results
        |
        v
Produce Quality Report
```

### Execution Principles

- Every execution must record the test case ID.
- Results should preserve the model and application version when available.
- AI responses should be saved for reproducible review.
- Automated checks should be distinguished from human-reviewed judgments.
- Failed test cases should include expected and actual behavior.
- Test scripts should be runnable independently of the SDRIS source code.

---

## 13. Development Setup

The following commands describe the planned Python testing environment. They will become operational after the project dependencies and scripts are implemented.

### Requirements

- Python 3.11+
- Running SDRIS MVP
- Access to the SDRIS test API
- Synthetic test datasets

### Installation

```bash
git clone <repository-url>
cd CSE599-SDRIS-AI-Testing

python3 -m venv .venv
source .venv/bin/activate

pip install -e ".[dev]"
```

### Environment Configuration

Create `.env` using `.env.example`.

```dotenv
SDRIS_BASE_URL=http://localhost:3000
SDRIS_ANALYZE_PATH=/api/analyze
EVALUATION_DATASET=datasets/ground_truth.jsonl
```

### Run Tests

```bash
pytest tests/ -v
```

### Generate Evaluation Report

```bash
python scripts/run_evaluation.py
python scripts/generate_report.py
```

These commands are implementation targets and are not yet verified.

---

## 14. Course Deliverables

The project is designed to address the assignment's required outputs.

### Required

- AI Test Modeling and Analysis
- 3D AI Test Decision Tables
- Test Cases and Test Datasets
- Data Generation and Augmentation
- Automated Test Scripts
- AI Test Execution Results
- AI Bug Reports
- Final Quality Report
- Test Coverage and Complexity Analysis
- Project Cost Analysis
- Project Presentation and Demo

### Optional Quality-of-Service Evaluation

Potential additional metrics:

- Performance
- Reliability
- Availability
- Accuracy
- Correctness

The assignment identifies QoS evaluation as an optional opportunity for extra credit.

### Instructor-Provided AI Testing Tool

The course assignment states that an agentic AI testing tool will be provided.

Its role in test modeling, test generation, augmentation, and execution must be confirmed and documented.

This repository will preserve evidence of the tool's usage where required.

---

## 15. Implementation Roadmap

### Phase 0 — Scope and Contract

**Target: November 14–21**

- [ ] Confirm SDRIS MVP scope
- [ ] Confirm instructor approval for testing a self-developed GenAI application
- [ ] Confirm individual or group project requirements
- [ ] Define SDRIS API contract
- [ ] Prepare synthetic sample logs

### Phase 1 — Test Modeling

**Target: November 22–30**

- [ ] Define AI testing requirements
- [ ] Design 3D test model
- [ ] Create decision tables
- [ ] Define expected results
- [ ] Establish evaluation criteria

### Phase 2 — Test Automation

**Target: December 1–7**

- [ ] Implement Python API client
- [ ] Implement dataset loader
- [ ] Implement functional test cases
- [ ] Implement AI evaluation tests
- [ ] Implement controlled data augmentation

### Phase 3 — Quality Evaluation

**Target: December 8–14**

- [ ] Execute test suite
- [ ] Record results
- [ ] Identify AI behavior defects
- [ ] Calculate quality metrics
- [ ] Compare with rule-based baseline where applicable

### Phase 4 — Final Delivery

**Target: December 15–20**

- [ ] Complete test coverage analysis
- [ ] Complete quality report
- [ ] Prepare bug reports
- [ ] Prepare presentation
- [ ] Rehearse demonstration
- [ ] Submit project

**Presentation: December 21, 2026**

---

## 16. Git and Commit Strategy

Development should use small, feature-focused commits.

Recommended commit sequence:

```text
docs: initialize project README and scope
chore: configure Python testing environment
docs: define AI test model and decision tables
test: add synthetic diagnostic datasets
feat: implement SDRIS API test client
test: add functional API test cases
test: add AI diagnosis evaluation
test: add evidence-grounding evaluation
test: add robustness test scenarios
feat: implement quality metrics
feat: generate automated quality reports
docs: complete final project report
```

Each commit should represent one coherent change.

---

## 17. Security and Data Privacy

This project must not expose confidential company information.

Public GitHub content must not contain:

- Internal server IP addresses
- BMC credentials
- Customer information
- Production system identifiers
- Proprietary diagnostic scripts
- Internal company test logs without authorization
- Confidential hardware configurations

Synthetic datasets should reproduce diagnostic behavior without copying restricted operational data.

The testing framework must not directly connect to company production servers.

---

## 18. Expected Outcomes

By the end of the course, the project aims to demonstrate:

1. A systematic AI test model for server diagnostic analysis.
2. Reusable functional and AI evaluation test cases.
3. Automated execution of diagnostic test datasets.
4. Quantitative evaluation of AI diagnostic quality.
5. Traceable test results and bug reports.
6. A documented quality assessment of the SDRIS MVP.

The project does not assume that AI diagnoses are always correct or that AI can replace engineering judgment.

The goal is to establish measurable evidence about the reliability and limitations of AI-assisted server log analysis.

---

## 19. Future Work

Potential extensions include:

- Cross-stage anomaly detection
- Historical server comparison
- Repair and retest correlation
- Real-time test monitoring
- Multi-agent diagnostic workflows
- Integration with server validation pipelines
- AI regression testing in CI/CD

These extensions belong to the broader SDRIS roadmap and are not required for the initial CSE599 project.

---

## 20. References

- CSTU — CSE599 AI & Software Test Automation Syllabus, November 2026
- CSTU — AI & Software Test Automation Project Assignment, November 2026
- SDRIS — Server Diagnostic & Reliability Intelligence System (project under development)

**Note:** The syllabus identifies the course as CSE599, while the project assignment labels it CSE590. The official course identifier should be confirmed with the instructor.

---

## Project Status

**Current Phase:** Planning and MVP integration

This README describes the proposed architecture and evaluation methodology. Implementation status and measured results will be updated as development progresses.
