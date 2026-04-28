Generate the next chapter of "From Zero to App With AI For Dummies."

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
   - **"For Dummies" style**: visionary but practical — orchestrating AI as specialized team members
   - Assume the reader already knows Clean Architecture, MVI, Room, Hilt, Compose
   - Focus on the AI PIPELINE: roles, skills, orchestration, handoffs
   - **At least 1 `.role-card`** per chapter defining or referencing a role
   - **At least 1 `.artifact-box`** per chapter showing a generated artifact
   - **At least 1 `.exercise-box`** per chapter building or customizing a role skill
   - Short paragraphs — walls of text kill understanding
   - **400-600 lines of HTML** — count lines before finalizing. If under 400 lines, expand sections with examples, diagrams, tips, and detailed explanations before presenting. Never pad content incrementally — produce complete, full-length content in one pass.
   - Use CSS classes: `.role-card`, `.pipeline-stage`, `.artifact-box`, `.orchestration-trace`, `.prompt-example.good`, `.prompt-example.bad`, `.comparison`, `.tip-box`, `.warning-box`, `.exercise-box`, `.checklist`, `.highlight-box`, `.stats-grid`, `.stat-card`, `.tool-card`, `.workflow-steps`
   - Include the theme toggle button in the navigation
   - **Validate HTML** — ensure all tags are properly closed. Close tip-box divs with `</div>`, never `</tip>`.
   - **Verify cross-references** — ensure all links between chapters use relative paths and point to valid targets.

## After generating:

9. Update `CLAUDE.md` — change `[ ]` to `[x]` for the generated chapter
10. Update `chapters/index.html` — remove the `pending` class from that chapter's card
11. Update navigation on the previous chapter (add "next chapter" link if missing)

## Important:
- The chapter must be COMPLETE — not a placeholder, but actual content ready for reading
- NEVER explain Android architecture patterns — assume the reader knows them
- Focus on AI orchestration: roles, skills, handoffs, artifacts, pipelines
- Every skill file shown should be complete enough to copy-paste and run
- Reference other courses with inline links: "For more on [topic], see [Course] Ch N"
- Read the previous chapter for a smooth transition
