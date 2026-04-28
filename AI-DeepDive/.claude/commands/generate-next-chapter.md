Generate the next chapter of "How AI Really Works: The Deep Dive."

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
   - `<main>` with full, rich content (target ~600 lines; do NOT cut if under 1000)
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
   - **"For Dummies" style with numbers**: friendly, conversational, uses analogies AND step-by-step numeric examples
   - **A+B approach**: always show the intuition FIRST (Level A), then follow immediately with a numeric walkthrough (Level B), then state the takeaway
   - Use small, friendly numbers: single digits where possible, max 2 decimal places
   - Use HTML tables (not ASCII art) for matrices and numeric grids
   - Use `<code>` for inline numbers and values
   - Use the correct CSS classes for examples, tips, warnings, exercises
   - **At least one `.math-walkthrough`** with a complete step-by-step numeric example
   - **At least one `.operation-box`** explaining a core operation conceptually
   - **At least one `.intuition-box`** connecting the numbers back to plain-English meaning
   - **At least one `.checkpoint-box`** with a quick self-test question
   - **At least one `.exercise-box`** with a hands-on computation the reader does themselves
   - Short paragraphs — walls of text kill understanding
   - Each chapter should end with a preview of how this connects to the next chapter
   - **Target ~600 lines of HTML** — but do NOT cut content if the chapter is under 1000 lines. Quality and completeness matter more than a hard line limit.
   - Keep code examples minimal (Python if needed, max 10-15 lines)
   - Use CSS classes: `.math-walkthrough`, `.operation-box`, `.intuition-box`, `.checkpoint-box`, `.prompt-example.good`, `.prompt-example.bad`, `.comparison`, `.tip-box`, `.warning-box`, `.exercise-box`, `.checklist`, `.highlight-box`, `.stats-grid`, `.stat-card`, `.tool-card`, `.workflow-steps`
   - Include the theme toggle button in the navigation
   - Cross-reference AI-Intro where appropriate: `<div class="tip-box"><strong>Companion:</strong> This expands on <a href="../../AI-Intro/chapters/NN-slug.html">AI-Intro Ch N: Title</a>.</div>`
   - When showing a numeric walkthrough, use the pattern: "Here's what we're doing" → "Here are the numbers" → "Here's what that means"

## After generating:

9. Update `CLAUDE.md` — change `[ ]` to `[x]` for the generated chapter
10. Update `chapters/index.html` — remove the `pending` class from that chapter's card
11. Update navigation on the previous chapter (add "next chapter" link if missing)

## Important:
- The chapter must be COMPLETE — not a placeholder, but actual content ready for reading
- Think of the reader as a smart developer who completed AI-Intro and wants to go deeper — they know the analogies, now they want to see the numbers
- Every major concept needs BOTH intuition (Level A) AND a numeric example (Level B)
- Read the previous chapter for a smooth transition
- Prioritize clarity over brevity — a well-explained numeric walkthrough is more valuable than covering more topics poorly
