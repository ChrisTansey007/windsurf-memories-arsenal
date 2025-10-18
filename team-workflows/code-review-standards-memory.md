# Code Review Standards Memory

## Overview

This Memory defines our team's code review process, standards, and expectations. All code must go through review before merging to main.

## Code Review Philosophy

**Our principles:**
- **Be kind and constructive** - Reviews are learning opportunities
- **Focus on the code, not the person** - Critique work, not people
- **Explain the "why"** - Don't just say "change this", explain reasoning
- **Praise good work** - Call out clever solutions and improvements
- **Respond promptly** - Review within 24 hours
- **Keep discussions focused** - Side conversations go to separate threads

## Review Checklist

### Code Quality
- [ ] Code follows project conventions
- [ ] No code duplication (DRY principle)
- [ ] Functions/methods are single-purpose
- [ ] Variable and function names are clear
- [ ] No magic numbers or strings
- [ ] Error handling is comprehensive
- [ ] Edge cases are considered

### Testing
- [ ] Unit tests added for new functionality
- [ ] Tests cover edge cases
- [ ] Existing tests still pass
- [ ] Test coverage maintained or improved
- [ ] Integration tests added if needed

### Security
- [ ] No hardcoded secrets or credentials
- [ ] Input validation present
- [ ] SQL injection prevention
- [ ] XSS prevention
- [ ] Authentication/authorization checked
- [ ] Sensitive data properly handled

### Performance
- [ ] No obvious performance issues
- [ ] Database queries optimized
- [ ] No N+1 queries
- [ ] Appropriate caching used
- [ ] Large datasets paginated

### Documentation
- [ ] Public APIs documented
- [ ] Complex logic commented
- [ ] README updated if needed
- [ ] CHANGELOG updated
- [ ] API docs updated

### UI/UX (if applicable)
- [ ] Responsive design works
- [ ] Accessibility standards met
- [ ] Loading states handled
- [ ] Error states handled
- [ ] User feedback provided

## Review Categories

### ✅ Approve
**When to use:**
- All checklist items passed
- No blocking issues
- Minor comments only

**Actions:**
- Approve the PR
- Add any optional suggestions as comments
- Merge is allowed

### 💬 Comment
**When to use:**
- Questions about implementation
- Suggestions for improvement
- Non-blocking feedback
- Educational comments

**Actions:**
- Leave comments
- PR can be merged without changes
- Author decides whether to address

### 🔄 Request Changes
**When to use:**
- Blocking issues found
- Security concerns
- Breaking changes
- Major bugs
- Missing critical tests

**Actions:**
- Clearly explain what needs to change
- Provide examples if helpful
- Block merge until addressed

## Comment Templates

### Suggesting an Alternative

```markdown
**Alternative approach:**

Consider using X instead of Y because [reason].

```typescript
// Suggested approach
const result = await processData(data);
```

This would improve [performance/readability/etc.].
```

### Asking for Clarification

```markdown
**Question:**

Could you explain the reasoning behind [specific decision]?

I'm wondering if we could also consider [alternative approach].
```

### Pointing Out an Issue

```markdown
**Issue:**

This could cause [problem] when [condition].

**Suggestion:**
```typescript
// Add validation
if (!data) {
  throw new Error('Data is required');
}
```
```

### Praising Good Work

```markdown
**Nice work!** 👏

This is a really clean solution to [problem]. I especially like how you [specific thing].
```

## What to Look For

### Code Smells
- **Long functions** - Break down into smaller functions
- **Deep nesting** - Use early returns or extract functions
- **Repeated code** - Extract to shared utility
- **Large classes** - Consider splitting responsibilities
- **Too many parameters** - Use options object
- **Magic values** - Define constants

### Common Issues
- **Missing error handling** - What happens if API fails?
- **Unhandled edge cases** - What if array is empty?
- **Poor naming** - `data`, `temp`, `x` are not descriptive
- **Commented-out code** - Delete it, we have git
- **Console.logs left in** - Remove debug code
- **Inconsistent formatting** - Run prettier/linter

### Best Practices
- **Single Responsibility** - Each function does one thing
- **Open/Closed Principle** - Open for extension, closed for modification
- **Don't Repeat Yourself** - Extract common code
- **Keep It Simple** - Simplest solution that works
- **You Aren't Gonna Need It** - Don't add unnecessary features
- **Composition over Inheritance** - Prefer composing objects

## Response Time Expectations

### For Reviewers
- **Small PRs (< 100 lines):** Review within 4 hours
- **Medium PRs (100-500 lines):** Review within 24 hours
- **Large PRs (> 500 lines):** Review within 48 hours
- **Urgent/hotfix PRs:** Review within 1 hour

### For Authors
- **Respond to comments:** Within 24 hours
- **Address feedback:** Within 48 hours
- **Request re-review:** Immediately after changes

## Pull Request Size Guidelines

**Ideal PR sizes:**
- **Small:** < 100 lines (Preferred)
- **Medium:** 100-500 lines (Acceptable)
- **Large:** 500-1000 lines (Requires justification)
- **X-Large:** > 1000 lines (Should be split)

