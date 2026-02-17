# Aspire CLI

> The command-line interface for creating, orchestrating, and deploying Aspire distributed applications.

**Confidence:** low
**Source:** earned
**Last validated:** 2026-02-16

## When to Use

Use the Aspire CLI when:
- Creating new Aspire projects from templates (`aspire new`)
- Adding Aspire orchestration to existing .NET solutions (`aspire init`)
- Adding hosting integrations and components (`aspire add`)
- Running and debugging Aspire AppHost locally (`aspire run`)
- Generating deployment manifests for cloud environments (`aspire publish`)
- Deploying Aspire applications to Azure Container Apps (`aspire deploy`)
- Managing Aspire CLI configuration (`aspire config`)
- Updating Aspire packages and CLI to latest versions (`aspire update`)
- Configuring MCP for AI coding agent integration (`aspire mcp init`)

## Core Commands

### Project Initialization & Creation

#### `aspire new [template]`
Creates a new Aspire project from a template.
- **Usage:** `aspire new` or `aspire new aspire-starter`
- **Common options:**
  - `--name`, `-n`: Project name
  - `--output`, `-o`: Output directory
  - `--source`, `-s`: Custom NuGet source for templates
  - `--version`: Specific template version
  - `--channel`: Template feed (stable or preview). Choice persists to `~/.aspire/globalsettings.json` for future commands
- **Key templates:**
  - `aspire-starter` (default): Recommended quickstart with AppHost, ServiceDefaults, API, and frontend
  - `aspire-ts-cs-starter`: TypeScript/React frontend + ASP.NET Core backend starter
  - `aspire`: Empty AppHost project
  - `aspire-apphost`: Just the orchestrator
  - `aspire-servicedefaults`: Just the shared configuration library
  - `aspire-integration-tests`: Test project scaffold for integration testing

#### `aspire init`
Adds Aspire orchestration to an existing .NET solution (brownfield approach).
- **Usage:** `aspire init` (run in a directory with a `.sln` file)
- **Behavior:**
  - Detects existing `.sln` or `.slnx` file
  - Generates AppHost and ServiceDefaults projects
  - Registers both projects in the solution
  - If no solution file exists, creates a minimal AppHost
- **Options:**
  - `--source`: Custom NuGet source
  - `--version`: Template version
  - `--channel`: Template feed (stable or preview). Choice persists to `~/.aspire/globalsettings.json` for future commands

### Component & Integration Management

#### `aspire add [name|id]`
Adds official Aspire hosting integrations to your AppHost project.
- **Usage:** `aspire add` (shows interactive list) or `aspire add redis` (add specific package)
- **Effect:** Adds NuGet package reference to AppHost and provides extension methods for orchestration
- **Common packages added:**
  - `Aspire.Hosting.Redis` — Redis container
  - `Aspire.Hosting.PostgreSQL` — PostgreSQL database
  - `Aspire.Hosting.SqlServer` — SQL Server database
  - `Aspire.Hosting.RabbitMQ` — Message broker
  - `Aspire.Hosting.Dapr` — Dapr distributed application runtime
  - Other databases, caches, and cloud services

**NuGet Naming Conventions:**
- Hosting packages: `Aspire.Hosting.<Technology>` (e.g., `Aspire.Hosting.Redis`)
- Client packages: `Aspire.<Organization>.<Technology>.Client` (e.g., `Aspire.StackExchange.Redis`)
- Community packages: `CommunityToolkit.Aspire.Hosting.<Technology>`

### Runtime & Development

#### `aspire run`
Runs the AppHost and all associated projects in development mode.
- **Usage:** `aspire run` (run from project directory)
- **Behavior:**
  - Auto-discovers AppHost project in current or subdirectory
  - Builds all resources
  - Starts the distributed application
  - Launches the Aspire Dashboard at `http://localhost:18888`
  - Watches for file changes and reloads on save (in preview)
- **Difference from `dotnet run`:**
  - `aspire run` orchestrates the entire distributed system
  - `dotnet run` only runs the AppHost without distributed features
- **Dashboard Features:**
  - Real-time service logs and traces
  - Resource monitoring (CPU, memory, network)
  - Container endpoint URLs
  - OTLP telemetry visualization

#### `aspire config`
Manages Aspire CLI configuration.
- **Subcommands:**
  - `aspire config list` — List all configuration values
  - `aspire config get <key>` — Get a specific value
  - `aspire config set <key> <value>` — Set a configuration value
  - `aspire config delete <key>` — Delete a configuration value
- **Example:** `aspire config set dashboard.otlp-endpoint http://custom:18889`

### Updates & Maintenance

#### `aspire update`
Updates Aspire packages and the Aspire CLI to the latest versions.
- **Usage:**
  - `aspire update` — Update Aspire packages in current AppHost project
  - `aspire update --self` — Update the Aspire CLI tool itself
  - `aspire update --check` — Check for available updates without applying them
