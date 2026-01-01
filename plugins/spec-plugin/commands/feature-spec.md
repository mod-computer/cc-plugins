---
description: Write a feature specification with traceable glassware requirements
---

# Write Feature Specification

**Output:** `docs/specs/<feature-name>.spec.md` or `design/requirements.md`

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

* [Requirement description] <glassware type="requirement" id="req-001" />
* [Requirement description] <glassware type="requirement" id="req-002" />
* [Requirement description] <glassware type="requirement" id="req-003" />
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

<glassware type="requirement" id="req-ux-1" />
[User-facing behavior, UI components, interaction flows, accessibility.]

<glassware type="requirement" id="req-ux-2" />
[Additional UX requirement. Use sub-IDs for related items: req-ux-2a, req-ux-2b]

### Business Logic Requirements

<glassware type="requirement" id="req-bus-1" />
[Validation rules, workflows, calculations, state transitions.]

### Data Requirements

<glassware type="requirement" id="req-data-1" />
[Data structures, storage, relationships, migrations.]

### Integration Requirements

<glassware type="requirement" id="req-int-1" />
[APIs, external services, data exchange formats.]

### Infrastructure Requirements

<glassware type="requirement" id="req-infra-1" />
[Deployment, scaling, monitoring, security.]

### Performance Requirements

<glassware type="requirement" id="req-perf-1" />
[Latency targets, throughput, resource limits.]

### Quality Requirements

<glassware type="requirement" id="req-qual-1" />
[Test coverage expectations, error handling, edge cases.]
```

## Glassware Annotations

Every requirement must have a glassware tag for traceability:

```markdown
<glassware type="requirement" id="req-unique-id" />
```

**ID Conventions:**
- Simple: `req-001`, `req-002`
- Categorized: `req-ux-1`, `req-bus-1`, `req-data-1`
- Hierarchical: `req-ux-1`, `req-ux-1a`, `req-ux-1b`

**Linking implementations:**

```typescript
// glassware[type=implementation, id=impl-1, requirements=req-001]
function doThing() { ... }

// glassware-begin[type=implementation, id=impl-2, requirements=req-001,req-002]
if (condition) {
    handleCase();
}
// glassware-end[id=impl-2]
```

## Key Principles

- **Formality on demand** - A tiny project doesn't need 7 categories; a complex feature might need all of them
- **Specific and testable** - "bcrypt with cost=12" not "secure hashing"
- **Every requirement gets a tag** - For traceability to implementation
- **Only include relevant categories** - Skip sections that don't apply

## Writing Good Requirements

**Do:**
- Be specific: "Response time under 200ms for 95th percentile"
- Include acceptance criteria
- Use hierarchical IDs for sub-requirements
- Specify data formats and validation rules

**Don't:**
- Write vague requirements: "make it fast", "handle errors gracefully"
- Skip edge cases and error states
- Forget validation rules
- Add requirements that can't be verified

## Verification

After implementation, verify coverage:

```bash
# Check all requirements have implementations
glassware

# See what changed since branching
glassware diff $(git merge-base HEAD main)
```
