# Team Roster

> Building Aspire applications with an AI squad named after famous robots from pop culture.

## Coordinator

| Name | Role | Notes |
|------|------|-------|
| Squad | Coordinator | Routes work, enforces handoffs and reviewer gates. Does not generate domain artifacts. |

## Members

| Name | Role | Charter | Status |
|------|------|---------|--------|
| Data | Aspire Generalist | `.ai-team/agents/data/charter.md` | ✅ Active |
| Johnny Five | Blogger | `.ai-team/agents/johnny-five/charter.md` | ✅ Active |
| Bishop | GitOps | `.ai-team/agents/bishop/charter.md` | ✅ Active |
| Baymax | DevRel | `.ai-team/agents/baymax/charter.md` | ✅ Active |
| Scribe | Session Logger | `.ai-team/agents/scribe/charter.md` | 📋 Silent |
| Ralph | Work Monitor | — | 🔄 Monitor |

## Coding Agent

<!-- copilot-auto-assign: false -->

| Name | Role | Charter | Status |
|------|------|---------|--------|
| @copilot | Coding Agent | — | 🤖 Coding Agent |

### Capabilities

**🟢 Good fit — auto-route when enabled:**
- Bug fixes with clear reproduction steps
- Test coverage (adding missing tests, fixing flaky tests)
- Lint/format fixes and code style cleanup
- Dependency updates and version bumps
- Small isolated features with clear specs
- Boilerplate/scaffolding generation
- Documentation fixes and README updates

**🟡 Needs review — route to @copilot but flag for squad member PR review:**
- Medium features with clear specs and acceptance criteria
- Refactoring with existing test coverage
- API endpoint additions following established patterns
- Migration scripts with well-defined schemas

**🔴 Not suitable — route to squad member instead:**
- Architecture decisions and system design
- Multi-system integration requiring coordination
- Ambiguous requirements needing clarification
- Security-critical changes (auth, encryption, access control)
- Performance-critical paths requiring benchmarking
- Changes requiring cross-team discussion

## Project Context

- **Owner:** bradygaster (bradyg@microsoft.com)
- **Stack:** .NET, Aspire, C#
- **Description:** Building Aspire applications and blogging the journey with an AI squad
- **Created:** 2026-02-16
