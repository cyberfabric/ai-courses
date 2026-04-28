# AI-Driven Development: A Practical Guide for Software Engineers

## Project Description
An HTML guide in English for experienced software engineers who want to master AI-driven development. The target audience is developers (especially Android/mobile) who already know how to code but want to understand how to build real projects in an AI-first world — tools, mindset, workflows, and professional practices.

The style is practical and direct — "senior dev talking to senior dev." No hand-holding on programming basics, but thorough explanation of AI-specific concepts. Complexity increases progressively from chapter to chapter.

## Language Rules
- All content is in **English**
- Technical terms used naturally (audience is developers) — no need for parenthetical explanations of common terms like API, IDE, CI/CD
- Newer AI-specific terms (context engineering, agentic coding, vibe coding) should be defined clearly on first use
- Tone: practical, direct, occasionally opinionated. Like a well-written engineering blog post.
- Address: second person singular (you)
- Examples must be from **different engineering roles** — minimum 3 roles per chapter

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
AI-Advanced/
  CLAUDE.md                              — This file
  .claude/
    commands/
      generate-next-chapter.md           — Skill for chapter generation
  chapters/
    index.html                           — Landing page with navigation
    assets/
      style.css                          — Shared CSS with dark/light theme
    01-the-new-paradigm.html             — The New Paradigm
    02-ai-coding-landscape.html          — The AI Coding Landscape
    03-mindset-shift.html                — The Mindset Shift
    04-setting-up-environment.html       — Setting Up Your AI Dev Environment
    05-context-engineering.html          — Context Engineering
    06-prompt-engineering-for-code.html  — Prompt Engineering for Code
    07-spec-driven-development.html      — Spec-Driven Development
    08-tdd-with-ai.html                  — Test-Driven Development with AI
    09-agentic-coding-workflows.html     — Agentic Coding Workflows
    10-vibe-vs-structured.html           — Vibe Coding vs Structured Development
    11-code-review-quality.html          — Code Review and Quality
    12-large-codebases.html              — Working with Large Codebases
    13-building-full-projects.html       — Building Full Projects
    14-android-ai-development.html       — Android-Specific AI Development
    15-privacy-security-ethics.html      — Privacy, Security, and Ethics
    16-future-continuous-learning.html   — The Future and Continuous Learning
  resources/
    anthropic-resources.txt              — Curated Anthropic links & summaries
    openai-resources.txt                 — Curated OpenAI links & summaries
    community-resources.txt              — Third-party guides, tools, tutorials
