Refresh ONE chapter of this course using the plan in `UPDATES.md`. Surgical edit — only the claims flagged by the auditor, never the evergreen content.

## Invocation
```
/refresh-next-chapter
```
Run from inside the course directory. No arguments. Reads `UPDATES.md`, picks the first unchecked refresh item, executes it, marks it done.

## CRITICAL: Preserve, don't rewrite

A confident LLM seeing a stale stat next to a good analogy will often "improve" the analogy while fixing the stat — and the analogy is the evergreen gold this course is built on. Three overlapping guardrails protect against this; follow ALL of them:

1. **Only edit what's listed.** If the UPDATES.md item says "Stale: Cursor pricing line ~412", you edit line 412. You do not reword the paragraph around it. You do not "improve" nearby sentences. If you spot a new stale claim mid-edit, append it as a new `[ ]` refresh item in `UPDATES.md` rather than fixing it in this invocation.
2. **Preserve blocks are untouchable.** The auditor listed analogies, exercises, "What's Next", and "Going Deeper" under **Preserve**. These are modified ONLY to replace specific stale facts named in the refresh item. They are never rewritten for style, flow, or "improvement."
3. **Structural invariants must hold.** After editing, grep-counts of custom CSS boxes and `<h2>` headings must match or exceed the original. Line count must stay within ±10% and never drop below 400.

## Steps

### 1. Load the plan
1. Read `UPDATES.md` in the current course directory. If it does not exist, stop and tell the user to run `/audit-course <course-id>` from the repo root first.
2. Find the first `[ ]` item under **Refresh queue**. If none, report "refresh queue empty" and stop.
3. Read that item's full block: stale claims, drifted claims, sources consulted, preserve list, scope estimate.

### 2. Read the chapter
1. Read the chapter HTML file in full.
2. Record these baseline counts (you will re-check after editing):
   - Total line count.
   - Count of each custom CSS box mentioned in this course's `CLAUDE.md` CSS registry (e.g., `.inside-look-box`, `.compare-box`, `.threat-box`, `.shield-box`, etc. — varies by course).
   - Count of `.tip-box`, `.warning-box`, `.exercise-box`, `.checklist`, `.highlight-box`.
   - Count of `<h2>` headings.
3. Locate each flagged claim in the file. Confirm the line numbers in `UPDATES.md` are still approximately correct (minor drift is fine; gross mismatch means the file has changed since audit — stop and re-audit).

### 3. Research phase (MANDATORY)
For each **STALE** claim in the refresh item:
1. Reuse the source URLs from `UPDATES.md` if they're less than 30 days old (check the dates recorded there).
2. Otherwise, run **one WebSearch** for the specific claim.
3. For any claim involving **pricing, version IDs, or benchmark numbers**, ALSO run **one WebFetch** on the authoritative vendor source (changelog, pricing page, release notes).
4. Record the exact replacement value (e.g., current model ID string, current price).

For **DRIFTED** claims in the same item (if any): same process, but if the web still supports the original claim, leave it and remove the drifted entry from `UPDATES.md`.

Do NOT research claims not listed in the refresh item. That's scope creep.

### 4. Edit with surgical precision

For each stale claim:
- Use the **Edit tool** (not Write). Small, targeted replacements.
- Replace only the stale token(s) — a model ID, a price, a feature name, a number.
- If a sentence around the claim is ALSO factually wrong as a consequence of the stale token, fix the minimum surrounding text. Example: if "Cursor offers a free tier at $0/mo, Pro at $20/mo" becomes "Cursor offers a free tier and Pro at $NEW/mo", rewrite exactly that sentence — not the paragraph.
- NEVER touch lines inside a **Preserve** block range unless that specific line contains one of the stale claims AND the fact being replaced is the problem.
- NEVER touch analogies, exercises, "What's Next", or "Going Deeper" except to swap a named fact.
- NEVER change HTML structure: no new divs, no renamed classes, no reflowed sections.

### 5. Validate
After all edits, verify ALL of these. If any fail, revert the problematic change and flag it:

1. **Line count**: total lines within ±10% of baseline, and ≥ 400.
2. **Custom box counts**: each custom box type present in the baseline is still present at ≥ the same count. Grep: `grep -c 'class="inside-look-box"' <file>` (or whatever boxes this course uses).
3. **Heading count**: `<h2>` count unchanged or higher.
4. **HTML tag hygiene**: `grep -c '<div' file` approximately equals `grep -c '</div>' file`. No invented closing tags (`</tip>`, `</note>`, `</card>`).
5. **Relative paths intact**: `assets/style.css`, prev/next nav links, any image refs unchanged.
6. **No broken quotes or entities**: scan for `&amp;amp;`, `""`, `''`, unclosed `<code>` or `<strong>`.

### 6. Diff-style report to user
Print a summary in this shape:

```
Refreshed: NN-slug.html

Changes:
  Line 65:  "claude-sonnet-4-20250514"  →  "claude-sonnet-4-7-20260301"
  Line 412: "$20/mo"                     →  "$25/mo (as of 2026-04)"
  Line 488: "Cascade (beta)"             →  "Cascade"

Preserved: kitchen analogy (lines 80–120), closing exercise (lines 445–470), What's Next.

Validation: ✓ line count 487 (baseline 485) ✓ box counts unchanged ✓ HTML valid.

Sources:
  - https://anthropic.com/... (2026-04-24)
  - https://cursor.com/pricing (2026-04-24)
```

### 7. Update tracking
1. In `UPDATES.md`, change this item's `[ ]` to `[x]` and append ` [completed YYYY-MM-DD]`.
2. If any new stale claims were discovered during the edit, append them as NEW `[ ]` refresh items in `UPDATES.md`.
3. If the chapter header area has room, optionally insert an HTML comment at the top of the file: `<!-- audited: YYYY-MM -->`. Replace any existing audit comment rather than stacking them.

### 8. Do NOT stage, do NOT commit
Leave all changes unstaged. The user reviews the diff and stages themselves.

## Escape hatches

- **If the UPDATES.md item is vague** (e.g., "refresh chapter — feels stale") and doesn't list specific claims: stop, tell the user, suggest they re-run `/audit-course` for this course.
- **If the auditor's line numbers are off by >20 lines**: the chapter has shifted significantly since audit. Stop and suggest re-audit.
- **If research reveals the original claim was already correct**: remove it from the stale list and note "verified current as of YYYY-MM-DD" in the UPDATES.md item before marking complete.
- **If validation fails after edits**: revert the offending change. Do not "fix" by adding compensating edits — the chapter was valid before, it must be valid after. Report what failed and why.

## Failure modes to avoid

- **Rewriting the analogy** because the paragraph around it had a stale stat. The stat is stale; the analogy is not. Edit one, leave the other.
- **Adding "modernization" edits** that weren't in the plan. If GitHub Copilot's description feels dated but it's not in the refresh item, leave it.
- **Fixing 10 claims when the item listed 3.** Append new claims to `UPDATES.md` for a future pass; do not fold them into this one.
- **Padding the chapter** to hit line count if a delete dropped you below 400. If you can't stay within ±10% by surgical edits alone, stop and re-scope the item — don't invent filler.
- **Trusting marketing pages** over vendor changelogs. Always prefer primary sources.
- **Using `Write` instead of `Edit`**. A full rewrite destroys the Preserve guarantee. Use `Edit` for every change.
