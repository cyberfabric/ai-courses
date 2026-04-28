# Automating Your Dev Workflow with AI

## Project Description
An HTML course for developers (especially Android/mobile) who use Claude Code daily and want to automate every repetitive part of their workflow. The reader already uses Claude Code for coding tasks but hasn't explored its automation capabilities — skills, hooks, MCP servers, scheduled agents, and CI/CD integration.

**Tool focus: Claude Code only.** This course never references Windsurf, Codex, Cursor, Copilot, or any other AI coding tool. Every example, recipe, and exercise uses Claude Code exclusively.

The style is **"For Dummies"** — friendly, approachable, heavy on practical examples and copy-paste-ready recipes. The reader is a smart developer who wants to stop doing things manually.

## Language Rules
- All content is in **English**
- Tone: friendly, conversational, like a colleague showing you their best automation tricks
- Use real-world developer scenarios (PRs, code review, testing, CI/CD, documentation)
- Address: second person singular (you)
- When introducing an automation, always show: "Here's what you do manually today" → "Here's how to automate it"
- Light humor is welcome — keep it engaging, not dry
- Use short paragraphs — walls of text kill understanding
- **NEVER mention Windsurf, Codex, Cursor, Copilot, or any other AI coding tool** — Claude Code only

## HTML Conventions
- Each chapter is a separate HTML file in `chapters/`
- Shared CSS: `assets/style.css` (relative path from chapters/)
- Each page includes:
  - `<nav class="top-nav">` with links to prev/next chapter, index, and theme toggle button
  - `<header class="chapter-header">` with chapter number and title
  - `<main>` with content
  - `<footer>` with prev/next navigation
  - `<script>` at the end of body for theme toggle (localStorage)
- Encoding: UTF-8
- HTML5 doctype
- Meta viewport for responsive
- Target chapter length: **400-600 lines HTML**

## File Structure
```
AI-Workflow/
  CLAUDE.md                                — This file
  .claude/
    commands/
      generate-next-chapter.md             — Skill for chapter generation
  chapters/
    index.html                             — Landing page with navigation
    assets/
      style.css                            — Shared CSS with dark/light theme
    01-automated-developer.html            — The Automated Developer
    02-automation-toolkit.html             — Your Automation Toolkit
    03-custom-skills.html                  — Custom Claude Code Skills
    04-hooks.html                          — Hooks That Work For You
    05-code-review.html                    — AI-Powered Code Review
    06-automating-tests.html               — Automating Tests with AI
    07-cicd-meets-ai.html                  — CI/CD Meets AI
    08-documentation.html                  — Documentation That Writes Itself
    09-productivity-agents.html            — Personal Productivity Agents
    10-mcp-servers.html                    — MCP Servers for Your Team
    11-orchestrating-workflows.html        — Orchestrating Multi-Step Workflows
    12-automation-playbook.html            — Your Automation Playbook
```

## Progress Tracking
- [x] Chapter 1: The Automated Developer
- [x] Chapter 2: Your Automation Toolkit
- [x] Chapter 3: Custom Claude Code Skills
- [x] Chapter 4: Hooks That Work For You
- [x] Chapter 5: AI-Powered Code Review
- [x] Chapter 6: Automating Tests with AI
- [x] Chapter 7: CI/CD Meets AI
- [x] Chapter 8: Documentation That Writes Itself
- [x] Chapter 9: Personal Productivity Agents
- [x] Chapter 10: MCP Servers for Your Team
- [x] Chapter 11: Orchestrating Multi-Step Workflows
- [x] Chapter 12: Your Automation Playbook
- [x] Chapter 13: Plugins & the Marketplace
- [x] Chapter 14: Subagents — Specialized Agents for Specialized Jobs
- [x] Chapter 15: Claude Code on the Web and Mobile

## Instructions for /generate-next-chapter
When the user invokes `/generate-next-chapter`:
1. Read this CLAUDE.md and find the first chapter marked with `[ ]` in Progress Tracking
2. Read the "Chapter Details" section below for that chapter's topics
3. Read `chapters/assets/style.css` for available CSS classes
4. Read `chapters/index.html` for navigation template
5. Read the previous chapter (if any) for context and smooth transition
6. Generate the HTML file in `chapters/` with full content (400-600 lines)
7. Update CLAUDE.md — mark the chapter as `[x]`
8. Update `chapters/index.html` — remove `pending` class from that chapter's card
9. Update navigation on the previous chapter if needed

