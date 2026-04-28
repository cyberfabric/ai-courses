Generate the next chapter of "AI Economics & Cost Engineering For Dummies."

## Steps:

1. Read `CLAUDE.md` — find the first chapter marked with `[ ]` in the "Progress Tracking" section
2. Read the "Chapter Details" section in CLAUDE.md — find the description of that chapter (structure, topics, what to include)
3. Read `chapters/assets/style.css` — review available CSS classes for styling
4. Read `chapters/index.html` — review the structure and navigation
5. Read the previous chapter (if any) for context and smooth transition

## Step 4.5 — Refresh data via WebSearch (REQUIRED for this course)

Before writing the chapter body, enumerate every external fact the chapter will cite:
- Model pricing (input rate, output rate, cache rates, batch discount) for every model named
- Cache TTLs and discount percentages for every provider named
- Batch API terms (discount, SLA) for every provider named
- Rate-limit tier structures for every provider named
- GPU hourly rates (on-demand and spot) for every GPU named (H100, H200, B200, GB200, consumer GPUs)
- Observability tool status for every tool named — **Helicone is in maintenance after Mintlify acquisition March 2026, VERIFY current state before recommending**
- OSS model availability for every model named (Llama 4 variants, DeepSeek V3.2/R2, Qwen 4, Mistral Large 3)
- Fine-tuning cost figures for every technique named (LoRA, QLoRA, full fine-tune)

For each fact, run `WebSearch` with a 2026 date qualifier (e.g., "Anthropic Claude Opus pricing April 2026", "H100 hourly rate April 2026", "Langfuse pricing 2026"). Record the verified figure and the source URL.

**Rules:**
- Do not write pricing or tool claims from memory — use searched values only.
- If a search returns results older than 6 months for a volatile topic, re-search with a tighter date filter before using.
- If a fact cannot be verified within 3 WebSearch attempts, OMIT it or mark it with a clear "as of <date>, source unconfirmed" caveat. Never fabricate a number.
- Cite the source URL either as an HTML comment immediately above the claim, or as a small footnote link at the end of the chapter.
- If a searched fact contradicts a number used in an earlier chapter of this course, update that earlier chapter after finishing the new one.

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
   - **"For Dummies" style**: friendly, conversational, uses analogies from everyday life (grocery bills, gym memberships, bulk shipping, electricity tariffs)
   - Use the correct CSS classes for examples, tips, warnings, exercises
   - **At least one `.cost-breakdown-box`** showing itemized cost math with real 2026 numbers
   - **At least one `.savings-callout`** highlighting a concrete % or $ savings
   - **At least one `.roi-box` OR `.pricing-table-box`** depending on whether the chapter is comparing scenarios or listing provider specs
   - **At least one `.exercise-box`** with a hands-on cost exercise
   - **At least one `.tip-box`** and one `.warning-box`
   - Every price/cost claim cites a 2026 source (WebSearch-verified) inline or as a footnote
   - Include concrete dollar numbers, not just percentages
   - Short paragraphs — walls of text kill understanding
   - Each chapter should end with a preview of how this connects to the next chapter
   - 400-600 lines of HTML

## After generating:

9. Update `CLAUDE.md` — change `[ ]` to `[x]` for the generated chapter
10. Update `chapters/index.html` — remove the `pending` class from that chapter's card
11. Update navigation on the previous chapter (add "next chapter" link if missing)
12. If any searched fact contradicts a number in an earlier chapter, update that earlier chapter too

## Important:
- The chapter must be COMPLETE — not a placeholder, but actual content ready for reading
- Think of the reader as a working developer who has already shipped at least one AI feature and been surprised by the bill
- Use real pricing, real tools, real numbers — dated to April 2026 or whenever the chapter is generated
- Read the previous chapter for smooth transition
- Every optimization technique needs a concrete before/after cost example in dollars
- Prioritize practical, immediately usable knowledge over theory
- The reader should be able to save money on their next deploy
