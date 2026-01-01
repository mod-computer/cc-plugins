---
description: Write a design document explaining architecture through principles and trade-offs
---

# Write DESIGN.md

**Output:** `DESIGN.md` at project root

## Process

### 1. Gather Context

Ask the user:
- What are the core principles informing this design?
- What does this system do "under the hood"?
- What are the current limitations vs. the long-term vision?

Explore the codebase to understand:
- Core abstractions and data structures
- How components interact
- Key implementation decisions and their rationale

### 2. Write Design Documentation

Follow the glassware approach: **explain architecture through principles and honest trade-offs**.

Structure:

```markdown
# [Project] Design

Under the hood, [Project] is [one-sentence description of what it really is
at a technical level - e.g., "a tool for building a graph database as an
overlay on source code"].

## Principles

There are a few key principles which inform the design of [Project]:

* [Principle name] - [explanation of what it means in practice and why it matters]
* [Principle name] - [explanation]
* [Principle name] - [explanation]

## Overview

[Explain how it works conceptually. Use code examples to illustrate.
"What exactly is X? Different Y have different Z, so..."
Help the reader understand the mental model.]

## Current Implementation (MVP)

[Be honest about scope: "The MVP implementation is much less flexible than
the design described in the overview. There is no X, we just scan all Y.
The bones are there though."]

### [Subsystem 1]

[Explain in detail with code examples. Include reasoning:
"This design is deliberately general: while the MVP has only X,
the underlying model supports Y, setting the foundation for Z."]

### [Subsystem 2]

[Explain trade-offs honestly: "This is inefficient, we copy everything
and build from scratch, but it is robust and simple to implement.
If/when this becomes a performance problem we can move to..."]

### [Subsystem 3]

[Continue for each major component]

### Relationship to the General Vision

[Where does the current implementation sit vs. the full vision?
What's additive (just add new modules)? What requires changes?
"Configuration is the last piece. The MVP hardcodes X. A future
version would move this to Y, allowing projects to define their own Z."]

### Testing Strategy

[How is it tested and why that approach?
"The key design principle is that tests should operate the external API...
This makes tests very robust to refactoring."]
```

## Key Principles

- **State principles up front** - Then show how they manifest in implementation
- **Be honest about limitations** - Use phrases like "expedient", "will probably be replaced", "much less flexible"
- **Explain the "why"** - Every implementation choice should have reasoning
- **Show the path forward** - How does MVP relate to the full vision?
- **Use code examples** - Illustrate abstractions with concrete code

## Anti-Patterns

- Describing what the code does without explaining why
- Hiding limitations or trade-offs
- Abstract architecture diagrams without narrative explanation
- Missing the connection between principles and implementation
- Treating current implementation as final rather than a step toward vision
