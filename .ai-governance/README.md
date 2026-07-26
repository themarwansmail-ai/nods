# AI Development Guide

Welcome to the NODS AI workspace.

This directory contains the governance, standards, and operating procedures that every AI coding agent must follow when contributing to the NODS platform.

The purpose of this directory is to ensure that all generated code—regardless of the AI model used—is consistent with the project's architecture, engineering standards, and long-term vision.

---

# Mission

Every implementation must:

- Respect the approved architecture.
- Preserve domain integrity.
- Produce production-quality code.
- Remain simple, maintainable, and testable.
- Prioritize correctness over speed.

AI is an engineering assistant—not an architect. Architectural decisions are made by the project and documented under `docs/architecture`.

---

# Source of Truth

Before performing any task, AI must consider the following documents authoritative.

## Architecture

```
docs/architecture/
```

Including (but not limited to):

- PLATFORM.md
- DOMAIN_ARCHITECTURE.md
- DEPENDENCY_RULES.md
- EVENT_FLOW.md
- UBIQUITOUS_LANGUAGE.md
- BOUNDED_CONTEXTS.md
- STRATEGIC_DECISIONS.md

These documents define the architecture of NODS.

Implementation must conform to them.

If implementation appears to conflict with architecture, stop and explain the conflict instead of inventing a solution.

---

# AI Documentation

This directory is organized as follows.

```
.ai/

README.md

PROJECT_CONTEXT.md
ARCHITECTURE_RULES.md
CODING_STANDARDS.md
FORBIDDEN.md
REVIEW_CHECKLIST.md
CONTEXT_INDEX.md
DECISION_LOG.md

AGENTS/
PROMPTS/
```

Each document has a specific responsibility.

AI should read only the documents relevant to the requested task.

---

# Engineering Principles

Every implementation must follow these principles.

- Domain-Driven Design (DDD)
- Clean Architecture
- SOLID Principles
- Composition over inheritance
- Explicit dependencies
- High cohesion
- Low coupling
- Testability
- Simplicity
- Readability
- Production quality

Shortcuts are not acceptable.

---

# AI Responsibilities

AI is expected to:

- understand the task before coding;
- read the required architecture documents;
- explain architectural conflicts before implementing;
- produce production-ready code;
- write appropriate tests;
- avoid unnecessary complexity;
- preserve existing architecture.

AI should never guess business rules.

When requirements are ambiguous, ask for clarification.

---

# General Workflow

Every implementation follows the same workflow.

1. Read the required context.
2. Understand the business requirement.
3. Review the relevant architecture.
4. Design the solution.
5. Implement production-quality code.
6. Write tests.
7. Perform a self-review.
8. Explain important design decisions.

---

# Architecture Changes

Architecture cannot be modified through implementation.

If AI believes a better approach exists:

1. Stop implementation.
2. Explain the conflict.
3. Explain trade-offs.
4. Wait for approval.

Only approved architectural decisions may change the architecture documents.

---

# Code Quality

Generated code should be:

- deterministic;
- readable;
- maintainable;
- testable;
- scalable;
- minimal.

Favor clarity over cleverness.

Avoid premature optimization.

---

# Long-Term Goal

NODS is intended to become a long-lived commercial SaaS platform.

Every implementation should optimize for maintainability over the lifetime of the product rather than short-term convenience.

Consistency is more valuable than novelty.

Architecture is more valuable than clever code.

Code should be written as if another engineer will maintain it for the next ten years.