## CSS Classes for Content
- `.automation-box` — automation idea, recipe, or insight (emerald accent, unique to this course)
- `.before-after-box` — manual vs automated comparison with `.before` and `.after` children (unique to this course)
- `.recipe-box` — step-by-step automation setup instructions (amber accent, unique to this course)
- `.prompt-example.good` — good examples (green accent)
- `.prompt-example.bad` — bad examples (red accent)
- `.comparison` — side-by-side comparisons
- `.tip-box` — tips and advice
- `.warning-box` — warnings and cautions
- `.exercise-box` — hands-on exercises (gold accent)
- `.checklist` — checklists with checkmarks
- `.highlight-box` — key messages (gradient background)
- `.stats-grid` + `.stat-card` — statistics display
- `.tool-card` — tool description cards (icon + name + description)
- `.workflow-steps` + `.step` + `.step-arrow` — visual workflow pipeline
- `.theme-toggle` — theme switch button (in nav)

## Content Guidelines
- **At least one `.automation-box`** per chapter with an automation idea or insight
- **At least one `.before-after-box`** per chapter showing manual vs automated workflow
- **At least one `.recipe-box`** per chapter with step-by-step setup instructions
- **At least one `.exercise-box`** per chapter where the reader builds something in Claude Code
- **All examples use Claude Code** — never reference other AI coding tools
- Keep code examples practical and copy-paste-ready (bash, JSON, markdown, YAML)
- Each chapter should end with a preview of how it connects to the next chapter

## Chapter Details

### Chapter 1: The Automated Developer
**File:** `01-automated-developer.html`
**Goal:** Inspire the reader to think "automate first" about every repetitive task in their dev workflow.

**Topics:**
- The 2026 developer landscape — AI tools are standard, but most devs still do repetitive tasks manually
- The "automate or repeat" mindset — if you do it twice, automate it the third time
- What Claude Code can automate beyond just writing code (reviews, tests, docs, CI/CD, communication)
- Automation ROI — time saved compounds (show a calculation: 5 min/day = 20 hours/year)
- Automation maturity levels: manual → scripted → AI-assisted → fully automated
- Identifying automation candidates in your daily workflow (the "automation audit")
- Common objections ("it takes longer to automate than to just do it") and why they're wrong at scale
- What this course will teach you — a preview of the automation stack we'll build
- The difference between "using AI to code" and "using AI to automate your workflow"

### Chapter 2: Your Automation Toolkit
**File:** `02-automation-toolkit.html`
**Goal:** Map out Claude Code's automation capabilities so the reader knows what building blocks are available.

**Topics:**
- Claude Code CLI overview — the commands and flags that matter for automation
- The skills system — `.claude/commands/` directory, how skills work, user vs project skills
- Hooks — `settings.json` hook configuration, hook types (PreToolUse, PostToolUse, Notification, etc.)
- CLAUDE.md as configuration — how CLAUDE.md files control Claude Code's behavior at project and user levels
- Shell scripting refresher — the bash basics you need for automation (variables, conditionals, pipes, jq)
- Combining Claude Code with shell scripts — piping, `claude -p` for non-interactive mode, exit codes
- GitHub Actions basics — workflow files, triggers, jobs, steps (foundation for Chapter 7)
- The automation stack diagram — how skills, hooks, CLAUDE.md, shell, and CI/CD fit together
- Choosing the right tool for the job — when to use a skill vs a hook vs a shell script vs CI/CD

### Chapter 3: Custom Claude Code Skills
**File:** `03-custom-skills.html`
**Goal:** Teach the reader to build reusable /commands that save hours of repetitive work.

**Topics:**
- Anatomy of a skill file — markdown in `.claude/commands/`, naming conventions, discoverability
- Writing your first skill — a `/generate-boilerplate` command that scaffolds Android components
- Parameterized prompts — using `$ARGUMENTS` for flexible, reusable skills
- Skill chaining — one skill calling another, building complex workflows from simple pieces
- Team-shared skill libraries — project-level `.claude/commands/` for team conventions
- Organizing skills by category — naming patterns, subdirectories, documentation
- Real examples gallery:
  - `/scaffold-feature` — generates ViewModel, Repository, UI, and tests for an Android feature
  - `/pr-description` — reads git diff and generates a structured PR description
  - `/explain-code` — produces onboarding-friendly explanations of complex code
  - `/refactor-to-compose` — converts XML layouts to Jetpack Compose
