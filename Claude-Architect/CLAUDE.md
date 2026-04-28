# Claude Certified Architect: Foundations

## Project Description
An HTML guide in English for developers preparing for Anthropic's Claude Certified Architect, Foundations (CCA-F) exam. The target audience is developers with 6+ months of hands-on Claude experience who want to earn the certification. The exam has 60 multiple-choice questions across 5 domains, 120 minutes, live proctored.

This course is **completely standalone** — no prerequisites, no references to other courses. Every concept is explained in the context of the CCA-F exam domains and the 6 exam scenarios.

The style is **"For Dummies"** — friendly, approachable, exam-focused. Like a colleague who already passed the cert walking you through what matters. No dry certification-speak. Practical, opinionated, full of exam tips and architectural patterns.

## Language Rules
- All content is in **English**
- Tone: friendly, conversational, exam-focused — like study prep with a knowledgeable colleague
- Use analogies from everyday life and software development
- **No math formulas** — explain everything through intuition, diagrams described in words, and analogies
- Address: second person singular (you)
- When introducing a concept, always connect it to the exam: "The exam tests this by..." or "In the Customer Support scenario, this shows up as..."
- Light humor is welcome — keep it engaging, not dry
- Use short paragraphs — walls of text kill understanding
- Code examples should be **Python, JSON, YAML, or shell commands** — practical API calls and config snippets

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

## Research Rules (CRITICAL)
The CCA-F certification was launched March 12, 2026. **You MUST search the web before writing each chapter.** Do not rely on model training data for exam specifics, API details, or certification content.

Key research sources:
- **Anthropic docs**: `docs.anthropic.com` — Claude API, Claude Code, Agent SDK
- **Anthropic blog**: `anthropic.com/news`, `anthropic.com/engineering`
- **MCP specification**: `modelcontextprotocol.io`
- **CCA-F exam resources**: `claudecertifications.com` — study guides, practice questions
- **Anthropic Academy**: Free courses on Skilljar — official prep materials
- **Community resources**: Medium articles, Dev.to posts, Reddit discussions on CCA-F prep

## File Structure
```
Claude-Architect/
  CLAUDE.md                              — This file
  .claude/
    commands/
      generate-next-chapter.md           — Skill for chapter generation
  chapters/
    index.html                           — Landing page with navigation
    assets/
      style.css                          — Shared CSS with dark/light theme
    01-exam-landscape.html               — Welcome to the CCA-F
    02-multi-agent-fundamentals.html     — Multi-Agent Systems
    03-task-decomposition.html           — Task Decomposition
    04-orchestration-patterns.html       — Orchestration Patterns
    05-tool-design.html                  — Designing Agent Tools
    06-mcp-integration.html              — MCP: The Universal Adapter
    07-claude-code-config.html           — Claude Code Configuration
    08-claude-code-workflows.html        — Claude Code Workflows
    09-prompt-engineering.html           — Prompt Engineering for Architects
    10-structured-output.html            — Structured Output & Validation
    11-context-reliability.html          — Context Management & Reliability
    12-exam-scenarios.html               — Exam Day: Scenarios & Final Review
    13-managed-agents.html               — Managed Agents for Architects
```

## Progress Tracking
- [x] Chapter 1: Welcome to the CCA-F
- [x] Chapter 2: Multi-Agent Systems
- [x] Chapter 3: Task Decomposition
- [x] Chapter 4: Orchestration Patterns
- [x] Chapter 5: Designing Agent Tools
- [x] Chapter 6: MCP: The Universal Adapter
- [x] Chapter 7: Claude Code Configuration
- [x] Chapter 8: Claude Code Workflows
- [x] Chapter 9: Prompt Engineering for Architects
- [x] Chapter 10: Structured Output & Validation
- [x] Chapter 11: Context Management & Reliability
- [x] Chapter 12: Exam Day: Scenarios & Final Review
- [x] Chapter 13: Managed Agents for Architects
- [x] Chapter 14: Agent Evaluations &amp; Observability

