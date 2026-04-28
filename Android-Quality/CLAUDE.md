# The Android Quality Stack For Dummies

## Project Description
An HTML course for **experienced Android developers** who never invested in quality tooling — detekt, Android lint, ktlint, StrictMode, LeakCanary, version catalogs, R8, convention plugins — because the answer was always "no time, ship the feature." This course is the path back: how to bolt a complete quality stack onto an existing Android project **without grinding feature work to a halt**.

The reader has shipped real apps. They've debugged real crashes. They are not new to Kotlin or Gradle. What they're missing is the **governance layer** — the static analysis, runtime safety nets, and build-time foundations that turn a working codebase into a maintainable one.

The style is **"For Dummies"** — friendly, anti-bikeshedding, pragmatic, like a senior Android dev showing you what you've been missing over coffee. Heavy on real `gradle.kts` snippets, real `lint.xml` configs, real baseline files, real `proguard-rules.pro` examples.

**Light AI thread.** Every chapter has a short "AI-Assisted Setup" tip — using Claude Code to draft a detekt config from your existing codebase, triage a 10,000-warning lint baseline, generate ProGuard keep rules from a release-only stack trace, write a custom detekt rule from a description. The tooling is the main act; AI is the speed-up.

## Language Rules
- All content is in **English**
- Tone: friendly, conversational, like a colleague who's seen every kind of "we don't have time for that" excuse
- Address: second person singular (you)
- Frame every tool as **leverage, not tax** — what does adopting it let you stop doing manually?
- Always show the *adoption ladder*: Day 1 (turn it on, baseline existing), Week 1 (tune severities, IDE integration), Month 1 (CI gate, custom rules)
- When introducing a tool, always show: *what it catches that humans miss* → *the install* → *the config* → *the rollout strategy*
- Light humor is welcome — quality tooling has a reputation for being boring; lean into making it not so
- Use short paragraphs — walls of text kill understanding
- AI tool references: Claude Code is the default. It's fine to say "ask Claude" or "your AI of choice" but lean toward Claude Code for skill-building examples

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

## Content Generation Rules
- All generated chapters MUST meet the **400-line minimum on the FIRST attempt**. Draft the FULL content in one pass targeting ~10% above the minimum. Verify with `wc -l` before finalizing.
- If under the minimum, expand with substantive sections (real configs, deeper case studies, expanded adoption-ladder breakdowns) — not filler, not line-by-line padding.
- If you end up within 10–15% above the minimum, LEAVE IT ALONE. Do not trim to fit a tighter range. Only trim if you're significantly over (e.g., >25% above), and then cut whole sections, not individual lines.
- Never pad content incrementally — produce complete, full-length content in one pass.

## HTML Validation Rules
- Always close `<div>` elements with `</div>` — never invent tags like `</tip>`, `</note>`, `</card>`, or `</box>`. Closing tags must match opening tags exactly.
- After writing each chapter, grep for unmatched/custom closing tags before declaring done.
- Validate all HTML tags are properly closed before completing a chapter.

## Project Structure Rules
- Always check the current working directory and respect the explicit project path provided by the user. Do NOT search parent directories or sibling projects unless explicitly asked.

## Cross-Reference Rules
- When generating multi-file series, ensure all cross-reference links between chapters are consistent. Use relative paths and verify link targets exist before finishing.

## File Structure
```
Android-Quality/
  CLAUDE.md                                — This file
  .claude/
    commands/
      generate-next-chapter.md             — Skill for chapter generation
      create-memory-map.md                 — Skill for visual chapter summaries
  chapters/
    index.html                             — Landing page with navigation
    assets/
      style.css                            — Shared CSS with dark/light theme
    01-why-you-keep-putting-this-off.html  — Reframing quality as leverage
    02-auditing-and-baselining.html        — The honest baseline + freeze the past
    03-android-lint.html                   — Built-in Android lint, properly configured
    04-detekt-and-konsist.html             — Detekt + Konsist for Kotlin
    05-ktlint-and-spotless.html            — Formatting without religious wars
    06-pre-commit-and-local-loop.html      — Pre-commit hooks & local dev loop
    07-strictmode.html                     — StrictMode runtime checks
    08-leakcanary.html                     — LeakCanary memory leak detection
    09-debug-build-inspectors.html         — Chucker, debug menus, debug-only flags
    10-version-catalogs-and-deps.html      — Version catalogs & dependency health
    11-r8-minification.html                — R8 minification & keep rules
    12-convention-plugins-and-ci-gate.html — Convention plugins & CI quality gate
    maps/                                  — Visual memory maps (generated on demand)
```

