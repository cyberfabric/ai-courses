# Spec Craft With AI For Dummies

## Project Description
An HTML guide in English for **PMs, POs, BAs, project managers, and business owners** &mdash; anyone writing specs in 2026 with AI assistance. The course teaches **spec craft with AI while keeping the human in the driving seat**: turning ideas into validated, engineering-ready specs without becoming a passive editor of generic AI output.

The reader is **tech-fluent but non-coding**. They know what a PR, an API, a repo, and a ticket are. They don't write code themselves. They write specs, drive discovery, talk to engineers, and own product outcomes.

The course is **deliberately tool-agnostic**. Examples reference Copilot, Windsurf, Claude (Code or chat), ChatGPT, and Gemini interchangeably. It is not built around any single SDD framework like BMAD or OpenSpec &mdash; principles travel across tools.

The style is **"For Dummies"**: friendly, encouraging, second-person, analogy-heavy. Patterns are framed as *what high-leverage PMs do* rather than as mistakes to avoid. **No blame, no critique, no scolding.**

## Language Rules
- All content is in **English**
- Tone: warm, encouraging, "patient mentor in your corner"
- Address: second person singular (you)
- Use analogies from product work, driving, cooking, writing, sports &mdash; not from coding
- Light humor is welcome; sarcasm is not
- Short paragraphs &mdash; walls of text kill understanding
- **No blame language.** Never "PMs always do X wrong." Always "here's what works well." Describe patterns; don't shame people for them.
- **Tool-agnostic phrasing.** Prefer "your AI tool", "the assistant", "the model" over single-tool names. When you need a concrete example, rotate across Copilot / Windsurf / Claude / ChatGPT / Gemini so no one tool dominates.
- Avoid framework-specific jargon (no BMAD, OpenSpec, Shape Up unless explicitly referenced as one option among many)

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
- All generated chapters MUST meet the 400-line minimum on the FIRST attempt. Draft the FULL content in one pass targeting ~10% above the minimum (~440-460 lines). Verify with `wc -l` before finalizing.
- If under the minimum, expand with substantive sections (concrete examples, sample dialogues, case sketches, deep-dives) &mdash; not filler, not line-by-line padding.
- If you end up within 10&ndash;15% above the minimum, LEAVE IT ALONE. Only trim if you're significantly over (e.g., >25% above), and then cut whole sections, not individual lines.
- Never pad content incrementally &mdash; produce complete, full-length content in one pass.

## HTML Validation Rules
- Use `</div>` to close `<div>` elements &mdash; never invent tags like `</tip>`, `</note>`, `</card>`, `</box>`. Closing tags must match opening tags exactly.
- Always close `tip-box`, `warning-box`, `driver-box`, `dialogue-box`, `spec-snippet`, `smell-test`, and `exercise-box` divs with `</div>`.
- After writing a chapter, grep for `</tip>`, `</note>`, `</card>`, `</box>`, `</driver>`, `</dialogue>`, `</spec>`, `</smell>` &mdash; these should never appear.
- Validate all HTML tags are properly closed before declaring the chapter done.

## Project Structure Rules
- Always check the current working directory and respect the explicit project path provided by the user. Do NOT search parent directories or sibling projects unless explicitly asked.

## Cross-Reference Rules
- When a chapter references another chapter in this course, use a relative path (e.g., `06-acceptance-criteria.html`) and verify the target file exists before finishing.
- Cross-references between chapters must be consistent: if chapter 5 says "we'll cover this in chapter 8", make sure chapter 8 actually covers it.

## File Structure
```
PM-SpecCraft/
  CLAUDE.md                              — This file
  .claude/
    commands/
      generate-next-chapter.md           — Skill for chapter-by-chapter generation
      create-memory-map.md               — Skill for visual chapter summary generation
  chapters/
    index.html                           — Landing page with navigation
    assets/
      style.css                          — Shared CSS with dark/light theme (rose/magenta)
    01-pm-in-2026.html                   — The PM in 2026: AI as Co-Pilot, Not Autopilot
    02-the-driving-seat.html             — The Driving Seat: 5 Decisions Only You Make
    03-fuzzy-to-sharp.html               — From Fuzzy Idea to Sharp Problem
    04-discovery-conversations.html      — Discovery Conversations with AI
    05-writing-the-prd.html              — Writing the PRD With AI (and Owning It)
    06-acceptance-criteria.html          — Acceptance Criteria & Edge Cases
    07-pressure-testing.html             — Pressure-Testing Your Spec
    08-seven-smell-tests.html            — Validating AI Output: 7 Smell Tests
    09-engineering-handoff.html          — The Engineering Handoff
    10-iterating-after-feedback.html     — Iterating After First Feedback
    11-your-ai-pm-kit.html               — Your Personal AI PM Kit
    12-habits-driving-seat.html          — Habits That Keep You in Control
    maps/                                — Visual memory maps (generated on demand)
```

