# Project Context

- **Owner:** bradygaster (bradyg@microsoft.com)
- **Project:** Building Aspire applications and blogging the journey with an AI squad
- **Stack:** .NET, Aspire, C#
- **Created:** 2026-02-16

## Learnings

<!-- Append new learnings below. Each entry is something lasting about the project. -->

### Aspire CLI Architecture & Workflows (2026-02-16)

The Aspire CLI is a greenfield/brownfield orchestration tool with three primary workflows:

**1. Project Initialization**
- `aspire new` creates from templates (starter, apphost, servicedefaults, integration-tests)
- `aspire init` retrofits existing .NET solutions with AppHost + ServiceDefaults
- Templates are distributed via NuGet and configurable per source/channel

**2. Component Management** 
- `aspire add` integrates hosting packages (Redis, PostgreSQL, RabbitMQ, etc.)
- Naming: `Aspire.Hosting.<Tech>` (hosting), `Aspire.*.Client` (client), `CommunityToolkit.Aspire.Hosting.*` (community)
- Packages provide extension methods for fluent AppHost orchestration

**3. Development-to-Deployment Pipeline**
- Local: `aspire run` launches AppHost + Dashboard (localhost:18888) with OTLP telemetry at :18889/:18890/:18891
- Publish: `aspire publish` generates JSON manifests of all resources
- Deploy: `aspire deploy` (preview) or `azd` integration for Azure Container Apps
- `azd` auto-generates Bicep IaC, builds containers, pushes to ACR, deploys to ACA

**Key Patterns:**
- AppHost is the single source of truth for distributed app topology
- Service references are declarative (no connection strings in code)
- Dashboard provides real-time telemetry, logs, traces, metrics, and resource endpoints
- Bicep customization enables enterprise networking, scaling, policies without touching AppHost

**For blogging:** Aspire CLI reduces friction in polyglot, cloud-native app development by unifying local orchestration with production deployment. The template + add + run pattern is intuitive for new adopters, and azd integration makes Azure deployment near-zero-config.

### README Developer Experience Patterns (2026-02-16)

When reviewing README files for developer-focused projects, prioritize these clarity patterns:

**1. Early Expectation Setting**
- Surface experimental status within first 3 lines (not buried at bottom)
- Use visual callouts (⚠️, 🚧) to signal "this is bleeding edge"
- Distinguish between "framework to adopt" vs "example to learn from"

**2. Prerequisites Before Quick Start**
- List required tools, subscriptions, SDKs upfront
- Include verification steps ("how do I know this worked?")
- Prevents "did I miss something?" confusion after setup

**3. Platform-Appropriate Commands**
- For .NET projects: Windows PowerShell first, Unix alternatives second
- For Node.js projects: Unix first (npm ecosystem leans Linux/macOS)
- Match command syntax to developer's expected environment

**4. Conceptual Over Countable**
- Avoid leading with implementation details ("21 agents")
- Lead with roles and capabilities ("specialists for testing, deployment, security")
- Implementation counts can change; conceptual model should be stable

**5. Bridge the Setup-to-Usage Gap**
- Add "What Happens Next" section after getting-started
- Show example output/interaction patterns
- Explain the mechanics of invocation (e.g., `@squad` in Copilot Chat)

**Key Files:**
- [README.md](../../../README.md) — Main entry point for AspireSquad framework
- `.ai-team/agents/{name}/charter.md` — Each agent's role definition
- `.github/agents/squad.agent.md` — Coordinator prompt for Copilot integration

📌 Team update (2026-02-16): README Structure & Onboarding standards consolidated — prerequisites upfront, status clarity, recommended paths, instant validation, progressive disclosure, visible support — decided by Data, Baymax

📌 Team update (2026-02-16): Git Workflow Documentation Standards established — always include verification commands, checks for destructive operations, cross-platform examples, branch awareness, conflict resolution guidance — decided by Bishop

📌 Team update (2026-02-16): All project documentation goes in docs/ folder, blog posts in docs/blog/ — user directive via Copilot

📌 Team update (2026-02-16): Aspire CLI as core skill — agents should prefer CLI-based workflows for Aspire development — user directive via Copilot
