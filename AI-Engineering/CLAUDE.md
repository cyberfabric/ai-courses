# AI-Ready Engineering For Dummies

## Project Description
An HTML guide in English for experienced developers who want to configure their projects for maximum AI productivity. This is NOT about learning architecture patterns — it's about teaching AI tools to work effectively with YOUR codebase through CLAUDE.md files, architecture rules, skills, hooks, MCP servers, and team onboarding.

The target audience is senior developers and tech leads who are already proficient with their tech stack but want to make their projects "AI-ready" — meaning AI tools consistently produce code that matches their team's architecture and conventions.

The style is **"For Dummies"** — friendly, approachable, like a senior colleague showing you how they've configured their entire project for AI success.

## Language Rules
- All content is in **English**
- Tone: practical, direct, like a colleague sharing hard-won configuration knowledge
- Use analogies from engineering and building to explain concepts
- Address: second person singular (you)
- Assume the reader already knows Clean Architecture, MVI, DI, and testing patterns
- Don't explain the underlying patterns — focus on how to encode them as AI configuration
- Reference other courses inline: "For more on [topic], see [Course Name] Chapter N"
- Short paragraphs — focus on actionable configuration

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
AI-Engineering/
  CLAUDE.md                              — This file
  .claude/
    commands/
      generate-next-chapter.md           — Skill for chapter generation
      create-memory-map.md               — Skill for visual chapter summary
  chapters/
    index.html                           — Landing page with navigation
    assets/
      style.css                          — Shared CSS (chocolate brown + cyan scheme)
    01-ai-ready-gap.html                 — Why Your Project Isn't AI-Ready Yet
    02-claude-md-mastery.html            — CLAUDE.md: Your Project's AI Brain
    03-context-engineering.html          — Context Engineering for Real Projects
    04-skills-at-scale.html              — Skills That Scale: Your Team's Command Library
    05-hooks-guardrails.html             — Hooks and Guardrails: Automated Quality Gates
    06-mcp-integration.html              — MCP Servers: Connecting AI to Your World
    07-architecture-rules.html           — Architecture Rules as AI Context
    08-team-onboarding.html              — Team Onboarding: From Solo to Squad
    09-thinking-and-planning.html        — Extended Thinking and Plan Mode
    10-cost-engineering.html             — Cost Engineering: Caching and Token Strategy
    11-project-audit.html                — The AI-Ready Audit: Your Project Scorecard
    12-playbook.html                     — Your AI-Ready Playbook
    maps/                                — Visual memory maps
