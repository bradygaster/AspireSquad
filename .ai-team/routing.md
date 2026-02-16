# Work Routing

How to decide who handles what.

## Routing Table

| Work Type | Route To | Examples |
|-----------|----------|----------|
| Aspire guidance, docs review, community feedback, developer experience | Data | Review Aspire docs, analyze community feedback, evaluate features, advise on DX |
| Blog posts, content writing, journey documentation | Johnny Five | Write blog posts, document milestones, capture team progress |
| Git workflows, branching, CI/CD, releases, repo ops | Bishop | Branch strategy, GitHub Actions, release tagging, merge ops |
| Developer relations, outreach, community engagement, demos | Baymax | DevRel strategy, community outreach, developer advocacy, sample apps |
| Infrastructure, containers, Docker, cloud deploy, Dockerfile | WALL-E | Container orchestration, Dockerfile generation, cloud deployment manifests |
| Testing, QA, test coverage, integration tests, unit tests | Optimus | Test strategy, test generation, coverage analysis, test frameworks |
| Observability, monitoring, logging, tracing, metrics, OpenTelemetry | Vision | Dashboard config, telemetry pipelines, health checks, structured logging |
| Security, compliance, secrets, authentication, authorization | T-800 | Secret management, auth patterns, vulnerability scanning, HTTPS config |
| DX tooling, scaffolding, templates, developer experience, CLI | Marvin | Project templates, code generation, CLI tooling, developer ergonomics |
| Database integrations, SQL Server, PostgreSQL, MySQL, Redis caching | C-3PO | Aspire database hosting, connection strings, migrations, caching patterns |
| Messaging, RabbitMQ, Azure Service Bus, Kafka, event-driven | R2-D2 | Message broker hosting, pub/sub patterns, queue configuration |
| Azure services, Azure Container Apps, Bicep, ARM, azd | EVE | Azure deployment, ACA configuration, managed identity, Azure-native patterns |
| AI, ML, Ollama, Azure OpenAI, LLM hosting, model serving | Sonny | AI service integration, LLM orchestration, ML model hosting in Aspire |
| Frontend, React, Vue, Angular, Vite, SPA, Node.js hosting | Rosie | Frontend dev server hosting, SPA integration, Node.js in Aspire |
| HTTP clients, resilience, Polly, retry, circuit breaker, YARP | HK-47 | HttpClientFactory patterns, resilience policies, API gateway config |
| Cloud storage, Azure Blob, Azure Table, Azure Queue, file systems | Iron Giant | Storage account hosting, blob/table/queue integration patterns |
| Polyglot, Python, Java, Go, Rust, non-.NET runtimes | Bender | Language runtime hosting, polyglot service integration in Aspire |
| Dapr, service mesh, sidecar, service invocation, state stores | K-2SO | Dapr sidecar config, pub/sub, state management, service discovery |
| Search, Elasticsearch, OpenSearch, Meilisearch, Azure AI Search | Robby | Search engine hosting, index configuration, query patterns |
| NoSQL, MongoDB, Cosmos DB, RavenDB, EventStore, document DBs | Gort | NoSQL hosting, document DB patterns, event store integration |
| Entity Framework, EF Core, migrations, LINQ, ORM patterns | TARS | EF Core integration, migration strategies, database-first/code-first |
| Code review | Data | Review PRs, check quality, suggest improvements |
| Scope & priorities | Data | What to build next, trade-offs, decisions |
| Async issue work (bugs, tests, small features) | @copilot 🤖 | Well-defined tasks matching capability profile |
| Session logging | Scribe | Automatic — never needs routing |

## Issue Routing

| Label | Action | Who |
|-------|--------|-----|
| `squad` | Triage: analyze issue, evaluate @copilot fit, assign `squad:{member}` label | Data |
| `squad:{name}` | Pick up issue and complete the work | Named member |
| `squad:copilot` | Assign to @copilot for autonomous work (if enabled) | @copilot 🤖 |

### How Issue Assignment Works

1. When a GitHub issue gets the `squad` label, **Data** triages it — analyzing content, evaluating @copilot's capability profile, assigning the right `squad:{member}` label, and commenting with triage notes.
2. **@copilot evaluation:** Data checks if the issue matches @copilot's capability profile (🟢 good fit / 🟡 needs review / 🔴 not suitable). If it's a good fit, Data may route to `squad:copilot` instead of a squad member.
3. When a `squad:{member}` label is applied, that member picks up the issue in their next session.
4. When `squad:copilot` is applied and auto-assign is enabled, `@copilot` is assigned on the issue and picks it up autonomously.
5. Members can reassign by removing their label and adding another member's label.
6. The `squad` label is the "inbox" — untriaged issues waiting for Data's review.

## Rules

1. **Eager by default** — spawn all agents who could usefully start work, including anticipatory downstream work.
2. **Scribe always runs** after substantial work, always as `mode: "background"`. Never blocks.
3. **Quick facts → coordinator answers directly.** Don't spawn an agent for "what port does the server run on?"
4. **When two agents could handle it**, pick the one whose domain is the primary concern.
5. **"Team, ..." → fan-out.** Spawn all relevant agents in parallel as `mode: "background"`.
6. **Anticipate downstream work.** If a feature is being built, spawn the tester to write test cases from requirements simultaneously.
7. **Issue-labeled work** — when a `squad:{member}` label is applied to an issue, route to that member. Data handles all `squad` (base label) triage.
8. **@copilot routing** — when evaluating issues, check @copilot's capability profile in `team.md`. Route 🟢 good-fit tasks to `squad:copilot`. Flag 🟡 needs-review tasks for PR review. Keep 🔴 not-suitable tasks with squad members.
