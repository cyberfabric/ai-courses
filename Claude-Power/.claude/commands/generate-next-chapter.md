Generate the next chapter of "Claude Power User For Dummies."

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
   - Use the correct CSS classes for examples, tips, warnings, exercises
   - **At least one `.power-tip`** with a power user technique
   - **At least one `.claude-example`** showing a real Claude interaction
   - **At least one `.shortcut-box`** with a quick action or keyboard shortcut
   - **At least one `.exercise-box`** with a hands-on exercise
   - Short paragraphs — walls of text kill understanding
   - Each chapter should end with a preview of how this connects to the next chapter
   - **400-600 lines of HTML** — count lines before finalizing. If under 400 lines, expand sections with examples, diagrams, tips, and detailed explanations before presenting. Never pad incrementally.
   - Use CSS classes: `.power-tip`, `.shortcut-box`, `.before-after`, `.claude-example`, `.prompt-example.good`, `.prompt-example.bad`, `.comparison`, `.tip-box`, `.warning-box`, `.exercise-box`, `.checklist`, `.highlight-box`, `.stats-grid`, `.stat-card`, `.tool-card`, `.workflow-steps`
   - Include the theme toggle button in the navigation
   - **Validate HTML** — ensure all tags are properly closed. Close tip-box divs with `</div>`, never `</tip>`.
   - **Verify cross-references** — ensure all links between chapters use relative paths and point to valid targets.
   - **WebSearch is MANDATORY** — search for the latest Claude features, updates, and best practices before writing each chapter. Claude evolves rapidly; content must reflect the current state of the platform.

## After generating:

9. Update `CLAUDE.md` — change `[ ]` to `[x]` for the generated chapter
10. Update `chapters/index.html` — remove the `pending` class from that chapter's card
11. Update navigation on the previous chapter (add "next chapter" link if missing)

## Important:
- The chapter must be COMPLETE — not a placeholder, but actual content ready for reading
- Think of the reader as a developer who already uses Claude daily but only scratches the surface
- Every technique should have a concrete example showing the before/after improvement
- Read the previous chapter for a smooth transition
- **WebSearch before writing** — Claude features change frequently. Always verify current capabilities.
- Prioritize practical, immediately-usable techniques over theory
