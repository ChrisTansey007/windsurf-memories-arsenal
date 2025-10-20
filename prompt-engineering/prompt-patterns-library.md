---
id: mem.prompt-patterns
type: memory
title: Prompt Patterns Library - Extracted from Analyzed Conversations
tags: [prompt-engineering, patterns, meta-learning, conversation-analysis, catalog]
summary: Living catalog of proven prompt patterns extracted from analyzed conversation threads - organized by category with effectiveness ratings and real-world evidence.
audience: developers, prompt-engineers
domain: prompt-engineering
version: 1
---

# Prompt Patterns Library

**Living catalog of effective prompt patterns extracted from real AI conversations.**

**Last Updated:** 2025-10-20  
**Total Patterns:** 6 (growing)  
**Source Threads:** 1+ analyzed conversations

---

## 🎯 How to Use This Library

1. **Find your situation** - Browse categories below
2. **Copy the pattern** - Use the template as-is or customize
3. **Track effectiveness** - Note if it worked for you
4. **Contribute back** - Add new patterns from your own analyses

---

## 📚 Pattern Categories

### 1. Clarification Patterns
*Prompts that elicit specific, targeted information*

#### Pattern: Domain Clarification
```
"What is the intended audience or domain for this {DOCUMENT_TYPE}?"
```
- **Effectiveness:** 5/5
- **Use When:** Output is too generic or unfocused
- **Why It Works:** Forces AI to consider context before proceeding
- **Source Thread:** agents.md structure (2025-10-20)

#### Pattern: Context Gathering
```
"What context or constraints should I know before proceeding with {TASK}?"
```
- **Effectiveness:** 4/5
- **Use When:** Starting complex tasks with unknowns
- **Why It Works:** Surfaces assumptions and prevents rework
- **Source Thread:** [To be added]

---

### 2. Constraint Patterns
*Prompts that specify output requirements and boundaries*

#### Pattern: Citation Requirement
```
"Include 2-3 real-world examples or citations validating this approach."
```
- **Effectiveness:** 5/5
- **Use When:** Need credibility and external validation
- **Why It Works:** Grounds AI output in verifiable sources
- **Source Thread:** agents.md structure (2025-10-20)

#### Pattern: Format Specification
```
"Output must include structured sections with examples and citations."
```
- **Effectiveness:** 5/5
- **Use When:** Need consistent, professional output
- **Why It Works:** Sets clear expectations upfront
- **Source Thread:** agents.md structure (2025-10-20)

#### Pattern: Scope Limiting
```
"Focus only on {SPECIFIC_AREA}. Explicitly note anything out of scope."
```
- **Effectiveness:** 4/5
- **Use When:** Preventing scope creep or tangents
- **Why It Works:** Creates clear boundaries
- **Source Thread:** [To be added]

---

### 3. Evaluation Patterns
*Prompts that request self-assessment or quality checks*

#### Pattern: Self-Scoring
```
"Score your draft for clarity, specificity, and constraint adherence (1-5 scale)."
```
- **Effectiveness:** 4/5
- **Use When:** Need quality assurance before finalization
- **Why It Works:** Triggers AI self-review mechanism
- **Source Thread:** agents.md structure (2025-10-20)

#### Pattern: Quality Gate Checklist
```
"Before finalizing, verify: {CHECKLIST}. If any item fails, revise."
```
- **Effectiveness:** 5/5
- **Use When:** Critical outputs requiring validation
- **Why It Works:** Systematic check prevents common errors
- **Source Thread:** [To be added]

---

### 4. Refinement Patterns
*Prompts that improve or transform existing content*

#### Pattern: Template Extraction
```
"Condense the prior response into a standardized reusable template."
```
- **Effectiveness:** 5/5
- **Use When:** Want to reuse successful approaches
- **Why It Works:** Transforms specific into general
- **Source Thread:** agents.md structure (2025-10-20)

#### Pattern: Upgrade Request
```
"Refactor prior answer to include external citations and examples from real projects."
```
- **Effectiveness:** 5/5
- **Use When:** Need to elevate quality of existing output
- **Why It Works:** Builds on existing work rather than starting over
- **Source Thread:** agents.md structure (2025-10-20)

---

### 5. Verification Patterns
*Prompts that ensure accuracy and completeness*

#### Pattern: Citation Addition
```
"Add 2 verifiable citations or repository links supporting each section."
```
- **Effectiveness:** 5/5
- **Use When:** Need factual grounding
- **Why It Works:** Makes claims verifiable and credible
- **Source Thread:** agents.md structure (2025-10-20)

