Toggle a "Quality Checked" badge on a course to signal it has been personally read and approved by the author.

## Usage

`/mark-proofread <course-id> [color]`

- `<course-id>` is the value of the `data-course` attribute used in `index.html` (it also matches the course directory name). Examples: `AI-Intro`, `AI-Harness`, `Claude-Architect`, `Security`.
- `[color]` is optional and selects the ribbon color. Accepted values: `green` (default) and `orange`. Anything else → abort with an error listing the supported colors.

The color is only meaningful when toggling **ON**. When toggling OFF, the existing ribbon is removed regardless of its color.

## What this skill does

Toggles a diagonal corner ribbon labeled **"QUALITY CHECKED"** in two places. The ribbon is green by default; pass `orange` to use the orange variant instead.

1. The course card in `/mnt/c/Projects/ps/AI-Courses/index.html`
2. The hero section of `<course-id>/chapters/index.html` — anchored to the `<h1>` title's corner (not the wide hero's edge) so it sits visibly over the title

Running the skill again on the same course removes the badge (toggle).

This is a **manual marker only** — it must never be auto-derived from progress, completion state, or anything else.

## Steps

### 1. Parse and validate the arguments

- Read the user's first argument as `<course-id>`. If no argument was provided, abort and ask the user which course to mark.
- Read the optional second argument as `<color>`. If absent, default to `green`. If present but not one of `green` | `orange`, abort with an error stating the supported colors.
- Verify the course exists by checking that:
  - `data-course="<course-id>"` appears in `/mnt/c/Projects/ps/AI-Courses/index.html` (use Grep)
  - The directory `/mnt/c/Projects/ps/AI-Courses/<course-id>/chapters/index.html` exists
- If validation fails, abort with a helpful error message and list the valid course IDs (extract them via `grep -oE 'data-course="[^"]+"' index.html | sort -u`).

### 2. Detect current badge state

For each of the two target files, check whether the badge is already present **for this specific course**:

- `index.html`: read the file and find the line `<div class="course-card" data-course="<course-id>" ...>`. Look at the next line — if it contains `class="quality-ribbon"`, the badge is present in that file.
- `<course-id>/chapters/index.html`: search for the literal string `class="hero-title"` inside the `<section class="index-hero">` block. That wrapper only exists when the badge is present, so its presence is the signal. (Each course chapter index has only one hero, so a simple presence check is enough.)

### 3. Decide direction (toggle on vs off)

