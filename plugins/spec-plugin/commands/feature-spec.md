---
description: Write a feature specification with traceable glassware requirements
---

# Write Feature Specification

**Output:** `docs/specs/<feature-name>.md` or `specs/<feature-name>.md`

## Process

### 1. Gather Context

Ask the user:
- What feature or area are we specifying?
- What are the core requirements?
- What level of formality is appropriate? (Simple list vs. full categorized spec)

Explore the codebase to understand:
- Existing patterns and conventions
- Integration points
- Related specifications

### 2. Write Specification

Follow the glassware approach: **formality on demand** - match the spec complexity to the project needs.

### Simple Format (for focused features)

```markdown
# [Feature/Area] Requirements

## Core Features

* [Requirement description] <glassware type="requirement" id="req-feature-001" />
* [Requirement description] <glassware type="requirement" id="req-feature-002" />
* [Requirement description] <glassware type="requirement" id="req-feature-003" />
```

### Full Format (for complex features)

```markdown
---
title: feature-name
type: specification
created: YYYY-MM-DD
---

# Feature Name

## Abstract

[One sentence: what this does and its key capabilities.]

## Motivation

[Problem being solved and why it matters. Impact/value.]

## Approach

[Key technical decisions and integration points. High-level strategy.]

## Requirements

### UX Requirements

* [User-facing behavior, UI components, interaction flows, accessibility.] <glassware type="requirement" id="req-feature-ux-1" />
* [Additional UX requirement.] <glassware type="requirement" id="req-feature-ux-2" />

### Business Logic Requirements

* [Validation rules, workflows, calculations, state transitions.] <glassware type="requirement" id="req-feature-bus-1" />

### Data Requirements

* [Data structures, storage, relationships, migrations.] <glassware type="requirement" id="req-feature-data-1" />

### Integration Requirements

* [APIs, external services, data exchange formats.] <glassware type="requirement" id="req-feature-int-1" />

### Infrastructure Requirements

* [Deployment, scaling, monitoring, security.] <glassware type="requirement" id="req-feature-infra-1" />

### Performance Requirements

* [Latency targets, throughput, resource limits.] <glassware type="requirement" id="req-feature-perf-1" />

### Quality Requirements

* [Test coverage expectations, error handling, edge cases.] <glassware type="requirement" id="req-feature-qual-1" />
```

## Glassware Tag Format

**CRITICAL:** The glassware tag MUST be at the END of the requirement line:

```markdown
# CORRECT - tag at end of line (glassware will parse this)
* Login page shows "Continue with Google" button. <glassware type="requirement" id="req-auth-ux-1" />

# WRONG - tag on separate line (glassware will NOT parse this)
<glassware type="requirement" id="req-auth-ux-1" />
Login page shows "Continue with Google" button.
```

**ID Conventions:**
- Use namespaced IDs: `req-{feature}-{category}-{number}`
- Examples: `req-auth-ux-1`, `req-ws-bus-2`, `req-collab-data-3`
- This prevents ID collisions across specification files

**Linking implementations:**

```typescript
// glassware[type=implementation, id=impl-auth-login, requirements=req-auth-ux-1]
function handleLogin() { ... }

// glassware-begin[type=implementation, id=impl-auth-validate, requirements=req-auth-bus-1,req-auth-bus-2]
if (condition) {
    handleCase();
}
// glassware-end[id=impl-auth-validate]
```

## Key Principles

- **Formality on demand** - A tiny project doesn't need 7 categories; a complex feature might need all of them
- **Specific and testable** - "bcrypt with cost=12" not "secure hashing"
- **Tag at end of line** - Glassware only parses tags that are at the end of requirement text
- **Namespaced IDs** - Use `req-{feature}-{category}-{number}` to avoid duplicates
- **Only include relevant categories** - Skip sections that don't apply

## Writing Good Requirements

**Do:**
- Be specific: "Response time under 200ms for 95th percentile"
- Include acceptance criteria
- Use namespaced IDs for uniqueness across files
- Specify data formats and validation rules
- Place glassware tag at END of the line

**Don't:**
- Write vague requirements: "make it fast", "handle errors gracefully"
- Skip edge cases and error states
- Forget validation rules
- Add requirements that can't be verified
- Put glassware tags on their own line

## Verification

After implementation, verify coverage:

```bash
# Check all requirements have implementations
glassware

# See what changed since branching
glassware diff $(git merge-base HEAD main)
```
