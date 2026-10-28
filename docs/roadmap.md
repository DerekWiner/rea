# REA roadmap

This roadmap describes intended work, not completed capabilities.

## Phase 1 — Define the contract

- [ ] Agree on artifact, evidence, finding and provenance fields in rea-core.
- [ ] Define schema versioning and compatibility rules.
- [ ] Add small synthetic fixtures and validation tests.
- [ ] Document the difference between reported claims, observed output and independently verified results.

## Phase 2 — Prove one workflow

- [ ] Select one narrow, useful investigation from a specialist REA.
- [ ] Support local input and offline processing first.
- [ ] Record configuration, tool versions and output hashes where useful.
- [ ] Produce a structured report with explicit limitations.
- [ ] Test malformed inputs and failure cases.

## Phase 3 — Interoperate

- [ ] Add a second specialist using the same core contract.
- [ ] Test whether artifacts and findings can be consumed without custom glue.
- [ ] Document any domain-specific extensions.
- [ ] Avoid centralizing specialist logic in the ecosystem repository.

## Phase 4 — Coordinate and synthesize

- [ ] Define bounded task interfaces for rea-orchestrator.
- [ ] Add task status, timeout, retry and error-reporting behavior.
- [ ] Preserve provenance through delegated work.
- [ ] Add synthesis-rea comparisons that link every material conclusion to evidence.

## Phase 5 — Evaluate responsibly

- [ ] Create reproducible benchmark cases.
- [ ] Measure accuracy, coverage, cost, latency and failure rates where applicable.
- [ ] Record human review and independent replication separately.
- [ ] Audit execution boundaries, data handling and external service use.

## Explicit non-goals for the initial stage

- A universal autonomous decompiler
- Automatically executing arbitrary artifacts
- Treating model-generated conclusions as ground truth
- Replacing every mature domain-specific tool
- Requiring MCP, JEV, a particular model provider or blockchain integration