## Progress Tracking
- [x] Chapter 1: The PM in 2026: AI as Co-Pilot, Not Autopilot
- [x] Chapter 2: The Driving Seat: 5 Decisions Only You Make
- [x] Chapter 3: From Fuzzy Idea to Sharp Problem
- [x] Chapter 4: Discovery Conversations with AI
- [x] Chapter 5: Writing the PRD With AI (and Owning It)
- [x] Chapter 6: Acceptance Criteria & Edge Cases
- [x] Chapter 7: Pressure-Testing Your Spec
- [x] Chapter 8: Validating AI Output: 7 Smell Tests
- [x] Chapter 9: The Engineering Handoff
- [x] Chapter 10: Iterating After First Feedback
- [x] Chapter 11: Your Personal AI PM Kit
- [x] Chapter 12: Habits That Keep You in Control

## Instructions for /generate-next-chapter
When the user invokes `/generate-next-chapter`:
1. Read this CLAUDE.md and find the first chapter marked with `[ ]` in the "Progress Tracking" section
2. Read the "Chapter Details" section below for that chapter's goal and topics
3. Read `chapters/assets/style.css` for available CSS classes (especially the four custom ones: `.driver-box`, `.dialogue-box`, `.spec-snippet`, `.smell-test`)
4. Read `chapters/index.html` for navigation template
5. Read the previous chapter (if any) for context and a smooth transition
6. Generate the HTML file in `chapters/` with full content (400-600 lines, aim ~440-460)
7. Update CLAUDE.md &mdash; mark the chapter as `[x]` in Progress Tracking
8. Update `chapters/index.html` &mdash; remove `pending` class from that chapter's card
9. Update navigation on the previous chapter if needed (add or fix the "next" link)

## CSS Classes for Content
**Custom to this course:**
- `.driver-box` &mdash; "this is yours to decide" callouts that flag PM-only judgment moments. Use 1-2 per chapter to remind the reader of decisions AI cannot make.
- `.dialogue-box` &mdash; multi-turn PM ↔ AI conversation. Use rows: `<div class="dialogue-pm">...</div>` and `<div class="dialogue-ai">...</div>`. Use heavily in chapters 3-7.
- `.spec-snippet` &mdash; PRD/spec excerpt in mono font. Add `.spec-before` (red) and `.spec-after` (green) modifiers to show transformations.
- `.smell-test` &mdash; short validation check / red flag. Encouraging tone, not scolding. Use in chapters 7, 8, 9.

**Shared across courses:**
- `.tip-box` &mdash; tips and advice (blue accent)
- `.warning-box` &mdash; heads-up callouts (amber accent &mdash; use sparingly; we avoid scolding)
- `.exercise-box` &mdash; "Try It" hands-on exercises (gold accent)
- `.prompt-example.good` / `.prompt-example.bad` &mdash; prompt examples (green / red); pair inside `.comparison` for side-by-side
- `.checklist` / `.checklist li.checked` &mdash; checklists with checkmarks
- `.highlight-box` &mdash; key-message gradient banner (rose gradient)
- `.stats-grid` + `.stat-card` &mdash; numeric callouts
- `.tool-card` &mdash; tool description cards (icon + name + description)
- `.workflow-steps` + `.step` + `.step-arrow` &mdash; visual workflow pipeline
- `.theme-toggle` &mdash; theme switch button (in nav)

