# From Zero to App With AI For Dummies

## Project Description
An HTML guide in English for experienced developers who want to build complete applications from a single-sentence idea using AI in specialized team roles. The running case study builds a recipes Android app from scratch: starting from "I want an offline-first Android app for managing recipes" and ending with a production-grade app — using AI as Product Owner, Product Manager, Architect, Developer, Code Reviewer, Security Reviewer, and QA Engineer.

Each role is formalized as an actual Claude Code skill with a system prompt, input/output contract, and rules. The orchestration uses Claude Code's Agent tool, plan mode, and structured handoffs between roles.

The target audience is experienced developers who know their tech stack. They don't need architecture explained — they need to learn how to build a reproducible AI-driven development pipeline.

The style is **"For Dummies"** — friendly and energetic, like a colleague demonstrating an exciting new way to build software.

## Language Rules
- All content is in **English**
- Tone: visionary but practical — "look what's possible, and here's exactly how to do it"
- Assume the reader knows Clean Architecture, MVI, Room, Hilt, Compose
- NEVER explain the underlying patterns — focus on the AI pipeline
- Each role is treated as a specialized team member, not just a prompt variation
- Reference other courses inline: "For more on [topic], see [Course Name] Chapter N"

## HTML Conventions
- Each chapter is a separate HTML file in `chapters/`
- Shared CSS: `assets/style.css`
- Target: **400-600 lines HTML**
- UTF-8, HTML5 doctype, meta viewport

## Content Generation Rules
- All generated chapters MUST meet the 400-line minimum on the FIRST attempt.
- Never pad content incrementally.

## HTML Validation Rules
- Always close tip-box divs with `</div>`, never `</tip>`.
- Validate all HTML tags are properly closed.

## Project Structure Rules
- Always check the current working directory. Do NOT search parent directories unless asked.

## Cross-Reference Rules
- All cross-reference links use relative paths and point to valid targets.

## File Structure
```
AI-Factory/
  CLAUDE.md
  .claude/
    commands/
      generate-next-chapter.md
      create-memory-map.md
  chapters/
    index.html
    assets/
      style.css                          — Shared CSS (forest green + cyan scheme)
    01-ai-factory.html                   — The AI Factory: Roles, Not Prompts
    02-orchestration.html                — Orchestration With Claude Code
    03-the-idea.html                     — One Sentence to App
    04-product-owner.html                — The AI Product Owner: Vision and Scope
    05-product-manager.html              — The AI Product Manager: Specs for Machines
    06-architect.html                    — The AI Architect: Design for the Machine
    07-implementation-plan.html          — From Design to Implementation Plan
    08-developer.html                    — The AI Developer: Writing Code at Scale
    09-code-reviewer.html                — The AI Code Reviewer: Quality at Machine Speed
    10-security-and-qa.html              — Security Review and QA Engineering
    11-full-pipeline.html                — The Full Pipeline: All Roles in Concert
    12-factory-playbook.html             — Your AI Factory Playbook
    13-agent-sdk.html                    — Running the Factory Programmatically — The Claude Agent SDK
    maps/
```

## Progress Tracking
- [x] Chapter 1: The AI Factory: Roles, Not Prompts
- [x] Chapter 2: Orchestration With Claude Code
- [x] Chapter 3: One Sentence to App
- [x] Chapter 4: The AI Product Owner: Vision and Scope
- [x] Chapter 5: The AI Product Manager: Specs for Machines
- [x] Chapter 6: The AI Architect: Design for the Machine
- [x] Chapter 7: From Design to Implementation Plan
- [x] Chapter 8: The AI Developer: Writing Code at Scale
- [x] Chapter 9: The AI Code Reviewer: Quality at Machine Speed
- [x] Chapter 10: Security Review and QA Engineering
- [x] Chapter 11: The Full Pipeline: All Roles in Concert
- [x] Chapter 12: Your AI Factory Playbook
- [x] Chapter 13: Running the Factory Programmatically — The Claude Agent SDK

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
- `.role-card` — role definition card with name, icon, input/output contract (green accent, `.role-name` + `.role-input` + `.role-output` children)
- `.pipeline-stage` — pipeline flow with connecting arrows (gradient green-to-blue)
- `.artifact-box` — generated artifact with source-role badge (teal accent)
- `.orchestration-trace` — execution trace with timing/cost (silver accent)
- `.prompt-example.good` / `.prompt-example.bad`
- `.comparison`, `.tip-box`, `.warning-box`, `.exercise-box`
- `.checklist`, `.highlight-box`, `.stats-grid`, `.stat-card`
- `.tool-card`, `.workflow-steps`

