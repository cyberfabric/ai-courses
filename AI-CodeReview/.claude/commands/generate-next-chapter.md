Generate the next chapter of "Reviewing AI Code For Dummies."

## Steps:

1. Read `CLAUDE.md` — find the first chapter marked with `[ ]` in the "Progress Tracking" section
2. Read the "Chapter Details" section in CLAUDE.md — find the description of that chapter (structure, topics, what to include)
3. Read `chapters/assets/style.css` — review available CSS classes for styling
4. Read `chapters/index.html` — review the structure and navigation
5. Read the previous chapter (if any) for context and smooth transition

## Research:

6. **Search the web** for the LATEST 2026 information on the chapter's topics. This is CRITICAL — the user wants cutting-edge 2026 content, not pre-2026 training data. Key sources to check:
   - Addy Osmani's Substack (addyo.substack.com) — "Code Review in the Age of AI" and "Avoiding Skill Atrophy"
   - Anthropic research (anthropic.com/research/) — AI coding skills study
   - Claude Code docs (code.claude.com/docs/) — /code-review feature
   - CodeRabbit blog (coderabbit.ai/blog/)
   - Qodo blog (qodo.ai/blog/) — AI code review tools and patterns
   - DEV Community articles on AI code review 2026
   - InfoQ, InfoWorld articles on skill atrophy and AI coding
   - ArXiv papers on AI-generated code quality
   - Medium articles on reviewing AI code (2025-2026)
7. Use the research to enrich the chapter with accurate, up-to-date details. Cite specific stats, tool versions, and research findings from 2025-2026.

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
   - **"For Dummies" style**: friendly, practical, opinionated — like a senior dev showing you how they actually review code
   - Use the correct CSS classes for examples, tips, warnings, exercises
   - **Every chapter MUST include at least one `.review-checklist`** with a structured checklist for that chapter's topic — this is the signature element of the course
   - **Every chapter MUST include at least one `.red-flag-box`** highlighting a common mistake or dangerous pattern in AI-generated code
   - **At least one `.ai-tell-box`** showing a recognizable pattern in AI-generated code
   - **At least one `.practice-drill`** with a concrete exercise the reader can do right now
   - **At least one `.exercise-box`** with a practical, hands-on task
   - **At least one analogy** woven into the prose
   - Code examples should be **real review scenarios** (diffs, PR comments, shell commands), NOT abstract examples
   - Short paragraphs — keep it scannable
   - Each chapter should end with a preview of what's coming next
   - 400-600 lines of HTML
   - Use CSS classes: `.review-checklist`, `.red-flag-box`, `.ai-tell-box`, `.practice-drill`, `.prompt-example.good`, `.prompt-example.bad`, `.comparison`, `.tip-box`, `.warning-box`, `.exercise-box`, `.checklist`, `.highlight-box`, `.stats-grid`, `.stat-card`, `.tool-card`, `.workflow-steps`
   - Include the theme toggle button in the navigation
   - **IMPORTANT**: Include 2026-specific data, tools, and research findings. Reference specific studies, tool versions, and statistics discovered during the research phase.

## After generating:

11. Update `CLAUDE.md` — change `[ ]` to `[x]` for the generated chapter
12. Update `chapters/index.html` — remove the `pending` class from that chapter's card
13. Update navigation on the previous chapter (add "next chapter" link if missing)

## Important:
- The chapter must be COMPLETE — not a placeholder, but actual content ready for reading
- Think of the reader as a developer who uses AI coding tools daily and wants to stay sharp — not lose their edge
- Be opinionated: recommend specific habits, tools, and workflows
- Keep code examples SHORT — show the shape of a review, not a full codebase
- Read the previous chapter for a smooth transition
- Always connect back to the reader's experience: "You just merged an AI-generated PR. Can you explain what it does? If not, here's the problem..."
- Honestly mention tradeoffs, limitations, and the reality that AI review tools have their own blind spots
- The tone should be encouraging, not fear-mongering — the goal is to stay sharp, not to be scared of AI
