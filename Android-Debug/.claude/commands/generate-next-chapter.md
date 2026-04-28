Generate the next chapter of "AI-Driven Debugging & Performance for Android."

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
   - **At least one `.debug-trace`** with a stacktrace, logcat output, or profiler output with AI analysis
   - **At least one `.root-cause`** with a root cause analysis finding
   - **At least one `.fix-pattern`** with a common fix pattern or solution
   - **At least one `.performance-metric`** with before/after metrics (where applicable to the chapter)
   - **At least one `.exercise-box`** with a hands-on exercise where the reader debugs or profiles something real
   - Short paragraphs — walls of text kill understanding
   - Each chapter should end with a preview of how this connects to the next chapter
   - 400-600 lines of HTML
   - Keep code examples practical and real (Kotlin, logcat output, stacktraces, profiler data, Gradle config — whatever fits the topic)
   - Use CSS classes: `.debug-trace`, `.performance-metric` (with `.metric-before` + `.metric-after`), `.root-cause`, `.fix-pattern`, `.prompt-example.good`, `.prompt-example.bad`, `.comparison`, `.tip-box`, `.warning-box`, `.exercise-box`, `.checklist`, `.highlight-box`, `.stats-grid`, `.stat-card`, `.tool-card`, `.workflow-steps`
   - Include the theme toggle button in the navigation

## After generating:

9. Update `CLAUDE.md` — change `[ ]` to `[x]` for the generated chapter
10. Update `chapters/index.html` — remove the `pending` class from that chapter's card
11. Update navigation on the previous chapter (add "next chapter" link if missing)

## Important:
- The chapter must be COMPLETE — not a placeholder, but actual content ready for reading
- Think of the reader as a smart Android developer who uses Claude Code daily and wants to debug/optimize faster
- Use real Android debugging scenarios: actual crash patterns, real profiler output formats, genuine performance issues
- Read the previous chapter for a smooth transition
- Every major concept needs a concrete example showing AI-assisted debugging in action
- Prioritize practical, copy-paste-ready examples over theory
- NEVER mention Windsurf, Codex, Cursor, Copilot, or any other AI coding tool — this course is Claude Code only
- Every chapter should teach the reader to build at least one reusable Claude Code skill (/command)
