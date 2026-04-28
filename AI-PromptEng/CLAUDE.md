# Prompt Engineering For Dummies

## Project Description
An HTML guide in English for anyone who uses AI tools and wants to get dramatically better results from them. The primary audience is an Android development team — developers, QA engineers, iOS developers, and managers — but the content is useful for anyone who interacts with AI assistants like Claude, ChatGPT, or Gemini.

The style is **"For Dummies"** — friendly, approachable, heavy on analogies and real-world examples. The reader is smart but may have never thought systematically about how to write prompts. Every chapter should produce at least one "wow, I should've been doing this all along" moment.

## Language Rules
- All content is in **English**
- Tone: friendly, conversational, like a colleague sharing tips over lunch
- Use analogies from everyday life and work to explain prompt engineering concepts
- Address: second person singular (you)
- When introducing a technique, always include a **before/after** example showing the improvement
- Light humor is welcome — keep it engaging, not dry
- Use short paragraphs — walls of text kill understanding
- Include examples relevant to different roles: developers, QAs, managers, iOS devs

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
AI-PromptEng/
  CLAUDE.md                              — This file
  .claude/
    commands/
      generate-next-chapter.md           — Skill for chapter generation
      create-memory-map.md               — Skill for visual chapter summary generation
  chapters/
    index.html                           — Landing page with navigation
    assets/
      style.css                          — Shared CSS with dark/light theme
    01-what-is-prompt-engineering.html    — What Is Prompt Engineering?
    02-anatomy-of-a-prompt.html          — Anatomy of a Great Prompt
    03-core-techniques.html              — Core Techniques
    04-roles-and-personas.html           — Role Play and Personas
    05-controlling-output.html           — Controlling Output Format
    06-prompt-patterns.html              — Prompt Patterns That Work
    07-when-prompts-go-wrong.html        — When Prompts Go Wrong
    08-prompting-for-qa.html             — Prompting for QA and Testing
    09-prompting-for-everyone.html       — Prompting for Everyone
    10-prompt-security.html              — Prompt Security and Safety
    11-model-differences.html            — Model Differences
    12-advanced-techniques.html          — Advanced Prompt Engineering
