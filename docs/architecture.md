# REA ecosystem architecture

## Goal

Provide a shared, evidence-first workflow for investigating unfamiliar artifacts without forcing every domain into one monolithic application.

## Responsibility boundaries

### REA

The ecosystem entry point. Defines shared principles, maps projects, documents interfaces and explains how investigations move between components.

### rea-core

Defines common structures for artifacts, evidence, provenance, experiment descriptions and findings. The core should remain small and domain-neutral.

### rea-orchestrator

Coordinates investigation plans and delegates bounded tasks to tools or specialist REAs. It should not bypass specialist safety rules or treat model-generated summaries as verified evidence.

### synthesis-rea

Compares findings from multiple investigations, identifies agreements and conflicts, and proposes cross-domain hypotheses. It must preserve links to supporting evidence and distinguish synthesis from verified conclusions.

### Specialist REAs

Own domain-specific parsing, adapters, analysis methods, validation and fixtures. Examples include cryptography, software auditing, digital hardware, legacy COBOL, materials science, biology and neural-network interpretability.

## Suggested investigation record

A minimal record should capture:

- A stable identifier for the investigation and input artifact
- Artifact origin and acquisition time, if known
- Content hash where applicable
- The question being investigated
- Tools and versions used
- Configuration and relevant parameters
- Observations and output references
- Interpretation and confidence
- Validation performed
- Limitations, unresolved questions and safety notes

The exact machine-readable schema should be defined in rea-core, versioned, and validated with fixtures before being adopted across projects.

## Trust boundaries

Inputs are data, not instructions. A repository, document, model response or artifact may contain malicious instructions or executable content. Parsing should be separated from execution. Execution, network access, credential use and external uploads require explicit policy and appropriate isolation.

Evidence records improve traceability but do not independently establish that an experiment happened as described or that a result is correct.

## Interoperability

Use narrow, documented interfaces. MCP may expose approved tools and resources, but connectivity is not itself authorization or verification. Proposed JEV routing and Alvearium identity or policy integrations should be optional adapters rather than hard dependencies.

## Initial implementation sequence

1. Agree on the minimal evidence and artifact contract in rea-core.
2. Build one deterministic, offline investigation workflow with fixtures.
3. Add a specialist adapter that consumes and emits the contract.
4. Add orchestration only after the specialist interface is stable.
5. Add synthesis once there are multiple evidence-producing workflows.
6. Evaluate reproducibility, failure handling and safety before broadening scope.