## Content Guidelines
- **At least 1 `.role-card`** per chapter defining or referencing a role
- **At least 1 `.artifact-box`** per chapter showing a generated artifact
- **At least 1 `.exercise-box`** per chapter building or customizing a role skill
- All examples build toward the recipes app
- Never explain Android architecture patterns
- Focus on orchestration: how roles hand off, how context flows, how quality gates work
- Every skill file shown should be complete enough to copy-paste and run

## Chapter Details

### Chapter 1: The AI Factory: Roles, Not Prompts
**File:** `01-ai-factory.html`
**Goal:** The paradigm shift from "using AI" to "orchestrating AI team members."
**Topics:**
- The shift: from ad-hoc prompting to formalized AI roles with contracts
- Why roles produce better results than ad-hoc prompting: consistency, reproducibility, quality
- The 7-role pipeline: Product Owner → Product Manager → Architect → Developer → Code Reviewer → Security Reviewer → QA Engineer
- The role contract pattern: each role has inputs, outputs, and quality criteria
- Claude Code skills as role implementations: why skills > prompts
- The Agent tool for orchestration: dispatching to specialized subagents
- The recipes app as our target: from "I want a recipes app" to production code
- What this course builds: by Chapter 12, you have a complete AI development pipeline
- Cross-reference: "AI-Agents Chapter 7 covers multi-agent orchestration theory. This course makes it operational."

### Chapter 2: Orchestration With Claude Code
**File:** `02-orchestration.html`
**Goal:** Technical foundation for multi-role AI orchestration.
**Topics:**
- The Agent tool: dispatching to subagents within Claude Code, passing context, getting results
- Plan mode: the orchestrator's first step (plan before executing any role)
- Skill files as role definitions: anatomy of a skill that embodies a role
- The orchestrator skill pattern: a master skill that coordinates all roles
- Passing context between roles: artifacts as handoffs (vision doc → specs → design → code)
- Error handling and re-dispatch: when a role produces unsatisfactory output
- The role registry: which skill handles which role, with fallback strategies
- Human oversight insertion points: where humans review before the pipeline continues
- Cross-reference: "Claude-Architect Chapter 4 covers orchestration patterns abstractly. This chapter implements them."

### Chapter 3: One Sentence to App
**File:** `03-the-idea.html`
**Goal:** Starting from a single sentence and mapping the full pipeline.
**Topics:**
- The one-sentence seed: "I want an offline-first Android app for managing recipes, organizing them into books, and generating grocery lists."
- Why constraints matter: platform (Android), architecture style (Clean Architecture + MVI), target audience (home cooks)
- The pipeline execution plan: what each role will produce in order
- The artifact chain: idea → vision → specs → design → code → review → tests
- The handoff protocol: structured output format for passing between roles
- Time and cost estimation: how long the pipeline takes, what it costs in tokens
- Configuring the pipeline for the recipes app: setting up the CLAUDE.md and skills directory
- The first run: executing the pipeline overview