## Progress Tracking
- [x] Chapter 1: Why You Keep Putting This Off (And How to Stop)
- [x] Chapter 2: Auditing Your Project + Baselining Existing Sins
- [x] Chapter 3: Android Lint, Properly Configured
- [x] Chapter 4: Detekt + Konsist: Kotlin Smells & Architecture Rules
- [x] Chapter 5: Ktlint & Spotless: One-Click Formatting
- [x] Chapter 6: Pre-commit Hooks & The Local Dev Loop
- [x] Chapter 7: StrictMode: Find Bugs Before Your Users Do
- [x] Chapter 8: LeakCanary: Memory Leaks Made Visible
- [x] Chapter 9: Debug-Build Inspectors
- [x] Chapter 10: Version Catalogs & Dependency Health
- [x] Chapter 11: R8: Minification Without Mysteries
- [x] Chapter 12: Convention Plugins & The CI Quality Gate

## Instructions for /generate-next-chapter
When the user invokes `/generate-next-chapter`:
1. Read this CLAUDE.md and find the first chapter marked with `[ ]` in Progress Tracking
2. Read the "Chapter Details" section below for that chapter's topics
3. Read `chapters/assets/style.css` for available CSS classes
4. Read `chapters/index.html` for navigation template
5. Read the previous chapter (if any) for context and smooth transition
6. Generate the HTML file in `chapters/` with full content (400-600 lines)
7. Update CLAUDE.md — mark the chapter as `[x]`
8. Update `chapters/index.html` — remove `pending` class from that chapter's card
9. Update navigation on the previous chapter if needed

## CSS Classes for Content

### Custom classes (unique to this course)
- `.tool-profile-box` — "Meet the Tool" spec sheet at the top of every tool chapter: name, what it catches that humans miss, install snippet, runtime cost, when to skip it. Forest-green accent.
- `.config-recipe` — Drop-in config block (Gradle Kotlin DSL, XML, YAML) annotated with "what this line does" callouts. The course is config-heavy; this is the workhorse.
- `.adoption-ladder` — Staged rollout box with three rungs: Day 1 / Week 1 / Month 1. Reinforces "don't grind dev to a halt." Use this once per tool chapter.

### Shared classes
- `.tip-box` — tips and advice
- `.warning-box` — warnings and cautions
- `.prompt-example.good` / `.prompt-example.bad` — Claude Code prompts shown as good/bad
- `.comparison` — side-by-side comparisons
- `.checklist` — checklists with checkmarks
- `.highlight-box` — key messages (gradient background)
- `.stats-grid` + `.stat-card` — statistics display
- `.tool-card` — generic tool description card (icon + name + description)
- `.workflow-steps` + `.step` + `.step-arrow` — visual workflow pipeline
- `.exercise-box` — hands-on exercises (gold accent)
- `.chapter-card` + `.part-divider` — index page only

## Content Guidelines
- **At least one `.tool-profile-box`** per tool chapter (Ch 3-12). Foundation chapters (1-2) can skip it.
- **At least one `.config-recipe`** per chapter showing real, copy-pasteable Gradle/XML/YAML config. Annotate every non-trivial line.
- **At least one `.adoption-ladder`** per tool chapter showing the Day 1 / Week 1 / Month 1 rollout.
- **At least one `.exercise-box`** per chapter where the reader runs a tool against their own project.
- **At least one "AI-Assisted Setup" subsection** per chapter — a short Claude Code prompt or skill that speeds up the boring config work.
- Code examples must be **real**: Kotlin DSL Gradle (`build.gradle.kts`), `lint.xml`, `detekt.yml`, `proguard-rules.pro`, `libs.versions.toml`, `.editorconfig`, GitHub Actions YAML.
- Each chapter ends with a preview of how it connects to the next.
- Every chapter teaches at least one **reusable Claude Code skill** (`/command`) — e.g., `/triage-lint-baseline`, `/draft-detekt-config`, `/explain-r8-keeprule`.

