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

### 6. Headless / Unattended Generation

Once you're confident in the workflow, you can run a full course end-to-end without babysitting it using Claude Code's **headless mode** (`claude -p`). This is useful for overnight runs or for courses where you don't need to review each chapter as it lands.

#### Three gotchas the naive loop misses

A `for` loop around `claude -p "/generate-next-chapter"` works — but it doesn't match the manual workflow because:

1. **Slash commands can't be chained inside a single `-p` call.** `claude -p "/generate-next-chapter then /create-memory-map"` only runs the first command. You need two separate invocations.
2. **To reuse context across two invocations, pass `--resume <session-id>`.** Capture the session ID from the first call with `--output-format json`, then feed it to the next call. This is what lets `/create-memory-map` skip re-reading the chapter that was just written.
3. **`/compact` is interactive-only** — it cannot be invoked from `-p`. But because `/generate-next-chapter` reads progress from `CLAUDE.md` (not from in-memory state), **starting a fresh session every few pairs achieves the same effect as `/compact`**. No state is lost: the `[ ]` → `[x]` markers in `CLAUDE.md` are the source of truth.

#### The script

Paste this into a file (e.g. `run.sh`) at the root of the course directory, then `bash run.sh`:

```bash
#!/usr/bin/env bash
# Unattended chapter + memory-map generation.
# Requires: claude CLI and jq. Run from inside a course directory.
set -u
TOTAL=${TOTAL:-12}        # chapters in the course
BATCH_SIZE=${BATCH_SIZE:-4}   # fresh session after every N pairs (acts like /compact)
TOOLS="Read,Write,Edit,Bash"
session_id=""

run_claude() {
  local prompt="$1" attempt out
  for attempt in 1 2 3; do
    local args=(--output-format json --allowedTools "$TOOLS")
    [[ -n "$session_id" ]] && args+=(--resume "$session_id")
    if out=$(claude -p "$prompt" "${args[@]}"); then
      session_id=$(jq -r '.session_id' <<<"$out")
      return 0
    fi
    echo "  retry $attempt in $((attempt*30))s" >&2
    sleep $((attempt*30))
  done
  return 1
}

for i in $(seq 1 "$TOTAL"); do
  ch=$(printf "%02d" "$i")
  if (( (i-1) % BATCH_SIZE == 0 )); then
    session_id=""   # fresh session -> substitute for /compact
    echo "=== batch starting at chapter $ch ==="
  fi
  echo "[$ch] generate"; run_claude "/generate-next-chapter" || exit 1
  echo "[$ch] map";      run_claude "/create-memory-map $ch"  || exit 1
done
```

#### How it maps to the manual workflow

| Manual step | Script equivalent |
|---|---|
| Run `/generate-next-chapter` | First `run_claude` call — starts/resumes a session, captures session ID |
| Run `/create-memory-map NN` | Second `run_claude` call — **resumes the same session**, so the chapter is still in context |
| Run `/compact` after 3–4 pairs | Clear `session_id` every `BATCH_SIZE` pairs → next call starts fresh |
| Retry on 500 / rate limit | `run_claude` retries up to 3× with 30/60/90s backoff |
| Progress across sessions | Handled automatically by `CLAUDE.md` `[ ]`/`[x]` markers — safe to rerun |

#### Prerequisites & notes

- Install `jq` (`sudo apt install jq` / `brew install jq`) — needed to parse session IDs.
- Tweak `TOTAL` and `BATCH_SIZE` via env vars: `TOTAL=13 BATCH_SIZE=3 bash run.sh`.
- If the script exits non-zero mid-run, just re-run it — `/generate-next-chapter` will pick up at the first unchecked `[ ]` chapter.
- This is **not** a literal `/compact`; it's a session reset. For very long-running single sessions where you need true compaction, you still have to use the interactive workflow.
