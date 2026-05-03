# AI-Courses

A collection of HTML-based courses in "For Dummies" style, each targeting a specific audience within the team. Every course is a standalone project with its own CLAUDE.md, chapters, styles, and `/generate-next-chapter` command.

## Courses

| Directory | Course | Audience | Chapters |
|-----------|--------|----------|----------|
| `AI-Intro/` | How AI Actually Works | Developers curious about AI internals | 10 |
| `AI-DeepDive/` | How AI Really Works: The Deep Dive | Developers who finished AI-Intro and want to go deeper | 13 |
| `AI-Frontier/` | AI in 2026: The State of the Frontier | Developers who finished AI-Intro/AI-DeepDive and want the current frontier | 13 |
| `AI-Ecosystem/` | The AI Developer's Toolkit | Developers navigating AI tools | 12 |
| `AI-Harness/` | AI Harness Engineering | Developers using AI coding tools | 11 |
| `AI-Advanced/` | AI-Driven Development | Senior engineers integrating AI | 17 |
| `PM-Course/` | Crash Course in Tech Skills | Non-technical PMs learning Windsurf, Git, OpenSpec | 14 |
| `AI-Workflow/` | Automating Your Dev Workflow with AI | Developers automating workflows with Claude Code | 15 |
| `Android-Debug/` | AI-Driven Debugging & Performance for Android | Android developers using AI to debug and optimize | 14 |
| `Android-OnDevice/` | On-Device AI for Android | Android developers shipping AI features on-device | 12 |
| `Android-AIFeatures/` | Building AI-Powered Features for Android | Android developers shipping user-facing AI features | 12 |
| `iOS-Debug/` | AI-Driven Debugging & Performance for iOS | iOS developers using AI to debug and optimize | 12 |
| `iOS-OnDevice/` | On-Device AI for iOS | iOS developers shipping AI features on-device | 12 |
| `iOS-AIFeatures/` | Building AI-Powered Features for iOS | iOS developers shipping user-facing AI features | 12 |
| `AI-Multimodal/` | Multimodal AI: Beyond Text | Developers exploring vision, audio, and video AI | 12 |
| `Claude-Architect/` | Claude Certified Architect: Foundations | Developers preparing for CCA-F certification | 14 |
| `Claude-Power/` | Claude Power User For Dummies | Developers mastering the full Claude ecosystem | 15 |
| `AI-Agents/` | Building AI Agents For Dummies | Developers building autonomous agent systems | 13 |
| `AI-RAG/` | RAG & Knowledge Systems For Dummies | All developers | 12 |
| `AI-PersonalAgents/` | Personal AI Agents For Dummies | Developers using AI agents in personal life | 12 |
| `AI-BuildIt/` | Build It With AI For Dummies | Developers wanting concrete AI project ideas | 12 |
| `AI-CodeReview/` | Reviewing AI Code For Dummies | Developers who use AI coding tools daily | 12 |
| `AI-LifeStrategy/` | Winning the AI Era For Dummies | Humans navigating career, money, health & purpose in the AI age | 12 |
| `AI-Engineering/` | AI-Ready Engineering For Dummies | Experienced devs configuring projects for AI productivity | 12 |
| `AI-Rewrite/` | Rewriting Apps With AI For Dummies | Experienced devs transforming existing codebases with AI | 12 |
| `AI-Factory/` | From Zero to App With AI For Dummies | Experienced devs building apps from scratch with AI roles | 13 |
| `AI-TechLeads/` | AI for Tech Leads For Dummies | Tech leads & engineering managers adopting AI on their teams | 12 |
| `AI-PromptEng/` | Prompt Engineering For Dummies | Developers, QAs, managers — everyone on the team | 12 |
| `Android-Quality/` | The Android Quality Stack For Dummies | Experienced Android devs bolting detekt/lint/StrictMode/etc. onto existing projects | 12 |
| `Android-DDD/` | Domain-Driven Design For Android Engineers | Senior Android developers learning DDD and applying it with AI | 12 |

