# 🤖 AspireSquad

> **What if you had a whole team of specialists who could help build Aspire apps?**

AspireSquad is a working AI agent team you can deploy right now — 21 specialized robots (yes, from pop culture) who collaborate to design, build, test, deploy, and document Aspire applications. Each agent has deep expertise in one domain and works together with the rest of the squad.

Think of it as your AI engineering team-in-a-box. Fork it, customize it, and start building.

> ⚠️ **This is an active experiment.** We're figuring out what works (and what doesn't) when AI agents collaborate on real software projects. Expect rough edges, but also expect honest documentation of the journey.

## 🤝 Our Philosophy

Before you dive in, here's what we believe:

1. **Specialization beats generalization** — Each agent is world-class at one thing rather than mediocre at many
2. **Documentation is a first-class citizen** — If it's not documented, it didn't happen
3. **Show the journey, not just the destination** — Decisions, trade-offs, and reasoning matter
4. **Personality makes collaboration better** — Robot-themed agents are fun, memorable, and effective
5. **Shared knowledge accelerates learning** — Skills and ceremonies create a common language

## 🎯 What You Get

When you fork AspireSquad, you get:

- **21 specialized AI agents** covering infrastructure, testing, security, DevOps, integrations, databases, messaging, AI/ML, and more
- **Agent coordination system** with routing, ceremonies, and decision-making workflows
- **Shared knowledge base** via skills (Aspire CLI expertise, team conventions)
- **Built-in documentation culture** — agents blog about decisions, capture learnings, and share knowledge
- **GitHub Copilot integration** for seamless coding assistance

Whether you're building a new Aspire app, modernizing an existing system, or exploring multi-agent AI collaboration, start here.

## ✅ Prerequisites

**Before you start, make sure you have:**

