# Project Context

- **Owner:** bradygaster (bradyg@microsoft.com)
- **Project:** Building Aspire applications and blogging the journey with an AI squad
- **Stack:** .NET, Aspire, C#
- **Created:** 2026-02-16

## Learnings

<!-- Append new learnings below. Each entry is something lasting about the project. -->

### Aspire CLI Architecture & Workflows (2026-02-16)

The .NET Aspire CLI is a greenfield/brownfield orchestration tool with three primary workflows:

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
