# Building AI Agents For Dummies

## Project Description
An HTML guide in English for developers who want to build autonomous AI agent systems. The target audience is experienced developers who have used AI tools (Claude Code, ChatGPT, etc.) and understand basic AI concepts (prompting, APIs, tool use) but have never designed or built an agent system from scratch. They want to go from "I use AI" to "I build AI agents."

The style is **"For Dummies"** — friendly, approachable, heavy on code examples and architectural diagrams described in text. The reader is smart (they're a developer) but has never implemented a ReAct loop, designed a tool schema for an agent, or orchestrated multiple agents. Every chapter should produce at least one "now I see how this works" moment, backed by runnable code.

## Language Rules
- All content is in **English**
- Tone: friendly, conversational, like a senior engineer walking you through building your first agent
- Use analogies from software engineering (microservices, event loops, message queues) to explain agent concepts
- Address: second person singular (you)
- When introducing a pattern, always show: "Here's the concept" → "Here's the code" → "Here's when you'd use this in practice"
- Light humor is welcome — keep it engaging, not dry
- Use short paragraphs — walls of text kill understanding
- Code examples in **Python** (primary) or **TypeScript** (alternative) — agents are built with code
- **WebSearch is MANDATORY for every chapter** — agent frameworks evolve rapidly. Always verify current APIs, SDKs, and best practices.

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
AI-Agents/
  CLAUDE.md                              — This file
  .claude/
    commands/
      generate-next-chapter.md           — Skill for chapter generation
  chapters/
    index.html                           — Landing page with navigation
    assets/
      style.css                          — Shared CSS with dark/light theme
    01-what-are-agents.html              — What Are AI Agents, Really?
    02-agent-architectures.html          — Agent Architectures
    03-tool-design.html                  — Tool Design for Agents
    04-first-agent.html                  — Your First Agent
    05-memory-state.html                 — Memory & State Management
    06-human-in-the-loop.html            — Human-in-the-Loop Patterns
    07-multi-agent.html                  — Multi-Agent Orchestration
    08-error-recovery.html               — Error Handling & Recovery
    09-evaluation.html                   — Agent Evaluation & Testing
    10-agent-frameworks.html             — Agent Frameworks & SDKs
    11-production.html                   — Production Deployment
    12-capstone.html                     — Building a Real Agent System
    13-managed-agents.html               — Managed Agents: Deploy on Anthropic's Infrastructure
```

## Progress Tracking
- [x] Chapter 1: What Are AI Agents, Really?
- [x] Chapter 2: Agent Architectures
- [x] Chapter 3: Tool Design for Agents
- [x] Chapter 4: Your First Agent
- [x] Chapter 5: Memory & State Management
- [x] Chapter 6: Human-in-the-Loop Patterns
- [x] Chapter 7: Multi-Agent Orchestration
- [x] Chapter 8: Error Handling & Recovery
- [x] Chapter 9: Agent Evaluation & Testing
- [x] Chapter 10: Agent Frameworks & SDKs
- [x] Chapter 11: Production Deployment
- [x] Chapter 12: Building a Real Agent System
- [x] Chapter 13: Managed Agents — Deploy on Anthropic's Infrastructure

## Instructions for /generate-next-chapter
When the user invokes `/generate-next-chapter`:
1. Read this CLAUDE.md and find the first chapter marked with `[ ]` in Progress Tracking
2. Read the "Chapter Details" section below for that chapter's topics
3. Read `chapters/assets/style.css` for available CSS classes
4. Read `chapters/index.html` for navigation template
5. Read the previous chapter (if any) for context and smooth transition
6. **WebSearch** for the latest agent frameworks, SDK APIs, patterns, and best practices relevant to the chapter topic
7. Generate the HTML file in `chapters/` with full content (400-600 lines)
8. Update CLAUDE.md — mark the chapter as `[x]`
9. Update `chapters/index.html` — remove `pending` class from that chapter's card
10. Update navigation on the previous chapter if needed

## CSS Classes for Content
- `.architecture-box` — architectural concept or system design explanation (emerald accent, unique to this course)
- `.agent-trace` — step-by-step agent execution trace showing think/tool/result/respond steps (gradient left border, unique to this course)
  - Contains `.trace-step` children with `.trace-label` (variants: `.think`, `.tool`, `.result`, `.respond`)
- `.pattern-box` — reusable design pattern description (cyan accent, unique to this course)
- `.pitfall-box` — common mistake or anti-pattern (red accent, unique to this course)
- `.prompt-example.good` — good examples (green accent)
- `.prompt-example.bad` — bad examples (red accent)
- `.comparison` — side-by-side comparisons
- `.tip-box` — tips and advice
- `.warning-box` — warnings and cautions
- `.exercise-box` — hands-on exercises (amber accent, labeled "Build It")
- `.checklist` — checklists with checkmarks
- `.highlight-box` — key messages (gradient background)
- `.stats-grid` + `.stat-card` — statistics display
- `.tool-card` — tool description cards (icon + name + description)
- `.workflow-steps` + `.step` + `.step-arrow` — visual workflow pipeline
- `.theme-toggle` — theme switch button (in nav)

## Content Guidelines
- **At least one `.architecture-box` per chapter** — explain a system design concept
- **At least one `.agent-trace` per chapter** — show a step-by-step execution trace
- **At least one `.pattern-box` per chapter** — describe a reusable pattern
- **At least one `.exercise-box` per chapter** — give the reader something to build
- **Real code examples in every chapter** — Python preferred, with enough context to be runnable
- Connect every concept to a practical use case the reader might encounter
- Balance theory ("why this pattern exists") with practice ("here's how to implement it")
- Each chapter should end with a brief preview of how this connects to the next chapter

## Chapter Details

### Chapter 1: What Are AI Agents, Really?
**File:** `01-what-are-agents.html`
**Goal:** Cut through the hype — define agents precisely, distinguish them from chatbots and scripts, and explain why they matter now.
**Topics:**
- The agent hype cycle: everyone says "agent" but nobody agrees what it means
- A clear definition: an agent is an LLM that can observe, reason, and act in a loop
- The spectrum: chatbots → copilots → agents → autonomous systems — where each fits
- What makes an agent an agent: the observe-think-act loop (not just API calls)
- Key capabilities: tool use, planning, memory, self-correction
- Why agents became possible in 2024-2025: better models, tool use APIs, function calling
- The agent vs workflow distinction: when you need an agent vs when a simple script suffices
- Real-world agent examples: coding agents (Claude Code, Cursor), research agents, customer support agents
- The risks: hallucination, runaway costs, unintended actions — why agents need guardrails
- The current landscape: who's building what (Anthropic, OpenAI, Google, open-source)
- Analogy: an agent is like an intern with a specific skill set, a task list, and access to tools — you give them a goal, they figure out the steps
- Exercise: Identify 3 tasks in your daily work that could be handled by an agent — what tools would each need?

### Chapter 2: Agent Architectures
**File:** `02-agent-architectures.html`
**Goal:** Map the major architectural patterns for building agents — the reader should know which blueprint to use for their problem.
**Topics:**
- Why architecture matters: the same LLM behaves completely differently depending on how you structure the loop
- Simple tool-use loop: call LLM → check for tool calls → execute tools → feed results back → repeat
- ReAct (Reasoning + Acting): think step by step, then act, then observe results, repeat
- Plan-and-Execute: make a full plan first, then execute steps one by one, re-plan if needed
- Reflexion: agent reviews its own output, identifies errors, and self-corrects
- Tree of Thoughts: explore multiple reasoning paths in parallel, pick the best
- The "router" pattern: a lightweight LLM decides which specialized agent to call
- Comparing architectures: when to use each (complexity vs control vs cost)
- The trade-off triangle: autonomy, reliability, cost — pick two
- Implementing a ReAct loop from scratch in Python (step-by-step code walkthrough)
- The system prompt's role: how the system prompt shapes agent behavior fundamentally
- Analogy: architectures are like management styles — micromanaging (simple loop), delegating with check-ins (ReAct), full project planning (plan-and-execute)
- Exercise: Implement a simple ReAct agent that can answer questions by searching the web and reading pages

### Chapter 3: Tool Design for Agents
**File:** `03-tool-design.html`
**Goal:** Teach the reader to design tools that agents can use reliably — the most underestimated skill in agent building.
**Topics:**
- Why tool design matters more than model selection: a great model with bad tools fails; a good model with great tools succeeds
- Tool anatomy: name, description, parameters (JSON Schema), return format
- The golden rules of tool design: clear names, complete descriptions, typed parameters, predictable outputs
- Writing tool descriptions that LLMs understand: be explicit, include examples, specify edge cases
- Parameter design: required vs optional, enums for constrained choices, sensible defaults
- Return format: structured data vs natural language — when to use each
- Error handling in tools: returning errors the agent can understand and recover from
- Tool granularity: too fine-grained (100 tiny tools) vs too coarse (1 god tool) — finding the sweet spot
- Dangerous tools: file deletion, network requests, database writes — how to make them safe
- Tool composition: building complex capabilities from simple, composable tools
- Testing tools independently before giving them to agents
- MCP (Model Context Protocol): the emerging standard for tool distribution
- Analogy: designing tools for an agent is like designing an API for a junior developer — be explicit, handle errors gracefully, don't assume knowledge
- Exercise: Design a tool set for a "file manager agent" — define 5 tools with full JSON schemas

### Chapter 4: Your First Agent
**File:** `04-first-agent.html`
**Goal:** Walk the reader through building a complete, working agent from scratch — no frameworks, just code.
**Topics:**
- The plan: build a research agent that can search the web, read pages, and summarize findings
- Setting up: API key, Python environment, dependencies (anthropic SDK or openai SDK)
- The tool-use loop in code: the core 20-line loop that powers every agent
- Defining tools: search, read_page, write_summary — with proper JSON schemas
- The system prompt: crafting instructions that guide the agent's behavior
- Running the agent: giving it a research question and watching it work
- Debugging the loop: logging every step (think, tool call, result) for visibility
- Handling edge cases: tool errors, infinite loops, context window limits
- Adding a step limit: preventing runaway execution
- Making it interactive: adding user confirmation before certain actions
- The full working code: a complete, copy-paste-ready agent (~100 lines)
- What you just built vs what frameworks do: understanding the foundation before adding layers
- Exercise: Extend the research agent with a new tool (e.g., `save_to_file`) and test it with 3 different queries

### Chapter 5: Memory & State Management
**File:** `05-memory-state.html`
**Goal:** Explain how agents remember things — the conversation history is not enough.
**Topics:**
- The memory problem: LLMs are stateless, but agents need to remember across steps and sessions
- Three types of agent memory: working memory, short-term (conversation), long-term (persistent)
- Working memory: scratchpad variables the agent uses during a single task
- Short-term memory: the conversation history — how it grows, how to manage it
- Long-term memory: storing and retrieving information across sessions (vector stores, databases, files)
- Context window management: summarization, compression, sliding windows
- The "memory tool" pattern: giving agents explicit tools to save and recall information
- Structured state: tracking task progress, completed steps, intermediate results
- Checkpointing: saving agent state so you can resume interrupted tasks
- Memory and multi-agent systems: sharing state between agents
- When NOT to use memory: keeping agents stateless when possible (simpler, cheaper, more predictable)
- Implementation: adding a simple key-value memory system to your agent
- Analogy: agent memory is like a developer's workflow — you have your current task (working memory), your chat history with colleagues (short-term), and your documentation/notes (long-term)
- Exercise: Add a memory system to your Chapter 4 agent that remembers previous research topics and can reference them

### Chapter 6: Human-in-the-Loop Patterns
**File:** `06-human-in-the-loop.html`
**Goal:** Show how to keep humans in control of agent systems — the most critical pattern for production agents.
**Topics:**
- Why full autonomy is (usually) a bad idea: the cost of mistakes, trust, and liability
- The autonomy spectrum: fully manual → approval gates → supervised autonomy → full autonomy
- Approval gates: requiring human approval before specific actions (destructive operations, external API calls, spending money)
- Implementation: a simple approval system using input() and configurable action lists
- Escalation patterns: when the agent should ask for help vs retry on its own
- Confidence thresholds: the agent rates its own confidence and escalates when uncertain
- The "budget" pattern: giving agents a resource budget (tokens, API calls, time) before requiring check-in
- Audit trails: logging every action for post-hoc review
- Notification patterns: alerting humans to important agent decisions without blocking execution
- The permission model: Claude Code's approach as a case study (allow, deny, auto-approve categories)
- Graceful degradation: what happens when the human doesn't respond?
- Building trust gradually: starting with tight controls and loosening as confidence grows
- Analogy: human-in-the-loop is like the permissions model on your phone — apps can do some things freely, need approval for sensitive actions, and are blocked from others entirely
- Exercise: Add an approval gate to your agent that requires confirmation before any file write or network request

### Chapter 7: Multi-Agent Orchestration
**File:** `07-multi-agent.html`
**Goal:** Teach the reader to design systems where multiple agents collaborate — the key to complex tasks.
**Topics:**
- When one agent isn't enough: task complexity, specialization, and the limits of single agents
- The supervisor pattern: one "manager" agent delegates to specialist agents
- The pipeline pattern: agents in a chain, each processing and passing results to the next
- The swarm pattern: agents collaborate as peers, routing work dynamically
- The debate pattern: multiple agents propose solutions, a judge agent picks the best
- Agent communication: how agents share information (shared memory, message passing, tool calls)
- Implementing a supervisor: code walkthrough of a manager that delegates research, analysis, and writing to specialist agents
- The coordination problem: avoiding duplicate work, handling conflicts, managing shared state
- Cost considerations: multi-agent systems multiply API costs — strategies for efficiency
- When to use multi-agent vs single agent with multiple tools: the decision framework
- Real-world examples: code review (linter agent + security agent + style agent), content creation (researcher + writer + editor)
- The "agent as tool" pattern: wrapping an entire agent as a tool for another agent
- Analogy: multi-agent orchestration is like a software team — you have a tech lead (supervisor), frontend and backend specialists (workers), and they coordinate through standups and shared docs (message passing)
- Exercise: Build a 2-agent system: a "researcher" agent that gathers information and a "writer" agent that synthesizes it into a summary

### Chapter 8: Error Handling & Recovery
**File:** `08-error-recovery.html`
**Goal:** Make agents robust — because in production, everything that can fail will fail.
**Topics:**
- Why agent failures are different from software bugs: non-deterministic, context-dependent, hard to reproduce
- Categories of agent failure: tool errors, LLM errors (hallucination, refusal, format violations), timeout, cost overrun
- Retry strategies: simple retry, exponential backoff, retry with modified prompt
- Fallback patterns: try tool A, if it fails try tool B, if both fail escalate to human
- Self-correction: the agent detects its own mistakes and tries again with new approach
- Guardrails: output validation, format checking, sanity checks before acting
- The "pre-flight check" pattern: validating conditions before executing a plan
- Circuit breakers: stopping the agent when error rate exceeds a threshold
- Timeout management: per-tool timeouts, per-task timeouts, total execution budgets
- Structured error messages: designing error returns that help agents recover
- Logging and observability: what to log, how to trace agent execution, debugging tools
- Dead letter queues: handling tasks that repeatedly fail
- Analogy: error handling in agents is like error handling in distributed systems — you need retries, circuit breakers, fallbacks, and monitoring, because no single step is guaranteed to succeed
- Exercise: Add comprehensive error handling to your agent — retry on tool failure, self-correct on format errors, escalate after 3 failed attempts

### Chapter 9: Agent Evaluation & Testing
**File:** `09-evaluation.html`
**Goal:** Answer the hardest question in agent development: "How do I know if my agent is good?"
**Topics:**
- The evaluation problem: traditional tests don't work for non-deterministic systems
- What to measure: task completion rate, accuracy, efficiency (steps taken, tokens used), cost per task
- End-to-end evaluation: running the agent on a test suite of tasks and measuring outcomes
- Step-level evaluation: checking individual decisions (did it pick the right tool? right parameters?)
- The "golden trajectory" approach: comparing agent's execution path to an expert's ideal path
- Benchmark suites: SWE-bench, GAIA, WebArena — existing benchmarks and what they test
- Building your own evaluation set: creating domain-specific test cases
- Regression testing: ensuring improvements don't break existing capabilities
- A/B testing agents: comparing agent versions on the same tasks
- Human evaluation: when you need human judges and how to structure the evaluation
- Evaluation-driven development: writing evals before building the agent (like TDD for agents)
- Cost vs quality tradeoffs: cheaper models with more steps vs expensive models with fewer steps
- Analogy: evaluating agents is like evaluating employees — you don't just check if they finished the task, you look at quality, efficiency, and whether they followed the right process
- Exercise: Create an evaluation suite for your research agent — 10 test queries with expected outcomes, and score the agent's performance

### Chapter 10: Agent Frameworks & SDKs
**File:** `10-agent-frameworks.html`
**Goal:** Survey the major frameworks so the reader can pick the right tool for their project.
**Topics:**
- Why frameworks exist: abstractions over the tool-use loop, built-in patterns, ecosystem benefits
- Claude Agent SDK (Anthropic): design philosophy, key features, when to use it
- OpenAI Agents SDK: handoffs, guardrails, tracing — the OpenAI approach
- LangGraph: graph-based agent workflows, state machines, persistence
- CrewAI: role-based multi-agent systems, task delegation
- AutoGen: Microsoft's conversational multi-agent framework
- Comparison table: features, maturity, community, learning curve, lock-in risk
- Framework vs no framework: when a framework helps vs when it adds unnecessary complexity
- The abstraction trap: frameworks that hide too much, making debugging impossible
- Migration: moving between frameworks, extracting your agent from a framework
- Building a simple agent in each framework: side-by-side code comparison (same task, different implementations)
- Choosing a framework: decision matrix based on your requirements
- Analogy: agent frameworks are like web frameworks — you CAN build everything from scratch with raw HTTP, but Django/Express/Rails give you patterns, conventions, and ecosystem. The question is always: do the abstractions match YOUR problem?
- Exercise: Implement the same agent in two frameworks (e.g., Claude Agent SDK and LangGraph) and compare the developer experience

### Chapter 11: Production Deployment
**File:** `11-production.html`
**Goal:** Bridge the gap between "it works on my laptop" and "it works in production at scale."
**Topics:**
- The production gap: why agents that work in development fail in production
- Cost management: token budgets, model selection per step, caching, prompt optimization
- Latency optimization: parallel tool calls, streaming, async execution, model selection for speed
- Scaling strategies: horizontal scaling, task queues, concurrent agent execution
- Observability: structured logging, tracing agent execution, dashboards and alerts
- Security: prompt injection defense, tool access control, data sanitization, API key management
- Rate limiting: handling API rate limits gracefully across multiple agents
- Persistence: storing agent state, conversation history, and results durably
- Deployment patterns: serverless functions, long-running workers, webhook-driven agents
- CI/CD for agents: testing agents in CI, staging environments, gradual rollout
- Monitoring in production: tracking success rates, costs, latency, error patterns over time
- The operations playbook: incident response for agent failures
- Analogy: deploying agents to production is like deploying microservices — you need monitoring, scaling, error handling, and a clear understanding of failure modes. The difference is that your "service" makes non-deterministic decisions
- Exercise: Create a deployment checklist for your agent — cover cost limits, error handling, monitoring, security, and rollback procedures

### Chapter 12: Building a Real Agent System
**File:** `12-capstone.html`
**Goal:** Capstone project — design, build, and prepare for deployment a multi-agent system that solves a real problem.
**Topics:**
- Choosing the project: a "code review agent system" with multiple specialized agents
- System design: architecture diagram, agent roles, communication patterns, tool definitions
- The Planning Agent: analyzes a PR and creates a review plan (what to check, in what order)
- The Security Agent: scans for vulnerabilities, injection risks, auth issues
- The Style Agent: checks coding standards, naming conventions, best practices
- The Orchestrator: coordinates agents, merges results, resolves conflicts, produces final review
- Implementation walkthrough: building each agent step by step
- Connecting the agents: the supervisor pattern in practice
- Adding human-in-the-loop: the reviewer approves/rejects agent findings before posting
- Error handling: what happens when one agent fails? Partial results vs full retry
- Evaluation: testing the system on real PRs, measuring precision and recall of findings
- Production readiness: cost estimation, latency budget, deployment plan
- Lessons learned: what worked, what was harder than expected, what you'd do differently
- The agent builder's mindset: key principles for your next agent project
- Exercise: Deploy your code review agent system on a real repository and run it against your last 5 PRs

### Chapter 13: Managed Agents — Deploy on Anthropic's Infrastructure
**File:** `13-managed-agents.html`
**Goal:** Teach the reader to deploy agents on Anthropic's Managed Agents infrastructure — the fastest path from agent code to production without managing servers.
**Topics:**
- The deployment problem revisited: Chapter 11 covered self-hosted — Managed Agents is the managed alternative
- What Managed Agents provides: a pre-built agent harness (model + tools + environment) running in Anthropic's cloud
- Architecture deep dive: Agent (configuration), Environment (container template), Session (running instance), Events (SSE messages)
- How Managed Agents compares to building your own harness: what you give up (customization) vs what you gain (zero infrastructure)
- Creating an Agent via the API: model selection, system prompt, tool configuration, MCP server attachment
- Environment configuration: specifying packages, network access, file mounts — building your agent's container template
- Starting Sessions: sending tasks, streaming Events via SSE, handling the event lifecycle
- Built-in tools: Bash execution, file operations, web search, web fetch — the tool set your agent gets for free
- The API in practice: Python/TypeScript SDK usage, the beta header, error handling
- Connecting MCP servers: extending your Managed Agent with custom tools via MCP
- Multi-agent preview: orchestrating multiple Managed Agents, the supervisor pattern on managed infrastructure
- Memory and Outcomes previews: persistent memory across sessions, tracking task success/failure
- When to use Managed Agents vs self-hosted: decision framework (task duration, customization, cost, compliance)
- Analogy: Managed Agents is to self-hosted agents what Heroku was to AWS EC2
- Exercise: Take the research agent from Chapter 4 and deploy it as a Managed Agent — compare the implementation effort
