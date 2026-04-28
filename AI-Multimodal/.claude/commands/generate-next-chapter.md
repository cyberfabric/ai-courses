Generate the next chapter of "Multimodal AI: Beyond Text."

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
   - **NO math formulas** — explain everything through intuition and analogies
   - Use the correct CSS classes for examples, tips, warnings, exercises
   - **At least one `.modality-box`** highlighting a specific modality detail
   - **At least one `.pipeline-box`** showing a multi-step processing pipeline
   - **At least one `.try-it-box`** with a hands-on experiment
   - **At least one concrete example** connecting to tools the reader uses (Claude, GPT-4, Gemini, Whisper)
   - **At least one `.exercise-box`** with a hands-on exercise
   - Short paragraphs — walls of text kill understanding
   - Each chapter should end with a preview of how this connects to the next chapter
   - 400-600 lines of HTML
   - Code examples in Python (max 10-15 lines each)
   - Use CSS classes: `.modality-box`, `.pipeline-box`, `.try-it-box`, `.model-card`, `.prompt-example.good`, `.prompt-example.bad`, `.comparison`, `.tip-box`, `.warning-box`, `.exercise-box`, `.checklist`, `.highlight-box`, `.stats-grid`, `.stat-card`, `.tool-card`, `.workflow-steps`
   - Include the theme toggle button in the navigation

## Quality checks (before finalizing):

9. **Line count**: Count the lines in the generated HTML. If under 400 lines, expand sections with more examples, diagrams, tips, and detailed explanations. Never pad incrementally — produce complete, full-length content in one pass.
10. **HTML validation**: Verify all HTML tags are properly closed. Close tip-box divs with `</div>`, never `</tip>`.
11. **Cross-references**: Ensure all links between chapters use relative paths and point to valid targets. Verify prev/next links are consistent.

## After generating:

12. Update `CLAUDE.md` — change `[ ]` to `[x]` for the generated chapter
13. Update `chapters/index.html` — remove the `pending` class from that chapter's card
14. Update navigation on the previous chapter (add "next chapter" link if missing)

## Important:
- The chapter must be COMPLETE — not a placeholder, but actual content ready for reading
- Think of the reader as a smart developer who has used text-based AI but hasn't explored multimodal capabilities deeply
- Use real-world analogies to make abstract concepts click
- Read the previous chapter for a smooth transition
- Every major concept needs an analogy or concrete example
- Prioritize understanding over completeness — it's better to explain 5 things well than 10 things poorly