```

## Progress Tracking
- [x] Chapter 1: The New Paradigm
- [x] Chapter 2: The AI Coding Landscape
- [x] Chapter 3: The Mindset Shift
- [x] Chapter 4: Setting Up Your AI Dev Environment
- [x] Chapter 5: Context Engineering
- [x] Chapter 6: Prompt Engineering for Code
- [x] Chapter 7: Spec-Driven Development
- [x] Chapter 8: Test-Driven Development with AI
- [x] Chapter 9: Agentic Coding Workflows
- [x] Chapter 10: Vibe Coding vs Structured Development
- [x] Chapter 11: Code Review and Quality
- [x] Chapter 12: Working with Large Codebases
- [x] Chapter 13: Building Full Projects
- [x] Chapter 14: Android-Specific AI Development
- [x] Chapter 15: Privacy, Security, and Ethics
- [x] Chapter 16: The Future and Continuous Learning
- [x] Chapter 17: Claude Skills, Subagents, Plugins & MCP — Extending Claude Code

## Instructions for /generate-next-chapter
When the user invokes `/generate-next-chapter`:
1. Read this CLAUDE.md and find the first chapter marked with `[ ]` in Progress Tracking
2. Read the "Chapter Details" section below for that chapter's topics
3. Read `chapters/assets/style.css` for available CSS classes
4. Read `chapters/index.html` for navigation template
5. Read the previous chapter (if any) for context and smooth transition
6. Read relevant resource files from `resources/` for reference links to include
7. Generate the HTML file in `chapters/` with full content (400-600 lines)
8. Update CLAUDE.md — mark the chapter as `[x]`
9. Update `chapters/index.html` — remove `pending` class from that chapter's card
10. Update navigation on the previous chapter if needed

## CSS Classes for Content
- `.prompt-example.good` — good examples (green accent)
- `.prompt-example.bad` — bad examples (red accent)
- `.comparison` — side-by-side comparisons
- `.tip-box` — tips and advice
- `.warning-box` — warnings and cautions
- `.exercise-box` — hands-on exercises (gold accent)
- `.checklist` — checklists with checkmarks
- `.highlight-box` — key messages (gradient background)
- `.stats-grid` + `.stat-card` — statistics display
- `.profession-tag` — role label for examples (e.g., "Android Dev", "Backend")
- `.tool-card` — tool description cards (icon + name + description)
- `.workflow-steps` + `.step` + `.step-arrow` — visual workflow pipeline
- `.theme-toggle` — theme switch button (in nav)

## Target Engineering Roles for Examples
When writing examples, use scenarios from these roles:
- **Android Developer**: Compose UI, Room DB, Retrofit, Gradle, Kotlin, ViewModel, Navigation
- **Backend Engineer**: REST APIs, databases, microservices, Python/Node.js, Docker
- **Full-Stack Developer**: React/Vue frontend + backend, deployment, end-to-end features
- **DevOps Engineer**: CI/CD pipelines, infrastructure as code, monitoring, Kubernetes
- **Team Lead**: Code review, architecture decisions, sprint planning, mentoring
- **Freelancer**: Client projects, rapid prototyping, multiple tech stacks, time management

## Research Resources
Reference material is stored in `resources/`:
- `anthropic-resources.txt` — Anthropic official docs, engineering blog, research papers
- `openai-resources.txt` — OpenAI articles and tools
- `community-resources.txt` — Industry guides, tool comparisons, tutorials, academic papers

When writing chapters, reference specific articles from these files where relevant. Include links to external resources in tip boxes or as further reading suggestions.

## Chapter Details

### Chapter 1: The New Paradigm
**File:** `01-the-new-paradigm.html`
**Goal:** Set the stage — what changed in software engineering between 2024 and 2026.
**Topics:**
- The before/after: how developers worked in 2023 vs how they work in 2026
- Key inflection points: Claude 3.5 Sonnet, GPT-4o, agentic coding tools, 1M token contexts
- The productivity multiplier: real data (DORA report, Anthropic research — 50% boost, 2-3x YoY)
- "Writing code" vs "engineering software" — the abstraction shift
- What stayed the same: architecture thinking, debugging intuition, domain expertise
- The adoption curve: 85% of devs use AI tools, startups adopt 2.5x faster than enterprises
- The new developer career ladder: AI-augmented roles
- Exercise: Audit your current workflow — identify 5 tasks AI could handle

### Chapter 2: The AI Coding Landscape
**File:** `02-ai-coding-landscape.html`
**Goal:** Map the entire tool ecosystem so the reader knows what exists.
**Topics:**
- Category 1: CLI agents — Claude Code, Aider, OpenHands
- Category 2: IDE-integrated — Cursor, Windsurf, GitHub Copilot, Android Studio Gemini
- Category 3: Chat-based — ChatGPT, Claude.ai, Gemini
- Category 4: Specialized — v0 (UI generation), Bolt, Lovable (full-stack prototyping)
- Comparison table: pricing, context window, key strengths, weaknesses
- Decision matrix: which tool for which task type
- The "multi-tool" developer: combining tools for maximum effect
- Automation rates: 79% with agents vs 49% with chatbots (Anthropic research)
- Exercise: Install three different tools, run the same task, compare outputs

### Chapter 3: The Mindset Shift
**File:** `03-mindset-shift.html`
**Goal:** Rewire thinking from "I write code" to "I direct an AI that writes code."
**Topics:**
- From typist to architect: your new role
- The "lazy developer" fallacy — AI-driven dev requires MORE thinking, not less
- Reading code vs writing code: the ratio flip
- Taste and judgment: the human skills that matter more now
- "Don't touch the keyboard yet" — the planning-first instinct
- Anti-patterns: prompt-and-pray, over-trusting, under-reviewing, full delegation
- The 80/20 rule: AI handles 80% of implementation, you handle 20% of architecture
- Skill atrophy risk: Anthropic research shows 17% comprehension drop with full delegation
- Strategic AI use: asking questions and seeking explanations retains more knowledge
- Exercise: Take a recent feature you built, rewrite the process as if directing an AI

### Chapter 4: Setting Up Your AI Dev Environment
**File:** `04-setting-up-environment.html`
**Goal:** Get the reader fully set up with AI coding tools.
**Topics:**
- Installing Claude Code: API key, CLI setup, first run, desktop app, web version
- Configuring Cursor: model selection, rules, .cursorrules file
- GitHub Copilot in VS Code/Android Studio: setup and configuration
- Android Studio Gemini integration: enabling Agent Mode
- Terminal setup: shell integration, aliases, PATH configuration
- The ideal multi-tool setup: when to use which tool
- Project-level configuration: .claude/, .cursor/, .github/copilot
- CLAUDE.md init: `claude /init` to bootstrap project instructions
- Exercise: Set up Claude Code on an existing project, run your first command

### Chapter 5: Context Engineering
**File:** `05-context-engineering.html`
**Goal:** Teach the single most important skill in AI-driven development.
**Topics:**
- Why context is king: the context window explained for developers (tokens, limits, costs)
- Context engineering vs prompt engineering: the crucial distinction
- CLAUDE.md files: purpose, structure, layered approach (global → project → directory)
- Project memory: .claude/ directory, custom commands, skills, hooks
- The context budget: what to include, what to exclude, token economics
- Context rot: when context becomes stale or contradictory
- Repo structure as context: how file organization affects AI understanding
- Documentation as AI fuel: README, ADRs, inline comments become critical
- Multi-file context: @-mentions, file references, search patterns
- The "new developer" test: if a new hire couldn't understand it, neither can the AI
- Runtime retrieval: "just in time" context loading strategies
- Exercise: Write a CLAUDE.md for your current project

### Chapter 6: Prompt Engineering for Code
**File:** `06-prompt-engineering-for-code.html`
**Goal:** Code-specific prompting that goes beyond general prompt engineering.
**Topics:**
- The anatomy of a good coding prompt: task + context + constraints + examples
- Generating code: "Implement X using Y pattern, following Z convention"
- Debugging prompts: error messages, stack traces, reproduction steps
- Refactoring prompts: specifying goals, constraints, what NOT to change
- Code review prompts: requesting specific types (security, performance, style)
- The iterative loop: prompt → review → refine → accept
- Good/bad comparison examples for each scenario (Android, backend, full-stack)
- Templates for common tasks: API endpoints, data models, UI components, tests
- Meta-prompting: "Write me a prompt template for..."
- Exercise: Build a prompt library for your 10 most common development tasks

### Chapter 7: Spec-Driven Development
**File:** `07-spec-driven-development.html`
**Goal:** Teach the Specify → Plan → Implement → Validate cycle.
**Topics:**
- Why specs matter more with AI: garbage in, garbage out at scale
- The specification document: acceptance criteria, edge cases, constraints, non-goals
- The planning phase: breaking specs into implementable chunks
- Implementation with AI: feeding specs to get predictable output
- Validation: automated checks, manual review, spec compliance verification
- Real example walkthrough: Android feature from spec to merged PR
- When specs are overkill: quick fixes, prototypes, explorations
- Tools: markdown templates, issue templates, GitHub spec-kit
- The spec as contract: McKinsey's two-layer approach (orchestration + execution)
- Exercise: Write a spec for a feature, then implement it with AI following the cycle

### Chapter 8: Test-Driven Development with AI
**File:** `08-tdd-with-ai.html`
**Goal:** Show how AI transforms TDD from tedious to productive.
**Topics:**
- The classic TDD problem: writing tests is slow and boring
- AI-powered TDD: let AI write tests from specs, then implement to pass them
- The workflow: spec → AI generates tests → AI implements → human reviews
- Test quality: what makes AI-generated tests good or bad
- Android-specific: JUnit, Espresso, Compose UI tests with AI
- Backend: API tests, integration tests, database tests with AI
- Coverage strategies: asking AI to find untested edge cases
- Mutation testing: using AI to verify test quality
- Anti-pattern: "generate tests for this code" (testing implementation, not behavior)
- Code coverage as behavioral guardrails (CodeScene pattern)
- Exercise: Take an untested class, write a spec, let AI generate tests, verify

### Chapter 9: Agentic Coding Workflows
**File:** `09-agentic-coding-workflows.html`
**Goal:** Teach multi-step autonomous AI workflows.
**Topics:**
- What "agentic" means: AI that plans, executes, and verifies in a loop
- Claude Code as an agent: reading files, running commands, editing code, running tests
- Multi-step tasks: "Add a new API endpoint with tests, documentation, and migration"
- Agent orchestration: multiple Claude Code instances, parallel work, sub-agents
- Custom skills/commands: creating reusable workflows (.claude/commands/)
- The trust spectrum: when to let the agent run free vs when to supervise
- Error recovery: what happens when the agent goes off track
- Long-running agents: harness patterns, compaction, checkpointing
- Real workflow: Claude Code builds a feature end-to-end while you review
- Multi-layer safeguards: generation checks, pre-commit, PR validation
- Exercise: Create a custom Claude Code skill for a repeated task in your project

### Chapter 10: Vibe Coding vs Structured Development
**File:** `10-vibe-vs-structured.html`
**Goal:** Define both approaches and teach when to use each.
**Topics:**
- Vibe coding defined: conversational, exploratory, low-structure AI coding
- Structured development defined: spec-driven, planned, validated AI coding
- When vibe coding wins: prototypes, POCs, learning, personal projects, hackathons
- When structured wins: production code, team projects, regulated industries
- The hybrid approach: vibe-code the prototype, then structure the production version
- Danger zones: vibe coding in production, over-structuring experiments
- Team considerations: how vibe coding affects code review and maintainability
- The morning/evening split: vibe-code new features, agent-driven tests/docs overnight
- Case study: same feature built both ways — comparing outcomes
- Exercise: Build a feature using pure vibe coding, then rebuild with full specs

### Chapter 11: Code Review and Quality
**File:** `11-code-review-quality.html`
**Goal:** Ensure AI-generated code meets professional standards.
**Topics:**
- The review mindset: AI code is "junior developer" code — capable but needs oversight
- Common AI code smells: over-engineering, inconsistent patterns, hallucinated APIs
- Security review: SQL injection, hardcoded secrets, improper auth in AI code
- Performance review: AI tends toward correctness over efficiency
- Architecture review: does AI code fit existing patterns?
- The 10-point review checklist for AI-generated changes
- Code ownership: you are responsible for AI-generated code, period
- Team workflows: PR templates, review guidelines for AI-assisted code
- Code Health assessment: targeting 9.5+ before deploying AI changes (CodeScene)
- Exercise: Review AI-generated code using the checklist, document findings

### Chapter 12: Working with Large Codebases
**File:** `12-large-codebases.html`
**Goal:** Strategies for using AI in existing, complex projects.
**Topics:**
- The context problem: large codebases exceed any context window
- Strategic context loading: what to include, what to summarize, what to skip
- Architecture documentation as AI enabler: ADRs, dependency maps, module docs
- Refactoring with AI: safe patterns for large-scale changes
- Migration stories: Java to Kotlin, XML to Compose, REST to GraphQL
- Legacy code: AI as code archaeologist — understanding undocumented code
- Monorepo strategies: scoping AI to relevant modules
- The "strangler fig" pattern with AI: incremental modernization
- CLAUDE.md for large projects: directory-level instructions
- Exercise: Use AI to document an undocumented module in your codebase

### Chapter 13: Building Full Projects
**File:** `13-building-full-projects.html`
**Goal:** End-to-end walkthrough from idea to deployed project.
**Topics:**
- Phase 1: Ideation and research (AI for market research, technical feasibility)
- Phase 2: Architecture design (AI-assisted system design, tech stack selection)
- Phase 3: Project scaffolding (generating boilerplate, CI/CD, project structure)
- Phase 4: Feature development (spec-driven, iterative AI implementation)
- Phase 5: Testing and QA (comprehensive AI-generated test suites)
- Phase 6: Documentation (AI-generated docs, README, API docs)
- Phase 7: Deployment and monitoring (AI-assisted DevOps)
- Real walkthrough: building a complete Android app from scratch with AI
- Time comparison: traditional vs AI-driven development timeline
- Exercise: Start a new side project using the full AI-driven workflow

### Chapter 14: Android-Specific AI Development
**File:** `14-android-ai-development.html`
**Goal:** Apply all prior learnings specifically to Android development.
**Topics:**
- Gemini in Android Studio: code completion, code transforms, commit messages, Agent Mode
- Generating Jetpack Compose UI: layouts, components, animations, Material Design 3
- Room database code generation: entities, DAOs, migrations
- Retrofit/Ktor API layer generation: models, services, error handling
- ViewModel and state management with AI assistance
- On-device AI: ML Kit, TensorFlow Lite, MediaPipe integration
- Gemini Nano on-device: building features using on-device LLMs
- Android-specific testing: Compose test generation, instrumented tests
- Gradle and build system: AI-assisted dependency management, build optimization
- Exercise: Build a complete Android screen (UI + ViewModel + Repository + Tests) using AI

### Chapter 15: Privacy, Security, and Ethics
**File:** `15-privacy-security-ethics.html`
**Goal:** Responsible AI-driven development practices.
**Topics:**
- What NOT to share: API keys, credentials, PII, proprietary algorithms
- Data sanitization: techniques for sharing code context safely
- License compliance: AI-generated code and open-source licenses
- Security implications: AI can generate vulnerable code — your responsibility
- OWASP top 10 in AI-generated code: common vulnerability patterns
- Corporate policies: navigating enterprise AI usage policies
- The attribution question: who "wrote" AI-generated code?
- Bias in code generation: AI reproduces training data patterns, including bad ones
- Environmental considerations: the carbon cost of AI-assisted development
- Building an AI usage policy for your team
- Exercise: Audit your last 5 AI interactions for potential security/privacy issues

### Chapter 16: The Future and Continuous Learning
**File:** `16-future-continuous-learning.html`
**Goal:** Prepare for what comes next and establish learning habits.
**Topics:**
- The acceleration curve: why AI capabilities are compounding
- Near-term predictions (2026-2027): multi-modal coding, autonomous agents, AI teams
- Skills that will matter more: architecture, system design, product thinking, taste
- Skills that will matter less: boilerplate coding, syntax memorization, repetitive debugging
- Staying current: newsletters, communities, podcasts, conferences
- The experimentation habit: trying new tools monthly
- Building your personal AI toolkit: curating tools, prompts, workflows
- Contributing back: sharing learnings, writing about AI-driven development
- Career strategy: positioning yourself as an AI-augmented developer
- Meta-reflection: this course was built with AI
- Exercise: Create a 90-day personal learning plan for AI-driven development

### Chapter 17: Claude Skills, Subagents, Plugins & MCP — Extending Claude Code
**File:** `17-extending-claude-code.html`
**Goal:** Teach the file-based extension stack that makes Claude Code project-shaped — Skills, Subagents, Plugins, MCP, Hooks, Auto Mode, sandboxing, Agent Teams.
**Topics:**
- The extension stack at a glance: Skills vs Subagents vs Plugins vs MCP vs Hooks — when each is the right tool
- Authoring a Skill: `.claude/skills/<name>/SKILL.md`, frontmatter (name, description, disable-model-invocation), `$ARGUMENTS`, ambient vs side-effect skills
- Authoring a Subagent: `.claude/agents/<name>.md`, isolated context, scoped `tools:` whitelist, model selection, when to delegate
- The Plugin marketplace: `/plugin`, official `claude-plugins-official`, code-intelligence plugins, private enterprise marketplaces (Cowork 2026-02-24)
- MCP servers in practice: `claude mcp add`, named integrations (Notion, Linear, Figma, databases), shared with Android Studio Agent Mode
- Hooks vs Skills vs CLAUDE.md: deterministic guardrails vs advisory expertise; the three-layer defense
- Auto Mode and `/sandbox`: classifier-gated approvals + OS-level isolation, the three risk categories, when to combine
- Agent Teams and parallel sessions: Writer/Reviewer pattern, fan-out via `claude -p` with `--allowedTools`
- Worked example: Android repo with a `compose-migration` Skill, `security-reviewer` Subagent, Linear MCP server, pre-commit Hook
- Anti-patterns: domain knowledge in CLAUDE.md, Subagent when Skill would do, Plugin sprawl, Auto Mode without sandbox
- Exercise: Author one Skill + one Subagent + one Hook in your own project; commit and run a task that exercises all three
