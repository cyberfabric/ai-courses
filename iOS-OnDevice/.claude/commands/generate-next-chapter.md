Generate the next chapter of "On-Device AI for iOS."

## Steps:

1. Read `CLAUDE.md` — find the first chapter marked with `[ ]` in the "Progress Tracking" section
2. Read the "Chapter Details" section in CLAUDE.md — find the description of that chapter (structure, topics, what to include)
3. Read `chapters/assets/style.css` — review available CSS classes for styling
4. Read `chapters/index.html` — review the structure and navigation
5. Read the previous chapter (if any) for context and smooth transition
6. **Use WebSearch** to find the latest iOS/Apple documentation, WWDC sessions, and developer blog posts relevant to this chapter's topics. Ensure all API names, framework capabilities, and best practices reflect the most current information (iOS 26+).

## Generating the chapter:

7. Create the HTML file in `chapters/` with the correct filename
8. Follow the HTML conventions from CLAUDE.md:
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
9. Content requirements:
   - In English
   - **"For Dummies" style**: friendly, conversational, uses analogies and everyday examples
   - **Practical and hands-on**: real Swift code, real iOS/Apple APIs, real model files
   - Use the correct CSS classes for examples, tips, warnings, exercises
   - **At least one `.device-benchmark`** showing performance metrics on real hardware
   - **At least one `.model-pipeline`** showing the data flow for an ML feature
   - **At least one `.apple-framework`** with Apple framework/API information
   - **At least one `.exercise-box`** with a hands-on exercise
   - Short paragraphs — walls of text kill understanding
   - Each chapter should end with a preview of how this connects to the next chapter
   - 400-600 lines of HTML
   - Keep code examples practical (Swift, Xcode config, Info.plist — max 20-30 lines per snippet)
   - Use CSS classes: `.device-benchmark`, `.model-pipeline`, `.apple-framework`, `.prompt-example.good`, `.prompt-example.bad`, `.comparison`, `.tip-box`, `.warning-box`, `.exercise-box`, `.checklist`, `.highlight-box`, `.stats-grid`, `.stat-card`, `.tool-card`, `.workflow-steps`
   - Include the theme toggle button in the navigation

## After generating:

10. Update `CLAUDE.md` — change `[ ]` to `[x]` for the generated chapter
11. Update `chapters/index.html` — remove the `pending` class from that chapter's card
12. Update navigation on the previous chapter (add "next chapter" link if missing)

## Important:
- The chapter must be COMPLETE — not a placeholder, but actual content ready for reading
- Think of the reader as a smart iOS developer who has never trained or deployed an ML model
- Use real-world iOS examples: Swift code, SPM dependencies, actual Apple API calls
- Read the previous chapter for a smooth transition
- Every major concept needs a practical example or code snippet
- Prioritize building working features over theory — get something running, then explain why it works
- Use WebSearch to verify all API names and capabilities are current for iOS 26+