- If the badge is **present in every applicable file** → toggle **OFF** (remove).
- Otherwise → toggle **ON** (add it everywhere it's missing). This auto-heals partial state from manual edits.

### 4a. Toggle ON — insert the ribbon HTML

The ribbon element is one of:

- Green (default): `<div class="quality-ribbon" aria-label="Quality checked by author"><span>Quality Checked</span></div>`
- Orange: `<div class="quality-ribbon quality-ribbon--orange" aria-label="Quality checked by author"><span>Quality Checked</span></div>`

Pick the variant matching the resolved `<color>` from step 1 and use the same string in **all three** target files for this run.

**In `index.html`**: insert the ribbon as a new line immediately after the opening `<div class="course-card" data-course="<course-id>" ...>` line, before the existing `<div class="course-header">`. Match the surrounding indentation (the ribbon line should be indented to match the card's children).

Use the Edit tool with `old_string` containing the opening card div line plus the next line (to make the match unique to this card), and `new_string` inserting the ribbon between them.

**In `<course-id>/chapters/index.html`**: the hero is a full-width banner, so a bare corner ribbon ends up at the far edge of the page and is almost invisible. To anchor the ribbon to the **title's corner**, wrap the existing `<h1>` in a new `.hero-title` container and place the ribbon inside that wrapper.

Before:
```html
  <section class="index-hero">
    <h1>Course Title Here</h1>
    <p class="tagline">...</p>
  </section>
```

After:
```html
  <section class="index-hero">
    <div class="hero-title">
      <div class="quality-ribbon" aria-label="Quality checked by author"><span>Quality Checked</span></div>
      <h1>Course Title Here</h1>
    </div>
    <p class="tagline">...</p>
  </section>
```

Steps to perform this edit:
1. Read the chapter index.html to find the exact `<h1>...</h1>` line inside `<section class="index-hero">` (the title text varies per course — do not hardcode it).
2. Use Edit with `old_string` = the `<section class="index-hero">` line + the h1 line, and `new_string` = the same section line + the opening `<div class="hero-title">` + the ribbon line + the (re-indented) h1 + the closing `</div>`.
3. Preserve the original h1 indentation style and add two extra spaces of indentation to account for the new wrapper nesting.

Skip insertion in any file where the badge is already present.

### 4b. Toggle OFF — remove the ribbon HTML

The class on the ribbon line may be either `class="quality-ribbon"` (green) or `class="quality-ribbon quality-ribbon--orange"` (orange). Match whichever one is present — `<color>` is ignored when toggling OFF.

**In `index.html`**: use Edit to remove the entire ribbon line (including its trailing newline). The line is uniquely identifiable by `quality-ribbon` plus the opening card div on its previous line.

**In `<course-id>/chapters/index.html`**: reverse the wrapping — strip the `<div class="hero-title">` wrapper and the ribbon inside it, leaving just the `<h1>` back in its original position. Read the file first to capture the exact h1 text, then Edit the whole four-line block (`<div class="hero-title">`, ribbon line, h1 line, `</div>`) back into the original unwrapped `<h1>` line at the original indentation.

If multiple badges exist by accident in the same file, remove all of them.

### 5. Ensure CSS is present (only when toggling ON)

The badge needs CSS rules. They live in two stylesheets, and the blocks are **different** because the hero uses a title wrapper and the course cards do not:

#### 5a. Root stylesheet (powers `index.html`)

File: `/mnt/c/Projects/ps/AI-Courses/assets/style.css`

If the selector `.quality-ribbon` is not already present (use Grep), append this block at the end of the file:

```css

/* Quality Checked badge — added by /mark-proofread */
.course-card {
  position: relative;
  overflow: hidden;
}
.quality-ribbon {
  position: absolute;
  top: 18px;
  right: -52px;
  width: 180px;
  transform: rotate(45deg);
  background: linear-gradient(135deg, #16a34a, #15803d);
  color: #fff;
  text-align: center;
  font-size: 11px;
  font-weight: 700;
  letter-spacing: 0.09em;
  text-transform: uppercase;
  padding: 5px 0;
  box-shadow: 0 2px 6px rgba(0, 0, 0, 0.25);
  pointer-events: none;
  z-index: 5;
}
.quality-ribbon span { display: block; }
.quality-ribbon--orange { background: linear-gradient(135deg, #f97316, #c2410c); }
```

#### 5b. Course chapter stylesheet (powers `<course-id>/chapters/index.html`)

File: `/mnt/c/Projects/ps/AI-Courses/<course-id>/chapters/assets/style.css`

If the selector `.hero-title` is not already present (use Grep), append this block at the end of the file. Note the extra `.hero-title` wrapper rules and the adjusted ribbon offsets — they make the ribbon hug the title's top-right corner instead of the hero's far edge:

```css

/* Quality Checked badge — added by /mark-proofread */
.hero-title {
  position: relative;
  display: inline-block;
  overflow: hidden;
  padding: 0.4rem 1.5rem 0;
}
.hero-title h1 {
  margin-top: 0;
}
.quality-ribbon {
  position: absolute;
  top: 10px;
  right: -54px;
  width: 180px;
  transform: rotate(45deg);
  background: linear-gradient(135deg, #16a34a, #15803d);
  color: #fff;
  text-align: center;
  font-size: 11px;
  font-weight: 700;
  letter-spacing: 0.09em;
  text-transform: uppercase;
  padding: 5px 0;
  box-shadow: 0 2px 6px rgba(0, 0, 0, 0.3);
  pointer-events: none;
  z-index: 5;
}
.quality-ribbon span { display: block; }
.quality-ribbon--orange { background: linear-gradient(135deg, #f97316, #c2410c); }
```

Never duplicate either block. When toggling OFF, leave the CSS in place — it's harmless without the HTML, and other courses on the same page may still be using it.

If `.quality-ribbon` is already present in a stylesheet but `.quality-ribbon--orange` is not (i.e. the file predates the color option), append just this single rule once at the end of that file:

```css
.quality-ribbon--orange { background: linear-gradient(135deg, #f97316, #c2410c); }
```

### 6. Report what happened

Print a one-line summary that includes the color when toggling ON, e.g.:
- `Added green Quality Checked badge to AI-Intro (2 files updated, CSS added to 2 stylesheets)`
- `Added orange Quality Checked badge to AI-Harness (2 files updated)`
- `Removed Quality Checked badge from AI-Intro (2 files updated)`

## Important

- **Never auto-commit** the changes. Leave the edits unstaged for the user to review and commit themselves.
- **Idempotent**: running the same direction twice in a row should produce no further changes after the first run completes.
- **Per-course scoping**: when editing `index.html`, the Edit's `old_string` MUST include the card's opening `<div class="course-card" data-course="<course-id>" ...>` so it cannot accidentally match the wrong card.
- **No commits, no pushes, no other side effects** — this skill only edits files.