### Chapter 4: The AI Product Owner: Vision and Scope
**File:** `04-product-owner.html`
**Goal:** Build the PO skill that turns an idea into a product vision.
**Topics:**
- The PO skill file: system prompt, role definition, output format
- Product vision document template: what the PO produces
- User persona generation: who uses this app and what they need
- Feature discovery: brainstorming with constraints (offline-first, mobile, recipe domain)
- MoSCoW prioritization: Must/Should/Could/Won't for the recipes app features
- Release roadmap: MVP features vs v1 vs v2
- The PO output contract: what the PM role expects as input
- Running the PO skill: live example with the recipes app idea
- Reviewing PO output: human oversight checkpoint

### Chapter 5: The AI Product Manager: Specs for Machines
**File:** `05-product-manager.html`
**Goal:** Build the PM skill that turns vision into AI-implementable specs.
**Topics:**
- The PM skill file: system prompt, input expectations, output format
- The key insight: specs must be written for AI consumption, not just humans
- Feature specification template: structured format AI can parse
- Acceptance criteria that AI can verify: testable, specific, measurable
- User stories with testable outcomes: "As a user, I can..." with AI-verifiable criteria
- Edge case enumeration: AI excels at discovering edge cases
- Non-functional requirements: performance budgets, accessibility targets
- API contracts between features: how features communicate
- The PM output contract: what the Architect expects
- Running the PM skill: live example producing recipes app specs

### Chapter 6: The AI Architect: Design for the Machine
**File:** `06-architect.html`
**Goal:** Build the Architect skill that turns specs into technical design.
**Topics:**
- The Architect skill file: system prompt, design document template, output format
- Module decomposition: from specs to 10-module structure
- Dependency graph generation: defining what depends on what
- Data model design: domain entities, Room entities, DTOs, mappers
- Technology selection: choosing Hilt, Room, Compose, Navigation (and why)
- Architecture rules generation: the Architect role CREATES the dual-format rules
- The Architect output contract: module structure + data models + rules → Developer input
- Running the Architect skill: live example designing the recipes app
- Cross-reference: "AI-Engineering Chapter 7 covers the architecture rules pattern. The Architect role generates these rules."

### Chapter 7: From Design to Implementation Plan
**File:** `07-implementation-plan.html`
**Goal:** Bridge between design and code with AI-assisted sprint planning.
**Topics:**
- Breaking architecture into implementable tasks: the task decomposition strategy
- Dependency ordering: core modules first, then data, then features
- Sprint planning with AI: grouping tasks into logical sprints
- The implementation backlog: prioritized list of tasks for the Developer role
- Task granularity: right size for AI execution (not too big, not too small)
- The plan as input to the Developer role: task spec format
- Risk assessment for each task: what could go wrong, fallback strategies
- The implementation plan for the recipes app: full backlog with 30+ tasks

### Chapter 8: The AI Developer: Writing Code at Scale
**File:** `08-developer.html`
**Goal:** Build the Developer skill that generates compilable, tested code.
**Topics:**
- The Developer skill file: system prompt, context loading, output format
- Context loading strategy: architecture rules + existing code + task spec
- Code generation patterns: one module at a time, one layer at a time
- The build-test-fix loop: generate → compile → fix errors → run tests → iterate
- Handling AI limitations: files too large, cross-module dependencies, context overflow
- The Developer output contract: compilable code + passing tests
- Running the Developer skill: generating the recipes app core module
- Common failures: compilation errors, missing imports, wrong package structure
- The iterative approach: multiple Developer invocations per module

### Chapter 9: The AI Code Reviewer: Quality at Machine Speed
**File:** `09-code-reviewer.html`
**Goal:** Build the Reviewer skill that checks code against architecture rules.
**Topics:**
- The Code Reviewer skill file: loads review checklists, produces structured feedback
- Structured review output: rule ID, severity (MUST/SHOULD/PREFER), location, explanation, fix
- The review-fix loop: Reviewer finds issues → Developer regenerates → Reviewer re-reviews
- When to accept vs when to send back: the acceptance threshold
- The Code Reviewer output contract: pass/fail with detailed findings
- Running the Reviewer skill: reviewing generated recipes app code against all 10 checklists
- Common findings: scope violations, missing error handling, wrong dependency direction
- Cross-reference: "AI-CodeReview covers the human side of reviewing AI code. This chapter automates the first pass."

