Generate a visual Memory Map for a specific chapter. The user provides the chapter number as an argument (e.g., `/create-memory-map 03`).

## Steps:

1. Read `CLAUDE.md` — get the course title, chapter list, and chapter details for the requested chapter
2. Find the chapter HTML file in `chapters/` matching the given chapter number (e.g., `03-*.html`)
3. Read the full chapter HTML — extract all key concepts, analogies, workflows, terms, and exercises
4. Read `chapters/index.html` — get the full chapter list for navigation (prev/next map links)
5. Read `chapters/assets/style.css` — review available memory map CSS classes

## Generating the memory map:

6. Create the `chapters/maps/` directory if it doesn't exist
7. Create the HTML file at `chapters/maps/<NN>-<slug>-map.html` where `<NN>-<slug>` matches the chapter filename (e.g., chapter file `03-tool-design.html` → map file `maps/03-tool-design-map.html`)
8. Follow these HTML conventions:
   - UTF-8, HTML5 doctype, meta viewport
   - Link to `../assets/style.css` (one level up from maps/)
   - `<nav class="top-nav">` with navigation and theme toggle:
     ```html
     <nav class="top-nav">
       <span class="nav-title">[Course Title]</span>
       <div class="nav-links">
         <a href="../index.html">Contents</a>
         <a href="../<chapter-file>">Chapter</a>
         <a href="<prev-map-file>">&#8592; Prev Map</a>
         <a href="<next-map-file>">Next Map &#8594;</a>
         <button class="theme-toggle" aria-label="Toggle theme">🌙</button>
       </div>
     </nav>
     ```
     - Omit "Prev Map" for the first chapter's map
     - Omit "Next Map" for the last chapter's map
   - `<header class="map-header">` with chapter number, title, and memory map badge:
     ```html
     <header class="map-header">
       <span class="chapter-number">Chapter N</span>
       <h1>[Chapter Title]</h1>
       <span class="map-badge">Memory Map</span>
     </header>
     ```
   - `<main>` with visual content (see below)
   - `<nav class="chapter-nav">` at the bottom with prev/next map links and a link back to the chapter
   - `<script>` before closing `</body>` for theme toggle:
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

9. **Visual content requirements** — use **at least 5** of these element types per map:

   **Concept Cards** (`.map-grid` + `.map-card`):
   A grid of 4-8 cards, each summarizing a key concept from the chapter.
   ```html
   <div class="map-grid">
     <div class="map-card">
       <span class="map-card-icon">🧩</span>
       <div class="map-card-title">Concept Name</div>
       <div class="map-card-desc">One-two sentence summary of the concept.</div>
     </div>
     <!-- more cards -->
   </div>
   ```

   **Flow Diagram** (`.map-flow`):
   A process or workflow from the chapter, shown as connected steps.
   ```html
   <div class="map-flow">
     <div class="map-flow-step">Step 1</div>
     <span class="map-flow-arrow">→</span>
     <div class="map-flow-step">Step 2</div>
     <span class="map-flow-arrow">→</span>
     <div class="map-flow-step">Step 3</div>
   </div>
   ```

   **Key Terms** (`.map-terms`):
   A glossary of 5-10 important terms from the chapter.
   ```html
   <dl class="map-terms">
     <dt>Term</dt>
     <dd>Definition in one sentence.</dd>
   </dl>
   ```

   **Relationship Map** (`.map-relationships`):
   Shows how a central concept relates to surrounding concepts.
   ```html
   <div class="map-relationships">
     <div class="map-rel-node">Related A</div>
     <div class="map-rel-node">Related B</div>
     <div class="map-rel-center">Core Concept</div>
     <div class="map-rel-node">Related C</div>
     <div class="map-rel-node">Related D</div>
   </div>
   ```

   **Big Idea** (`.map-big-idea`):
   The single most important takeaway from the chapter.
   ```html
   <div class="map-big-idea">
     <span class="big-idea-icon">💡</span>
     <h3>The Big Idea</h3>
     <p>The one thing you should remember from this chapter.</p>
   </div>
   ```

   **Timeline** (`.map-timeline`):
   A step-by-step sequence or historical progression.
   ```html
   <ol class="map-timeline">
     <li class="map-timeline-item" data-step="1">
       <h4>Step Title</h4>
       <p>Brief description.</p>
     </li>
   </ol>
   ```

   **Comparison Table** (`.map-compare`):
   Side-by-side comparison of concepts.
   ```html
   <table class="map-compare">
     <thead><tr><th>Aspect</th><th>Option A</th><th>Option B</th></tr></thead>
     <tbody><tr><td>Feature</td><td>Value</td><td>Value</td></tr></tbody>
   </table>
   ```

   **Quick Quiz** (`.map-quiz`):
   3-5 self-test questions with expandable answers.
   ```html
   <div class="map-quiz">
     <h3>Quick Quiz</h3>
     <details>
       <summary>What is X?</summary>
       <p class="quiz-answer">X is ...</p>
     </details>
   </div>
   ```

   **Summary Strip** (`.map-summary`):
   The "if you remember nothing else" bullet points. Always include this at the bottom.
   ```html
   <div class="map-summary">
     <h3>Key Takeaways</h3>
     <ul>
       <li class="map-summary-item">Takeaway one.</li>
       <li class="map-summary-item">Takeaway two.</li>
     </ul>
   </div>
   ```

10. Content guidelines:
    - **Distill, don't duplicate** — the map summarizes the chapter, it doesn't repeat it
    - Use **emojis liberally** as visual markers for concepts (in card icons, section headers, etc.)
    - Use clear **section headings** (h2) to organize the map into logical areas
    - Keep text extremely concise — bullet points and short phrases over paragraphs
    - The map should be scannable in under 2 minutes
    - Target **300-500 lines** of HTML
    - Include the **Summary Strip** as the last content element in every map
    - Make sure the map captures the chapter's analogies — they're often the most memorable parts

## After generating:

11. Update `chapters/index.html` — add a memory map link after the chapter card for this chapter:
    ```html
    <a href="maps/<NN>-<slug>-map.html" class="map-link" title="Memory Map">🧠</a>
    ```
    Insert this inside the `.chapter-row` div, right after the closing `</a>` of the `.chapter-card`.

12. Update the chapter HTML file — add a memory map link in the top nav `div.nav-links`, before the theme toggle button:
    ```html
    <a href="maps/<NN>-<slug>-map.html">🧠 Map</a>
    ```

13. If a previous map exists, update its "Next Map" link to point to this new map. If a next map already exists, update the new map's "Next Map" link accordingly.

## Important:
- The memory map must be COMPLETE — a full visual summary ready for review
- Extract the most important concepts, not every detail
- Think of this as a **cheat sheet** or **study card** for the chapter
- Every map should give someone who read the chapter a quick refresher, and give someone who hasn't read it a preview of what it covers
- Use varied visual elements — don't make every map look identical. Some chapters are more flow-oriented, others are more concept-heavy, others are more comparison-focused. Let the content dictate the layout.