- **Behavior:**
  - Updates all `Aspire.*` package references to latest versions
  - Respects channel selection (stable vs preview) from global settings
  - Shows version changes and requires confirmation before applying
- **Example workflow:**
```bash
# Check if updates are available
aspire update --check

# Update packages in current project
aspire update

# Update the CLI tool itself
aspire update --self
```

### AI Integration & Tooling

#### `aspire mcp init`
Configures Model Context Protocol (MCP) for AI coding agents to work with Aspire applications.
- **Usage:** `aspire mcp init` (run in AppHost directory)
- **Behavior:**
  - Initializes MCP configuration for the current Aspire app
  - Exposes integration documentation to AI agents
  - Exposes AppHost state and resource definitions to AI agents
  - Creates `.mcp/` configuration in project root
- **Use case:** Enables AI coding assistants (like GitHub Copilot, Cursor, etc.) to understand your Aspire app structure, available integrations, and deployment state
- **Example:**
```bash
cd ./MyAspireApp.AppHost
aspire mcp init
# AI agents can now query Aspire app structure and docs
```

### Deployment & Publishing

#### `aspire publish`
Generates deployment artifacts (manifests) describing Aspire resources.
- **Usage:** `aspire publish --output ./manifests`
- **Output:** JSON manifest files describing containers, services, and resources
- **Use case:** Preparation for deployment to various environments (Azure, Docker Compose, Kubernetes, etc.)

#### `aspire deploy` (Preview)
Deploys artifacts created by `aspire publish` to target environments.
- **Usage:** `aspire deploy --from ./manifests --target azure-container-apps`
- **Status:** Preview/emerging feature

### Global Options (All Commands)
- `-h`, `--help` — Show help for the command
- `-d`, `--debug` — Enable debug logging
- `--wait-for-debugger` — Wait for debugger before running
- `--version` — Print Aspire CLI version
- `--allow-preview` — Allow preview/experimental features

## Template Workflows

### New Project from Scratch
```bash
# Create new Aspire starter project
aspire new aspire-starter -n MyAspireApp -o ~/projects/

# Navigate and run
cd ~/projects/MyAspireApp
aspire run
```

The starter template includes:
- **AppHost**: Orchestration project that models services and resources
- **ServiceDefaults**: Shared configuration library (telemetry, resiliency, discovery)
- **API**: Example backend service
- **Web**: Example frontend (Blazor or React)
- Integration test project (optional)

### Adding Aspire to Existing .NET Solution
```bash
# In directory with existing .sln file
aspire init

# View the newly added AppHost
code ./MyExistingApp.AppHost/Program.cs

# Run with Aspire
aspire run
```

### Project Structure Best Practices
```
MyAspireApp/
├── MyAspireApp.AppHost/           # Orchestration project (references others)
│   ├── Program.cs                 # Resource definitions
│   └── appsettings.json           # AppHost config
├── MyAspireApp.ServiceDefaults/   # Shared config library
│   ├── Extensions.cs              # Telemetry, resiliency, discovery
│   └── *.cs
├── MyAspireApp.Api/               # Example API service
├── MyAspireApp.Web/               # Example frontend
└── MyAspireApp.Tests/             # Integration tests
```

## Component Management Patterns

### Adding Database Components

**PostgreSQL:**
```bash
aspire add postgres

# In AppHost/Program.cs:
var postgres = builder.AddPostgres("postgres");
var db = postgres.AddDatabase("mydb");
var apiService = builder.AddProject<Projects.Api>("api")
  .WithReference(db);
```

**SQL Server:**
```bash
aspire add sqlserver

# In AppHost/Program.cs:
var sqlserver = builder.AddSqlServer("sqlserver");
var db = sqlserver.AddDatabase("mydb");
```

### Adding Cache & Messaging

**Redis:**
```bash
aspire add redis

var redis = builder.AddRedis("redis");
var api = builder.AddProject<Projects.Api>("api")
  .WithReference(redis);
```

**RabbitMQ:**
```bash
aspire add rabbitmq

var rabbitmq = builder.AddRabbitMQ("messaging");
var worker = builder.AddProject<Projects.Worker>("worker")
  .WithReference(rabbitmq);
```

### Adding Cloud Integrations

**Azure Container Apps:**
```bash
aspire add azure-container-apps

# In AppHost/Program.cs:
builder.AddAzureContainerAppEnvironment("aca");
```

**Azure Managed Redis (Cloud Cache):**
```bash
aspire add azure-redis

# In AppHost/Program.cs:
var redis = builder.AddAzureManagedRedis("cache");
var api = builder.AddProject<Projects.Api>("api")
  .WithReference(redis);
```

