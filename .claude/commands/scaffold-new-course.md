Generate a new course in the AI-Courses collection.

## What you need from the user:
Before generating anything, ask the user for:
1. **Course name** — the title (e.g., "How AI Actually Works")
2. **Directory name** — the folder name (e.g., `AI-Intro`)
3. **Target audience** — who is this for? (e.g., "non-technical PMs", "senior Android developers")
4. **Tone and style** — what's the vibe? (default: "For Dummies" — friendly, approachable)
5. **Chapter list** — titles and brief descriptions for each chapter (or topics to cover, and you'll propose chapters)
6. **Platform specifics** — any OS/tool constraints? (e.g., "Mac only", "Windsurf-specific")
7. **Custom CSS classes** — 2-4 unique box types for this course (e.g., `.analogy-box`, `.try-it-box`)
8. **Color scheme** — primary color for the course (must be distinct from existing courses: teal=AI-Intro, orange=AI-Harness, indigo=PM-Course)

## Steps to generate:

### 1. Create the directory structure
```
<DirectoryName>/
  CLAUDE.md
  .claude/
    commands/
      generate-next-chapter.md
      create-memory-map.md
  chapters/
    index.html
    assets/
      style.css
```

### 2. Create `chapters/assets/style.css`
- Fork the base CSS from an existing course (e.g., `AI-Intro/chapters/assets/style.css`)
- Change the color scheme (--color-primary, --color-primary-light, nav background, header gradient, pre background, thead, card-number)
- Add the custom CSS classes for this course (follow the pattern of `.analogy-box`, `.try-it-box`, etc.)
- Keep all shared classes (`.tip-box`, `.warning-box`, `.prompt-example`, `.comparison`, `.checklist`, `.highlight-box`, `.stats-grid`, `.stat-card`, `.tool-card`, `.workflow-steps`, `.chapter-card`, `.part-divider`, `.exercise-box`)
- Include dark theme variants for all custom classes
- Include all memory map CSS classes (`.map-header`, `.map-badge`, `.map-grid`, `.map-card`, `.map-card-icon`, `.map-card-title`, `.map-card-desc`, `.map-flow`, `.map-flow-step`, `.map-flow-arrow`, `.map-terms`, `.map-relationships`, `.map-rel-center`, `.map-rel-node`, `.map-big-idea`, `.map-timeline`, `.map-timeline-item`, `.map-compare`, `.map-quiz`, `.map-summary`, `.map-summary-item`, `.map-link`). Copy these from an existing course's style.css — they are identical across all courses and use CSS custom properties to auto-adapt to each course's color scheme.
- Add `.map-card`, `.map-big-idea`, `.map-quiz`, `.map-summary` to the smooth transitions selector list
- Include dark theme variants and responsive breakpoints for memory map classes
- Include smooth transitions, responsive breakpoints, and print styles

### 3. Create `chapters/index.html`
- Follow the pattern from existing courses (nav, hero section, chapter list with part dividers, footer, theme toggle script)
- All chapters start with `class="chapter-card pending"`
- Group chapters into Parts (3-5 parts)
- Use the course's color scheme in the hero gradient

### 4. Create `CLAUDE.md`
Include all of these sections (follow the AI-Intro/CLAUDE.md pattern):
- **Project Description** — audience, scope, style
- **Language Rules** — tone, terminology, audience address
- **HTML Conventions** — markup standards, file structure
- **Content Generation Rules** — include these exact rules:
  - All generated chapters MUST meet the 400-line minimum on the FIRST attempt. Count lines before finalizing. If under 400 lines, expand sections with examples, diagrams, tips, and detailed explanations before presenting.
  - Never pad content incrementally — produce complete, full-length content in one pass.
- **HTML Validation Rules** — include these exact rules:
  - Always close tip-box divs with `</div>`, never `</tip>`.
  - Validate all HTML tags are properly closed before completing a chapter.
- **Project Structure Rules** — include these exact rules:
  - Always check the current working directory and respect the explicit project path provided by the user. Do NOT search parent directories or sibling projects unless explicitly asked.
- **Cross-Reference Rules** — include these exact rules:
  - When generating multi-file series, ensure all cross-reference links between chapters are consistent. Use relative paths and verify link targets exist before finishing.
- **File Structure** — directory listing with descriptions
- **Progress Tracking** — checkbox list of all chapters (all `[ ]`)
- **Instructions for /generate-next-chapter** — step-by-step guide
- **CSS Classes for Content** — all available classes with descriptions
- **Content Guidelines** — required elements per chapter
- **Chapter Details** — detailed outline for EACH chapter with:
  - File name
  - Goal (one sentence)
  - Topics (6-12 bullet points of what to cover)

### 5. Create `.claude/commands/create-memory-map.md`
Copy the `create-memory-map.md` command from any existing course (e.g., `AI-Intro/.claude/commands/create-memory-map.md`). This file is identical across all courses — it reads the course's own `CLAUDE.md` for context and generates visual memory map pages in `chapters/maps/`.

### 6. Create `.claude/commands/generate-next-chapter.md`
Follow the established pattern:
- Read CLAUDE.md to find next incomplete chapter
- Read chapter details for topics
- Read style.css for CSS classes
- Read index.html for navigation
- Read previous chapter for context
- Generate 400-600 lines HTML with full content
- **Count lines before finalizing** — if under 400 lines, expand with examples, diagrams, tips, and detailed explanations before presenting. Never pad incrementally.
- **Validate HTML** — ensure all tags are properly closed. Close tip-box divs with `</div>`, never `</tip>`.
- **Verify cross-references** — ensure all links between chapters use relative paths and point to valid targets.
- Update CLAUDE.md progress tracking
- Update index.html to remove pending class
- Update previous chapter navigation

### 7. Update root `index.html`
Add the new course card to the appropriate group in the card view and the roadmap view of `/mnt/c/Projects/ps/AI-Courses/index.html`. Follow the existing patterns for both views.

## Important:
- The course must be **completely standalone** — no references to other courses or the root
- Each course has its **own color scheme** (distinct from existing courses)
- The CLAUDE.md chapter details must be **detailed enough** that `/generate-next-chapter` can produce complete chapters without additional context
- All files should be ready to use immediately after generation
- The index.html should be viewable in a browser right away (all chapters will show as pending/grayed out)
- The root `index.html` must be updated with the new course
