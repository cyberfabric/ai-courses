Generate the next chapter of "AI-Driven Development: A Practical Guide for Software Engineers."

## Steps:

1. Read `CLAUDE.md` — find the first chapter marked with `[ ]` in the "Progress Tracking" section
2. Read the "Chapter Details" section in CLAUDE.md — find the description of that chapter (structure, topics, what to include)
3. Read `chapters/assets/style.css` — review available CSS classes for styling
4. Read `chapters/index.html` — review the structure and navigation
5. Read the previous chapter (if any) for context and smooth transition
6. Read relevant resource files from `resources/` for links to reference in the content

## Generating the chapter:

7. Create the HTML file in `chapters/` with the correct filename
8. Follow the HTML conventions from CLAUDE.md:
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
9. Content requirements:
   - In English
   - Use the correct CSS classes for examples, tips, warnings, exercises
   - Include examples from **DIFFERENT engineering roles** (minimum 3 roles per chapter)
   - Practical and direct — written for experienced developers
   - Explains AI-specific concepts thoroughly but doesn't patronize on programming basics
   - 400-600 lines of HTML
   - Use `.profession-tag` to label which role each example is for
   - Include at least one code example or realistic code snippet per chapter
   - Include at least one `.exercise-box` with a hands-on exercise
   - Reference external resources from `resources/` files where relevant

## After generating:

10. Update `CLAUDE.md` — change `[ ]` to `[x]` for the generated chapter
11. Update `chapters/index.html` — remove the `pending` class from that chapter's card
12. Update navigation on the previous chapter (add "next chapter" link if missing)

## Important:
- The chapter must be COMPLETE — not a placeholder, but actual content ready for reading
- Use examples from at least 3 different engineering roles
- Use CSS classes: `.prompt-example.good`, `.prompt-example.bad`, `.comparison`, `.tip-box`, `.warning-box`, `.exercise-box`, `.checklist`, `.highlight-box`, `.stats-grid`, `.stat-card`, `.profession-tag`, `.tool-card`, `.workflow-steps`
- Include the theme toggle button in the navigation
- Read the previous chapter for a smooth transition
- Code examples should use real languages: Kotlin, Python, TypeScript, YAML, Bash
