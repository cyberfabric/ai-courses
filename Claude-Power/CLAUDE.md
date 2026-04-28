# Claude Power User For Dummies

## Project Description
An HTML guide in English for developers who already use Claude daily but want to master the full ecosystem. The target audience is experienced developers (especially mobile/Android) who use Claude Code, Claude.ai, and the Claude API but only scratch the surface of what's possible. They want to go from "I use Claude" to "I'm a Claude power user."

The style is **"For Dummies"** — friendly, approachable, heavy on practical examples and before/after comparisons. The reader is smart (they're a developer using Claude daily) but hasn't explored Projects, Artifacts, custom skills, hooks, memory systems, or advanced API features. Every chapter should produce at least one "I didn't know I could do that" moment.

## Language Rules
- All content is in **English**
- Tone: friendly, conversational, like a colleague showing you their favorite shortcuts
- Use concrete before/after examples to demonstrate improvements
- Address: second person singular (you)
- When introducing a feature, always show: "Here's what you're probably doing now" → "Here's the power user way"
- Light humor is welcome — keep it engaging, not dry
- Use short paragraphs — walls of text kill understanding
- **WebSearch is MANDATORY for every chapter** — Claude features evolve rapidly. Always verify current capabilities, flags, and UI before writing.

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

## Content Generation Rules
- All generated chapters MUST meet the 400-line minimum on the FIRST attempt. Count lines before finalizing. If under 400 lines, expand sections with examples, diagrams, tips, and detailed explanations before presenting.
- Never pad content incrementally — produce complete, full-length content in one pass.

## HTML Validation Rules
- Always close tip-box divs with `</div>`, never `</tip>`.
- Validate all HTML tags are properly closed before completing a chapter.

## Project Structure Rules
- Always check the current working directory and respect the explicit project path provided by the user. Do NOT search parent directories or sibling projects unless explicitly asked.

## Cross-Reference Rules
- When generating multi-file series, ensure all cross-reference links between chapters are consistent. Use relative paths and verify link targets exist before finishing.

## File Structure
```
Claude-Power/
  CLAUDE.md                              — This file
  .claude/
    commands/
      generate-next-chapter.md           — Skill for chapter generation
  chapters/
    index.html                           — Landing page with navigation
    assets/
      style.css                          — Shared CSS with dark/light theme
    01-claude-universe.html              — The Claude Universe
    02-claude-ai-power.html              — Claude.ai Power Features
    03-claude-code-mastery.html          — Claude Code CLI Mastery
    04-ide-integration.html              — IDE Integration Deep Dive
    05-claude-md-memory.html             — CLAUDE.md & Memory Systems
    06-skills-and-hooks.html             — Custom Skills & Hooks
    07-claude-api.html                   — The Claude API
    08-code-review.html                  — Claude for Code Review
    09-documentation.html                — Claude for Documentation
    10-debugging.html                    — Claude for Debugging
    11-team-patterns.html                — Team Collaboration Patterns
    12-playbook.html                     — Building Your Claude Playbook
    13-managed-agents.html               — Claude Managed Agents
    14-subagents.html                    — Subagents — Specialized Workers in .claude/agents/
    15-plugins-marketplace.html          — Plugins & the Marketplace Ecosystem
```

## Progress Tracking
- [x] Chapter 1: The Claude Universe
- [x] Chapter 2: Claude.ai Power Features
- [x] Chapter 3: Claude Code CLI Mastery
- [x] Chapter 4: IDE Integration Deep Dive
- [x] Chapter 5: CLAUDE.md & Memory Systems
- [x] Chapter 6: Custom Skills & Hooks
- [x] Chapter 7: The Claude API
- [x] Chapter 8: Claude for Code Review
- [x] Chapter 9: Claude for Documentation
- [x] Chapter 10: Claude for Debugging
- [x] Chapter 11: Team Collaboration Patterns
- [x] Chapter 12: Building Your Claude Playbook
- [x] Chapter 13: Claude Managed Agents
- [x] Chapter 14: Subagents — Specialized Workers in .claude/agents/
- [x] Chapter 15: Plugins & the Marketplace Ecosystem

## Instructions for /generate-next-chapter
When the user invokes `/generate-next-chapter`:
1. Read this CLAUDE.md and find the first chapter marked with `[ ]` in Progress Tracking
2. Read the "Chapter Details" section below for that chapter's topics
3. Read `chapters/assets/style.css` for available CSS classes
4. Read `chapters/index.html` for navigation template
5. Read the previous chapter (if any) for context and smooth transition
6. **WebSearch** for the latest Claude features, updates, and documentation relevant to the chapter topic
7. Generate the HTML file in `chapters/` with full content (400-600 lines)
8. Update CLAUDE.md — mark the chapter as `[x]`
9. Update `chapters/index.html` — remove `pending` class from that chapter's card
10. Update navigation on the previous chapter if needed

## CSS Classes for Content
- `.power-tip` — power user technique or advanced trick (violet accent, unique to this course)
- `.shortcut-box` — keyboard shortcuts and quick actions (cyan accent, unique to this course)
- `.before-after` — side-by-side before/after comparison (red/green split, unique to this course)
  - Contains `.before` and `.after` children
- `.claude-example` — real Claude interaction example (warm gradient, unique to this course)
  - Contains `.user-msg` and `.claude-msg` children for conversation flow
- `.prompt-example.good` — good examples (green accent)
- `.prompt-example.bad` — bad examples (red accent)
- `.comparison` — side-by-side comparisons
- `.tip-box` — tips and advice
- `.warning-box` — warnings and cautions
- `.exercise-box` — hands-on exercises (gold accent, labeled "Try It Yourself")
- `.checklist` — checklists with checkmarks
- `.highlight-box` — key messages (gradient background)
- `.stats-grid` + `.stat-card` — statistics display
- `.tool-card` — tool description cards (icon + name + description)
- `.workflow-steps` + `.step` + `.step-arrow` — visual workflow pipeline
- `.theme-toggle` — theme switch button (in nav)

## Content Guidelines
- **At least one `.power-tip` per chapter** — show an advanced technique most people miss
- **At least one `.claude-example` per chapter** — show a real interaction with Claude
- **At least one `.shortcut-box` per chapter** — show a quick action or keyboard shortcut
- **At least one `.exercise-box` per chapter** — give the reader something to try right now
- **At least one `.before-after` per chapter** — show the improvement from basic to power user approach
- Every technique should be immediately actionable — the reader should be able to try it right after reading
- Connect features to real developer workflows, not abstract capabilities
- Each chapter should end with a brief preview of how this connects to the next chapter

## Chapter Details

### Chapter 1: The Claude Universe
**File:** `01-claude-universe.html`
**Goal:** Give the reader a complete mental map of every Claude product and when to use each one.
**Topics:**
- The Claude ecosystem at a glance: Claude.ai (web/mobile), Claude Code (CLI), Claude Code (IDE extensions), Claude API, Claude Agent SDK
- Claude.ai: the conversational interface — when to use it (brainstorming, writing, analysis, research)
- Claude Code CLI: the developer's power tool — when to use it (coding, file operations, git workflows, automation)
- Claude Code in VS Code and JetBrains: embedded AI — when to use it (inline editing, quick questions without leaving the editor)
- Claude API: building Claude into your apps — when to use it (custom integrations, automated pipelines, product features)
- Claude Agent SDK: building autonomous agents — when to use it (multi-step tasks, complex workflows)
- The model family: Opus, Sonnet, Haiku — what each is best at and their cost/speed tradeoffs
- How they all connect: same models, different interfaces, different superpowers
- Decision framework: "I want to ___" → use this product
- Common mistakes: using Claude.ai for coding tasks (use Claude Code), using the API for one-off questions (use Claude.ai)
- Exercise: Map your current Claude usage — which product are you using for each task? Are you using the right one?

### Chapter 2: Claude.ai Power Features
**File:** `02-claude-ai-power.html`
**Goal:** Unlock the features in Claude.ai that most users never discover.
**Topics:**
- Projects: organizing conversations with persistent context (project instructions, uploaded files, knowledge bases)
- How to write great project instructions — the difference between vague and powerful
- Artifacts: interactive outputs that live outside the chat (code, documents, diagrams, apps)
- Creating and iterating on Artifacts — building mini-apps in conversation
- Custom instructions (profile-level): teaching Claude your preferences once so you never repeat them
- Styles: controlling Claude's tone, format, and behavior with presets
- Starred conversations and conversation management
- File uploads: what works, what doesn't, size limits, best formats
- Search: finding past conversations and using web search
- Keyboard shortcuts in Claude.ai that save time
- Mobile app features and differences from the web experience
- Claude.ai vs ChatGPT vs Gemini: where Claude.ai genuinely excels
- Exercise: Create a Project with custom instructions for your most common task

### Chapter 3: Claude Code CLI Mastery
**File:** `03-claude-code-mastery.html`
**Goal:** Transform the reader from a basic Claude Code user to a CLI power user.
**Topics:**
- Installation and setup: getting the latest version, authentication methods
- The basics most people know: asking questions, editing files, running commands
- Slash commands: `/help`, `/clear`, `/compact`, `/review`, `/commit`, `/cost`, and more
- Flags that change everything: `--print`, `--output-format`, `--model`, `--allowedTools`, `--permission-mode`
- Headless mode: using Claude Code in scripts and CI/CD (`--print` flag, piping input)
- Plan mode vs direct execution: when to plan first
- Permission modes: default, auto-accept, and custom permissions
- The `!` prefix: running shell commands without leaving Claude Code
- Context management: how Claude Code reads your project, CLAUDE.md files, and what goes into context
- Multi-turn conversations: when to continue vs when to start fresh
- Cost awareness: tracking token usage with `/cost`, strategies for reducing spend
- Model selection: when to use Opus vs Sonnet vs Haiku within Claude Code
- The `.claude/` directory: settings, commands, memory — what lives where
- Exercise: Run Claude Code with `--print` to automate a task you do manually today

### Chapter 4: IDE Integration Deep Dive
**File:** `04-ide-integration.html`
**Goal:** Make Claude Code in VS Code and JetBrains as natural as using the terminal.
**Topics:**
- VS Code extension: installation, setup, and first use
- The Claude Code panel: opening, positioning, and keyboard shortcuts
- Inline editing: selecting code and asking Claude to modify it
- Context from your editor: how the extension sends file context, selections, and diagnostics
- Terminal integration: running Claude Code commands from the VS Code terminal vs the panel
- JetBrains extension: installation, setup, and differences from VS Code
- Keybindings: default shortcuts and how to customize them
- Working with multiple files: how to reference and navigate between files
- Integration with VS Code features: problems panel, source control, terminal
- Tips for large projects: managing context, focusing Claude on specific directories
- Common pitfalls: extension conflicts, performance issues, authentication problems
- Comparison: CLI vs VS Code panel vs JetBrains — when each shines
- Exercise: Set up your IDE extension and complete a real task using only the panel (no terminal)

### Chapter 5: CLAUDE.md & Memory Systems
**File:** `05-claude-md-memory.html`
**Goal:** Teach the reader to configure Claude's persistent knowledge — the most underused power feature.
**Topics:**
- What CLAUDE.md is: project-level instructions that load automatically into every conversation
- The CLAUDE.md hierarchy: project root, subdirectories, user-level, enterprise-level — how they merge
- Writing effective CLAUDE.md files: what to include, what to skip, real examples
- Common patterns: coding standards, project context, tool preferences, forbidden patterns
- The `.claude/` directory deep dive: `settings.json`, `settings.local.json`, memory files
- Memory system: how Claude Code stores and retrieves memories across conversations
- User-level instructions: `~/.claude/CLAUDE.md` for preferences that apply to ALL projects
- Settings hierarchy: user settings vs project settings vs local settings — what overrides what
- Anti-patterns: CLAUDE.md files that are too long, too vague, or contradictory
- Updating and maintaining CLAUDE.md as your project evolves
- Version controlling CLAUDE.md: what to commit vs what to keep local
- The connection to context windows: how CLAUDE.md content affects your available context budget
- Exercise: Write a CLAUDE.md for your current project — include coding standards, project structure, and key conventions

### Chapter 6: Custom Skills & Hooks
**File:** `06-skills-and-hooks.html`
**Goal:** Show the reader how to extend Claude Code with reusable commands and automated triggers.
**Topics:**
- What skills (slash commands) are: reusable prompt templates you invoke with `/command-name`
- Creating your first skill: the `.claude/commands/` directory and markdown format
- Skill anatomy: the markdown file structure, variables, and prompt engineering for skills
- Practical skill examples: `/generate-tests`, `/review-pr`, `/refactor`, `/explain`
- Project skills vs user skills: `.claude/commands/` vs `~/.claude/commands/`
- What hooks are: shell commands that run automatically before/after Claude Code actions
- Hook triggers: `PreToolUse`, `PostToolUse`, `Notification`, and others
- Practical hook examples: auto-format on save, lint checks before commit, notification on completion
- Configuring hooks in `settings.json`: the hooks configuration format
- Combining skills and hooks: building powerful automated workflows
- Debugging skills and hooks: common issues and how to fix them
- Sharing skills with your team: version control and distribution strategies
- Exercise: Create a custom `/daily-standup` skill that generates a summary of your recent git activity

### Chapter 7: The Claude API
**File:** `07-claude-api.html`
**Goal:** Give the reader the confidence and knowledge to use the Claude API directly.
**Topics:**
- Why use the API when you have Claude Code? Use cases for direct API access
- Getting started: API keys, the Anthropic SDK (Python and TypeScript), first API call
- The Messages API: structure of a request (system prompt, messages, model, max_tokens)
- Streaming responses: real-time output for better UX
- Tool use (function calling): defining tools, handling tool calls, the tool use loop
- Extended thinking: enabling Claude to reason step-by-step before responding
- Vision: sending images to Claude for analysis
- System prompts: crafting effective system prompts for API usage
- Token counting and cost management: understanding input/output tokens, caching
- Prompt caching: reducing costs for repeated context with cache_control
- Error handling: rate limits, retries, and graceful degradation
- The Claude Agent SDK: building multi-step agents that use tools autonomously
- Exercise: Build a simple script that uses the Claude API to analyze a file and suggest improvements

### Chapter 8: Claude for Code Review
**File:** `08-code-review.html`
**Goal:** Build a systematic Claude-powered code review workflow.
**Topics:**
- Why AI code review matters: catching bugs, enforcing standards, learning from feedback
- Quick review: using `/review` in Claude Code for instant feedback
- Reviewing a PR: feeding diff context to Claude for thorough analysis
- What to ask Claude to look for: bugs, security issues, performance, readability, edge cases
- Prompt templates for different review types: security review, performance review, architecture review
- Building a review skill: creating a custom `/review-pr` command tailored to your project
- Automated review with hooks: triggering reviews on git operations
- Reviewing your own code before pushing: the "fresh eyes" technique
- Handling Claude's false positives: when AI review feedback is wrong
- Code review checklists: combining human and AI review for maximum coverage
- Integrating Claude review into CI/CD pipelines using `--print` mode
- Team review workflows: shared review skills and standards
- Exercise: Review your last 3 commits with Claude — compare what Claude finds vs what you'd catch manually

### Chapter 9: Claude for Documentation
**File:** `09-documentation.html`
**Goal:** Use Claude to generate and maintain documentation that developers actually read.
**Topics:**
- The documentation problem: why docs are always outdated and how AI changes that
- Generating READMEs: feeding project context and getting a comprehensive README
- API documentation: using Claude to document endpoints, parameters, and examples
- Architecture Decision Records (ADRs): using Claude to document why decisions were made
- Changelog generation: creating human-readable changelogs from git history
- Code comments: when and how to use Claude for inline documentation
- Onboarding guides: generating "how to get started" docs for new team members
- Keeping docs in sync: using skills and hooks to update docs when code changes
- Documentation style: teaching Claude your documentation conventions via CLAUDE.md
- Generating diagrams: using Artifacts in Claude.ai or Mermaid syntax in code
- The anti-patterns: over-documented code, stale docs, AI-generated boilerplate
- Building a documentation skill: a custom `/generate-docs` command
- Exercise: Generate a README for a project that currently has none (or update one that's outdated)

### Chapter 10: Claude for Debugging
**File:** `10-debugging.html`
**Goal:** Build a systematic debugging workflow powered by Claude.
**Topics:**
- The debugging mindset: how to present problems to Claude for maximum help
- Stack traces and error messages: copy-paste debugging done right
- The "explain this error" pattern: getting Claude to decode cryptic errors
- Rubber duck debugging with Claude: talking through problems to find solutions
- Log analysis: feeding log files to Claude for pattern detection
- Reproducing bugs: using Claude to generate minimal reproduction cases
- The bisect approach: using Claude with git bisect to find breaking commits
- Debugging across languages: how Claude handles Python, TypeScript, Kotlin, Swift differently
- Performance debugging: profiling output analysis with Claude
- Debugging prompts that work: templates for common debugging scenarios
- When Claude gets it wrong: recognizing AI debugging hallucinations
- Building a debugging skill: a custom `/debug` command with structured problem input
- Exercise: Take a real bug you're currently stuck on and walk through the debugging workflow with Claude

### Chapter 11: Team Collaboration Patterns
**File:** `11-team-patterns.html`
**Goal:** Scale Claude usage from individual productivity to team-wide leverage.
**Topics:**
- The team adoption challenge: different skill levels, different tools, different preferences
- Shared CLAUDE.md files: establishing team-wide conventions and standards
- Shared skills library: building a team collection of reusable slash commands
- Onboarding new team members to Claude: what to teach first, common mistakes
- Knowledge sharing: documenting "what worked" and "what didn't" with Claude
- Code review standards: aligning AI-assisted review across the team
- Cost management across teams: monitoring usage, setting budgets, optimizing spend
- Security considerations: API keys, sensitive data, what not to share with Claude
- Team workflows: PR creation, branch management, release processes with Claude
- Training sessions: running "Claude power user" workshops for your team
- Measuring impact: how to tell if Claude is actually making your team more productive
- Building a team Claude playbook: a living document of best practices
- Exercise: Draft a "Getting Started with Claude" guide for a new team member joining your project

### Chapter 12: Building Your Claude Playbook
**File:** `12-playbook.html`
**Goal:** Help the reader create their personal Claude system — a daily workflow that compounds over time.
**Topics:**
- The playbook concept: a personal system, not just a collection of tips
- Auditing your current workflow: where do you spend time that Claude could save?
- Morning routine: starting the day with Claude (standup prep, task planning, context loading)
- The development loop: code → review → test → debug → document — Claude at every step
- Building your skill library: the 5-10 custom commands that cover 80% of your work
- CLAUDE.md maintenance: keeping your project instructions fresh and effective
- Context management strategies: when to start fresh, when to continue, how to compact
- Cost optimization: getting maximum value per dollar spent on Claude
- Staying current: following Claude updates, new features, model improvements
- The compound effect: how small optimizations add up to massive productivity gains
- Common pitfalls: over-reliance, context fatigue, prompt laziness, not verifying output
- Your 30-day challenge: a day-by-day plan to level up your Claude usage
- Exercise: Create your personal Claude playbook document — your go-to reference for how YOU use Claude

### Chapter 13: Claude Managed Agents
**File:** `13-managed-agents.html`
**Goal:** Show the reader how Managed Agents let you offload long-running tasks to cloud-hosted Claude instances — the "set it and forget it" power move.
**Topics:**
- What are Managed Agents? Anthropic's pre-built agent harness running in managed infrastructure — no servers to manage
- The four core concepts: Agent (model + system prompt + tools), Environment (container template), Session (running instance), Events (SSE streaming)
- When to use Managed Agents vs Claude Code vs the raw API: the decision framework
- Creating your first agent: configuring model, system prompt, tools, and MCP servers via the API
- Environments: container templates with packages, network access, and mounted files — your agent's workspace
- Sessions: starting a task, streaming events, checking status — the lifecycle of work
- Built-in tools: Bash, file operations, web search, web fetch, MCP servers — what's available out of the box
- The Events API: SSE streaming, message types, handling events in your application
- Practical use cases for power users: automated code review, scheduled report generation, data processing pipelines, research tasks
- Before/after: running a 30-minute analysis task manually vs offloading it to a Managed Agent
- Research previews: Multi-agent orchestration, Memory across sessions, Outcomes tracking
- Cost and billing: understanding how Managed Agent sessions are billed
- Exercise: Create a Managed Agent that analyzes a GitHub repository and produces a code quality report

### Chapter 14: Subagents — Specialized Workers in .claude/agents/
**File:** `14-subagents.html`
**Goal:** Teach the reader the third Claude Code extension primitive — subagents — and how to use built-in (Explore / Plan / general-purpose) and custom subagents to keep main context clean, run work in parallel, and scope permissions per worker.
**Topics:**
- Mental model: skills run procedures, hooks run on events, subagents run in their own context window
- Skills vs hooks vs subagents at-a-glance comparison
- Built-in subagents: Explore (Haiku, read-only, thoroughness levels), Plan (read-only, used in plan mode), General-purpose (full tools)
- Decision framework: when to delegate vs stay in the main loop
- Defining a custom subagent: location (`.claude/agents/`), full frontmatter table (name, description, tools, disallowedTools, model, permissionMode, maxTurns, skills, mcpServers, hooks, memory, background, effort, isolation, color, initialPrompt)
- Permission modes explained (default / acceptEdits / auto / dontAsk / bypassPermissions / plan) and inheritance rules
- Persistent memory: user / project / local scopes and the MEMORY.md file
- The `--agent` flag for whole-session role-playing, plus `"agent"` setting to pin a project default
- Scope priority: managed → `--agents` flag → project → user → plugin
- Four invocation patterns: natural language, `@-mention`, `/agents` UI, `--agent` flag
- Parallel execution (the code-review fan-out: style + security + tests in parallel)
- Foreground vs background subagents and the pre-approval flow
- Common pitfalls: over-delegating, lost context, model mismatch, no nested spawning
- Forks (experimental, `CLAUDE_CODE_FORK_SUBAGENT=1`, `/fork`): subagents that inherit full conversation history
- Agent Teams (experimental, `CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS=1`): cross-session coordination, `SendMessage` resume
- Practical patterns: code-review fan-out, research-then-implement, multi-language reviewer pool, isolated-worktree edits
- Exercise: Build a `code-review-fanout` workflow with three parallel subagents and a slash command that consolidates findings

### Chapter 15: Plugins & the Marketplace Ecosystem
**File:** `15-plugins-marketplace.html`
**Goal:** Teach the reader the packaging-and-distribution layer of Claude Code — how plugins bundle skills, hooks, subagents, MCP servers, LSP servers, monitors, and commands into one installable unit, and how the official, community, and private marketplaces work.
**Topics:**
- What a plugin is: a bundle of skills + hooks + subagents + MCP servers + slash commands + LSP + monitors + bin/
- Standalone (`.claude/`) vs Plugin trade-offs and when to graduate
- Plugin manifest at `.claude-plugin/plugin.json` (name, description, version, author)
- The directory layout warning: only `plugin.json` goes inside `.claude-plugin/`
- The official Anthropic marketplace (`claude-plugins-official`) — auto-available, browseable at claude.com/plugins
- Community marketplaces (buildwithclaude.com, claudemarketplaces.com, awesome lists) and how to add them
- Private enterprise marketplaces (Cowork, Feb 24 2026): Customize admin menu, per-user provisioning, auto-install, restricted visibility
- The 12 new MCP connectors (Google Calendar, Drive, Gmail, DocuSign, Apollo, Clay, Outreach, Similarweb, MSCI, LegalZoom, FactSet, WordPress, Harvey)
- `/plugin` UI tabs (Discover / Installed / Marketplaces / Errors), `/plugin install`, `/plugin marketplace add/list/refresh/remove`
- Skill namespacing in plugins (`/plugin-name:skill-name`)
- The `--plugin-dir` flag and `/reload-plugins` for hot-reload development
- Background monitors as a plugin component (`monitors/monitors.json`)
- Default `settings.json` in plugins (only `agent` and `subagentStatusLine` keys supported)
- Converting standalone configs to a plugin (mechanical migration)
- Publishing strategy: git-based marketplace, version pinning vs git-SHA versioning
- Submitting to the official marketplace via claude.ai or platform.claude.com submission forms
- Decision framework: plugins vs skills vs hooks vs subagents
- Security considerations: untrusted plugins, plugin subagent restrictions (no hooks/mcpServers/permissionMode), version pinning, audit trail
- Practical use cases: language packs, on-call plugins, security-review packs, design-system packs
- Debugging plugin issues: directory layout, Errors tab, isolating failing components
- Exercise: Bundle your favorite skill + hook + subagent into a plugin and publish it to a private repo for your team