## Chapter Details

### Chapter 1: Why You Keep Putting This Off (And How to Stop)
**File:** `01-why-you-keep-putting-this-off.html`
**Goal:** Reframe quality tooling as leverage rather than tax, and convince a tired-of-shipping-features Android dev that the next month of work will pay back forever.

**Topics:**
- The 5 lies you've told yourself: "we'll add it later," "we don't have time," "the team won't follow it," "our codebase is too messy now," "linters are nitpicky and slow"
- The actual cost of skipping the stack — concrete bug categories that lint, detekt, StrictMode, and LeakCanary catch automatically (NPEs from unchecked nullables, leaked Activities, NetworkOnMainThread, unread vars, dead code paths)
- What "the stack" means in this course — the four pillars (static analysis, runtime safety nets, build-time foundation, CI gate)
- The "no time" objection, dismantled — how each tool pays for itself in the first week (real before/after stories: PR-review time, debugging time, regressions caught)
- The adoption ladder framing — Day 1 / Week 1 / Month 1 — and why the *baseline file* is the secret to onboarding without a multi-month backfill
- The light AI thread preview — how Claude Code can draft your initial configs from your existing code, triage warning lists, and convert pain points into rules
- A short tour of the 12-chapter journey
- A self-assessment checklist: which of these does your project have? Which would have caught your last 3 production bugs?
- "Permission to start small" — adopting one tool at a time is fine, in fact recommended
- Setting the tone: this is *bolting on*, not greenfield. Your codebase is messy. That's fine.

### Chapter 2: Auditing Your Project + Baselining Existing Sins
**File:** `02-auditing-and-baselining.html`
**Goal:** Take an honest look at the current project state and introduce the *baseline file* concept — freeze the past so the future is clean.

**Topics:**
- The honest audit — what you can learn in 30 minutes with `./gradlew dependencies`, `./gradlew :app:lint`, and `./gradlew tasks --group verification`
- Reading the dependency tree — direct vs. transitive, version conflicts, unexpected pulls
- The three categories of "quality debt": **codebase debt** (lint/detekt findings), **dependency debt** (outdated, vulnerable, unused), **process debt** (no CI gates, no formatting standard)
- The baseline file concept — what it is, why it's the unlock for adoption on legacy code, what the baseline is *not* (it is not "we'll fix this later" — it's "new code is held to the standard")
- How baselines work in Android lint, detekt, and ktlint (pointer; deep dives in their chapters)
- Audit deliverables — a one-page report you produce in this chapter: top 10 lint categories, top 5 dependency risks, current process gaps
- AI-Assisted Audit: a `/audit-android-project` Claude Code skill that takes your `lint.xml`, `build.gradle.kts`, and root `build.gradle.kts` and produces a prioritized audit report
- Picking your starting point — which tool to adopt first based on your audit (heuristics: lots of nullables → detekt first; mystery crashes in release → R8 + StrictMode; team conflicts on PRs → ktlint first)
- "Don't fix it all" — the trap of the multi-week cleanup PR, and why incremental adoption beats it
- Setting up your tracking — a `quality-debt.md` doc (or GitHub Project) so you see progress
- Exercise: run the audit on your real project and produce your one-page report

### Chapter 3: Android Lint, Properly Configured
**File:** `03-android-lint.html`
**Goal:** Turn the built-in Android linter from a ignored noise channel into a high-signal first line of defense.

