# Groceries MCP Constitution

## Core Principles

### I. Reliable MCP Contracts
Every exposed tool MUST have a clear, narrow purpose and a stable, documented input and output contract. Inputs MUST be validated before use, and errors MUST identify the failed operation without exposing secrets or internal stack details. Changes to tool behavior MUST be reflected in the corresponding documentation and examples.

### II. Accurate Grocery Data
The server MUST preserve the meaning and provenance of grocery data supplied by users or upstream services. It MUST distinguish unavailable or unknown values from confirmed values and MUST NOT fabricate prices, availability, product details, or successful outcomes. Normalization MUST retain enough source context to explain material transformations.

### III. Safe and Minimal Data Handling
The server MUST request and retain only data needed for the requested grocery operation. Credentials and sensitive user data MUST NOT appear in logs, errors, or examples. Operations that create, update, or delete user data MUST validate their targets and report the actual result; they MUST NOT claim success before the upstream operation succeeds.

### IV. Testable Behavior
New behavior and behavior changes MUST include automated coverage at the narrowest useful level. Tests MUST cover input validation, expected results, and failure behavior for changed contracts. Integration tests MUST cover boundaries where behavior depends on external services or shared schemas. Tests MUST NOT require live credentials or mutate real user data.

### V. Maintainable and Observable Design
Implementations MUST favor the smallest design that satisfies the documented use case. External calls and consequential state changes MUST produce enough structured diagnostic information to investigate failures without logging sensitive values. Dependencies and abstractions MUST be added only when they address a stated requirement.

## Additional Constraints

The project MUST use the Model Context Protocol for the server interface. Tool names, descriptions, and schemas MUST help clients select and invoke operations correctly. External service integrations MUST handle timeouts and errors explicitly, and MUST avoid retrying non-idempotent operations unless the operation is known to be safe to repeat.

## Development Workflow

A change that affects a tool contract MUST update its documentation and tests in the same change. Before marking work complete, contributors MUST review the change against these principles and report which relevant checks were run and any checks that remain outstanding. Automated checks MUST be run when requested by the task or required by repository guidance.

## Governance

This constitution governs project decisions and takes precedence over conflicting local development practices. Amendments MUST be made in a reviewed change that explains the reason and impact. The version MUST follow semantic versioning: MAJOR for incompatible changes to principles or governance, MINOR for added principles or materially expanded requirements, and PATCH for clarifications and non-semantic wording changes. The ratification date records the original adoption date; the last-amended date changes whenever this document changes. Contributors and reviewers MUST assess relevant changes for compliance, and any deviation MUST be documented with its rationale.

**Version**: 1.0.1 | **Ratified**: 2026-10-28 | **Last Amended**: 2026-10-28
