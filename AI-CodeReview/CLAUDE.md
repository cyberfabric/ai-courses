# Reviewing AI Code For Dummies

## Project Description
An HTML guide in English for developers who use AI coding tools (Claude Code, Cursor, Copilot, Windsurf) daily and want to stay sharp — not lose their edge to skill atrophy. The focus is exclusively on the **reactive side**: what happens AFTER the AI writes the code. How to review it, understand it, verify it, and maintain your skills while leveraging AI's speed.

This course fills a specific gap. Other courses cover proactive AI usage (feeding context, prompting, workflows). This one covers what you do when the code lands in front of you — whether it's your AI's output or a colleague's AI-assisted PR.

This course is **completely standalone** — no prerequisites, no references to other courses. If a concept needs explaining, it gets explained here.

The style is **"For Dummies"** — friendly, approachable, heavy on checklists, real-world scenarios, and "here's what I actually do" moments. The reader is smart (they're a developer) but hasn't built a structured review discipline for AI-generated code. No academic tone. Like a senior engineer sharing their actual review workflow over coffee.

## Language Rules
- All content is in **English**
- Tone: friendly, practical, opinionated — like a colleague sharing their review discipline
- Use analogies from everyday life and software development
- **No fear-mongering** — the goal is to stay sharp and be confident, not to be scared of AI
- Address: second person singular (you)
- When introducing a technique, always answer: "OK, but what does this look like when I'm reviewing a real PR?"
- Light humor is welcome — keep it engaging, not dry
- Use short paragraphs — walls of text kill understanding
- Code examples should be **review scenarios** (diffs, PR comments, shell commands, review checklists), NOT abstract tutorials

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

## 2026 Research Requirement
- **CRITICAL**: Every chapter MUST include up-to-date 2026 information. Before generating any chapter, search the web for the latest research, tools, and trends on the chapter's topics. The user explicitly wants cutting-edge 2026 content, not pre-2026 training data.
- Key sources to search: Addy Osmani's Substack, Anthropic research, Claude Code docs, CodeRabbit, Qodo, DEV Community, InfoQ, ArXiv, Medium
- Cite specific studies, statistics, and tool versions discovered during research

## File Structure
```
AI-CodeReview/
  CLAUDE.md                              — This file
  .claude/
    commands/
      generate-next-chapter.md           — Skill for chapter generation
  chapters/
    index.html                           — Landing page with navigation
    assets/
      style.css                          — Shared CSS with dark/light theme (cyan scheme)
    01-review-mindset.html               — The Review Mindset Shift
    02-reading-ai-code.html              — Reading AI-Generated Code
    03-review-checklist.html             — The Structured Review Checklist
    04-ai-reviews-ai.html               — Using AI to Review AI
    05-claude-review-toolkit.html        — Claude Code's Review Toolkit
    06-git-archaeology.html              — Understanding What Changed
    07-skill-atrophy.html                — Fighting Skill Atrophy
    08-comprehension-workflow.html        — The Comprehension Workflow
    09-reviewing-colleagues.html         — Reviewing Your Colleagues' AI-Assisted PRs
    10-codebase-ownership.html           — Codebase Ownership at Scale
    11-security-deep-dive.html           — Security Review for AI Code
    12-personal-playbook.html            — Your Personal Review Playbook
```

## Progress Tracking
- [x] Chapter 1: The Review Mindset Shift
- [x] Chapter 2: Reading AI-Generated Code
- [x] Chapter 3: The Structured Review Checklist
- [x] Chapter 4: Using AI to Review AI
- [x] Chapter 5: Claude Code's Review Toolkit
- [x] Chapter 6: Understanding What Changed
- [x] Chapter 7: Fighting Skill Atrophy
- [x] Chapter 8: The Comprehension Workflow
- [x] Chapter 9: Reviewing Your Colleagues' AI-Assisted PRs
- [x] Chapter 10: Codebase Ownership at Scale
- [x] Chapter 11: Security Review for AI Code
- [x] Chapter 12: Your Personal Review Playbook

## Instructions for /generate-next-chapter
When the user invokes `/generate-next-chapter`:
1. Read this CLAUDE.md and find the first chapter marked with `[ ]` in Progress Tracking
2. Read the "Chapter Details" section below for that chapter's topics
3. Read `chapters/assets/style.css` for available CSS classes
4. Read `chapters/index.html` for navigation template
5. Read the previous chapter (if any) for context and smooth transition
6. **Research the topic**: Search the web for the LATEST 2026 information — this is mandatory, not optional
7. Generate the HTML file in `chapters/` with full content (400-600 lines)
8. Update CLAUDE.md — mark the chapter as `[x]`
9. Update `chapters/index.html` — remove `pending` class from that chapter's card
10. Update navigation on the previous chapter if needed

## CSS Classes for Content
- `.review-checklist` — Structured review checklist (cyan accent, unique to this course) — the signature element
- `.red-flag-box` — Red flag warning about dangerous AI patterns (red accent, unique to this course)
- `.ai-tell-box` — "AI Tell" showing a recognizable AI-generated code pattern (purple accent, unique to this course)
- `.practice-drill` — Concrete exercise the reader can do right now (amber accent, unique to this course)
- `.prompt-example.good` — good examples (green accent)
- `.prompt-example.bad` — bad examples (red accent)
- `.comparison` — side-by-side comparisons
- `.tip-box` — tips and advice
- `.warning-box` — warnings and cautions
- `.exercise-box` — hands-on exercises (amber accent)
- `.checklist` — checklists with checkmarks
- `.highlight-box` — key messages (gradient background)
- `.stats-grid` + `.stat-card` — statistics display
- `.tool-card` — tool description cards (icon + name + description)
- `.workflow-steps` + `.step` + `.step-arrow` — visual workflow pipeline
- `.theme-toggle` — theme switch button (in nav)

## Content Guidelines
- **Every chapter MUST include at least one `.review-checklist`** with a structured checklist for the chapter's topic — this is the signature element of the course, making review systematic instead of ad-hoc
- **Every chapter MUST include at least one `.red-flag-box`** highlighting a common mistake or dangerous pattern in AI-generated code
- **At least one `.ai-tell-box` per chapter** showing a recognizable AI code pattern
- **At least one `.practice-drill` per chapter** with a concrete exercise
- **At least one `.exercise-box` per chapter** with a practical, hands-on task
- **At least one analogy per chapter** woven into the prose
- Code examples should be review scenarios (diffs, PR comments, shell commands), NOT abstract tutorials
- When explaining a technique, show how it looks in a real PR review
- Always connect back to the reader's experience: "You just merged an AI-generated PR. Can you explain what it does?"
- Each chapter should end with a brief preview connecting to the next chapter
- Short paragraphs — maximum 3-4 sentences per paragraph
- Be opinionated: recommend specific tools and habits, don't just list options
- Tone: encouraging, not fear-mongering

## Key References for Research
When generating chapters, search the web for the latest 2026 information. Key sources:
- Addy Osmani: addyo.substack.com/p/code-review-in-the-age-of-ai
- Addy Osmani: addyo.substack.com/p/avoiding-skill-atrophy-in-the-age
- Anthropic research: anthropic.com/research/AI-assistance-coding-skills
- ArXiv: 2601.20245v1 (How AI Impacts Skill Formation)
- Claude Code docs: code.claude.com/docs/en/code-review
- CodeRabbit: coderabbit.ai
- Qodo: qodo.ai/blog/5-ai-code-review-pattern-predictions-in-2026/
- Graphite: graphite.com/guides/ai-code-review-implementation-best-practices
- DEV Community articles on AI code review 2026
- InfoQ: infoq.com/news/2026/02/ai-coding-skill-formation/

## Chapter Details

### Chapter 1: The Review Mindset Shift
**File:** `01-review-mindset.html`
**Goal:** Establish why reviewing AI code is fundamentally different and why this skill matters more than ever in 2026.
**Topics:**
- The bottleneck moved: writing code is no longer the hard part — verification is
- Why AI code looks right but often isn't (plausible but subtly wrong)
- 2026 stats: 45% of AI-generated code contains security flaws, logic errors 1.75× more frequent, XSS 2.74× higher
- Review time increased 91%, PR sizes grew 154% with AI assistance — net delivery time stayed flat
- The knowledge transfer problem: code review is how teams share context — if AI writes and nobody reviews deeply, on-call becomes expensive
- The accountability checkpoint: "Can I explain what this code does and why it works?" — if no, the PR isn't ready
- Analogy: AI code review is like being an editor, not a proofreader — you're checking meaning, not just spelling
- Human reviewer focus areas vs what AI catches (different blind spots)
- The "high-speed intern" mental model: AI produces at scale, but needs supervision
- 81% of organizations lack full visibility into where AI-generated code exists in production
- Review checklist: the mindset shift checklist (treat AI output with MORE scrutiny, not less)
- Red flag: blindly approving AI-generated code because "it compiles and tests pass"
- AI tell: overly verbose comments explaining obvious code
- Practice drill: take your last merged PR — can you explain every function? If not, that's the gap this course addresses

### Chapter 2: Reading AI-Generated Code
**File:** `02-reading-ai-code.html`
**Goal:** Train the reader's eye to recognize AI-generated code patterns and read large AI diffs efficiently.
**Topics:**
- Common AI code "tells": over-abstraction, unnecessary wrapper functions, generic variable names, overly defensive error handling
- How AI hallucinates APIs: inventing methods that don't exist, using deprecated patterns, mixing framework versions
- The "looks smart but is fragile" pattern: AI writes code that handles the happy path beautifully but crumbles on edge cases
- Copy-paste duplication: AI loves to repeat similar code blocks instead of creating shared utilities
- Speed-reading techniques for large AI-generated diffs (500+ lines)
- Mental models for quickly assessing code quality: the "does this code teach me anything?" test
- The over-commenting pattern: AI adds comments that restate the code instead of explaining why
- The "kitchen sink" import: AI imports more than it needs
- Dead code: AI generates unused functions or unreachable branches
- When AI code is actually GOOD: recognizing when AI nailed it (so you don't waste time reviewing good code)
- Review checklist: reading AI code efficiently
- Red flag: AI-generated code that you can't trace back to a clear requirement
- AI tell: a function that handles 5 edge cases when only 2 are possible in the current system
- Practice drill: take an AI-generated diff from your recent history and list every "tell" you can spot

### Chapter 3: The Structured Review Checklist
**File:** `03-review-checklist.html`
**Goal:** Provide a concrete, actionable 10-point checklist for reviewing any AI-generated change.
**Topics:**
- The PR Contract Framework (from Addy Osmani): intent, proof of functionality, risk assessment + AI disclosure, review focus areas
- The 10-point review checklist for AI-generated code:
  1. Intent clarity: does the change match what was requested?
  2. Logic correctness: does the algorithm actually do what it claims?
  3. Edge cases: what happens with null, empty, boundary values?
  4. Security: auth, input validation, secrets, XSS, injection?
  5. Performance: unnecessary loops, N+1 queries, memory leaks?
  6. Duplication: does this duplicate existing code in the codebase?
  7. Integration: does it work with the rest of the system (not just in isolation)?
  8. Tests: are the tests testing the right things (not just achieving coverage)?
  9. Maintainability: will someone understand this in 6 months?
  10. The "explain it back" test: can the author explain every line?
- Security-critical review: auth, payments, secrets = treat AI as "high-speed intern"
- Incrementalism: breaking AI output into digestible commits for easier review
- The "explain it back" test in practice — how to do it with yourself and with colleagues
- Review checklist: the full 10-point checklist (this IS the signature element of the chapter)
- Red flag: AI-generated tests that test the implementation rather than the behavior
- AI tell: a test that mirrors the code structure instead of testing outcomes
- Practice drill: apply the 10-point checklist to your next AI-generated PR before merging

### Chapter 4: Using AI to Review AI
**File:** `04-ai-reviews-ai.html`
**Goal:** Show how to use AI review tools effectively — as a first pass, not a replacement for human judgment.
**Topics:**
- Multi-model review strategy: different LLMs catch different biases — use Claude to review Copilot's code, GPT to review Claude's
- Tool comparison (2026): CodeRabbit, Greptile, DeepSource, Qodo, SonarQube, GitHub Copilot PR review
- Full-codebase-aware tools vs diff-only tools: 40-60% more cross-file issues caught with full codebase awareness
- Ad-hoc LLM checks: pasting diffs into Claude or GPT before committing — quick and effective
- Treating AI review as "first-pass" — spellcheck, not editor
- Configuring AI review sensitivity: disabling unhelpful comment types, tuning thresholds
- AI review tools catch 70-80% of low-hanging fruit (null pointers, missing coverage, anti-patterns)
- What AI review tools miss: architectural coherence, business logic correctness, institutional context
- The "dialog" pattern: one AI writes, another reviews, human orchestrates fixes
- Open source vs commercial tools: 2026 comparison
- Review checklist: setting up your AI review stack
- Red flag: trusting AI review as the final word (it's advisory, not authoritative)
- AI tell: AI reviewer flagging stylistic issues while missing a logic error
- Practice drill: run your last PR through two different AI review tools and compare what each catches

### Chapter 5: Claude Code's Review Toolkit
**File:** `05-claude-review-toolkit.html`
**Goal:** Deep dive into Claude Code's code review features — the most relevant tool for this audience.
**Topics:**
- The `/code-review` command: how it works — dispatches a fleet of specialized agents
- Multi-agent review architecture: agents find bugs in parallel, verify findings, rank by severity
- Automatic vs manual review triggers: automatic check runs vs `@claude review` on-demand
- REVIEW.md: configuring what Claude reviews and what it ignores
- GitHub Actions integration: claude-code-action for CI/CD pipeline reviews
- Reading and acting on inline review comments: how to interpret Claude's findings
- Scaling reviews: lightweight pass for trivial PRs, deep analysis for complex ones
- Custom review rules: adding project-specific review criteria
- The review output: overview comment + inline bug comments with severity
- Combining Claude Code review with manual review: the optimal workflow
- Limitations: what Claude Code's review doesn't catch (and what you still need to do manually)
- Review checklist: setting up Claude Code review for your project
- Red flag: disabling review rules because they're "too noisy" without investigating why
- AI tell: Claude's review catching a real bug that a human would likely miss (cross-file dependency issue)
- Practice drill: set up `/code-review` on one of your PRs and analyze what it finds

### Chapter 6: Understanding What Changed
**File:** `06-git-archaeology.html`
**Goal:** Teach git-based techniques for understanding and tracing AI-generated changes.
**Topics:**
- Git diff strategies for AI-generated changes: `--stat`, `--word-diff`, `--color-moved`
- Commit archaeology: reading commit messages, understanding the sequence of changes
- Using `git log --oneline --graph` to see the shape of AI's work
- Using `git blame` to identify which parts were AI-generated vs human-written
- Asking AI to explain its own changes: "explain the diff between HEAD and HEAD~3"
- Annotating commits with AI-generation context: commit message conventions
- The "why not just the diff" problem: AI changes often touch many files — how to find the important parts
- Interactive exploration: `git show`, `git diff --name-only`, `git log -p`
- Tools for tracking AI-generated code provenance (2026 state of the art)
- Building a mental model of the codebase from git history
- Review checklist: git commands for understanding AI changes
- Red flag: a massive commit with no clear explanation of what changed and why
- AI tell: AI-generated commits that touch unrelated files (scope creep)
- Practice drill: use `git log` and `git diff` to reconstruct what an AI agent did in your last session

### Chapter 7: Fighting Skill Atrophy
**File:** `07-skill-atrophy.html`
**Goal:** Provide concrete strategies for maintaining developer skills while using AI tools heavily.
**Topics:**
- The Anthropic study deep dive: 52 engineers, 17% comprehension drop, debugging gaps most severe
- The three usage patterns that preserve learning:
  1. Conceptual Inquiry: ask questions, code yourself (scored 65%+ on comprehension)
  2. Generation-Then-Comprehension: generate, manually copy, ask follow-up questions
  3. Hybrid Code-Explanation: ask for code + explanation together
- Delegation without understanding scored below 40% on comprehension tests
- Skills most at risk: debugging, system architecture, API recall, critical thinking
- "No-AI Days": weekly manual coding sessions as cross-training
- The 15-30 minute rule: attempt problems independently before consulting AI
- AI Hygiene: verify AI output, test edge cases, ask for explanations every time
- Learning journals: tracking AI assists to identify recurring knowledge gaps
- Retrieval practice: flashcards and exercises based on AI solutions
- Choosing which skills to offload safely vs which to protect fiercely
- The Microsoft/Carnegie Mellon finding: more AI reliance = less critical thinking
- Claude Code's Learning/Explanatory mode (2026)
- Review checklist: your weekly skill maintenance routine
- Red flag: not being able to debug code that AI wrote for you
- AI tell: when you can't explain what a function does without re-asking the AI
- Practice drill: pick one AI-generated function from today — explain it line by line without any AI help

### Chapter 8: The Comprehension Workflow
**File:** `08-comprehension-workflow.html`
**Goal:** Provide a systematic workflow for understanding AI-generated code, not just shipping it.
**Topics:**
- The "teach it back" technique: if you can teach it, you understand it
- Step-by-step comprehension workflow:
  1. Read the diff — what changed?
  2. Identify the intent — what was the AI trying to do?
  3. Trace the data flow — how does data move through the change?
  4. Question the assumptions — what does the AI assume about the system?
  5. Test your understanding — can you predict what happens with unexpected input?
- Asking AI to explain its decisions: specific prompts that work
- The "rubber duck" approach: explaining AI code to a colleague (or to yourself out loud)
- Active reading vs passive scanning: techniques for engaging with code
- Building mental models of unfamiliar code patterns
- When to read line-by-line vs when to skim for structure
- The comprehension journal: documenting what you learned from each review
- Time-boxing comprehension: how much time to spend understanding vs just shipping
- Review checklist: the comprehension workflow checklist
- Red flag: merging code you "mostly understand" — the gaps will bite you during on-call
- AI tell: code that solves the problem in a way you wouldn't have thought of — this is where learning happens
- Practice drill: take an AI-generated change and write a one-paragraph explanation of what it does and why — without asking the AI

### Chapter 9: Reviewing Your Colleagues' AI-Assisted PRs
**File:** `09-reviewing-colleagues.html`
**Goal:** Address the team dynamics of reviewing code when everyone uses AI.
**Topics:**
- The new reality: most PRs now contain some AI-generated code
- Requiring AI disclosure in PRs: why transparency matters
- The PR Contract Framework applied to team reviews: intent, proof, risk, AI disclosure
- How to review without being a jerk: constructive feedback on AI-assisted code
- The "can you explain this?" conversation: asking without implying incompetence
- Pair reviewing: human reviews AI output together with the author
- Knowledge transfer through review discussions: turning reviews into learning moments
- When to send a PR back: clear criteria for rejection
- When velocity pressure conflicts with thorough review
- Building a team review culture that values understanding over speed
- Team agreements: review SLAs, AI disclosure norms, escalation paths
- Review checklist: reviewing a colleague's AI-assisted PR
- Red flag: a colleague who can't explain their own AI-generated code during review
- AI tell: PRs where the commit messages describe the prompt rather than the change
- Practice drill: draft a team review agreement covering AI disclosure and review expectations

### Chapter 10: Codebase Ownership at Scale
**File:** `10-codebase-ownership.html`
**Goal:** Address the challenge of maintaining codebase understanding when AI generates most of the code.
**Topics:**
- The ownership crisis: 100% of organizations have AI code in production, only 19% have full visibility
- Repository intelligence tools (2026): Greptile, Sourcegraph, and full-codebase-aware AI tools
- Architecture documentation that stays current: ADRs, system diagrams, dependency maps
- Code ownership models in AI-heavy teams: CODEOWNERS files, area experts, rotation
- The "bus factor" problem amplified by AI: when the person who prompted the AI leaves
- Strategies for onboarding onto AI-generated codebases
- Keeping architectural coherence when AI generates individual features
- The documentation-as-review practice: write docs for AI-generated code as a comprehension exercise
- Monitoring code quality metrics over time: complexity, coupling, test coverage
- When to refactor AI-generated code vs when to leave it alone
- Review checklist: codebase ownership health check
- Red flag: a module where nobody on the team can explain how it works
- AI tell: inconsistent patterns across files because different AI sessions produced different solutions
- Practice drill: pick one module in your codebase — write a one-page architecture doc for it without AI help

### Chapter 11: Security Review for AI Code
**File:** `11-security-deep-dive.html`
**Goal:** Deep dive into security-specific review techniques for AI-generated code.
**Topics:**
- The 2026 security landscape: 53% of AI-generated code ships with vulnerabilities
- OWASP Top 10 in the context of AI-generated code: which vulnerabilities AI introduces most
- Common security patterns AI gets wrong:
  - Authentication and authorization (incomplete checks, missing edge cases)
  - Input validation (trusting user input, incomplete sanitization)
  - Secret management (hardcoded values, insecure storage)
  - XSS (2.74× higher frequency in AI code)
  - SQL injection (parameterized queries forgotten)
- Static analysis tools: Snyk, SonarQube, Semgrep — 2026 capabilities
- Dynamic analysis and penetration testing AI output
- The "high-speed intern" review for security-critical code
- Threat modeling for AI-generated changes: a lightweight process
- Security review automation: gates in CI/CD that block insecure AI code
- The "security sandwich": human threat model → AI implementation → human security review
- Review checklist: security review for AI-generated code
- Red flag: AI-generated code that handles authentication or payment without human security review
- AI tell: AI using deprecated cryptographic functions or insecure defaults
- Practice drill: run a static analysis tool on your latest AI-generated PR and analyze the findings

### Chapter 12: Your Personal Review Playbook
**File:** `12-personal-playbook.html`
**Goal:** Help the reader build their own structured, sustainable review discipline.
**Topics:**
- Building your personal review discipline: it's a practice, not a one-time setup
- Daily habits: the 5-minute morning review (scan yesterday's merged AI code)
- Weekly habits: the deep-dive session (pick one complex AI-generated module, understand it fully)
- Monthly habits: the skills audit (what am I relying on AI for that I couldn't do myself?)
- Templates you can customize: PR review template, comprehension journal template, skills tracker
- Metrics for tracking your review effectiveness: bugs caught, comprehension score, review time
- Combining proactive (context feeding before AI writes) and reactive (review after AI writes) practices
- The review discipline as career insurance: staying employable in the AI era
- Building the habit: starting small, increasing gradually, not trying to review everything
- Tool stack recommendation: your personal AI review toolkit for 2026
- When to be thorough vs when to be fast: risk-based review allocation
- The 80/20 of review: where to focus for maximum impact
- Review checklist: your personal review playbook setup checklist
- Red flag: spending so much time reviewing that you lose the productivity benefit of AI
- AI tell: noticing that you've stopped learning from reviews — time to refresh your approach
- Practice drill: create your personal review playbook — write down your daily, weekly, and monthly review habits and commit to trying them for two weeks
