Generate the next chapter of "Building AI-Powered Features for iOS."

## Steps:

1. Read `CLAUDE.md` — find the first chapter marked with `[ ]` in the "Progress Tracking" section
2. Read the "Chapter Details" section in CLAUDE.md — find the description of that chapter (structure, topics, what to include)
3. Read `chapters/assets/style.css` — review available CSS classes for styling
4. Read `chapters/index.html` — review the structure and navigation
5. Read the previous chapter (if any) for context and smooth transition

## Research:

5b. **Use WebSearch** to find the latest information about the iOS frameworks and APIs referenced in this chapter's topics. Search for:
    - Latest Apple documentation and WWDC sessions for the relevant frameworks
    - Real-world iOS apps using the features discussed in this chapter
    - Any new APIs, deprecations, or best practices announced since WWDC 2025
    - Swift code examples and patterns from the developer community

This ensures each chapter includes the most current and accurate information.

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
   - **Product-focused**: real user scenarios, real UX patterns, real iOS implementations
   - Use the correct CSS classes for examples, tips, warnings, exercises
   - **At least one `.product-pattern`** showing a proven UX/product pattern for AI features
   - **At least one `.user-story-box`** showing a scenario from the user's perspective
   - **At least one `.api-recipe`** showing a step-by-step API integration
   - **At least one `.exercise-box`** with a hands-on exercise
   - Short paragraphs — walls of text kill understanding
   - Each chapter should end with a preview of how this connects to the next chapter
   - 400-600 lines of HTML
   - Keep code examples practical (Swift, SwiftUI, API calls — max 20-30 lines per snippet)
   - Use CSS classes: `.product-pattern`, `.user-story-box`, `.api-recipe`, `.prompt-example.good`, `.prompt-example.bad`, `.comparison`, `.tip-box`, `.warning-box`, `.exercise-box`, `.checklist`, `.highlight-box`, `.stats-grid`, `.stat-card`, `.tool-card`, `.workflow-steps`
   - Include the theme toggle button in the navigation

## After generating:

9. Update `CLAUDE.md` — change `[ ]` to `[x]` for the generated chapter
10. Update `chapters/index.html` — remove the `pending` class from that chapter's card
11. Update navigation on the previous chapter (add "next chapter" link if missing)

## Important:
- The chapter must be COMPLETE — not a placeholder, but actual content ready for reading
- Think of the reader as a smart iOS developer who wants to ship AI features that users love
- Focus on the PRODUCT side: what to build, how users interact with it, what makes a great AI feature
- Use real-world iOS examples: Swift code, SwiftUI views, API integration patterns
- Read the previous chapter for a smooth transition
- Every major concept needs a practical example or code snippet
- Balance technical implementation with UX/product thinking — this is not just an API tutorial
- Where relevant, add cross-references to iOS-OnDevice chapters for deeper infrastructure topics