## Content Guidelines
Each chapter must include, at minimum:
- **At least one `.driver-box`** &mdash; flag a decision that the reader, not the AI, must make.
- **At least one concrete example** showing the workflow in action (a real-feeling product scenario, not a toy one).
- **At least one `.exercise-box`** &mdash; a small hands-on exercise the reader can try this week with their own AI tool of choice.
- **At least one `.dialogue-box`** in chapters 3-10 &mdash; multi-turn PM ↔ AI conversation that models the technique.
- **Tool diversity:** in any chapter that names a tool, name at least two different ones across the chapter (Copilot/Windsurf/Claude/ChatGPT/Gemini). Never depend on a single tool's UI.
- **No prerequisites.** Don't assume the reader read the previous chapter. Reference it ("we sharpened the problem statement in chapter 3") but don't require it.
- **End with a one-paragraph preview** of how this connects to the next chapter.

## Chapter Details

### Chapter 1: The PM in 2026: AI as Co-Pilot, Not Autopilot
**File:** `01-pm-in-2026.html`
**Goal:** Set the frame. AI accelerates the spec-writing job; the reader still steers it. Establish the "co-pilot, not autopilot" mental model that runs through the whole course.
**Topics:**
- A vignette: a PM in 2026 walks through their morning, using AI for 4-5 different spec-related tasks &mdash; what changed, what didn't
- Where AI fits in the PM job today: drafting, expanding, summarizing, pressure-testing, formatting
- The "vague brief, AI fills the rest" pattern &mdash; describe it factually, with empathy, never as a failure
- What stays human in 2026: judgment, taste, customer truth, accountability for outcomes, the right to change your mind
- The co-pilot metaphor: who flies, who navigates, who lands the plane &mdash; and why "autopilot" is a different mode entirely
- Tool-agnostic principles vs tool-specific tricks &mdash; this course teaches the principles
- A one-page mental model: Driver (you) ↔ Co-pilot (AI) ↔ Spec (the artifact) &mdash; introduced as a simple diagram in HTML
- What this course will do (teach a repeatable craft) and won't do (push a single framework or tool)
- Try It: pick one task you did this week and identify which 30% was uniquely yours

### Chapter 2: The Driving Seat: 5 Decisions Only You Make
**File:** `02-the-driving-seat.html`
**Goal:** Name the irreducible PM decisions. Make it crisp where AI can help versus where it cannot.
**Topics:**
- Why "what only you decide" needs to be explicit before you start using AI
- Decision 1: **Is this problem worth solving?** &mdash; AI can list problems; only you can pick the one that matters
- Decision 2: **Who is the user?** &mdash; AI can generate segments; only you can validate them with real people
- Decision 3: **What's in scope, what's out?** &mdash; AI can list options; only you can say no
- Decision 4: **What does success look like?** &mdash; AI can suggest metrics; only you can defend the one you'll be judged on
- Decision 5: **When is it good enough to ship?** &mdash; AI cannot weigh risk vs urgency vs team capacity for you
- For each decision: how AI can be a sounding board *without* taking the decision over
- A sample `.dialogue-box` showing a healthy "AI as sounding board" exchange on Decision 1
- A `.driver-box` after each decision summarizing "what's yours"
- Try It: write down today's 5 decisions on a current product question, before opening any AI tool

### Chapter 3: From Fuzzy Idea to Sharp Problem
**File:** `03-fuzzy-to-sharp.html`
**Goal:** Use AI to sharpen problem statements. Show the back-and-forth that turns "users want better notifications" into something specific and actionable.
**Topics:**
- Why fuzzy problems produce fuzzy specs &mdash; and why AI quietly makes this worse if you don't intervene
- The "5 whys" loop with AI: ask, push back, ask again
- A working problem-statement template: **Problem / Users / Evidence / Success** &mdash; show it as a `.spec-snippet`
- Live example: take a vague brief ("notifications are bad") through 4 rounds of sharpening with AI &mdash; in `.dialogue-box` form
- Show a `.spec-snippet.spec-before` (vague) and `.spec-snippet.spec-after` (sharp) for the same problem
- Separating problem from solution: how AI tends to skip ahead, and how to redirect it
- Pushing back on AI's first reframe: when the AI's neat problem statement is *too neat*
- Watching for invented context: AI will fill gaps with plausible-sounding details; flag them
- A `.driver-box` on the boundary: AI can sharpen language; only you decide which problem is yours to own
- Try It: take one vague brief from your current backlog through this loop &mdash; aim for 3-4 rounds, not 1

