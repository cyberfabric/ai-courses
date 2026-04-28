Append ONE new chapter to the end of this course using the plan in `UPDATES.md`. Always append — never renumber existing chapters.

## Invocation
```
/append-next-chapter
```
Run from inside the course directory. No arguments. Reads `UPDATES.md`, picks the first unchecked item from the **Append queue**, generates a full chapter, integrates it into the course.

## Why append-only?

Mid-course insertion breaks prev/next nav in every other chapter, scrambles the `CLAUDE.md` chapter order, produces an unreadable git diff, and invalidates any external bookmarks. If a new topic is conceptually mid-course, the chapter's opening paragraph can cross-link to earlier chapters ("This extends a thread from Chapter 4…") — that is the correct way to handle it.

## CRITICAL: Up-to-date content requirement

A new chapter generated from training data is dead on arrival. This command enforces Security-course-level freshness:
- **≥5 WebSearches** on the chapter's topic before writing.
- **≥2 WebFetches** on authoritative sources (vendor docs, changelogs, primary research).
- Reuse URLs already recorded in the `UPDATES.md` append item if they're less than 30 days old; otherwise run fresh research.
- Name real tools, real people, real incidents — never hypotheticals when a current example exists.

## Steps

### 1. Load the plan
1. Read `UPDATES.md` in the current course directory. If it does not exist, stop and tell the user to run `/audit-course <course-id>` from the repo root first.
2. Find the first `[ ]` item under **Append queue**. If none, report "append queue empty" and stop.
3. Read the item's full block: new chapter title, why, topics, sources, suggested filename.

### 2. Determine the next chapter number
1. List `chapters/*.html` in the current course. Extract the numeric prefix from each (`01-`, `02-`, …).
2. Find the maximum. The new chapter is `max + 1`, zero-padded to 2 digits.
3. Use the suggested filename from `UPDATES.md` if it matches this number; otherwise rename to use the correct number. Example: if last chapter is `11-...html` and append item suggests `13-...html`, correct to `12-...html`.

### 3. Read the course conventions
1. Read `CLAUDE.md` for this course — capture tone rules, content guidelines, required elements per chapter, and the CSS class registry.
2. Read `chapters/assets/style.css` — confirm available CSS classes.
3. Read the **last existing chapter** (current max-numbered file) for voice, transition style, and structural pattern.
4. Read `chapters/index.html` — note the chapter card format and navigation.

### 4. Research (MANDATORY)
1. Run **≥5 WebSearches** on the chapter's topic. Target the bullets listed under "Topics" in the append item. Include at least one search scoped to the last 6 months.
2. Run **≥2 WebFetches** on authoritative sources — vendor docs, release notes, ArXiv, or the primary-source blog post that introduced the concept.
3. For any claim involving pricing, version IDs, or specific benchmark numbers, verify against the vendor's own page.
4. Collect concrete names (tools, companies, models, people, incidents) to use in the chapter body.

### 5. Generate the chapter
Create `chapters/NN-slug.html` following ALL conventions from this course's `CLAUDE.md`:

**Structure (from the existing chapter template):**
- UTF-8 encoding, HTML5 doctype, meta viewport.
- Link to `assets/style.css`.
- `<nav class="top-nav">` with links to index, prev (the previous chapter), next (this will initially be the index since this is the last chapter), and the theme-toggle button.
- `<header class="chapter-header">` with chapter number and title.
- `<main>` with full body content (400–600 lines).
- `<footer>` with prev/next navigation.
- `<script>` at end of body for the theme toggle (copy the exact script from an existing chapter in this course).

