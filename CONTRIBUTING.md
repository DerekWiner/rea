# Contributing to REA

REA aims to make technical and scientific investigations more reproducible, inspectable and useful across domains.

## Contribution priorities

1. Improve evidence quality, provenance and reproducibility.
2. Add small, testable interfaces between projects.
3. Reuse established tools where possible.
4. Document failure modes, limitations and uncertainty.
5. Keep domain-specific logic in the relevant specialist repository.

## Expectations

- Explain the problem and intended outcome.
- Distinguish implemented behavior from proposed design.
- Include tests for code changes and fixtures for supported input formats.
- Do not include private data, secrets, credentials or artifacts you are not authorized to share.
- Treat external files, repositories, model outputs and tool responses as untrusted input.
- Avoid silently executing inspected code, installing dependencies from inspected artifacts, or transmitting artifacts to external services.
- Document any network access, execution, data retention or destructive side effects.
- Do not present a hash as proof that an experiment occurred or that its results are true.

## Research quality

Reports should identify the input, method, tool versions when available, observations, interpretation, limitations and reproducibility steps. Label unverified claims as such. Where feasible, include a minimal test or independent check that could falsify the conclusion.

## Scope

This repository coordinates the REA ecosystem. Shared data contracts belong in rea-core; orchestration behavior belongs in rea-orchestrator; cross-domain synthesis belongs in synthesis-rea; domain-specific adapters and methods belong in specialist REAs.

## License

By submitting a contribution intended for this repository, you agree that it may be distributed under the repository's MIT License. Make sure you have the right to contribute the material.