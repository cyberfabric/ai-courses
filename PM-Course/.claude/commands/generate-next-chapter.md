Generate the next chapter of "Crash Course in Tech Skills: A PM's Guide to Windsurf, Git, and OpenSpec."

## Steps:

1. Read `CLAUDE.md` — find the first chapter marked with `[ ]` in the "Progress Tracking" section
2. Read the "Chapter Details" section in CLAUDE.md — find the description of that chapter (structure, topics, what to include)
3. Read `chapters/assets/style.css` — review available CSS classes for styling
4. Read `chapters/index.html` — review the structure and navigation
5. Read the previous chapter (if any) for context and smooth transition
6. For OpenSpec chapters (8-11), also read `presentation.html` for accurate OpenSpec workflow details

## Generating the chapter:

7. Create the HTML file in `chapters/` with the correct filename
8. Follow the HTML conventions from CLAUDE.md:
   - UTF-8, HTML5 doctype, meta viewport
   - Link to `assets/style.css`
   - `<nav class="top-nav">` with navigation (index, prev, next) and theme toggle button:
     ```html
     <button class="theme-toggle" aria-label="Toggle theme">&#127769;</button>
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
       toggle.textContent = saved === 'dark' ? '\u2600\uFE0F' : '\uD83C\uDF19';
       toggle.addEventListener('click', () => {
         const current = document.documentElement.getAttribute('data-theme');
         const next = current === 'dark' ? 'light' : 'dark';
         document.documentElement.setAttribute('data-theme', next);
         localStorage.setItem('theme', next);
         toggle.textContent = next === 'dark' ? '\u2600\uFE0F' : '\uD83C\uDF19';
       });
     </script>
     ```
9. Content requirements:
   - In English
   - **"For Dummies" style**: friendly, patient, encouraging — like a helpful colleague
   - **No jargon without explanation** — every technical term gets a plain-language definition
   - Use the correct CSS classes for examples, tips, warnings, exercises
   - **At least one `.real-world-box`** connecting a concept to something familiar (Google Docs, email, etc.)
   - **At least one `.try-it-box`** with a hands-on "your turn" moment (except conceptual chapters 3, 6, 8)
   - **At least one `.screenshot-box`** in hands-on chapters describing what the reader will see
   - **Use `.dont-panic-box`** when something might look intimidating
   - Short paragraphs — walls of text are intimidating
   - Each chapter should end with a preview connecting to the next chapter
   - 400-600 lines of HTML
   - All Git operations through Windsurf UI — NEVER show terminal git commands
   - BitBucket Server (self-hosted, not Cloud) — fork-based workflow
   - Mac-only instructions (Terminal.app, Finder, Cmd shortcuts)
   - Use CSS classes: `.screenshot-box`, `.try-it-box`, `.dont-panic-box`, `.real-world-box`, `.prompt-example.good`, `.prompt-example.bad`, `.comparison`, `.tip-box`, `.warning-box`, `.exercise-box`, `.checklist`, `.highlight-box`, `.stats-grid`, `.stat-card`, `.tool-card`, `.workflow-steps`
   - Include the theme toggle button in the navigation

## After generating:

10. Update `CLAUDE.md` — change `[ ]` to `[x]` for the generated chapter
11. Update `chapters/index.html` — remove the `pending` class from that chapter's card
12. Update navigation on the previous chapter (add "next chapter" link if missing)

## Important:
- The chapter must be COMPLETE — not a placeholder, but actual content ready for reading
- Think of the reader as a smart PM who has never used developer tools — explain everything from scratch
- Use real-world analogies to make abstract concepts click (Google Docs, email, filing cabinets)
- Read the previous chapter for a smooth transition
- Every major concept needs an analogy or connection to something the reader already knows
- Prioritize clarity over completeness — it's better to explain 5 things well than 10 things poorly
- NEVER condescend — the reader is smart, just unfamiliar with this world
- For OpenSpec chapters: use the latest commands (/opsx:propose, /opsx:apply, /opsx:archive) and align with presentation.html
