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
<glassware type="requirement" id="req-ux-1" />
User-facing behavior, UI components, flows, accessibility.

### Business Logic Requirements
<glassware type="requirement" id="req-bus-1" />
Validation rules, workflows, calculations, state transitions.

### Data Requirements
<glassware type="requirement" id="req-data-1" />
Data structures, storage, relationships, migrations.

### Integration Requirements
<glassware type="requirement" id="req-int-1" />
APIs, external services, data exchange formats.

### Infrastructure Requirements
<glassware type="requirement" id="req-infra-1" />
Deployment, scaling, monitoring, security.

### Performance Requirements
<glassware type="requirement" id="req-perf-1" />
Latency targets, throughput, resource limits.

### Quality Requirements
<glassware type="requirement" id="req-qual-1" />
Test coverage, error handling, edge cases.
```

## Writing Good Requirements

**Do:**
- Be specific and testable (e.g., "bcrypt with cost=12", not "secure hashing")
- Include acceptance criteria
- Use hierarchical IDs for sub-requirements (req-ux-1, req-ux-1a, req-ux-1b)
- Add glassware tags for traceability

**Don't:**
- Write vague requirements ("make it fast")
- Skip edge cases and error states
- Forget to specify data formats and validation rules

## Spec Location

Save to: `docs/specs/<feature-name>.spec.md` or `.mod/specs/<feature-name>.spec.md`
