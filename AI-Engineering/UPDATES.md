# Course Updates — AI-Engineering
Generated: 2026-04-30
Auditor: Claude Code /audit-course

## Summary
- Chapters scanned: 12
- Refresh queue: 11 items (5 substantive, 6 light)
- Append queue: 1 candidate
- Do-not-touch: 1 chapter

The user pre-flagged three concerns and all three are confirmed by live-web verification:
1. `.ctx` is **not** a real Claude Code feature — the course invented the extension. Anthropic's product uses `.md` files in `.claude/rules/` with YAML frontmatter. ~60 mentions across 11 files.
2. The course teaches "skills" but uses the legacy path `.claude/commands/`. In current Claude Code (2026), slash commands and skills are unified and the recommended shape is `.claude/skills/<name>/SKILL.md`. The old `.claude/commands/` path still works as legacy.
3. The `.claude/rules/` explanation is correct but incomplete: it doesn't mention `.claude/skills/` as a peer of `.claude/rules/`, and it doesn't acknowledge documented bugs with the `paths:` frontmatter (the `globs:` field is more reliable, and rules don't fire on Write only Read).

## Refresh queue

- [x] 04-skills-at-scale.html — heavy
  - Stale: line 37 defines a skill as "a reusable prompt stored as a Markdown file in your project's `.claude/commands/` directory" — current Claude Code recommends `.claude/skills/<name>/SKILL.md` (a directory containing SKILL.md plus optional supporting files); the `.claude/commands/` path is legacy that still works
  - Stale: starter library directory tree (lines 51-80) shows flat `.md` files in `.claude/commands/` — should show `skills/<name>/SKILL.md` shape; mention that supporting files (templates, scripts) can sit alongside SKILL.md
  - Stale: example skill files (lines 139, 202, 235, 354) all use `.claude/commands/<name>.md` — should update to `.claude/skills/<name>/SKILL.md`
  - Stale: maturity rubric (line 435) "3-5 skills in .claude/commands/" — update path
  - Stale: closing exercise (lines 458, 469) `mkdir -p .claude/commands` and acceptance criteria — update path
  - Drifted: chapter doesn't mention frontmatter that lets Claude auto-invoke a skill; current best-practice skills use frontmatter to control whether the user or Claude triggers the skill
  - Sources consulted: https://code.claude.com/docs/en/skills (2026-04-30), https://code.claude.com/docs/en/slash-commands (2026-04-30)
  - Preserve: function-vs-CLI analogy (line 42), skill anatomy section (lines 134-175), `/generate-next-chapter` case study (lines 261-291), naming-convention table (lines 86-110), closing exercise structure (lines 451-470)
  - Scope: heavy — concept update, not just find-replace

- [x] 07-architecture-rules.html — heavy
  - drift since audit: chapter was already substantively refreshed before this run (`.ctx` → `.claude/rules/` swap mostly done at lines 47-82/169/245/327/352; Read-only loading limitation already documented at chapter lines 290-292 with #23478 link). Remaining work was 3 string edits (lines 395, 413, 425) plus one new warning-box about open `paths:` YAML bugs (#17204, #13905, #21858). Effective scope: light, not heavy.
  - Stale: every `.ctx` reference (lines 47-82, 169, 245, 327, 352, etc.) — Claude Code has no `.ctx` extension; the dual-format pattern still works but uses plain `.md` files in `.claude/rules/`
  - Stale: line 218 "drop a markdown file in there with a `paths:` frontmatter" — `paths:` has documented bugs (anthropics/claude-code#13905, #17204); recommend `globs:` as the more reliable default and note the documentation gap
  - Stale: line 395 example skill at `.claude/commands/check-architecture.md` — update to `.claude/skills/check-architecture/SKILL.md`
  - Drifted: chapter doesn't mention the Read-only loading limitation — path-scoped rules fire when Claude reads a matching file but not on Write/Create (anthropics/claude-code#23478); readers writing rules to enforce Write-time conventions need to know this
  - Sources consulted: https://code.claude.com/docs/en/memory (2026-04-30), https://github.com/anthropics/claude-code/issues/13905 (2026-04-30), https://github.com/anthropics/claude-code/issues/17204 (2026-04-30), https://github.com/anthropics/claude-code/issues/23478 (2026-04-30), https://github.com/anthropics/claude-code/issues/16299 (2026-04-30)
  - Preserve: dual-format pattern intro (lines 47-82), the 10 topic areas table (lines 88-111), symlink section (lines 277-288), cross-tool note about AGENTS.md (line 300), closing exercise (lines 496-510)
  - Scope: heavy — affects the chapter's central pattern

- [x] 03-context-engineering.html — medium
  - drift since audit: the `.ctx` → `.claude/rules/` framing was already done before this run (no `.ctx` references remain in the chapter). Effective work was 3 additive edits: 5-min TTL nuance with 1h-vs-5m write-cost note added to line ~119, `.claude/skills/` block added to the recipes-app directory diagram, and `.claude/skills/` mention added to readiness rubric levels 3 and 4. Chapter was already 715 lines (over the 600 band before refresh) — added 4 lines, did not trim per skill's no-line-cut rule.
  - Stale: line 325 "Claude Code now supports this natively through path-scoped rules in `.claude/rules/`" is fine, but the surrounding `.ctx` framing (line 325 onward, plus references throughout) needs to use plain `.md` in `.claude/rules/`
  - Stale: directory diagram around line 409 only mentions `.claude/rules/` — should also include `.claude/skills/` so the reader's mental model of `.claude/` is complete
  - Stale: readiness rubric (lines 620-630) talks about "no `.claude/rules/` files" but never mentions `.claude/skills/` as a separate readiness signal
  - Drifted: line 119 mentions caching of unscoped `.claude/rules/` files — accurate but should clarify that the cache TTL default is now 5 minutes (early-March 2026 change), so longer idle periods cost a re-cache
  - Sources consulted: https://code.claude.com/docs/en/memory (2026-04-30), https://platform.claude.com/docs/en/build-with-claude/prompt-caching (2026-04-30)
  - Preserve: mise-en-place analogy (line 42), context budget concept (lines 200-234), conflicting-rules warning (lines 444-451), closing exercise (lines 640-670), the "what reloads / what evaporates" framing (line 161)
  - Scope: medium — terminology + one missing concept (skills as peer)

- [x] 10-cost-engineering.html — medium
  - Stale: 14 `.ctx` mentions — lines 33, 42, 82, 120, 130, 138 and through; replace with `.md` rule file or "rule file in `.claude/rules/`"
  - Stale: stat at line 120 "~2K tokens for full architecture rules (10 .ctx files)" — restate as "10 `.claude/rules/*.md` files"
  - Drifted: line 47 "Cached content expires after 5 minutes of inactivity" — currently accurate (Anthropic moved to 5-minute default in early March 2026), but worth adding that 1-hour caching is still available as a paid option (2× write cost vs 1.25× for 5-min); some readers will want this lever
  - Drifted: lines 151-160 model selection table (Opus/Sonnet/Haiku) — model names are stable, but if specific dollar figures get added during refresh, current public pricing is Opus 4.6 $5/$25 per M tokens, Sonnet 4.6 $3/$15
  - Sources consulted: https://platform.claude.com/docs/en/build-with-claude/prompt-caching (2026-04-30), https://platform.claude.com/docs/en/about-claude/pricing (2026-04-30)
  - Preserve: caching mechanics intro (lines 37-43), 5-min TTL scenario table (lines 45-63 — TTL number is currently right, leave it), the four-step prompt-prefix workflow (lines 69-101), before/after comparison (lines 126-145), model-selection guidance (lines 162-198), closing exercise
  - Scope: medium — heavy find-replace plus one TTL nuance

- [x] 11-project-audit.html — medium
  - Stale: 13 `.ctx` mentions threaded through the audit rubric — same swap to `.md` rule files
  - Stale: line 177 upgrade table "Move to .claude/commands/ and commit" — update to `.claude/skills/`; mention legacy compat for teams who already have `.claude/commands/`
  - Stale: line 396 "How many skills are in .claude/commands/?" — update path
  - Stale: line 377 example skill at `.claude/commands/audit-readiness.md` — update to `.claude/skills/audit-readiness/SKILL.md`
  - Drifted: rubric should add a row asking "does the project use `.claude/skills/` (current) or only `.claude/commands/` (legacy)?" — this is a real readiness signal in 2026
  - Sources consulted: https://code.claude.com/docs/en/skills (2026-04-30), https://code.claude.com/docs/en/slash-commands (2026-04-30)
  - Preserve: 5-pillar framework (lines 39-90), per-pillar scoring rubric (lines 66-260), prioritized improvement plan (lines 306-366), closing audit exercise (lines 424-435)
  - Scope: medium — terminology + one new rubric row

- [x] 01-ai-ready-gap.html — light
  - Stale: 6 `.ctx` mentions (lines 126, 232, etc.) — pure find-replace to `.md rule file in .claude/rules/`
  - Sources consulted: https://code.claude.com/docs/en/memory (2026-04-30)
  - Preserve: AI-Ready Spectrum table (lines 45-104), 5-pillar framework (lines 107-137), compounding-effect section (lines 186-219), Quick Readiness Check exercise (lines 405-434)
  - Scope: light (≤5 claims, simple substitution)

- [x] 02-claude-md-mastery.html — light
  - drift since audit: chapter was already 675 lines pre-refresh (over the 600 band) before this run started. Net change: +4 lines for the new `.claude/skills/` peer-concept tip-box → 679 lines. Skill's no-line-cut rule means the overflow is preserved as-is.
  - Stale: 2 `.ctx` mentions — replace with `.md` in `.claude/rules/`
  - Drifted: cross-references to `.claude/rules/` (lines 159, 188, 264, 601) are correct but should mention `.claude/skills/` once as the peer concept readers will encounter
  - Sources consulted: https://code.claude.com/docs/en/memory (2026-04-30), https://code.claude.com/docs/en/skills (2026-04-30)
  - Preserve: 4-tier hierarchy explanation (lines 45-100), specificity-ladder and negative-space technique (lines 196-241), recipes app teardown (lines 334-405), closing exercise (lines 618-637)
  - Scope: light

- [x] 06-mcp-integration.html — light
  - drift since audit: fresh research surfaced a NEW drift the audit missed — Claude Code's canonical project-shared MCP config location in 2026 is `.mcp.json` at the project root (managed via `claude mcp add --scope project`), while the chapter still teaches `.claude/settings.json`. Both still work, but the audit declared MCP guidance evergreen. Worth a follow-up edit in a future pass; this run only addressed the 2 cited `.ctx` mentions per scope discipline.
  - Stale: 2 `.ctx` mentions including line 368 "A .ctx file is faster, cheaper, and always available. MCP requires a running server, network access, and API tokens" — reword in terms of `.md` rule files in `.claude/rules/`; the underlying point (static rule files vs running MCP server) is still valid
  - Sources consulted: https://code.claude.com/docs/en/memory (2026-04-30)
  - Preserve: MCP client-server architecture intro (lines 39-43), project-level vs user-level config (lines 120-140), read-only database pattern (lines 217-261), MCP security boundaries (lines 298-315), all MCP-specific guidance (it is evergreen)
  - Scope: light

- [x] 08-team-onboarding.html — light
  - Stale: 4 `.ctx` mentions — same swap
  - Stale: lines 263-267 table "Team skills | .claude/commands/" and "Personal skills | ~/.claude/commands/" — update to `.claude/skills/` and `~/.claude/skills/`; mention legacy `.claude/commands/` still works
  - Stale: line 293 example skill at `.claude/commands/adoption-report.md` — update to `.claude/skills/adoption-report/SKILL.md`
  - Stale: line 297 bash check `ls .claude/commands/*.md | wc -l` — update path
  - Sources consulted: https://code.claude.com/docs/en/skills (2026-04-30)
  - Preserve: team maturity model (lines 47-136), evidence-based skeptic conversion (lines 173-207), shared vs personal config boundaries (lines 252-276), onboarding checklist template (lines 309-347)
  - Scope: light

- [x] 09-thinking-and-planning.html — light
  - Stale: 8 `.ctx` mentions in passing references — same swap
  - Stale: three example skill paths at lines 157, 298, 338 (`.claude/commands/extract-module.md`, `.claude/commands/plan-migration.md`, `.claude/commands/draft-adr.md`) — update to `.claude/skills/<name>/SKILL.md`
  - Stale: line 490 artifact "one plan-mode skill in `.claude/commands/`" — update path
  - Sources consulted: https://code.claude.com/docs/en/skills (2026-04-30), https://code.claude.com/docs/en/sub-agents (2026-04-30)
  - Preserve: extended-thinking decision matrix (lines 50-65), plan-execute-validate pattern (lines 95-151), case-study comparisons (lines 226-267), closing exercise (lines 452-491)
  - Scope: light

- [x] 12-playbook.html — light
  - Stale: 2 `.ctx` mentions — same swap
  - Stale: line 137 example skill at `.claude/commands/maintenance-review.md` — update to `.claude/skills/maintenance-review/SKILL.md`
  - Stale: line 153 "List all skills in .claude/commands/" — update path
  - Drifted: line 169 "Staying Current" section is generic; could mention `.claude/skills/` and the skill-vs-command unification as one example of what "staying current" looks like — small addition, not a rewrite
  - Sources consulted: https://code.claude.com/docs/en/skills (2026-04-30)
  - Preserve: complete configuration checklist (lines 34-114), maintenance schedule (lines 116-163), AI-Ready Project Template structure (lines 192-240), 90-day plan (lines 264-321), AI Engineering Manifesto (lines 376-392)
  - Scope: light

- [x] index.html — trivial
  - Stale: 2 `.ctx` mentions in chapter blurbs — one-line edits to use `.md` rule files / `.claude/rules/`
  - Sources consulted: https://code.claude.com/docs/en/memory (2026-04-30)
  - Preserve: card layout, navigation, course-overview text
  - Scope: trivial

### Companion update — CLAUDE.md (the course's spec file)

The course's own `CLAUDE.md` should be updated alongside the chapter refreshes so future regenerations don't reintroduce the old terminology:
- Chapter 3 details mention "the `.ctx` file pattern: condensed reference files (25 lines max)" — update to "the path-scoped rule pattern: condensed `.md` files in `.claude/rules/` with `paths:` or `globs:` frontmatter".
- Chapter 7 details mention "Condensing to `.ctx` files" — update to "Condensing to path-scoped rule files".
- Chapter 4 details refer to "skill library" and the "skill" concept — fine to keep; just ensure any examples in chapter generation will use `.claude/skills/` as the recommended path.
- File Structure block (top of CLAUDE.md) shows `.claude/commands/` for course-meta skills (`generate-next-chapter.md`, `create-memory-map.md`) — these are this course's *own* tooling and currently still work as legacy commands; leave them alone unless the user wants to migrate them in the same pass.

## Append queue

- [ ] New: Plugins and Distribution: Shipping AI-Ready Config
  - Why: Plugins are a 2026 Claude Code addition that bundle skills + subagents + commands + hooks into a single distributable package. The course currently teaches each piece individually but never closes the "how do I ship this config across teams" loop. This is a natural Chapter 13 capstone after the playbook chapter, and it's the single biggest gap surfaced by the course-level web search.
  - Topics:
    - What a plugin is and how it differs from a loose collection of files
    - Plugin anatomy: directory structure, manifest, install script
    - Packaging a shared `.claude/rules/` set as a plugin
    - Packaging a shared `.claude/skills/` library as a plugin
    - Packaging hooks alongside skills and rules
    - Versioning plugins and rolling out updates across teams
    - Distributing internally (private repo) vs publicly (open-source plugins)
    - Security review of third-party plugins before installing
    - Plugin vs MCP server: when each is the right answer
    - Case study: packaging the recipes app's full AI-ready config as one plugin
  - Sources consulted: https://code.claude.com/docs/en/skills (2026-04-30), https://github.com/hesreallyhim/awesome-claude-code (2026-04-30)
  - Suggested filename: 13-plugins-distribution.html
  - Status: candidate — promote to active if the user wants the course to expand to 13 chapters; leave parked otherwise.

## Do-not-touch

- 05-hooks-guardrails.html — no `.ctx` references, no skills-vs-commands path issues; the v2.1.69 reference at line 154 is a mild version-marker but not misleading. Hook lifecycle, PreToolUse / PostToolUse / SubagentStop semantics, and the starter-kit content are all current.

## Sources consulted (master list)
- https://code.claude.com/docs/en/skills (2026-04-30) — current shape of skills, `.claude/skills/<name>/SKILL.md`, frontmatter behavior
- https://code.claude.com/docs/en/slash-commands (2026-04-30) — slash command and skill unification, `.claude/commands/` legacy compat
- https://code.claude.com/docs/en/memory (2026-04-30) — `.claude/rules/` directory and CLAUDE.md hierarchy
- https://code.claude.com/docs/en/sub-agents (2026-04-30) — subagent semantics referenced in Ch 9
- https://platform.claude.com/docs/en/build-with-claude/prompt-caching (2026-04-30) — 5-min and 1-hour TTL options, write/read multipliers
- https://platform.claude.com/docs/en/about-claude/pricing (2026-04-30) — current Opus 4.6 / Sonnet 4.6 / Haiku 4.5 pricing
- https://github.com/anthropics/claude-code/issues/13905 (2026-04-30) — `paths:` frontmatter YAML bug
- https://github.com/anthropics/claude-code/issues/17204 (2026-04-30) — `paths:` vs `globs:` documentation gap
- https://github.com/anthropics/claude-code/issues/16299 (2026-04-30) — path-scoped rules sometimes load globally
- https://github.com/anthropics/claude-code/issues/23478 (2026-04-30) — rules load on Read but not on Write
- https://github.com/hesreallyhim/awesome-claude-code (2026-04-30) — plugin ecosystem overview
