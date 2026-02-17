# Project Context

- **Owner:** bradygaster (bradyg@microsoft.com)
- **Project:** Building Aspire applications and blogging the journey with an AI squad
- **Stack:** .NET, Aspire, C#
- **Created:** 2026-02-16

## Learnings

<!-- Append new learnings below. Each entry is something lasting about the project. -->

### 2026-02-16: README Git Workflow Review
**Context:** Reviewed README.md git workflows (fork flow and clone-and-reinit flow) for correctness and completeness.

**Key findings:**
1. **Upstream sync workflow incomplete** — Only showed `git fetch` + `git merge` with no conflict resolution guidance. Recommended rebase-first approach or branch-based merge for safety.
2. **Missing verification steps** — Destructive operations like `rm -rf .git` had no verification. Added `git status`, `git remote -v`, and branch checks.
3. **Cross-platform commands correct but could be clearer** — Dual commands for Windows/Linux are good, but verification commands also need dual versions.
4. **First commit message in Option 2 misleading** — Said "Initial commit: AspireSquad starting point" when it should reflect this is now a different project derived from template.
5. **No branch hygiene guidance** — Neither workflow checked current branch or confirmed default branch name.

**Risk areas identified:**
- Users syncing from upstream will hit merge conflicts on customized `.ai-team/` files with no guidance
- `.git` removal failures can lead to corrupted repo state if not verified
- Default branch name depends on user's git config (`init.defaultBranch`)
- Remote URL typos common and hard to debug without immediate verification

**Git workflow best practices for template repos:**
- Always verify after destructive operations
- Always show remote verification (`git remote -v`)
- For upstream syncing: rebase for individuals, branch-merge for teams
- Template repos should guide users to rename/reclaim the project in first commit

📌 Team update (2026-02-16): Git Workflow Documentation Standards established — always include verification commands, checks for destructive operations, cross-platform examples, branch awareness, conflict resolution guidance — decided by Bishop

### 2026-02-16: Repository initialization and GitHub publication
**Context:** Created public GitHub repository and published initial AspireSquad codebase.

**Key paths:**
- Repository: `https://github.com/bradygaster/AspireSquad`
- Remote: origin → `https://github.com/bradygaster/AspireSquad.git`
- Branch: main (tracking origin/main)
- Initial commit count: 163 objects, 135.66 KiB

**GitHub CLI workflow:**
- Single command `gh repo create` with `--source=.`, `--remote=origin`, `--push` flags handles repository creation, remote setup, and initial push atomically
- Automatically configures upstream tracking for main branch
- Publishes repository with description: "AI agent team framework for building Aspire applications"

**Pre-push requirements verified:**
- Working directory must be clean (all changes committed)
- Committed pending README.md changes before repository creation
- Used standard commit message format for preceding commit
