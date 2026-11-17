# CSE590 Project Overview (English)

## Project Title
AI-Based Test Modeling and Quality Evaluation of the SDRIS Server Diagnostic System

**Course:** CSTU CSE590 — AI & Software Test Automation  
**Team:** Team 3  
**Target submission:** December 20, 2026  
**Target presentation:** December 21, 2026

## Summary
This project uses SDRIS (Server Diagnostic & Reliability Intelligence System) as the System Under Test (SUT). SDRIS is a server diagnostic platform under development that aims to help engineers analyze test logs, identify abnormal events, organize supporting evidence, and generate AI-assisted troubleshooting recommendations.

The course project **does not rebuild SDRIS**. Instead, it designs test models, datasets, and automated evaluations to assess the MVP's functional correctness, AI diagnostic quality, evidence reliability, and robustness.

## Planned MVP Testing Workflow
1. Prepare synthetic server diagnostic logs.
2. Submit logs through an available SDRIS interface (the actual API contract is not yet confirmed).
3. Check parsing, fault detection, and diagnostic outputs.
4. Compare responses against ground truth, evidence references, and expected uncertainty handling.
5. Produce test records, bug reports, quality metrics, and a final report.

## Testing Scope
- Black-box / white-box and API testing
- 3D AI test models and decision tables
- Synthetic test datasets and controlled augmentation
- Python / pytest test automation
- Diagnostic correctness, evidence validity, unsupported claims, and uncertainty handling
- Coverage, complexity, project cost, and quality reporting

## Initial Scenario
NVMe/FIO storage failure is a candidate first end-to-end scenario. ECC, network, and boot issues may be added based on actual SDRIS MVP availability. These are **planned scenarios**, not claims of implemented functionality.

## Team Collaboration
Members familiar with server validation can review diagnostic scenarios and ground truth. All members can contribute to test modeling, case design, dataset annotation, execution records, defect tracking, and quality reporting. Specific responsibilities will be agreed upon by the team.

## Current Status and Open Questions
The repository's README primarily describes a proposed framework. Python test scripts, example APIs, and a complete diagnostic workflow must not be assumed operational. The proposed 3D dimensions, instructor-provided agentic AI testing tool, and approval to test a self-developed SUT require confirmation.

**Data safety:** Only synthetic or explicitly authorized public data may be committed. Do not upload internal logs, customer data, real system identifiers, IPs, credentials, or proprietary scripts.

## Related Documents
- [中文介紹](project-overview.zh-TW.md)
- [Team Onboarding](team-onboarding.md)
- [Assignment Mapping](assignment-mapping.md)
- [Full Project README](../README.md)
