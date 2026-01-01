---
name: adding-traces
description: Guide for adding glasswear-readable traces to code
---

# Adding Traces to Code

Link code to requirements using glasswear annotations.

## Annotation Format

### Single-Line (for statements/declarations)
```typescript
// glassware[type=implementation, id=<unique-id>, requirements=<req-id>,<req-id-2>]
function myFunction() { ... }
```

### Multi-Line (for code regions)
```typescript
// glassware-begin[type=implementation, id=<unique-id>, requirements=<req-id>]
if (condition) {
    // multiple lines
    doSomething();
}
// glassware-end[id=<unique-id>]
```

## ID Conventions

Use descriptive, unique IDs:
- `impl-auth-validate-password`
- `impl-checkout-calculate-total`
- `impl-api-rate-limit`

## When to Add Traces

**Always trace:**
- Business logic (validation, calculations, state transitions)
- Security-sensitive code (auth, encryption, access control)
- Integration points (API calls, data transformations)

**Optional:**
- Simple utility functions
- Boilerplate/framework code
- Test setup/teardown

## Multiple Requirements

One implementation can satisfy multiple requirements:
```typescript
// glassware[type=implementation, id=impl-user-create, requirements=req-data-1,req-bus-1,req-int-1]
async function createUser(data: UserInput): Promise<User> { ... }
```

## Verification

```bash
# See all requirements and their status
glassware

# See details of a specific annotation
glassware show <id>

# Compare with base branch
glassware diff main
```

## Common Issues

- **Orphaned implementations**: Trace references a requirement that doesn't exist
- **Missing end tag**: Multi-line region without matching `glassware-end`
- **Duplicate IDs**: Each annotation needs a unique ID