## Instructions for /generate-next-chapter
When the user invokes `/generate-next-chapter`:
1. Read this CLAUDE.md and find the first chapter marked with `[ ]` in Progress Tracking
2. Read the "Chapter Details" section below for that chapter's topics
3. Read `chapters/assets/style.css` for available CSS classes
4. Read `chapters/index.html` for navigation template
5. Read the previous chapter (if any) for context and smooth transition
6. **MANDATORY: Search the web** for the latest information on the chapter's topics — check Anthropic docs, CCA-F exam resources, MCP spec, community study guides, and recent articles
7. Generate the HTML file in `chapters/` with full content (400-600 lines)
8. Update CLAUDE.md — mark the chapter as `[x]`
9. Update `chapters/index.html` — remove `pending` class from that chapter's card
10. Update navigation on the previous chapter (add "next chapter" link if missing)

## CSS Classes for Content

### Course-specific boxes:
- `.exam-tip-box` — Blue accent, for exam-specific hints and strategies. **Required in every chapter.**
- `.architect-box` — Dark blue accent, for design patterns and architectural tradeoffs. **Required in every chapter.**

### Shared boxes:
- `.prompt-example.good` / `.prompt-example.bad` — Green/red labeled examples
- `.comparison` — Side-by-side grid for good/bad examples
- `.tip-box` — General tips (blue)
- `.warning-box` — Warnings and gotchas (orange)
- `.exercise-box` — Hands-on tasks (gold). **Required in every chapter.**
- `.highlight-box` — Key concept callout (blue gradient)
- `.stats-grid` + `.stat-card` — Number/stat display grid
- `.tool-card` — Tool/feature card with icon
- `.workflow-steps` — Horizontal step flow with arrows
- `.checklist` — Checkbox-style list. **Required at end of every chapter for Quick Review.**

## Content Guidelines

Every chapter MUST include:
1. **Domain weight callout** in the introduction (e.g., "This covers Domain 1 — 27% of the exam")
2. At least one `.exam-tip-box` with certification-specific advice
3. At least one `.architect-box` with a design pattern or architectural tradeoff
4. At least one `.exercise-box` with a practical task
5. **Scenario connections** — mention which of the 6 exam scenarios apply
6. **Quick Review** section at the end with 3-5 key takeaways as a `.checklist`
7. Preview of the next chapter

The 6 exam scenarios are:
1. Customer Support Resolution Agent
2. Code Generation with Claude Code
3. Multi-Agent Research System
4. Developer Productivity with Claude
5. Claude Code for CI/CD
6. Structured Data Extraction

## Chapter Details

