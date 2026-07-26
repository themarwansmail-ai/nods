# Strategic Decisions

**Document ID:** 07_STRATEGIC_DECISIONS.md  
**Status:** Approved  
**Owner:** Architecture  
**Last Updated:** YYYY-MM-DD

---

# Purpose

This document records the major strategic architectural decisions that define the business model of NODS.

These decisions establish the long-term direction of the platform and provide the rationale behind the strategic domain model.

Unlike implementation decisions, strategic decisions are expected to remain stable over the lifetime of the platform.

Future architectural work should align with these decisions unless a formal review concludes that a decision is no longer appropriate.

---

# Decision Format

Each decision contains:

- Decision
- Status
- Rationale
- Consequences

---

# SD-001 — Organization is the Root Business Entity

## Status

Approved

## Decision

Organization is the highest-level business entity within NODS.

Every business operation belongs to exactly one Organization.

## Rationale

Organizations provide ownership, governance, and business boundaries.

Using Organization rather than Company or Tenant keeps the platform industry-neutral.

## Consequences

- Every business capability operates within an Organization.
- Organization ownership is explicit across the platform.

---

# SD-002 — Location Replaces Branch

## Status

Approved

## Decision

The canonical business term is **Location**.

Branch, Store, Outlet, and Site are deprecated.

## Rationale

Location supports restaurants, warehouses, factories, offices, distribution centers, retail stores, and future industries without changing the business language.

## Consequences

All future documentation and product terminology must use Location.

---

# SD-003 — Identity is Independent of People

## Status

Approved

## Decision

Identity is a dedicated Bounded Context separate from People.

## Rationale

A Person represents a human.

A User represents a digital identity.

These concepts evolve independently.

Separating them prevents business relationships from becoming coupled to authentication and authorization.

## Consequences

People owns:

- Person
- Employee
- Employment
- Assignment

Identity owns:

- User
- Access Role
- Permission
- Session

---

# SD-004 — Access Roles are not Business Roles

## Status

Approved

## Decision

Access Roles exist solely for authorization.

Business responsibilities remain part of the business domain.

## Rationale

Job titles and organizational responsibilities change independently from software permissions.

Combining them creates unnecessary coupling.

## Consequences

Titles such as:

- Kitchen Leader
- Supervisor
- Branch Manager

must never be used as Access Roles.

---

# SD-005 — One Business Concept has One Owner

## Status

Approved

## Decision

Every business concept belongs to exactly one Bounded Context.

## Rationale

Shared ownership creates ambiguity and conflicting business rules.

Single ownership enables independent evolution.

## Consequences

Contexts may reference concepts owned by other contexts but may never redefine them.

---

# SD-006 — Analytics Never Owns Operational Truth

## Status

Approved

## Decision

Analytics consumes operational information but never becomes the source of record.

## Rationale

Operational truth belongs to operational contexts.

Analytics derives knowledge rather than creating it.

## Consequences

Reports, KPIs, dashboards, and insights are derived views.

Operational changes always originate from their owning context.

---

# SD-007 — Scheduling and Attendance are Separate Domains

## Status

Approved

## Decision

Scheduling and Attendance represent different business capabilities.

## Rationale

Scheduling models planned work.

Attendance models actual work.

The business rules governing these concepts differ significantly.

## Consequences

Attendance must never modify scheduling decisions.

Scheduling does not determine attendance outcomes.

---

# SD-008 — Business Language is Canonical

## Status

Approved

## Decision

The Ubiquitous Language is the authoritative vocabulary for NODS.

## Rationale

Consistent terminology reduces ambiguity and improves collaboration across architecture, product, engineering, and operations.

## Consequences

New business terminology requires architectural review before adoption.

Deprecated terms must not be reintroduced.

---

# SD-009 — Bounded Contexts Define Business Ownership

## Status

Approved

## Decision

Business capabilities are partitioned by Bounded Context rather than organizational structure or technical implementation.

## Rationale

Contexts are determined by business language and ownership.

Departments, teams, services, or applications must not influence strategic boundaries.

## Consequences

Future modules must be evaluated against existing contexts before introducing new ones.

---

# SD-010 — Strategic Architecture Before Implementation

## Status

Approved

## Decision

Strategic domain modeling is completed before implementation begins.

## Rationale

Business architecture is significantly more expensive to change than application code.

A stable strategic model reduces long-term complexity and implementation risk.

## Consequences

No implementation should redefine business concepts established by the architecture documents.

Changes to the strategic model require architectural review.

---

# Governance

Strategic Decisions are considered part of the Architecture Foundation.

A new Strategic Decision should only be added when it:

- changes the strategic domain model;
- introduces a new architectural principle;
- redefines business ownership; or
- materially affects the evolution of NODS.

Implementation details, framework choices, libraries, infrastructure, and technology selections are intentionally excluded from this document.