**Topics:**
- Meet Android Lint — what it catches that other tools don't (Android-specific issues: API level mismatches, manifest problems, accessibility, hardcoded strings, deprecated APIs, R8 incompatibilities)
- The default state — why `./gradlew lint` is usually ignored (output volume, severity defaults, no CI gate)
- Configuring `lint.xml` — issue-level severity, scope filters, regex paths, the `<issues>` element
- The `lintOptions` / `lint {}` block in `build.gradle.kts` — `abortOnError`, `warningsAsErrors`, `checkReleaseBuilds`, `disable`/`enable`, `htmlReport` and `xmlReport`
- The Lint baseline file — `lint-baseline.xml`, generating it, what to commit, when to regenerate
- Severity tuning strategy — `error` for showstoppers, `warning` for new code, `informational` for taste rules
- Categories worth promoting to error today — `NewApi`, `MissingPermission`, `InvalidPackage`, `HardcodedText`, `WrongConstant`
- Custom lint checks (light intro) — what they are, when worth writing one, the `lint.jar` registry pattern
- AI-Assisted Setup: a `/triage-lint-baseline` Claude Code skill that reads your `lint-baseline.xml` and groups findings by category, severity, and likely effort
- The CI hook — running `./gradlew :app:lintRelease` on PRs, treating new findings as blockers
- Adoption ladder: Day 1 baseline + critical-issue promotion → Week 1 IDE inspections + dev-mode warnings-as-errors → Month 1 CI gate + per-team severity ownership
- Exercise: generate a baseline on your project, promote 3 categories to error, file a PR

### Chapter 4: Detekt + Konsist: Kotlin Smells & Architecture Rules
**File:** `04-detekt-and-konsist.html`
**Goal:** Add a Kotlin-aware static analyzer (detekt) and a sidebar on enforcing architecture rules in code (Konsist).