### Chapter 10: Security Review and QA Engineering
**File:** `10-security-and-qa.html`
**Goal:** Build Security Reviewer and QA Engineer skills.
**Topics:**
- The Security Reviewer skill: OWASP checks, dependency audit, auth review, secret detection
- Security review output: severity-rated findings with remediation steps
- The QA Engineer skill: test generation strategy, edge case discovery, coverage measurement
- QA output: comprehensive test suite with coverage report
- The testing strategy for the recipes app: 128+ ViewModel tests, integration tests
- Edge case testing: AI finding scenarios humans miss
- Combining Security + QA: the "ship readiness" assessment
- Human oversight: which security findings need human judgment

### Chapter 11: The Full Pipeline: All Roles in Concert
**File:** `11-full-pipeline.html`
**Goal:** End-to-end execution of the complete 7-role pipeline.
**Topics:**
- The orchestrator skill: coordinating PO → PM → Architect → Developer → Reviewer → Security → QA
- Full pipeline execution on the recipes app: from idea to reviewed, tested code
- Human oversight insertion points: after PO vision, after Architect design, after Developer code
- Error recovery patterns: what happens when a role fails or produces poor output
- The pipeline execution log: tracking what each role produced, time spent, tokens used
- Time and cost analysis: how long the full pipeline takes, what it costs
- Comparing pipeline output to the actual recipes app at `/app/recipes/`
- Lessons from the run: where the pipeline excels, where it needs human help

### Chapter 12: Your AI Factory Playbook
**File:** `12-factory-playbook.html`
**Goal:** Making the pipeline reusable, customizable, and team-shareable.
**Topics:**
- Adapting the pipeline to other platforms: iOS (SwiftUI), web (React/Next.js), backend (Spring Boot)
- Adding custom roles: Designer, DevOps, Technical Writer, Performance Engineer
- Removing or combining roles: smaller projects that don't need all 7
- The skill library as a team asset: sharing, versioning, and evolving the pipeline
- Cost optimization: which roles need Opus (Architect, Reviewer), which can use Sonnet (Developer, QA)
- The factory as a competitive advantage: shipping faster without sacrificing quality
- Connecting back to AI-Engineering: "The foundation that makes the factory possible"
- Connecting to AI-Rewrite: "Same app, different path — rewrite vs greenfield"
- The complete skill library reference: all 7 role skills ready to copy-paste

### Chapter 13: Running the Factory Programmatically — The Claude Agent SDK
**File:** `13-agent-sdk.html`
**Goal:** Translate the interactive Claude Code factory into a library-form pipeline that can run in CI, cron, or as part of an embedded product.
**Topics:**
- The Claude Agent SDK: same loop, same tools, library form (Python + TypeScript)
- Renaming context: Claude Code SDK → Claude Agent SDK (2026)
- Installing `@anthropic-ai/claude-agent-sdk` (TS) or `claude-agent-sdk` (Python)
- The `query()` async iterator and `ClaudeAgentOptions`
- Auto-loading existing skills, sub-agents, and CLAUDE.md from `.claude/`
- Re-implementing the orchestrator as a Python script with per-stage budget control
- Headless pipeline execution: cron-driven, CI-driven, webhook-driven
- Structured outputs: skill-side JSON contracts vs SDK-side schema enforcement
- Cost monitoring and budget enforcement via PreToolUse / PostToolUse hooks
- Hybrid usage: developers run interactively in Claude Code, CI runs the same skills via the SDK
- When to graduate from Claude Code → Agent SDK
- Security caveats: re-adding human checkpoints as approval gates
- Worked example: GitHub Actions workflow that runs RecipeVault nightly
