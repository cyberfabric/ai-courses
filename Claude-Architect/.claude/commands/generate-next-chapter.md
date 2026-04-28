Generate the next chapter of "Claude Certified Architect: Foundations."

## Steps:

1. Read `CLAUDE.md` — find the first chapter marked with `[ ]` in the "Progress Tracking" section
2. Read the "Chapter Details" section in CLAUDE.md — find the description of that chapter (structure, topics, what to include)
3. Read `chapters/assets/style.css` — review available CSS classes for styling
4. Read `chapters/index.html` — review the structure and navigation
5. Read the previous chapter (if any) for context and smooth transition

## Research (MANDATORY):

This certification was launched in March 2026. **You MUST search the web before writing each chapter** — do not rely on model training data for CCA-F specifics.

6. **Search the web** for the latest information on the chapter's topics. For EVERY chapter, search:
   - Anthropic's official docs and blog (`docs.anthropic.com`, `anthropic.com/news`, `anthropic.com/engineering`)
   - Claude Code documentation (`docs.anthropic.com/en/docs/claude-code`)
   - MCP specification (`modelcontextprotocol.io`)
   - CCA-F exam resources (`claudecertifications.com`)
   - Anthropic Academy courses on Skilljar
   - Community study guides and exam experience reports (Medium, Dev.to, Reddit)
   - Recent articles specifically about the chapter's domain topics
7. Use the research to enrich the chapter with **accurate, up-to-date details** — exam domain weights, scenario specifics, API details, and architectural patterns must reflect the current state of the certification

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
   - **"For Dummies" style**: friendly, practical, exam-focused — like a colleague who already passed the cert walking you through it
   - Use the correct CSS classes for examples, tips, warnings, exercises
   - **Every chapter MUST include at least one `.exam-tip-box`** with certification-specific advice (e.g., "The exam loves to test this," "Watch for this distractor")
   - **Every chapter MUST include at least one `.architect-box`** showing a design pattern or architectural tradeoff relevant to the topic
   - **At least one `.exercise-box`** with a practical hands-on task
   - **Domain weight callout** in the chapter introduction (e.g., "This chapter covers Domain 1, which is 27% of the exam")
   - **Scenario connections**: mention which of the 6 exam scenarios the chapter's content applies to
   - **Quick Review section** at the end with 3-5 key takeaways as a `.checklist`
   - Code examples should be **Python, JSON, YAML, or shell commands** — practical config and API snippets
   - Short paragraphs — keep it scannable
   - Each chapter should end with a preview of what's coming next
   - 400-600 lines of HTML
   - Use CSS classes: `.exam-tip-box`, `.architect-box`, `.prompt-example.good`, `.prompt-example.bad`, `.comparison`, `.tip-box`, `.warning-box`, `.exercise-box`, `.checklist`, `.highlight-box`, `.stats-grid`, `.stat-card`, `.tool-card`, `.workflow-steps`
   - Include the theme toggle button in the navigation

## After generating:

11. Update `CLAUDE.md` — change `[ ]` to `[x]` for the generated chapter
12. Update `chapters/index.html` — remove the `pending` class from that chapter's card
13. Update navigation on the previous chapter (add "next chapter" link if missing)

## Important:
- The chapter must be COMPLETE — not a placeholder, but actual content ready for reading
- Think of the reader as a developer with 6+ months of Claude experience who wants to pass the CCA-F
- Be opinionated: recommend study strategies, highlight what the exam emphasizes
- Keep code examples SHORT — show API calls, config snippets, architectural diagrams in text, not full implementations
- Read the previous chapter for a smooth transition
- Always connect concepts to the exam scenarios: "In the Customer Support Agent scenario, this pattern shows up as..."
- Honestly mention common exam traps and misconceptions
- The 6 exam scenarios are: Customer Support Resolution Agent, Code Generation with Claude Code, Multi-Agent Research System, Developer Productivity with Claude, Claude Code for CI/CD, Structured Data Extraction