- Debugging skills — when your skill doesn't produce what you expect
- Skill versioning and evolution — updating skills as your workflow changes

### Chapter 4: Hooks That Work For You
**File:** `04-hooks.html`
**Goal:** Set up automated actions that trigger on Claude Code events without manual intervention.

**Topics:**
- What hooks are in Claude Code — event-driven automation via `settings.json`
- Hook types explained: PreToolUse, PostToolUse, Notification, Stop, SubagentStop
- Hook matchers — matching specific tools (Edit, Write, Bash) for targeted automation
- Creating a lint-on-save hook — auto-run ktlint/detekt when Claude edits Kotlin files
- Creating a format-on-save hook — auto-format with spotless after file edits
- Creating a test-on-change hook — run relevant tests when source files are modified
- Hook for commit message standards — enforce conventional commits format
- Combining hooks with shell scripts — complex logic triggered by simple events
- Hook debugging and logging — understanding when hooks fire and what they do
- Safety guardrails via hooks — preventing dangerous operations (force push, main branch commits)
- Hook ordering and performance — keeping hooks fast so they don't slow down your workflow

### Chapter 5: AI-Powered Code Review
**File:** `05-code-review.html`
**Goal:** Automate code review workflows so every PR gets consistent, thorough review.

**Topics:**
- The code review bottleneck — why reviews are slow and what AI can fix
- Using Claude Code for PR review — `claude -p "review this diff"` with structured output
- Building a `/review` skill — a comprehensive review command that checks style, logic, security, and performance
- Automated PR description generation — a skill that reads the diff and writes the PR body
- Security scanning prompts — teaching Claude Code to spot OWASP top 10 vulnerabilities
- Style consistency checks — encoding your team's style guide in CLAUDE.md rules
- Review checklists as skills — domain-specific review for Android (lifecycle, threading, memory leaks)
- Integrating review into GitHub Actions — automated review comments on every PR via Claude Code
- Team review standards in CLAUDE.md — encoding what "good code" means for your team
- Before/after: manual review vs AI-augmented review workflow

### Chapter 6: Automating Tests with AI
**File:** `06-automating-tests.html`
**Goal:** Use Claude Code to generate, maintain, and improve test suites with minimal manual effort.

**Topics:**
- The testing pain — why developers skip tests and how automation fixes it
- Generating unit tests with Claude Code — `claude -p "generate tests for this class"`
- Building a `/generate-tests` skill — a command that reads a source file and produces comprehensive tests
- Test generation for Android specifics — JUnit 5, Compose testing, Espresso, MockK patterns
- Coverage gap detection workflow — using Claude Code to find untested code paths
- Maintaining tests when code changes — a skill that updates tests alongside refactors
- Flaky test diagnosis — using Claude Code to analyze and fix intermittent test failures
- Mutation testing concepts — using AI to verify test quality (are your tests actually catching bugs?)
- Test quality validation — a review skill specifically for test code
- The testing automation pipeline — from code change to tested, reviewed, and merged

### Chapter 7: CI/CD Meets AI
**File:** `07-cicd-meets-ai.html`
**Goal:** Integrate Claude Code into CI/CD pipelines for automated changelogs, reviews, and deployment checks.

**Topics:**
- Why put AI in your pipeline — the case for Claude Code in CI/CD
- GitHub Actions + Claude Code — using `claude -p` in workflow steps
- Scheduled agents — Claude Code running on a cron schedule for maintenance tasks
- Remote triggers — invoking Claude Code agents from webhooks or other systems
- Automated changelog generation — a workflow that writes CHANGELOG.md from git history
- Release notes from commits — structured, human-readable release notes for every version
- Version bump automation — semantic versioning based on commit types
- Deployment pre-checks with AI — Claude Code verifying deployment readiness
- Build failure diagnosis — AI-powered analysis of CI failures with suggested fixes
- CI/CD recipes for Android — Gradle build caching, signing, Play Store upload verification
- PR merge automation — auto-merge when all checks pass and review is approved
- Cost and rate limit considerations — keeping CI/CD AI usage efficient

### Chapter 8: Documentation That Writes Itself
**File:** `08-documentation.html`
**Goal:** Automate documentation generation and keep docs perpetually in sync with code.