**Content (per this course's CLAUDE.md):**
- "For Dummies" tone — friendly, analogy-rich, short paragraphs.
- All course-specific required elements (check the "Content Guidelines" section of CLAUDE.md — e.g., AI-Harness requires at least one `.inside-look-box`; Security requires `.threat-box`, `.shield-box`, `.real-attack-box`, `.think-like-attacker`).
- At least one `.exercise-box` with a hands-on task.
- At least one analogy woven into the prose.
- A "What's Next" closing section pointing back to the course index (or to a natural next step if one exists).
- A "Going Deeper" pointer if this course uses them (check existing chapters).
- Short paragraphs, scannable structure.
- Real names: cite specific tools, companies, incidents from research — no hypotheticals when a real example exists.

**Length — non-negotiable:**
- 400 lines minimum on the FIRST draft. Draft the FULL content in one pass at ~10% above minimum. Count with `wc -l` before finalizing.
- If under 400, expand with substantive sections (examples, case studies, deeper dives) — NOT filler, not line-by-line padding.
- If you land 400–460 lines, leave it. Only trim if significantly over 600, and then cut whole sections, not individual lines.

**HTML hygiene:**
- Close every `<div>` with `</div>` — never `</tip>`, `</note>`, or any invented closing tag.
- Verify every opened tag has a matching close before declaring done.
- Relative paths: `../chapters/` is wrong inside a chapter file; use `assets/style.css`, `index.html`, and sibling chapter filenames directly.

### 6. Integrate into the course

**Update `CLAUDE.md`:**
1. Add a checkbox line under **Progress Tracking**: `- [x] Chapter NN: Title` (mark done, since we're generating it now).
2. Add a **Chapter Details** block at the end of that section matching the shape of existing blocks — file name, goal (one sentence), topics (8–12 bullets matching what was researched).
3. If there's a **File Structure** listing of chapter files, add the new file there too.

**Update `chapters/index.html`:**
1. Add a new chapter card matching the existing pattern. The card should NOT have the `pending` class (it's done).
2. If chapters are grouped into Parts, place it in the most appropriate existing Part, or add a new Part if the topic doesn't fit.

**Update the previous chapter's nav:**
1. Open the now-second-to-last chapter.
2. Update its footer "next" link to point to the new chapter instead of the index.
3. Update its top-nav "next" link similarly.

### 7. Update root index files
From the repo root:

1. Open `/mnt/c/Projects/ps/AI-Courses/index.html`. Find this course's card. Update the chapter count if it's shown.

### 8. Validation
Before reporting done:
- `wc -l` on the new chapter: confirm 400–600 lines.
- `grep -c '<div' NEW_FILE` vs `grep -c '</div>' NEW_FILE`: counts match.
- `grep -c 'class="exercise-box"' NEW_FILE`: ≥ 1.
- Confirm the course-specific required boxes are present (e.g., for AI-Harness: `.inside-look-box` present; for Security: `.threat-box`, `.shield-box`, `.real-attack-box`, `.think-like-attacker` all present).
- Confirm the previous chapter's `next` link points to the new file, not the index.
- Confirm `CLAUDE.md` now lists the chapter in both Progress Tracking and Chapter Details.

### 9. Mark the append item complete
1. In `UPDATES.md`, change the `[ ]` to `[x]` on this item and append ` [completed YYYY-MM-DD]`.

### 10. Do NOT stage, do NOT commit
Leave all changes unstaged. Report to the user with:
- New chapter file path and line count.
- Files modified (CLAUDE.md, chapters/index.html, previous chapter, root index files).
- A one-paragraph summary of what the new chapter covers.

## Failure modes to avoid

- **Using training data instead of WebSearch**: this command is specifically designed to close the baseline-quality gap. A chapter written from training data alone defeats the entire purpose — it will be stale the day it ships.
- **Inserting mid-course**: never. Always append. If the topic is conceptually mid-course, cross-link from the new chapter's intro.
- **Padding to hit 400 lines**: produce the full draft in one pass. If you're short, add a new substantive section (another concrete example, a case study, a compare-box) — never pad paragraphs line-by-line.
- **Skipping the previous chapter's nav update**: this is the one integration step most often forgotten, and it leaves a dead-end nav link in the previous chapter.
- **Forgetting root index updates**: the course's chapter count on the root catalog page will silently drift out of sync if you skip this.
