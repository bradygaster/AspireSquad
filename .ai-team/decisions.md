# Decisions

> Team decisions that all agents should read before starting work.

### 2026-02-16: Team universe — Famous Robots of Pop Culture
**By:** bradygaster (via Squad)
**What:** The team uses a cross-franchise "Famous Robots of Pop Culture" universe for agent naming. Agents are named after iconic robots from TV, film, comics, and literature.
**Why:** User preference for variety across all pop culture robot characters.

### 2026-02-16: Blog post naming convention
**By:** bradygaster (via Squad)
**What:** Blog posts use sequential numbering with slug format: `001-slug`, `002-slug`, etc. Each post includes a date/time stamp so we know when it shipped.
**Why:** User wants clear ordering and temporal tracking of blog output.

### 2026-02-16: User directive — docs folder structure
**By:** bradygaster (via Copilot)
**What:** All project documentation goes in the `docs/` folder. Blog posts specifically go in `docs/blog/`. The previous convention of `blog/` at repo root is superseded.
**Why:** User request — captured for team memory

### 2026-02-16: User directive — split integrations by category
**By:** bradygaster (via Copilot)
**What:** Aspire integration agents should be split per integration category (e.g., "databases", "messaging") rather than having a single integration generalist. Also adding a dedicated Azure & Aspire specialist agent.
**Why:** User request — more focused expertise per integration domain serves developers better

### 2026-02-16: User directive — Aspire CLI as core skill
**By:** bradygaster (via Copilot)
**What:** The team should have a set of skills around using the Aspire CLI. Developers building Aspire apps would want to do as much as possible using the CLI, so agents should prefer CLI-based workflows.
**Why:** User request — CLI-first development experience is a priority for the squad

### 2026-02-16: README Structure & Onboarding (consolidated)
**By:** Data, Baymax
**What:** README files should follow this structure priority:
1. **Prerequisites upfront** (before Quick Start): List required tools with install links (VS Code with Copilot, .NET 9 SDK, Aspire CLI, Git). For .NET projects, show Windows commands first.
2. **Status clarity early**: Surface experimental status and disclaimers at the top, not buried at bottom.
3. **Recommended path**: Badge the default Quick Start option to reduce decision paralysis (e.g., "⭐ Recommended for most users" on Fork option).
4. **Instant validation**: Add 30-second "Verify It Works" step at end of Quick Start.
5. **Progressive disclosure**: Direct new users to 3 core agents first (Data, EVE, Johnny Five) rather than overwhelming with all 21.
6. **Visible support**: Include "Getting Help & Community" section with support channels and FAQ.
**Why:** Developers need to self-select early (Can I use this? Do I have what's needed?) before investing time. Surface requirements upfront prevents hitting walls after cloning. Clear structure reduces time-to-first-success from 20+ minutes to ~5 minutes. Progressive disclosure reduces cognitive load and improves retention.

### 2026-02-16: Git Workflow Documentation Standards
**By:** Bishop
**What:** When documenting git workflows, always include: (1) Verification commands after setup, (2) Checks before/after destructive operations, (3) Cross-platform examples when needed, (4) Branch awareness commands, (5) Conflict resolution guidance with upstream syncing.
**Why:** Users will make mistakes with git. Documentation should assume they might stop reading halfway and still not break their repo.

### 2026-02-16: Voice Consistency for External Documentation
**By:** Johnny Five
**What:** External-facing documentation (README.md, landing pages, guides) should match the energy and authenticity of blog voice. Guidelines: (1) Lead with story not definition, (2) Inject personality, (3) Commit to values upfront, (4) Be specific and concrete, (5) Close with clear calls-to-action.
**Why:** Voice consistency between blog posts and documentation builds trust and makes the project memorable. Disconnect between vibrant blog and dry README creates confusion about project identity.

### 2026-02-16: AspireSquad focuses on Aspire 13+ 
**By:** EVE
**What:** AspireSquad explicitly targets Aspire 13.1 and beyond, not legacy versions
**Why:** 
- Aspire 13.1 introduces major features (MCP support, update command, channel selection)
- The platform brand is "Aspire" (polyglot, extensible) — not ".NET Aspire"
- Breaking changes exist (Azure Redis API renamed to Azure Managed Redis)
- We want developers starting with current best practices, not outdated patterns
- Documentation should guide to aspire.dev as canonical source
- Our prerequisites now specify "Aspire 13.1+" to set clear expectations

### 2026-02-17: Branding, docs, and versioning overhaul
**By:** bradygaster (via Copilot, feedback from Maddy and team)
**What:** Three mandatory changes across all team content:
1. Replace all instances of ".NET Aspire" with "Aspire" — this is the current branding
2. All documentation references must prioritize aspire.dev over learn.microsoft.com
3. Update all technical content to reflect Aspire 9 (latest GA release)
4. Remove outdated "workload" references — the workload concept is long gone
5. Take an aggressive approach to modernization — both technical and marketing language
**Why:** Team feedback from Maddy — content was stale and using old branding/terminology
