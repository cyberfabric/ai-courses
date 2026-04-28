Append the next new chapter from a course's `UPDATES.md` append queue. Re-verifies the topic with fresh WebSearch, generates the chapter, wires it into the course (CLAUDE.md, index.html, previous chapter footer), bumps the course's chapter count in the root catalog files, regenerates an associated memory map if the course uses them, and ticks the checkbox.

## Invocation
```
/append-next-chapter <course-id>
```
- `<course-id>` is a course directory name (e.g., `AI-Engineering`, `AI-Harness`, `Security`).
- This command processes ONE append item per invocation. Re-invoke to advance the queue.

## CRITICAL: WebSearch is MANDATORY
The append queue captures topics the audit thought were missing AT AUDIT TIME. Domains move fast — the topic may have been absorbed into another chapter, repositioned by a vendor, or rendered obsolete. The append re-verifies before generating. Hard minimums:
- **≥3 WebSearches** on the chapter topic.
- **≥1 WebFetch** on the most authoritative source (vendor docs, changelog, official spec — not a blog).
- If the fresh research suggests a materially different framing than `UPDATES.md`'s Topics list, **surface it in the report before generating**. Do not silently rewrite the spec; the user may want to amend the queue first.
- If the fresh research suggests the topic no longer warrants a new chapter (e.g., it's now standard knowledge covered in two existing chapters), report that finding and STOP — do not generate. The user will decide whether to mark the item `[x]` with a "rejected" note or push back.

## Steps

### 1. Resolve and load
1. Resolve `<course-id>` to an absolute directory. Stop with a clear error if it doesn't exist.
2. Read `<course-id>/UPDATES.md` in full. Find the FIRST `[ ]` item under `## Append queue`. If none exists, report `append queue is empty for <course-id>` and stop.
3. Extract for the chosen item: Title, Why, Topics (8–12 bullets), Sources, Suggested filename.

### 2. Load course conventions
1. Read `<course-id>/CLAUDE.md`. Extract: target line band, CSS class registry, content guidelines, tone markers, cross-reference format, chapter-card structure used by `index.html`.
2. Read `<course-id>/chapters/assets/style.css` to verify CSS classes you intend to use.
3. Read the most recent existing chapter for tone, transitions, and footer-navigation format. The new chapter must read like a peer of the existing ones.
4. Read `<course-id>/chapters/index.html` to copy the chapter-card format.

### 3. Re-verify with fresh WebSearch
1. Run ≥3 WebSearches on the chapter topic. Mix of "what is X in 2026", "X best practices", "X vendor docs".
2. Run ≥1 WebFetch on the most authoritative URL from `UPDATES.md`'s Sources list (or its current equivalent).
3. Classify:
   - **Still warranted, framing unchanged** — proceed.
   - **Still warranted, framing has shifted** — surface the new framing in a one-paragraph report; ask the user to confirm before generating. Pause.
   - **No longer warranted** — explain why; STOP without generating. Do not tick the box.
4. Track every URL with today's date for the final report and the chapter's source citations.

### 4. Generate the chapter
Only proceed if step 3 returned "still warranted, framing unchanged" (or the user confirmed the new framing).

1. Determine the chapter number: take `Suggested filename`'s `NN-` prefix, OR the next available number after the highest existing chapter file. Verify no collision.
2. Determine the slug: from `Suggested filename`, OR derive from the Title using kebab-case.
3. Final filename: `<course-id>/chapters/<NN>-<slug>.html`.
4. Generate the FULL chapter content in one pass, following the per-course `/generate-next-chapter` conventions:
   - Line band from CLAUDE.md (typically 400–600). Hit the minimum on the FIRST attempt; never pad incrementally.
   - Required structural elements per the course's content guidelines (e.g., `.config-block`, `.audit-box`, `.exercise-box` for AI-Engineering).
   - Theme toggle, top nav with prev/index/next, bottom footer nav.
   - Cross-references to existing chapters and sibling courses where natural.
   - Content driven by the Topics list from `UPDATES.md`.
   - Cite the verified sources from step 3 inline where appropriate.

### 5. Wire the chapter into the course
1. **`<course-id>/CLAUDE.md`**:
   - Add a new entry to the "Progress Tracking" section, marked `[x]` (the chapter is generated, not pending).
   - Append a "Chapter Details" block matching the course's existing format (File, Goal, Topics).
2. **`<course-id>/chapters/index.html`**:
   - Add a chapter card for the new chapter. Copy the format from an existing card. Do NOT include a `pending` class — the chapter exists.
3. **Previous chapter HTML** (the chapter whose number is `<NN>-1`):
   - Update the bottom `<footer>` and top nav: ensure the "Next" link points at `<NN>-<slug>.html`. If the previous chapter was last in the course before this append, it likely has no "Next" link — add one.
4. **Root catalog files — REQUIRED for appends.** A new chapter changes the course's chapter count, and that count is rendered in the root catalogs. Skipping this step leaves the catalog out of sync with reality.
   - **`/mnt/c/Projects/ps/AI-Courses/index.html`** — find the course's card by `data-course="<course-id>"`. In that card, bump:
     - the `data-chapters="N"` attribute on the `<div class="course-card">` from `N` to `N+1`
     - the visible text inside `<span class="progress-text">0/N chapters</span>` from `0/N` to `0/N+1` (preserve the existing "done" count if it isn't 0)
     - any matching `data-chapters="N"` on a `<a class="roadmap-card" data-course="<course-id>">` further down the page (only some courses appear in the roadmap section).
   - **`/mnt/c/Projects/ps/AI-Courses/CLAUDE.md`** — find the course's row in the Courses table. Bump the `Chapters` column from `N` to `N+1`.
   - This is the ONLY scope in which an append touches the root catalog. `/scaffold-new-course` is responsible for *adding* a course's row/card; this command is responsible for keeping that row's chapter count accurate when chapters are appended.

### 6. AUTO-STEP: generate the memory map
1. Check if `<course-id>/.claude/commands/create-memory-map.md` exists.
2. Check if other chapters in this course have memory maps in `<course-id>/chapters/maps/`. If at least one map exists, the course uses memory maps as a convention.
3. If both conditions are true, generate a memory map for the new chapter by following the steps in `<course-id>/.claude/commands/create-memory-map.md` for chapter `<NN>`.
4. If the course has no memory-map command, or no other chapter has a map, skip and note in the report.

### 7. Tick the box
1. Edit `<course-id>/UPDATES.md`: change the leading `[ ]` of this append item to `[x]`.
2. If the actual filename differs from `Suggested filename`, append an indented line: `  - generated as: <NN>-<slug>.html`.
3. If step 3 detected a framing shift that the user confirmed, append: `  - framing updated from audit: <one-line summary>`.

### 8. Report (terse)
Print:
- New chapter file path
- Line count
- Number of fresh WebSearches and WebFetches performed
- Files modified (`<course-id>/CLAUDE.md`, `<course-id>/chapters/index.html`, previous chapter HTML, root `/index.html`, root `/CLAUDE.md`, optional map)
- Old → new chapter count for the course (e.g., `12 → 13`)
- Map status (generated / skipped — no map convention / skipped — no command)
- Framing-shift note (if any)
- The next `[ ]` item in the append queue (Title), or "append queue is empty" if this was the last one

Do NOT stage or commit. The user reviews and commits.

## Hard rules
- Read `UPDATES.md` first, ALWAYS.
- WebSearch BEFORE generating.
- If fresh research says the topic no longer warrants a chapter, STOP and report — do not generate filler.
- Generate the FULL chapter content in one pass. No placeholders, no "TODO: expand later" sections.
- Wire the chapter into CLAUDE.md, index.html, and the previous chapter's nav atomically. A chapter that exists but isn't linked is a worse failure than one that doesn't exist.
- Bump the chapter count in the root catalogs (`/index.html`, root `/CLAUDE.md`) on every append. The catalogs render the per-course chapter count; if you skip this, the catalog drifts out of sync. The "do not touch the catalog" rule applies only to *adding/removing course rows* (that's `/scaffold-new-course`'s job) — bumping the chapter count of an existing row is part of `/append-next-chapter`'s job.
- Do NOT add a course's row to a catalog where it doesn't exist. Only update existing rows.
- Do NOT touch the refresh queue. Only the append queue.
- One `[ ]` per invocation. Re-invoke for the next.
- Do not stage or commit.

## Failure modes to avoid
- **Generating without verifying**: skipping fresh WebSearch produces a chapter that's already stale on day one.
- **Padding to hit the minimum line band**: produce real content, not filler. If you can't hit 400 lines on a topic, the topic probably doesn't warrant a chapter — surface that finding in step 3.
- **Forgetting to wire the chapter into nav**: orphaned chapters break the reading flow. Always update CLAUDE.md, index.html, and the previous chapter's footer.
- **Forgetting the root catalog chapter-count bump**: the course's chapter count on `/index.html` and root `/CLAUDE.md` will silently drift. The card still loads, the nav still works, but the catalog now lies. Always bump.
- **Adding a course row to a catalog where it doesn't exist**: that's `/scaffold-new-course`'s job. If a course's row is missing from `index.html`, surface that and stop — don't insert it.
- **Forgetting the memory map when other chapters have one**: a course-wide convention should not have a single chapter missing its map.
