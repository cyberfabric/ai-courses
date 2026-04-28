Generate the next chapter of "The Android Quality Stack For Dummies."

## Steps:

1. Read `CLAUDE.md` — find the first chapter marked with `[ ]` in the "Progress Tracking" section
2. Read the "Chapter Details" section in CLAUDE.md — find the description of that chapter (file name, goal, topics)
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
   - **"For Dummies" style**: friendly, conversational, anti-bikeshedding, pragmatic
   - **Tone**: experienced Android dev who has been deferring quality tooling — frame everything as "you've been putting this off; here's how to finally do it without grinding feature work to a halt"
   - **Light AI thread**: each chapter has at least one short "AI-Assisted Setup" subsection with a concrete Claude Code prompt or skill
   - **At least one `.tool-profile-box`** per tool chapter (Ch 3-12) — the "Meet the Tool" spec sheet (name, what it catches, install snippet, runtime cost, when to skip it)
   - **At least one `.config-recipe`** per chapter — real, copy-pasteable Gradle Kotlin DSL / XML / YAML config with annotations
   - **At least one `.adoption-ladder`** per tool chapter — Day 1 / Week 1 / Month 1 staged rollout
   - **At least one `.exercise-box`** per chapter — a hands-on exercise where the reader runs the tool against their own project
   - Use other CSS classes as appropriate: `.tip-box`, `.warning-box`, `.prompt-example.good`, `.prompt-example.bad`, `.comparison`, `.checklist`, `.highlight-box`, `.stats-grid`, `.stat-card`, `.tool-card`, `.workflow-steps`
   - Short paragraphs — walls of text kill understanding
   - Each chapter should end with a preview of how it connects to the next
   - 400-600 lines of HTML — verify with `wc -l` before finalizing
   - Code examples must be **real and current**: Kotlin DSL Gradle (`build.gradle.kts`), `lint.xml`, `detekt.yml`, `proguard-rules.pro`, `libs.versions.toml`, `.editorconfig`, GitHub Actions YAML

## After generating:

9. Update `CLAUDE.md` — change `[ ]` to `[x]` for the generated chapter
10. Update `chapters/index.html` — remove the `pending` class from that chapter's card
11. Update navigation on the previous chapter if needed (next-chapter link)

## HTML Validation:

- Always close `<div>` elements with `</div>` — never `</tip>`, `</note>`, `</card>`, `</box>`
- After writing the chapter, grep for unmatched/custom closing tags before declaring done
- Validate all HTML tags are properly closed before completing the chapter

## Important:

- The chapter must be COMPLETE — not a placeholder, but actual content ready for reading
- Think of the reader as a smart, experienced Android dev who has shipped real apps but never invested in detekt/lint/etc. They are not new to Kotlin or Gradle. Don't condescend.
- Use real Android quality scenarios: actual lint findings, real detekt smell categories, real `proguard-rules.pro` patterns, real CI YAML
- Read the previous chapter for a smooth transition — every chapter should feel like part of the same journey
- Every major concept needs a concrete config example — copy-pasteable, not pseudocode
- Prioritize practical, tested-in-production examples over theory
- The framing is **"leverage, not tax"** — every tool you introduce should be sold as letting the reader stop doing something manually
- Every chapter should teach the reader to build at least one reusable Claude Code skill (`/command`) — e.g., `/triage-lint-baseline`, `/draft-detekt-config`, `/explain-r8-keeprule`
