# 💭 Windsurf Memories Arsenal

**Production-ready Memories for Windsurf/Cascade AI**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)

---

## 🎯 What Are Windsurf Memories?

**Memories** are Windsurf's powerful feature that allows Cascade to remember project-specific context, coding standards, architectural decisions, and team conventions across sessions.

Think of Memories as **persistent knowledge** that Cascade can reference to:
- Understand your project structure
- Follow your coding conventions
- Remember architectural decisions
- Apply your team's standards
- Maintain consistency across sessions

---

## ⚡ Quick Start

### 1. Browse Memories

Choose from our categories:
- **Project Types:** Next.js, FastAPI, React Native, etc.
- **Team Workflows:** Code review, deployment, testing standards
- **Coding Standards:** TypeScript, Python, API design patterns
- **Architectures:** Microservices, monorepo, serverless

### 2. Copy to Your Project

```bash
# Copy a Memory to your Windsurf project
cp project-types/nextjs-app-router-memory.md \
   ~/your-project/.windsurf/memories/
```

### 3. Activate in Windsurf

Memories are automatically loaded when you open your project in Windsurf!

---

## 📚 What's Inside

### Project Type Memories (12)

**Web Frameworks:**
- ✅ Next.js App Router
- ✅ Next.js Pages Router
- ✅ React + Vite
- ✅ Vue + Nuxt
- ✅ Svelte Kit

**Backend Frameworks:**
- ✅ FastAPI (Python)
- ✅ Express (Node.js)
- ✅ NestJS (Node.js)
- ✅ Django (Python)
- ✅ Flask (Python)

**Mobile:**
- ✅ React Native
- ✅ Expo

### Team Workflow Memories (8)

- ✅ Code Review Standards
- ✅ Git Commit Conventions
- ✅ PR Template & Process
- ✅ Testing Requirements
- ✅ Deployment Checklist
- ✅ Security Guidelines
- ✅ Performance Standards
- ✅ Documentation Requirements

### Coding Standards Memories (10)

**Languages:**
- ✅ TypeScript Best Practices
- ✅ Python Best Practices
- ✅ JavaScript Modern Patterns
- ✅ Go Conventions

**Patterns:**
- ✅ REST API Design
- ✅ GraphQL Schema Design
- ✅ Database Schema Patterns
- ✅ Error Handling Patterns
- ✅ Testing Patterns
- ✅ Security Patterns

### Architecture Memories (6)

- ✅ Microservices Architecture
- ✅ Monorepo Structure
- ✅ Serverless Architecture
- ✅ Event-Driven Architecture
- ✅ Clean Architecture
- ✅ Domain-Driven Design

---

## 🌟 Featured Memories

### Most Popular

#### 1. Next.js App Router Memory
Complete context for Next.js 14+ projects with App Router
```bash
cp project-types/nextjs-app-router-memory.md .windsurf/memories/
```

#### 2. Code Review Standards Memory
Team code review conventions and checklist
```bash
cp team-workflows/code-review-standards-memory.md .windsurf/memories/
```

#### 3. TypeScript Best Practices Memory
Modern TypeScript patterns and conventions
```bash
cp coding-standards/typescript-best-practices-memory.md .windsurf/memories/
```

---

## 💡 How to Use Memories

### Basic Usage

1. **Copy Memory to your project:**
   ```bash
   mkdir -p .windsurf/memories
   cp path/to/memory.md .windsurf/memories/
   ```

2. **Open project in Windsurf**
   - Memories are automatically loaded
   - Cascade can now reference this knowledge

3. **Cascade applies the Memory:**
   - Follows your conventions
   - Uses your patterns
   - Maintains consistency

### Advanced Usage

**Combine Multiple Memories:**
```bash
# Full-stack project example
cp project-types/nextjs-app-router-memory.md .windsurf/memories/
cp project-types/fastapi-memory.md .windsurf/memories/
cp team-workflows/code-review-standards-memory.md .windsurf/memories/
cp coding-standards/typescript-best-practices-memory.md .windsurf/memories/
```

**Create Custom Memories:**
```bash
# Use our template
cp templates/memory-template.md .windsurf/memories/my-custom-memory.md
# Edit to match your needs
```

---

## 🎓 Understanding Memories

### What Makes a Good Memory?

✅ **Specific and actionable**
- Concrete examples
- Clear conventions
- Explicit patterns

✅ **Project-relevant**
- Focused on your tech stack
- Aligned with your architecture
- Matches your team's needs

✅ **Consistently applied**
- Used across all code
- Enforced in reviews
- Part of standards

❌ **Avoid:**
- Generic advice
- Contradictory rules
- Too many memories (keep it focused)

### Memory vs. Rule vs. Workflow

