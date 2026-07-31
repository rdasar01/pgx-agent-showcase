# PGx-Agent

> A governed multi-agent clinical decision-support copilot for pharmacogenomic analysis, clinical-trial matching, and drug-safety review.

> **Project status:** In development
> **Intended use:** Technical demonstration and portfolio project
> **Clinical status:** Not validated or approved for clinical use

## Overview

**PGx-Agent** is a multi-agent clinical decision-support system designed to assist with personalized clinical-trial matching, pharmacogenomic analysis, and drug-safety review.

The system cross-references patient genomic variants with biomedical evidence, drug-response annotations, adverse drug reaction data, and active clinical trials. It combines hybrid retrieval-augmented generation, specialized agents, schema-constrained outputs, workflow automation, and human-in-the-loop review to produce traceable candidate recommendations.

PGx-Agent is being designed as a Python-based API and will be deployed and evaluated in Google Cloud using relevant public biomedical datasets.

This repository is a public portfolio showcase containing project documentation, a high-level architecture diagram, a synthetic patient profile, and an illustrative structured output. The complete implementation and proprietary system components are maintained separately.

## Business Problem

Clinicians and researchers must cross-reference patient genomic variants across multiple biomedical resources, active clinical trials, and known adverse drug reactions. This process can be time-consuming and difficult to perform consistently.

Conventional keyword matching is often inadequate because star alleles—such as **CYP2D6*4**—must be interpreted in the context of:

* The patient’s diplotype
* Predicted metabolizer phenotype
* Current and proposed medications
* Drug–gene and drug–drug interactions
* Disease context
* Clinical-trial eligibility criteria
* Available evidence quality

PGx-Agent is intended to organize and synthesize this evidence into a structured report for qualified human review.

## Technical Objective

PGx-Agent uses an orchestrator agent to coordinate specialized pharmacogenomic and clinical-trial analysis components.

The proposed workflow includes:

1. Validate the submitted patient profile and analysis request.
2. Delegate pharmacogenomic research to a Variant Analysis Agent.
3. Retrieve relevant studies through a Trial Matching Agent.
4. Combine genomic, eligibility, intervention, and safety constraints.
5. Apply hybrid retrieval and re-ranking to identify relevant candidate trials.
6. Evaluate evidence quality, contradictions, missing information, and potential safety concerns.
7. Return three ranked candidate trials with supporting evidence and uncertainty indicators.
8. Require clinician review before any output is used in a healthcare workflow.

The system is intended to support—not replace—qualified clinical judgment.

## Proposed Data Sources

### PharmGKB and ClinPGx

Curated pharmacogenomic resources connecting genes, variants, phenotypes, medications, diseases, and clinical guidance.

### PGxMine

Pharmacogenomic relationships extracted from biomedical literature.

### ClinicalTrials.gov API

Public clinical-study information, including:

* Study descriptions
* Recruitment status
* Eligibility criteria
* Interventions
* Trial phases
* Study locations
* Sponsor information

Use of each source remains subject to its applicable terms, attribution requirements, and data-use policies.

## Proposed Architecture

### Hybrid Retrieval and Ranking

The retrieval pipeline is designed to combine:

* **Structured filtering** for recruitment status, study phase, eligibility criteria, interventions, and locations
* **Sparse retrieval** for exact biomedical terminology and star-allele identifiers
* **Dense bi-encoder retrieval** for semantic candidate generation
* **Cross-encoder re-ranking** for detailed comparison of patient context, genomic evidence, and trial criteria

This approach is intended to improve retrieval quality when terminology varies between biomedical sources or exact keyword overlap is limited.

### Multi-Agent Workflow

The proposed system includes specialized components for:

* Request routing and validation
* Pharmacogenomic evidence retrieval
* Clinical-trial retrieval
* Eligibility analysis
* Drug-safety analysis
* Evidence synthesis
* Contradiction and uncertainty detection
* Structured report generation

The system will use schema-constrained JSON outputs to represent:

* Trial relevance
* Genomic compatibility
* Eligibility considerations
* Potential drug–gene interactions
* Potential drug–drug interactions
* Evidence provenance
* Confidence indicators
* Safety flags
* Unresolved questions

### Human Oversight and Governance

The proposed governance framework includes:

* Source citations and evidence provenance
* Structured-output validation
* Confidence and evidence-quality indicators
* Safety and uncertainty flags
* Audit logs of agent actions
* Documented escalation conditions
* Human review before downstream use

## Application and Deployment

The application is being designed around a lightweight Python API that exposes the orchestration, retrieval, ranking, and report-generation workflow.

Potential deployment components include:

* Containerized Python services
* Google Cloud deployment
* Managed secret storage
* Logging and monitoring
* Automated evaluation pipelines
* Google Workspace integration through Apps Script
* Role-based access controls

Any integration with clinical documentation would require appropriate privacy, security, compliance, validation, and organizational review before use.