#### Pattern: Assumption Declaration
```
"List all assumptions you're making. If any are uncertain, ask for clarification."
```
- **Effectiveness:** 4/5
- **Use When:** Complex problems with ambiguity
- **Why It Works:** Surfaces hidden assumptions
- **Source Thread:** [To be added]

---

### 6. Comparison Patterns
*Prompts that request analysis of alternatives*

#### Pattern: Contrast Request
```
"Explain how this {ARTIFACT} differs from or complements a {RELATED_ARTIFACT}."
```
- **Effectiveness:** 4/5
- **Use When:** Need to understand relationships between artifacts
- **Why It Works:** Clarifies positioning and prevents confusion
- **Source Thread:** agents.md structure (2025-10-20)

#### Pattern: Alternative Proposal
```
"Propose 2-3 alternative approaches with pros/cons for each."
```
- **Effectiveness:** 5/5
- **Use When:** Want to explore options before committing
- **Why It Works:** Prevents tunnel vision
- **Source Thread:** [To be added]

---

## 📊 Effectiveness Rating System

**5/5** - Consistently produces excellent results, highly reusable  
**4/5** - Very effective, minor variations needed for some contexts  
**3/5** - Generally useful, may need significant adaptation  
**2/5** - Works occasionally, context-dependent  
**1/5** - Rarely effective, needs major rework

**Ratings based on:**
- Clarity impact
- Specificity gain
- Reusability across domains
- Consistency of results

---

## 🔄 Pattern Evolution

**As we analyze more threads:**
- ✅ Patterns get refined based on performance
- ✅ Effectiveness ratings validated across multiple uses
- ✅ Patterns combined into compound patterns
- ✅ Domain-specific variations documented
- ✅ Frequency tracking (how often pattern appears)

---

## 🌱 Contributing New Patterns

**When you find an effective prompt:**

1. **Identify the category** (clarify, constrain, evaluate, refine, verify, compare)
2. **Extract the template** (replace specifics with {{VARIABLES}})
3. **Document effectiveness** (initial rating + evidence)
4. **Note source thread** (for traceability)
5. **Add to appropriate section** above

**Format:**
```markdown
#### Pattern: {NAME}
```
"{pattern template with {{VARIABLES}}}"
```
- **Effectiveness:** {1-5}/5
- **Use When:** {scenarios}
- **Why It Works:** {mechanism}
- **Source Thread:** {thread-id} ({date})
```

---

## 📈 Pattern Validation

**When pattern appears in multiple threads:**
- Update effectiveness rating if higher performance observed
- Add cross-references to all source threads
- Note any variations that work better in specific domains
- Consider promoting to "Proven Pattern" (3+ validations)

**Example:**
```markdown
#### Pattern: Citation Requirement ⭐ PROVEN (3 threads)
```
"Include 2-3 real-world examples or citations validating this approach."
```
- **Effectiveness:** 5/5 (validated across 3 threads)
- **Use When:** Need credibility and external validation
- **Why It Works:** Grounds AI output in verifiable sources
- **Source Threads:** 
  - agents.md (2025-10-20)
  - email-oauth-debug (2025-10-19)
  - api-design (2025-10-18)
```

---

## 🎯 Quick Reference by Goal

**I want clearer output:**
→ Domain Clarification, Context Gathering

**I want more specific results:**
→ Format Specification, Scope Limiting

**I want verified/credible output:**
→ Citation Requirement, Citation Addition

**I want to improve existing output:**
→ Template Extraction, Upgrade Request

**I want to prevent errors:**
→ Self-Scoring, Quality Gate Checklist

**I want to explore options:**
→ Contrast Request, Alternative Proposal

---

## 🔗 Related Arsenal Items

**📝 Prompts:**
- [Prompt Forensics Analyzer](https://github.com/ChrisTansey007/prompt-arsenal/blob/main/meta-prompting/prompt-forensics-analyzer.md) - Extract patterns from threads

**🔄 Workflows:**
- [Insights Extraction Pipeline](https://github.com/ChrisTansey007/ai-workflows-arsenal/blob/main/windsurf/meta-analysis/insights-extraction-pipeline.md) - How to add patterns to this library

**⚙️ Rules:**
- [Prompt Quality Standards](https://github.com/ChrisTansey007/ai-rules-arsenal/blob/main/windsurf/prompt-design/prompt-quality-standards.md) - Evaluation framework

---

## 📝 Changelog

**v1.0 (2025-10-20)**
- Initial library created
- Added 6 core patterns from agents.md analysis
- Established rating system and contribution guidelines

---

**This library grows with every analyzed conversation thread.** 🌱  
**Current coverage:** Meta-prompting, documentation standards  
**Next domains:** API design, debugging, UI development
