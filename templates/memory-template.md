# [Memory Title] Memory

## Overview

[Brief description of what this Memory covers and when to use it]

## Purpose

[Explain the purpose and scope of this Memory]

**This Memory helps Cascade:**
- [Benefit 1]
- [Benefit 2]
- [Benefit 3]

## [Section 1: Main Topic]

### [Subsection]

[Content with specific guidelines, patterns, or standards]

**Key points:**
- [Point 1]
- [Point 2]
- [Point 3]

**Example:**
```[language]
// Code example showing the pattern
```

**Why this matters:**
[Explanation of why this standard/pattern is important]

## [Section 2: Related Topic]

### [Pattern Name]

**When to use:**
[Description of when this pattern applies]

**Implementation:**
```[language]
// Example implementation
```

**Benefits:**
- [Benefit 1]
- [Benefit 2]

**Pitfalls to avoid:**
- [Common mistake 1]
- [Common mistake 2]

## Common Patterns

### Pattern 1: [Name]

**Problem:** [What problem this solves]

**Solution:**
```[language]
// Solution code
```

**Example:**
```[language]
// Real-world example
```

### Pattern 2: [Name]

[Similar structure as Pattern 1]

## Best Practices

### Do's ✅

- **[Practice 1]:** [Why]
  ```[language]
  // Good example
  ```

- **[Practice 2]:** [Why]
  ```[language]
  // Good example
  ```

### Don'ts ❌

- **[Anti-pattern 1]:** [Why to avoid]
  ```[language]
  // Bad example
  ```

- **[Anti-pattern 2]:** [Why to avoid]
  ```[language]
  // Bad example
  ```

## Conventions

### Naming Conventions
- **[Type]:** [Convention] (e.g., `camelCase`, `PascalCase`)
- **[Type]:** [Convention]
- **[Type]:** [Convention]

### File Organization
```
[Directory structure example]
```

### Code Structure
```[language]
// Structure template
```

## Important Notes

⚠️ **Critical information:**
- [Important note 1]
- [Important note 2]
- [Important note 3]

💡 **Tips:**
- [Helpful tip 1]
- [Helpful tip 2]

## Examples

### Example 1: [Scenario Name]

**Context:** [When this applies]

**Implementation:**
```[language]
// Complete example
```

**Explanation:**
[What's happening and why]

### Example 2: [Scenario Name]

[Similar structure]

## Checklist

When [doing activity], ensure:
- [ ] [Checklist item 1]
- [ ] [Checklist item 2]
- [ ] [Checklist item 3]
- [ ] [Checklist item 4]

## Common Mistakes

### Mistake 1: [Name]

**Problem:**
[Description of the issue]

**Why it's wrong:**
[Explanation]

**Correct approach:**
```[language]
// Correct implementation
```

### Mistake 2: [Name]

[Similar structure]

## Tools & Resources

### Required Tools
- **[Tool 1]:** [Purpose]
- **[Tool 2]:** [Purpose]

### Helpful Resources
- [Resource 1]: [Link] - [Description]
- [Resource 2]: [Link] - [Description]

### Commands
```bash
# Common commands for this context
command-1
command-2
```

## Integration with Other Memories

**Works well with:**
- [Memory 1] - [How they complement each other]
- [Memory 2] - [How they complement each other]

**Supersedes:**
- [If this replaces older patterns]

## Decision Log

### Why We Do This

**[Decision 1]:**
- **Rationale:** [Why we made this choice]
- **Date:** [When decided]
- **Context:** [Circumstances]

**[Decision 2]:**
[Similar structure]

## Team-Specific Customizations

[Any team-specific variations or additions]

**Our additions:**
- [Custom rule 1]
- [Custom rule 2]

## Evolution & Updates

**Last updated:** [Date]
**Version:** [Version number]
**Changes:**
- [Change 1]
- [Change 2]

## Quick Reference

**TL;DR:**
- [Key point 1]
- [Key point 2]
- [Key point 3]
- [Key point 4]

---

## Template Usage Notes

**When creating your own Memory:**

1. **Replace all bracketed text** with your specific content
2. **Remove sections that don't apply** - Not every Memory needs every section
3. **Add sections as needed** - This is a starting point, customize freely
4. **Be specific** - Generic advice isn't helpful, provide concrete examples
5. **Include code examples** - Show, don't just tell
6. **Keep it focused** - One Memory per topic/concern
7. **Update regularly** - Memories should evolve with your project

**Good Memory characteristics:**
- ✅ Specific and actionable
- ✅ Includes real examples
- ✅ Explains the "why" not just the "what"
- ✅ Updated regularly
- ✅ Focused on one topic
- ✅ Team-reviewed and agreed upon

**Poor Memory characteristics:**
- ❌ Too generic or vague
- ❌ No examples
- ❌ Just lists of rules without context
- ❌ Out of date
- ❌ Tries to cover too much
- ❌ Individual preferences, not team standards

---

## Example Memory Structure

Here's how a well-structured Memory might look:

```markdown
# React Component Patterns Memory

## Overview
Standard patterns for React components in our application.

## Component Types

### Server Components (Default)
```tsx
// Async, server-side
export default async function UserList() {
  const users = await getUsers();
  return <div>{users.map(...)}</div>;
}
```

### Client Components (When Needed)
```tsx
'use client';
import { useState } from 'react';

export default function SearchBar() {
  const [query, setQuery] = useState('');
  return <input value={query} />;
}
```

## Props Pattern

```tsx
interface ButtonProps {
  label: string;
  onClick: () => void;
  variant?: 'primary' | 'secondary';
}

export default function Button({ label, onClick, variant = 'primary' }: ButtonProps) {
  return <button onClick={onClick}>{label}</button>;
}
```

[... continues with more specific patterns ...]
```

---

**Happy Memory creating! This template helps ensure consistency and completeness.** 💭
