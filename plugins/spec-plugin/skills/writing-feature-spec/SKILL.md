---
name: writing-feature-spec
description: Guide for writing feature specifications with UX, business logic, infra, and performance requirements
---

# Writing a Feature Specification

Write specs that give agents the information needed to implement correctly.

## Spec Structure

```markdown
---
title: feature-name
type: specification
created: YYYY-MM-DD
---

# Feature Name

## Abstract
One sentence: what this does and key capabilities.

## Motivation
- Problem being solved
- Impact/value

## Approach
Key technical decisions and integration points.

## Requirements

### UX Requirements

* User-facing behavior, UI components, flows, accessibility. <glassware type="requirement" id="req-feature-ux-1" />

### Business Logic Requirements

* Validation rules, workflows, calculations, state transitions. <glassware type="requirement" id="req-feature-bus-1" />

### Data Requirements

* Data structures, storage, relationships, migrations. <glassware type="requirement" id="req-feature-data-1" />

### Integration Requirements

* APIs, external services, data exchange formats. <glassware type="requirement" id="req-feature-int-1" />

### Infrastructure Requirements

* Deployment, scaling, monitoring, security. <glassware type="requirement" id="req-feature-infra-1" />

### Performance Requirements

* Latency targets, throughput, resource limits. <glassware type="requirement" id="req-feature-perf-1" />

### Quality Requirements

* Test coverage, error handling, edge cases. <glassware type="requirement" id="req-feature-qual-1" />
```

## Glassware Tag Format

**CRITICAL:** Place glassware tags at the END of the requirement line, not on a separate line:

```markdown
# CORRECT - tag at end of line
* Login page shows "Continue with Google" button. <glassware type="requirement" id="req-auth-ux-1" />

# WRONG - tag on separate line (glassware won't parse this)
<glassware type="requirement" id="req-auth-ux-1" />
Login page shows "Continue with Google" button.
```

## ID Conventions

Use unique, namespaced IDs to avoid collisions across spec files:
- `req-auth-ux-1` (feature: auth, category: ux, number: 1)
- `req-ws-bus-3` (feature: workspace, category: business logic, number: 3)
- `req-collab-data-2` (feature: collaboration, category: data, number: 2)

## Writing Good Requirements

**Do:**
- Be specific and testable (e.g., "bcrypt with cost=12", not "secure hashing")
- Include acceptance criteria
- Use namespaced IDs to avoid duplicates (req-auth-ux-1, not req-ux-1)
- Place glassware tag at END of the requirement line

**Don't:**
- Write vague requirements ("make it fast")
- Skip edge cases and error states
- Forget to specify data formats and validation rules
- Put glassware tags on their own line

## Spec Location

Save to: `docs/specs/<feature-name>.spec.md` or `specs/<feature-name>.md`
