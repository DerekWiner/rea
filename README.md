# REA

**Reverse Engineering Anything, an evidence-first research ecosystem.**

REA is a modular framework for investigating unfamiliar software, technical systems, models and scientific artifacts. It aims to turn opaque inputs into structured, testable understanding through existing tools, controlled experiments, provenance and explicit uncertainty.

REA is an ecosystem of interoperable projects, not a claim that one agent can automatically reverse-engineer everything.

## Principles

- **Evidence before assertion.** Separate observations, reported claims, interpretations and hypotheses.
- **Reproducibility.** Record inputs, methods, tool versions, configuration and outputs where practical.
- **Provenance.** Preserve where artifacts came from and how conclusions were produced.
- **Least privilege.** Treat inspected artifacts as untrusted. Do not execute code or connect to external systems without an explicit, controlled decision.
- **Tool reuse.** Prefer established tools and narrow adapters over rebuilding mature capabilities.
- **Human review.** Make uncertainty and consequential decisions visible.
- **Modularity.** Domain specialists should work independently and interoperate through documented contracts.

## Project map

| Project | Responsibility | Status |
| --- | --- | --- |
| [rea-core](https://github.com/DerekWiner/rea-core) | Shared investigation records and structural validation | Working schema and validator |
| [rea-orchestrator](https://github.com/DerekWiner/rea-orchestrator) | Task validation, explicit worker dispatch, approval gate, audit events and upstream-capture normalization | Runnable local prototype, no live MCP adapter yet |
| [synthesis-rea](https://github.com/DerekWiner/synthesis-rea) | Future comparison and synthesis across investigations | Scaffold |
| [alvearium-commons](https://github.com/DerekWiner/alvearium-commons) | Narrow adapters and reproducibility receipts for existing research tools | Purpose defined, adapter not yet implemented |
| Specialist REAs | Domain-specific investigation and tool adapters | Developed independently |

REA investigates and reconstructs. MCP can provide interfaces to tools and data. JEV is a proposed fast triage and routing layer. Alvearium concerns agent coordination, identity, permissions and governance. These responsibilities are related but distinct, and integrations remain future work until implemented and tested.

## Typical investigation flow

1. Register the artifact and record its source.
2. Identify format, boundaries, risks and the question being investigated.
3. Select existing tools and a bounded analysis plan.
4. Run approved analysis or experiments in an appropriate environment.
5. Capture outputs, configuration, versions and hashes where useful.
6. Separate observations from interpretations and hypotheses.
7. Validate findings with tests, independent evidence or replication.
8. Publish a structured report with limitations and unresolved questions.

## Current status

REA has a working foundation in `rea-core` and a broader set of planned components. It does not yet provide a complete reverse-engineering engine, universal artifact decompiler or fully autonomous investigation runtime.

The next useful milestone is a live, bounded upstream REA adapter that converts native tool results into the tested capture contract, validates records with REA Core, and retains raw evidence. See the [ecosystem roadmap](docs/ecosystem-roadmap.md) for repository boundaries, milestones, setup and automation requirements.

## License

The REA project is licensed under the MIT License. See [LICENSE](LICENSE). Third-party tools, datasets and artifacts retain their own licenses and usage restrictions.
