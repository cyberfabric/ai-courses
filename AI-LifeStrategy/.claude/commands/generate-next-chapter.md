Generate the next chapter of "Winning the AI Era For Dummies."

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
   - **"For Dummies" style**: friendly, direct, like a sharp friend giving life advice over beers
   - Every section must be practical and actionable — strategies, not philosophy
   - Use the correct CSS classes for examples, tips, warnings, exercises
   - **At least one `.strategy-box`** per chapter — a concrete life strategy move
   - **At least one `.reality-check-box`** per chapter — a hard truth or myth-busting moment
   - **At least one `.action-plan`** per chapter — structured steps with timelines using `.action-step`, `.step-number`, `.step-content`, `.step-timeline`
   - **At least one `.ai-leverage-box`** per chapter — specifically how AI amplifies this topic
   - **At least one `.exercise-box`** per chapter — hands-on task the reader does immediately
   - Short paragraphs — walls of text kill momentum
   - Each chapter should end with a preview connecting to the next chapter
   - **400-600 lines of HTML** — count lines before finalizing. If under 400 lines, expand sections with examples, diagrams, tips, and detailed explanations before presenting. Never pad content incrementally — produce complete, full-length content in one pass.
   - Use CSS classes: `.strategy-box`, `.reality-check-box`, `.action-plan`, `.ai-leverage-box`, `.prompt-example.good`, `.prompt-example.bad`, `.comparison`, `.tip-box`, `.warning-box`, `.exercise-box`, `.checklist`, `.highlight-box`, `.stats-grid`, `.stat-card`, `.tool-card`, `.workflow-steps`
   - Include the theme toggle button in the navigation
   - **Validate HTML** — ensure all tags are properly closed. Close tip-box divs with `</div>`, never `</tip>`.
   - **Verify cross-references** — ensure all links between chapters use relative paths and point to valid targets.

## After generating:

9. Update `CLAUDE.md` — change `[ ]` to `[x]` for the generated chapter
10. Update `chapters/index.html` — remove the `pending` class from that chapter's card
11. Update navigation on the previous chapter (add "next chapter" link if missing)

## Important:
- The chapter must be COMPLETE — not a placeholder, but actual content ready for reading
- Think of the reader as a developer who is smart but anxious about their future in an AI world
- This is LIFE strategy, not coding tutorials — career, money, health, relationships, purpose
- Every section should give actionable advice, not vague motivational fluff
- Use real data, trends, and concrete examples — not hand-waving predictions
- Address AI anxiety honestly — acknowledge fears, then provide practical paths forward
- Read the previous chapter for a smooth transition
- Every major claim needs supporting evidence or a concrete example
- End each chapter with a connection to the next topic
