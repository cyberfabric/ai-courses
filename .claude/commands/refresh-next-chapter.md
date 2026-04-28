Refresh the next chapter in a course's `UPDATES.md` refresh queue. Re-verifies sources with fresh WebSearch, applies edits while honoring Preserve ranges, regenerates the chapter's memory map, and ticks the checkbox.

## Invocation
```
/refresh-next-chapter <course-id>
```
- `<course-id>` is a course directory name (e.g., `AI-Engineering`, `AI-Harness`, `Security`).
- This command processes ONE chapter per invocation. Re-invoke to advance the queue.

## CRITICAL: WebSearch is MANDATORY
Audits collect dated facts. By the time a refresh runs, the "current truth" the audit captured may have drifted again. The refresh re-verifies before editing. Hard minimums:
- **≥1 fresh WebSearch per Stale or Drifted claim** that names a load-bearing fact (model ID, version number, official guidance like "200 lines", feature name, pricing).
- **≥1 WebFetch per chapter** on the authoritative source already cited in `UPDATES.md` (or its current equivalent if the URL moved).
- **Floor: ≥2 fresh WebSearches per chapter** even when only one or two claims need verification — defends against dated audits.
- If a fresh result contradicts what `UPDATES.md` captured, **trust the fresh result.** Note the drift in the final report.
- If a Source URL 404s, find the replacement and use it. Record the new URL in the post-run report.

Prefer vendor changelogs and release-note pages over marketing blogs. Never edit a chapter using only what `UPDATES.md` claims — always reground in fresh research.

## CRITICAL: Preserve ranges are inviolable
The audit's Preserve list names line ranges and the structural element they protect (analogy, audit-box, exercise-box, "What's Next", closing manifesto). Inside those ranges, the ONLY allowed edit is replacing a specific cited stale claim. Do not "improve" prose, restructure boxes, or rewrite analogies — even if you think you can do better. The Preserve list is a fence, not a suggestion.

## Steps

### 1. Resolve and load
1. Resolve `<course-id>` to an absolute directory. Stop with a clear error if it doesn't exist.
2. Read `<course-id>/UPDATES.md` in full. Find the FIRST `[ ]` item under `## Refresh queue`. If none exists, report `refresh queue is empty for <course-id>` and stop.
3. Extract for the chosen item: filename, scope (`light-edit` / `medium` / `heavy`), every Stale/Drifted/Missing claim with line ranges, Sources consulted with dates, Preserve line ranges.

### 2. Load course conventions
1. Read `<course-id>/CLAUDE.md`. Extract: target line band (typically 400–600), CSS class registry, content guidelines (required elements like `.config-block`, `.audit-box`, `.exercise-box`), tone markers, cross-reference format.
2. Read `<course-id>/chapters/assets/style.css` only if you need to verify a CSS class is available. Skip otherwise.
3. Read the target chapter file in full. Note absolute line numbers — they may have shifted since the audit.

### 3. Re-verify with fresh WebSearch
For each Stale/Drifted/Missing item from step 1:
1. Run a WebSearch targeting the specific claim (e.g., `"Claude Code CLAUDE.md line target 2026"` for a "200-line" claim).
2. WebFetch the authoritative source URL from `UPDATES.md`. If it 404s or has materially changed, find the current equivalent.
3. Classify the live truth:
   - **Confirmed** — UPDATES.md is still right; proceed with the planned edit.
   - **Drift since audit** — fresh result differs; use the fresh result and note the drift.
   - **Reverted** — the change UPDATES.md flagged has been rolled back; skip this item entirely and note it.
4. Track every URL you actually fetched/searched, with today's date. These go into the post-run report.

Do NOT skip step 3 even when the audit was written yesterday. The discipline matters more than the calendar gap.

