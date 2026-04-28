Audit an existing course for content rot and missing topics. Produces a plan file (`UPDATES.md`) the user can then execute chapter-by-chapter via `/refresh-next-chapter <course-id>` and `/append-next-chapter <course-id>`. Both follow-up commands live at the AI-Courses root alongside this one, are course-agnostic, and re-verify every load-bearing claim with fresh WebSearch before editing — so audit-stale URLs are caught at refresh time, not at audit time.

## Invocation
```
/audit-course <course-id>
```
- `<course-id>` is a course directory name (e.g., `AI-Harness`, `AI-Advanced`, `Security`).

## CRITICAL: This command is READ-ONLY
- Do NOT edit any chapter HTML files.
- Do NOT edit any `CLAUDE.md` files.
- The ONLY new file this command writes is `<course-id>/UPDATES.md`.
- If `UPDATES.md` already exists, read it first, preserve completed `[x]` items, and merge new findings.

## CRITICAL: WebSearch is MANDATORY
This command's entire value depends on verifying claims against the live web. Courses rot because training data ages; the only remedy is fresh research. Hard minimums:
- **≥3 WebSearches per chapter**, scoped to that chapter's topic.
- **1–2 WebFetches per chapter** on authoritative sources (vendor docs, changelogs, release notes, ArXiv, primary-source blogs — NOT marketing pages).
- **2–3 course-level WebSearches** asking "what emerged in this domain in the last 6 months that isn't covered in this outline?" — these produce append-queue candidates.
- Record every URL consulted in `UPDATES.md`. No audit output is valid without the source list.

Prefer vendor changelogs and release-note pages over marketing blogs. Pricing pages over "comparison" listicles. Primary research over aggregator re-posts.

## Steps

### 1. Resolve and read the course
1. Resolve `<course-id>` to an absolute directory. If the directory does not exist, stop with a clear error.
2. Read `<course-id>/CLAUDE.md` in full. Extract:
   - The chapter list and file names.
   - The CSS class registry (custom boxes: `.inside-look-box`, `.threat-box`, `.compare-box`, etc.).
   - The content rules (line counts, required elements, "For Dummies" tone markers).
3. List all chapter files in `<course-id>/chapters/*.html`. Cross-check against the CLAUDE.md chapter list; flag any mismatches.

### 2. Scan each chapter for volatile claims
For each chapter file, read it and extract candidate "volatile claims" — the things most likely to rot. Look for:
- **Version IDs and model names**: regex-style patterns like `claude-*-202*`, `gpt-*`, `gemini-*-*`, `sonnet-*`, `opus-*`, explicit version numbers.
- **Pricing**: `$N/mo`, `$N per`, specific price tables, free-tier limits.
- **Benchmark numbers**: percentages (`NN%`), token limits (`NK tokens`, `NM tokens`), context windows, latency figures.
- **Tool/feature names**: "Agent Mode", "Canvas", "Cascade", "Projects", "Artifacts" — features rotate in and out.
- **Tool lists**: any "in 2026, the major tools are…" style enumeration.
- **External URLs**: especially blog posts with years in the URL or title.
- **Dated phrasing**: "as of 2025", "currently", "this year", "recently shipped".

Record line numbers for each volatile claim. Do not yet judge whether it is stale — just catalogue.

### 3. Per-chapter WebSearch verification
For each chapter:
1. Identify the 3–5 most load-bearing volatile claims (the ones a reader would act on — pricing, model IDs, feature availability, tool existence).
2. Run **≥3 WebSearches** on that chapter's topic targeting those claims. Examples:
   - "Cursor pricing 2026 plans"
   - "Claude Sonnet latest model ID"
   - "Windsurf Cascade agent mode status"
