Generate the next chapter of "AI in 2026: The State of the Frontier."

This course is **time-stamped on purpose** and depends on **current web sources**. Unlike every other course in the AI-Courses collection, the chapter generator MUST use WebSearch before drafting — training-data knowledge is not enough, the frontier moves too fast.

## Steps:

1. Read `CLAUDE.md` — find the first chapter marked with `[ ]` in the "Progress Tracking" section
2. Read the "Chapter Details" section in CLAUDE.md — find the description of that chapter (goal, topics, WebSearch suggestions)
3. Read `chapters/assets/style.css` — review available CSS classes for styling
4. Read `chapters/index.html` — review the structure and navigation
5. Read the previous chapter (if any) for context and smooth transition

## **MANDATORY: WebSearch step (before drafting)**

6. Run **3–5 WebSearch queries** scoped to the chapter's topics. Use the "WebSearch suggestions" listed for that chapter in CLAUDE.md as a starting point, but adapt based on what you need.
   - Always include the current year/month in the query (e.g., "frontier AI models April 2026")
   - Cover at least: (a) current state of the topic, (b) recent papers/announcements, (c) contrarian views or limitations
   - Save the source URLs — you must cite them inline in the HTML
7. Quickly extract from the results:
   - Specific named models with version numbers and release dates
   - Specific named benchmarks with current scores
   - Specific named papers, authors, or labs with statements
   - At least one contrarian source / limitation / failure mode
8. If the chapter is in Part III (Beyond LLMs) or Part IV (Hard Problems), also search for the alternative-path or anti-hype angle specifically.

## Generating the chapter:

9. Create the HTML file in `chapters/` with the correct filename
10. Follow the HTML conventions from CLAUDE.md:
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
11. **Time-stamped content (course-specific):**
    - **Open the chapter** with a `.frontier-box` containing the snapshot date and one-paragraph summary of the current state — e.g., `<div class="frontier-box">As of April 2026, [topic] looks like this: ...</div>`
    - **Cite WebSearch sources inline** with `<a href="URL">Source Name</a>` — at least one citation per major claim
    - **Always include a `.contrarian-box`** — the anti-hype counter-fact for the chapter
    - **Always include a `.forecast-box`** for chapters in Parts II–IV (predictions, what to expect)
    - **Always include a `.alt-path-box`** for chapters in Part III (alternatives to LLMs)
    - **Call out what may rot fast** — version numbers, prices, leaderboard positions — vs. what is likely to remain true (architectures, trade-offs, open problems)

12. Content requirements:
    - In English
    - **"For Dummies" with current sources**: friendly, conversational, intermediate technical depth (like AI-DeepDive)
    - Always pair an exciting fact with a contrarian one — every chapter needs both `.frontier-box` (or `.forecast-box`) AND `.contrarian-box` content
    - Use specific named models with version numbers and dates
    - Use named benchmarks with actual scores
    - Use HTML tables (not ASCII art) for model/benchmark comparisons
    - Use `<code>` for inline numbers, model names, and benchmark scores
    - **At least one `.frontier-box`** opening the chapter with the snapshot date
    - **At least one `.contrarian-box`** with the anti-hype angle
    - **At least one inline citation** to a WebSearch source per major claim
    - For Parts II–IV chapters, **at least one `.forecast-box`** with predictions
    - For Part III chapters, **at least one `.alt-path-box`** showcasing alternatives
    - Short paragraphs — walls of text kill understanding
    - Each chapter should end with a preview of how this connects to the next chapter
    - **Target ~600 lines of HTML** — but do NOT cut content if the chapter is under 1000 lines
    - Include the theme toggle button in the navigation
    - Cross-reference AI-Intro and AI-DeepDive where appropriate: `<div class="tip-box"><strong>Companion:</strong> This builds on <a href="../../AI-Intro/chapters/NN-slug.html">AI-Intro Ch N</a> and <a href="../../AI-DeepDive/chapters/NN-slug.html">AI-DeepDive Ch N</a>.</div>`

## After generating:

13. Update `CLAUDE.md` — change `[ ]` to `[x]` for the generated chapter
14. Update `chapters/index.html` — remove the `pending` class from that chapter's card
15. Update navigation on the previous chapter if needed
16. Run `wc -l <file>` to verify the chapter is at least 400 lines. If under, expand with substantive sections (NOT line-by-line padding) before declaring done.
17. Grep for unmatched/custom closing tags before declaring done: `grep -nE '</[a-z]+>' <file>` should only show standard HTML tags.

## Important:
- The chapter must be COMPLETE — not a placeholder, but actual content ready for reading
- Think of the reader as a smart developer who finished AI-Intro and AI-DeepDive and now wants to understand the *current frontier*
- Every claim about a current model/benchmark MUST come from a WebSearched source, not training-data memory
- Every chapter must be honest about what may rot fastest (version numbers, prices, scores) vs. what will remain true (architectures, trade-offs, open problems)
- Read the previous chapter for a smooth transition
- Prioritize honesty over excitement — a contrarian counter-fact is required, not optional
