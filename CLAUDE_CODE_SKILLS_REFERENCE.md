# Claude Code Skills & Agents — Complete Reference Guide

> A detailed reference for all installed skills, agents, plugins, and MCP servers in this Claude Code setup.
> Covers when to use each tool, what commands are available, and how they work together.

---

## Table of Contents

1. [GSD — Get Shit Done](#1-gsd--get-shit-done)
2. [everything-claude-code (ECC)](#2-everything-claude-code-ecc)
3. [ui-ux-pro-max](#3-ui-ux-pro-max)
4. [claude-mem](#4-claude-mem)
5. [Superpowers](#5-superpowers)
6. [MCP Servers](#6-mcp-servers)
7. [awesome-claude-code (Resource Directory)](#7-awesome-claude-code-resource-directory)
8. [How They Work Together](#8-how-they-work-together)
9. [Quick Decision Guide](#9-quick-decision-guide)

---

## 1. GSD — Get Shit Done

**Source:** https://github.com/gsd-build/get-shit-done
**Install method:** `npx get-shit-done-cc`
**Namespace:** `/gsd:*`
**Role:** Macro-level project manager — takes you from idea to shipped product through structured phases.

### What it does

GSD is a full spec-driven development system. It enforces a **Research → Plan → Execute → Verify** loop for every feature or project. It manages roadmaps, phases, and milestones, and uses specialized sub-agents to handle each stage autonomously.

### When to use it

- Starting a new project from scratch
- Managing a multi-phase build with multiple features
- When you want structured planning before writing any code
- When you need to track progress across long sessions or days of work
- Debugging a complex, hard-to-reproduce issue systematically

### Commands

| Command | What it does | When to use |
|---|---|---|
| `/gsd:new-project` | Deep context gathering, creates roadmap and phase breakdown | Day 1 of a new project |
| `/gsd:plan-phase` | Creates a detailed `PLAN.md` for a specific phase with verification loop | Before executing any phase |
| `/gsd:execute-phase` | Runs all plans in a phase using wave-based parallelization | After planning is approved |
| `/gsd:progress` | Shows current phase status, what's done, what's next | Daily check-in |
| `/gsd:debug` | Systematic debugging with persistent state across context resets | Hard bugs that need investigation |
| `/gsd:resume-work` | Restores full context from a previous session | Coming back after a break |
| `/gsd:new-milestone` | Archives current milestone, starts next version cycle | After shipping a version |
| `/gsd:verify-work` | Validates built features through conversational UAT | After executing a phase |
| `/gsd:map-codebase` | Runs parallel mapper agents to analyze and document the codebase | Before planning on an existing repo |
| `/gsd:add-phase` | Adds a new phase to the end of the current milestone | When scope expands |
| `/gsd:insert-phase` | Inserts urgent work as a decimal phase (e.g., 2.1) between existing phases | Urgent mid-milestone work |
| `/gsd:remove-phase` | Removes a future phase and renumbers subsequent ones | Descoping work |
| `/gsd:health` | Diagnoses planning directory health and optionally repairs issues | When something seems broken |
| `/gsd:settings` | Configure model profile and workflow toggles | Setup/config |
| `/gsd:help` | Full command list and usage guide | Getting started |

### Key concepts

- **Phases** — discrete chunks of work with a plan, execution, and verification step
- **Milestones** — a group of phases that together ship a version
- **PLAN.md** — the artifact GSD creates before executing; acts as the source of truth
- **Wave-based execution** — parallel agent execution for independent tasks within a phase

---

## 2. everything-claude-code (ECC)

**Source:** https://github.com/affaan-m/everything-claude-code
**Install method:** Claude plugin marketplace
**Namespace:** `/everything-claude-code:*`
**Role:** Micro-level coding toolkit — handles individual tasks, code quality, testing, security, and reviews.

### What it does

ECC is a collection of 100+ skills, 14+ agents, hooks, and commands built from months of intensive Claude Code use. It covers nearly every coding workflow — from TDD to security scanning to content creation to deployment patterns.

### When to use it

- Writing code and want to enforce good practices (TDD, security, reviews)
- Need a quick plan for a single task without full GSD overhead
- Working in a specific language or framework and want best-practice patterns
- Doing research before building
- Reviewing code you or someone else wrote

### Core Commands

| Command | What it does | When to use |
|---|---|---|
| `/everything-claude-code:tdd` | Enforces test-driven development — write tests first, then implementation | Any new feature or bug fix |
| `/everything-claude-code:security-review` | Scans for OWASP Top 10, secrets, injection, SSRF, unsafe crypto | After touching auth, APIs, or user input |
| `/everything-claude-code:plan` | Restates requirements, assesses risks, creates step-by-step plan | Before a non-trivial task |
| `/everything-claude-code:blueprint` | Turns a one-line objective into a full construction plan | When you have an idea but no plan |
| `/everything-claude-code:e2e` | Generates and runs Playwright end-to-end tests | After building a UI feature |
| `/everything-claude-code:deep-research` | Multi-source research using web and code search | Before building something new |
| `/everything-claude-code:prompt-optimize` | Analyzes and improves a prompt you're writing | When crafting prompts for AI |

### Language-Specific Reviews & TDD

| Command | Language/Stack |
|---|---|
| `/everything-claude-code:python-review` | Python — PEP 8, type hints, security |
| `/everything-claude-code:go-review` | Go — idiomatic patterns, concurrency |
| `/everything-claude-code:kotlin-review` | Kotlin/Android — coroutines, Compose |
| `/everything-claude-code:go-test` | Go — table-driven TDD |
| `/everything-claude-code:kotlin-test` | Kotlin — Kotest TDD |
| `/everything-claude-code:tdd-workflow` | General TDD workflow for any language |

### Build Error Fixers

| Command | When to use |
|---|---|
| `/everything-claude-code:go-build` | Go build or vet errors |
| `/everything-claude-code:kotlin-build` | Kotlin/Gradle build failures |
| `/everything-claude-code:gradle-build` | Android/KMP Gradle errors |

### Session & Memory

| Command | What it does |
|---|---|
| `/everything-claude-code:save-session` | Saves current session state to `~/.claude/sessions/` |
| `/everything-claude-code:resume-session` | Loads the most recent saved session |
| `/everything-claude-code:learn-eval` | Extracts reusable patterns from the session |

### Other Notable Skills

| Command | What it does |
|---|---|
| `/everything-claude-code:aside` | Answers a quick side question without losing main context |
| `/everything-claude-code:verification-loop` | Comprehensive verification system for a session |
| `/everything-claude-code:configure-ecc` | Interactive installer to set up ECC features |
| `/everything-claude-code:skill-create` | Analyzes local git history and generates a custom skill |
| `/everything-claude-code:instinct-status` | Shows learned instincts (project + global) with confidence scores |

---

## 3. ui-ux-pro-max

**Source:** https://github.com/nextlevelbuilder/ui-ux-pro-max-skill
**Install method:** Claude plugin marketplace
**Namespace:** `/ui-ux-pro-max:ui-ux-pro-max`
**Role:** UI/UX design intelligence — makes Claude an expert designer for any stack.

### What it does

Gives Claude access to a comprehensive design system library including 50+ visual styles, 161 color palettes, 57 font pairings, and component patterns. Works across 10 major stacks.

### When to use it

- Starting a new UI and need a design direction
- Picking a color palette or font combination
- Designing components and want best-practice implementations
- Building a consistent design system across a project
- Translating a vague "make it look good" request into a concrete design spec

### Supported Stacks

| Stack | Supported |
|---|---|
| React | ✓ |
| Next.js | ✓ |
| Vue | ✓ |
| Svelte | ✓ |
| SwiftUI | ✓ |
| React Native | ✓ |
| Flutter | ✓ |
| Tailwind CSS | ✓ |
| shadcn/ui | ✓ |
| HTML/CSS | ✓ |

### How to invoke

Just run `/ui-ux-pro-max:ui-ux-pro-max` and describe what you're building. It will ask about your stack, style preferences, and then output design recommendations with component code.

---

## 4. claude-mem

**Source:** https://github.com/thedotmack/claude-mem
**Install method:** Claude plugin marketplace (`claude-mem@thedotmack`)
**Namespace:** `/do`, `/make-plan`, `/mem-search`, `/smart-explore`
**Role:** Persistent memory compression — remembers context across sessions automatically.

### What it does

claude-mem hooks into your Claude Code sessions and compresses important context — decisions made, code written, problems solved, patterns learned — into a persistent memory store. When you start a new session, this context is automatically loaded so Claude isn't starting from scratch.

### When to use it

- Working on a long-running project across multiple days
- You've explained your codebase/architecture before and don't want to repeat it
- You want Claude to remember past decisions and not contradict them
- Returning to a project after a break

### Commands

| Command | What it does | When to use |
|---|---|---|
| `/mem-search` | Search your memory store for past context | Finding a past decision or discussion |
| `/make-plan` | Creates a plan with full historical memory context loaded | Planning that should consider past work |
| `/do` | Executes a task with memory context injected | Any task that benefits from session history |
| `/smart-explore` | Explores the codebase with memory of past explorations | Navigating a familiar but large codebase |

### How it works automatically

After install, claude-mem registers hooks that:
1. **Observe** your session in real-time
2. **Compress** important context at the end of each session
3. **Inject** relevant memories at the start of new sessions

No manual action needed — it runs in the background.

---

## 5. Superpowers

**Source:** https://github.com/obra/superpowers
**Install method:** `claude plugins install superpowers@claude-plugins-official`
**Namespace:** Skills trigger automatically — no `/command` needed
**Role:** Complete software development workflow — spec → plan → subagent-driven execution.

### What it does

Superpowers wraps the full development workflow in a set of composable skills that activate automatically. When you describe a feature to build, it steps back and teases out a proper spec before writing any code. Then it creates a clear plan, executes it via subagent-driven development, and verifies the result.

### When to use it

- You want structured spec/plan/execute flow without explicit commands
- Building features where autonomous multi-hour execution without deviation is desirable
- Pair with GSD for maximum structure, or use standalone for lighter projects
- Enforces TDD, YAGNI, and DRY automatically

### Skills (trigger automatically)

| Skill | What it does |
|---|---|
| `brainstorming` | Teases out a clear spec through conversation before writing code |
| `writing-plans` | Creates clear implementation plans a junior dev could follow |
| `executing-plans` | Runs plans via subagent-driven development with inspection |
| `test-driven-development` | Enforces true red/green TDD throughout execution |
| `subagent-driven-development` | Parallel subagent execution with review at each step |
| `systematic-debugging` | Structured debugging with root cause investigation |
| `verification-before-completion` | Verifies work against plan criteria before calling it done |
| `requesting-code-review` | Structured code review requests |
| `receiving-code-review` | Processes and applies review feedback |
| `using-git-worktrees` | Manages git worktrees for parallel branch work |
| `dispatching-parallel-agents` | Coordinates multiple agents on independent tasks |
| `finishing-a-development-branch` | Branch cleanup, final checks, and PR preparation |

### Key difference from GSD

GSD requires explicit commands (`/gsd:plan-phase`, `/gsd:execute-phase`) and manages a full project directory structure. Superpowers is lighter — it activates implicitly and focuses on the immediate task. Use GSD for multi-phase projects with roadmaps; Superpowers for individual features or when you want autonomous execution without the overhead.

---

## 6. MCP Servers

MCP (Model Context Protocol) servers extend Claude's capabilities by connecting it to external systems. These are installed globally and available in every session.

### GitHub MCP

**URL:** `https://api.githubcopilot.com/mcp`
**Transport:** HTTP
**Install:** `claude mcp add-json github '{"type":"http","url":"https://api.githubcopilot.com/mcp","headers":{"Authorization":"Bearer YOUR_GITHUB_PAT"}}' --scope user`

Connects Claude directly to the GitHub API. Enables reading repos, managing issues and PRs, monitoring Actions workflows, analyzing security findings, and automating GitHub workflows through natural language.

**Use for:**
- Searching code across repos without leaving the terminal
- Creating/updating issues and PRs
- Checking CI/CD run status and failure analysis
- Reviewing Dependabot alerts and security findings
- Managing releases and notifications

---

### Context7 MCP

**Package:** `@upstash/context7-mcp`
**Transport:** stdio via `npx -y @upstash/context7-mcp@latest`
**Install:** `claude mcp add --transport stdio context7 -- npx -y @upstash/context7-mcp@latest`

Fetches up-to-date, version-specific library documentation and code examples directly from source. Eliminates hallucinated APIs by grounding Claude in real, current docs.

**Use for:**
- Working with any library and needing accurate API docs
- Getting real code examples that match the version you're using
- Avoiding stale knowledge about rapidly-evolving packages (React, Next.js, Tailwind, etc.)

**How to invoke:** Just mention `use context7` in your prompt, or Claude will use it automatically when researching libraries.

---

### Supabase MCP

**URL:** `https://mcp.supabase.com/mcp`
**Transport:** HTTP
**Install:** `claude mcp add --transport http supabase https://mcp.supabase.com/mcp`
**Note:** Requires authentication — run `claude mcp auth supabase` after install.

Direct integration with the Supabase platform. Enables querying databases, managing tables and migrations, reading logs, and interacting with Edge Functions without leaving Claude Code.

**Use for:**
- Querying your Supabase database during development
- Generating and reviewing migrations
- Checking database logs and performance
- Managing RLS policies and Auth configurations
- Deploying and testing Edge Functions

---

### CCUsage MCP

**Package:** `@ccusage/mcp`
**Transport:** stdio via `npx -y @ccusage/mcp@latest`
**Install:** `claude mcp add --transport stdio ccusage -- npx -y @ccusage/mcp@latest`

Exposes Claude Code usage data (token counts, costs, session history) from local JSONL files directly to Claude. Enables real-time cost awareness during sessions.

**Use for:**
- Checking how much a session has cost so far
- Reviewing daily/monthly usage and spend
- Comparing costs across different sessions or projects
- Budget tracking and awareness

**CLI alternative:** `npx ccusage@latest` for a standalone usage report.

---

### notebooklm-mcp

**Binary:** `notebooklm-mcp`
**Transport:** stdio
**Role:** Connects Claude to Google NotebookLM for notebook management, source ingestion, AI audio/video studio creation, and cross-notebook research.

**Use for:**
- Creating NotebookLM notebooks from URLs, text, or Drive documents
- Generating AI audio overviews and video from sources
- Querying notebooks with natural language
- Research synthesis across multiple sources

---

## 7. awesome-claude-code (Resource Directory)

**Source:** https://github.com/hesreallyhim/awesome-claude-code
**Type:** Curated discovery resource — NOT a plugin to install
**Role:** Directory of the best community-built Claude Code tools, skills, hooks, and configs.

### What it is

An "awesome list" — a community-maintained, selectively curated index of everything useful for Claude Code. Think of it as the App Store for Claude Code enhancements.

### When to browse it

- You want to do something your current skills don't cover
- Setting up Claude Code for a new language or framework
- Looking for hooks that automate things in the background
- Want CLAUDE.md templates for a specific project type
- Looking for IDE integrations or usage monitors

### Categories

| Category | What you'll find |
|---|---|
| **Agent Skills** | Specialized agents for coding, research, writing |
| **Workflows & Knowledge Guides** | Best-practice workflow documents to feed Claude |
| **Tooling** | CLI tools, orchestrators, config managers |
| **IDE Integrations** | VS Code, Cursor, JetBrains integrations |
| **Usage Monitors** | Token/cost tracking tools |
| **Hooks** | Auto-triggers on save, tool use, session start/end |
| **Slash Commands** | Ready-made `/commands` for git, testing, CI, docs |
| **CLAUDE.md Files** | Project config templates by language and domain |
| **Status Lines** | Terminal status bar configurations |
| **Alternative Clients** | Non-official Claude Code clients |

---

## 8. How They Work Together

These tools are designed to complement each other — they occupy different layers of your workflow and rarely overlap.

```
┌─────────────────────────────────────────────────────────────┐
│                    PROJECT LEVEL (GSD)                      │
│   /gsd:new-project → /gsd:plan-phase → /gsd:execute-phase  │
│              → /gsd:verify-work → /gsd:progress            │
└─────────────────────────┬───────────────────────────────────┘
                          │
┌─────────────────────────▼───────────────────────────────────┐
│           TASK LEVEL (ECC + Superpowers)                    │
│   /everything-claude-code:tdd → :security-review → :review │
│   Superpowers: spec → plan → subagent execution (auto)      │
└─────────────────────────┬───────────────────────────────────┘
                          │
┌─────────────────────────▼───────────────────────────────────┐
│                  DESIGN LAYER (ui-ux-pro-max)               │
│              /ui-ux-pro-max:ui-ux-pro-max                   │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│               MEMORY LAYER (claude-mem) — always on         │
│        Runs in background, persists context automatically   │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│               MCP LAYER — always available                  │
│  GitHub · Context7 · Supabase · CCUsage · NotebookLM        │
└─────────────────────────────────────────────────────────────┘
```

### Typical full workflow

```
1. Starting a project
   → /gsd:new-project          (research, roadmap, phase breakdown)

2. Planning a phase
   → /gsd:plan-phase           (creates PLAN.md with verification criteria)

3. Executing the phase
   → /gsd:execute-phase        (runs plans with parallel agents)

4. During execution — coding quality
   → /everything-claude-code:tdd              (write tests first)
   → /everything-claude-code:security-review  (check for vulnerabilities)
   → /everything-claude-code:python-review    (language-specific review)

5. Working with libraries
   → Context7 MCP auto-fetches accurate docs (mention "use context7")

6. Working with Supabase backend
   → Supabase MCP for direct DB queries, migrations, and logs

7. Building UI components
   → /ui-ux-pro-max:ui-ux-pro-max            (design system + component code)

8. Verifying the phase
   → /gsd:verify-work          (UAT against plan criteria)

9. Between sessions
   → claude-mem auto-saves context
   → /gsd:resume-work          (restores project context next session)

10. Tracking costs
    → CCUsage MCP for real-time spend during session

11. Discovering new tools
    → browse https://github.com/hesreallyhim/awesome-claude-code
```

---

## 9. Quick Decision Guide

> "Which tool do I reach for?"

| Situation | Use |
|---|---|
| Starting a new project | `/gsd:new-project` |
| Planning a chunk of work | `/gsd:plan-phase` |
| Writing a new feature | `/everything-claude-code:tdd` or Superpowers (auto) |
| Just wrote code, want a quality check | `/everything-claude-code:python-review` (or go/kotlin) |
| About to ship — security check | `/everything-claude-code:security-review` |
| Need a UI component or design direction | `/ui-ux-pro-max:ui-ux-pro-max` |
| Build is failing | `/everything-claude-code:go-build` / `:kotlin-build` |
| Can't find a bug | `/gsd:debug` |
| Returning after a break | `/gsd:resume-work` |
| Need accurate library docs | Context7 MCP (say "use context7") |
| Working with Supabase | Supabase MCP (direct queries/migrations) |
| Managing GitHub issues/PRs | GitHub MCP |
| Checking session costs | CCUsage MCP |
| Looking for a tool you don't have | Browse awesome-claude-code |
| Need context from a past session | `/mem-search` |
| Quick task, no project structure needed | `/everything-claude-code:plan` then just do it |

---

*Generated with Claude Code — maintained at https://github.com/yash-prime/claude-code-skills-reference*