```

## Progress Tracking
- [x] Chapter 1: Why Your Project Isn't AI-Ready Yet
- [x] Chapter 2: CLAUDE.md: Your Project's AI Brain
- [x] Chapter 3: Context Engineering for Real Projects
- [x] Chapter 4: Skills That Scale: Your Team's Command Library
- [x] Chapter 5: Hooks and Guardrails: Automated Quality Gates
- [x] Chapter 6: MCP Servers: Connecting AI to Your World
- [x] Chapter 7: Architecture Rules as AI Context
- [x] Chapter 8: Team Onboarding: From Solo to Squad
- [x] Chapter 9: Extended Thinking and Plan Mode
- [x] Chapter 10: Cost Engineering: Caching and Token Strategy
- [x] Chapter 11: The AI-Ready Audit: Your Project Scorecard
- [x] Chapter 12: Your AI-Ready Playbook

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
- `.config-block` — configuration file example with file-path header (brown accent, unique to this course)
- `.audit-box` — readiness assessment item with scoring (amber accent, unique to this course)
- `.before-after-config` — side-by-side without/with AI config (red/green split, with `.before-config` and `.after-config` children, unique to this course)
- `.team-tip` — team-specific advice for leads (teal accent, unique to this course)
- `.prompt-example.good` — good examples (green accent)
- `.prompt-example.bad` — bad examples (red accent)
- `.comparison` — side-by-side comparisons
- `.tip-box` — tips and advice
- `.warning-box` — warnings and cautions
- `.exercise-box` — hands-on exercises (cyan accent)
- `.checklist` — checklists with checkmarks
- `.highlight-box` — key messages (gradient background)
- `.stats-grid` + `.stat-card` — statistics display
- `.tool-card` — tool description cards (icon + name + description)
- `.workflow-steps` + `.step` + `.step-arrow` — visual workflow pipeline
- `.theme-toggle` — theme switch button (in nav)

## Content Guidelines
- **At least 1 `.config-block` per chapter** — with a real configuration example (CLAUDE.md snippet, settings.json, skill file)
- **At least 1 `.audit-box` per chapter** — with a readiness assessment
- **At least 1 `.exercise-box` per chapter** — producing a committable artifact
- All examples reference the recipes app architecture where appropriate
- Cross-references use: `<div class="tip-box"><strong>Deep Dive:</strong> For more on [topic], see <a href="../../OtherCourse/chapters/NN-slug.html">Course Name Ch N</a>.</div>`
- Never explain Clean Architecture, MVI, Room, Hilt, or Compose basics
- Focus on the AI configuration: what to write in CLAUDE.md, how to structure rules, when to create skills

## Chapter Details

### Chapter 1: Why Your Project Isn't AI-Ready Yet
**File:** `01-ai-ready-gap.html`
**Goal:** Audit what makes a project AI-ready vs AI-hostile and introduce the 5-pillar framework.
**Topics:**
- The AI-ready spectrum: from AI-hostile (no docs, no rules, no skills) to AI-native (full configuration)
- The 5 pillars of AI readiness: CLAUDE.md, context engineering, skills/hooks, architecture rules, team configuration
- Why "just use Claude Code" isn't enough — the cost of bad context (wrong patterns, wasted tokens, rework)
- The compounding effect: good configuration makes EVERY AI interaction better
- Auditing your current project: the quick readiness check (5 questions)
- The recipes app as case study: what makes it AI-ready (CLAUDE.md, architecture rules, skills, multi-module structure)
- The new developer test: if a new dev can't be productive in 30 minutes with your CLAUDE.md, it's not good enough
- What this course will build: by Chapter 12, your project scores 4/4 on every pillar
- Cross-reference: "This course complements AI-Rewrite (applying setup to a rewrite) and AI-Factory (building from zero)."

### Chapter 2: CLAUDE.md: Your Project's AI Brain
**File:** `02-claude-md-mastery.html`
**Goal:** Deep dive into production-grade CLAUDE.md files — far beyond the basics.
**Topics:**
- CLAUDE.md hierarchy: root → directory → user → enterprise. When to use each level.
- Writing rules that actually constrain AI: the difference between "use Clean Architecture" (too vague) and specific forbidden patterns
- Encoding architecture decisions: module boundaries, dependency rules, naming conventions
- Forbidden patterns: what AI must NEVER do (e.g., "NEVER add feature-to-feature dependencies")
- The "negative space" technique: telling AI what NOT to do is often more effective than what TO do
- Keeping CLAUDE.md in sync with evolving codebases: the monthly review checklist
- Real-world teardown: the recipes app CLAUDE.md line by line
- Template: the universal CLAUDE.md starter kit (copy-paste and customize)
- Cross-reference: "For CLAUDE.md basics, see Claude-Power Chapter 5. This chapter goes production-grade."

### Chapter 3: Context Engineering for Real Projects
**File:** `03-context-engineering.html`
**Goal:** Context engineering as a project setup discipline, not just prompting theory.
**Topics:**
- Context budget planning: how much context does your project need? (Token math for different project sizes)
- Documentation-as-context: README, ARCHITECTURE.md, API docs — writing docs that serve both humans AND AI
- Directory-level CLAUDE.md files: when to split configuration across directories
- The `.ctx` file pattern: condensed reference files (25 lines max) that fit in any context window
- Architecture documentation that AI can consume: structure over prose
- Avoiding context pollution: when more context hurts (conflicting rules, outdated docs, irrelevant files)
- The "context audit": listing everything AI reads and asking "does this help?"
- The recipes app context strategy: how 10 rules files × 2 formats = comprehensive coverage in minimal tokens
- Cross-reference: "AI-Harness Chapter 3 explains context windows. AI-Advanced Chapter 5 covers context theory. This chapter is about engineering your project's context layer."

### Chapter 4: Skills That Scale: Your Team's Command Library
**File:** `04-skills-at-scale.html`
**Goal:** Building a team-shared skill library with categories, versioning, and quality standards.
**Topics:**
- Skill library architecture: directory structure, naming conventions, categorization
- Parameterized skills: using `$ARGUMENTS` for flexible, reusable skills
- Skill composition: one skill calling others (the "macro skill" pattern)
- Quality standards for team skills: documentation, testing, review process
- Skill categories: scaffold, review, test, document, deploy, migrate
- Version control for skills: how to evolve skills without breaking existing workflows
- The `/generate-next-chapter` skill as a case study: anatomy of a well-designed skill
- Building your first 5 team skills: the starter library
- Cross-reference: "AI-Workflow Chapter 3 introduces skills. Claude-Power Chapter 6 covers basics. This chapter is about building a professional skill library."

### Chapter 5: Hooks and Guardrails: Automated Quality Gates
**File:** `05-hooks-guardrails.html`
**Goal:** Hooks as quality infrastructure — not just automation, but safety nets.
**Topics:**
- The hook matrix: must-have hooks vs nice-to-have (organized by risk level)
- PreToolUse hooks: safety gates that prevent destructive operations before they happen
- PostToolUse hooks: formatting, linting, test execution after AI edits
- SubagentStop hooks: oversight for long-running agent tasks
- Combining hooks with CI/CD: hooks as the local complement to pipeline checks
- Hook debugging: when hooks fail silently, how to diagnose
- Performance considerations: hooks that run on every edit vs hooks that run on commit
- The essential hook starter kit: 5 hooks every project should have
- Cross-reference: "AI-Workflow Chapter 4 introduces hooks. This chapter provides the production hook playbook."

### Chapter 6: MCP Servers: Connecting AI to Your World
**File:** `06-mcp-integration.html`
**Goal:** Configuring MCP servers for your project (not building them from scratch).
**Topics:**
- MCP ecosystem in 2026: the most useful public MCP servers and what they do
- Configuring MCP in settings.json: project-level vs user-level configuration
- Team-shared MCP configurations: ensuring everyone has the same tools
- Database access via MCP: read-only patterns for safe data exploration
- Internal tool integration: Jira, Confluence, Slack, GitHub via MCP
- MCP security boundaries: what to allow, what to restrict, permission models
- When NOT to use MCP: simple file reads don't need a server
- Setting up your first 3 MCP servers: the practical guide
- Cross-reference: "AI-Workflow Chapter 10 covers building MCP servers. Claude-Architect Chapter 6 covers MCP architecture. This chapter is about selecting and configuring MCP for your team."

### Chapter 7: Architecture Rules as AI Context
**File:** `07-architecture-rules.html`
**Goal:** The dual-format rules pattern — teaching AI your standards.
**Topics:**
- Why rules before code: preventing AI from introducing architectural violations
- The dual-format pattern: review checklists (verbose, for thorough review) + `.ctx` files (condensed, for development)
- The 10 topic areas: package structure, presentation, domain, data, error handling, network, testing, DI, Gradle, navigation
- Writing review checklists: MUST/SHOULD/PREFER severity levels, concrete rules, examples
- Condensing to `.ctx` files: the 25-line constraint, one-line summaries, rule IDs
- Loading rules into CLAUDE.md: when to reference vs when to inline
- Measuring rule compliance: how to check if AI follows your rules
- The actual recipes app rules as templates: walkthrough of `presentation-layer-ai-review-checklist.md` and `.claude/rules/presentation-layer.md`
- Evolving rules as architecture changes: the rule maintenance lifecycle
- Cross-reference: "AI-CodeReview Chapter 3 covers review checklists conceptually. This chapter shows how to encode them as AI configuration."

### Chapter 8: Team Onboarding: From Solo to Squad
**File:** `08-team-onboarding.html`
**Goal:** How to onboard a team to an AI-ready project.
**Topics:**
- The team onboarding playbook: day 1 (install + first task), week 1 (custom skills), month 1 (creating own skills)
- The 30-minute onboarding session: what to cover, what to skip
- Measuring adoption: not just usage but configuration quality (are they using skills? following rules?)
- Dealing with skeptics: showing value through specific time-saved examples
- Dealing with enthusiasts: preventing "AI-everything" chaos with guidelines
- Shared vs personal configuration: what's in the repo vs what's per-developer
- The configuration maturity model: Level 0 (no config) to Level 4 (AI-native project)
- Onboarding templates: the checklist every new team member follows
- Cross-reference: "Claude-Power Chapter 11 covers team patterns. This chapter is the operational onboarding guide."

### Chapter 9: Extended Thinking and Plan Mode
**File:** `09-thinking-and-planning.html`
**Goal:** Extended thinking and plan mode as project configuration tools.
**Topics:**
- Extended thinking: what it is, when it helps, when it wastes tokens
- Configuring extended thinking via CLAUDE.md: "Use extended thinking for architecture decisions"
- Plan mode as a workflow tool: when to use it, how it integrates with skills
- The "plan-execute-validate" pattern: structured approach for complex tasks
- Integrating plan mode into skills: skills that force planning before coding
- Budget thinking: extended thinking costs more — when the quality justifies the cost
- The recipes app example: plan mode for module extraction vs direct generation for test writing
- When NOT to use extended thinking: simple edits, formatting, boilerplate generation

### Chapter 10: Cost Engineering: Caching and Token Strategy
**File:** `10-cost-engineering.html`
**Goal:** The financial side of AI-ready engineering — managing costs at team scale.
**Topics:**
- Prompt caching mechanics: what gets cached, the 5-minute TTL, how CLAUDE.md content gets cached
- The context budget: how much context (input) vs how much generation (output) — finding the sweet spot
- Model selection by task type: Opus for architecture decisions, Sonnet for implementation, Haiku for formatting
- Model selection in CLAUDE.md: recommending models for different skill categories
- Cost monitoring and alerts: tracking spend per developer, per project, per skill
- Team spend management: budgets, approvals, usage dashboards
- ROI calculation: quantifying time saved vs tokens spent
- The CLAUDE.md cost optimization patterns: caching-friendly rule ordering, minimal but sufficient context
- Cost comparison: well-configured project vs poorly-configured project (3-5x difference)

### Chapter 11: The AI-Ready Audit: Your Project Scorecard
**File:** `11-project-audit.html`
**Goal:** A structured audit the reader runs on their own project.
**Topics:**
- The 5-pillar audit framework: CLAUDE.md, context, skills/hooks, architecture rules, team config
- Scoring rubric: 0 (absent) to 4 (excellent) per pillar, with specific criteria for each level
- Common gaps and quick fixes: the most frequent failures and how to address them
- The prioritized improvement plan: what to fix first based on highest impact
- One-week quick wins: 5 improvements you can make in a week that have outsized impact
- One-month deep improvements: 5 changes that require more effort but transform your workflow
- One-quarter transformation: the full journey from Level 0 to Level 4
- The audit template: ready to copy-paste into any project's issue tracker

### Chapter 12: Your AI-Ready Playbook
**File:** `12-playbook.html`
**Goal:** Consolidation chapter — the complete configuration checklist and maintenance plan.
**Topics:**
- The complete configuration checklist: everything from Chapters 1-11 in one actionable list
- Maintenance schedule: weekly (update rules), monthly (review CLAUDE.md), quarterly (audit skills)
- Staying current: how to evolve your AI readiness as Claude Code updates
- The AI-Ready Project Template: a starter kit with CLAUDE.md, skills, hooks, rules — ready to clone
- The 90-day AI readiness plan: week-by-week guide from zero to fully configured
- Connecting to AI-Rewrite: "Now that your project is AI-ready, use it to rewrite existing code"
- Connecting to AI-Factory: "Or use it to build from scratch with AI in every role"
- Your personal AI engineering manifesto: what you've learned and how you'll apply it