| Feature | Memory | Rule | Workflow |
|---------|--------|------|----------|
| **Purpose** | Remember context | Guide behavior | Execute steps |
| **Scope** | Project-wide | Chat/trajectory | Multi-step process |
| **Persistence** | Always loaded | Per session | On-demand |
| **Best For** | Standards, architecture | Response style | Task automation |

**Use Together:**
- **Memory:** "We use TypeScript strict mode"
- **Rule:** "Always explain type decisions"
- **Workflow:** Steps to add new feature

---

## 📖 Memory Categories

### 1. Project Type Memories

**What they include:**
- Tech stack overview
- Project structure
- File organization
- Dependencies and tools
- Build/dev commands
- Testing setup
- Deployment process

**When to use:**
- Starting new project
- Onboarding team members
- Ensuring consistency

### 2. Team Workflow Memories

**What they include:**
- Code review process
- Git conventions
- PR requirements
- Testing standards
- Deployment checklist
- Communication patterns

**When to use:**
- Team collaboration
- Maintaining standards
- Onboarding new members

### 3. Coding Standards Memories

**What they include:**
- Language conventions
- Style guidelines
- Pattern preferences
- Error handling
- Testing approaches
- Documentation requirements

**When to use:**
- Ensuring code quality
- Maintaining consistency
- Teaching best practices

### 4. Architecture Memories

**What they include:**
- System design principles
- Component organization
- Data flow patterns
- Communication patterns
- Scaling strategies
- Technical decisions

**When to use:**
- Complex projects
- Multiple services
- Team alignment
- Decision documentation

---

## 🚀 Getting Started Guide

### For Solo Developers

**Step 1:** Choose your stack
```bash
# Example: Next.js + TypeScript
cp project-types/nextjs-app-router-memory.md .windsurf/memories/
cp coding-standards/typescript-best-practices-memory.md .windsurf/memories/
```

**Step 2:** Add your preferences
- Edit memories to match your style
- Add project-specific details
- Remove irrelevant sections

**Step 3:** Start coding
- Cascade now knows your preferences
- Consistent code generation
- Better suggestions

### For Teams

**Step 1:** Select team memories
```bash
# Core team setup
cp team-workflows/code-review-standards-memory.md .windsurf/memories/
cp team-workflows/git-commit-conventions-memory.md .windsurf/memories/
cp team-workflows/pr-process-memory.md .windsurf/memories/
```

**Step 2:** Add project memories
```bash
# Your specific stack
cp project-types/[your-stack]-memory.md .windsurf/memories/
cp coding-standards/[your-language]-memory.md .windsurf/memories/
```

**Step 3:** Share with team
```bash
# Commit to repository
git add .windsurf/memories/
git commit -m "Add team Memories"
git push
```

**Step 4:** Team onboarding
- New members clone repo
- Memories automatically load
- Instant alignment with standards

---

## 🛠️ Customization

### Editing Memories

Memories are Markdown files you can edit:

```markdown
# My Project Memory

## Tech Stack
- Next.js 14 (App Router)
- TypeScript (strict mode)
- Tailwind CSS
- PostgreSQL with Prisma

## Project Structure
/app - Next.js app directory
/components - React components
/lib - Utility functions
/prisma - Database schema

## Conventions
- Use 'use client' only when necessary
- All components are TypeScript
- Props interfaces end with 'Props'
- API routes in /app/api/
```

### Combining with Arsenal

**Complete setup:**
```bash
# 1. Memories (what Cascade remembers)
cp memories-arsenal/project-types/nextjs-memory.md .windsurf/memories/

# 2. Rules (how Cascade behaves)
cp ai-rules-arsenal/windsurf/by-framework/nextjs-app-router.md .windsurf/rules/

# 3. Workflows (what Cascade does)
cp ai-workflows-arsenal/windsurf/development/*.md .windsurf/workflows/

# 4. Prompts (what you ask)
# Use from prompt-arsenal as needed
```

**Result:** Complete AI-powered development environment!

---

## 📊 Best Practices

### Memory Management

✅ **Do:**
- Keep memories focused and specific
- Update as project evolves
- Remove outdated information
- Use clear, concise language
- Include examples

❌ **Don't:**
- Create too many memories (< 10 recommended)
- Include contradictory information
- Leave obsolete content
- Make memories too generic
- Forget to update

### Organization

**Recommended structure:**
```
.windsurf/
├── memories/
│   ├── project-overview.md        # Project basics
│   ├── tech-stack.md              # Technologies used
│   ├── coding-standards.md        # Team conventions
│   ├── architecture.md            # System design
│   └── workflows.md               # Team processes
├── rules/
│   └── [your rules]
└── workflows/
    └── [your workflows]
```

### Maintenance