## Conventions

Every course follows the same structure:
```
CourseName/
  CLAUDE.md                        — Project description, chapter details, progress tracking
  .claude/
    commands/
      generate-next-chapter.md     — Skill for chapter-by-chapter generation
      create-memory-map.md         — Skill for visual chapter summary generation
  chapters/
    index.html                     — Landing page with chapter navigation
    assets/
      style.css                    — Shared CSS with dark/light theme
    01-topic.html                  — Numbered chapter files
    02-topic.html
    ...
    maps/                          — Visual memory maps (generated on demand)
      01-topic-map.html
      02-topic-map.html
      ...
```

### Style rules
- **"For Dummies"** tone: friendly, approachable, heavy on analogies
- Each chapter: 400-600 lines of HTML
- Shared CSS with dark/light theme toggle (localStorage)
- Each course has a unique color scheme and 2-4 custom CSS classes
- Responsive design, print styles included

### Content Generation Rules
- All generated chapters MUST meet the 400-line minimum on the FIRST attempt. Draft the FULL content in one pass targeting ~10% above the minimum. Verify with `wc -l` before finalizing.
- If under the minimum, expand with substantive sections (examples, case studies, deep-dives) — not filler, not line-by-line padding.
- If you end up within 10–15% above the minimum, LEAVE IT ALONE. Do not trim to fit a tighter range. Only trim if you're significantly over (e.g., >25% above), and then cut whole sections, not individual lines.
- Never pad content incrementally — produce complete, full-length content in one pass.

### HTML Tag Hygiene
- Use `</div>` to close `<div>` elements — never invent tags like `</tip>`, `</note>`, or `</card>`. Closing tags must match opening tags exactly.
- After writing HTML chapters, grep for unmatched/custom closing tags before declaring done.
- Validate all HTML tags are properly closed before completing a chapter.

### Slash Command Scope Discipline
- `/scaffold-new-course` creates SCAFFOLDING only (CLAUDE.md, commands, index, chapter outlines) — do NOT generate chapter content in the same run.
- Chapter content is produced only via `/generate-next-chapter` (or equivalent) on explicit invocation.
- Standalone HTML pages should use inline JSON (not `fetch()`) so they work on `file://` URLs, and should not include nav links to pages outside their scope.

### Project Structure
- Always check the current working directory and respect the explicit project path provided by the user. Do NOT search parent directories or sibling projects unless explicitly asked.

### Cross-References
- When generating multi-file series, ensure all cross-reference links between chapters are consistent. Use relative paths and verify link targets exist before finishing.

### Memory Maps
- Each chapter can have a visual memory map — a single-page visual summary with concept cards, flow diagrams, timelines, quizzes, and key takeaways
- Generated on demand per chapter via `/create-memory-map <chapter-number>` from within the course directory
- Map files live in `chapters/maps/<NN>-<slug>-map.html`
- Maps link to their chapter and have prev/next map navigation
- index.html and chapter files get cross-links added when a map is generated

### Index File
- `index.html` — Full course catalog. Add new courses here.

### Creating a new course
Use `/scaffold-new-course` from this root directory. It will scaffold the full structure.

### Chapter Generation Resume Behavior
- `/generate-next-chapter` MUST start by reading the course's `CLAUDE.md` and finding the first chapter marked `[ ]` in the "Progress Tracking" section — that is the next chapter to generate. Never guess; never ask which chapter.
- If the user says **"continue"** or **"proceed"** (or similar bare continuations) with no other context while inside a course directory, treat it as an implicit `/generate-next-chapter` invocation: read the progress tracker, pick the first `[ ]` chapter, and generate it.
- After a chapter is generated, mark it `[x]` in the progress tracker in the same turn — this is what makes resume work across sessions, API errors, and rate limits.