### Chapter 4: Discovery Conversations with AI
**File:** `04-discovery-conversations.html`
**Goal:** Use AI to widen exploration without losing customer truth. Show how to brainstorm safely, generate alternatives, and recognize the limits of what AI can replace.
**Topics:**
- Brainstorming with AI safely: prompt for breadth first ("give me 12 angles"), then narrow
- Generating user segments with AI &mdash; and the trap of accepting them without grounding
- Jobs-To-Be-Done candidates: how AI can list plausible jobs, and why you still need real interviews
- Hypothesis generation: turning fuzzy assumptions into testable statements with AI's help
- The alternative-solution table: a `.spec-snippet` template comparing 3-5 solution shapes (cost, risk, fit)
- Recognizing AI-flavored generic outputs: "leverage", "robust", "seamless", "delight" &mdash; how to spot them and ask for specifics
- A `.dialogue-box` showing a healthy discovery conversation: PM widens, AI suggests, PM grounds, AI sharpens
- What AI **cannot** replace: real customer voice, real usage data, real signal from sales/support &mdash; called out in a `.driver-box`
- When to leave the chat: signs you've gone as far as a discovery conversation can take you
- Try It: pick a feature idea, ask AI for 10 alternative solutions, then mark which 3 you'd actually validate with users this week

### Chapter 5: Writing the PRD With AI (and Owning It)
**File:** `05-writing-the-prd.html`
**Goal:** Co-author a complete PRD without becoming a passive editor of AI prose. Walk through an outline-first workflow that keeps the reader in voice.
**Topics:**
- A reusable PRD anatomy: Problem / Users / Goals & Non-goals / Scope / UX shape / AC / Risks / Metrics / Open questions &mdash; show as a `.spec-snippet`
- The outline-first workflow: write the headings yourself, then have AI fill skeletons under each
- Why prompting for a "full PRD" is the wrong unit of work
- Attaching context to AI: research notes, prior PRDs, product glossary, ticket history &mdash; show how each shifts output quality
- A `.dialogue-box` walking from "here's my outline plus context" to "here's the AC section" to a refinement
- Voicing decisions in your own words: take an AI draft and rewrite the 2-3 sentences that contain your actual product judgment
- Iterative refinement: pass-by-pass, not all-at-once
- Versioning discipline: save before each big edit, label changes, keep a one-line decision history at the top
- A `.driver-box` on the line: AI drafts language; you choose the call
- Tool diversity callout: Copilot / Windsurf / Claude / ChatGPT all do this differently &mdash; principle stays the same
- Try It: pick a real ticket, write the PRD outline yourself, then use AI to fill exactly two sections &mdash; rewrite one of those sections in your voice

### Chapter 6: Acceptance Criteria & Edge Cases
**File:** `06-acceptance-criteria.html`
**Goal:** Use AI to find what you'd otherwise miss. Show how AI accelerates writing testable AC, generating edge cases, and reaching a Definition of Done.
**Topics:**
- The AC mindset: each criterion must be testable, observable, and unambiguous
- Common AC formats: "Given/When/Then", checklist style, behavior list &mdash; pros and cons of each
- Show a `.spec-snippet.spec-before` of vague AC and a `.spec-snippet.spec-after` of testable AC, derived through one AI loop
- Generating edge case lists with AI: empty states, error states, slow networks, accessibility, permissions, multi-language, time zones, large data sets
- Prompts that find what you missed: "what would break this?", "what does the unhappy path look like?", "what happens if the user does this twice fast?"
- Pruning noise: AI generates many candidates; you keep the few that matter for this release
- A `.dialogue-box` showing the "what could break this" loop &mdash; AI lists 12, PM marks 4 as in-scope
- The Definition of Done conversation: scoping accessibility, perf budgets, error rates as part of DoD
- A `.smell-test` for AC: if you can't write a test for it, it's not yet AC
- A `.driver-box` on prioritization: AI can list edge cases forever; you decide which are worth the cost
- Try It: take an in-flight ticket; ask AI for 10 edge cases; circle the 3 that change your release plan

