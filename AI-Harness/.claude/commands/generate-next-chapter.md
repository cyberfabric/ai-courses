Generate the next chapter of "AI Harness Engineering: What's Really Running Your AI Tools."

## Steps:

1. Read `CLAUDE.md` — find the first chapter marked with `[ ]` in the "Progress Tracking" section
2. Read the "Chapter Details" section in CLAUDE.md — find the description of that chapter (structure, topics, what to include)
3. Read `chapters/assets/style.css` — review available CSS classes for styling
4. Read `chapters/index.html` — review the structure and navigation
5. Read the previous chapter (if any) for context and smooth transition

## Research:

6. **Search the web** for the latest information on the chapter's topics. Key sources to check:
   - Anthropic docs (anthropic.com/engineering/)
   - OpenAI docs (openai.com/index/)
   - Cursor blog (cursor.com/blog/)
   - Martin Fowler (martinfowler.com/articles/exploring-gen-ai/)
   - Recent Medium articles on harness engineering
   - ArXiv papers on AI coding agents
7. Use the research to enrich the chapter with accurate, up-to-date details

## Generating the chapter:

8. Create the HTML file in `chapters/` with the correct filename
9. Follow the HTML conventions from CLAUDE.md:
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
10. Content requirements:
   - In English
   - **"For Dummies" style**: friendly, practical, opinionated — like a colleague showing you the engine room
   - Use the correct CSS classes for examples, tips, warnings, exercises
   - **Every chapter MUST include at least one `.inside-look-box`** showing what the harness does internally during a user action — this is the signature element of the course
   - **Chapters 3, 4, 5, 7, and 8 MUST include at least one `.compare-box`** comparing how different tools handle the same concept
   - **At least one `.exercise-box`** with a practical exploration task
   - **At least one analogy** woven into the prose
   - Code examples should be **config snippets** (JSON, YAML, markdown, shell commands), NOT Python
   - Short paragraphs — keep it scannable
   - Each chapter should end with a preview of what's coming next
   - 400-600 lines of HTML
   - Use CSS classes: `.inside-look-box`, `.compare-box`, `.prompt-example.good`, `.prompt-example.bad`, `.comparison`, `.tip-box`, `.warning-box`, `.exercise-box`, `.checklist`, `.highlight-box`, `.stats-grid`, `.stat-card`, `.tool-card`, `.workflow-steps`
   - Include the theme toggle button in the navigation

## After generating:

11. Update `CLAUDE.md` — change `[ ]` to `[x]` for the generated chapter
12. Update `chapters/index.html` — remove the `pending` class from that chapter's card
13. Update navigation on the previous chapter (add "next chapter" link if missing)

## Important:
- The chapter must be COMPLETE — not a placeholder, but actual content ready for reading
- Think of the reader as a smart developer who uses AI tools daily but has never thought about what's happening behind the scenes
- Be opinionated: recommend, don't just list features
- Keep code examples SHORT — show the shape of a config or command, not a full implementation
- Read the previous chapter for a smooth transition
- Always connect back to the reader's experience: "When you type X in Claude Code, here's what actually happens..."
- Show how concepts manifest in multiple tools (Claude Code + at least one other)
- Honestly mention tradeoffs, limitations, and anti-patterns
- Code examples should use config formats (JSON, YAML, markdown, shell) — this course is about understanding and configuring harnesses, not writing ML code
