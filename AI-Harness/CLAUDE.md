# AI Harness Engineering: What's Really Running Your AI Tools

## Project Description
An HTML guide in English for developers who use AI coding tools (Claude Code, Cursor, Codex, Windsurf) daily but have no idea what's happening behind the scenes. The target audience is developers who know how to prompt AI but don't understand the infrastructure that wraps the LLM — the system prompts, tool registries, context management, memory systems, and guardrails that make these tools actually useful.

This course is **completely standalone** — no prerequisites, no references to other courses. If a concept needs explaining (tokens, context windows, etc.), it gets explained here in the context of harness engineering.

The style is **"For Dummies"** — friendly, approachable, heavy on analogies and "peek behind the curtain" moments. The reader is smart (they're a developer) but has never thought about what happens between their prompt and the LLM's response. No math. No academic tone. Like a senior engineer showing you around the engine room.

## Language Rules
- All content is in **English**
- Tone: friendly, conversational, like a colleague showing you the internals over coffee
- Use analogies from everyday life and software development
- **No math formulas** — explain everything through intuition, diagrams described in words, and analogies
- Address: second person singular (you)
- When introducing a component, always answer: "OK, but what does this actually do when I use Claude Code / Cursor / ChatGPT?"
- Light humor is welcome — keep it engaging, not dry
- Use short paragraphs — walls of text kill understanding
- Code examples should be **configuration snippets** (JSON, YAML, markdown, shell commands), NOT Python — this course is about configuring and understanding harnesses, not building ML pipelines

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
AI-Harness/
  CLAUDE.md                              — This file
  .claude/
    commands/
      generate-next-chapter.md           — Skill for chapter generation
  chapters/
    index.html                           — Landing page with navigation
    assets/
      style.css                          — Shared CSS with dark/light theme
    01-what-is-a-harness.html            — What Is a Harness?
    02-anatomy-of-a-harness.html         — The Anatomy of a Harness
    03-context-engineering.html          — Context Engineering
    04-tools-and-tool-use.html           — Tools and Tool Use
    05-memory-and-state.html             — Memory and State
    06-claude-code-under-the-hood.html   — Claude Code Under the Hood
    07-codex-cursor-windsurf.html        — Codex, Cursor, and Windsurf
    08-browser-apps.html                 — Browser Apps: ChatGPT and Claude.ai
    09-harness-engineering-in-practice.html — Harness Engineering in Practice
    10-building-your-own.html            — Building Your Own
    11-context-and-planning.html         — Plan Mode & Context Strategy
```

## Progress Tracking
- [x] Chapter 1: What Is a Harness?
- [x] Chapter 2: The Anatomy of a Harness
- [x] Chapter 3: Context Engineering
- [x] Chapter 4: Tools and Tool Use
- [x] Chapter 5: Memory and State
- [x] Chapter 6: Claude Code Under the Hood
- [x] Chapter 7: Codex, Cursor, and Windsurf
- [x] Chapter 8: Browser Apps: ChatGPT and Claude.ai
- [x] Chapter 9: Harness Engineering in Practice
- [x] Chapter 10: Building Your Own
- [x] Chapter 11: Plan Mode & Context Strategy

## Instructions for /generate-next-chapter
When the user invokes `/generate-next-chapter`:
1. Read this CLAUDE.md and find the first chapter marked with `[ ]` in Progress Tracking
2. Read the "Chapter Details" section below for that chapter's topics
3. Read `chapters/assets/style.css` for available CSS classes
4. Read `chapters/index.html` for navigation template
5. Read the previous chapter (if any) for context and smooth transition
6. **Research the topic**: Search the web for the latest information on the chapter's topics — check Anthropic docs, OpenAI docs, Cursor blog, Martin Fowler articles, and recent Medium posts on harness engineering
7. Generate the HTML file in `chapters/` with full content (400-600 lines)
8. Update CLAUDE.md — mark the chapter as `[x]`
9. Update `chapters/index.html` — remove `pending` class from that chapter's card
10. Update navigation on the previous chapter if needed

## CSS Classes for Content
- `.inside-look-box` — "Inside the Harness" peek behind the curtain (amber accent, unique to this course)
- `.compare-box` — Two-column tool comparison grid (unique to this course)
  - Contains `.compare-item` children with `.compare-title` headers
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
- **Every chapter MUST include at least one `.inside-look-box`** showing what happens internally when a user performs an action — this is the signature element of the course, making the invisible visible
- **Chapters 3, 4, 5, 7, and 8 MUST include at least one `.compare-box`** comparing how different tools handle the same concept
- **At least one `.exercise-box` per chapter** with a practical, hands-on task
- **At least one analogy per chapter** woven into the prose — use familiar concepts (OS, kitchen, suitcase, smartphone) to explain harness concepts
- Code examples should be config snippets (JSON, YAML, markdown, shell), not Python
- When explaining a concept, show how it manifests in at least two different tools
- Always connect back to the reader's experience: "When you type X in Claude Code, here's what actually happens..."
- Each chapter should end with a brief preview connecting to the next chapter
- Short paragraphs — maximum 3-4 sentences per paragraph
- Be opinionated: recommend, don't just list features

## Key References for Research
When generating chapters, search the web for the latest information. Key sources:
- Anthropic: anthropic.com/engineering/effective-harnesses-for-long-running-agents
- OpenAI: openai.com/index/unlocking-the-codex-harness/
- Cursor: cursor.com/blog/codex-model-harness
- Martin Fowler: martinfowler.com/articles/exploring-gen-ai/harness-engineering.html
- ArXiv paper: 2603.05344 (Building Effective AI Coding Agents for the Terminal)
- LangChain: blog.langchain.com/the-anatomy-of-an-agent-harness/
- Medium articles on harness engineering (2025-2026)

## Chapter Details

### Chapter 1: What Is a Harness?
**File:** `01-what-is-a-harness.html`
**Goal:** The "aha" introduction. The reader should walk away understanding that the harness is everything between them and the LLM.
**Topics:**
- You already use harnesses every day — you just never noticed
- The raw LLM: what happens when you call a model API with nothing else (it's underwhelming)
- The harness defined: the complete software infrastructure that wraps the LLM
- Core analogy: the harness is to an LLM what an operating system is to a CPU — the CPU does math, but the OS makes it useful
- Second analogy: a race car driver (LLM) vs the pit crew, track, rules, radio (harness)
- Why "prompt engineering" is only one small piece — the real game is harness engineering
- The 2025-2026 realization: harness improvements often beat model improvements
- Quick preview: the six components of a harness (system prompt, tools, context, memory, guardrails, persistence)
- Where you'll see harnesses: Claude Code, ChatGPT, Cursor, Windsurf, Codex
- Inside the Harness: what happens between you pressing Enter and seeing a response
- Exercise: Call a raw LLM API vs use ChatGPT for the same question — list everything ChatGPT does that the raw API doesn't

### Chapter 2: The Anatomy of a Harness
**File:** `02-anatomy-of-a-harness.html`
**Goal:** Break down the six core components so the reader has a mental model of the whole architecture.
**Topics:**
- Component 1: System Prompt / Scaffolding — the instructions the user never sees
- Component 2: Tool Integration Layer — giving the LLM hands (file read, web search, code execution)
- Component 3: Context Engineering — curating what information reaches the model
- Component 4: Memory and State Management — working memory, session state, long-term recall
- Component 5: Verification and Guardrails — permission boundaries, output validation, safety rails
- Component 6: Session Persistence — saving progress, resuming work, handoff between sessions
- How the components work together: the request lifecycle from user input to final output
- Analogy: a restaurant kitchen — the chef (LLM), the recipe book (system prompt), the ingredient prep (context), the sous chefs (tools), the health inspector (guardrails), the reservation book (persistence)
- Not all harnesses have all six components — simpler apps skip some
- Inside the Harness: walk through what happens when you say "refactor this function" in Claude Code
- Exercise: Pick an AI tool you use daily and identify which of the six components you can observe

### Chapter 3: Context Engineering
**File:** `03-context-engineering.html`
**Goal:** Teach how the right information gets into the context window — the most critical harness job.
**Topics:**
- The context window is prime real estate — every token counts
- What goes into a context window: system prompt + conversation + retrieved info + tool results
- The curation problem: the codebase is 500K lines, the window is 200K tokens — what do you pick?
- System reminders: injected instructions that appear at intervals (not just at the start)
- CLAUDE.md and AGENTS.md: persistent project context files the harness reads automatically
- Retrieval strategies: keyword search, semantic search, file-tree heuristics
- Context compaction: summarizing older conversation turns to free up space
- The "lost in the middle" problem: models pay less attention to the middle of long contexts
- Hashline technique (2026): how formatting changes alone dramatically improved coding success
- Analogy: context engineering is like packing a suitcase — you can't take everything, so you pick what matters most for THIS trip
- Compare: how Claude Code, Cursor, and Codex each solve context curation differently
- Inside the Harness: what Claude Code puts into the context window when you open a project
- Exercise: Open CLAUDE.md (or create one) and design context that would help an AI understand your project

### Chapter 4: Tools and Tool Use
**File:** `04-tools-and-tool-use.html`
**Goal:** Explain how LLMs call functions — the mechanism that turns a text generator into an agent.
**Topics:**
- LLMs can't do anything except generate text — tools are how they act on the world
- What tool use actually is: the model outputs a structured request, the harness executes it, the result goes back
- Tool schemas: how the harness tells the model what tools exist (name, description, parameters)
- The tool use loop: model decides to call a tool → harness validates → executes → returns result → model continues
- Categories of tools: file system, terminal, web search, code execution, API calls
- Tool selection: how the model picks which tool to use (it's just another text generation decision)
- Parallel tool calls: some harnesses let the model request multiple tools at once
- Deferred tool loading: registering hundreds of tools without overwhelming the context
- MCP (Model Context Protocol): a standard for connecting tools across different harnesses
- Analogy: tools are like apps on a smartphone — the phone (LLM) can do basic things alone, but apps (tools) make it truly useful
- Compare: tool registries in Claude Code (built-in + MCP) vs Cursor (15+ specialized tools) vs Codex (JSON-RPC)
- Inside the Harness: a step-by-step trace of Claude Code reading a file, editing it, and running tests
- Exercise: List 10 actions your AI coding tool can perform — now categorize them by tool type

### Chapter 5: Memory and State
**File:** `05-memory-and-state.html`
**Goal:** Explain the different layers of memory in a harness and how they create the illusion of continuity.
**Topics:**
- The fundamental truth: LLMs have no memory — every request starts from zero
- Working memory: the conversation in the current context window
- Session state: what the harness tracks between tool calls within a single session
- Cross-session memory: how some tools remember things across separate conversations
- The memory hierarchy: working context (tokens) → session state (harness variables) → persistent memory (files/DB)
- How chat apps fake memory: appending the entire conversation history with every request
- How coding tools use the filesystem AS memory: writing plans, notes, CLAUDE.md updates
- Git-based session handoff: committing progress so a new session can pick up where the last left off
- Memory in Windsurf's Cascade: persistent agentic architecture that carries context forward
- The compaction challenge: when conversations grow too long, what gets summarized and what gets dropped
- Analogy: memory layers are like a desk (working memory), filing cabinet (session state), and warehouse archive (persistent storage)
- Compare: how Claude Code, Cursor, and ChatGPT each handle memory differently
- Inside the Harness: what happens to your conversation when you hit the context limit
- Exercise: Start a long conversation with an AI tool, then reference something from the very beginning — observe when and how it "forgets"

### Chapter 6: Claude Code Under the Hood
**File:** `06-claude-code-under-the-hood.html`
**Goal:** Deep dive into Claude Code's harness as a case study of a sophisticated agent harness.
**Topics:**
- Claude Code architecture overview: CLI agent with tool loop
- The system prompt: what Claude Code tells the model before you say anything
- CLAUDE.md hierarchy: global → project → directory-level instructions
- Tool registry: file read/write, bash, web search, MCP tools, and how they're registered
- The agent loop: plan → act → observe → repeat
- Permission system: allowlists, auto-approve patterns, and the trust spectrum
- Hooks system: pre-tool and post-tool execution callbacks for custom logic
- Context management: how Claude Code decides what files to include
- Compaction: automatic summarization when context fills up
- Dual-agent pattern: initializer agent that spawns worker sub-agents for complex tasks
- Plan mode and worktrees: structured approaches for large changes
- Settings layers: global config, project config, command-line flags
- The Claude Agent SDK: the general-purpose harness framework behind Claude Code
- Inside the Harness: complete trace of "add a login page with tests" from prompt to committed code
- Exercise: Run `claude --help` and explore the configuration options — identify harness components you now recognize

### Chapter 7: Codex, Cursor, and Windsurf
**File:** `07-codex-cursor-windsurf.html`
**Goal:** Show how three other major tools build their harnesses differently, solving the same fundamental problems.
**Topics:**
- OpenAI Codex:
  - Agent loop architecture: items, turns, threads
  - Codex App Server with JSON-RPC communication
  - AGENTS.md and progressive disclosure of context
  - Repository optimization for agent consumption
  - Sandboxed execution environment
- Cursor:
  - Model-specific harness tuning per frontier model
  - 15+ specialized tools including semantic code search
  - Subagents for parallel work
  - MCP integration for extensibility
  - Cursor Bench: internal evaluation suite for harness quality
  - Background agents
- Windsurf (Cascade):
  - Persistent agentic architecture vs stateless
  - Code mode vs Chat mode: different harness configurations
  - Built-in planning agent + execution model
  - SWE-1.5: a model trained together with its harness via reinforcement learning
  - Flows and context awareness
- Compare: side-by-side comparison of how each handles the six harness components
- Inside the Harness: same coding task, three different harness approaches
- Exercise: If you have access to two or more of these tools, give them the same coding task and observe the differences

### Chapter 8: Browser Apps — ChatGPT and Claude.ai
**File:** `08-browser-apps.html`
**Goal:** Show that browser chat apps are simpler harnesses built on the same principles.
**Topics:**
- Browser apps are harnesses too — just simpler ones
- ChatGPT's harness: system prompt + tools (web search, code interpreter, DALL-E, file upload)
- Claude.ai's harness: system prompt + artifacts + analysis tool + web search
- Custom GPTs and Projects: user-configurable mini-harnesses
- What browser apps lack compared to coding tools: no filesystem, no terminal, no git
- Why this matters: understanding the harness explains why ChatGPT is great for chat but mediocre for coding
- The tool evolution: how ChatGPT went from text-only to multi-tool in 2 years
- Memory features: how ChatGPT's "memory" works (harness-level persistence, not model-level)
- System prompts in the wild: leaked system prompts reveal harness decisions
- The simplicity advantage: fewer components means fewer failure modes
- Analogy: browser apps are like Swiss Army knives (versatile, portable, limited), coding tools are like a full workshop (specialized, powerful, complex)
- Compare: ChatGPT vs Claude.ai vs Gemini — harness differences that explain capability differences
- Inside the Harness: what actually happens when ChatGPT "browses the web" for you
- Exercise: Ask ChatGPT or Claude.ai to do something that requires a tool it doesn't have — observe how it fails gracefully (or not)

### Chapter 9: Harness Engineering in Practice
**File:** `09-harness-engineering-in-practice.html`
**Goal:** Show real-world harness engineering techniques and results from 2025-2026.
**Topics:**
- The industry realization: harness engineering delivers more improvement than model training for most coding tasks
- Hashline technique: format changes (adding line numbers, structured delimiters) dramatically improved LLM code editing success
- Stripe's Minions: how harness engineering at scale produced 1,300 AI PRs per week
- The eval-driven approach: measure harness changes like you measure code changes
- SWE-Bench and Cursor Bench: standardized tests for harness quality
- Harness tuning techniques:
  - System prompt iteration: test different instructions, measure success rates
  - Tool design: better tool descriptions improve tool selection accuracy
  - Context curation: what you exclude matters as much as what you include
  - Output format control: structured outputs reduce parsing errors
- Model-harness co-design: Windsurf's approach of training the model and harness together
- The "boring" improvements that work: better error messages, clearer tool descriptions, smarter defaults
- Anti-patterns: over-prompting, tool sprawl, context stuffing, ignoring verification
- Inside the Harness: before and after of a harness improvement — same model, same task, different success rate
- Exercise: Take one AI coding task you do regularly and design a harness improvement (better CLAUDE.md section, custom command, or workflow change)

### Chapter 10: Building Your Own
**File:** `10-building-your-own.html`
**Goal:** Practical guide to customizing and extending harnesses you already use.
**Topics:**
- You don't need to build a harness from scratch — you're already customizing one
- CLAUDE.md deep dive: writing effective project instructions, directory-level overrides, what to include and what to skip
- AGENTS.md: progressive disclosure for OpenAI tools
- Custom commands: creating reusable workflows in `.claude/commands/`
- Hooks: pre-tool and post-tool execution for custom validation and automation
- MCP servers: extending your harness with custom tools (database access, API integration, specialized search)
- Permission configuration: tuning the trust spectrum for your workflow
- The Claude Agent SDK: building custom agent applications with harness infrastructure
- Configuration layers: global settings, project settings, session overrides
- When to build from scratch vs extend: most developers should extend, few should build
- The minimal viable harness: system prompt + one tool + context curation
- Putting it all together: designing a complete harness configuration for a real project
- What's next: the future of harness engineering (autonomous agents, self-improving harnesses, standardization)
- Inside the Harness: your project before and after proper harness configuration
- Exercise: Create a complete CLAUDE.md, one custom command, and one hook for your current project — compare results before and after

### Chapter 11: Plan Mode & Context Strategy
**File:** `11-context-and-planning.html`
**Goal:** Teach practical decision-making about plan mode and /clear as harness engineering tools.
**Topics:**
- Real-world scenario: generating 10 chapters sequentially — the plan/clear dilemma
- Plan mode as a constraint mechanism: the harness swaps the tool registry to read-only
- When plan mode earns its keep (complex changes, unfamiliar codebases, 3+ file changes)
- When plan mode is overhead (repetitive tasks, clear patterns, well-defined commands)
- What /clear actually does: full context reset, new session created, CLAUDE.md reloaded
- /clear vs /compact: nuclear reset vs lossy surgical summary
- The prompt cache and its 5-minute TTL — timing your clears for cache efficiency
- Context as asset (consistency, cross-references, conventions) vs liability (noise, attention decay, cost)
- Token economics: carrying context vs re-discovering it — the break-even question
- Decision framework: practical guide for when to plan, when to clear, when to compact
- The ten-chapter playbook: staged context management for sequential generation
- What gets lost on /clear and how to protect it (write to CLAUDE.md before clearing)
- Inside the Harness: before and after /clear — context window at chapter 10 vs fresh start
- Exercise: Audit your own context strategy on a multi-step task
