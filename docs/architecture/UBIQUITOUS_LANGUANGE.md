# Ubiquitous Language

**Document ID:** 05_UBIQUITOUS_LANGUAGE.md  
**Status:** Draft  
**Owner:** Architecture  
**Last Updated:** YYYY-MM-DD

---

# Purpose

This document defines the official business vocabulary of NODS.

The Ubiquitous Language establishes a single, shared understanding of business concepts across Product, Engineering, Design, Operations, and all future stakeholders.

Every architecture document, Product Requirement Document (PRD), workflow, discussion, and implementation must use the terminology defined here.

If two terms appear to describe the same concept, this document is the source of truth.

---

# Goals

- Establish one meaning for every core business concept.
- Eliminate ambiguous terminology.
- Define ownership of each concept.
- Create a stable language that scales with the platform.
- Ensure future bounded contexts are built upon consistent terminology.

---

# Principles

## One Concept → One Name

Each business concept has exactly one official name.

---

## One Name → One Meaning

A business term must never represent multiple concepts.

---

## Business Language First

Business terminology must describe the business itself—not the software implementation.

---

## Stable Vocabulary

Core business concepts should remain stable over time.

New terminology should only be introduced when representing genuinely new business concepts.

---

## Explicit Ownership

Every business concept belongs to exactly one Bounded Context.

That context owns the meaning, lifecycle, and evolution of the concept.

---

# Naming Rules

- Use singular nouns.
- Prefer business terminology over technical terminology.
- Prefer industry-neutral names whenever possible.
- Avoid abbreviations.
- Avoid implementation-specific terminology.
- Do not invent synonyms.
- If a concept already exists, use its official name.

---

# Core Concept Relationships

The following diagram illustrates the conceptual relationships between the foundational business concepts.

```text
Organization
│
└── owns
    │
    ▼
Location


Person
│
├── may have
│   ▼
│ Employment
│
├── may receive
│   ▼
│ Assignment
│
└── may have
    ▼
User


User
│
└── has
    ▼
Access Role
        │
        └── contains
            ▼
        Permission
```

These relationships describe business concepts only.

They do **not** represent implementation details, database models, or system architecture.

---

# Core Business Vocabulary

---

# Organization

## Definition

A legal or business entity that owns and operates one or more Locations.

Organizations define the highest level of business ownership within NODS.

## Owned By

Organization Context

## Related Concepts

- Location
- Employee
- Employment

## Forbidden Synonyms

- Company
- Business
- Client
- Tenant

---

# Location

## Definition

A physical place where an Organization performs business operations.

Examples include:

- Restaurant
- Warehouse
- Office
- Factory
- Distribution Center
- Retail Store
- Cloud Kitchen

## Owned By

Organization Context

## Related Concepts

- Organization

## Forbidden Synonyms

- Branch
- Store
- Outlet
- Site

---

# Person

## Definition

A human known to NODS.

A Person exists independently of employment status, operational responsibilities, or system access.

A Person may:

- be employed by an Organization
- receive operational assignments
- have a User account
- never access NODS

## Owned By

People Context

## Related Concepts

- Employee
- Employment
- Assignment
- User

## Forbidden Synonyms

- User
- Employee
- Staff
- Worker
- Team Member

---

# Employee

## Definition

A Person employed by an Organization.

Employment represents a business relationship.

Being an Employee does **not** imply system access.

## Owned By

People Context

## Related Concepts

- Person
- Employment
- Organization

## Forbidden Synonyms

- User
- Operator
- Staff

---

# Employment

## Definition

The business relationship between a Person and an Organization.

Employment defines organizational affiliation but does not determine permissions, authentication, or operational responsibilities.

## Owned By

People Context

## Related Concepts

- Employee
- Organization
- Person

## Forbidden Synonyms

None

---

# Assignment

## Definition

The allocation of an Employee to a specific operational responsibility within an Organization for a defined period of time.

Assignments are temporary and may change without affecting Employment or User access.

## Owned By

People Context

## Related Concepts

