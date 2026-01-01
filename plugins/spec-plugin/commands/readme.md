---
description: Write a README that explains the "why" through narrative and examples
---

# Write README.md

**Output:** `README.md` at project root

## Process

### 1. Gather Context

Ask the user:
- What's the one-sentence vision for this project?
- What problem does it solve? What's the hypothesis?
- Can you walk me through a typical usage scenario?

Explore the codebase to understand:
- Tech stack and key dependencies
- Directory structure and organization
- How someone would actually use this

### 2. Write Narrative Documentation

Follow the glassware approach: **explain the "why" through a complete walkthrough example**.

Structure:

```markdown
# Project Name

> Tagline/vision statement

[One paragraph explaining what this is and why it matters]

## Conceptual Overview

[Explain the problem being solved. Use questions the reader might ask.
Start with "You may be familiar with..." or "The hypothesis behind X is..."
Make it conversational and exploratory.]

## An Example

[Complete walkthrough showing the tool/system in action:
- Start with a simple, realistic scenario
- Show each step with actual code blocks
- Include command outputs where relevant
- Build up complexity gradually
- Explain what's happening at each step
- Use phrases like "Now if we run..." "Hang on though, what's this..."]

## How [Project] Works

[Explain the conceptual model and key abstractions.
"Different projects will have different workflows..."
Help the reader build a mental model.]

## Thoughts

[Optional: scratch space for future thinking, open questions]
```

## Key Principles

- **Lead with "why", not "what"** - Don't list features, explain the problem
- **Use a complete example** - Walk through real usage, not bullet points
- **Show real outputs** - Include actual command outputs and results
- **Be conversational** - "Hang on though...", "Let's fix that...", "Great, this is true..."
- **Avoid template-filling** - Write narrative prose that fits this specific project

## Anti-Patterns

- Overly long READMEs that bury key information
- Feature lists without context on why they matter
- Missing architecture context (readers will guess wrong)
- Abstract descriptions instead of concrete examples
- Template-style sections that don't fit the project