### 4. Apply edits
For each item still in scope after step 3:
1. Edit the chapter HTML to address the Stale/Drifted/Missing claim. Use exact-string Edit operations; no full-file rewrites unless the scope is `heavy` and a section is being replaced wholesale.
2. **Honor Preserve.** Inside any Preserve line range, only replace specific cited claims (e.g., updating "100 lines" to "200 lines" inside a sentence). Do not touch surrounding prose.
3. Stay within the course's line-target band from CLAUDE.md. If a `heavy` scope adds 100+ lines, verify the result still fits the band — if it overflows, condense rather than truncate, and never trim Preserve content.
4. Use only CSS classes registered in the course's CLAUDE.md.
5. HTML hygiene: close `<div>` with `</div>`, never `</tip>` / `</note>` / `</card>`. Validate matching tags before finishing.
6. Cross-references: relative paths only; verify link targets exist.

### 5. Verify
1. `wc -l <course-id>/chapters/<file>` — must be within the course's line band.
2. `grep -E "</(tip|note|card|warning|exercise|config|audit|highlight)[^>]*>" <course-id>/chapters/<file>` — must return nothing (no invented closing tags).
3. Spot-check ONE Preserve range: confirm the named element (e.g., audit-box, exercise-box) is still present in roughly the original location. The line numbers may have shifted; the element must remain.
4. If any check fails, fix it before proceeding to the next step.

### 6. AUTO-STEP: regenerate the memory map
1. Check if `<course-id>/.claude/commands/create-memory-map.md` exists. If not, skip and note "course has no memory-map command" in the report.
2. Check if `<course-id>/chapters/maps/<NN>-*-map.html` exists for the refreshed chapter (where `<NN>` is the chapter number from the filename). If no map currently exists, skip silently — refresh does not proactively create maps that the user hadn't already chosen to generate.
3. If both exist, regenerate the map by following the steps in `<course-id>/.claude/commands/create-memory-map.md` for chapter `<NN>`. Read the refreshed chapter, regenerate the map file, update `chapters/index.html` and the chapter HTML if the create-memory-map skill specifies (it does — see steps 11–13 of that skill).
4. The map regen reads the chapter you just refreshed, so it reflects the new content automatically.

### 7. Tick the box
1. Edit `<course-id>/UPDATES.md`: change the leading `[ ]` of the chosen item to `[x]`.
2. If any drift-since-audit was detected in step 3, append a single indented line under the item: `  - drift since audit: <one-line note>`.

### 8. Report (terse)
Print:
- Chapter file path
- Lines before → lines after
- Number of fresh WebSearches and WebFetches performed
- Drift-since-audit notes (if any)
- Map regen status (regenerated / skipped — no map / skipped — no command)
- The next `[ ]` item in the refresh queue (filename + scope), or "refresh queue is empty" if this was the last one

Do NOT stage or commit. The user reviews the diff and commits.

## Hard rules
- Read `UPDATES.md` first, ALWAYS. Never guess which chapter is next.
- WebSearch BEFORE editing, never after. Edits must reflect the freshest info.
- Preserve ranges are inviolable. Do not "improve" content inside them.
- One `[ ]` per invocation. Do not loop through multiple chapters in a single run — the user re-invokes for the next one. This keeps each chapter individually reviewable.
- Do not stage or commit.
- Do not touch the append queue. Only the refresh queue.

## Failure modes to avoid
- **Trusting UPDATES.md sources blindly**: skipping the fresh WebSearch defeats the purpose of the refresh.
- **Editing inside Preserve ranges to "polish" prose**: that's how good content gets degraded.
- **Padding or trimming to hit a line count**: if you're outside the band, restructure sections; never line-pad or line-cut.
- **Forgetting to tick the box**: the next `/refresh-next-chapter` invocation will pick the same chapter again. Always update `UPDATES.md` at the end.
- **Skipping memory map regen**: if a map exists for the chapter, refreshing the chapter without refreshing the map leaves a stale summary. Auto-step is not optional when a map is present.