**If PR is too large:**
- Split into multiple PRs
- Use feature branches
- Incremental development
- Pair programming instead

## Merge Requirements

**All PRs must have:**
- [ ] At least 1 approval
- [ ] All comments resolved
- [ ] All CI checks passing
- [ ] No merge conflicts
- [ ] Up-to-date with base branch

**Additional requirements for:**

**Production changes:**
- [ ] 2 approvals required
- [ ] QA sign-off
- [ ] Security review (if applicable)

**Database changes:**
- [ ] Migration tested
- [ ] Rollback plan documented
- [ ] DBA review

**Breaking changes:**
- [ ] Migration guide provided
- [ ] Deprecation warnings added
- [ ] Documentation updated
- [ ] Team notified

## Self-Review Checklist

**Before requesting review:**

- [ ] Read through your own changes
- [ ] Remove debug code and console.logs
- [ ] Run linter and fix issues
- [ ] Run all tests locally
- [ ] Update documentation
- [ ] Write clear PR description
- [ ] Add screenshots if UI changes
- [ ] Request specific reviewers
- [ ] Add appropriate labels

## Difficult Situations

### Disagreements
1. **Discuss respectfully** - Both sides explain reasoning
2. **Seek consensus** - Find middle ground
3. **Escalate if needed** - Team lead makes final call
4. **Document decision** - Add comment explaining outcome

### Blocked PRs
1. **Author:** Address feedback or explain why not
2. **Reviewer:** Be specific about what needs to change
3. **Both:** Hop on a call if comments aren't resolving it

### Stale PRs
- **After 3 days:** Reviewer pings author
- **After 7 days:** Tech lead reviews
- **After 14 days:** Close or assign new owner

## Code Review Anti-Patterns

**Avoid these:**

❌ **Nitpicking** - Excessive focus on minor style issues
Use linters and formatters instead

❌ **Drive-by comments** - Single comment without full review
Complete the review before submitting

❌ **Rubber stamping** - Approving without actually reviewing
Take time to understand changes

❌ **Scope creep** - Asking for unrelated changes
File separate issues for out-of-scope items

❌ **Bike-shedding** - Debating trivial matters
Focus on what's important

❌ **Being a blocker** - Requesting changes for personal preferences
Save "request changes" for real issues

## Examples of Good Review Comments

### Constructive Feedback

```markdown
This works, but we could improve performance here:

```typescript
// Current: O(n²)
items.forEach(item => {
  related.find(r => r.id === item.relatedId);
});

// Suggested: O(n)
const relatedMap = new Map(related.map(r => [r.id, r]));
items.forEach(item => {
  const rel = relatedMap.get(item.relatedId);
});
```

This would scale better with larger datasets.
```

### Asking Questions

```markdown
Could you help me understand the edge case where `data` might be undefined?

Should we add a guard clause at the start of the function?
```

### Suggesting Best Practices

```markdown
Consider extracting this validation logic into a reusable validator:

This pattern appears in several places, and centralizing it would:
- Make it easier to maintain
- Ensure consistent validation
- Simplify testing

Happy to create a follow-up issue if you'd prefer to handle it separately.
```

### Positive Feedback

```markdown
Really nice refactoring! 🎉

The new structure is much easier to follow. I especially like how you:
- Separated concerns between data fetching and rendering
- Added proper error boundaries
- Included loading states

This is exactly the pattern we should follow elsewhere.
```

## Metrics We Track

**Team metrics:**
- Average time to first review
- Average time to merge
- PR size distribution
- Review participation rate
- Comments per PR

**Individual metrics (for growth, not evaluation):**
- PRs submitted
- Reviews completed
- Response time
- Approval rate

## Tools We Use

- **GitHub:** PR platform
- **GitHub Actions:** CI/CD
- **CodeCov:** Coverage tracking
- **SonarQube:** Code quality
- **Prettier:** Code formatting
- **ESLint:** JavaScript linting
- **Black:** Python formatting
- **MyPy:** Python type checking

## Review Etiquette

### For Authors

**Do:**
- Write clear PR descriptions
- Keep PRs small and focused
- Respond to feedback promptly
- Be open to suggestions
- Thank reviewers

**Don't:**
- Take feedback personally
- Argue about every comment
- Ignore feedback
- Merge without approval
- Get defensive

### For Reviewers

**Do:**
- Review promptly
- Be specific and constructive
- Explain reasoning
- Acknowledge good work
- Ask questions instead of demanding

**Don't:**
- Be dismissive or condescending
- Demand changes for preferences
- Approve without reviewing
- Leave vague comments
- Forget to follow up

## Learning from Reviews

**For everyone:**
- Reviews are learning opportunities
- Good patterns should be documented
- Bad patterns should be discussed
- Share knowledge in team meetings
- Update this Memory as we learn

## Summary

**Key takeaways:**
1. Be kind, constructive, and respectful
2. Focus on code quality, security, and performance
3. Review promptly (within 24 hours)
4. Keep PRs small (< 500 lines preferred)
5. Use the review checklist
6. Explain your reasoning
7. Learn from every review

**Remember:** Code reviews make us all better developers! 🚀
