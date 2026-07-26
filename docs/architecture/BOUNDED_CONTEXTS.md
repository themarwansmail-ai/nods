# Bounded Contexts

**Document ID:** 06_BOUNDED_CONTEXTS.md  
**Status:** Draft  
**Owner:** Architecture  
**Last Updated:** YYYY-MM-DD

---

# Purpose

This document defines the strategic Bounded Contexts of NODS.

A Bounded Context is an explicit boundary within which a particular business model and its language are valid.

Each context owns:

- its business concepts
- its business rules
- its lifecycle
- its terminology
- the evolution of its model

No business concept may be owned by more than one Bounded Context.

---

# Objectives

This document establishes:

- Ownership of business capabilities
- Ownership of business terminology
- Context boundaries
- Responsibilities
- Collaboration between contexts
- Strategic separation of the domain model

---

# Principles

## Business First

Bounded Contexts are defined by business language, not technical implementation.

---

## Single Ownership

Every business concept has exactly one owning context.

Other contexts may reference the concept but cannot redefine its meaning.

---

## Autonomous Evolution

Each context should be able to evolve its business model independently without requiring changes to unrelated contexts.

---

## Explicit Collaboration

Contexts collaborate through well-defined business relationships.

No context should directly own another context's language.

---

## Stable Boundaries

Context boundaries should remain stable as features grow.

New functionality should extend an existing context whenever possible rather than creating unnecessary new contexts.

---

# Strategic Context Catalog

---

# Organization Context

## Purpose

Defines the organizational structure of the business.

This context answers:

> "Who owns the business and where does it operate?"

---

## Owns

- Organization
- Location

---

## Responsibilities

- Organization lifecycle
- Organizational hierarchy
- Location ownership
- Business operating locations

---

## Does NOT Own

- Employees
- Authentication
- Scheduling
- Inventory
- Tasks
- Attendance

---

## Upstream For

- People
- Operations
- Inventory
- Scheduling
- Attendance
- Analytics

---

# People Context

## Purpose

Defines the humans participating in the business.

This context answers:

> "Who are the people inside the organization?"

---

## Owns

- Person
- Employee
- Employment
- Assignment

---

## Responsibilities

- Person identity
- Employment lifecycle
- Organizational affiliation
- Operational assignments

---

## Does NOT Own

- User accounts
- Permissions
- Authentication
- Shift schedules
- Attendance
- Payroll
- Performance evaluations

---

## Depends On

- Organization

---

## Upstream For

- Identity
- Scheduling
- Attendance
- Operations
- Analytics

---

# Identity Context

## Purpose

Defines digital identities and access control.

This context answers:

> "Who can access NODS and what are they allowed to do?"

---

## Owns

- User
- Session
- Access Role
- Permission

---

## Responsibilities

- Authentication
- Authorization
- User lifecycle
- Access control

---

## Does NOT Own

- Employees
- Organizations
- Business responsibilities
- Job titles
- Operational assignments

---

## Depends On

- People

---

## Upstream For

All contexts requiring authenticated access.

---

# Scheduling Context

## Purpose

Plans operational work.

This context answers:

> "What work is planned?"

---

## Owns

- Shift
- Schedule
- Shift Assignment

---

## Responsibilities

- Workforce scheduling
- Shift planning
- Operational planning
- Resource allocation

---

## Does NOT Own

- Attendance
- Employment
- Authentication
- Tasks
- Inventory

---

## Depends On

- Organization
- People

---

## Upstream For

- Attendance
- Operations
- Analytics

---

# Attendance Context

## Purpose

Records actual workforce participation.

This context answers:

> "What actually happened?"

---

## Owns

- Attendance
- Check-In
- Check-Out
- Attendance Record

---

## Responsibilities

- Presence recording
- Time tracking
- Attendance history
- Attendance exceptions

---

## Does NOT Own

- Shift planning
- Employee records
- Authentication
- Payroll

---

## Depends On

- Scheduling
- People

---

## Upstream For

- Analytics
- Performance
- Payroll (future)

---

# Operations Context

## Purpose

Coordinates operational work performed by the business.

This context answers:

> "What work must be performed?"

---

## Owns

- Task
- Incident
- Checklist
- Operational Workflow

---

## Responsibilities

- Daily operations
- Task management
- Operational incidents
- Operational procedures

---

## Does NOT Own

- Inventory quantities
- Employee identity
- Authentication
- Attendance

---

## Depends On

- People
- Organization

---

## Upstream For

- Analytics

---

# Inventory Context

## Purpose

Manages business resources.

This context answers:

> "What resources does the business have?"

---

## Owns

- Inventory Item
- Stock
- Movement
- Stock Adjustment
- Waste

---

## Responsibilities

- Inventory lifecycle
- Stock movement
- Quantity tracking
- Inventory valuation
- Resource availability

---

## Does NOT Own

- Purchasing
- Finance
- Operational tasks
- Employee records

---

## Depends On

- Organization

---

## Upstream For

- Operations
- Analytics
- Procurement (future)

---

# Analytics Context

## Purpose

Provides business insight through analysis of operational data.

This context answers:

> "What does the business know?"

Analytics does not create business facts.

It derives information from other contexts.

---

## Owns

- KPI
- Metric
- Dashboard
- Trend
- Insight
- Report

---

## Responsibilities

- Business intelligence
- KPI calculation
- Reporting
- Trend analysis
- Decision support

---

## Does NOT Own

Any operational business data.

Analytics is a consumer of business information.

---

## Depends On

- Organization
- People
- Scheduling
- Attendance
- Operations
- Inventory

---

## Upstream For

Executive decision-making.

---

# Context Relationships

```
Organization
        │
        ▼
People
        │
        ▼
Identity

Organization ─────────────┐
                          │
People ───────────────────┼────► Scheduling
                          │
                          ▼
                    Attendance

People ───────────────► Operations

Organization ─────────► Inventory

Scheduling ───────────► Attendance

Attendance ────────────┐
Operations ────────────┤
Inventory ─────────────┼────► Analytics
Organization ──────────┤
People ────────────────┘
```

Arrows indicate business dependency.

A downstream context may depend upon the language and concepts of an upstream context.

The upstream context must remain independent of downstream consumers.

---

# Ownership Rules

## Rule 1

A business concept has exactly one owning context.

---

## Rule 2

Only the owning context may change the definition of a business concept.

---

## Rule 3

Contexts may reference another context's concepts but may not redefine them.

---

## Rule 4

Business rules remain inside the owning context.

---

## Rule 5

Analytics never owns operational truth.

It derives knowledge from other contexts.

---

## Rule 6

Identity owns access to the platform.

People owns the humans using the platform.

These responsibilities must never be merged.

---

# Future Contexts

The following contexts are intentionally excluded from the current strategic model but may be introduced as NODS evolves:

- Procurement
- Finance
- Payroll
- Performance Management
- Maintenance
- CRM
- Customer Management
- Vendor Management
- Asset Management
- Quality Management
- Compliance

These contexts should only be added when they introduce a distinct business language and cannot be represented within an existing context.

---

# Governance

Bounded Contexts define the strategic architecture of NODS.

New business concepts must be evaluated against this document before they are introduced.

No new context should be created unless:

- it owns a distinct business capability;
- it introduces a unique business language;
- it cannot naturally belong to an existing context; and
- its responsibilities are clearly separated from all existing contexts.

Changes to context ownership require architectural review and approval.