**Monthly review:**
- [ ] Check if memories are still accurate
- [ ] Update with new conventions
- [ ] Remove deprecated practices
- [ ] Add new learnings
- [ ] Sync with team

---

## 🤝 Contributing

We welcome contributions! Here's how:

### Add a New Memory

1. **Use the template:**
   ```bash
   cp templates/memory-template.md my-new-memory.md
   ```

2. **Fill in all sections:**
   - Clear, specific content
   - Real-world examples
   - Tested in production

3. **Submit a PR:**
   - Follow our guidelines
   - Include usage examples
   - Explain the value

See [CONTRIBUTING.md](CONTRIBUTING.md) for details.

---

## 🔗 Related Arsenal Projects

### The Complete Arsenal Ecosystem

```
💭 windsurf-memories-arsenal  ⭐ YOU ARE HERE - What Cascade remembers
📝 prompt-arsenal             → What to build
⚙️ ai-rules-arsenal           → How Cascade behaves
🔄 ai-workflows-arsenal       → Multi-step processes
🤖 ai-scripts-arsenal         → Automation scripts
🔗 arsenal-integration-hub    → How to use together
```

**Use them together for maximum power!**

---

## 📖 Documentation

- **[Getting Started](docs/GETTING-STARTED.md)** - Quick start guide
- **[Memory Guide](docs/MEMORY-GUIDE.md)** - Deep dive into Memories
- **[Best Practices](docs/BEST-PRACTICES.md)** - Tips and patterns
- **[Examples](docs/EXAMPLES.md)** - Real-world usage
- **[FAQ](docs/FAQ.md)** - Common questions

---

## 🎯 Use Cases

### Use Case 1: New Project Setup

**Problem:** Starting Next.js project, want consistent structure

**Solution:**
```bash
cp project-types/nextjs-app-router-memory.md .windsurf/memories/
```

**Result:** Cascade knows your structure and conventions from day 1

### Use Case 2: Team Onboarding

**Problem:** New developer needs to learn team standards

**Solution:**
```bash
# New dev clones repo with memories
git clone repo
cd repo
# Open in Windsurf - memories auto-load!
```

**Result:** Instant alignment with team conventions

### Use Case 3: Multi-Service Project

**Problem:** Microservices with different technologies

**Solution:**
```bash
# Frontend service
cp project-types/nextjs-memory.md services/frontend/.windsurf/memories/

# Backend service
cp project-types/fastapi-memory.md services/api/.windsurf/memories/

# Shared standards
cp team-workflows/code-review-standards-memory.md .windsurf/memories/
```

**Result:** Consistent standards across services

---

## 📊 Stats

- **36 Production-Ready Memories**
- **4 Categories** (Project, Team, Standards, Architecture)
- **100% Open Source** (MIT License)
- **Battle-Tested** in real projects

---

## 🙏 Acknowledgments

Built from:
- Real-world Windsurf usage
- Community best practices
- Industry standards
- Team feedback

Special thanks to:
- Windsurf/Codeium team for the Memories feature
- The Arsenal community
- All contributors

---

## 📝 License

MIT License - see [LICENSE](LICENSE) file for details.

---

## 💬 Community

- **Discussions:** Ask questions, share ideas
- **Issues:** Report bugs, request memories
- **Twitter:** #WindsurfMemories
- **Blog:** Coming soon!

---

## 🚀 Quick Examples

### Example 1: Full-Stack App

```bash
# Setup memories for full-stack project
mkdir -p .windsurf/memories

# Frontend
cp project-types/nextjs-app-router-memory.md .windsurf/memories/

# Backend
cp project-types/fastapi-memory.md .windsurf/memories/

# Standards
cp coding-standards/typescript-best-practices-memory.md .windsurf/memories/
cp coding-standards/rest-api-design-memory.md .windsurf/memories/

# Team
cp team-workflows/code-review-standards-memory.md .windsurf/memories/
```

### Example 2: Solo Developer

```bash
# Minimal setup
mkdir -p .windsurf/memories

# Just your stack
cp project-types/react-vite-memory.md .windsurf/memories/
cp coding-standards/typescript-best-practices-memory.md .windsurf/memories/
```

---

## 🎉 Get Started Now!

```bash
# 1. Clone the repository
git clone https://github.com/ChrisTansey007/windsurf-memories-arsenal.git

# 2. Browse memories
cd windsurf-memories-arsenal
ls project-types/

# 3. Copy to your project
cp project-types/nextjs-app-router-memory.md ~/your-project/.windsurf/memories/

# 4. Open in Windsurf and code!
```

---

<div align="center">

**Made with ❤️ for the Windsurf community**

[⬆ Back to Top](#-windsurf-memories-arsenal)

</div>