### Chapter 7: Pressure-Testing Your Spec
**File:** `07-pressure-testing.html`
**Goal:** Adversarially review your own spec before engineering does. Show how to use AI to play multiple critical reviewers.
**Topics:**
- Why self-review with AI is high leverage &mdash; you find issues before they cost trust
- Red-team prompts: "you're a senior engineer reviewing this spec; what's wrong, what's missing, what's risky?"
- Role-playing reviewers in sequence: engineer, designer, legal/compliance, customer support, security, finance
- A `.dialogue-box` walking through a single spec under 3 different reviewer roles
- Listing assumptions explicitly: have AI extract every implicit assumption in the spec
- Risk register: a `.spec-snippet` template with assumption / probability / impact / mitigation
- "What would a senior PM ask me about this?" &mdash; a prompt that often surfaces 5-10 missing items
- The gap matrix: scope rows × reviewer columns; check each cell for unaddressed concerns
- A `.smell-test` block listing 5 questions you should always run on your spec before sharing it
- Converting findings into spec edits: don't just collect issues, fix them in the same session
- A `.driver-box` on which findings to act on: AI lists; you triage
- Try It: run a current spec through three reviewer personas; pick the one finding that most changes the spec

### Chapter 8: Validating AI Output: 7 Smell Tests
**File:** `08-seven-smell-tests.html`
**Goal:** Spot when AI output is wrong, hand-wavy, or generic. Give the reader seven concrete checks they can run in seconds.
**Topics:**
- Why confidence ≠ correctness: AI tone is uniform regardless of how grounded the answer is
- Smell test 1: **Generic-language tells.** Words like "leverage", "robust", "seamless", "scalable", "delight" with no specifics &mdash; how to interrogate them
- Smell test 2: **Fabricated specifics.** Made-up version numbers, screen names, feature names, customer names &mdash; how to spot them
- Smell test 3: **Suspiciously round numbers.** "30% improvement", "50% of users", "10x faster" &mdash; ask for sources
- Smell test 4: **Missing context.** AC that ignores your platform, your stack, your team's reality &mdash; the "blank product" tell
- Smell test 5: **Hallucinated metrics.** Metrics that aren't measurable in your product today &mdash; ask "how would we observe this?"
- Smell test 6: **Vague verbs.** "Improve", "optimize", "streamline", "enhance" &mdash; force them into observable behavior
- Smell test 7: **The "uncanny consensus".** AI agreeing with you too quickly, or producing text that perfectly matches your prompt &mdash; ask for the strongest counter-argument
- For each smell test: a `.smell-test` box with the tell, a quick check, and a re-prompt
- A `.dialogue-box` showing one round of "AI gives generic output → PM runs smell test → AI sharpens"
- When to delete and restart vs. patch in place: a 2-criterion rule
- A `.driver-box` on accountability: smell tests are your job, not the AI's
- Try It: pick one paragraph of AI-generated spec text and run all 7 tests on it

### Chapter 9: The Engineering Handoff
**File:** `09-engineering-handoff.html`
**Goal:** Hand off AI-augmented specs without breaking trust with engineers. Make transparency the default and turn pushback into iteration.
**Topics:**
- What engineers actually want from a spec in 2026 &mdash; same as 2020 but with new failure modes
- Marking what's confirmed vs. assumed: a `.spec-snippet` showing inline annotations ("[CONFIRMED with X]", "[ASSUMPTION]")
- Transparency about AI-generated sections: when and how to disclose, why it builds trust
- Leaving open questions visible at the top of the spec rather than hiding them
- A `.dialogue-box` simulating an eng review where the engineer challenges an AI-generated edge case &mdash; PM responds well
- Responding to engineering pushback: when they're right, when you should hold the line, and how to tell
- The "expand the spec on review" anti-pattern: don't quietly invent new requirements via AI mid-review &mdash; reframe as "let me think about this and come back"
- A `.smell-test` for handoff: if the engineer asks "where did this come from?" and you can't answer, that's the test
- Review-comment etiquette: how to respond to comments without lengthy AI-generated essays
- Building team norms: what conventions help your team trust AI-augmented specs
- A `.driver-box` on accountability: you sign the spec; AI doesn't
- Try It: review the last spec you shipped; mark each line as confirmed/assumed; share with one engineer for a 10-minute calibration