**Note:** As of Aspire 13.1, Azure Redis Enterprise APIs have been renamed:
- `AddAzureRedisEnterprise` → `AddAzureManagedRedis` (new name)
- `AddAzureRedis` is now obsolete — use `AddAzureManagedRedis` instead

## Run and Debug Workflows

### Local Development with Dashboard
```bash
# Terminal 1: Start Aspire
aspire run

# Terminal 2 (if needed): Attach debugger to AppHost
# Dashboard auto-opens at http://localhost:18888
```

### Dashboard Access & Configuration

**Default Endpoints:**
- **Dashboard UI:** `http://localhost:18888`
- **OTLP gRPC:** `http://localhost:18889`
- **OTLP HTTP:** `http://localhost:18890`
- **Resource Service:** `http://localhost:18891`

**Environment Variables (in launchSettings.json or AppHost):**
```json
{
  "ASPNETCORE_URLS": "http://localhost:18888",
  "DOTNET_DASHBOARD_OTLP_ENDPOINT_URL": "http://localhost:18889",
  "DOTNET_DASHBOARD_UNSECURED_ALLOW_ANONYMOUS": "true",
  "DASHBOARD__TELEMETRYLIMITS__MAXLOGCOUNT": "50000"
}
```

### Debugging a Single Service
```csharp
// In AppHost/Program.cs
var api = builder.AddProject<Projects.Api>("api")
  .WithEnvironment("ASPNETCORE_ENVIRONMENT", "Development")
  .WithEnvironment("DOTNET_ENVIRONMENT", "Development");

// Attach debugger to api process in your IDE
```

## Deployment Workflows

### Azure Container Apps with Azure Developer CLI (azd)

**Prerequisites:**
```bash
# Install Azure Developer CLI
winget install azure-cli
# or brew install azure-cli (macOS)

# Install Aspire CLI
dotnet tool install -g aspire
```

**Deployment Steps:**

1. **Initialize azd in Aspire project:**
```bash
cd ./MyAspireApp
azd init --template aspire
# Prompts for project name, subscription, etc.
```

2. **Provision Azure Infrastructure:**
```bash
azd provision
# Generates Bicep templates, creates:
# - Container Apps Environment
# - Azure Container Registry (ACR)
# - Log Analytics Workspace
# - Managed Identity
# - Other required resources
```

3. **Deploy Application:**
```bash
azd deploy
# Builds container images
# Pushes to ACR
# Updates Azure Container Apps services
```

4. **Generate & Customize Bicep (Optional):**
```bash
azd infra gen
# Outputs /infra directory with:
# - main.bicep
# - resources.bicep
# - parameters.json
# Edit for custom scaling, networking, policies, etc.
```

**Manifest Generation (Manual):**
```bash
aspire publish --output ./manifests
# Generates JSON manifests describing all resources
# Can be used with other deployment tools
```

### Key Deployment Concepts

**azd Integration:**
- AppHost is executed with special flags to generate deployment manifest
- All container images are built and pushed to ACR
- Services are mapped to Azure Container Apps
- Bicep templates automate infrastructure provisioning

**Custom Bicep:**
```bicep
// /infra/main.bicep
param location string = resourceGroup().location
param environment string = 'dev'

// Resources generated from AppHost
resource containerApp 'Microsoft.App/containerApps@2023-05-01' = {
  name: 'myapp-${environment}'
  location: location
  // ...
}
```

**Environment Configuration:**
```bash
# .env file for azd
AZURE_SUBSCRIPTION_ID=xxx
AZURE_LOCATION=eastus
AZURE_RESOURCE_GROUP=myapp-rg
```

## Anti-Patterns

**Don't:**
- Use `dotnet run` on AppHost directly when testing the distributed system; use `aspire run`
- Add database/infrastructure packages without using `aspire add`; this skips configuration helpers
- Run `aspire new` inside an existing solution directory; use `aspire init` instead
- Modify AppHost resource definitions without understanding the reference model
- Deploy to Azure without understanding azd and Bicep customization options
- Commit secrets to AppHost configuration; use environment variables or Azure Key Vault

**Avoid in AppHost:**
- Direct database connection strings in code (use resource references)
- Hard-coded container image names (let Aspire template them)
- Mixing orchestration logic with business logic

## References

- **Official Aspire Docs:** https://aspire.dev/
- **CLI Overview:** https://aspire.dev/reference/cli/overview/
- **Templates:** https://aspire.dev/get-started/aspire-sdk-templates/
- **Component Integrations:** https://aspire.dev/integrations/overview/
- **Deployment to Azure:** https://aspire.dev/deployment/azure/aca/
- **Dashboard Configuration:** https://aspire.dev/dashboard/configuration/
- **Custom Integrations:** https://aspire.dev/integrations/custom-integrations/hosting-integrations/
- **GitHub: dotnet/aspire:** https://github.com/dotnet/aspire
- **Community Toolkit:** https://github.com/CommunityToolkit/Aspire
