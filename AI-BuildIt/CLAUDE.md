# Build It With AI For Dummies

## Project Description
An HTML guide in English for developers who use Claude Code daily and want **concrete project ideas** to build. This is NOT a theory course — every chapter is packed with 3-5 actionable project ideas across different domains, complete with difficulty ratings, tech stacks, and enough detail to start building immediately.

The target audience is developers (comfortable with terminals, APIs, and Claude Code) who are technically capable but stuck asking "what should I build?" They want inspiration, not lectures.

The style is **"For Dummies"** — friendly, approachable, like an excited friend pitching project ideas at a hackathon. Every paragraph should make the reader want to open their terminal.

## Language Rules
- All content is in **English**
- Tone: energetic, action-oriented, like a friend excitedly pitching project ideas over coffee
- Use analogies from building and making things to explain concepts
- Address: second person singular (you)
- When introducing a project idea, lead with what it DOES and why it's COOL
- Light humor is welcome — keep it engaging
- Use short paragraphs — walls of text kill momentum
- Focus on concrete, buildable projects — not abstract theory

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
AI-BuildIt/
  CLAUDE.md                              — This file
  .claude/
    commands/
      generate-next-chapter.md           — Skill for chapter generation
  chapters/
    index.html                           — Landing page with navigation
    assets/
      style.css                          — Shared CSS with dark/light theme (hot pink/rose + cyan scheme)
    01-cli-tools.html                    — CLI Tools That Think
    02-dev-productivity.html             — Developer Productivity Tools
    03-code-generation.html              — Code Generation & Scaffolding
    04-data-tools.html                   — Data Wrangling & Analysis Tools
    05-knowledge-search.html             — Knowledge Base & Search Projects
    06-monitoring-dashboards.html        — Monitoring & Analytics Dashboards
    07-web-apps.html                     — Web Apps With AI Superpowers
    08-api-microservices.html            — API Design & Microservices
    09-bots-conversational.html          — Bots & Conversational Interfaces
    10-workflow-automation.html          — Workflow Automation & Integrations
    11-creative-projects.html            — Creative & Generative Projects
    12-launchpad.html                    — Your AI Project Launchpad