### Chapter 10: Iterating After First Feedback
**File:** `10-iterating-after-feedback.html`
**Goal:** Use AI to incorporate feedback fast without losing the spec's through-line.
**Topics:**
- Feedback intake: capture all comments first, classify before changing anything
- Three buckets: **Must-fix** (blocks shipping), **Should-consider** (real point, may or may not change), **Out-of-scope** (good idea, different spec)
- Using AI to draft responses to comment threads: where it helps, where it sounds robotic
- Diff-style edit prompts: "here's the section, here's the comment &mdash; propose 2 alternative edits, mark trade-offs"
- A `.dialogue-box` showing a feedback batch turned into a clean diff via AI
- Keeping a decision history: a one-line "Changed X because Y" log at the top of the spec
- Stakeholder-specific re-framing: same spec, three audiences (eng / leadership / sales) &mdash; AI as translator, you as editor
- A `.spec-snippet.spec-before` / `.spec-snippet.spec-after` showing the same paragraph rewritten for engineering vs. for leadership
- When to rewrite vs. patch: a 30%-rule of thumb
- A `.smell-test` for iteration: if the spec's through-line shifted but no decision was logged, stop and reconcile
- A `.driver-box` on what doesn't change: the original problem; the original user; the call you made
- Try It: take a recent spec with feedback comments, classify each into the 3 buckets, draft an AI-assisted response to one comment, rewrite it in your voice

### Chapter 11: Your Personal AI PM Kit
**File:** `11-your-ai-pm-kit.html`
**Goal:** Build a reusable kit so you don't start from scratch each spec. Make the kit portable across tools.
**Topics:**
- Why a kit beats freelancing every spec: cumulative compounding, less re-explanation, more consistency
- The four parts of the kit: **Templates / Context packs / Prompt library / Naming conventions**
- Templates: PRD outline, AC checklist, edge-case prompt, risk register, retro one-pager
- Context packs: product overview, customer segments, glossary, prior decisions log, "what we don't do" list
- A `.spec-snippet` showing a context pack's structure (5 short sections, ~1 page)
- Prompt library: 10-15 reusable prompts, each with input shape, expected output, when to use
- A `.dialogue-box` showing the same prompt re-used three times across three different specs
- Naming conventions and storage: where the kit lives, how to find it, who else can edit it
- Tool-agnostic portability: same kit content works in Copilot, Windsurf, Claude, ChatGPT, Gemini &mdash; show three concrete attachment shapes
- Maintaining the kit: a 30-min monthly review, prune unused prompts, add new ones from recent wins
- A `.driver-box` on ownership: this is *your* kit, not the team's standard &mdash; teams are next chapter
- A `.smell-test` for kit health: if you haven't reused it in 30 days, prune it
- Try It: pick three of your most-used prompts and write each in template form &mdash; that's your kit v0.1

### Chapter 12: Habits That Keep You in Control
**File:** `12-habits-driving-seat.html`
**Goal:** Daily and weekly habits to stay the decision-maker as AI use compounds. Close the course with a forward-looking practice.
**Topics:**
- Why habits matter more than tools: the tools change every quarter; the practice persists
- The "what did I decide today" log: 1-2 lines per day, 5 minutes total &mdash; show a sample as a `.spec-snippet`
- Weekly spec review ritual: re-read each spec you shipped this week, mark the parts that were yours vs. AI-augmented
- Periodic prompt audit: every month, review your prompt library for staleness and creeping verbosity
- Cadence with engineering: a standing 15-minute window for spec calibration with one engineer per week
- Knowing when to set AI aside: meetings with humans, customer calls, post-incident reviews, scope-cutting calls
- Signs you're slipping into autopilot: AI tone in your own writing, fewer questions in reviews, no "hmm" moments &mdash; framed as a `.smell-test`, not a critique
- The AI fluency curve: what changes after 3 months, 6 months, 12 months of practice
- How the role grows from here: more time on judgment, less on prose &mdash; what to invest in
- A closing `.driver-box` re-stating the core promise of the course: you stayed in the driving seat, and your specs are the proof
- A short "what next" section: the course is done; what does the reader do tomorrow?
- Try It: tonight, write down today's three decisions in a single line each. That's day 1 of the log.