### Chapter 1: Welcome to the CCA-F
**File:** `01-exam-landscape.html`
**Goal:** Orient the reader on what the CCA-F exam is, how it's structured, and how to use this course to prepare.
**Topics:**
- What is the CCA-F certification and why it matters (Anthropic's first official cert)
- Exam format: 60 questions, 120 minutes, live proctored, no external tools
- The 5 competency domains and their weights (27%, 18%, 20%, 20%, 15%)
- The 6 exam scenarios — brief overview of each
- How 4 of 6 scenarios are randomly selected per exam sitting
- Prerequisites: 6+ months hands-on with Claude APIs, Agent SDK, Claude Code, MCP
- Official study resources: Anthropic Academy (13 free courses), claudecertifications.com
- How this course maps to the exam domains (course roadmap)
- Study timeline recommendations (6-10 weeks for experienced devs, 2-4 months for newer)
- Exam-day logistics and what to expect

### Chapter 2: Multi-Agent Systems
**File:** `02-multi-agent-fundamentals.html`
**Goal:** Explain multi-agent architecture fundamentals — the foundation of Domain 1 (27% of the exam).
**Topics:**
- Why single agents hit walls — complexity, context limits, specialization needs
- Agent roles and specialization — researcher, coder, reviewer, orchestrator
- Hub-and-spoke topology: central orchestrator delegates to specialist agents
- Peer-to-peer topology: agents collaborate as equals
- The agent loop: plan → act → observe → repeat
- Autonomous agents vs orchestrated agents — when to use each
- Claude Agent SDK basics — how Anthropic implements multi-agent
- Agent communication: structured messages, handoffs, shared state
- Common pitfalls: over-decomposition, chatty agents, unclear responsibilities
- Analogy: orchestra (orchestrated) vs jazz ensemble (autonomous)
- Exam scenarios where this appears: Multi-Agent Research, Customer Support

### Chapter 3: Task Decomposition
**File:** `03-task-decomposition.html`
**Goal:** Teach how to break complex tasks into agent-manageable subtasks — a key Domain 1 skill.
**Topics:**
- Why decomposition matters — context window limits, parallelism, reliability
- Hierarchical decomposition: epic → story → task (project management analogy)
- DAG-based workflows: directed acyclic graphs for task dependencies
- Static decomposition: predetermined task structure
- Dynamic decomposition: orchestrator decides at runtime based on results
- Fan-out/fan-in patterns: parallel execution with result aggregation
- Dependency management between subtasks
- Granularity decisions: too coarse vs too fine
- Error handling at the subtask level — retry, skip, escalate
- Exam scenarios: Multi-Agent Research (decompose research query), Code Gen (decompose coding task)
- Practice: decompose a real-world task into an agent workflow

### Chapter 4: Orchestration Patterns
**File:** `04-orchestration-patterns.html`
**Goal:** Cover the major orchestration patterns tested in the exam — hub-and-spoke, pipeline, map-reduce.
**Topics:**
- Hub-and-spoke in depth: orchestrator responsibilities (routing, aggregation, error handling)
- Pipeline/chain pattern: sequential processing, each agent transforms and passes
- Map-reduce pattern: parallel execution with result aggregation
- Routing pattern: directing tasks to specialized agents based on classification
- Escalation and fallback patterns: what happens when an agent fails
- State passing between agents — what to share, what to isolate
- Agent lifecycle management: spawning, monitoring, terminating
- Choosing the right pattern: decision framework based on task characteristics
- Anti-patterns: God orchestrator, circular dependencies, missing error handling
- Exam scenarios: Customer Support (routing + escalation), Multi-Agent Research (map-reduce)
- Real-world examples from Anthropic's agent architecture documentation

### Chapter 5: Designing Agent Tools
**File:** `05-tool-design.html`
**Goal:** Teach tool schema design and the boundary between agent reasoning and tool execution — Domain 2 focus.
**Topics:**
- What tools are in the Claude API: name, description, input_schema
- Tool description design: clear, specific, includes when-to-use guidance
- Parameter schema design: required vs optional, enums, nested objects
- Tool granularity: one-purpose tools vs Swiss-army-knife tools
- The reasoning boundary: what the agent decides vs what the tool does
- Tool overload: too many tools confuse the model — keeping it focused
- Parallel tool calls: when and how Claude uses them
- Error responses that help the agent recover (structured error objects)
- Tool testing strategies: unit testing tools independent of the model
- Tool versioning and backward compatibility
- Exam scenarios: Customer Support (tool for ticket lookup, knowledge base search), Structured Data Extraction (tool for schema validation)

### Chapter 6: MCP: The Universal Adapter
**File:** `06-mcp-integration.html`
**Goal:** Deep dive into Model Context Protocol — architecture, implementation, and exam-relevant details.
**Topics:**
- What MCP solves: the N×M integration problem (N agents × M tools)
- MCP architecture: hosts, clients, servers, and transports
- Transport types: stdio (local) vs HTTP/SSE (remote) — when to use each
- The three MCP primitives: tools, resources, and prompts
- Building an MCP server: registering tools, handling requests
- Connecting MCP servers to Claude Code and other clients
- Security boundaries: authentication, authorization, sandboxing
- MCP server discovery and configuration
- Resource management: exposing data sources through MCP
- Prompt templates in MCP: reusable prompt patterns
- Common MCP patterns: database access, API gateway, file system
- Exam scenarios: Structured Data Extraction (MCP for data sources), Dev Productivity (MCP for internal tools)

### Chapter 7: Claude Code Configuration
**File:** `07-claude-code-config.html`
**Goal:** Cover Claude Code's configuration system — CLAUDE.md, settings, hooks, permissions — Domain 3 focus.
**Topics:**
- CLAUDE.md hierarchy: user-level, project-level, directory-level — how they merge
- What goes in CLAUDE.md: project context, conventions, instructions, constraints
- CLAUDE.md as persistent context engineering — it's always in the system prompt
- Settings layers: global settings vs project settings vs local settings
- Permission configuration: allowlist, denylist, trust spectrum
- Hooks system: PreToolUse, PostToolUse — automating workflows
- Agent skills: `.claude/commands/` — creating reusable parameterized prompts
- Project skills vs user skills — scope and sharing
- The trust spectrum: from full manual approval to fully autonomous
- Best practices: what to put in CLAUDE.md vs what to leave out
- Exam scenarios: Code Gen with Claude Code (CLAUDE.md for project context), Dev Productivity (hooks for automation)

### Chapter 8: Claude Code Workflows
**File:** `08-claude-code-workflows.html`
**Goal:** Cover Claude Code's advanced workflow features — plan mode, worktrees, CI/CD — Domain 3 focus.
**Topics:**
- Plan mode: designing before executing — when and how to use it
- Git worktrees: isolated branches for parallel work
- MCP server integration in Claude Code: adding external tools
- `claude -p` for non-interactive/headless execution
- CI/CD integration: running Claude Code in pipelines (GitHub Actions, etc.)
- Scheduled agents and remote triggers
- The dual-agent pattern: initializer agent + worker sub-agents
- Batch processing with Claude Code
- Security considerations for CI/CD: API key management, permissions
- Cost management: monitoring and controlling API usage
- Exam scenarios: Claude Code for CI/CD (pipeline integration), Code Gen (worktrees for feature branches)

### Chapter 9: Prompt Engineering for Architects
**File:** `09-prompt-engineering.html`
**Goal:** Cover production-grade prompt engineering techniques — Domain 4 focus.
**Topics:**
- Few-shot prompting: providing examples for consistent output
- Chain-of-thought: encouraging step-by-step reasoning
- Role prompting: setting behavioral context in system prompts
- System prompt design for agent harnesses: instructions, constraints, personality
- Explicit criteria: defining evaluation rubrics in the prompt
- Prompt templates and parameterization — reusable prompt patterns
- The difference between user prompts and system-level instructions
- Prompt iteration and A/B testing in production
- Prompt reliability: making prompts robust to edge cases
- Temperature and sampling parameters: when to adjust
- Anti-patterns: over-prompting, contradictory instructions, prompt injection vulnerabilities
- Exam scenarios: all scenarios test prompt engineering to some degree

### Chapter 10: Structured Output & Validation
**File:** `10-structured-output.html`
**Goal:** Cover JSON schema enforcement, validation loops, and extraction pipelines — Domain 4 focus.
**Topics:**
- Why structured output matters: parsing reliability, downstream integration
- JSON schema enforcement in the Claude API: `tool_use` for structured responses
- Output parsing strategies: regex, JSON parsing, schema validation
- Validation loops: generate → validate → retry — the standard pattern
- Constrained decoding: forcing output to match a schema
- Building extraction pipelines: multi-step extraction from unstructured text
- Pydantic-style validation: type checking, field constraints, custom validators
- Handling malformed output gracefully: fallbacks, partial extraction
- When to use structured output vs freeform text
- Schema design best practices: flat vs nested, required vs optional fields
- Error handling in extraction: missing fields, type mismatches, confidence scores
- Exam scenarios: Structured Data Extraction (the primary scenario), Customer Support (extracting ticket data)

### Chapter 11: Context Management & Reliability
**File:** `11-context-reliability.html`
**Goal:** Cover context window management, escalation patterns, and reliability engineering — Domain 5 focus.
**Topics:**
- Token budgets: understanding and managing context window limits
- Context window arithmetic: system prompt + conversation + tools = total
- Compaction strategies: summarization, truncation, sliding window
- The "lost in the middle" problem: information near the edges is remembered better
- Escalation patterns: agent-to-human handoff, tiered support
- Error handling and retry logic: exponential backoff, circuit breakers
- Graceful degradation: what to do when the model fails or context overflows
- Long-running interactions: session persistence and conversation state
- Rate limiting and quota management
- Monitoring and observability: logging, metrics, alerting for agent systems
- Reliability testing: chaos engineering for AI systems
- Exam scenarios: Customer Support (long conversations, escalation), Multi-Agent Research (context across agents)

### Chapter 12: Exam Day: Scenarios & Final Review
**File:** `12-exam-scenarios.html`
**Goal:** Walk through all 6 exam scenarios, provide practice questions, and deliver final exam strategies.
**Topics:**
- Deep walkthrough of each exam scenario:
  1. Customer Support Resolution Agent — domains tested, patterns expected, common traps
  2. Code Generation with Claude Code — domains tested, patterns expected, common traps
  3. Multi-Agent Research System — domains tested, patterns expected, common traps
  4. Developer Productivity with Claude — domains tested, patterns expected, common traps
  5. Claude Code for CI/CD — domains tested, patterns expected, common traps
  6. Structured Data Extraction — domains tested, patterns expected, common traps
- How scenarios map to the 5 domains (matrix view)
- 10 practice questions with detailed explanations
- Exam-day strategies: time management (2 min per question), elimination technique
- Domain-weight-aware prioritization: spend more time on Domain 1 questions (27%)
- Common exam traps and misconceptions
- Final checklist: every key concept by domain
- Resources for further study after passing

### Chapter 13: Managed Agents for Architects
**File:** `13-managed-agents.html`
**Goal:** Cover Anthropic's Managed Agents from an architectural decision-making perspective — when to use managed vs custom, how it maps to exam domains, and design tradeoffs.
**Topics:**
- What Managed Agents adds to the Claude ecosystem: a fully managed agent runtime alongside the API, Agent SDK, and Claude Code
- Architecture overview: Agent, Environment, Session, Events — the four pillars
- Domain 1 connection (Agentic Architecture): how Managed Agents implements orchestration patterns, multi-agent preview, task decomposition at platform level
- Domain 2 connection (Tool Integration): built-in tools, MCP server attachment, how tool design from Chapter 5 applies
- Domain 3 connection (Claude Code Workflows): Managed Agents as cloud counterpart to local Claude Code, CI/CD integration
- Domain 4 connection (Prompt Engineering): system prompt design for managed agents, reliability in managed environments
- Domain 5 connection (Context & Reliability): session lifecycle, event streaming reliability, graceful degradation
- The architectural decision: managed vs self-hosted — decision matrix (customization, cost, compliance, latency, ops overhead)
- Environment design: container architecture, packages, network policies, security boundaries
- Research previews and exam implications: Multi-agent, Memory, Outcomes
- Exam scenario connections: Customer Support (long-running), Multi-Agent Research (cloud orchestration), CI/CD (scheduled agents)
- Practice questions: 3-5 MCQs testing architectural decisions about when to use Managed Agents
- Exercise: Design a Managed Agents architecture for the Multi-Agent Research exam scenario

### Chapter 14: Agent Evaluations & Observability
**File:** `14-evals-and-observability.html`
**Goal:** Cover the eval-design and production-observability discipline that closes Domain 5 — how an architect proves an agent works and keeps working across model upgrades, prompt revisions, and tool changes.
**Topics:**
- Why eval rigor is the architect's job — the ship-without-eval drift failure mode
- Three eval types from Anthropic's official taxonomy: single-turn, multi-turn, agent-level
- Pre-launch vs production evals — the architect's deployment lens
- Capability evals (start low, graduate) vs regression evals (stay near 100%)
- Designing eval datasets — 20–50 tasks from real failures, unambiguous, balanced, isolated
- Eval frameworks: Harbor + Terminal-Bench 2.0, skill-creator, Braintrust, MLflow, Agent SDK hooks, OpenTelemetry
- Eval-aware design patterns: structured outputs as testable boundaries, hooks as deterministic checkpoints, structured errors as scoring signals
- The three-agent planning/generation/evaluation harness pattern (April 2026)
- LLM-as-judge — calibration, sycophancy, "Unknown" out-clauses
- Non-determinism metrics: pass@k vs pass^k and when each fits
- Production observability: tokens/session, tool-success rate, escalation rate, first-contact resolution, cost-per-resolution, latency — OpenTelemetry as the 2026 standard
- Eval-driven iteration loop: capture → codify → reproduce → iterate → graduate
- Anti-patterns: deploy-time-only evals, happy-path-only sampling, uncalibrated LLM judges, eval-suite rot
- Scenario-by-scenario eval design for all 6 CCA-F scenarios
- Practice questions and a hands-on exercise: design a 10-task eval suite for the Customer Support scenario