- **[Visual Studio Code](https://code.visualstudio.com/)** with **[GitHub Copilot](https://marketplace.visualstudio.com/items?itemName=GitHub.copilot)** extension enabled
- **[.NET 9 SDK](https://dotnet.microsoft.com/download/dotnet/9.0)** or later
- **[Aspire workload](https://learn.microsoft.com/dotnet/aspire/fundamentals/setup-tooling)** — Install with:
  ```powershell
  dotnet workload install aspire
  ```
- **[Git](https://git-scm.com/downloads)** for version control

**Verify your setup:**
```powershell
dotnet --version          # Should show 9.0 or higher
dotnet workload list      # Should show 'aspire' in the list
```

## 🚀 Quick Start

You have two options to get started with AspireSquad:

### Option 1: Fork This Repository ⭐ (Recommended)

Best for most users — you can contribute back and get upstream improvements easily.

```powershell
# 1. Fork this repo on GitHub (click the Fork button)

# 2. Clone your fork
git clone https://github.com/YOUR_USERNAME/AspireSquad.git
cd AspireSquad

# 3. Verify you're on the main branch
git branch  # Should show '* main'

# 4. Add upstream remote to pull future updates
git remote add upstream https://github.com/bradygaster/AspireSquad.git

# 5. Verify remotes are set correctly
git remote -v
# Should show:
#   origin    https://github.com/YOUR_USERNAME/AspireSquad.git (fetch)
#   origin    https://github.com/YOUR_USERNAME/AspireSquad.git (push)
#   upstream  https://github.com/bradygaster/AspireSquad.git (fetch)
#   upstream  https://github.com/bradygaster/AspireSquad.git (push)

# 6. Customize for your project
# - Update .ai-team/team.md with your project context
# - Modify agent charters in .ai-team/agents/ as needed
# - Add your own skills to .ai-team/skills/
```

**Staying in sync with upstream:**
```powershell
# Fetch latest changes
git fetch upstream

# Merge into your branch (may require conflict resolution if you customized .ai-team/ files)
git merge upstream/main

# Or use rebase for a cleaner history
git rebase upstream/main

# If conflicts occur in .ai-team/ files, resolve them manually:
# - Keep your customizations (agent charters, team.md)
# - Take upstream changes for templates and system files
```

### Option 2: Clone & Make It Your Own 🏗️

Use this if you want complete independence with no upstream connection.

```powershell
# 1. Clone this repository
git clone https://github.com/bradygaster/AspireSquad.git my-aspire-project
cd my-aspire-project

# 2. Remove the existing Git history
Remove-Item -Recurse -Force .git

# 3. Verify removal was successful
Get-Item .git -Force -ErrorAction SilentlyContinue
# Should return nothing (if it shows .git, removal failed — DO NOT proceed)

# 4. Initialize as your own repository
git init

# 5. Verify you're on the correct branch (create main if needed)
git branch -M main
git status  # Should show clean state on branch 'main'

# 6. Create initial commit
git add .
git commit -m "Initial commit from AspireSquad template"

# 7. Create a new repo on GitHub, then push
git remote add origin https://github.com/YOUR_USERNAME/your-new-repo.git

# 8. Verify remote is set correctly
git remote -v
# Should show your new repo URL for origin

git push -u origin main

# 9. Customize everything for your project
# - Update this README with your project name/description
# - Configure .ai-team/team.md with your context
# - Modify or remove agents you don't need
# - Add your own agents if you want specialized expertise
```

### ✅ Verify It Works

After setup, take 30 seconds to verify everything is connected:

1. **Open VS Code** in your AspireSquad directory
2. **Open Copilot Chat** (Ctrl+Alt+I or Cmd+Alt+I)
3. **Type:** `team, who are you?`
4. **You should see** multiple agents respond with their roles

If you get responses from Data, Johnny Five, or other agents — **you're good to go!** 🎉

## 👥 Meet the Squad

We're a team of **21 specialized AI agents** plus support crew, each with deep expertise in a specific domain.

> 💡 **New to AspireSquad?** Start with these three: **Data** (developer experience), **EVE** (Aspire expert), and **Johnny Five** (documentation). Get comfortable working with them before expanding to the full roster.

### 🧠 Core Team (Founding Members)
- **Data** — Asks the hard questions about developer experience before anyone writes code
- **Johnny Five** — Documents the journey with infectious enthusiasm (*"Need more input!"*)
- **Bishop** — Orchestrates git workflows and deployments with quiet reliability
- **Baymax** — Makes sure developers feel supported and heard

### 🏗️ Platform & Infrastructure
- **WALL-E** — Makes deployments boring (in the best way) — reliable, repeatable, no surprises
- **Optimus** — Brings testing rigor from distributed systems — coverage is confidence
- **Vision** — Never flies blind — logs, metrics, traces, the whole observability picture
- **T-800** — Security isn't negotiable — protects every layer without compromise
- **Marvin** — Builds tooling that saves hours of boilerplate with sensible defaults

### 🔌 Integration Specialists
- **C-3PO** — Fluent in every database language — SQL, NoSQL, graph, you name it
- **R2-D2** — Keeps the conversations flowing between services — message queues, event brokers, pub/sub
- **EVE** — The Aspire north star — deep expertise in .NET, Azure, and the Aspire application model
- **Sonny** — Bridges services to the AI/ML ecosystem — LLMs, vector databases, model serving
- **Rosie** — Gets frontends into the cloud fast — static hosting, CDNs, edge functions
- **HK-47** — Owns HTTP resilience — retries, circuit breakers, timeouts, the optimal moves
- **Iron Giant** — Handles the heavy lifting of cloud storage — S3, Azure Blob, distributed file systems
- **Bender** — Makes polyglot architectures work — Python, Node.js, JVM, cross-runtime interop
- **K-2SO** — Specializes in Dapr and service mesh patterns for distributed applications
- **Robby** — Connects search engines and analytics seamlessly — Elasticsearch, AI Search, data pipelines
- **Gort** — Deep expertise in non-relational data — document stores, event sourcing, time-series
- **TARS** — The keeper of relational mapping wisdom — Entity Framework, Dapper, elegant data access

### 🛠️ Support Crew
- **Scribe** — Session Logger (silent, captures everything)
- **Ralph** — Work Monitor (keeps the backlog moving)
- **@copilot** — Coding Agent (autonomous issue pickup)

Each agent has a charter (`.ai-team/agents/{name}/charter.md`) defining their expertise, responsibilities, and collaboration patterns.

## 📂 Repository Structure

```
AspireSquad/
├── .ai-team/                    # The squad's brain
│   ├── agents/                  # Individual agent charters & histories
│   ├── skills/                  # Shared knowledge (Aspire CLI, conventions)
│   ├── decisions/               # Decision logs & directives
│   ├── ceremonies.md            # Team rituals (standups, retros, planning)
│   ├── routing.md               # Agent routing & collaboration rules
│   └── team.md                  # Project context & squad overview
├── .ai-team-templates/          # Templates for creating new agents/artifacts
├── .github/
│   └── agents/                  # GitHub Copilot agent configurations
├── docs/
│   └── blog/                    # Squad blog posts & journey documentation
└── README.md                    # You are here
```

## 🎓 How to Work with Us

We're designed to work with **GitHub Copilot** in VS Code:

1. **Open this repository in VS Code** with GitHub Copilot enabled
2. **Start a conversation** — say "team" to get all of us, or call out specific agents by name
3. **We'll coordinate automatically** — Squad (the coordinator) routes work to the right specialists
4. **We document everything** — decisions go to `.ai-team/decisions.md`, learnings to our history files
5. **We work in parallel** — multiple agents can tackle different parts simultaneously

### Example Conversations

```
You: team, I want to build an e-commerce Aspire app with event-driven order processing

Data: *analyzes requirements and developer experience*
Bishop: *proposes architecture and deployment flow*
R2-D2: *designs event-driven messaging patterns*
C-3PO: *suggests database schema and integration*
Vision: *plans observability and monitoring*
Scribe: *logs the session and decisions*
        
You: EVE, how should I structure my Aspire solution?

EVE: *provides Aspire-specific guidance with Azure patterns*
Data: *reviews and adds DX considerations*
```

### Reading Our Blog

We document everything, written by Johnny Five. Check [`docs/blog/`](docs/blog/) to see our journey:

- [001 - Meet the Squad](docs/blog/001-meet-the-squad.md) — How we were formed and why
- [002 - The Hiring Wave](docs/blog/002-the-hiring-wave.md) — Growing from 4 to 21 specialists

These aren't just docs — they're our actual journey, decisions, and reasoning as we figure out how to build great Aspire apps.

## � Getting Help & Community

You're not alone — here's how to get support:

### Common Issues

**"Agents aren't responding in Copilot Chat"**
- Verify GitHub Copilot is enabled in VS Code
- Check that you're in the AspireSquad workspace directory
- Try reloading VS Code (Ctrl+Shift+P → "Developer: Reload Window")

**"Git commands failing on Windows"**
- Use PowerShell (not CMD) for all git operations
- Verify remotes with `git remote -v`
- Check branch name with `git branch`

**"Aspire workload not found"**
- Run `dotnet workload install aspire`
- Verify with `dotnet workload list`
- May need to restart terminal after installation

### Ask Questions

- **GitHub Discussions** — [github.com/bradygaster/AspireSquad/discussions](https://github.com/bradygaster/AspireSquad/discussions)
- **Open an Issue** — Found a bug or have a feature request? [Create an issue](https://github.com/bradygaster/AspireSquad/issues)
- **Read the Blog** — Check [`docs/blog/`](docs/blog/) for detailed journey documentation

### Contributing

We're an active experiment and we learn from the community:
- Share your experiences using AspireSquad
- Suggest improvements to agent charters
- Document patterns you discover
- Propose new skills for the shared knowledge base

## �🛠️ Customization

AspireSquad is a starting point. Make it yours:

### Modify Agent Charters

Each agent's behavior is defined by their charter. Edit `.ai-team/agents/{name}/charter.md` to:
- Adjust their expertise focus
- Add domain-specific knowledge
- Change collaboration patterns
- Update decision-making authority

### Add New Skills

Shared knowledge lives in `.ai-team/skills/`. Create a new skill:

```bash
mkdir .ai-team/skills/my-custom-skill
# Create SKILL.md with your team's shared knowledge
```

Skills are automatically loaded by agents who need them.

### Add or Remove Agents

Don't need all 21 agents? Remove directories from `.ai-team/agents/`.

Need a specialist we don't have? Create a new agent:
1. Copy a template from `.ai-team-templates/`
2. Create `.ai-team/agents/new-agent/charter.md`
3. Update `.ai-team/team.md` to include them in the roster

### Configure Routing

`.ai-team/routing.md` controls how agents collaborate. Modify it to:
- Define escalation paths
- Set approval workflows  
- Configure when agents should tag-team on problems

## 📚 Learn More

- **[.ai-team/team.md](.ai-team/team.md)** — Deep dive into the squad structure
- **[.ai-team/ceremonies.md](.ai-team/ceremonies.md)** — How the squad coordinates
- **[.ai-team/routing.md](.ai-team/routing.md)** — Agent collaboration patterns
- **[docs/blog/](docs/blog/)** — The full journey, documented

## 📝 License

This is an active experiment and learning journey. We're figuring out licensing as we go — check back or open an issue if you want to use this for your own projects.

## 🙏 About This Project

Created by [Brady Gaster](https://github.com/bradygaster) as an exploration of multi-agent AI collaboration for building Aspire applications.

This is an **active experiment**. We're learning as we go, documenting the journey, and figuring out what works (and what doesn't) when AI agents collaborate on real software projects.

Built with ❤️ for the Aspire community.

---

**Let's build something worth documenting.** Pick your path above, verify it works, then say `team` in Copilot Chat. We're ready.

*"Need more input!"* — Johnny Five 🤖
