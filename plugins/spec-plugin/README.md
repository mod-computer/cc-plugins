# spec-plugin

Claude Code plugin for writing specifications and managing requirement traceability with glassware.

## Installation

First, add the cc-plugins marketplace (if not already added):

```bash
claude plugins:add-marketplace /path/to/cc-plugins
```

Then install the plugin:

```bash
claude plugins:install spec-plugin
```

Or use `/plugin` in Claude Code and select `spec-plugin`.

## Commands

### `/review <spec-file>`

Reviews a specification file against the current git branch:
- Runs `glassware` to check requirement status
- Analyzes files changed on the branch
- Identifies missing traces and unimplemented requirements
- Proposes updates to specs and code

## Skills

### `writing-readme`
Guide for writing READMEs that give agents the right context to build correctly.

### `writing-feature-spec`
Guide for writing feature specifications with UX, business logic, infra, and performance requirements.

### `implement-spec`
Guide for implementing specifications with traceability.

### `adding-traces`
Guide for adding glassware-readable traces to code.

## Glassware Annotation Format

**Requirements** (in markdown specs):

CRITICAL: The glassware tag MUST be at the END of the requirement line:
```markdown
## Feature

* Requirement description here. <glassware type="requirement" id="req-feature-1" />
```

**Implementations** (in TypeScript):
```typescript
// glassware[type=implementation, id=impl-1, requirements=req-feature-1]
function feature() { ... }
```

## Verification

Run `glassware` to check requirement coverage:

```bash
glassware
```