**Topics:**
- Meet Detekt — what it catches that Android Lint doesn't (Kotlin idioms, complexity metrics, naming, exceptions handling, formatting violations not caught by ktlint)
- Installing detekt — the Gradle plugin, applied at the root project, `detekt {}` block configuration
- The `detekt.yml` config file — generating the default, the rule sets (style, complexity, exceptions, naming, performance, potential-bugs)
- Severity & build-failing — `failFast`, `buildUponDefaultConfig`, suppressions via `@Suppress`
- The detekt baseline — generating, when to use it, the legacy-code adoption pattern (same idea as Lint's baseline)
- Type-resolution mode — why detekt with type resolution catches more, and the cost of enabling it
- The most-valuable-by-default rules: `LongMethod`, `ComplexCondition`, `NestedBlockDepth`, `ReturnCount`, `MagicNumber`, `TooGenericExceptionCaught`, `SwallowedException`, `WildcardImport`
- Writing a custom detekt rule — the `Rule` class skeleton, AST visitors, when worth writing one
- AI-Assisted Setup: a `/draft-custom-detekt-rule` Claude Code skill — describe the smell in English, get a Kotlin Rule class skeleton back
- Konsist sidebar — what it is (architecture-as-code testing for Kotlin), how it complements detekt, sample assertions ("classes in `domain` must not import from `presentation`", "viewmodels must end with `ViewModel`")
- Konsist tests live in `src/test`, run with `./gradlew test`, fail fast on architecture drift
- Adoption ladder: Day 1 plugin install + baseline → Week 1 enable rule sets + IDE plugin → Month 1 custom rules + Konsist tests for top architecture invariants
- Exercise: install detekt, generate a baseline, enable type resolution, find the top 5 fixable findings

### Chapter 5: Ktlint & Spotless: One-Click Formatting
**File:** `05-ktlint-and-spotless.html`
**Goal:** Eliminate style debates from PRs by automating formatting at save-time, pre-commit, and CI.

**Topics:**
- The case against bikeshedding — why "tabs vs. spaces" arguments are a sign your team needs ktlint, not better arguments
- Meet ktlint — Kotlin's de-facto formatter, `.editorconfig`-driven, opinionated by design
- Installing ktlint — the standalone CLI, the Gradle plugin (jlleitschuh or pinterest), the IntelliJ plugin
- The `.editorconfig` file — what to set: `indent_size`, `max_line_length`, `ktlint_*` rule toggles, project-wide consistency
- The "format the whole repo once" PR — running `./gradlew ktlintFormat`, committing the diff in isolation, never looking back
- Meet Spotless — what it adds beyond ktlint (multi-language formatting: Kotlin, Java, XML, Gradle, license headers)
- The `spotless {}` block — `kotlin { ktlint("VERSION") }`, target globs, `licenseHeader`, `endWithNewline`, `trimTrailingWhitespace`
- IDE integration — Save Actions plugin (IntelliJ/Android Studio), settings to format-on-save, "reformat code on commit"
- The pre-commit hook angle — quickly previewed here, deeper in Chapter 6
- AI-Assisted Setup: a `/draft-editorconfig` Claude Code skill that takes your project's existing files and produces a sane `.editorconfig` matching current conventions
- The CI gate — `./gradlew ktlintCheck` (or `spotlessCheck`) on PRs, blocking unformatted code
- Adoption ladder: Day 1 install + one-shot format PR → Week 1 IDE format-on-save for everyone → Month 1 CI gate + custom rules disabled where annoying
- Exercise: install spotless with ktlint, run the format PR on a feature branch, measure the diff size

### Chapter 6: Pre-commit Hooks & The Local Dev Loop
**File:** `06-pre-commit-and-local-loop.html`
**Goal:** Move quality checks left — fire them before push, not after — so feedback comes in seconds, not in CI minutes.

**Topics:**
- The "left shift" mental model — every minute a check finds an issue earlier saves N minutes downstream (review time, CI time, context-switch cost)
- The dev loop ladder: IDE inspection → save action → pre-commit hook → pre-push hook → CI
- Native Git hooks — `.git/hooks/pre-commit`, the limits (per-clone, easy to skip, not in source control)
- Hook frameworks for Kotlin/Android: `pre-commit` (Python-based, popular), `lefthook` (fast, Go-based), `husky` (Node-based, common in mixed JS+Android repos)
- Recommended choice and tradeoffs — leans toward `lefthook` for Android-only projects (no Node/Python dep), `husky` if your repo already has a JS layer
- The `lefthook.yml` config — running `ktlintFormat` on staged files only (the `{staged_files}` token), running detekt-staged, blocking on lint failures
- "Format on commit" vs "format on save" — when each is right, the failure modes
- The pre-push hook — running `./gradlew :app:lintDebug detekt` before push to catch what local format-on-save misses
- Speeding up local checks — Gradle daemon, configuration cache, `--continuous`, only running affected modules
- IDE-side: enabling Android Studio's File Watchers, "Run inspections on commit," "Optimize imports on commit"
- AI-Assisted Setup: a `/draft-lefthook-config` Claude Code skill that produces a `lefthook.yml` tuned to your project's modules and tools
- The "what if a check is broken" override — `--no-verify` is a smell; better answer is fast, reliable hooks
- Adoption ladder: Day 1 install hook framework + one fast check (ktlint format) → Week 1 add detekt + lint to pre-push → Month 1 IDE-side standardized inspections per team
- Exercise: install lefthook in your project, configure ktlint pre-commit, measure local feedback time vs. CI time

### Chapter 7: StrictMode: Find Bugs Before Your Users Do
**File:** `07-strictmode.html`
**Goal:** Use StrictMode to surface main-thread offenses, leaked closeables, and accidental SQLite-on-main during development — when you can fix them.

**Topics:**
- Meet StrictMode — the runtime safety net Android shipped in 2010 that almost no app turns on
- ThreadPolicy violations — `detectDiskReads`, `detectDiskWrites`, `detectNetwork`, `detectCustomSlowCalls`, `detectResourceMismatches`
- VmPolicy violations — `detectLeakedClosableObjects`, `detectLeakedRegistrationObjects`, `detectActivityLeaks`, `detectFileUriExposure`, `detectCleartextNetwork`
- Where to enable it — in `Application.onCreate()`, gated on `BuildConfig.DEBUG`, never in release
- `penaltyLog()` vs `penaltyDeath()` vs `penaltyDropBox()` — which to use during dev, which to use in CI integration tests
- Reading the violation output — interpreting the stack trace, finding the actual offender (usually 5-10 frames deep)
- The "untrip-strictmode-then-restore" anti-pattern — why teams disable it after a bad week, and the right answer (suppress specific violations, fix the others)
- `StrictMode.allowThreadDiskReads { ... }` — the legitimate-suppression pattern, when it's correct
- Common offenders in Android codebases: `SharedPreferences.commit()` on main, synchronous `Room` queries, `getSharedPreferences()` cold start, large `BitmapFactory.decodeResource()` on main, eager DB migration on app start
- Building a `/explain-strictmode-violation` skill — paste the StrictMode log, get a plain-English explanation of which call is offending and why
- StrictMode in instrumented tests — how to fail tests on violations, the JUnit rule pattern
- Adoption ladder: Day 1 enable with `penaltyLog` + read the first 10 violations → Week 1 fix the top 5, suppress the rest with `allowThreadDiskReads` → Month 1 `penaltyDeath` in dev, JUnit rule in CI tests
- Exercise: enable StrictMode in your debug build, run the app for 5 minutes of normal usage, paste the violation log into Claude Code for triage

### Chapter 8: LeakCanary: Memory Leaks Made Visible
**File:** `08-leakcanary.html`
**Goal:** Install LeakCanary, hook it into your debug builds, and learn to read its trace output to find leaks before they become OOMs.

**Topics:**
- Meet LeakCanary — Square's heap-watcher that automatically detects leaked Activities, Fragments, and Views, captures a heap snapshot, and tells you exactly which reference is keeping the leak alive
- The two-line install — `debugImplementation("com.squareup.leakcanary:leakcanary-android:VERSION")` and you're done
- How LeakCanary works (high level) — `ObjectWatcher`, the 5-second window, the heap analyzer, the leak trace
- Reading a leak trace — GC roots, retention chain, where the *real* fix is (almost never the immediately-printed line)
- The classic Android leaks: static field holding Activity, inner class with implicit outer reference, ViewModel outliving Activity, unregistered listeners, Handler with delayed message, Bitmap held in static cache, `LiveData` observers without `LifecycleOwner`
- Fragment + ViewBinding leaks — the canonical `_binding = null` in `onDestroyView` pattern and how to enforce it via detekt or Konsist
- Compose-era considerations — `remember` lifecycle, `LaunchedEffect`, `rememberCoroutineScope`, why Compose generally leaks less but isn't immune
- Suppressing known leaks — `LeakCanary.config = config.copy(referenceMatchers = ...)`, when it's appropriate (3rd-party SDK leaks)
- The CI angle — running LeakCanary in instrumented tests, failing on any leak, the GitHub Action setup
- AI-Assisted Setup: a `/explain-leak-trace` skill — paste the LeakCanary report, get a 1-paragraph explanation + the smallest fix
- Common false-positive patterns — what to genuinely ignore vs. what looks ignorable but isn't
- Adoption ladder: Day 1 install in `debugImplementation` → Week 1 fix the top 3 leaks LeakCanary surfaces → Month 1 add to instrumented tests, fail CI on new leaks
- Exercise: install LeakCanary, navigate around your app for 10 minutes, fix the first leak it surfaces

### Chapter 9: Debug-Build Inspectors
**File:** `09-debug-build-inspectors.html`
**Goal:** Add three more debug-only safety nets — a network inspector (Chucker), a debug menu pattern, and debug-only feature flags — without polluting release builds.

**Topics:**
- The "debug-only kit" — a curated set of dependencies that ship to engineers but never users, gated via `debugImplementation`
- Meet Chucker — Square's in-app HTTP inspector, an OkHttp interceptor that records requests/responses and surfaces them in a notification + in-app screen
- Installing Chucker — `debugImplementation`, plugging the interceptor into your `OkHttpClient`, redacting sensitive headers
- Reading Chucker output — request/response pairs, body size, timing, retries, errors at a glance during development
- The debug menu pattern — a hidden screen reachable from a debug-only entry point (long-press logo, gesture, settings link), gated on `BuildConfig.DEBUG`
- What goes in your debug menu: build info (version, commit, build type), feature flag overrides, force-crash button, force-ANR button, log export, navigate-to-screen jumps, "clear app data" shortcut
- Debug-only feature flags — overriding remote-config values locally for testing, a `DebugFeatureFlagRepository` that wraps the prod one
- Build-variant gating — `buildTypes { debug { } }`, `productFlavors`, why `debugImplementation` is your friend, how to keep release lean
- The release-build verification — checking your release APK/AAB doesn't include any debug-only code (apkanalyzer, sanity grep)
- Other inspectors worth knowing about (brief mentions, not deep dives) — Flipper alternatives, Rebugger for Compose recomposition, Beagle for in-app debugging UI
- AI-Assisted Setup: a `/draft-debug-menu` skill — describe what you want in your debug menu, get a Compose `DebugMenuScreen` skeleton
- Adoption ladder: Day 1 add Chucker + verify it doesn't ship in release → Week 1 build a minimal debug menu with build info + feature-flag overrides → Month 1 expand the debug menu based on team requests
- Exercise: install Chucker, navigate the app, verify Chucker is absent from a release build, add a "build info" screen to your debug menu

### Chapter 10: Version Catalogs & Dependency Health
**File:** `10-version-catalogs-and-deps.html`
**Goal:** Switch to Gradle version catalogs (the modern way to manage dependencies) and add tooling that flags unused, outdated, and risky dependencies.

**Topics:**
- The dependency mess — what your `build.gradle.kts` looks like before catalogs, why it's hard to maintain (drift across modules, version conflicts, "where is this library used?")
- Meet Gradle version catalogs — the `libs.versions.toml` file, `[versions]`, `[libraries]`, `[plugins]`, `[bundles]`
- Migrating to a catalog — picking the right granularity, naming conventions (`androidx-core-ktx` vs `core`), bundles for grouped deps (`networking` = retrofit + okhttp + moshi)
- The mechanical migration — going module by module, AI-assisted bulk replacement
- Meet `dependency-analysis-gradle-plugin` — finds unused dependencies, misused implementation/api, transitive deps you should declare directly
- Running it — `./gradlew buildHealth`, reading the output, the kinds of findings (unused, redundant, etc.)
- Meet `ben-manes/versions` plugin — finds outdated dependencies, the `dependencyUpdates` task, filtering pre-release/snapshot
- The vulnerability layer (light) — pointing at OWASP Dependency-Check or Snyk for CVE scanning, why it matters even for inner deps
- Renovate / Dependabot for automated PRs — the basic config, the "weekly batch update" pattern
- AI-Assisted Setup: a `/migrate-to-version-catalog` skill — given your existing `build.gradle.kts` files, produce a `libs.versions.toml` and the corresponding module updates
- The catalog vs. composite-build vs. plugin-publishing tradeoff (light) — why catalogs win for most teams
- Adoption ladder: Day 1 create `libs.versions.toml` and migrate one module → Week 1 finish all modules + add `buildHealth` task → Month 1 add `versionsUpdate` to a weekly cron + Renovate config
- Exercise: migrate your largest module to the version catalog, run `buildHealth`, file a PR removing the top 3 unused deps

### Chapter 11: R8: Minification Without Mysteries
**File:** `11-r8-minification.html`
**Goal:** Demystify R8/ProGuard so release builds are smaller, faster, and don't crash with `ClassNotFoundException` or `NoSuchMethodError`.

**Topics:**
- Meet R8 — the bundled minifier in Android Gradle Plugin, what it does (shrink, optimize, obfuscate, deobfuscate)
- Why R8 exists — APK size, startup time, attack surface (obfuscation as a mild deterrent, not security)
- Enabling R8 — `minifyEnabled = true`, `shrinkResources = true`, `proguardFiles`, the default `proguard-android-optimize.txt`
- The keep-rule mental model — R8 strips everything not reachable from your manifest. Anything reflected, JNI'd, or named-by-string needs a keep rule
- Common keep-rule patterns — Gson/Moshi DTOs, Retrofit interfaces, Hilt modules, ViewBinding generated classes, custom views referenced from XML, JNI methods
- Reading a release-only crash — the obfuscated stack trace, the `mapping.txt` file, retracing with `retrace.jar` or Android Studio
- The `mapping.txt` golden rule — commit it (or upload to Crashlytics) for *every* release, or your stack traces are useless
- The "rules from libraries" angle — most libraries ship `consumer-proguard-rules.pro`; what to do when a library *doesn't* and you crash on `ProcessReleaseResources`
- Optimizing past the defaults — `-allowaccessmodification`, `-repackageclasses`, fullMode in newer AGPs, what's safe and what isn't
- The "I'll just disable minification" anti-pattern — why your APK gets 30% bigger and your competitive advantage shrinks
- Baseline Profiles teaser — the *startup* equivalent of minification, briefly introduced as the next-level optimization
- AI-Assisted Setup: a `/draft-keep-rules` skill — paste a release-only stack trace, get the precise `-keep` rules to add
- Adoption ladder: Day 1 enable minification in a release-debug build → Week 1 fix all crashes, ship release → Month 1 add Crashlytics symbol upload + verify mapping for every release
- Exercise: turn on minification on a feature branch, fix the first 3 release-only failures, paste any remaining stack traces into Claude Code

### Chapter 12: Convention Plugins & The CI Quality Gate
**File:** `12-convention-plugins-and-ci-gate.html`
**Goal:** Package the entire stack (lint + detekt + ktlint + tests + StrictMode setup) into one convention plugin so every module gets it for free, then wire it into a PR-blocking CI gate.

**Topics:**
- The "copy-paste Gradle config across modules" problem — what your repo looks like before convention plugins (each module has its own `lint {}`, `detekt {}`, applied plugins)
- Meet convention plugins — Gradle's built-in mechanism for sharing build logic via `buildSrc/` or an included build (`build-logic/`)
- The `build-logic/` setup — included build with `kotlin-dsl`, `gradlePlugin { plugins { ... } }`, registering plugin IDs (`my.app.android.application`, `my.app.android.library`)
- Writing your first convention plugin — `AndroidApplicationConventionPlugin.kt`, applying common plugins, configuring `lint {}`, `detekt {}`, `kotlinOptions { ... }`
- The "stack" plugin — one plugin (`my.app.quality`) that applies lint config, detekt config, ktlint, and the StrictMode `Application` snippet generation
- Sharing config files — keeping `detekt.yml`, `lint.xml`, `lint-baseline.xml` per-module vs. shared vs. inherited; the right boundaries
- Per-module overrides — when a module legitimately needs a different rule set, how to express it cleanly
- Meet GitHub Actions for Android — `setup-java`, the AGP cache action, the gradle wrapper, the `actions/cache` for `~/.gradle`
- The CI quality gate — the matrix of jobs you want: `lint`, `detekt`, `ktlintCheck`, `test`, `buildHealth`. Failing the merge on any of them.
- The "danger" / PR comment angle — bot comments on PRs surfacing lint findings inline (Reviewdog, Danger, custom GH Action)
- Branch protection rules — making the gate enforced, not advisory; the org-level "require status checks" toggle
- AI-Assisted Setup: a `/draft-quality-convention-plugin` skill — given your existing module configs, produce a convention plugin that consolidates them
- The 30-day rollout — week 1 convention plugin in `build-logic`, week 2 migrate modules, week 3 add CI gate, week 4 enforce branch protection
- The closing message: you went from "no time for quality" to "every PR runs the full stack." This compounds. Forever.
- Exercise: stand up a `build-logic/` included build, write the `AndroidApplicationConventionPlugin`, migrate one module, add a GitHub Actions workflow that runs lint + detekt
