---
name: implement-spec
description: Guide for implementing specifications with traceability
---

# Implementing a Specification

Implement specs thoroughly and add traces for every requirement.

## Workflow

1. **Read the spec** - Understand all requirements before coding
2. **Plan implementation order** - Dependencies first (data → logic → UI)
3. **Implement with traces** - Add glassware annotations as you code
4. **Verify coverage** - Run `glassware` to check for unimplemented requirements

## Adding Traces

Every requirement should have at least one implementation trace:

```typescript
// glassware[type=implementation, id=impl-auth-1, requirements=req-bus-1]
function validatePassword(password: string): boolean {
  return password.length >= 8;
}

// For larger blocks:
// glassware-begin[type=implementation, id=impl-auth-2, requirements=req-bus-1,req-bus-2]
if (!user.verified) {
  await sendVerificationEmail(user);
  throw new UnverifiedError();
}
// glassware-end[id=impl-auth-2]
```

## Granularity Guidelines

- **Simple functions** (≤10 lines, no branching): One trace per function
- **Complex functions** (conditionals, multiple concerns): Multiple traces for different blocks
- **Business logic** (auth, payments, validation): Always detailed line-level traces

## Verification

```bash
# Check all requirements have implementations
glassware

# See what changed since branching
glassware diff $(git merge-base HEAD main)
```

## Completion Checklist

- [ ] All requirements have implementation traces
- [ ] `glassware` shows no unimplemented requirements
- [ ] Tests cover requirement edge cases
- [ ] Complex logic has granular traces
