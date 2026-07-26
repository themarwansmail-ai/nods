# Architecture Rules

This document defines the architectural rules that every AI agent must follow when contributing to the NODS platform.

These rules are mandatory.

If a requested implementation conflicts with any rule in this document, the AI must stop, explain the conflict, and wait for approval before proceeding.

---

# Rule 1 — Architecture is the Source of Truth

The approved architecture under `docs/architecture/` is authoritative.

Implementation must conform to the architecture.

Implementation must never redefine the architecture.

---

# Rule 2 — Respect Bounded Contexts

Every feature belongs to exactly one bounded context.

Business logic must remain inside its owning bounded context.

Do not duplicate business rules across contexts.

Cross-context communication must occur only through approved interfaces or events.

---

# Rule 3 — Follow Clean Architecture

Dependencies always point inward.

Presentation
→ Application
→ Domain

Infrastructure implements interfaces defined by the Domain or Application layers.

The Domain layer must never depend on Infrastructure.

---

# Rule 4 — Protect the Domain

Business rules belong in the Domain.

Never place business logic inside:

- React components
- API routes
- Database queries
- Infrastructure services
- UI helpers

The Domain is responsible for enforcing business invariants.

---

# Rule 5 — Aggregate Integrity

Aggregates are consistency boundaries.

All state changes must occur through Aggregate methods.

Do not modify Aggregate state directly.

Repositories load and persist Aggregates.

---

# Rule 6 — Value Objects

Use Value Objects to model concepts with no identity.

Value Objects must be:

- immutable
- validated
- self-contained

Primitive obsession should be avoided.

---

# Rule 7 — Domain Events

Use Domain Events to represent important business occurrences.

Domain Events must:

- be immutable
- describe something that already happened
- contain only relevant business data

Do not use Domain Events as commands.

---

# Rule 8 — Application Layer Responsibilities

The Application layer coordinates use cases.

It may:

- load Aggregates
- call Domain methods
- persist changes
- publish events

It must not contain business rules.

---

# Rule 9 — Infrastructure Responsibilities

Infrastructure exists to support the Domain.

Examples include:

- databases
- Supabase
- PostgreSQL
- external APIs
- email providers
- storage
- authentication adapters

Infrastructure must not own business logic.

---

# Rule 10 — Presentation Responsibilities

Presentation handles interaction with users.

Examples include:

- Next.js pages
- API routes
- UI components
- request validation
- response formatting

Presentation must not implement business rules.

---

# Rule 11 — Explicit Dependencies

Dependencies must be explicit.

Avoid hidden coupling.

Avoid service locators.

Avoid global mutable state.

Favor constructor injection where appropriate.

---

# Rule 12 — Simplicity

Choose the simplest design that satisfies the architecture.

Avoid:

- unnecessary abstractions
- speculative design
- premature optimization
- over-engineering

Complexity must always have a clear justification.

---

# Rule 13 — Production Quality

Every implementation must be production-ready.

Temporary solutions are not acceptable.

Do not leave:

- TODOs
- placeholder implementations
- commented-out code
- incomplete features

---

# Rule 14 — Testing

Code without tests is incomplete.

Every feature should include appropriate tests.

Tests should verify business behavior rather than implementation details.

---

# Rule 15 — Consistency

Consistency is preferred over novelty.

When multiple valid implementations exist, choose the one that best matches the existing codebase.

The project should feel as though it was written by a single engineering team.

---

# Rule 16 — Challenge Assumptions

AI should not blindly follow requests that violate the architecture.

When a conflict is detected:

1. Stop.
2. Explain the issue.
3. Describe the trade-offs.
4. Recommend an approach.
5. Wait for approval.

Protecting the architecture takes priority over completing the task.

---

# Rule 17 — Long-Term Thinking

NODS is designed as a long-lived commercial SaaS platform.

Every design decision should optimize for:

- maintainability
- scalability
- readability
- correctness
- developer experience

Avoid decisions that prioritize short-term convenience over long-term quality.

---

# Final Principle

The goal of every implementation is not merely to make the code work.

The goal is to preserve the integrity of the architecture while delivering production-quality software.