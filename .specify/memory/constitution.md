<!-- Sync Impact Report
Version change: Unversioned scaffold → 1.0.0 (initial project constitution)
Modified principles:
- Template principle 1 → I. Training-Only Purpose and Scope
- Template principle 2 → II. Offline-First and Replaceable Infrastructure
- Template principle 3 → III. Authorization at Each Data Boundary
- Template principle 4 → IV. Verified Changes
- Template principle 5 → V. Simple, Layered .NET Design
Added sections:
- Project Constraints (replaces the template's second general section)
- Development Workflow (replaces the template's third general section)
Removed sections: None.
Follow-up TODO: Confirm the original ratification date; the repository does not establish it.
-->
# ContosoDashboard Constitution

## Core Principles

### I. Training-Only Purpose and Scope
ContosoDashboard is fictional software for training. Code, documentation, and demonstrations
MUST identify mock authentication and other training-only behavior accurately. Changes MUST NOT
claim production readiness, production security, or operational support that the project does
not provide. Known limitations MUST remain visible in relevant documentation.

Rationale: Clear boundaries prevent training examples from being mistaken for production guidance.

### II. Offline-First and Replaceable Infrastructure
The application and its normal training workflows MUST remain usable locally without cloud
accounts or external service dependencies. Infrastructure that is intended to be replaceable
MUST be accessed through suitable interfaces and dependency injection, with local implementations
preserved for training. Documentation MUST distinguish a proposed migration path from a verified
production implementation.

Rationale: Offline availability is a core training requirement, and abstraction keeps examples
focused on replaceable infrastructure rather than cloud setup.

### III. Authorization at Each Data Boundary
Protected pages and service operations MUST enforce authorization using the authenticated
identity and applicable role or resource ownership. UI visibility or filtering MUST NOT be the
only protection for data access. Changes to authorization or user-scoped data MUST include tests
for permitted access and denied cross-user or role access, as applicable. Mock authentication
MUST continue to be described as training-only.

Rationale: Defense in depth is essential even in a simplified training application.

### IV. Verified Changes
Behavior changes MUST include automated tests at the most relevant available layer. Changes
affecting authorization, data ownership, or persistence MUST include focused regression coverage.
Before a change is proposed for integration, contributors MUST run the relevant tests and build
checks and report any checks that could not be run.

Rationale: Repeatable verification makes the training code dependable and exposes regressions.

### V. Simple, Layered .NET Design
Changes MUST preserve clear separation among the application's UI, services, models, and data
responsibilities. New abstractions MUST address a concrete need, such as infrastructure
replacement, testability, or a clear separation of concerns; speculative frameworks and
unnecessary indirection MUST be avoided. Implementations MUST remain understandable for the
project's training audience.

Rationale: The codebase demonstrates maintainable patterns while keeping examples approachable.

## Project Constraints

- The project uses ASP.NET Core 8 with Blazor Server and Entity Framework Core. Changes MUST
  preserve this stack unless an approved feature specification explicitly authorizes a migration.
- SQL Server LocalDB is the documented local database. The application MUST NOT acquire a
  required cloud database or external runtime service as an incidental feature dependency.
- Authentication is a mock training implementation. It MUST NOT be presented as password-based
  production authentication or as a substitute for a production identity provider.
- User-facing and contributor documentation MUST stay consistent with the implemented behavior,
  offline-training scope, and known limitations.

## Development Workflow

- Feature work MUST use the repository's Spec Kit workflow: document requirements in a
  specification, plan material design decisions, and derive actionable implementation tasks.
- Specifications and implementation plans MUST identify applicable constitution principles and
  state how the proposed change satisfies them. Conflicts MUST be resolved before implementation.
- Reviews MUST verify relevant tests and build checks, assess authorization and user-data
  boundaries where touched, and ensure documentation matches the delivered behavior.
- Stakeholder documents and README guidance MUST be updated when a change materially alters
  documented behavior, constraints, or training instructions.

## Governance

This constitution governs project specifications, plans, implementation, and reviews. A proposed
amendment MUST state its rationale and impact, be reviewed and approved by the repository
maintainers, and update this document's version and amendment date. The change review MUST check
that dependent specifications, plans, tasks, and contributor guidance remain consistent.

Versioning follows semantic versioning:

- **MAJOR**: remove or redefine a principle or constraint, or make a backward-incompatible
  governance change.
- **MINOR**: add a principle or section, or materially expand governance requirements.
- **PATCH**: clarify or refine wording without changing the obligations.

Every feature specification and code review MUST consider applicable principles and identify
unresolved violations. Work that conflicts with this constitution MUST be revised or receive an
explicit constitution amendment before integration. Reviewers MUST verify the required tests,
build checks, and documentation updates for the change.

**Version**: 1.0.0 | **Ratified**: TODO(RATIFICATION_DATE): original adoption date unknown | **Last Amended**: 2026-10-26