**Topics:**
- The documentation problem — why docs are always outdated and how automation fixes it
- Auto-generating README files — a `/generate-readme` skill that reads your project and writes the README
- API documentation from code — generating endpoint docs, request/response examples
- Architecture Decision Records (ADRs) — using Claude Code to draft ADRs from PR discussions
- Keeping docs in sync with code changes — a hook that flags when code changes make docs stale
- KDoc/Javadoc generation — a skill that adds documentation to undocumented public APIs
- Onboarding docs automation — generating "getting started" guides from project structure
- Diagram descriptions from code — creating PlantUML/Mermaid diagrams of architecture
- Documentation freshness checks — a scheduled agent that audits doc currency
- The documentation workflow — write code → auto-generate docs → review → merge

### Chapter 9: Personal Productivity Agents
**File:** `09-productivity-agents.html`
**Goal:** Build personal automations that save time on meta-work outside of direct coding.

**Topics:**
- Meta-work — the invisible time sink (standups, status updates, context switching)
- Code archaeology with AI — `git blame` + Claude Code for understanding legacy decisions
- Automated standup summaries — a skill that reads your git log and drafts a standup update
- Building a daily digest skill — what changed in the repo overnight, summarized for you
- PR status dashboards — using Claude Code to generate a summary of open PRs and their state
- Tech debt tracking — a skill that identifies and catalogues technical debt with severity ratings
- Personal knowledge base — using Claude Code to maintain notes on architecture decisions and patterns
- Time-saving shell aliases — combining bash aliases with `claude -p` for one-liner automations
- Notification triage — using AI to prioritize and summarize GitHub notifications
- The productivity stack — combining multiple automations into a morning routine

### Chapter 10: MCP Servers for Your Team
**File:** `10-mcp-servers.html`
**Goal:** Build and deploy MCP servers that extend Claude Code's capabilities to internal tools and data.

**Topics:**
- What MCP is and why it matters — the Model Context Protocol explained simply
- How MCP connects Claude Code to the world — tools, resources, prompts
- Anatomy of an MCP server — the request/response protocol, tool definitions, transport types
- Building your first MCP server — a simple TypeScript server that queries your team's API
- Connecting to internal tools — examples for Jira, Confluence, Slack, internal dashboards
- MCP server for database queries — give Claude Code read access to your staging database
- MCP server for deployment status — check deployment state without leaving Claude Code
- Team-shared MCP configurations — `.claude/settings.json` with shared server definitions
- Security considerations — authentication, access control, what data to expose
- Testing MCP servers — verifying your server works correctly before team rollout
- MCP server deployment — running servers locally vs hosting for the team

### Chapter 11: Orchestrating Multi-Step Workflows
**File:** `11-orchestrating-workflows.html`
**Goal:** Chain multiple automations into powerful end-to-end workflows that handle complex tasks.

**Topics:**
- From single automations to pipelines — the power of composition
- Composing skills into workflows — one skill that calls multiple others in sequence
- The feature-to-PR pipeline — from ticket to branch to code to tests to PR in one command
- Scheduled Claude Code agents — cron jobs + `claude -p` for maintenance automation
- Remote triggers — webhook-driven Claude Code execution for event-based automation
- Error recovery patterns — what to do when an automation step fails (retry, fallback, alert)
- Multi-repo automation — coordinating changes across related repositories
- Webhook integration — connecting external events (Slack messages, Jira transitions) to Claude Code
- Monitoring and alerting — knowing when your automations succeed or fail
- When NOT to automate — recognizing when automation adds complexity without value
- The orchestration maturity model — from scripts to agents to fully autonomous workflows

### Chapter 12: Your Automation Playbook
**File:** `12-automation-playbook.html`
**Goal:** Consolidate everything into a personal automation strategy and a plan for continuous improvement.

**Topics:**
- The automation audit — systematically reviewing your workflow for automation opportunities
- Prioritization framework — effort vs impact matrix for deciding what to automate next
- Building an automation library — organizing your skills, hooks, MCP servers, and scripts
- Maintenance strategies — keeping automations current as tools and codebases evolve
- Measuring ROI — tracking time saved, error reduction, and team velocity improvements
- Team adoption playbook — how to introduce automation to your team without resistance
- Automation anti-patterns — over-automation, brittle pipelines, "automate and forget"
- The automation backlog — maintaining a living list of automation opportunities
- Sharing automations — contributing skills and MCP servers to the community
- Staying current as Claude Code evolves — following updates, adapting automations
- Your 30-day automation challenge — a concrete plan for the reader's first month of automation