## Evaluation Plan

The project will be evaluated across several dimensions:

* Retrieval precision and recall
* Trial-ranking quality
* Eligibility-constraint coverage
* Citation and evidence accuracy
* Output-schema compliance
* Contradiction detection
* Safety-flag consistency
* Hallucination and unsupported-claim rates
* End-to-end latency
* Reproducibility
* Human-review usability

Evaluation examples in this repository will use synthetic or appropriately public data.

## Public Repository Scope

This repository is a public portfolio showcase for PGx-Agent. It presents the project’s intended purpose, proposed architecture, governance approach, and evaluation strategy without exposing the proprietary implementation.

The repository includes:

* A project overview and technical design summary
* A high-level architecture diagram
* A synthetic patient profile
* A representative structured output example
* Medical, safety, and intellectual-property disclaimers

The repository does not include:

* Production source code
* Proprietary orchestration logic
* Agent prompts or routing instructions
* Retrieval and ranking implementations
* Production API integrations
* Cloud deployment configuration
* Credentials, secrets, or access tokens
* Private evaluation datasets
* Protected health information
* Internal commercial strategy or product roadmaps

## Repository Structure

```text
pgx-agent-showcase/
├── README.md
├── NOTICE.md
├── architecture.png
├── synthetic-patient.json
└── sample-output.json
```

### File Descriptions

* **`README.md`** — Describes the project, business problem, proposed architecture, governance approach, evaluation plan, limitations, and intended use.
* **`NOTICE.md`** — Contains copyright, ownership, and permitted-use information.
* **`architecture.png`** — Provides a high-level visual representation of the proposed system architecture.
* **`synthetic-patient.json`** — Contains a fictional patient profile created solely for demonstration.
* **`sample-output.json`** — Shows an illustrative example of the system’s proposed structured output.

## Security and Data Handling

This public repository does not contain production services, credentials, restricted datasets, or clinical records.

The example files must contain only synthetic or independently public information. Do not include:

* Protected health information
* Personally identifiable information
* Real patient records
* API keys or authentication tokens
* Cloud credentials
* Private endpoints
* Confidential organizational data
* Licensed data that cannot be redistributed

The `synthetic-patient.json` file must represent a fictional individual and must not be derived from an identifiable patient record.

The `sample-output.json` file is illustrative and must not be interpreted as a validated clinical recommendation.

Security, privacy, access control, audit logging, secret management, and regulatory requirements for the complete implementation are outside the scope of this public showcase repository.

## Limitations

This repository documents a proposed and developing system. It does not contain the complete PGx-Agent implementation and cannot independently execute pharmacogenomic analysis, retrieve active clinical trials, or generate patient-specific recommendations.

The architecture, workflows, and sample outputs represent the intended system design and may change as development and evaluation continue.

The included examples have several limitations:

* The patient profile is synthetic.
* The sample output is illustrative rather than clinically validated.
* Trial availability and recruitment status may change over time.
* Biomedical evidence may be incomplete, conflicting, or updated after the examples are created.
* The examples do not establish clinical eligibility, treatment suitability, efficacy, or safety.
* Performance claims should not be inferred unless supported by documented evaluation results.
* The public repository does not demonstrate the complete proprietary retrieval, ranking, orchestration, or safety-validation process.

PGx-Agent remains an experimental decision-support project. Its outputs must not be used as a substitute for qualified clinical judgment, validated pharmacogenomic interpretation, or review of authoritative biomedical sources.

## Medical Disclaimer

PGx-Agent is not a medical device and is not intended to diagnose, treat, cure, prevent, or independently manage any disease or medical condition.

This project does not provide medical advice. Its outputs must not be used as a substitute for professional clinical judgment, validated pharmacogenomic interpretation, institutional review, or consultation with qualified healthcare professionals.

No clinical decision should be made solely from information generated by this project.

## Repository Access and Licensing

This public repository is provided for portfolio review and informational purposes.

No open-source license is granted unless a specific file or directory states otherwise. The absence of an open-source license means that permission is not granted to copy, modify, distribute, sublicense, commercialize, or create derivative works from the repository’s contents.

Viewing this repository does not grant ownership or intellectual-property rights in PGx-Agent, its documentation, designs, code, workflows, or related materials.

Third-party software, APIs, datasets, and trademarks remain subject to their respective licenses, terms, and ownership rights.

## Copyright

Copyright © 2026 **Raji Dasari**. All rights reserved.

PGx-Agent and the original materials contained in this repository are proprietary. No permission is granted to reproduce, modify, distribute, sublicense, commercialize, or create derivative works without prior written authorization from the copyright owner.

The complete proprietary implementation is not included in this public repository.

## Contact

For employment-related discussions, technical interviews, demonstrations, or authorized access inquiries:

* **Name:** Raji Dasari
* **LinkedIn:** https://www.linkedin.com/in/rajidasari/
* **Email:** RajiDasari@hotmail.com
