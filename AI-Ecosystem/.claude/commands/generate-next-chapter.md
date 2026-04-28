Generate the next chapter of "The AI Developer's Toolkit: A Practical Guide to the Ecosystem."

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
   - **"For Dummies" style**: friendly, practical, opinionated — like a colleague explaining tools over lunch
   - Use the correct CSS classes for examples, tips, warnings, exercises
   - **For tool chapters: always answer the four questions**:
     1. What is it? (one sentence)
     2. What does it do? (core functionality)
     3. When would I use it? (practical scenarios)
     4. When should I NOT use it? (anti-patterns, overkill)
   - **Every tool chapter MUST include a `.why-care-box`** answering "Why should I, as a developer, care?"
   - **Every tool chapter MUST include a `.use-skip-box`** with `.use-it` and `.skip-it` sections
   - **At least one code example per chapter** (Python, 10-20 lines max, illustrative not tutorial)
   - **At least one `.exercise-box`** with a practical exploration task
   - Short paragraphs — keep it scannable
   - Each chapter should end with a preview of what's coming next
   - 400-600 lines of HTML
   - Use CSS classes: `.why-care-box`, `.use-skip-box`, `.prompt-example.good`, `.prompt-example.bad`, `.comparison`, `.tip-box`, `.warning-box`, `.exercise-box`, `.checklist`, `.highlight-box`, `.stats-grid`, `.stat-card`, `.tool-card`, `.workflow-steps`
   - Include the theme toggle button in the navigation

## After generating:

9. Update `CLAUDE.md` — change `[ ]` to `[x]` for the generated chapter
10. Update `chapters/index.html` — remove the `pending` class from that chapter's card
11. Update navigation on the previous chapter (add "next chapter" link if missing)

## Important:
- The chapter must be COMPLETE — not a placeholder, but actual content ready for reading
- Think of the reader as a smart developer who knows how to code but has never used these AI tools
- Be opinionated: recommend, don't just list features
- Keep code examples SHORT — show the shape, not the full tutorial
- Read the previous chapter for a smooth transition
- Always connect back to the reader's world: "As an Android dev, you might use this for..."
- Honestly mention the learning curve and gotchas for each tool
- Code examples should use Python (that's what the ecosystem uses)
