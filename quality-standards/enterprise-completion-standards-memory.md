---
id: mem.enterprise-completion-standards
type: memory
title: Enterprise Completion Standards
tags: [quality, enterprise, completion, standards, audit-trail, compliance]
summary: Team-specific DONE definitions, acceptance gates, and quality standards for enterprise-grade work. Complements the Complete Problem-Solving rule.
version: 1
last_updated: 2025-10-31
---

# Enterprise Completion Standards Memory

**What Cascade remembers:** Your organization's quality standards, acceptance criteria, and what "DONE" means for different types of work.

**Works with:** [Complete Problem-Solving Rule](https://github.com/ChrisTansey007/ai-rules-arsenal/blob/main/windsurf/by-domain/complete-problem-solving.md)

---

## 🎯 Purpose

This memory defines **team-specific completion standards** that go beyond the universal Complete Problem-Solving rule. It captures:
- Your organization's DONE definitions
- Team-specific acceptance gates
- Quality thresholds and SLAs
- Compliance requirements
- Evidence standards

---

## 📋 Our Team's DONE Definitions

### Software/DevOps Work

**Standard DONE criteria:**
- ✅ **Health checks pass:** Primary endpoint returns 200 for ≥30 minutes
- ✅ **Zero errors:** Logs show no errors above INFO level (last 2 minutes)
- ✅ **Tests pass:** Build + unit tests + integration tests + type/lint = 0 failures
- ✅ **Code coverage:** ≥80% coverage for new code, ≥70% overall
- ✅ **Performance:** p95 latency < 200ms, p99 < 500ms
- ✅ **Security:** No high/critical vulnerabilities in scan
- ✅ **Documentation:** README updated, API docs current, changelog entry added
- ✅ **Review:** At least 1 peer approval on PR
- ✅ **Deployment:** Successful deploy to staging, smoke tests pass

**Critical/Production work adds:**
- ✅ **Runbook:** Incident response documented
- ✅ **Monitoring:** Alerts configured for key metrics
- ✅ **Rollback plan:** Documented and tested
- ✅ **Stakeholder approval:** Product/Engineering manager sign-off

---

### Data/Analytics Work

**Standard DONE criteria:**
- ✅ **Objective met:** Target metric achieved (state exact threshold)
- ✅ **Statistical validity:** p < 0.05 or confidence interval excludes 0
- ✅ **Sample size:** Power analysis confirms adequate sample (≥80% power)
- ✅ **Reproducibility:** Notebook + dataset hash provided, re-run confirms results
- ✅ **Peer review:** Data scientist peer validation
- ✅ **Visualization:** Clear plots/dashboards for stakeholders
- ✅ **Documentation:** Analysis doc with methodology, assumptions, limitations
- ✅ **Data quality:** Missing data < 5%, outliers investigated

**Critical decisions add:**
- ✅ **Independent validation:** Re-run with holdout sample or different time period
- ✅ **Sensitivity analysis:** Key assumptions tested
- ✅ **Stakeholder review:** Business owner approval
- ✅ **Monitoring plan:** Metrics tracked post-launch

---

### Research/Writing/Documentation

**Standard DONE criteria:**
- ✅ **Sources:** ≥3 primary/authoritative sources for key claims
- ✅ **Citations:** All claims cited with links/references
- ✅ **Counterevidence:** Major counterarguments addressed
- ✅ **Clarity:** Executive summary + key takeaways + limitations
- ✅ **Accuracy:** Technical details verified by SME
- ✅ **Completeness:** All required sections present
- ✅ **Readability:** Grammarly/spell-check clean, reading level appropriate

**External-facing docs add:**
- ✅ **Legal review:** Terms reviewed by legal (if applicable)
- ✅ **Brand compliance:** Follows brand guidelines
- ✅ **Accessibility:** WCAG 2.1 AA compliant (for web docs)
- ✅ **Stakeholder approval:** Marketing/Product sign-off

---

### Product/UX Work

**Standard DONE criteria:**
- ✅ **Prototype:** Interactive artifact available (link or build)
- ✅ **Core flow:** Primary user journey implemented
- ✅ **Usability:** Task success rate ≥90% on N≥5 users
- ✅ **Accessibility:** WCAG 2.1 AA compliant, keyboard navigation works
- ✅ **Responsive:** Works on mobile, tablet, desktop
- ✅ **Performance:** Page load < 3s, interaction < 100ms
- ✅ **Documentation:** User flow diagrams, design specs, known limitations

**Launch-ready adds:**
- ✅ **Analytics:** Event tracking implemented and tested
- ✅ **A/B test:** Experiment configured (if applicable)
- ✅ **Stakeholder approval:** Product manager + Design lead sign-off
- ✅ **Support docs:** Help articles or tooltips ready

---

### Security/Compliance Work

**Standard DONE criteria:**
- ✅ **Vulnerability scan:** No high/critical issues (CVSS ≥7.0)
- ✅ **Dependency audit:** All dependencies up-to-date, no known CVEs
- ✅ **Code review:** Security-focused review completed
- ✅ **Secrets:** No hardcoded secrets, all in vault/env vars
- ✅ **Authentication:** Proper auth/authz on all endpoints
- ✅ **Input validation:** All user inputs sanitized
- ✅ **Logging:** Security events logged (auth failures, permission denials)

**Compliance-critical adds:**
- ✅ **Audit trail:** All changes logged with timestamps and actors
- ✅ **Data privacy:** GDPR/CCPA requirements met (if applicable)
- ✅ **Penetration test:** External security audit passed
- ✅ **Compliance sign-off:** Security officer approval

---

## 🎯 Quality Thresholds

### Code Quality
- **Test coverage:** ≥80% for new code, ≥70% overall
- **Cyclomatic complexity:** ≤10 per function
- **Code duplication:** <3% duplicate code
- **Linting:** 0 errors, <5 warnings
- **Type safety:** 100% type coverage (TypeScript/Python)

### Performance
- **API latency:** p95 < 200ms, p99 < 500ms
- **Page load:** First Contentful Paint < 1.5s, Time to Interactive < 3s
- **Database queries:** <100ms for simple queries, <500ms for complex
- **Memory usage:** <500MB per service instance

### Reliability
- **Uptime:** 99.9% SLA (43 minutes downtime/month max)
- **Error rate:** <0.1% of requests
- **Recovery time:** <15 minutes for P0 incidents
- **Data loss:** Zero tolerance

---

## 📊 Evidence Standards

### What to Include in Evidence Packs

**For Production Deployments:**
1. Health check screenshot/link (30+ minutes uptime)
2. Log excerpt (last 2 minutes, no errors)
3. Test results summary (all passing)
4. Performance metrics (latency, error rate)
5. PR link with approvals
6. Deployment timestamp and version

**For Data Analysis:**
1. Statistical summary (p-values, confidence intervals, effect sizes)
2. Plots/visualizations (with clear labels)
3. Notebook link + dataset hash
4. Peer review notes
5. Dashboard link (if applicable)

**For Security Work:**
1. Vulnerability scan report
2. Dependency audit results
3. Code review notes (security-focused)
4. Penetration test results (if applicable)
5. Compliance checklist (completed)

**For Documentation:**
1. Published doc link
2. Review/approval trail
3. Grammarly/spell-check results
4. Accessibility audit (if web doc)
5. Stakeholder sign-offs

---

## 🔄 When to Use Complete-Mode

### Always Use (Mandatory)

- ✅ Production incidents (P0/P1)
- ✅ Security vulnerabilities
- ✅ Compliance-related changes
- ✅ Data migrations
- ✅ Infrastructure changes
- ✅ Public-facing launches
- ✅ Revenue-impacting features

### Recommended Use

- ✅ Critical features (high user impact)
- ✅ Complex bug fixes (multiple root causes)
- ✅ Performance optimizations
- ✅ Database schema changes
- ✅ API contract changes
- ✅ Third-party integrations

### Optional Use

- ⚠️ Internal tools (lower stakes)
- ⚠️ Experimental features (behind feature flags)
- ⚠️ Documentation updates (non-critical)
- ⚠️ Refactoring (no behavior change)

### Skip (Use Normal Workflow)

- ❌ Typo fixes
- ❌ Comment updates
- ❌ Dependency version bumps (patch versions)
- ❌ Simple UI tweaks

---

## 🎓 Team-Specific DONE Overlays

### Our API Standard

```markdown
[DONE overlay — Our Team's API Standard]
- OpenAPI spec: Updated and validated (swagger-cli validate passes)
- Tests: Integration tests ≥90% coverage, all passing
- Performance: p95 < 200ms, p99 < 500ms (load test with 1000 RPS)
- Security: Scan clean (no high/critical), auth on all endpoints
- Documentation: API docs published, changelog updated, migration guide (if breaking)
- Monitoring: Alerts configured (error rate >1%, latency >500ms)
- Stakeholder approval: Product manager + Tech lead sign-off
```

### Our Frontend Standard

```markdown
[DONE overlay — Our Team's Frontend Standard]
- Build: Production build succeeds, bundle size <500KB
- Tests: Unit tests ≥80% coverage, E2E tests for critical flows
- Performance: Lighthouse score ≥90 (Performance, Accessibility, Best Practices)
- Accessibility: WCAG 2.1 AA compliant, keyboard navigation works
- Responsive: Works on mobile (375px), tablet (768px), desktop (1440px)
- Browser support: Chrome, Firefox, Safari, Edge (latest 2 versions)
- Documentation: Component docs in Storybook, design specs linked
- Review: Design lead approval + peer code review
```

### Our Data Pipeline Standard

```markdown
[DONE overlay — Our Team's Data Pipeline Standard]
- Data quality: <1% missing data, outliers investigated
- Performance: Pipeline completes in <30 minutes (for daily batch)
- Monitoring: Data quality alerts configured, pipeline failure alerts
- Reproducibility: SQL/code in version control, data lineage documented
- Testing: Unit tests for transformations, integration test with sample data
- Documentation: Pipeline diagram, data dictionary, runbook for failures
- Validation: Output validated against known-good dataset
- Stakeholder approval: Data engineering lead sign-off
```

---

## 🚨 Incident Response Standards

### P0 (Critical) Incidents

**DONE criteria:**
- ✅ Service restored (health checks passing ≥30 minutes)
- ✅ Root cause identified and documented
- ✅ Permanent fix deployed (not just workaround)
- ✅ Monitoring/alerting improved (prevent recurrence)
- ✅ Runbook updated
- ✅ Post-mortem completed (within 48 hours)
- ✅ Action items assigned and tracked

**Evidence pack:**
- Incident timeline (start, detection, mitigation, resolution)
- Root cause analysis
- Fix PR with before/after metrics
- Updated runbook
- Post-mortem doc link

### P1 (High) Incidents

**DONE criteria:**
- ✅ Issue resolved (verified by reporter)
- ✅ Root cause documented
- ✅ Fix deployed and verified
- ✅ Monitoring improved (if applicable)
- ✅ Brief incident summary

**Evidence pack:**
- Issue description + resolution
- Fix PR
- Verification results

---

## 📈 Success Metrics

### Track These Metrics

**Quality:**
- % of work completed on first attempt (target: ≥95%)
- Rework rate (target: <5%)
- Defect escape rate (target: <1%)

**Speed:**
- Time to DONE (track by work type)
- Time saved by avoiding rework
- Incident MTTR (Mean Time To Resolution)

**Compliance:**
- % of critical work with complete audit trails (target: 100%)
- % of security scans with 0 high/critical (target: ≥95%)
- % of compliance requirements met (target: 100%)

---

## 🔗 Related Arsenal Items

### Rules
- [Complete Problem-Solving](https://github.com/ChrisTansey007/ai-rules-arsenal/blob/main/windsurf/by-domain/complete-problem-solving.md) ⭐ Core rule
- [Prompt Quality Standards](https://github.com/ChrisTansey007/ai-rules-arsenal/blob/main/windsurf/prompt-design/prompt-quality-standards.md)
- [Next.js App Router](https://github.com/ChrisTansey007/ai-rules-arsenal/blob/main/windsurf/by-framework/nextjs-app-router.md)
- [FastAPI Python](https://github.com/ChrisTansey007/ai-rules-arsenal/blob/main/windsurf/by-framework/fastapi-python.md)

### Workflows
- [Run Tests and Fix](https://github.com/ChrisTansey007/ai-workflows-arsenal) - Automated testing
- [Security Scan](https://github.com/ChrisTansey007/ai-workflows-arsenal) - Security validation
- [Code Review Assistant](https://github.com/ChrisTansey007/ai-workflows-arsenal) - Pre-commit review

### Prompts
- [Self-Score Output](https://github.com/ChrisTansey007/prompt-arsenal/blob/main/quality-assurance/self-score-output.md) - Quality validation
- [Prompt Forensics Analyzer](https://github.com/ChrisTansey007/prompt-arsenal/blob/main/meta-prompting/prompt-forensics-analyzer.md) - Post-completion analysis

### Examples
- [Enterprise Quality Setup](https://github.com/ChrisTansey007/arsenal-integration-hub/tree/main/examples/enterprise-quality) - Complete integration guide

---

## 💡 Customization Guide

### How to Customize This Memory

1. **Update quality thresholds** to match your team's standards
2. **Add team-specific DONE overlays** for your common work types
3. **Define your SLAs** and performance targets
4. **Document your compliance requirements** (GDPR, SOC2, HIPAA, etc.)
5. **Add your monitoring/alerting standards**
6. **Include your review/approval processes**

### Example: Adding a New Overlay

```markdown
### Our Mobile App Standard

[DONE overlay — Our Team's Mobile App Standard]
- Build: iOS + Android builds succeed, no warnings
- Tests: Unit tests ≥80%, UI tests for critical flows
- Performance: App launch <2s, screen transitions <300ms
- Size: APK <50MB, IPA <100MB
- Compatibility: iOS 14+, Android 10+
- Accessibility: VoiceOver/TalkBack support, dynamic type
- Store: Screenshots updated, release notes written
- Review: Mobile lead approval + QA sign-off
```

---

## 📝 Usage Examples

### Example 1: Using with Complete-Mode

```
@complete-mode
Task = Fix payment processing bug in production
Context = Stripe integration; affecting 10% of transactions; $50k/day revenue impact

[DONE overlay — Our Team's API Standard]
scope:payment-flow depth:deep risk_tolerance:low strict:on
```

Cascade will use both:
- **Complete-mode rule** (universal framework)
- **This memory** (team-specific API standard)

### Example 2: Quick Reference During Work

When working on a feature, check this memory:
- "What's our DONE criteria for frontend work?"
- "What evidence do I need for the PR?"
- "Do I need complete-mode for this change?"

### Example 3: Onboarding New Team Members

New developers read this memory to understand:
- What "DONE" means on this team
- Quality standards and thresholds
- When to use rigorous vs. normal workflow
- What evidence is expected

---

## 🎯 Quick Reference

### When in Doubt

**Ask yourself:**
1. Is this production-critical? → Use complete-mode
2. Does this affect users/revenue? → Use complete-mode
3. Is this compliance-related? → Use complete-mode
4. Could this cause an incident? → Use complete-mode
5. Is this a simple, low-risk change? → Normal workflow is fine

**Remember:**
- Complete-mode is for **critical work**, not everything
- Use `depth:shallow` for lighter rigor when needed
- Evidence packs make reviews faster, not slower
- Audit trails protect you and the team

---

**Last Updated:** 2025-10-31  
**Maintained By:** Engineering Team  
**Review Frequency:** Quarterly

---

**This memory ensures Cascade knows your team's professional standards!** 🎯