### Chapter 13: Plugins & the Marketplace
**File:** `13-plugins-and-marketplace.html`
**Goal:** Teach the reader to bundle their existing skills, hooks, MCP servers, and subagents into one installable plugin, and to discover and install plugins from official and team marketplaces.

**Topics:**
- Why plugins exist — the package-manager metaphor and the "share with your team" loop
- Anatomy of a plugin — `.claude-plugin/plugin.json` manifest, what auto-discovers from `commands/`, `skills/`, `agents/`, `hooks/`, `.mcp.json`
- Browsing and installing from the official `claude-plugins-official` marketplace
- The `/plugin` interactive UI and direct `/plugin install <name>@<marketplace>` form
- Install scopes — user vs project vs local and when to use each
- Adding your own marketplaces — `/plugin marketplace add` from owner/repo, git URL, local path, remote URL
- The `marketplace.json` catalog format
- Building your first plugin from existing skills/hooks (recipe walkthrough)
- Versioning and updates — semver discipline and the cache-bump-without-version-change footgun
- Team-shared marketplaces — the two-repo pattern (catalog repo separate from plugin source repos)
- Plugin namespacing (`plugin-name:skill-name`) — the only place colon syntax is real
- Security: vetting third-party plugins, no binary signing in 2026, the trust model
- Migration: from `.claude/commands/` + `scripts/` to a shareable plugin
- Examples gallery: claudemd-keeper, browser-control, repomix, awesome-claude-plugins

### Chapter 14: Subagents — Specialized Agents for Specialized Jobs
**File:** `14-subagents.html`
**Goal:** Teach the reader to delegate heavy work to specialized agents with their own context window, tool allowlist, and model — and stop drowning their main conversation in logs.

**Topics:**
- The context-window problem subagents solve (intermediate-output bloat)
- What a subagent is — markdown file in `.claude/agents/<name>.md` with YAML frontmatter
- Frontmatter reference — `name`, `description`, `tools`, `model` (required vs optional)
- How delegation works — auto-delegation by description, `@agent-name` mention (April 2026 typeahead), programmatic via Task tool
- Built-in subagents — Explore, Plan, general-purpose
- Writing your first subagent (code-reviewer recipe with `/agents` interactive helper)
- Subagent vs skill vs plugin — when to reach for each
- Cost optimization — Haiku/Sonnet/Opus right-sizing, `model: inherit`
- Parallel subagent invocation for independent investigations
- Subagents in CI via `anthropics/claude-code-action@v1`
- Project-level vs user-level subagents (project wins on name collision)
- Common mistakes — over-fragmentation, wrong tool allowlist, vague descriptions
- Android-flavored subagent gallery — lifecycle-checker, gradle-doctor, compose-reviewer, security-auditor

### Chapter 15: Claude Code on the Web and Mobile
**File:** `15-claude-code-anywhere.html`
**Goal:** Show the reader the three surfaces Claude Code now runs on (terminal, web, mobile), the primitives that move sessions between them, and how to design automations that run wherever the reader is.

**Topics:**
- The three surfaces — terminal, web (claude.ai/code), mobile app
- `--remote` (terminal → cloud), `--teleport` (cloud → terminal), `/remote-control` (local → phone) — three different jobs, easy to confuse
- Session persistence across surfaces — `--resume` (local history) vs `--teleport` (cloud session)
- The cloud VM environment — what's pre-installed, resource ceilings (4 vCPU / 16 GB RAM / 30 GB disk)
- What carries over from the repo (.claude/settings.json, .claude/agents, .mcp.json, plugins) vs what stays home (~/.claude/)
- The sandbox — Linux bubblewrap, macOS seatbelt, the four network access levels, 84% reduction in permission prompts
- Sandbox security realities — CVE-2026-39861 symlink escape, defense-in-depth framing
- When cloud, when local — compute, secrets, latency, parallelism trade-offs
- Setup scripts vs SessionStart hooks — when to use each, the $CLAUDE_CODE_REMOTE env var
- Routines — scheduled cloud sessions that don't depend on your laptop being awake
- Mobile use cases — monitoring sessions, approving auto-fix, kicking off long-running work
- Auto-fix PRs — Claude subscribes to GitHub events, makes clear fixes automatically; the comment-triggered automation caveat
- Cloud Claude Code vs the GitHub Action — when each fits
- What doesn't work in the cloud — interactive auth, custom base images, memory-heavy builds, user-only config, Bun
- Recipe: moving a weekly-maintenance agent from cron-on-laptop to scheduled cloud session