- Employee
- Employment

## Forbidden Synonyms

None

---

# User

## Definition

A digital identity authorized to access NODS.

A User represents a system account rather than a business person.

A User may be linked to a Person but is not itself a Person.

## Owned By

Identity Context

## Related Concepts

- Person
- Access Role
- Session

## Forbidden Synonyms

- Employee
- Staff
- Login
- Account Holder

---

# Access Role

## Definition

A named collection of Permissions that authorizes a User to perform actions within NODS.

Access Roles exist solely for authorization and do not represent business responsibilities or job titles.

## Owned By

Identity Context

## Related Concepts

- Permission
- User

## Forbidden Synonyms

- Position
- Job
- Manager
- Supervisor
- Kitchen Leader

---

# Permission

## Definition

An atomic capability that authorizes a User to perform a specific action within a defined scope.

Permissions are the smallest unit of authorization and are combined into Access Roles.

## Owned By

Identity Context

## Related Concepts

- Access Role

## Forbidden Synonyms

- Privilege
- Authority

---

# Session

## Definition

A temporary authenticated interaction between a User and NODS.

A Session represents active system access and has no business meaning outside the Identity Context.

## Owned By

Identity Context

## Related Concepts

- User

## Forbidden Synonyms

None

---

# Shift

## Definition

A scheduled period during which operational work is expected to be performed.

A Shift defines planned work time, not actual attendance.

## Owned By

Scheduling Context

## Related Concepts

- Assignment
- Attendance

## Forbidden Synonyms

- Schedule

---

# Attendance

## Definition

The recorded presence of an Employee during an assigned Shift.

Attendance represents actual participation rather than planned work.

## Owned By

Attendance Context

## Related Concepts

- Shift
- Employee

## Forbidden Synonyms

- Check In
- Clock In

---

# Inventory Item

## Definition

A managed resource whose quantity, availability, or movement is tracked by the business.

Inventory Items may represent ingredients, finished goods, packaging, supplies, or other operational resources.

## Owned By

Inventory Context

## Related Concepts

- Movement

## Forbidden Synonyms

- Product
- Material
- Stock

---

# Movement

## Definition

A business event representing a change in the state or quantity of an Inventory Item.

Examples include receiving, consumption, transfer, adjustment, and waste.

## Owned By

Inventory Context

## Related Concepts

- Inventory Item

## Forbidden Synonyms

- Transaction

---

# Task

## Definition

A unit of operational work assigned to one or more Employees with an expected outcome.

Tasks describe work to be performed rather than organizational responsibilities.

## Owned By

Operations Context

## Related Concepts

- Assignment

## Forbidden Synonyms

- Job
- Duty

---

# Incident

## Definition

An unexpected operational event requiring documentation, investigation, or corrective action.

Incidents capture operational exceptions rather than routine activities.

## Owned By

Operations Context

## Related Concepts

- Task

## Forbidden Synonyms

- Problem
- Issue
- Complaint

---

# Reserved Terms

The following terms have specific architectural meanings and must not be reused for unrelated concepts.

- Aggregate
- Entity
- Value Object
- Domain Event
- Policy
- Context
- Workflow
- Command
- Query

---

# Deprecated Terms

The following terms are intentionally excluded from the NODS vocabulary.

| Deprecated | Use Instead |
|------------|-------------|
| Company | Organization |
| Business | Organization |
| Tenant | Organization |
| Client | Organization |
| Branch | Location |
| Store | Location |
| Outlet | Location |
| Site | Location |
| Worker | Person or Employee |
| Staff | Employee |
| Team Member | Employee |
| Login | User |
| Role | Access Role |

---

# Governance

The Ubiquitous Language is part of the Architecture Foundation.

Changes to this document require architectural review.

No business terminology may be introduced into NODS without ensuring:

- it represents a distinct business concept;
- it does not duplicate an existing concept;
- it belongs to a single Bounded Context; and
- it remains consistent with the overall strategic domain model.

This document is the authoritative source for all business vocabulary used throughout NODS.