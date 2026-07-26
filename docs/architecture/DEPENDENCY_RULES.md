# Dependency Rules

## Overview

This document defines the architectural dependency rules of the NODS platform. Its purpose is to preserve clear ownership, minimize coupling, and ensure that every component of the platform evolves independently while collaborating through well-defined boundaries.

These rules apply to every platform layer, business domain, shared service, and future implementation within NODS.

---

## Layer Dependency Rules

Dependencies between architectural layers follow a strict direction.

```text
Platform Foundation
        │
        ▼
Business Domains
        │
        ▼
Shared Services
```

The following rules apply:

- Platform Foundation may be used by every other layer.
- Business Domains may depend on Platform Foundation.
- Shared Services may depend on Platform Foundation and Business Domains only when providing shared capabilities.
- Business Domains must never depend on Shared Services for business rules.
- Dependencies must always flow downward and never create circular relationships.

---

## Domain Dependency Rules

Business Domains collaborate through clearly defined boundaries.

The following rules apply:

- Every domain owns its own business rules.
- Domains may reference information owned by another domain but must not modify another domain's business rules.
- Domains communicate through contracts or business events rather than internal implementation.
- A domain must never directly depend on the internal implementation of another domain.
- Domain dependencies should remain directional and avoid circular references.

---

## Forbidden Dependencies

The following architectural patterns are prohibited within NODS:

- Circular dependencies between domains.
- Shared ownership of business rules.
- Direct access to another domain's internal data or implementation.
- Duplication of business rules across multiple domains.
- Platform Foundation depending on Business Domains.
- Shared Services becoming owners of business logic.

Any exception to these rules must be documented and approved through an Architecture Decision Record (ADR).

---

## Dependency Principles

The dependency model of NODS follows these principles:

- Dependencies should be explicit rather than implicit.
- Business Domains remain independently evolvable.
- Collaboration does not imply ownership.
- Shared Services support business capabilities without replacing them.
- Platform Foundation provides common capabilities without containing business logic.
- Architectural simplicity is preferred over unnecessary coupling.

---

## Architecture Review

The dependency rules have been reviewed to ensure consistency with the Platform Architecture and Domain Architecture.

These rules establish the architectural constraints that govern how components of NODS interact and provide the foundation for Event Flow, Bounded Contexts, and future implementation.

All future architectural decisions that introduce new dependencies should be evaluated against these rules and documented through an ADR when exceptions are required.
