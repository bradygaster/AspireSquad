---
name: "readme-dx-review"
description: "Developer experience checklist for reviewing README files and getting-started documentation"
domain: "documentation"
confidence: "low"
source: "earned"
---

## Context
Use this skill when reviewing README files, getting-started guides, or any documentation that serves as a developer's first experience with a project. These patterns reduce friction at key decision points: "Can I use this?", "Should I use this?", "How do I use this?", "Will this work for me?"

## Patterns

### 1. Surface Project Status Early
Place experimental/beta/production status within the first 3 lines of the README, ideally right after the tagline. Use visual markers (⚠️, 🚧, ✅) to signal maturity level.

**Why:** Developers scanning documentation need to self-select immediately. Burying "this is experimental" disclaimers at the bottom wastes their time and creates frustration.

**Example Placement:**
```markdown
# ProjectName

> Tagline describing what this is

> ⚠️ **Active Experiment**: This is a learning journey, not production software.

First paragraph explaining the project...
```

### 2. Prerequisites Before Quick Start
List required tools, subscriptions, accounts, and SDKs before any clone/fork/install instructions. Include a verification step so developers can confirm their environment is ready.

**Components:**
- Tools (IDE, CLI, runtime)
- Accounts/subscriptions (cloud services, API keys)
- Minimum versions
- Verification command or test

**Why:** Prevents the "I followed all the steps but nothing works" scenario. Developers know upfront what's required and can test their setup before investing time.

### 3. Platform-Appropriate Command Examples
Match your command syntax to your primary developer audience's expected environment. For .NET/C# projects, show Windows PowerShell first. For Node.js/Python projects, show Unix shell first.

**Pattern:**
```markdown
# Primary audience command
Remove-Item -Recurse -Force .git   # Windows PowerShell
# Alternative: rm -rf .git for Linux/macOS
```

**Why:** Reduces cognitive load. Developers work in their native environment and shouldn't have to mentally translate commands.

### 4. Lead with Roles, Not Counts
When describing systems with multiple components/agents/services, emphasize roles and capabilities over implementation counts. "Specialists for testing, deployment, and security" is clearer than "23 specialized components."

**Why:** Implementation details change. The conceptual model should be stable. Leading with counts makes the framework feel arbitrary.

**Before:** "21 specialized AI agents"  
**After:** "Specialized AI agents covering testing, security, deployment, and databases"

### 5. Bridge the Setup-to-Usage Gap
Add a "What Happens Next?" section after getting-started instructions. Show what the developer will see, what gets created, and how to verify the first successful interaction.

**Structure:**
- What to do first (first command/interaction)
- What output to expect
- How to know it worked
- Where to go next

**Why:** The gap between "I installed this" and "I'm productively using this" is where most abandonment happens. Explicit guidance bridges that gap.

## Examples

### Good Status Visibility
```markdown
# ProjectName
> An AI-powered code generator for REST APIs

> 🚧 **Beta Software**: Core features work, but expect breaking changes and rough edges.

ProjectName helps you...
```

### Prerequisites Section
```markdown
## Prerequisites

Before getting started, ensure you have:
- Node.js 18+ installed
- GitHub account with Copilot subscription
- Azure subscription (free tier works)

**Verify your setup:**
```bash
node --version    # Should show v18.0.0 or higher
gh auth status    # Should show "Logged in to github.com"
```
```

### What Happens Next Section
```markdown
## What Happens Next?

After cloning the repo:

1. Run `npm install` to install dependencies
2. Run `npm start` to launch the dev server
3. Open http://localhost:3000 — you should see the welcome screen
4. Try creating your first API: `npm run generate -- --name todos`

You'll see output like:
```
✓ Generated models/todo.ts
✓ Generated routes/todos.ts
✓ Updated index.ts
```

The API is now available at GET/POST http://localhost:3000/api/todos
```

## Anti-Patterns

- **Burying disclaimers** — "This is experimental" hidden in a footer or license section
- **Assuming prerequisites** — Not listing required tools because "everyone has Node installed"
- **Universal commands** — Showing only `rm -rf` on a Windows-focused project
- **Setup without verification** — No way to test if the setup actually worked
- **Implementation-first framing** — Leading with "327 modules" instead of "what it does"
- **Skipping the gap** — Going from installation directly to API reference without showing first usage
