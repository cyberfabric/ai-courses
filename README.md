# AI-Courses

A collection of HTML-based courses in **"For Dummies"** style, built with Claude Code. Each course targets a specific audience and covers a focused topic — from AI fundamentals to on-device Android ML to personal productivity agents.

## Project Structure

```
AI-Courses/
├── CLAUDE.md                          # Project-wide instructions
├── index.html                         # Full course catalog
├── .claude/commands/                  # Root-level skills (scaffold + audit/refresh/append/mark-proofread)
│
├── CourseName/                        # Each course follows this layout:
│   ├── CLAUDE.md                      # Course description & chapter details
│   ├── .claude/commands/
│   │   ├── generate-next-chapter.md   # Chapter generation command
│   │   └── create-memory-map.md       # Visual summary generation command
│   └── chapters/
│       ├── index.html                 # Landing page with chapter navigation
│       ├── assets/style.css           # Shared CSS (dark/light theme)
│       ├── 01-topic.html              # Numbered chapter files
│       ├── 02-topic.html
│       └── maps/                      # Visual memory maps
│           ├── 01-topic-map.html
│           └── 02-topic-map.html
```

## Workflows

All workflows use **Claude Code slash commands**. Make sure you're in the correct directory before running them.

### 1. Create a New Course

From the **root** directory (`AI-Courses/`):

```
/scaffold-new-course
```

Provide a description of what the course should cover, who it's for, and any specific topics. Claude will scaffold the full course structure.

### 2. Generate Chapters

Navigate **inside** the course directory first, then run:

```
/generate-next-chapter
```

This generates the next chapter in sequence based on the course's `CLAUDE.md` plan.

### 3. Create a Memory Map

Memory maps are single-page visual summaries of a chapter — concept cards, flow diagrams, quizzes, and key takeaways. From **inside** the course directory:

```
/create-memory-map 01
```

Replace `01` with the chapter number you want to summarize.

### 4. Maintain an Existing Course

Once a course is published, the world keeps moving — model versions ship, vendor docs reshuffle, new techniques appear. Four root-level skills (run from the **root** `AI-Courses/` directory) keep courses fresh:

```
/audit-course <course-id>           # produce a refresh+append plan in <course>/UPDATES.md
/refresh-next-chapter <course-id>   # apply one refresh from the queue
/append-next-chapter <course-id>    # generate one new chapter from the queue
/mark-proofread <course-id> [color] # toggle a "Quality Checked" ribbon
```

The flow is **audit → refresh/append → mark-proofread**:

- **`/audit-course`** is read-only. It re-verifies every load-bearing claim with fresh `WebSearch` and writes a `UPDATES.md` plan into the course — two queues (chapters to refresh, new chapters to append) plus the source URLs it consulted. It never edits chapters itself.
- **`/refresh-next-chapter`** pops one item from the refresh queue, re-grounds it with fresh `WebSearch`, applies the edits (honoring `Preserve` ranges from `UPDATES.md`), regenerates the chapter's memory map, and ticks the checkbox. Re-invoke to advance.
- **`/append-next-chapter`** pops one item from the append queue, re-verifies the topic is still warranted, generates the new chapter, wires it into `CLAUDE.md` / `chapters/index.html` / the previous chapter's footer, bumps the chapter count in the root catalog, and (if the course uses them) generates a memory map. Re-invoke to advance.
- **`/mark-proofread`** toggles a green or orange "QUALITY CHECKED" ribbon on the course card in `index.html` and on the chapter index hero — used after you've personally read a course end-to-end.

All three maintenance commands re-run `WebSearch` at execution time (not just at audit time), so a stale `UPDATES.md` won't quietly land bad facts.

### 5. Recommended Flow: Full Course Generation

For generating an entire course (chapters + memory maps) efficiently, use this batch workflow:

1. `cd` into the course directory
2. Enter **plan mode** (once for the whole session)
3. Run `/generate-next-chapter`
4. Run `/create-memory-map XX` (where `XX` is the chapter just generated)
5. Repeat steps 3–4 three to four times
6. Run `/compact` to free up context
7. Repeat steps 3–6 until all chapters are done

> **Why plan mode?** It helps Claude maintain a coherent plan across chapters and keeps generation consistent.
>
> **Why compact?** Each chapter is 400–600 lines of HTML. After a few chapters, compacting the conversation prevents hitting context limits and keeps generation fast.