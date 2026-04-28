Generate the next chapter of "Automating Your Dev Workflow with AI."

## Steps:

1. Read `CLAUDE.md` — find the first chapter marked with `[ ]` in the "Progress Tracking" section
2. Read the "Chapter Details" section in CLAUDE.md — find the description of that chapter (structure, topics, what to include)
3. Read `chapters/assets/style.css` — review available CSS classes for styling
4. Read `chapters/index.html` — review the structure and navigation
5. Read the previous chapter (if any) for context and smooth transition

## Generating the chapter:

6. Create the HTML file in `chapters/` with the correct filename
7. Follow the HTML conventions from CLAUDE.md:
   - UTF-8, HTML5 doctype, meta viewport
   - Link to `assets/style.css`
   - `<nav class="top-nav">` with navigation (index, prev, next) and theme toggle button:
     ```html
     <button class="theme-toggle" aria-label="Toggle theme">🌙</button>
     ```
   - `<header class="chapter-header">` with chapter number and title
   - `<main>` with full, rich content (400-600 lines)
   - `<footer>` with prev/next navigation
   - `<script>` before the closing `</body>` for theme toggle:
     ```html
     <script>
       const toggle = document.querySelector('.theme-toggle');
       const saved = localStorage.getItem('theme') || 'light';
       document.documentElement.setAttribute('data-theme', saved);
       toggle.textContent = saved === 'dark' ? '☀️' : '🌙';
       toggle.addEventListener('click', () => {
         const current = document.documentElement.getAttribute('data-theme');
         const next = current === 'dark' ? 'light' : 'dark';
         document.documentElement.setAttribute('data-theme', next);
         localStorage.setItem('theme', next);
         toggle.textContent = next === 'dark' ? '☀️' : '🌙';
       });
     </script>
     ```
8. Content requirements:
   - In English
   - **"For Dummies" style**: friendly, conversational, uses analogies and everyday examples
   - **All examples must use Claude Code** — never reference Windsurf, Codex, Cursor, Copilot, or other AI coding tools
   - Use the correct CSS classes for examples, tips, warnings, exercises
   - **At least one `.automation-box`** with an automation idea, recipe, or insight
   - **At least one `.before-after-box`** showing the manual vs automated version of a workflow
   - **At least one `.recipe-box`** with step-by-step instructions for setting up an automation
   - **At least one `.exercise-box`** with a hands-on exercise where the reader builds or configures something in Claude Code
   - Short paragraphs — walls of text kill understanding
   - Each chapter should end with a preview of how this connects to the next chapter
   - 400-600 lines of HTML
   - Keep code examples practical and real (bash, JSON, markdown — whatever fits the topic)
   - Use CSS classes: `.automation-box`, `.before-after-box` (with `.before` + `.after`), `.recipe-box`, `.prompt-example.good`, `.prompt-example.bad`, `.comparison`, `.tip-box`, `.warning-box`, `.exercise-box`, `.checklist`, `.highlight-box`, `.stats-grid`, `.stat-card`, `.tool-card`, `.workflow-steps`
   - Include the theme toggle button in the navigation

## After generating:

9. Update `CLAUDE.md` — change `[ ]` to `[x]` for the generated chapter
10. Update `chapters/index.html` — remove the `pending` class from that chapter's card
11. Update navigation on the previous chapter (add "next chapter" link if missing)

## Important:
- The chapter must be COMPLETE — not a placeholder, but actual content ready for reading
- Think of the reader as a smart Android developer who uses Claude Code daily but hasn't explored automation deeply
- Use real-world examples from developer workflows (PRs, code review, testing, CI/CD, documentation)
- Read the previous chapter for a smooth transition
- Every major concept needs a concrete example showing the automation in action
- Prioritize practical, copy-paste-ready examples over theory
- NEVER mention Windsurf, Codex, Cursor, Copilot, or any other AI coding tool — this course is Claude Code only