```

## Progress Tracking
- [x] Chapter 1: CLI Tools That Think
- [x] Chapter 2: Developer Productivity Tools
- [x] Chapter 3: Code Generation & Scaffolding
- [x] Chapter 4: Data Wrangling & Analysis Tools
- [x] Chapter 5: Knowledge Base & Search Projects
- [x] Chapter 6: Monitoring & Analytics Dashboards
- [x] Chapter 7: Web Apps With AI Superpowers
- [x] Chapter 8: API Design & Microservices
- [x] Chapter 9: Bots & Conversational Interfaces
- [x] Chapter 10: Workflow Automation & Integrations
- [x] Chapter 11: Creative & Generative Projects
- [x] Chapter 12: Your AI Project Launchpad

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
- `.project-card` — project idea callout box (pink border) with `.project-name`, `.project-difficulty` (.weekend/.week/.month), `.stack-pills` with `.pill` children, and `.project-desc` (unique to this course)
- `.spark-box` — "Inspiration Spark" callout for expansion ideas (cyan accent, unique to this course)
- `.stack-pills` — horizontal row of tech stack pill badges with `.pill` children (unique to this course)
- `.prompt-example.good` — good examples (green accent)
- `.prompt-example.bad` — bad examples (red accent)
- `.comparison` — side-by-side comparisons
- `.tip-box` — tips and advice
- `.warning-box` — warnings and cautions
- `.exercise-box` — "Start Building" hands-on exercises (cyan accent)
- `.checklist` — checklists with checkmarks
- `.highlight-box` — key messages (gradient background)
- `.stats-grid` + `.stat-card` — statistics display
- `.tool-card` — tool description cards (icon + name + description)
- `.workflow-steps` + `.step` + `.step-arrow` — visual workflow pipeline
- `.theme-toggle` — theme switch button (in nav)

## Content Guidelines
- **At least 3 `.project-card` boxes per chapter** — each with a project name, difficulty badge, tech stack pills, and 2-3 sentence pitch
- **At least 1 `.spark-box` per chapter** — "what if you also..." expansion ideas
- **At least 1 `.exercise-box` per chapter** — "Start Building" hands-on task to get started immediately
- Every project idea must include: what it does, why it's useful, what tech stack to use, and difficulty (Weekend / Week / Month)
- No abstract theory without a concrete project attached
- Each chapter ends with a "Pick Your Project" section encouraging the reader to choose one idea and start
- All examples assume Claude Code / Claude API as the AI backbone
- Use `.stack-pills` inside `.project-card` to show technologies

## Chapter Details

### Chapter 1: CLI Tools That Think
**File:** `01-cli-tools.html`
**Goal:** Inspire the reader to build AI-powered command-line tools that understand natural language and automate terminal workflows.
**Topics:**
- Why the CLI is the perfect home for AI: fast, scriptable, composable, pipe-friendly
- The anatomy of an AI CLI tool: input parsing, LLM call, structured output, action
- Project: **Smart Git Companion** — translates "show me what changed in auth last week" into the right git commands (Weekend, Python/TypeScript)
- Project: **Log Detective** — pipe any log file in, get root cause analysis and fix suggestions (Weekend, Python)
- Project: **Config Generator** — describe what you want in English, get nginx/Docker/K8s/Gradle configs (Weekend, Python)
- Project: **Smart File Organizer** — point at a messy directory, AI renames and sorts by content analysis (Weekend, Python)
- Project: **Terminal Translator** — type what you want to do in English, get the exact bash command with --explain flag (Weekend, Python/TypeScript)
- How to distribute your CLI tool: pip, npm, homebrew tap
- The composability advantage: piping AI tools together
- Performance tips: streaming responses, caching, local models for speed
- Spark: combine all five into a unified AI terminal assistant
- Exercise: build the Terminal Translator in 30 minutes with Claude Code

### Chapter 2: Developer Productivity Tools
**File:** `02-dev-productivity.html`
**Goal:** Build tools that automate the tedious non-coding parts of software development.
**Topics:**
- The hidden time sink: developers spend 30-40% of time NOT writing code
- Project: **PR Description Generator** — reads git diff, writes detailed PR descriptions with summary, motivation, and test notes (Weekend, Python/TypeScript)
- Project: **Code Review Prep Tool** — analyzes a PR before you review: summarizes changes, flags issues, identifies missing tests (Week, TypeScript)
- Project: **Meeting Notes to Tickets** — takes meeting notes or transcripts, extracts action items, creates structured tickets with acceptance criteria (Weekend, Python)
- Project: **Documentation Autopilot** — scans codebase for undocumented public APIs, generates docs, README sections, and usage examples (Week, Python/TypeScript)
- Project: **Dependency Auditor** — analyzes project dependencies, explains each, flags outdated/vulnerable ones, suggests lighter alternatives (Weekend, Python)
- Integrating with existing workflows: git hooks, CI/CD, IDE extensions
- The "review before commit" pattern: AI checks your work before it ships
- Building VS Code extensions with AI backends
- Spark: chain PR Generator + Code Review + Docs into a complete "code quality pipeline"
- Exercise: build the PR Description Generator and hook it into your workflow

### Chapter 3: Code Generation & Scaffolding
**File:** `03-code-generation.html`
**Goal:** Build tools that generate boilerplate, scaffolds, and production-ready starter code from natural language descriptions.
**Topics:**
- Why scaffolding matters: the first 2 hours of every feature are the most boring
- Project: **API Endpoint Generator** — describe an API in English, get full endpoint code, tests, and OpenAPI spec (Week, Python/TypeScript)
- Project: **Android Feature Scaffolder** — describe a feature, get Fragment, ViewModel, XML layouts, navigation graph, and tests (Week, Kotlin)
- Project: **Database Schema Designer** — describe your data model in English, get schema with migrations, model classes, and seed data (Weekend, Python)
- Project: **Test Suite Generator** — point at a class, get comprehensive unit tests, edge cases, and integration stubs (Weekend, Python/TypeScript)
- Project: **Component Library Builder** — describe UI components, get React/Compose components with props, stories, and tests (Week, TypeScript/Kotlin)
- Template engines: how to make generated code match YOUR project's conventions
- The validation loop: generating, testing, and refining in one pass
- Project customization: teaching the generator your team's patterns
- Spark: build a "project bootstrap" that generates entire project skeletons from a one-paragraph description
- Exercise: build the Database Schema Designer and generate a schema for a recipe app

### Chapter 4: Data Wrangling & Analysis Tools
**File:** `04-data-tools.html`
**Goal:** Build tools that make working with data conversational instead of requiring pandas/SQL expertise.
**Topics:**
- The data accessibility problem: everyone has data, few can query it
- Project: **CSV Whisperer** — chat with any CSV file using natural language questions, get answers and charts (Weekend, Python)
- Project: **Data Cleaner** — feed messy data, describe "clean," get duplicates removed, formats fixed, gaps filled (Weekend, Python)
- Project: **JSON/XML Transformer** — convert complex nested data structures through conversation (Weekend, Python)
- Project: **SQL Query Builder** — describe what you want in English, get SQL, optionally run it and explain results (Weekend, Python)
- Project: **Spreadsheet Automator** — reads Google Sheets/Excel, performs complex analysis via natural language, writes results back (Week, Python)
- Visualization: generating charts from data descriptions
- The safety layer: previewing destructive operations before executing
- Handling large datasets: chunking, streaming, and summarization strategies
- Spark: combine CSV Whisperer + SQL Builder into a universal "talk to your data" tool
- Exercise: build the CSV Whisperer and analyze a real dataset in 20 minutes

### Chapter 5: Knowledge Base & Search Projects
**File:** `05-knowledge-search.html`
**Goal:** Build systems that make information findable and useful using embeddings, RAG, and semantic search.
**Topics:**
- Why keyword search fails: "that article about memory leaks" has no keyword match
- Embeddings in 60 seconds: turning text into searchable vectors
- Project: **Personal Knowledge Vault** — index notes, bookmarks, and highlights; search semantically across everything (Week, Python)
- Project: **Codebase Q&A Bot** — index an entire codebase, ask "how does auth work?" and get answers with file references (Week, Python/TypeScript)
- Project: **Team FAQ Generator** — monitors Slack/Teams, identifies repeated questions, auto-generates FAQ with sourced answers (Month, Python)
- Project: **Documentation Search Engine** — index multiple doc sources into one searchable interface (Week, Python)
- Project: **Bookmark Intelligence** — turns browser bookmarks into a living knowledge base with summaries and semantic search (Weekend, Python)
- Choosing a vector database: Chroma, Qdrant, Pinecone, or just SQLite with embeddings
- Chunking strategies: how to split documents for best retrieval
- The RAG pattern: retrieve, augment, generate
- Spark: add a chat interface to your Knowledge Vault for conversational search
- Exercise: build Bookmark Intelligence and search your own bookmarks semantically

### Chapter 6: Monitoring & Analytics Dashboards
**File:** `06-monitoring-dashboards.html`
**Goal:** Build dashboards that don't just show data but explain what it means and suggest what to do.
**Topics:**
- The dashboard problem: 90% of dashboards are looked at once and forgotten
- AI-narrated dashboards: metrics + plain-English explanations + recommendations
- Project: **Smart App Monitor** — monitors crash reports (Crashlytics), groups related crashes, identifies root causes, suggests fixes (Week, Python)
- Project: **GitHub Activity Dashboard** — tracks repos: PR velocity, review times, issue aging, AI-generated weekly summaries (Week, Python/TypeScript)
- Project: **Personal Finance Tracker** — import bank CSV, auto-categorize transactions, track budgets, AI spending insights (Weekend, Python)
- Project: **Server Health Narrator** — collects metrics, generates plain-English health reports instead of graphs (Week, Python)
- Project: **Social Media Analytics** — track followers, engagement, content performance, get AI-written improvement suggestions (Weekend, Python)
- Building with Streamlit/Gradio for quick dashboards
- Scheduled reports: daily/weekly AI-generated digests via email or Slack
- Alert intelligence: reducing noise by having AI triage alerts
- Spark: build a "morning briefing" that combines all your dashboards into one AI-narrated summary
- Exercise: build the Personal Finance Tracker with a sample bank CSV export

### Chapter 7: Web Apps With AI Superpowers
**File:** `07-web-apps.html`
**Goal:** Build web applications where AI is the core feature, not a bolt-on.
**Topics:**
- The AI-native web app: when the LLM IS the product
- Project: **AI Form Builder** — describe a form in English, get a working web form with validation and conditional logic (Week, TypeScript/React)
- Project: **Content Repurposer** — paste a blog post, get Twitter threads, LinkedIn posts, email newsletters, Instagram captions (Weekend, Python + Flask/FastAPI)
- Project: **Landing Page Generator** — describe your product in a paragraph, get a complete landing page with hero, features, pricing, FAQ (Weekend, TypeScript/HTML)
- Project: **Interview Prep App** — enter a job description, get practice questions, evaluate answers in real-time (Week, TypeScript/React)
- Project: **Recipe Scaler & Converter** — paste a recipe, scale servings, convert units, substitute ingredients, generate shopping lists (Weekend, Python + Flask)
- Streaming responses: making AI web apps feel fast with SSE
- Auth and rate limiting: protecting your AI-powered endpoints
- Cost management: caching responses, choosing the right model size
- Deployment: Vercel, Railway, Fly.io — shipping AI web apps for free/cheap
- Spark: add user accounts and history to any of these, turning a tool into a SaaS
- Exercise: build the Content Repurposer and repurpose a real blog post

### Chapter 8: API Design & Microservices
**File:** `08-api-microservices.html`
**Goal:** Build APIs and backend services that use LLMs for intelligent processing.
**Topics:**
- The AI microservice pattern: a thin API wrapper around structured LLM calls
- Project: **Smart Webhook Processor** — receives webhooks, routes/processes based on natural language rules (Week, Python/TypeScript)
- Project: **Email Intelligence API** — accepts raw email, returns structured data: intent, urgency, required action, suggested reply (Weekend, Python)
- Project: **Content Moderation API** — goes beyond keyword matching, understands context and sarcasm, returns severity scores (Weekend, Python)
- Project: **Translation API With Context** — accepts domain context, produces register-appropriate translations with glossaries (Week, Python)
- Project: **Data Enrichment Service** — send a company name, get structured data: description, industry, tech stack, recent news (Weekend, Python)
- Structured output: forcing JSON responses from LLMs (tool use, JSON mode)
- Error handling: what happens when the LLM returns garbage
- Rate limiting and queuing: handling high-throughput AI services
- Testing AI APIs: snapshot tests, evaluation frameworks, quality metrics
- Spark: combine multiple AI microservices into an intelligent backend that processes any incoming data
- Exercise: build the Email Intelligence API and test it with 10 real emails

### Chapter 9: Bots & Conversational Interfaces
**File:** `09-bots-conversational.html`
**Goal:** Build useful bots for Slack, Discord, Telegram, and other platforms.
**Topics:**
- Why bots: meet people where they already are (messaging apps)
- The good bot vs the annoying bot: design principles for bots people actually use
- Project: **Team Standup Bot** — collects async standups in Slack/Discord, summarizes blockers, identifies patterns (Week, Python/TypeScript)
- Project: **On-Call Companion Bot** — send an alert to Telegram, get runbooks, similar incidents, and investigation steps (Week, Python)
- Project: **Learning Buddy Bot** — quizzes you on study topics, adapts difficulty, uses spaced repetition (Weekend, Python)
- Project: **Expense Report Bot** — send receipt photo, get extraction + categorization + monthly report (Week, Python)
- Project: **Daily Briefing Bot** — personalized morning digest: weather, calendar, news, GitHub notifications (Weekend, Python)
- Platform SDKs: Slack Bolt, Discord.py, python-telegram-bot
- Conversation state management: remembering context across messages
- Multi-turn interactions: when a bot needs to ask follow-up questions
- Deploying bots: always-on servers vs serverless (Lambda, Cloud Functions)
- Spark: build a "meta-bot" that routes to specialized bots based on the request
- Exercise: build the Daily Briefing Bot and get your first morning digest tomorrow

### Chapter 10: Workflow Automation & Integrations
**File:** `10-workflow-automation.html`
**Goal:** Build intelligent automations that connect services and make decisions — smarter than Zapier because they understand context.
**Topics:**
- Beyond Zapier: when automation needs to THINK, not just move data
- The event-driven AI pattern: trigger → analyze → decide → act
- Project: **Smart Email-to-Action Pipeline** — classifies emails, triggers workflows: invoices to accounting, meetings to calendar, newsletters to digest (Week, Python)
- Project: **Content Publishing Pipeline** — write markdown, get SEO title, meta description, social posts, scheduled across platforms (Week, Python/TypeScript)
- Project: **Release Notes Generator** — triggered by git tag, reads commits, groups by feature/fix, generates notes, posts to Slack + GitHub (Weekend, Python)
- Project: **Customer Feedback Analyzer** — collects reviews from App Store/email/tickets, categorizes sentiment, identifies trends, weekly report (Week, Python)
- Project: **Hiring Pipeline Automator** — screens applications, scores against requirements, schedules promising candidates, sends personalized responses (Month, Python)
- Integration patterns: webhooks, polling, event streams
- The orchestrator pattern: one central brain coordinating multiple services
- Error recovery: what happens when step 3 of 5 fails
- Scheduling: cron jobs, event triggers, manual kicks
- Spark: build a personal "automation dashboard" that shows all your running workflows and their status
- Exercise: build the Release Notes Generator and trigger it on your next git tag

### Chapter 11: Creative & Generative Projects
**File:** `11-creative-projects.html`
**Goal:** Build creative tools that amplify human creativity — for fun, art, games, and writing.
**Topics:**
- AI as a creative partner, not a replacement
- The joy of building things that are just FUN
- Project: **Story Collaborator** — you and AI take turns writing; maintains plot, character voice, and story arc (Weekend, Python + Flask)
- Project: **Dungeon Master Bot** — text-based RPG game master with dynamic adventures, ASCII maps, persistent world state (Week, Python)
- Project: **Commit Message Poet** — git hook that rewrites commits as haikus, limericks, or movie trailer narration (Weekend, Python)
- Project: **Trivia Game Generator** — generates custom trivia games on any topic with varying difficulty, tracks scores (Weekend, Python/TypeScript)
- Project: **Music Practice Companion** — describe what you're learning, get practice plans, theory explanations, exercises (Weekend, Python)
- Maintaining consistency: how to keep AI creative output coherent over long sessions
- The temperature dial: controlling randomness for different creative needs
- Persistence: saving game state, story progress, creative artifacts
- Multiplayer: building creative AI tools for groups
- Spark: combine Story Collaborator + Dungeon Master into a full interactive fiction engine
- Exercise: build the Commit Message Poet and install it as a git hook right now

### Chapter 12: Your AI Project Launchpad
**File:** `12-launchpad.html`
**Goal:** Give the reader a framework for picking, scoping, building, and shipping AI projects — plus a mega-list of bonus ideas.
**Topics:**
- The "what should I build?" framework: feasibility × value × learning × fun
- Scoping: the Weekend MVP approach — build the smallest useful version in 48 hours
- Tech stack decision framework: when to use Python vs TypeScript, CLI vs web, API vs bot
- Prompt engineering patterns that apply to EVERY project in this course
- Cost management: keeping Claude API costs under $5/month for personal projects
- The build loop: idea → prototype → test → iterate → ship
- Open-sourcing your project: README template, license, contribution guide
- Sharing your work: blog posts, demos, Show HN, Product Hunt
- 10+ Bonus Project Ideas: home automation controller, podcast summarizer, resume tailor, workout generator, meal prep planner, code style enforcer, meeting transcriber, travel itinerary optimizer, habit tracker with AI coaching, personal CRM, language learning partner
- From side project to product: when a project deserves more investment
- Building a portfolio of AI projects: how 5 small projects beat 1 big unfinished one
- Your 30-day challenge: pick one project per week from this course and ship it
