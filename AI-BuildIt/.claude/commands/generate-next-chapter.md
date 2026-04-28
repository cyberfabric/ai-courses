Generate the next chapter of "Build It With AI For Dummies."

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
   - **"For Dummies" style**: friendly, conversational, like an excited friend pitching project ideas at a hackathon
   - Every project idea must be concrete and actionable — name, difficulty, tech stack, pitch
   - Use the correct CSS classes for examples, tips, warnings, exercises
   - **At least 3 `.project-card` boxes** per chapter, each with a project name, difficulty badge, stack pills, and description
   - **At least 1 `.spark-box`** per chapter with "what if you also..." expansion ideas
   - **At least 1 `.exercise-box`** per chapter with a "Start Building" hands-on task
   - Short paragraphs — walls of text kill understanding
   - Each chapter should end with a "Pick Your Project" section encouraging the reader to choose one idea and start
   - **400-600 lines of HTML** — count lines before finalizing. If under 400 lines, expand sections with examples, diagrams, tips, and detailed explanations before presenting. Never pad content incrementally — produce complete, full-length content in one pass.
   - Use CSS classes: `.project-card`, `.spark-box`, `.stack-pills`, `.prompt-example.good`, `.prompt-example.bad`, `.comparison`, `.tip-box`, `.warning-box`, `.exercise-box`, `.checklist`, `.highlight-box`, `.stats-grid`, `.stat-card`, `.tool-card`, `.workflow-steps`
   - Include the theme toggle button in the navigation
   - **Validate HTML** — ensure all tags are properly closed. Close tip-box divs with `</div>`, never `</tip>`.
   - **Verify cross-references** — ensure all links between chapters use relative paths and point to valid targets.

## After generating:

9. Update `CLAUDE.md` — change `[ ]` to `[x]` for the generated chapter
10. Update `chapters/index.html` — remove the `pending` class from that chapter's card
11. Update navigation on the previous chapter (add "next chapter" link if missing)

## Important:
- The chapter must be COMPLETE — not a placeholder, but actual content ready for reading
- Think of the reader as a developer who has Claude Code and wants to build something cool RIGHT NOW
- Every project idea needs: what it does, why it's useful, tech stack, and difficulty (Weekend / Week / Month)
- Use `.project-card` for each project idea with `.project-name`, `.project-difficulty`, `.stack-pills .pill`, and `.project-desc`
- Use `.spark-box` for "and you could also..." expansion ideas
- All examples should assume Claude Code / Claude API as the AI backbone
- Read the previous chapter for a smooth transition
- Prioritize inspiring the reader to BUILD — every section should make them want to open their terminal
