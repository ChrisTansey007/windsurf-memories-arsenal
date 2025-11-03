---
id: mem.closure-checklist
type: memory
title: Closure Checklist - Team Standards for Completion
tags: [quality, closure, placeholders, cleanup, finalization, pre-launch]
summary: Team-specific closure criteria and placeholder detection patterns. Complements the Closure Audit rule with organization-specific standards for what constitutes "truly done."
version: 1
last_updated: 2025-10-31
---

# Closure Checklist Memory

**What Cascade remembers:** Your team's specific closure criteria, placeholder patterns to detect, and what "truly done" means before shipping.

**Works with:** [Closure Audit Rule](https://github.com/ChrisTansey007/ai-rules-arsenal/blob/main/windsurf/by-domain/closure-audit.md)

---

## 🎯 Purpose

This memory defines **team-specific closure standards** that complement the universal Closure Audit rule. It captures:
- Your organization's placeholder patterns
- Team-specific "done" criteria
- Acceptable tech debt thresholds
- Ownership and review requirements
- Domain-specific closure gates

---

## 🚨 Our Team's Placeholder Patterns

### Code Markers (Auto-Detect)

**Critical (P0) - Must fix before merge:**
- `TODO:` in production code paths
- `FIXME:` anywhere
- `HACK:` in critical systems
- `XXX:` (urgent attention needed)
- `NotImplementedError` in called functions
- `pass` in non-abstract methods
- Commented-out code blocks >10 lines

**Important (P1) - Must fix before release:**
- `@TODO` in comments
- `TEMP:` markers
- `console.log` / `print` in production code
- `debugger` statements
- Hardcoded credentials or secrets
- `localhost` / `127.0.0.1` in configs

**Acceptable (P2) - Can defer with owner:**
- `// TODO: Optimize` (performance improvements)
- `// FUTURE:` (planned enhancements)
- `@deprecated` (with migration plan)

### Config/Environment Markers

**Critical (P0):**
- `YOUR_API_KEY_HERE`
- `changeme`
- `placeholder`
- `development` mode in production configs
- Missing required environment variables
- Expired SSL certificates

**Important (P1):**
- `.env.example` with actual secrets
- Hardcoded database URLs
- Debug mode enabled
- Verbose logging in production

### Documentation Markers

**Critical (P0):**
- `[TODO]` in user-facing docs
- Broken links in README
- Missing API documentation for public endpoints

**Important (P1):**
- `TBD` in internal docs
- `coming soon` in changelogs
- `[citation needed]` in research docs
- `lorem ipsum` placeholder text

**Acceptable (P2):**
- `DRAFT:` sections (with review date)
- Incomplete examples (with "WIP" label)

---

## 📋 Our Team's Closure Gates

### Software/DevOps Closure

**Must have before merge:**
- ✅ Zero P0/P1 TODOs in code
- ✅ All tests passing (no skipped tests without justification)
- ✅ No placeholder configs (.env files clean)
- ✅ Health check endpoint implemented and passing
- ✅ Error logs clean (no noisy warnings)
- ✅ Linter passing with 0 errors
- ✅ Security scan clean (no high/critical vulnerabilities)
- ✅ PR description complete (what/why/how/testing)
- ✅ At least 1 peer approval
- ✅ Runbook updated (if ops-impacting)

**Must have before production deploy:**
- ✅ All of the above, plus:
- ✅ Monitoring/alerts configured
- ✅ Rollback procedure documented
- ✅ Load testing completed (if high-traffic)
- ✅ Stakeholder sign-off
- ✅ Deployment checklist completed

### Data/Analytics Closure

**Must have before sharing results:**
- ✅ All notebooks checked into version control
- ✅ Dataset hash/snapshot recorded
- ✅ Temp files removed or archived
- ✅ All claims have statistical support or "directional" label
- ✅ Charts/tables have labels, units, sources
- ✅ No `[citation needed]` or placeholder text
- ✅ Reproducibility instructions included
- ✅ Peer review completed

**Must have before production pipeline:**
- ✅ All of the above, plus:
- ✅ Data quality metrics documented
- ✅ Error handling for edge cases
- ✅ Monitoring/alerting configured
- ✅ Backfill procedure documented
- ✅ Stakeholder approval

### Research/Writing Closure

**Must have before publication:**
- ✅ ≥3 primary sources for key claims
- ✅ All citations present and formatted correctly
- ✅ Broken links fixed
- ✅ Executive summary complete
- ✅ Key takeaways section present
- ✅ Limitations section included
- ✅ All acronyms defined on first use
- ✅ No TBD/coming soon sections
- ✅ Plagiarism check passed
- ✅ Named reviewer approval
- ✅ Next review date scheduled

---

## 🎯 Acceptable Tech Debt Criteria

### When P2 (Deferred) is Acceptable

**Must have ALL of:**
1. ✅ **Explicit rationale** - Why deferring is acceptable
2. ✅ **Named owner** - Who will address it
3. ✅ **Due date** - When it will be addressed
4. ✅ **Tracking ticket** - Created in issue tracker
5. ✅ **Risk assessment** - What could go wrong if not fixed
6. ✅ **Stakeholder approval** - Product/Engineering manager sign-off

**Examples of acceptable P2 debt:**
```markdown
## P2: Optimize database query performance
**Rationale:** Current performance acceptable (<500ms p95), optimization can wait
**Owner:** Backend Team Lead
**Due:** Sprint 23 (2 weeks)
**Ticket:** JIRA-1234
**Risk:** Query may slow down as data grows, monitor p95 latency
**Approved by:** Engineering Manager (2025-10-31)
```

### When Debt is NOT Acceptable

**Never defer (must be P0/P1):**
- ❌ Security vulnerabilities
- ❌ Data privacy issues
- ❌ Compliance violations
- ❌ User-facing bugs
- ❌ Production incidents
- ❌ Broken critical functionality
- ❌ Hardcoded secrets
- ❌ Missing error handling in critical paths

---

## 🔍 Our Team's Discovery Methods

### Pass 1: Automated Scans

```bash
# Text marker search
grep -r "TODO\|FIXME\|HACK\|XXX\|TBD\|TEMP" \
  --exclude-dir={node_modules,dist,build,.git} .

# Placeholder config search
grep -r "YOUR_.*_HERE\|changeme\|placeholder" \
  --include=*.env* --include=*.config.* .

# Debug statement search
grep -r "console\.log\|debugger\|print(" \
  --include=*.{js,ts,py} --exclude-dir={node_modules,__pycache__} .

# Broken link check (for docs)
markdown-link-check **/*.md
```

### Pass 2: Manual Review

**Code review checklist:**
- [ ] Read through all changed files
- [ ] Check for commented-out code
- [ ] Verify error handling present
- [ ] Check for hardcoded values
- [ ] Review test coverage

**Config review checklist:**
- [ ] All environment variables documented
- [ ] No secrets in version control
- [ ] Production configs separate from dev
- [ ] All required configs present

**Documentation review checklist:**
- [ ] README up to date
- [ ] API docs match implementation
- [ ] Changelog updated
- [ ] Migration guide (if breaking changes)

### Pass 3: Automated Testing

```bash
# Run full test suite
npm run test

# Run linter
npm run lint

# Run security scan
npm audit
# or
snyk test

# Run type checker
npm run type-check
```

### Pass 4: Deployment Smoke Test

```bash
# Deploy to staging
./deploy-staging.sh

# Run smoke tests
curl https://staging.example.com/health
curl https://staging.example.com/api/v1/status

# Check logs for errors
kubectl logs -l app=myapp --since=5m | grep ERROR
```

---

## 📊 Closure Metrics We Track

### Code Quality Metrics

**Target thresholds:**
- **TODO count:** 0 in production code
- **Test coverage:** ≥80% overall, ≥90% for critical paths
- **Linter errors:** 0
- **Security vulnerabilities:** 0 high/critical
- **Code duplication:** <3%

**Track over time:**
- TODOs added vs removed per sprint
- Average time TODO remains in codebase
- % of PRs merged with TODOs (target: <2%)

### Deployment Readiness Metrics

**Pre-deploy checklist completion:**
- % of deploys with all checklist items complete (target: 100%)
- Average time from "code complete" to "deploy ready"
- % of deploys requiring rollback (target: <1%)

### Documentation Completeness

**Track:**
- % of API endpoints with documentation (target: 100%)
- % of docs with broken links (target: 0%)
- % of docs with TBD/placeholder text (target: 0%)

---

## 🎯 Domain-Specific Closure Criteria

### Frontend Closure

**Must have:**
- ✅ Accessibility audit passed (WCAG 2.1 AA)
- ✅ Responsive design tested (mobile, tablet, desktop)
- ✅ Browser compatibility verified (Chrome, Firefox, Safari, Edge)
- ✅ Performance budget met (Lighthouse score ≥90)
- ✅ No console errors in production build
- ✅ Analytics events implemented and tested
- ✅ Error boundaries in place
- ✅ Loading states for all async operations

### Backend/API Closure

**Must have:**
- ✅ All endpoints have error handling
- ✅ Rate limiting configured
- ✅ Authentication/authorization on all protected endpoints
- ✅ Input validation on all user inputs
- ✅ OpenAPI/Swagger docs up to date
- ✅ Health check endpoint implemented
- ✅ Logging configured (structured logs)
- ✅ Monitoring/alerts configured

### Database Closure

**Must have:**
- ✅ Migrations tested (up and down)
- ✅ Indexes on frequently queried columns
- ✅ Foreign key constraints in place
- ✅ Backup/restore procedure tested
- ✅ Data retention policy documented
- ✅ Query performance acceptable (<500ms p95)
- ✅ Connection pooling configured

### Infrastructure/DevOps Closure

**Must have:**
- ✅ Infrastructure as code (Terraform/CloudFormation)
- ✅ Secrets in vault (not in code)
- ✅ Auto-scaling configured
- ✅ Disaster recovery plan documented
- ✅ Monitoring/alerting configured
- ✅ Runbook for common issues
- ✅ Rollback procedure tested

---

## 🔗 Related Arsenal Items

### Rules
- [Closure Audit](https://github.com/ChrisTansey007/ai-rules-arsenal/blob/main/windsurf/by-domain/closure-audit.md) ⭐ Core rule
- [Complete Problem-Solving](https://github.com/ChrisTansey007/ai-rules-arsenal/blob/main/windsurf/by-domain/complete-problem-solving.md) - Complementary
- [Prompt Quality Standards](https://github.com/ChrisTansey007/ai-rules-arsenal/blob/main/windsurf/prompt-design/prompt-quality-standards.md)

### Memories
- [Enterprise Completion Standards](./enterprise-completion-standards-memory.md) - Overall quality standards
- [Code Review Standards](https://github.com/ChrisTansey007/windsurf-memories-arsenal) - Review criteria

### Workflows
- [Run Tests and Fix](https://github.com/ChrisTansey007/ai-workflows-arsenal) - Automated testing
- [Code Review Assistant](https://github.com/ChrisTansey007/ai-workflows-arsenal) - Pre-merge review
- [Security Scan](https://github.com/ChrisTansey007/ai-workflows-arsenal) - Security validation

### Prompts
- [RuleMiner](https://github.com/ChrisTansey007/prompt-arsenal/blob/main/meta-prompting/ruleminer-extract-rules.md) - Extract closure patterns
- [Self-Score Output](https://github.com/ChrisTansey007/prompt-arsenal/blob/main/quality-assurance/self-score-output.md) - Quality validation

---

## 💡 Usage Examples

### Example 1: Using with Closure Audit

```
@closure-audit
Task = Finalize authentication feature for production
Context = Next.js app; JWT auth; merge tomorrow

[DONE overlay — Software/DevOps (Closure)]
strict:on accept_debt:low
```

Cascade will use both:
- **Closure Audit rule** (universal framework)
- **This memory** (team-specific patterns and criteria)

### Example 2: Pre-Merge Checklist

Before creating PR, check this memory:
- "What are our team's P0 markers?"
- "What closure gates must be satisfied?"
- "What's acceptable as P2 debt?"

### Example 3: Onboarding New Developers

New developers read this memory to understand:
- What placeholders are never acceptable
- How to properly defer work (P2 with owner/date)
- Team's closure standards and expectations

---

## 🎓 Customization Guide

### How to Customize This Memory

1. **Add your team's specific markers**
   ```markdown
   ## Our Custom Markers
   - `@yourname-todo` - Personal TODOs
   - `REVIEW:` - Needs team review
   - `PERF:` - Performance optimization needed
   ```

2. **Define your closure gates**
   ```markdown
   ## Our API Closure Gates
   - OpenAPI spec updated
   - Integration tests ≥90% coverage
   - Performance: p95 < 200ms
   - Security scan clean
   - Rate limiting configured
   ```

3. **Set your tech debt thresholds**
   ```markdown
   ## Our Debt Acceptance Criteria
   - P2 acceptable if: owner + due date + ticket + approval
   - Max P2 items per sprint: 5
   - Review all P2 items monthly
   ```

4. **Document your discovery methods**
   ```markdown
   ## Our Automated Scans
   - Pre-commit: lint + type-check
   - Pre-merge: full test suite + security scan
   - Pre-deploy: smoke tests + load tests
   ```

---

## 📝 Quick Reference

### Pre-Merge Checklist

- [ ] Run `@closure-audit` with `strict:on`
- [ ] Zero P0/P1 items in Closure Register
- [ ] All P2 items have owner + due date + ticket
- [ ] Evidence pack complete
- [ ] Peer review approved
- [ ] CI/CD passing

### Pre-Deploy Checklist

- [ ] All pre-merge items, plus:
- [ ] Monitoring/alerts configured
- [ ] Rollback procedure documented
- [ ] Stakeholder sign-off
- [ ] Deployment checklist complete
- [ ] Smoke tests passing in staging

### Pre-Publication Checklist (Docs/Research)

- [ ] All citations present and verified
- [ ] Broken links fixed
- [ ] No TBD/placeholder sections
- [ ] Peer review complete
- [ ] Plagiarism check passed
- [ ] Next review date scheduled

---

**Last Updated:** 2025-10-31  
**Maintained By:** Engineering Team  
**Review Frequency:** Quarterly

---

**This memory ensures Cascade knows your team's closure standards!** 🎯
