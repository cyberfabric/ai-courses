Generate the next chapter of "Building AI Agents For Dummies."

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
   - **At least one `.architecture-box`** explaining an architectural concept or system design
   - **At least one `.agent-trace`** showing a step-by-step agent execution trace
   - **At least one `.pattern-box`** describing a reusable design pattern
   - **At least one `.exercise-box`** with a hands-on "Build It" exercise
   - Short paragraphs — walls of text kill understanding
   - Each chapter should end with a preview of how this connects to the next chapter
   - **400-600 lines of HTML** — count lines before finalizing. If under 400 lines, expand sections with examples, diagrams, tips, and detailed explanations before presenting. Never pad incrementally.
   - Include real code examples (Python preferred, TypeScript acceptable) — agents are built with code
   - Use CSS classes: `.architecture-box`, `.agent-trace`, `.pattern-box`, `.pitfall-box`, `.prompt-example.good`, `.prompt-example.bad`, `.comparison`, `.tip-box`, `.warning-box`, `.exercise-box`, `.checklist`, `.highlight-box`, `.stats-grid`, `.stat-card`, `.tool-card`, `.workflow-steps`
   - Include the theme toggle button in the navigation
   - **Validate HTML** — ensure all tags are properly closed. Close tip-box divs with `</div>`, never `</tip>`.
   - **Verify cross-references** — ensure all links between chapters use relative paths and point to valid targets.
   - **WebSearch is MANDATORY** — search for the latest agent frameworks, SDKs, patterns, and best practices before writing each chapter. The agent ecosystem evolves rapidly; content must reflect current state.

## After generating:

9. Update `CLAUDE.md` — change `[ ]` to `[x]` for the generated chapter
10. Update `chapters/index.html` — remove the `pending` class from that chapter's card
11. Update navigation on the previous chapter (add "next chapter" link if missing)

## Important:
- The chapter must be COMPLETE — not a placeholder, but actual content ready for reading
- Think of the reader as a developer who has used AI tools but never built an agent system
- Every architecture and pattern needs concrete code examples — agents are built, not theorized
- Read the previous chapter for a smooth transition
- **WebSearch before writing** — agent frameworks and SDKs change frequently. Always verify current APIs and capabilities.
- Balance theory with practice — explain WHY a pattern works, then show HOW to implement it