3. Run **1–2 WebFetches** on the authoritative source (e.g., `anthropic.com/pricing`, the vendor's changelog).
4. For each claim, classify:
   - **STALE** — the live web contradicts it; must be fixed.
   - **DRIFTED** — still technically true but newer info exists and reader would benefit.
   - **CURRENT** — no change needed.

### 4. Identify the "preserve" blocks
For each chapter, identify the evergreen material that a refresh MUST NOT touch except to replace specific stale facts:
- Analogies (kitchen, suitcase, apartment, etc.) — note line ranges.
- The closing exercise / exercise boxes.
- "What's Next" preview.
- "Going Deeper" pointer (where present).
- Core pedagogical scaffolding: definitions, mental models, decision frameworks.

Record line ranges. These will be listed under **Preserve** in `UPDATES.md` and serve as explicit protection during refresh.

### 5. Course-level topic gap analysis
Run **2–3 course-level WebSearches** for the course's domain:
- "what's new in <domain> 2026 vs 2025"
- "<domain> topics missing from typical course"
- "<domain> major developments last 6 months"

Compare findings against the CLAUDE.md chapter outline. Propose new chapter candidates ONLY if:
- The topic is genuinely not covered (check via keyword search across chapter files).
- It has enough depth to fill 400–600 lines of "For Dummies"-style content.
- It fits the course's audience.

Reject trivial updates ("X shipped a minor feature") — those belong in refresh items, not new chapters.

### 6. Write `UPDATES.md`
Create `<course-id>/UPDATES.md` with this exact structure:

```markdown
# Course Updates — <course-id>
Generated: YYYY-MM-DD
Auditor: Claude Code /audit-course

## Summary
- Chapters scanned: N
- Refresh queue: N items
- Append queue: N items
- Do-not-touch: N chapters

## Refresh queue
- [ ] NN-slug.html — <refresh|light-edit|heavy>
  - Stale: <claim> (line ~NN) — <why stale / current truth per web>
  - Stale: <claim> (line ~NN) — <why stale / current truth per web>
  - Drifted: <claim> (line ~NN) — <newer info available>
  - Sources consulted: <url> (YYYY-MM-DD), <url> (YYYY-MM-DD)
  - Preserve: <analogy name> (lines NN-NN), closing exercise (lines NN-NN), What's Next
  - Scope: <light-edit (≤5 claims) | medium (6–15) | heavy (section rewrite)>

## Append queue
- [ ] New: <Chapter Title>
  - Why: <what emerged; why it belongs in this course>
  - Topics: (8–12 bullets in the same shape as existing Chapter Details blocks in CLAUDE.md)
  - Sources: <url> (YYYY-MM-DD), <url> (YYYY-MM-DD)
  - Suggested filename: NN-slug.html (next available number)

## Do-not-touch
- NN-slug.html — evergreen, nothing time-bound found
- NN-slug.html — minor drift only, not worth a refresh pass this cycle
```

Rules for the file:
- **Checkboxes are load-bearing** — `/refresh-next-chapter` and `/append-next-chapter` both scan for the first `[ ]` item. Do not omit them. Both commands also re-verify sources with fresh WebSearch before editing, so audit-stale URLs are caught at refresh time, not at audit time.
- **Sources must be real URLs you actually fetched/searched**, with the date you consulted them. The refresh command reuses these; bogus URLs poison the next step.
- **Preserve lines are line ranges in the CURRENT chapter file**, not abstract descriptions. Future edits may shift numbers; that's acceptable — the description of what to preserve (the analogy, the exercise) is what matters.
- **Scope estimates calibrate the refresher's expectations.** Over-estimating scope is the #1 way refresh degrades good content.

### 7. Report to user
After writing `UPDATES.md`, print a summary:
- Path to the file.
- Counts (refresh / append / do-not-touch).
- Any chapters that flagged surprising amounts of rot.
- Any missing-chapter candidates worth highlighting.

Do NOT stage or commit. The user reviews `UPDATES.md` before any execution.

## Calibration: when NOT to flag

Over-flagging is as damaging as under-flagging, because it burns the user's attention and encourages mass refreshes that degrade good content. Do not flag:
- Minor wording drift that doesn't mislead a reader.
- "Claude 3.5 Sonnet" mentioned as historical context (not as a recommendation) — it's a timeline marker, leave it.
- Pricing claims when the page itself says "check vendor for current pricing".
- External links to blog posts unless the content is factually wrong now.
- Features that were renamed but still exist (note the rename in drifted, not stale).

When in doubt, classify as DRIFTED not STALE. The user can promote drifted items to the refresh queue if they want.

## Failure modes to avoid
- **Citing outdated sources**: a marketing blog from 2024 does not count as "current." Prefer vendor changelogs.
- **Inventing a URL you didn't actually fetch**: every source listed in `UPDATES.md` must have been consulted. No guessing.
- **Over-flagging**: if every chapter lands in the refresh queue, you've miscalibrated — re-evaluate and move borderline items to do-not-touch.
- **Under-preserving**: if a refresh item's Preserve list is empty, the refresher has nothing protecting the evergreen content. Always list at least the analogies and closing exercise.
- **Touching chapter HTML**: this command is read-only. If you find yourself about to edit a chapter, stop.
