# REA ecosystem roadmap

This roadmap defines a practical sequence for evolving the repositories as one evidence-driven system. It distinguishes code that exists from work that still needs implementation.

## Current repository boundaries

- **Upstream REA (morluto/rea)** supplies the external reverse-engineering MCP server, CLI, guided investigation workflows and target-specific tool integrations.
- **REA (this repository)** defines the ecosystem, principles, project boundaries and integration sequence.
- **REA Core** owns the versioned investigation record and structural/reference validator.
- **REA Orchestrator** owns task envelopes, explicit worker registration, local approval gates, dispatch outcomes and audit events. It now includes a synthetic upstream-capture normalizer and a CI test against REA Core.
- **Synthesis-REA** should compare multiple validated investigation records, identify agreement and conflict, and preserve citations to source findings.
- **Alvearium Commons** should hold narrow adapters, reproducibility receipts and evaluation interfaces, rather than duplicate domain logic.
- **Specialist REAs** should own domain-specific methods, tool adapters and validation criteria. Crypto-REA and Bio-REA are candidate first specialists.

## Non-negotiable contract

Every integration should preserve:

1. Artifact identity and provenance, including checksums where practical.
2. Tool/provider name, version, configuration and execution mode.
3. Distinctions between direct observations, reported claims, interpretations, hypotheses and independent verification.
4. Finding-to-evidence references.
5. Failed runs, missing capabilities, uncertainty and unresolved questions.
6. Raw outputs or stable references to them, subject to privacy, retention and licensing restrictions.

Schema validity is necessary but not sufficient. It does not prove that an experiment ran or that a finding is true.

## Milestones

### 1. Repeatable developer setup

- Create a workspace containing rea, rea-core and rea-orchestrator.
- Install Python, Git and a Node.js version supported by the selected upstream REA release.
- Run each repository's tests.
- Install upstream REA in a development environment and connect one supported agent client.
- Use only a harmless test application or synthetic target at first.

### 2. Prove the capture boundary

- Capture one upstream REA investigation with tool results, provider version, target identity and limitations.
- Convert it using the orchestrator's capture normalizer.
- Validate the result with REA Core.
- Compare normalized evidence with raw tool output.
- Retain the capture, normalized record, validation output and a short report.

The normalizer's capture envelope is our integration contract. It is not represented as upstream's native MCP wire format.

### 3. Build the live adapter

After the fixture contract is stable, add a versioned MCP client adapter that discovers available tools and guided prompts, calls only approved tools, records raw results, and emits the capture envelope. It must fail closed when required tools are unavailable. Runtime operations need a separate approval and safety policy from static inspection.

### 4. Connect one specialist

Choose a bounded, testable investigation first. Crypto-REA can test bytecode, transaction or protocol artifacts; a software REA can test the initial upstream bridge. Before Bio-REA, ensure the evidence contract works and then add biology-specific validation for experimental and scientific claims.

### 5. Cross-REA synthesis

- Accept only versioned investigation records.
- Compare findings and identify agreement, contradiction and missing evidence.
- Preserve source record IDs and evidence references.
- Report uncertainty instead of forcing consensus.
- Add synthetic conflict cases and a small benchmark corpus.

### 6. Safe automation

Only after the previous stages are reproducible:

- Add a durable queue and persistent run store.
- Execute expensive or untrusted workers in isolated processes or containers with resource and network restrictions.
- Add structured permissions, secret handling, retention rules and operator-visible approvals.
- Add bounded retries only for operations known to be safe to retry.
- Schedule low-risk static analyses and notify an operator when review is required.

Do not automate unrestricted execution of arbitrary artifacts or allow an agent to expand its own privileges.

## What the operator needs to do

### Required first

- Install Git, Python 3.10+, and a supported Node.js version.
- Choose a local workspace and keep separate virtual environments where helpful.
- Clone the three repositories and run their tests.
- Install upstream REA using its official setup process, review the changes it proposes, and restart the chosen agent client.
- Select a small, authorized, static-analysis-friendly target.
- Record the upstream REA version and the target's checksum or deterministic manifest.

### Needed before model-assisted analysis

- Select an agent client that supports local MCP servers.
- Decide which model provider may receive tool results, and review its data policy before analyzing confidential artifacts.
- Add API credentials only to the agent client's supported secret store or environment, never to the repository or investigation records.
- Install optional analysis providers only when the target type requires them. Ghidra, JADX, Frida and similar tools are not universal requirements.

### Needed for unattended or remote operation

- A dedicated VM/VPS or container host, non-root service account and restricted filesystem.
- Process/container isolation, CPU/memory/time limits, outbound network policy and artifact retention rules.
- Persistent database/queue, backups, monitoring and authenticated operator controls.
- Explicit approval policy for runtime experiments and external actions.

These are not required for the first local integration. Do not pay for infrastructure until the local evidence path works.

## Automation already present

- The orchestrator has GitHub Actions CI.
- Its CI checks out REA Core and tests the capture normalizer against the actual REA Core validator.
- Synthetic fixtures can be normalized without a model key or external analysis provider.

## Automation not yet present

- Live upstream REA MCP transport in the orchestrator.
- Automatic conversion of native upstream result payloads into our capture envelope.
- Automatic REA Core validation inside dispatcher completion.
- Durable storage, queueing, process isolation or remote worker management.
- Scheduled investigation runs and specialist delegation.
- Cross-REA synthesis against real investigation records.

Treat these as implementation milestones, not as features that already exist.
