Generate the next chapter of "Domain-Driven Design For Android Engineers."

## Steps:

1. Read `CLAUDE.md` — find the first chapter marked with `[ ]` in the "Progress Tracking" section
2. Read the "Chapter Details" section in CLAUDE.md — find the description of that chapter (goal, topics, what to include)
3. Read `chapters/assets/style.css` — review available CSS classes for styling
4. Read `chapters/index.html` — review the chapter list and navigation order
5. Read the previous chapter (if any) for context and a smooth transition

## Generating the chapter:

6. Create the HTML file in `chapters/` with the correct filename (matches the entry in CLAUDE.md and index.html)
7. Follow the HTML conventions from CLAUDE.md:
   - UTF-8, HTML5 doctype, meta viewport
   - Link to `assets/style.css`
   - `<nav class="top-nav">` with navigation (contents, prev, next) and a theme toggle button:
     ```html
     <button class="theme-toggle" aria-label="Toggle theme">🌙</button>
     ```
   - `<header class="chapter-header">` with chapter number and title
   - `<main>` with full, rich content (400-600 lines, target ~440-460 on the first pass)
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
   - **"For Dummies" style** — friendly, peer-to-peer, heavy on Android-specific analogies and worked examples
   - Audience: senior Android engineers who already ship production apps
   - Use the correct CSS classes for examples, callouts, and exercises
   - **At least one `.domain-box`** showing a Kotlin domain-model snippet (entity, value object, aggregate, etc.) — uses inner `.model-text` for monospace code
   - **At least one `.language-box`** introducing a key term and "do not say" alternatives — uses inner `.term` and `.do-not-say`
   - **At least one `.context-box` OR `.android-box`** anchoring the concept in a bounded context or in Android-specific terms (Gradle modules, MVI/MVVM, Room, Retrofit, coroutines, Hilt) — `.android-box` uses inner `.android-code` for monospace code
   - **At least one `.exercise-box`** with a hands-on action the reader can take in their own codebase today
   - **At least one `.tip-box` and one `.warning-box`** — DDD has subtle traps; flag them
   - Worked code examples in **Kotlin**, idiomatic for modern Android
   - Short paragraphs — walls of text kill understanding
   - Each chapter ends with a brief "What's Next" preview connecting to the following chapter
   - 400-600 lines of HTML
   - Available CSS classes: `.domain-box`, `.language-box`, `.context-box`, `.android-box`, `.tip-box`, `.warning-box`, `.exercise-box`, `.highlight-box`, `.prompt-example.good`, `.prompt-example.bad`, `.comparison`, `.checklist`, `.stats-grid`, `.stat-card`, `.tool-card`, `.workflow-steps`, `.step`, `.step-arrow`
   - Include the theme toggle button in the navigation

9. Validate before finalizing:
   - Run `wc -l chapters/<NN>-*.html` — must be ≥400. If under, expand sections (add another `.domain-box` worked example, deepen the Android case study, expand the exercise) — never pad incrementally.
   - Grep for unmatched custom closing tags (`</tip>`, `</domain>`, `</context>`, etc.) — every `<div>` must close with `</div>`.
   - Verify cross-references: any `<a href="NN-...html">` must point to an existing chapter file.

## After generating:

10. Update `CLAUDE.md` — change `[ ]` to `[x]` for the generated chapter
11. Update `chapters/index.html` — remove the `pending` class from that chapter's card (`class="chapter-card pending"` → `class="chapter-card"`)
12. Update navigation on the previous chapter (add or correct the "next chapter" link if missing)

## Important:
- The chapter must be COMPLETE on the first pass — not a placeholder, but actual content ready for reading
- The reader is a senior Android engineer; do not over-explain Kotlin or AndroidX basics, but DO explain DDD vocabulary the first time it appears
- Use real Kotlin code — idiomatic, compilable-looking — not pseudocode
- Read the previous chapter for a smooth narrative transition
- Every DDD concept needs a concrete Android example (Gradle module, Room entity, MVI state, etc.)
- Prioritize practical, immediately usable knowledge over theory
- The reader should be able to apply something from the chapter to their own codebase TODAY
