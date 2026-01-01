---
name: writing-readme
description: Guide for writing READMEs that give agents the right context to build correctly
---

# Writing a Repository README

A good README gives agents (and humans) the context needed to understand and build correctly in this codebase.

## Required Sections

### 1. Project Overview
- One-sentence description of what this project does
- Key technologies and frameworks used
- Architecture pattern (monorepo, microservices, monolith, etc.)

### 2. Directory Structure
```
project/
├── src/           # What lives here
├── packages/      # If monorepo, list key packages
├── tests/         # Test organization
└── docs/          # Specs, RFCs, design docs
```

### 3. Key Patterns
- How files are organized (feature-first, layer-first, etc.)
- Naming conventions for files, functions, components
- Where new features should be added
- Import/export patterns

### 4. Development Commands
```bash
# Essential commands only
pnpm install      # Setup
pnpm dev          # Run locally
pnpm test         # Run tests
pnpm build        # Build for production
```

### 5. Specifications & Traceability
- Where specs live (e.g., `.mod/specs/` or `docs/specs/`)
- How to write specs (link to writing-feature-spec skill)
- How traces work with glasswear annotations

## Anti-Patterns to Avoid

- Overly long READMEs that bury key information
- Missing architecture context (agents will guess wrong)
- No mention of where new code should go
- Missing test expectations

## Template

```markdown
# Project Name

One-sentence description.

## Tech Stack
- Frontend: [framework]
- Backend: [framework]
- Database: [type]

## Structure
[brief directory overview]

## Development
[essential commands]

## Patterns
[key conventions agents should follow]

## Specs
Specifications live in `[path]`. See [link] for writing specs.
```
