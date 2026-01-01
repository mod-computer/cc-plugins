---
description: Write an RFC specifying a concrete, implementable scope with detailed interfaces
---

# Write RFC

**Output:** `rfcs/NNNN-title.md` (e.g., `rfcs/0001-mvp.md`)

## Process

### 1. Gather Context

Ask the user:
- What's the relationship to README/DESIGN? What part does this RFC implement?
- What are the motivating use cases? What questions should this answer?
- What's the interface (CLI commands, API endpoints, UI flows)?

Determine the RFC number:
- Check existing `rfcs/` directory for the next number
- Use format: `0001-descriptive-name.md`

### 2. Write RFC

Follow the glassware approach: **specify a concrete, implementable scope with detailed interface definitions**.

Structure:

```markdown
# [Title]

## Introduction

[Describe what this RFC covers and how it relates to other docs:
"This RFC describes an initial, minimally useful version of [Project]
which demonstrates the key ideas described aspirationally in the
README.md and DESIGN.md documents. Those documents describe [expansive
vision]. As a first version though, we choose a much more restricted scope."

"The objective in this RFC is to implement [specific, bounded goal]."]

## Use Case

[The motivating scenario. Be specific about what questions this should answer:

"The motivating use case for this MVP is to [goal]. The codebase is
assumed to contain [assumptions].

There are a few questions I think we will want to answer:

* [Specific question 1]
* [Specific question 2]

More interesting questions arise when [scenario]. In this case I think
we want to ask:

* [Question]
  * [Sub-question]
  * [Sub-question]
* [Question]"]

## [Interface Type] Interface

[Detailed specification of how users interact. Be precise:

"The `command` can be run [where/when]. In order for this to work we
need to [requirements]. We do this by [approach]. This assumption will
change in the long term, but for now it is expedient."

For CLI tools:
- Each command with arguments
- Expected outputs (show examples)
- Exit codes and their meanings
- Edge cases and error handling

For APIs:
- Endpoints with request/response formats
- Authentication requirements
- Error responses]

### [Feature Subsection]

[Break down complex features. Use numbered steps:

"The diff command also analyzes [what] by:
1. [Step 1]
2. [Step 2]
3. [Step 3]
4. [Step 4]

This mapping is included in [where]. [Edge cases] are tracked as [what]."]

## [Syntax/Format Name]

[If there's a DSL, annotation format, or data structure, specify completely:

"The specific syntax depends on [context]. We have [N] kinds of [thing]:
[type 1] and [type 2]."

For each context/language:
- Show complete examples
- Explain validation rules
- Cover edge cases

"**Validation**: [Rule]. If [condition], the parser should report
an error indicating [what information].

**Important**: For [edge case], [specific requirement]. This allows
for [capability]. The [field] must match [constraint]."]

## Implementation

[Technical approach - what tools/libraries, key decisions:

"[Project] is a [language] project. We will need:

* [dependency] for [purpose]
* [dependency] for [purpose]"]

---

## Appendix A: [Format Name]

[Detailed schemas and examples. This is where precision matters:

"The `command` outputs a JSON object with the following structure:

**Fields:**
* `field1`: [description]
* `field2`: An object containing:
  * `subfield`: [description]

**Example output:**
```json
{
  "field1": "value",
  ...
}
```"]

## Appendix B: [Another Format]

[Continue with additional detailed specifications as needed]
```

## Key Principles

- **Scope explicitly** - What's in vs. out of this RFC
- **Specify interfaces precisely** - Exit codes, formats, validation rules, edge cases
- **Use appendices for details** - Keep main text readable, put schemas in appendices
- **Include examples everywhere** - Every format/syntax needs concrete examples
- **Be honest about expedience** - "This assumption will change, but for now..."

## Anti-Patterns

- Vague interface specifications ("returns data")
- Missing exit codes or error handling
- Assuming readers know the context from other docs
- Schemas without examples
- Mixing aspirational vision with concrete specification
