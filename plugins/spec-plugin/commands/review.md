---
description: Review requirements and traces to identify gaps and address
---

# Review Spec and Traces

**Spec file:** "$ARGUMENTS"

## Process

1. **Run glasswear status**
   ```bash
   glassware
   ```

2. **Get branch changes**
   ```bash
   glassware diff $(git merge-base HEAD main)
   ```

3. **Analyze coverage gaps**
   - Identify requirements without implementations
   - Find code changes not linked to requirements
   - Check for orphaned implementations

4. **Propose updates**
   - Add missing implementation annotations to code
   - Update spec requirements if implementation diverged
   - Flag ambiguous matches for human review

## Annotation Formats

**Requirements (in .md files):**

CRITICAL: Glassware tag MUST be at the END of the requirement line:
```markdown
## Feature

* Requirement description here. <glassware type="requirement" id="req-feature-1" />
```

**Implementations (in .ts/.tsx files):**
```typescript
// glassware[type=implementation, id=impl-1, requirements=req-feature-1]
function feature() { ... }

// For multi-line regions:
// glassware-begin[type=implementation, id=impl-2, requirements=req-feature-1]
if (condition) {
    doSomething();
}
// glassware-end[id=impl-2]
```

## Output

Generate a summary showing:
- Requirements status (implemented/unimplemented)
- Code changes and their requirement coverage
- Proposed trace additions with exact annotations to add
- Spec updates if implementation changed scope
