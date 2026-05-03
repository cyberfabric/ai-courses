Generate the next chapter of "Spec Craft With AI For Dummies."

## Steps:

1. Read `CLAUDE.md` — find the first chapter marked with `[ ]` in the "Progress Tracking" section
2. Read the "Chapter Details" section in CLAUDE.md — find the description of that chapter (goal and topics)
3. Read `chapters/assets/style.css` — review available CSS classes, including the four custom classes for this course: `.driver-box`, `.dialogue-box` (with `.dialogue-pm` and `.dialogue-ai` rows), `.spec-snippet` (with optional `.spec-before` and `.spec-after`), and `.smell-test`
4. Read `chapters/index.html` — review the structure and navigation
5. Read the previous chapter (if any) for context and a smooth transition

## Generating the chapter:

6. Create the HTML file in `chapters/` with the correct filename (matching the file name in the chapter outline)
7. Follow the HTML conventions from CLAUDE.md:
   - UTF-8, HTML5 doctype, meta viewport
   - Link to `assets/style.css`
   - `<nav class="top-nav">` with navigation (index, prev, next) and theme toggle button:
     ```html
     <button class="theme-toggle" aria-label="Toggle theme">🌙</button>
     ```
   - `<header class="chapter-header">` with chapter number and title
   - `<main>` with full, rich content (400-600 lines, aim ~440-460)
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
   - **"For Dummies" style** — friendly, encouraging, second person, analogy-heavy
   - **Tool-agnostic** — name at least two different AI tools (Copilot / Windsurf / Claude / ChatGPT / Gemini) when concrete examples are needed; never depend on one tool's UI
   - **No blame** — describe patterns as "what works well", never as "what PMs do wrong"
   - **At least one `.driver-box`** flagging a decision the reader, not the AI, must make
   - **At least one concrete example** showing the workflow on a realistic product scenario
   - **At least one `.exercise-box`** with a "Try It" the reader can do this week
   - **At least one `.dialogue-box`** in chapters 3-10 showing a multi-turn PM ↔ AI exchange (use `<div class="dialogue-pm">...</div>` and `<div class="dialogue-ai">...</div>` for rows)
   - Use `.spec-snippet` for PRD/spec excerpts; pair `.spec-before` / `.spec-after` to show transformations
   - Use `.smell-test` for short validation checks (encouraging tone)
   - Short paragraphs — walls of text kill understanding
   - End each chapter with a one-paragraph preview of how it connects to the next chapter
   - Keep code/snippet examples minimal — this course is about specs, not code
   - Include the theme toggle button in the navigation

## After generating:

9. Update `CLAUDE.md` — change `[ ]` to `[x]` for the generated chapter in the "Progress Tracking" section (this is what makes resume work across sessions)
10. Update `chapters/index.html` — remove the `pending` class from that chapter's card
11. Update navigation on the previous chapter (add or fix the "next chapter" link)

## Validation before finishing:

- Run `wc -l <file>` — must be between 400 and 600 (≥ 400 and ≤ 600)
- Grep for stray custom closing tags: `grep -E "</tip>|</note>|</card>|</box>|</driver>|</dialogue>|</spec>|</smell>" <file>` — should return nothing
- All cross-references between chapters use relative paths and point to existing files

## Important:
- The chapter must be COMPLETE — not a placeholder, but actual content ready for reading
- The reader is **tech-fluent but non-coding** — PM, PO, BA, project manager, business owner. Don't teach them what a PR or API is, but don't show them code either.
- Frame everything around **staying in the driving seat** — every chapter should reinforce that AI accelerates but doesn't replace PM judgment
- Read the previous chapter for a smooth transition
- Prioritize understanding and practical use over completeness — better to show 4 things deeply than 10 things shallowly
- Never produce content that could read as blame, critique, or "PMs are doing it wrong" — always frame as "here's what high-leverage PMs do"
