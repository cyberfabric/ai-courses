# Crash Course in Tech Skills: A PM's Guide to Windsurf, Git, and OpenSpec

## Project Description
An HTML course in English for non-technical Product Managers who need to learn enough tech skills to use Windsurf (AI-powered IDE), Git, BitBucket Server, and OpenSpec as part of their daily workflow. The target audience has zero technical background — they don't know what a CLI, IDE, or repository is.

The style is **"For Dummies"** — friendly, approachable, heavy on real-world analogies. The reader is smart (they're a PM) but has no background in developer tools. Explain everything through analogies to things they already know (Google Docs, email, file managers). Each chapter should make them feel more confident, not more confused.

**Platform:** Mac only (Terminal.app, Finder, Mac keyboard shortcuts).
**Git approach:** All Git operations through Windsurf UI — no terminal git commands.
**BitBucket:** BitBucket Server (self-hosted, not Cloud). Fork-based workflow.
**OpenSpec walkthrough:** Builds a Google Notes/Keep clone across Chapters 9-10.

## Language Rules
- All content is in **English**
- Tone: friendly, patient, encouraging — like a helpful colleague sitting next to you
- Use analogies from everyday work life (Google Docs, email, filing cabinets, sticky notes)
- **No jargon without explanation** — every technical term gets a plain-language definition first
- Address: second person singular (you)
- When introducing a concept, connect it to something the reader already knows
- Light humor is welcome — keep it warm, not condescending
- Use short paragraphs — walls of text are intimidating
- Never assume the reader knows what something is — when in doubt, explain it

## HTML Conventions
- Each chapter is a separate HTML file in `chapters/`
- Shared CSS: `assets/style.css` (relative path from chapters/)
- Each page includes:
  - `<nav class="top-nav">` with links to prev/next chapter, index, and theme toggle button
  - `<header class="chapter-header">` with chapter number and title
  - `<main>` with content
  - `<footer>` with prev/next navigation
  - `<script>` at the end of body for theme toggle (localStorage)
- Encoding: UTF-8
- HTML5 doctype
- Meta viewport for responsive
- Target chapter length: **400-600 lines HTML**

## File Structure
```
PM-Course/
  CLAUDE.md                              — This file
  presentation.html                      — Team reference: OpenSpec presentation
  .claude/
    commands/
      generate-next-chapter.md           — Skill for chapter generation
  chapters/
    index.html                           — Landing page with navigation
    assets/
      style.css                          — Shared CSS with dark/light theme
    01-welcome.html                      — Welcome to the Other Side
    02-terminal-basics.html              — The Terminal: Your New Friendly Neighbor
    03-buzzword-guide.html               — Speaking Developer: A Buzzword Survival Guide
    04-windsurf-intro.html               — Meet Windsurf: Your AI-Powered Workspace
    05-git-with-windsurf.html            — Your First Git Journey (No Terminal Required)
    06-remotes-and-bitbucket.html        — Remotes, BitBucket, and Working with Others
    07-first-pr.html                     — Pushing Code and Creating Your First PR
    08-openspec-intro.html               — OpenSpec: What It Is and Why You Care
    09-openspec-propose.html             — Hands-On: Starting a Google Notes App with OpenSpec
    10-openspec-apply.html               — Hands-On: Implementing, Archiving, and Adding Features
    11-specs-management.html             — Managing Your Specs Like a Pro
    12-full-workflow.html                — The Full PM Workflow: From Ticket to PR
    13-troubleshooting.html              — When Things Go Wrong: A Troubleshooting Guide
    14-cheat-sheet.html                  — Your Cheat Sheet and Next Steps
```

## Progress Tracking
- [x] Chapter 1: Welcome to the Other Side
- [x] Chapter 2: The Terminal: Your New Friendly Neighbor
- [x] Chapter 3: Speaking Developer: A Buzzword Survival Guide
- [x] Chapter 4: Meet Windsurf: Your AI-Powered Workspace
- [x] Chapter 5: Your First Git Journey (No Terminal Required)
- [x] Chapter 6: Remotes, BitBucket, and Working with Others
- [x] Chapter 7: Pushing Code and Creating Your First PR
- [x] Chapter 8: OpenSpec: What It Is and Why You Care
- [x] Chapter 9: Hands-On: Starting a Google Notes App with OpenSpec
- [x] Chapter 10: Hands-On: Implementing, Archiving, and Adding Features
- [x] Chapter 11: Managing Your Specs Like a Pro
- [x] Chapter 12: The Full PM Workflow: From Ticket to PR
- [x] Chapter 13: When Things Go Wrong: A Troubleshooting Guide
- [x] Chapter 14: Your Cheat Sheet and Next Steps

## Instructions for /generate-next-chapter
When the user invokes `/generate-next-chapter`:
1. Read this CLAUDE.md and find the first chapter marked with `[ ]` in Progress Tracking
2. Read the "Chapter Details" section below for that chapter's topics
3. Read `chapters/assets/style.css` for available CSS classes
4. Read `chapters/index.html` for navigation template
5. Read the previous chapter (if any) for context and smooth transition
6. For OpenSpec chapters (8-11), also read `presentation.html` for accurate OpenSpec information
7. Generate the HTML file in `chapters/` with full content (400-600 lines)
8. Update CLAUDE.md — mark the chapter as `[x]`
9. Update `chapters/index.html` — remove `pending` class from that chapter's card
10. Update navigation on the previous chapter if needed

## CSS Classes for Content
- `.screenshot-box` — visual guide: what the reader will see on screen (blue accent, unique to this course)
- `.try-it-box` — hands-on "your turn" moments (green accent, unique to this course)
- `.dont-panic-box` — reassurance when things look scary (lavender accent, unique to this course)
- `.real-world-box` — connecting tech to things PMs already know (amber accent, unique to this course)
- `.prompt-example.good` — good examples (green accent)
- `.prompt-example.bad` — bad examples (red accent)
- `.comparison` — side-by-side comparisons
- `.tip-box` — tips and advice
- `.warning-box` — warnings and cautions
- `.exercise-box` — formal exercises (gold accent)
- `.checklist` — checklists with checkmarks
- `.highlight-box` — key messages (gradient background)
- `.stats-grid` + `.stat-card` — statistics display
- `.tool-card` — tool description cards (icon + name + description)
- `.workflow-steps` + `.step` + `.step-arrow` — visual workflow pipeline
- `.reference-card` — link to external reference (used on index for presentation.html)
- `.theme-toggle` — theme switch button (in nav)

## Content Guidelines
- **At least one `.real-world-box`** per chapter connecting a concept to something familiar
- **At least one `.try-it-box`** per chapter (except purely conceptual chapters 3, 6, 8)
- **At least one `.screenshot-box`** in hands-on chapters describing what the reader will see
- **Use `.dont-panic-box`** whenever introducing something that might look intimidating
- Keep terminal commands to the absolute minimum (only Chapter 2 and OpenSpec init commands)
- **All Git operations through Windsurf UI** — never show git terminal commands
- **BitBucket Server** — self-hosted, company URL, not bitbucket.org
- **Fork workflow** — readers cannot edit the main repository directly
- Each chapter ends with a brief preview connecting to the next chapter
- No personal stories or references to specific team members — keep it generic

## OpenSpec Reference
Key commands and workflow (align with presentation.html):
- `openspec init` — Initialize OpenSpec in a project
- `openspec new change <name>` — Create a new change directory
- `/opsx:propose` (equals `/opsx:ff`) — Fast-forward: create all artifacts (proposal + specs)
- `/opsx:new` + `/opsx:continue` — Create artifacts one by one
- `/opsx:apply` — Implement the tasks from specs
- `/opsx:archive` — Archive working data; only WHEN/THEN scenarios go to specs/ folder
- `openspec status` — Check what's ready
- `openspec validate` — Validate specs
- `openspec list` — List changes and specs

**Two-phase workflow:**
- Phase 1 (PM, PR #1): proposal.md + specs/ (non-technical WHEN/THEN scenarios)
- Phase 2 (Dev, PR #2): design.md + tasks.md + implementation + archive

**Key behaviors:**
- When archiving, working data is archived and only the behavioral scenarios go to the specs/ folder
- When creating specs for a new feature, AI reads existing specs for context
- Change directories can be ticket-prefixed (e.g., `mob123-feature-name`)
- Specs must be non-technical, QA-friendly, behavioral (WHEN/THEN format)

## Chapter Details

### Chapter 1: Welcome to the Other Side
**File:** `01-welcome.html`
**Goal:** Set expectations, reduce fear, build excitement for what's coming.
**Topics:**
- What this course is about — a bridge from PM world to just enough tech
- Why this matters: you'll be creating specs and PRs, not writing code
- The tools you'll learn: Terminal (briefly), Windsurf, Git, BitBucket, OpenSpec
- How this course works: each chapter builds on the previous one
- What you WON'T need to learn: programming, databases, system architecture
- The end goal: by Chapter 12, you'll do the full workflow from ticket to PR
- The Google Notes app you'll build as practice in Chapters 9-10
- A quick roadmap of all 14 chapters

### Chapter 2: The Terminal: Your New Friendly Neighbor
**File:** `02-terminal-basics.html`
**Goal:** Demystify the terminal. By the end, the reader can navigate folders and create files confidently.
**Topics:**
- What is a terminal? (It's just a text-based way to talk to your computer)
- Other names for the same thing: CLI, command line, shell — all mean the same
- How to open Terminal on Mac: Spotlight (Cmd+Space, type "Terminal") or Applications > Utilities
- The prompt: what that blinking cursor means
- `pwd` — "Where am I?" (and seeing the same path in Finder)
- `ls` — "What's in this folder?" (and comparing with Finder's view)
- `cd` — "Go to that folder" (and `cd ..` to go back up)
- `mkdir` — "Create a new folder" (and watching it appear in Finder)
- `touch` — "Create a new empty file" (and watching it appear in Finder)
- The home directory: what `~` means
- How paths work: `/Users/yourname/Documents/my-project`
- Why developers use the terminal: it's faster for certain tasks
- Try-it: create a folder called `my-first-project`, put a file inside, verify in Finder
- Only these 6 commands — that's all you need for this course

### Chapter 3: Speaking Developer: A Buzzword Survival Guide
**File:** `03-buzzword-guide.html`
**Goal:** Build vocabulary so the reader isn't lost when developers use these terms. No hands-on, purely conceptual.
**Topics:**
- IDE — like Microsoft Word, but for code (Windsurf is an IDE)
- Repository (repo) — a project folder that remembers every change ever made
- Git — the technology that tracks changes (like Track Changes in Word, but way better)
- Commit — a save point with a description ("Added the login button")
- Branch — a parallel copy of the project to work on without breaking the original
- Merge — combining your changes back into the main project
- Pull Request (PR) — "Hey team, I made changes — please review before we merge"
- Fork — your personal copy of someone else's project (like photocopying a document)
- Clone — downloading a repository to your computer
- Push — uploading your changes to the server
- Pull — downloading the latest changes from the server
- BitBucket — where repositories live online (like Google Drive, but for code)
- How all these terms connect: a visual flow diagram
- Real-world analogy tying it all together

### Chapter 4: Meet Windsurf: Your AI-Powered Workspace
**File:** `04-windsurf-intro.html`
**Goal:** The reader can open a project in Windsurf and navigate the interface confidently.
**Topics:**
- What is Windsurf? An IDE with a built-in AI assistant (Cascade)
- Downloading and installing Windsurf on Mac
- Opening Windsurf for the first time: what you see
- Opening a folder: File > Open Folder (use the project folder from Chapter 2)
- The three main panels:
  - File Explorer (left) — your project's files and folders, like Finder
  - Editor (center) — where you view and edit file contents
  - Cascade (AI chat) — your AI assistant you can ask questions
- Creating a new file from Windsurf (right-click in file explorer)
- Editing a file: click to open, type, save with Cmd+S
- The integrated terminal (bottom panel) — you'll use this for OpenSpec commands later
- Don't panic about all the buttons — you only need a few
- Try-it: open your project folder, create a text file, type a sentence, save it

### Chapter 5: Your First Git Journey (No Terminal Required)
**File:** `05-git-with-windsurf.html`
**Goal:** The reader can initialize a repo, stage, commit, and view history — all from Windsurf UI.
**Topics:**
- What "initializing a repository" means: turning on change tracking for this folder
- Finding the Source Control panel in Windsurf (the branch icon on the left sidebar)
- Initializing a Git repo: click "Initialize Repository" button
- Creating a file and seeing the "U" badge (Untracked — Git doesn't know about this file yet)
- Staging: telling Git "include this file in my next save point"
- Writing a commit message: describe what you did in one sentence
- Clicking "Commit": your first save point is created
- Editing the file and seeing the "M" badge (Modified — Git noticed you changed something)
- Staging and committing the edit with a new message
- Deleting a file and seeing the "D" badge (Deleted)
- Committing the deletion
- Viewing your commit history: the timeline of all your save points
- The pattern: change → stage → write message → commit (repeat forever)
- Try-it: create a file, commit; add text, commit; remove text, commit; check the log

### Chapter 6: Remotes, BitBucket, and Working with Others
**File:** `06-remotes-and-bitbucket.html`
**Goal:** Understand the conceptual model of remote repos, forks, and PRs. No hands-on commands.
**Topics:**
- Local vs remote: your computer vs the company server
- What BitBucket Server is: a website hosted by your company (not bitbucket.org)
- Accessing BitBucket: you'll use your company's internal URL in a browser
- Why companies use their own server: security, control, compliance
- Browsing repositories on BitBucket: seeing files, commits, branches
- Why you can't edit the main repository directly: it's the source of truth
- Forks explained: your personal copy of the main repo on BitBucket
- The fork workflow step by step:
  1. Fork the repo on BitBucket (creates your copy)
  2. Clone your fork to your Mac (download it)
  3. Create a branch (isolate your changes)
  4. Make changes and commit
  5. Push to your fork (upload back to BitBucket)
  6. Create a Pull Request from your fork to the main repo
- Pull Requests: the review process, comments, approvals, merging
- What happens after merge: your changes are now in the main project
- Real-world analogy: forks are like photocopying a master document, making edits on your copy, then submitting your edits for the team to review and approve

### Chapter 7: Pushing Code and Creating Your First PR
**File:** `07-first-pr.html`
**Goal:** Walk through the full cycle: clone → branch → change → commit → push → PR.
**Topics:**
- Starting point: you have a forked repository on BitBucket
- Cloning your fork in Windsurf: how to get the clone URL from BitBucket
- Opening the cloned project in Windsurf
- Understanding what appeared on your Mac after cloning
- Creating a new branch in Windsurf (bottom-left branch indicator → Create New Branch)
- Naming your branch: descriptive names like `add-login-specs`
- Making a change: create or edit a file
- Staging and committing (same as Chapter 5)
- Pushing your branch: Windsurf will offer to "Publish Branch" — click it
- What just happened: your branch is now on your fork on BitBucket
- Opening BitBucket in your browser, navigating to your fork
- Creating a Pull Request: source (your fork/branch) → destination (main repo/main branch)
- Filling in the PR: title, description, adding reviewers
- What happens next: the team reviews, leaves comments, approves
- After approval: the maintainer merges your PR
- Try-it: walk through the entire cycle with a practice file

### Chapter 8: OpenSpec: What It Is and Why You Care
**File:** `08-openspec-intro.html`
**Goal:** Understand OpenSpec conceptually — what it is, why it exists, and the PM's role.
**Topics:**
- The problem: miscommunication between "what to build" and "how to build it"
- Spec-Driven Development: define the behavior first, then implement
- OpenSpec in one sentence: a framework that organizes HOW you describe WHAT to build
- The four artifacts:
  - `proposal.md` — WHY and WHAT (the business case)
  - `specs/` — WHAT the system does (behavioral scenarios, WHEN/THEN format)
  - `design.md` — HOW to implement (technical, dev-owned)
  - `tasks.md` — Implementation checklist (technical, dev-owned)
- Your role as PM: you own `proposal.md` and `specs/` (Phase 1, PR #1)
- The developer's role: they own `design.md` and `tasks.md` (Phase 2, PR #2)
- What specs look like: plain-language WHEN/THEN scenarios, no code, no technical jargon
- The handoff: you submit PR #1 with specs, the dev picks up and creates PR #2
- How AI helps: you describe what you want, AI generates the specs, you review and refine
- OpenSpec commands overview (just names, you'll use them in Chapter 9)
- Link to the team presentation (presentation.html) for the full reference
- Real-world analogy: specs are like a recipe — describe the dish, not the cooking technique

### Chapter 9: Hands-On: Starting a Google Notes App with OpenSpec
**File:** `09-openspec-propose.html`
**Goal:** Walk through init, propose, and review for a Google Notes/Keep clone.
**Topics:**
- What you'll build: a simple notes app like Google Keep (grid of note cards, create/edit notes, light/dark theme)
- Setting up: open an empty folder in Windsurf
- Opening Windsurf's integrated terminal (Ctrl+` or View > Terminal)
- Running `openspec init` — what appeared (the `openspec/` directory)
- Exploring the structure: changes/, specs/, archive/
- Running `/opsx:propose` in the Cascade chat with your feature description
- What to type: describe the Notes app features in plain language
- Watching AI generate the proposal and specs
- Reviewing `proposal.md`: does the WHY and WHAT make sense?
- Reviewing the specs: are the WHEN/THEN scenarios correct? Are they complete?
- Refining: telling AI to adjust scenarios (you're the PM, your judgment matters)
- Understanding the change directory that was created
- Committing the proposal and specs using Windsurf Source Control (like Chapter 5)
- What you just did: Phase 1 of the OpenSpec workflow, ready for a PR
- Try-it: create the proposal and specs yourself, review every scenario

### Chapter 10: Hands-On: Implementing, Archiving, and Adding Features
**File:** `10-openspec-apply.html`
**Goal:** Complete the cycle: apply, archive, then do a second feature to see spec evolution.
**Topics:**
- Quick recap: you have a proposal + specs for the Notes app, committed
- Running `/opsx:apply` in Cascade — watching AI implement the features
- What happened: code was generated, tasks were checked off in tasks.md
- You don't need to understand all the code — that's the dev's domain
- Running `/opsx:archive` — what archiving does:
  - Working data (proposal, design, tasks) moves to the archive/ directory
  - Only the WHEN/THEN behavioral scenarios move to the specs/ folder
  - The specs/ folder becomes the "source of truth" for what the app does
- Committing after archive
- Starting feature #2: adding random colors to note cards
- Running `/opsx:propose` again with the color feature description
- How AI reads existing specs: it knows about the notes feature already
- Reviewing new specs: notice they reference existing behavior
- Running `/opsx:apply` and `/opsx:archive` for the second feature
- After archiving: the specs/ folder now includes both features' scenarios
- The key insight: specs accumulate and evolve, becoming the living documentation
- Try-it: add a third feature (e.g., pinning notes to the top) on your own

### Chapter 11: Managing Your Specs Like a Pro
**File:** `11-specs-management.html`
**Goal:** Day-to-day OpenSpec management — naming, organizing, validating, and understanding spec evolution.
**Topics:**
- Ticket-prefixed change directories: `mob123-add-dark-mode` (company convention)
- Why ticket prefixes matter: traceability from ticket to specs to code
- Multiple changes at the same time: each gets its own directory
- The specs/ folder as Single Source of Truth: accumulated behavioral knowledge
- How archiving works in detail:
  - Before archive: changes/mob123-add-dark-mode/ has all working files
  - After archive: only WHEN/THEN scenarios survive in specs/
  - Technical details (design, tasks) go to archive/ for reference
- How AI uses existing specs: when you create a new change, AI reads all current specs
- Why this matters: new features are consistent with existing behavior
- Useful commands:
  - `openspec status` — what needs attention?
  - `openspec validate` — are my specs well-formed?
  - `openspec list` — overview of all changes and specs
- Keeping specs non-technical: the rules in config.yaml
- What good specs look like vs bad specs (comparison examples)
- Try-it: run `openspec status`, `list`, and `validate` on your Notes app project

### Chapter 12: The Full PM Workflow: From Ticket to PR
**File:** `12-full-workflow.html`
**Goal:** Tie everything together — the complete end-to-end flow a PM follows daily.
**Topics:**
- The complete workflow visualized as a step pipeline
- Step 1: Receive a ticket (e.g., "MOB-456: Add dark mode to the Notes app")
- Step 2: Open the project in Windsurf
- Step 3: Create a branch (e.g., `mob456-add-dark-mode`)
- Step 4: `openspec new change mob456-add-dark-mode`
- Step 5: `/opsx:propose` — create proposal and specs, review them
- Step 6: Refine specs — your PM judgment matters here
- Step 7: Commit using Windsurf Source Control
- Step 8: Push and create a PR on BitBucket Server
- Step 9: Team reviews your specs PR
- Step 10: After approval and merge — dev picks up and creates PR #2
- What to look for when reviewing the dev's PR #2
- Tips for writing good specs: be specific, be behavioral, think about edge cases
- Common mistakes PMs make and how to avoid them
- This is your daily workflow — it gets easier every time

### Chapter 13: When Things Go Wrong: A Troubleshooting Guide
**File:** `13-troubleshooting.html`
**Goal:** Build confidence by showing that errors are normal and fixable.
**Topics:**
- First rule: error messages are messages, not explosions — read them
- Terminal errors:
  - "command not found" — you mistyped or the tool isn't installed
  - "No such file or directory" — you're in the wrong folder
  - "Permission denied" — rare, ask a developer for help
- Git errors:
  - "nothing to commit" — you forgot to save the file or stage the changes
  - "please tell me who you are" — Git needs your name and email (one-time setup)
  - "push rejected" — someone else changed the remote, you need to pull first
  - "detached HEAD" — you're looking at history, not a branch — just switch back
- Windsurf issues:
  - Files not showing — you opened the wrong folder
  - Source Control not visible — no repo initialized yet
  - Cascade not responding — check your internet connection
- OpenSpec issues:
  - "no active change" — run `openspec new change` first
  - Specs not generating — describe the feature more clearly
- BitBucket issues:
  - Can't create PR — check you're on the right branch and fork
  - "No reviewers" — ask your team lead for the right reviewer list
- The golden rule: read the error message out loud — it usually tells you what to do
- When to ask for help: you've tried twice and it's still not working

### Chapter 14: Your Cheat Sheet and Next Steps
**File:** `14-cheat-sheet.html`
**Goal:** Quick reference card for everything learned. The chapter they'll bookmark.
**Topics:**
- Terminal quick reference (the 6 commands you need):
  - `pwd` — where am I?
  - `ls` — what's here?
  - `cd <folder>` — go there
  - `cd ..` — go up one level
  - `mkdir <name>` — create a folder
  - `touch <name>` — create a file
- Git workflow quick reference (the 4-step cycle):
  - Change a file
  - Stage the change
  - Write a commit message
  - Commit
- Windsurf quick reference:
  - Open folder: File > Open Folder
  - Source Control: branch icon in left sidebar
  - Terminal: Ctrl+` or View > Terminal
  - Save: Cmd+S
- OpenSpec quick reference:
  - `openspec init` — start OpenSpec
  - `openspec new change <name>` — new feature
  - `/opsx:propose` — create proposal + specs
  - `/opsx:apply` — implement
  - `/opsx:archive` — finalize
  - `openspec status` / `validate` / `list` — check state
- BitBucket PR quick reference:
  - Fork → Clone → Branch → Change → Commit → Push → PR
- Glossary: every term from the course, A-Z
- What to learn next if you're curious
- Confidence reminder: you now know enough to participate meaningfully in technical workflows
