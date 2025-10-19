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

### ✅ Available Now (3 Memories)

#### Project Type Memories
- ✅ **[Next.js App Router](./project-types/nextjs-app-router-memory.md)** - Complete Next.js 14+ with App Router, RSC, and TypeScript
- ✅ **[FastAPI Python](./project-types/fastapi-memory.md)** - Modern async FastAPI backend with PostgreSQL and SQLAlchemy

#### Team Workflow Memories
- ✅ **[Code Review Standards](./team-workflows/code-review-standards-memory.md)** - Team code review process, checklist, and conventions

### 🚧 Coming Soon (33 More Memories)

We're actively building more memories! Contributions welcome.

**Project Types (10 more):**
- 🚧 Next.js Pages Router
- 🚧 React + Vite
- 🚧 Vue + Nuxt  
- 🚧 Svelte Kit
- 🚧 Express (Node.js)
- 🚧 NestJS (Node.js)
- 🚧 Django (Python)
- 🚧 Flask (Python)
- 🚧 React Native
- 🚧 Expo

**Team Workflows (7 more):**
- 🚧 Git Commit Conventions
- 🚧 PR Template & Process
- 🚧 Testing Requirements
- 🚧 Deployment Checklist
- 🚧 Security Guidelines
- 🚧 Performance Standards
- 🚧 Documentation Requirements

**Coding Standards (10):**
- 🚧 TypeScript Best Practices
- 🚧 Python Best Practices
- 🚧 JavaScript Modern Patterns
- 🚧 Go Conventions
- 🚧 REST API Design
- 🚧 GraphQL Schema Design
- 🚧 Database Schema Patterns
- 🚧 Error Handling Patterns
- 🚧 Testing Patterns
- 🚧 Security Patterns

**Architecture (6):**
- 🚧 Microservices Architecture
- 🚧 Monorepo Structure
- 🚧 Serverless Architecture
- 🚧 Event-Driven Architecture
- 🚧 Clean Architecture
- 🚧 Domain-Driven Design

**Want to contribute?** See [CONTRIBUTING.md](CONTRIBUTING.md) or [open an issue](https://github.com/ChrisTansey007/windsurf-memories-arsenal/issues) to request a memory!

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

### Combining with Arsenal Ecosystem

**Complete Next.js setup example:**
```bash
# 1. Install all Arsenal repos
curl -sSL https://raw.githubusercontent.com/ChrisTansey007/arsenal-integration-hub/main/scripts/install-all.sh | bash

# 2. Copy Next.js memory
cp ~/arsenals/windsurf-memories-arsenal/project-types/nextjs-app-router-memory.md .windsurf/memories/

# 3. Copy Next.js rule
cp ~/arsenals/ai-rules-arsenal/windsurf/by-framework/nextjs-app-router.md .windsurf/rules/

# 4. Copy helpful workflows
cp ~/arsenals/ai-workflows-arsenal/windsurf/development/code-review-assistant.md .windsurf/workflows/
cp ~/arsenals/ai-workflows-arsenal/windsurf/development/run-tests-and-fix.md .windsurf/workflows/
cp ~/arsenals/ai-workflows-arsenal/windsurf/git-workflows/commit-and-pr.md .windsurf/workflows/
```

**Or use our setup script:**
```bash
~/arsenals/arsenal-integration-hub/scripts/setup-project.sh my-project fullstack
```

**See complete examples:**
- [Solo Developer Setup](https://github.com/ChrisTansey007/arsenal-integration-hub/tree/main/examples/solo-developer)
- [Team Setup](https://github.com/ChrisTansey007/arsenal-integration-hub/tree/main/examples/team-setup)
- [Full-Stack Next.js App](https://github.com/ChrisTansey007/arsenal-integration-hub/tree/main/examples/fullstack-nextjs-app)

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

**💭 windsurf-memories-arsenal** ⭐ YOU ARE HERE  
What Cascade remembers - Project context, standards, conventions

**⚙️ [ai-rules-arsenal](https://github.com/ChrisTansey007/ai-rules-arsenal)**  
How Cascade behaves - Development rules for frameworks and patterns  
→ **Pair with:** [Next.js Rule](https://github.com/ChrisTansey007/ai-rules-arsenal/blob/main/windsurf/by-framework/nextjs-app-router.md) + [Next.js Memory](./project-types/nextjs-app-router-memory.md)

**🔄 [ai-workflows-arsenal](https://github.com/ChrisTansey007/ai-workflows-arsenal)**  
Multi-step automation - Testing, code review, PR creation workflows  
→ **Pair with:** [Code Review Workflow](https://github.com/ChrisTansey007/ai-workflows-arsenal/blob/main/windsurf/development/code-review-assistant.md) + [Code Review Memory](./team-workflows/code-review-standards-memory.md)

**📝 [prompt-arsenal](https://github.com/ChrisTansey007/prompt-arsenal)**  
Reusable prompts - Custom agents and system configurations

**🤖 [ai-scripts-arsenal](https://github.com/ChrisTansey007/ai-scripts-arsenal)**  
Automation scripts - Repository setup and management

**🔗 [arsenal-integration-hub](https://github.com/ChrisTansey007/arsenal-integration-hub)**  
Complete examples - See how to use all Arsenal tools together  
→ **Start here:** [Installation Guide](https://github.com/ChrisTansey007/arsenal-integration-hub#-quick-start)

**Use them together for maximum power!**

---

## 📖 Documentation

- **[Arsenal Integration Hub](https://github.com/ChrisTansey007/arsenal-integration-hub)** - Complete setup examples
- **[Template](./templates/memory-template.md)** - Create your own memories
- **[Contributing Guide](CONTRIBUTING.md)** - Add new memories

**Coming Soon:**
- 🚧 Getting Started Guide
- 🚧 Memory Guide Deep Dive
- 🚧 Best Practices
- 🚧 FAQ

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

- **3 Production-Ready Memories** (33 more coming soon!)
- **4 Categories** (Project Types, Team Workflows, Coding Standards, Architecture)
- **100% Open Source** (MIT License)
- **Battle-Tested** in real projects
- **Community Contributions Welcome**

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
