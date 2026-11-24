# Candidate AI Test Modeling & 3D Decision Table — DRAFT

**IMPORTANT:** The assignment explicitly demands **3D AI test models and 3D decision tables**, but does **not** define their axes, notation, adequacy criteria or coverage method. The design below is a **team proposal**; do not claim it is Professor Gao's formal 3D methodology until confirmed.

## Target AI capabilities
- **AF-01:** Failure classification (e.g., Memory vs Storage).
- **AF-02:** Evidence-grounded diagnostic analysis (findings cite relevant source lines).
- **AF-03:** Uncertainty handling (insufficient/conflicting evidence does not become confirmed RCA).
- Optional: log summarization and recommended next diagnostic steps.

## Candidate 3D dimensions

| Dimension | Meaning | Suggested levels |
| --- | --- | --- |
| X — AI capability | Which behavior is evaluated? | Classification, evidence grounding, uncertainty |
| Y — Fault scenario | Which domain/condition? | DIMM corrected ECC, NVMe throughput anomaly, no-fault/normal |
| Z — Input quality | How is evidence presented? | Complete, incomplete, noisy, conflicting |

These are **not official axes**. A decision table maps each valid (X,Y,Z) combination to an expected result and a prohibited conclusion.

## Example candidate decision table (illustrative; review before use)

| ID | X | Y | Z | Required outcome | Disallowed outcome |
| --- | --- | --- | --- | --- | --- |
| R-01 | Classification | DIMM corrected ECC | Complete | Classify as memory-related and identify observed ECC event | Report storage fault |
| R-02 | Evidence | DIMM corrected ECC | Complete | Reference synthetic ECC line and location | Fabricate unseen log lines |
| R-03 | Uncertainty | DIMM corrected ECC | Incomplete | Distinguish observation from root-cause hypothesis | State failing DIMM definitely proven |
| R-04 | Classification | NVMe throughput anomaly | Noisy | Recognize the observed throughput failure relative to provided threshold | Conclude SSD defective solely from low bandwidth |
| R-05 | Evidence | Normal/no-fault | Complete | Say no fault evidence in supplied data | Hallucinate a fault |
| R-06 | Uncertainty | DIMM corrected ECC | Conflicting | Flag contradictory signals; recommend checks | Silently choose a confirmed RCA |

**Important domain distinction:** A log line stating *fault certainty 100%* does not alone establish physical root cause or replacement action. Corrected ECC events are not automatically proof that a particular DIMM must be replaced.

## Test complexity and traceability

For an initial proposal with X=3, Y=3, Z=4, the unfiltered full-factorial count is **3 × 3 × 4 = 36 combinations**. This is a *planning ceiling*, not a claim of 36 valid cases or executions. Remove invalid combinations with reasons; mark which combinations are selected, generated, executed, passed, failed or blocked.

For GenAI variability, repeat a selected subset (e.g., 3 trials) under controlled versions/parameters and analyze consistency. Separate deterministic response-schema assertions from semantic assessment requiring ground truth/human review.

Minimum traceability per case:
`requirement_id -> model_cell_id -> case_id -> dataset_id + ground_truth_version -> generated_script/tool_version -> run_id -> raw_output -> evaluation -> bug_id (if any)`.

## Evaluation design (proposed, not assignment-prescribed)

| Metric | Operational definition |
| --- | --- |
| Classification accuracy | Correct fault category / cases with an applicable known category |
| Grounding rate | Supported diagnostic claims / scored diagnostic claims (human-reviewed sample) |
| Unsupported-claim rate | Claims unsupported by supplied evidence / scored claims |
| Uncertainty handling | Cases correctly signaling insufficient/contradictory evidence / applicable cases |
| Coverage | Executed valid 3D model cells / selected valid cells (also report exclusions) |
| Reliability | Repeated-case agreement or stability, with a declared method |
| Latency / cost | End-to-end response time; run count, effort and token/API spend if available |

Define severity and pass/fail **before** execution. Serious ungrounded conclusions should be separately flagged rather than masked by an aggregate weighted score. Keep all illustrative numbers clearly labeled as illustrative.

## Open instructor confirmations
1. Are the chosen axes and decision table representation acceptable?
2. Does the instructor-provided agentic test tool generate the official modeling/table representation?
3. What are the desired adequacy metrics, minimum cases and augmentation methodology?
4. Which AI evaluation/rubric criteria are expected?
