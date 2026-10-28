# REA

**Reverse Engineering Anything — an evidence-first research ecosystem.**

REA is a modular framework for investigating unfamiliar software, technical systems, models and scientific artifacts. It aims to turn opaque inputs into structured, testable understanding by combining existing tools, controlled experiments, provenance and clear statements of uncertainty.

REA is an ecosystem of interoperable projects, not a promise that one agent can automatically reverse-engineer everything.

## Principles

- **Evidence before assertion.** Separate observations, reported claims, interpretations and hypotheses.
- **Reproducibility.** Record inputs, methods, tool versions, configuration and outputs wherever practical.
- **Provenance.** Preserve where an artifact came from and how conclusions were produced.
- **Least privilege.** Treat inspected artifacts as untrusted data. Do not execute code or connect to external systems without an explicit, controlled decision.
- **Tool reuse.** Prefer established open-source tools and narrow adapters over rebuilding mature capabilities.
- **Human review.** Make uncertainty and consequential decisions visible to the operator.
- **Modularity.** Domain specialists should be useful independently and interoperable through documented contracts.

## Project map

| Project | Responsibility |
| --- | --- |
| [rea-core](https://github.com/DerekWiner/rea-core) | Shared artifact, evidence, provenance and experiment contracts |
| [rea-orchestrator](https://github.com/DerekWiner/rea-orchestrator) | Delegation, task routing and coordination across specialists |
| [synthesis-rea](https://github.com/DerekWiner/synthesis-rea) | Cross-domain comparison, hypothesis generation and synthesis |
| Specialist REAs | Domain-specific investigation and adapters, developed as separate repositories |

The project boundaries are intentional. REA investigates and reconstructs; MCP connects tools and data; JEV is a proposed fast triage and routing layer; Alvearium concerns agent identity, permissions and governance. These are distinct responsibilities, and integrations remain future work until implemented and tested.

## Typical investigation flow

1. Register the artifact and record its source.
2. Identify format, boundaries, risks and the question being investigated.
3. Select existing tools and a bounded analysis plan.
4. Run approved analysis or experiments in an appropriate environment.
5. Capture outputs, configuration, versions and hashes where useful.
6. Separate direct observations from interpretations and hypotheses.
7. Validate findings with tests, independent evidence or replication.
8. Publish a structured report with limitations and unresolved questions.

## Current status

REA is at the foundation and architecture stage. This repository establishes the ecosystem's purpose and coordination principles. It does not yet provide a complete reverse-engineering engine, autonomous execution framework or universal artifact decompiler.

Initial development should focus on a small shared evidence contract and one end-to-end specialist workflow before expanding the ecosystem.

## License

The REA project is licensed under the MIT License. See LICENSE. Third-party tools, datasets and artifacts retain their own licenses and usage restrictions.