# Forbidden Practices

This document defines practices that are prohibited within the NODS codebase.

These rules exist to preserve architecture, maintainability, consistency, and production quality.

Unless explicitly approved by the project architect, AI must never violate these rules.

---

# 1. Architecture

Never:

- Violate Clean Architecture.
- Introduce circular dependencies.
- Allow Domain to depend on Infrastructure.
- Skip the Application layer.
- Place business logic outside the Domain.
- Access another bounded context's internal implementation.
- Bypass Aggregate Roots.
- Modify Aggregate state directly.
- Duplicate business rules across bounded contexts.

---

# 2. Code Quality

Never:

- Use `any`.
- Use `@ts-ignore`.
- Use `@ts-nocheck`.
- Disable TypeScript strict mode.
- Disable ESLint to silence problems.
- Ignore compiler warnings.
- Leave dead code.
- Leave commented-out implementations.
- Commit experimental code.

---

# 3. Temporary Code

Never commit:

- TODO placeholders
- FIXME placeholders
- HACK comments
- Stub implementations
- Mock business logic
- Fake validation
- Fake authentication
- Fake authorization

If something cannot be completed correctly, stop and explain why.

---

# 4. Business Logic

Never place business rules inside:

- React components
- Next.js pages
- API routes
- Database queries
- Repository implementations
- Supabase adapters
- Utility functions

Business rules belong in the Domain.

---

# 5. Database

Never:

- Build SQL through string concatenation.
- Ignore transactions when consistency is required.
- Skip validation before persistence.
- Depend on database behavior to enforce business rules.
- Store invalid domain data.

The database protects data integrity.

The Domain protects business integrity.

---

# 6. Error Handling

Never:

- Swallow exceptions.
- Return null to indicate failure without a documented reason.
- Hide errors from callers.
- Log errors without context.
- Catch exceptions without handling them.

Errors should be explicit.

---

# 7. Testing

Never:

- Merge untested business logic.
- Delete tests to make builds pass.
- Write tests that depend on execution order.
- Test implementation details instead of behavior.
- Ignore failing tests.

---

# 8. Security

Never:

- Hardcode secrets.
- Hardcode API keys.
- Hardcode credentials.
- Commit environment variables.
- Expose internal errors to clients.
- Trust client input.
- Skip authorization checks.
- Assume authenticated users are authorized.

Security is mandatory.

---

# 9. Performance

Never:

- Optimize without evidence.
- Introduce caching without a defined invalidation strategy.
- Execute unnecessary database queries.
- Load unnecessary data.
- Prematurely optimize code at the expense of readability.

Measure before optimizing.

---

# 10. Dependencies

Never:

- Add a new dependency without justification.
- Introduce libraries that duplicate existing functionality.
- Use a package for trivial functionality.
- Couple business logic to third-party SDKs.

Prefer the standard library whenever practical.

---

# 11. AI Behavior

Never:

- Guess business rules.
- Invent requirements.
- Invent APIs.
- Invent database tables.
- Invent architecture.
- Assume undocumented behavior.
- Change architecture silently.
- Continue implementation after detecting an architectural conflict.

When uncertain:

1. Stop.
2. Explain the uncertainty.
3. Ask for clarification.

---

# 12. Repository Hygiene

Never:

- Rename files without reason.
- Move folders unnecessarily.
- Reformat unrelated files.
- Change project structure without approval.
- Mix refactoring with feature implementation.

Keep commits focused.

---

# Final Rule

Do not trade long-term maintainability for short-term progress.

If following these rules prevents implementation, stop and explain the constraint instead of violating the architecture.