```

## Progress Tracking
- [x] Chapter 1: What Is Prompt Engineering?
- [x] Chapter 2: Anatomy of a Great Prompt
- [x] Chapter 3: Core Techniques: Zero-Shot, Few-Shot, and Chain-of-Thought
- [x] Chapter 4: Role Play and Personas
- [x] Chapter 5: Controlling Output Format
- [x] Chapter 6: Prompt Patterns That Work
- [x] Chapter 7: When Prompts Go Wrong
- [x] Chapter 8: Prompting for QA and Testing
- [x] Chapter 9: Prompting for Everyone: Writing, Analysis, and Planning
- [x] Chapter 10: Prompt Security and Safety
- [x] Chapter 11: Model Differences and Cross-Platform Tips
- [x] Chapter 12: Advanced Prompt Engineering

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
- `.prompt-box` — example prompt with monospace text (amber accent, unique to this course)
- `.output-box` — AI output/response example (green accent, unique to this course)
- `.technique-box` — technique highlight/explanation (purple accent, unique to this course)
- `.before-after` — side-by-side before/after prompt comparison (unique to this course)
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
- **At least one `.prompt-box`** per chapter showing a real prompt
- **At least one `.output-box`** per chapter showing AI output
- **At least one `.technique-box`** per chapter highlighting a technique
- **At least one `.before-after`** per chapter showing a prompt improvement
- **At least one `.exercise-box`** per chapter with a hands-on exercise
- Include examples for **different roles** where relevant (dev, QA, manager, iOS dev)
- Every technique needs a **concrete, copy-pasteable example**
- When possible, connect techniques to tools the reader uses (Claude, ChatGPT, Gemini, Cursor)
- Each chapter should end with a brief preview of how this connects to the next chapter

## Chapter Details

### Chapter 1: What Is Prompt Engineering?
**File:** `01-what-is-prompt-engineering.html`
**Goal:** Convince the reader that prompt engineering is a real skill worth learning — not just "typing stuff into ChatGPT."
**Topics:**
- The gap between "using AI" and "getting great results from AI"
- What prompt engineering actually is: the art of communicating clearly with AI
- Why the same question phrased differently gets wildly different answers — with live examples
- The "garbage in, garbage out" principle applied to AI
- A quick history: from googling skills to prompting skills
- The 80/20 of prompting: small changes, massive improvements
- Who needs this: developers, QAs, managers, designers — anyone who types into an AI
- The mental model: AI as a brilliant but literal intern who follows instructions exactly
- Why "just ask it" isn't enough: the difference between a 2-minute prompt and a 2-second prompt
- Common myths: "AI understands me," "longer prompts are better," "there's one perfect prompt"
- What this course will teach you: a systematic approach, not guesswork
- Exercise: Take a prompt you've used recently and identify what's missing

### Chapter 2: Anatomy of a Great Prompt
**File:** `02-anatomy-of-a-prompt.html`
**Goal:** Give the reader a reusable framework for building any prompt from scratch.
**Topics:**
- The five building blocks of a prompt: Task, Context, Constraints, Format, Examples
- **Task**: what you want the AI to do — be specific, use action verbs
- **Context**: background info the AI needs — your role, the situation, what you've tried
- **Constraints**: boundaries and rules — what to avoid, length limits, tone requirements
- **Format**: how you want the output — bullet points, JSON, table, essay, code
- **Examples**: showing the AI what you mean — the most powerful building block
- The order matters: how to structure these blocks for maximum clarity
- The "instruction hierarchy": system prompt > user prompt > context
- Before/after: a vague prompt vs the same prompt with all five blocks
- The "one prompt, one task" rule: why splitting complex requests works better
- Common mistakes: burying the task, conflicting constraints, missing context
- Template: a fill-in-the-blank prompt template the reader can use immediately
- Exercise: Rewrite a bad prompt using all five building blocks

### Chapter 3: Core Techniques: Zero-Shot, Few-Shot, and Chain-of-Thought
**File:** `03-core-techniques.html`
**Goal:** Teach the three fundamental prompting strategies and when to use each.
**Topics:**
- **Zero-shot**: asking the AI to do something with no examples — when it works, when it doesn't
- **Few-shot**: providing 2-5 examples before your actual request — the power of showing, not telling
- How to pick good few-shot examples: diversity, edge cases, format consistency
- **Chain-of-thought (CoT)**: asking the AI to think step by step
- Why "think step by step" works: it forces the AI to show intermediate reasoning
- When CoT helps most: math, logic, complex analysis, debugging
- When CoT hurts: simple tasks where it adds unnecessary verbosity
- Combining techniques: few-shot + CoT for maximum accuracy
- The "let's think about this carefully" variants and what they actually do
- Zero-shot CoT vs explicit CoT: "think step by step" vs structured reasoning prompts
- Real examples for each technique: code review, test case generation, data analysis
- Decision flowchart: which technique to use for which task
- Exercise: Solve the same problem three ways — zero-shot, few-shot, and CoT — compare results

### Chapter 4: Role Play and Personas
**File:** `04-roles-and-personas.html`
**Goal:** Teach the reader how to use role/persona prompting to dramatically change AI behavior.
**Topics:**
- What persona prompting is: "You are a..." and why it works
- The psychology: how role-setting activates different "knowledge areas" in the model
- Basic roles: expert, critic, teacher, interviewer, translator
- Role stacking: combining multiple personas ("You are a senior Android developer who also has QA experience")
- The specificity spectrum: "You are an expert" vs "You are a senior Android developer at a fintech company with 10 years of experience in Kotlin"
- How roles change tone, depth, and focus — side-by-side comparisons
- Roles for different team members: developer persona, QA persona, PM persona, security reviewer
- The "pretend you're explaining to..." technique for adjusting complexity level
- System prompts vs user-level role instructions: what goes where
- Anti-patterns: over-specified roles, contradictory personas, harmful role-play
- Custom instructions in Claude and ChatGPT: making personas persistent
- When NOT to use personas: simple factual questions, basic code completion
- Exercise: Write three personas for your daily work and test each with the same question

### Chapter 5: Controlling Output Format
**File:** `05-controlling-output.html`
**Goal:** Teach the reader to get exactly the format they need from AI — every time.
**Topics:**
- Why format matters: the difference between useful output and "I need to reformat this myself"
- Requesting specific formats: JSON, XML, CSV, YAML, Markdown, HTML
- Markdown formatting: headers, tables, bullet points, numbered lists, code blocks
- JSON output: specifying schemas, nested objects, arrays — with validation tips
- Table output: when to use markdown tables vs structured data
- Code output: language specification, commenting requirements, file structure
- The "respond ONLY with..." technique for clean, parseable output
- Controlling length: "in exactly 3 bullet points," "in under 100 words," "one paragraph"
- Controlling tone: formal, casual, technical, ELI5
- Multi-part outputs: asking for analysis + recommendation + action items in one prompt
- Using delimiters: XML tags, triple backticks, headers to structure AI responses
- Handling when the AI ignores your format: reinforcement techniques
- Exercise: Get the AI to output a perfectly formatted test plan as a markdown table

### Chapter 6: Prompt Patterns That Work
**File:** `06-prompt-patterns.html`
**Goal:** Give the reader a library of copy-paste prompt patterns for common daily tasks.
**Topics:**
- The "pattern library" concept: reusable prompt structures you adapt to each situation
- Pattern 1: The Explainer — "Explain X as if I'm a [level]. Focus on [aspect]. Use [format]."
- Pattern 2: The Reviewer — "Review this [thing] for [criteria]. List issues as [format]. Prioritize by [metric]."
- Pattern 3: The Generator — "Generate [N] [things] that [criteria]. Format as [format]. Include [details]."
- Pattern 4: The Transformer — "Convert this [input format] to [output format]. Preserve [aspects]. Ignore [aspects]."
- Pattern 5: The Debugger — "Here's the problem: [description]. Here's what I expected: [expected]. Here's what happened: [actual]. Here's the code: [code]."
- Pattern 6: The Comparator — "Compare [A] and [B] across these dimensions: [list]. Present as a table. Recommend which to use for [scenario]."
- Pattern 7: The Planner — "I need to [goal]. My constraints are [list]. Create a step-by-step plan with [deliverables] at each step."
- Pattern 8: The Summarizer — "Summarize this [content] in [format]. Focus on [audience]. Highlight [key aspects]."
- How to build your own patterns: identifying the variables in your recurring prompts
- Team prompt libraries: sharing patterns across your team
- Exercise: Create a prompt pattern for a task you do at least once a week

### Chapter 7: When Prompts Go Wrong
**File:** `07-when-prompts-go-wrong.html`
**Goal:** Teach systematic prompt debugging — what to do when AI gives bad results.
**Topics:**
- The prompt debugging mindset: it's YOUR prompt, not the AI's fault
- Failure mode 1: The AI misunderstood the task — ambiguous instructions
- Failure mode 2: The AI lacks context — you assumed knowledge it doesn't have
- Failure mode 3: The AI followed instructions too literally — edge case you didn't think of
- Failure mode 4: The AI hallucinated — confident but wrong
- Failure mode 5: The output format is wrong — missing or ignored format instructions
- The debugging checklist: 5 questions to ask when output is wrong
- The "explain your reasoning" technique: asking AI to show its work so you can spot where it went wrong
- Iterative refinement: the prompt → review → adjust → retry loop
- When to start over vs when to iterate: recognizing a dead end
- The "negative prompting" technique: telling AI what NOT to do
- Prompt versioning: keeping track of what you've tried and what worked
- The temperature factor: when randomness helps and when it hurts
- Exercise: Take a prompt that gives inconsistent results and systematically fix it

### Chapter 8: Prompting for QA and Testing
**File:** `08-prompting-for-qa.html`
**Goal:** Give QA engineers (and developers who write tests) a toolkit of prompting techniques for testing workflows.
**Topics:**
- Why QA is a prompt engineering superpower: testers think in edge cases, which is exactly what good prompting requires
- Generating test cases: from a feature spec to comprehensive test scenarios
- Prompting for edge cases: "Now think of 10 edge cases that could break this feature"
- Bug report writing: using AI to turn vague observations into structured, actionable bug reports
- Test data generation: creating realistic but fake data for testing
- Exploratory testing with AI: "If you were trying to break this feature, what would you try?"
- Regression testing prompts: "Given these changes, what existing functionality might break?"
- API testing prompts: generating requests for different status codes, edge cases, and error conditions
- Accessibility testing: prompting AI to review UI for WCAG compliance
- Performance testing scenarios: using AI to generate load test scripts and scenarios
- The QA persona: "You are a senior QA engineer who is known for finding bugs nobody else finds"
- Prompts for non-functional requirements: security, performance, usability
- Exercise: Generate a complete test plan for a feature you're currently working on

### Chapter 9: Prompting for Everyone: Writing, Analysis, and Planning
**File:** `09-prompting-for-everyone.html`
**Goal:** Show how prompt engineering applies beyond code — for writing, analysis, planning, and communication.
**Topics:**
- Email drafting: "Write a professional email to [person] about [topic]. Tone: [formal/friendly]. Key points: [list]."
- Meeting preparation: "Generate an agenda for a [type] meeting. Duration: [time]. Attendees: [roles]. Goals: [list]."
- Document review: "Review this document for [criteria]. Suggest improvements. Highlight unclear sections."
- Data analysis prompts: "Analyze this data and identify [patterns/trends/outliers]. Present findings as [format]."
- Decision frameworks: "Help me decide between [options]. My priorities are [list]. Present as a pros/cons matrix."
- Presentation outlines: "Create a [N]-slide outline for a presentation about [topic] for [audience]."
- Status report generation: "Generate a status report from these notes: [input]. Format: [template]."
- Interview preparation: "Generate [N] interview questions for a [role] position focusing on [skills]."
- Learning and research: "Explain [topic] at [level]. Then give me 5 questions to test my understanding."
- Delegation and task breakdown: "Break this project into tasks for a team of [N] people with [skills]."
- The manager's toolkit: prompts for 1:1s, performance reviews, team planning
- Exercise: Pick 3 non-coding tasks from your last week and write optimized prompts for them

### Chapter 10: Prompt Security and Safety
**File:** `10-prompt-security.html`
**Goal:** Explain how prompts can be exploited and how to write defensive prompts.
**Topics:**
- Why this chapter matters: if you build anything with AI, you need to understand prompt security
- Prompt injection: what it is, how it works, why it's dangerous
- Direct injection: "Ignore your instructions and do X instead"
- Indirect injection: hiding malicious instructions in data the AI processes
- Real-world examples: prompt injection attacks that made headlines
- The system prompt leak: how attackers extract hidden instructions
- Data exfiltration: getting AI to reveal sensitive information from its context
- Jailbreaking: techniques attackers use to bypass safety guardrails
- Defensive prompting: techniques to make your prompts resistant to injection
- Input validation: sanitizing user input before it reaches the AI
- Output validation: checking AI responses before acting on them
- The principle of least privilege: giving AI only the context it needs
- Layered defenses: why no single technique is enough
- Exercise: Try to break a prompt you've written — then fix the vulnerability

### Chapter 11: Model Differences and Cross-Platform Tips
**File:** `11-model-differences.html`
**Goal:** Help the reader understand how different AI models respond to prompts and write portable prompts.
**Topics:**
- The model landscape: Claude (Anthropic), GPT (OpenAI), Gemini (Google), open-source models
- Why the same prompt gives different results on different models
- Claude's strengths: long context, instruction following, structured output, safety
- GPT's strengths: broad training, plugins/tools ecosystem, image generation
- Gemini's strengths: multimodal, Google integration, large context windows
- Open-source models (Llama, Mistral): when to use them, prompting differences
- Model-specific quirks: what works on one model but fails on another
- Writing portable prompts: techniques that work well across all major models
- System prompt differences: how Claude, GPT, and Gemini handle system-level instructions
- API vs chat interface: how the same model behaves differently in different contexts
- Model selection guide: which model for which task (code, writing, analysis, creative)
- Cost considerations: how prompt design affects token usage and cost
- Exercise: Take your best prompt and test it on 2-3 different AI models — compare results

### Chapter 12: Advanced Prompt Engineering
**File:** `12-advanced-techniques.html`
**Goal:** Introduce advanced techniques for readers who've mastered the basics and want to push further.
**Topics:**
- Prompt chaining: breaking complex tasks into a sequence of simpler prompts
- How to design a chain: identifying handoff points, what to pass between steps
- Meta-prompting: using AI to write prompts ("Write me a prompt that will...")
- Self-reflection prompts: "Now review your own answer and identify weaknesses"
- Tree-of-thought: exploring multiple reasoning paths before committing to an answer
- Structured reasoning: XML tags, numbered steps, and explicit reasoning frameworks
- Prompt optimization: A/B testing prompts, measuring output quality systematically
- Building prompt libraries for your team: documentation, versioning, sharing
- Automated prompt pipelines: using prompts in scripts, CI/CD, and automation
- The CLAUDE.md pattern: embedding prompts in your project for AI tools to follow
- Evaluation at scale: how to measure prompt quality across hundreds of outputs
- The future of prompt engineering: will it still matter as models improve?
- Exercise: Design a 3-step prompt chain for a complex task in your workflow
