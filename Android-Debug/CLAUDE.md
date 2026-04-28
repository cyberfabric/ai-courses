# AI-Driven Debugging & Performance for Android

## Project Description
An HTML course for Android developers who want to use AI to debug faster and optimize performance. The reader already uses Claude Code for coding but hasn't applied it systematically to debugging — crash analysis, profiling, memory leaks, ANRs, Compose performance, build times, and production monitoring.

**Tool focus: Claude Code only.** This course never references Windsurf, Codex, Cursor, Copilot, or any other AI coding tool. Every example, skill, and exercise uses Claude Code exclusively.

The style is **"For Dummies"** — friendly, approachable, like a senior Android dev showing you debugging tricks over coffee. Heavy on practical examples with real stacktraces, profiler output, and hands-on exercises.

## Language Rules
- All content is in **English**
- Tone: friendly, conversational, like a colleague who's seen every crash pattern
- Use real Android debugging scenarios (actual crash patterns, real profiler output, genuine Gradle issues)
- Address: second person singular (you)
- When introducing a debugging technique, always show: "Here's the raw output" → "Here's what AI finds" → "Here's the fix"
- Light humor is welcome — debugging is painful enough without dry writing
- Use short paragraphs — walls of text kill understanding
- **NEVER mention Windsurf, Codex, Cursor, Copilot, or any other AI coding tool** — Claude Code only

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
Android-Debug/
  CLAUDE.md                                — This file
  .claude/
    commands/
      generate-next-chapter.md             — Skill for chapter generation
  chapters/
    index.html                             — Landing page with navigation
    assets/
      style.css                            — Shared CSS with dark/light theme
    01-ai-debugger-mindset.html            — The AI-Powered Debugger Mindset
    02-crash-logs-logcat.html              — Crash Logs, Logcat & Stacktraces
    03-anr-diagnosis.html                  — ANR Diagnosis and Prevention
    04-memory-leaks.html                   — Memory Leak Detection with AI
    05-compose-recomposition.html          — Compose Recomposition Performance
    06-network-debugging.html              — Network Debugging with AI
    07-gradle-build-performance.html       — Gradle Build Performance
    08-battery-power.html                  — Battery and Power Optimization
    09-ai-assisted-profiling.html          — AI-Assisted Profiling
    10-flaky-tests.html                    — Flaky Test Diagnosis
    11-production-monitoring.html          — Production Monitoring & Crash Reporting
    12-performance-playbook.html           — Performance Budgets and Your Debugging Playbook
    13-16kb-page-size.html                 — Debugging 16 KB Page Size Compatibility for Native Libraries
    14-modern-background-restrictions.html — Debugging Background-Work Restrictions on Modern Android (15 / 16)
```

## Progress Tracking
- [x] Chapter 1: The AI-Powered Debugger Mindset
- [x] Chapter 2: Crash Logs, Logcat & Stacktraces
- [x] Chapter 3: ANR Diagnosis and Prevention
- [x] Chapter 4: Memory Leak Detection with AI
- [x] Chapter 5: Compose Recomposition Performance
- [x] Chapter 6: Network Debugging with AI
- [x] Chapter 7: Gradle Build Performance
- [x] Chapter 8: Battery and Power Optimization
- [x] Chapter 9: AI-Assisted Profiling
- [x] Chapter 10: Flaky Test Diagnosis
- [x] Chapter 11: Production Monitoring & Crash Reporting
- [x] Chapter 12: Performance Budgets and Your Debugging Playbook
- [x] Chapter 13: Debugging 16 KB Page Size Compatibility for Native Libraries
- [x] Chapter 14: Debugging Background-Work Restrictions on Modern Android (15 / 16)

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
- `.debug-trace` — stacktrace, logcat output, or profiler data with AI analysis (crimson accent, unique to this course)
- `.performance-metric` — before/after performance metrics with `.metric-before` and `.metric-after` children (unique to this course)
- `.root-cause` — root cause analysis finding (unique to this course)
- `.fix-pattern` — common fix pattern or solution (green accent, unique to this course)
- `.prompt-example.good` — good examples (green accent)
- `.prompt-example.bad` — bad examples (red accent)
- `.comparison` — side-by-side comparisons
- `.tip-box` — tips and advice
- `.warning-box` — warnings and cautions
- `.exercise-box` — hands-on exercises (gold accent)
- `.checklist` — checklists with checkmarks
- `.highlight-box` — key messages (gradient background)
- `.stats-grid` + `.stat-card` — statistics display
- `.tool-card` — tool description cards (icon + name + description)
- `.workflow-steps` + `.step` + `.step-arrow` — visual workflow pipeline
- `.theme-toggle` — theme switch button (in nav)

## Content Guidelines
- **At least one `.debug-trace`** per chapter with a stacktrace, log output, or profiler data with AI analysis
- **At least one `.root-cause`** per chapter with a root cause analysis finding
- **At least one `.fix-pattern`** per chapter showing a common fix pattern or solution
- **At least one `.performance-metric`** per chapter (where applicable) showing before/after metrics
- **At least one `.exercise-box`** per chapter where the reader debugs or profiles something real
- **All examples use Claude Code** — never reference other AI coding tools
- Keep code examples practical and real (Kotlin, logcat, stacktraces, Gradle config, profiler data)
- Each chapter should end with a preview of how it connects to the next chapter
- Every chapter should teach the reader to build at least one reusable Claude Code skill (/command)

## Chapter Details

### Chapter 1: The AI-Powered Debugger Mindset
**File:** `01-ai-debugger-mindset.html`
**Goal:** Shift the reader from "stare at logs and guess" to a systematic AI-assisted debugging methodology.

**Topics:**
- Why debugging is still the biggest time sink for Android devs — real numbers and developer surveys
- The traditional debugging cycle vs. the AI-augmented cycle (observe → hypothesize with AI → verify → fix)
- How AI reads stacktraces differently than you do — pattern matching across millions of known issues
- Setting up Claude Code for Android debugging — CLAUDE.md rules, project context, relevant file patterns
- Your first AI-assisted debug session: feeding a NullPointerException stacktrace to Claude Code
- Building a `/debug` skill — a reusable command that takes a stacktrace and returns structured analysis
- The "5 Whys" technique with AI — using follow-up prompts to drill past symptoms to root causes
- When AI is wrong — recognizing hallucinated fixes and validating AI suggestions before applying them
- The debugging journal — using Claude Code to maintain a log of bugs, root causes, and fixes

### Chapter 2: Crash Logs, Logcat & Stacktraces
**File:** `02-crash-logs-logcat.html`
**Goal:** Master the art of feeding Android-specific log output to AI and getting actionable analysis back.

**Topics:**
- Anatomy of an Android stacktrace — what each part means and what AI needs to see
- Logcat output: filtering the noise — using `adb logcat` flags to capture what matters
- Reading FATAL EXCEPTION blocks with AI — multi-cause crashes, chained exceptions, Caused by chains
- Proguard/R8 obfuscated stacktraces — deobfuscating first, then AI analysis (mapping files, retrace tool)
- Building an `/analyze-crash` skill that takes raw logcat output and returns: crash type, affected component, likely root cause, and suggested fix
- Multi-device crashes — using AI to compare stacktraces across different API levels and manufacturers
- Third-party library crashes — when the stacktrace points into OkHttp, Retrofit, Room, or Compose internals
- Common crash patterns AI recognizes instantly: IllegalStateException on fragments, BadTokenException, DeadObjectException
- Exercise: capture a real crash, paste the full logcat into Claude Code, walk through the AI analysis

### Chapter 3: ANR Diagnosis and Prevention
**File:** `03-anr-diagnosis.html`
**Goal:** Use AI to diagnose Application Not Responding errors — among the hardest Android bugs to troubleshoot.

**Topics:**
- What ANRs are and why they're worse than crashes — UX impact, Play Store vitals penalty
- The 5-second rule: main thread blocking, broadcast timeouts, service timeouts
- Reading ANR traces (`/data/anr/traces.txt`) — the format, what to look for, how AI parses them
- Building an `/analyze-anr` skill that identifies: blocked thread, lock holder, call chain, and suggested fix
- Common ANR patterns: database on main thread, synchronous network calls, heavy SharedPreferences commits
- Using AI to trace the call chain from the blocked method back to your code
- StrictMode as an ANR prevention tool — setup, reading its output, having AI analyze violations
- Coroutine dispatcher misuse — Dispatchers.Main where Dispatchers.IO should be, and how AI spots this
- Building a `/check-anr-risks` skill that scans code for common main-thread violations
- Exercise: introduce a deliberate Thread.sleep(6000) in onCreate, capture the ANR trace, use Claude Code to diagnose

### Chapter 4: Memory Leak Detection with AI
**File:** `04-memory-leaks.html`
**Goal:** Combine LeakCanary output and heap dump analysis with AI to find and fix memory leaks systematically.

**Topics:**
- Why memory leaks matter on Android — OOM crashes, janky UI, background kill priority
- LeakCanary 101 — setup, how it works, the leak trace format
- Feeding LeakCanary output to Claude Code — the leak trace is structured data that AI analyzes excellently
- Building an `/analyze-leak` skill that returns: leaking object, GC root, retention chain explanation, and fix options
- The classic Android memory leaks: Activity reference in static field, inner class holding Activity context, ViewModel outliving Activity, unregistered listeners
- AI-assisted heap dump analysis — exporting .hprof from Android Studio, key metrics to extract
- Fragment and ViewBinding leaks — the onDestroyView cleanup pattern and how AI audits for missing cleanup
- Compose-era memory considerations — `remember` vs `rememberSaveable`, LaunchedEffect scope leaks
- Building a `/scan-for-leaks` skill that reviews your codebase for known leak patterns
- Exercise: create a deliberate leak, run LeakCanary, use Claude Code to analyze and fix it

### Chapter 5: Compose Recomposition Performance
**File:** `05-compose-recomposition.html`
**Goal:** Diagnose and fix Jetpack Compose performance issues using AI to analyze recomposition counts and layout overhead.

**Topics:**
- The recomposition mental model — what triggers recomposition, why excessive recomposition kills performance
- Enabling recomposition counting in Android Studio (Layout Inspector) and reading the output
- Feeding recomposition metrics to Claude Code — "This composable recomposes 47 times during a scroll"
- Common recomposition traps AI catches: unstable parameters, lambda allocations, missing `remember`, reading state in wrong scope
- The stability system — `@Stable`, `@Immutable`, Compose compiler reports, and how AI interprets stability warnings
- Building an `/analyze-recomposition` skill that identifies the cause and suggests a fix
- `derivedStateOf`, `snapshotFlow`, `rememberUpdatedState` — when and why to use each
- Lazy list performance — LazyColumn/LazyRow pitfalls: missing key, heavy item composables, nested scrolling
- Baseline Profiles and Compose — generating baseline profiles, measuring startup improvement
- Exercise: build a deliberately inefficient Compose screen, measure recomposition, use Claude Code to optimize

### Chapter 6: Network Debugging with AI
**File:** `06-network-debugging.html`
**Goal:** Use AI to diagnose network-layer issues in OkHttp/Retrofit-based Android apps.

**Topics:**
- The network debugging challenge on Android — SSL, timeouts, retries, serialization, threading
- OkHttp interceptor logging — setting up HttpLoggingInterceptor, capturing request/response pairs
- Feeding HTTP logs to Claude Code — headers, response codes, timing, body content for analysis
- Building an `/analyze-network` skill that identifies: failed requests, slow responses, unnecessary calls
- Retrofit error handling patterns — AI reviewing Response<T> handling, sealed class error models
- SSL/TLS debugging — certificate pinning failures, SSLHandshakeException analysis with AI
- Timeout and retry strategies — AI analyzing OkHttp client configuration and suggesting optimal values
- Caching strategy review — AI auditing Cache-Control headers and OkHttp cache configuration
- API call deduplication — AI scanning for duplicate or redundant API calls
- Exercise: capture a failing API flow, paste interceptor logs into Claude Code, get step-by-step diagnosis

### Chapter 7: Gradle Build Performance
**File:** `07-gradle-build-performance.html`
**Goal:** Use AI to analyze Gradle build scans and optimize build times for Android projects.

**Topics:**
- Why build speed matters — developer flow state, CI costs, iteration speed
- Capturing build data — `--scan`, `--profile`, build-scan plugin, the reports Gradle generates
- Feeding a Gradle build scan summary to Claude Code — task times, configuration phase duration, cache hit rates
- Building an `/analyze-build` skill that identifies slowest tasks, cache misses, and configuration bottlenecks
- Common Android build killers: kapt vs KSP, unnecessary `implementation` vs `api`, disabled build cache
- Kapt to KSP migration — AI analyzing annotation processor setup and generating a migration plan
- Dependency analysis with AI — unused dependencies, version conflicts, unnecessary transitive pulls
- Modularization for build speed — AI suggesting module boundaries based on dependency graph
- CI-specific optimizations — remote build cache, parallel execution, Gradle daemon configuration
- Exercise: run `./gradlew assembleDebug --profile`, feed the report to Claude Code, implement top 3 recommendations

### Chapter 8: Battery and Power Optimization
**File:** `08-battery-power.html`
**Goal:** Use AI to identify and fix battery-draining behaviors in your Android app.

**Topics:**
- Why battery optimization is a platform requirement — Doze mode, App Standby Buckets, restricted background
- Battery Historian — capturing a bug report, running Battery Historian, reading the output
- Feeding Battery Historian data to Claude Code — wake locks, alarms, job schedules, network timelines
- Building an `/analyze-battery` skill that identifies excessive wake locks, inefficient scheduling, background abuse
- WakeLock audit with AI — scanning codebase for PowerManager.WakeLock usage, checking acquire/release patterns
- WorkManager vs AlarmManager vs JobScheduler — AI recommending the right API for each use case
- Location services battery drain — AI reviewing LocationRequest parameters and suggesting optimal settings
- Foreground service audit — when you need a foreground service vs when WorkManager suffices
- Network batching and prefetching strategies — AI reviewing network patterns and suggesting batching
- Exercise: capture a bug report after 30 min of app usage, extract battery stats, use Claude Code to find top 3 drains

### Chapter 9: AI-Assisted Profiling
**File:** `09-ai-assisted-profiling.html`
**Goal:** Learn to extract profiler data from Android Studio and use AI to interpret CPU, memory, and network traces.

**Topics:**
- The profiler data gap — Android Studio shows graphs, AI explains what they mean
- CPU profiling — capturing a method trace, exporting trace data, feeding hot methods to Claude Code
- Building a `/profile-cpu` skill that takes hot methods with call counts and durations, identifies bottlenecks
- Memory profiling — heap dump snapshots, allocation tracking, feeding allocation summaries to AI
- Identifying allocation-heavy code paths — AI reviewing methods that allocate excessively during scroll/animation
- Network profiling — timeline of requests, payload sizes, connection reuse, AI spotting inefficiencies
- System Trace (Perfetto) analysis — capturing a system trace, extracting key events, AI interpreting the timeline
- Frame rendering analysis — identifying janky frames, dropped frames during transitions, AI pinpointing causes
- Combining profiler data with code context — feeding both profiler output AND source code for a complete picture
- Exercise: profile a screen transition, export the CPU trace, use Claude Code to explain the 3 most expensive calls

### Chapter 10: Flaky Test Diagnosis
**File:** `10-flaky-tests.html`
**Goal:** Use AI to systematically diagnose and fix tests that pass sometimes and fail other times.

**Topics:**
- Why flaky tests erode trust — the "retry and ignore" culture and its cost
- Categorizing flaky tests: timing-dependent, order-dependent, environment-dependent, resource-dependent
- Feeding test failure logs to Claude Code — test name, assertion failure, stacktrace, recent code changes
- Building a `/diagnose-flaky` skill that returns: flakiness category, likely root cause, fix strategy
- Timing flakiness in Android — `runBlocking` vs `runTest`, `advanceUntilIdle`, coroutine test dispatchers
- Compose UI test flakiness — `waitForIdle`, `waitUntil`, synchronization with animations
- Espresso test flakiness — IdlingResource missing or misconfigured, AI auditing synchronization gaps
- Shared mutable state between tests — AI scanning test classes for static state, shared databases, missing cleanup
- CI environment differences — tests passing locally but failing on CI due to emulator speed, timezone, locale
- Exercise: take your team's most notorious flaky test, collect failure logs, use Claude Code to find the root cause

### Chapter 11: Production Monitoring & Crash Reporting
**File:** `11-production-monitoring.html`
**Goal:** Use AI to analyze Firebase Crashlytics reports and production monitoring data to prioritize and fix production issues.

**Topics:**
- The production debugging challenge — no debugger, only telemetry
- Firebase Crashlytics overview — crash clusters, non-fatal exceptions, breadcrumbs, custom keys
- Feeding Crashlytics crash reports to Claude Code — crash summary, affected versions, device distribution
- Building a `/triage-crash` skill that returns: severity assessment, user impact, root cause hypothesis, fix priority
- Non-fatal exception analysis — caught exceptions that indicate problems (excessive retries, fallback paths)
- Crash trends and regression detection — AI comparing crash rates across releases to find regressions
- Custom Crashlytics keys and logs — teaching AI what your custom keys mean for domain-specific analysis
- ANR monitoring in production — Google Play Console ANR data, clusters, AI analysis of patterns
- Performance monitoring integration — Firebase Performance traces, slow rendering, network timing
- Building a `/weekly-crash-report` skill that summarizes the week's top crashes with fix recommendations
- Exercise: export top 3 Crashlytics clusters, feed to Claude Code, produce a prioritized fix plan

### Chapter 12: Performance Budgets and Your Debugging Playbook
**File:** `12-performance-playbook.html`
**Goal:** Establish measurable performance budgets and build a personal AI-debugging playbook for ongoing use.

**Topics:**
- What performance budgets are — concrete thresholds for startup, frame rate, memory, APK size, network
- Setting budgets for your app — AI helping choose realistic targets based on app category and user base
- Benchmark libraries — Macrobenchmark and Microbenchmark setup, baseline measurement, feeding results to AI
- Building a `/check-budgets` skill that compares current benchmarks against budgets and flags violations
- Startup time optimization — App Startup library, tracing cold/warm/hot start, AI analyzing the startup trace
- APK size analysis — apkanalyzer, resource shrinking, code shrinking, AI identifying biggest size contributors
- The debugging decision tree — a flowchart for "my app is slow/crashing/draining battery" routing to the right tool
- Building your personal debugging toolkit — curating skills built throughout this course
- Team debugging culture — sharing skills across the team, consistent practices, knowledge base
- Continuous performance monitoring — automated benchmark runs in CI, AI-powered regression alerts
- The 30-day debugging challenge — week 1 crash analysis, week 2 profiling, week 3 memory/battery, week 4 test stability

### Chapter 13: Debugging 16 KB Page Size Compatibility for Native Libraries
**File:** `13-16kb-page-size.html`
**Goal:** Diagnose and fix the `dlopen failed: unsupported page size 16384` crash class that gates Google Play submissions for any app shipping native code in 2026.

**Topics:**
- The `unsupported page size 16384` / `is not page-size compatible` logcat signature and why it appears
- The 30-second mental model: 4 KB-aligned `.so` segments cannot be `mmap()`-ed onto a 16 KB page grid
- Catching it before shipping: APK Analyzer alignment column, `check_elf_alignment.sh`, `llvm-objdump -p`, `zipalign -c -P 16`
- Building an `/analyze-page-size` skill that audits an alignment report and produces a remediation plan
- Identifying the offending `.so` from a crash log (manual + via `/diagnose-page-size-crash` skill)
- When the culprit is a transitive NDK dependency: React Native, Flutter, OpenCV, ML Kit, SQLCipher, Conscrypt, Unity/Unreal — version-bump cheat sheet
- Rebuilding with NDK r28+ and AGP 8.5.1+ for 16 KB alignment by default
- Legacy linker flags for older NDK: `-Wl,-z,max-page-size=16384 -Wl,-z,common-page-size=16384`
- Runtime alternatives: replace hardcoded `4096` / `PAGE_SIZE` with `getpagesize()` or `sysconf(_SC_PAGESIZE)`
- Testing: Android Studio 16 KB emulator system images and Pixel 8/9 "Boot with 16 KB page size" developer toggle, verified with `adb shell getconf PAGE_SIZE`
- Decision matrix: bump dependency vs rebuild from source vs drop dependency vs wait vs fork-and-patch
- Closing exercise: introduce a misaligned `libnative-lib.so`, capture the crash, run `/diagnose-page-size-crash`, fix two ways

### Chapter 14: Debugging Background-Work Restrictions on Modern Android (15 / 16)
**File:** `14-modern-background-restrictions.html`
**Goal:** Diagnose silent and noisy background-work failures introduced by Android 15 and 16 — `ForegroundServiceStartNotAllowedException` from `BOOT_COMPLETED`, the 6-hour `dataSync`/`mediaProcessing` FGS timeout, and Android 16 job runtime quotas concurrent with FGS.

**Topics:**
- The restriction landscape mapped across Android 12 → 13 → 14 → 15 → 16 with the exception each version added
- `ForegroundServiceStartNotAllowedException` from `BOOT_COMPLETED`: the exact "BG-FGS-start not allowed" message, restricted vs allowed FGS types, how to reproduce with `adb shell am compat enable FGS_BOOT_COMPLETED_RESTRICTIONS`
- Migrating BootReceiver-triggered foreground services to WorkManager `OneTimeWorkRequest` with constraints
- The 6-hour cumulative `dataSync` / `mediaProcessing` FGS timeout: implementing `Service.onTimeout(int, int)`, the few-second `stopSelf()` window, the `RemoteServiceException: "did not stop within its timeout"` failure mode
- Forcing the FGS timeout in test: `adb shell am compat enable FGS_INTRODUCE_TIME_LIMITS` plus `device_config put activity_manager data_sync_fgs_timeout_duration`
- Android 16 JobScheduler quota changes: jobs concurrent with FGS or in active bucket now adhere to runtime quotas; `setImportantWhileForeground()` silently ignored
- New Android 16 debugging APIs: `JobScheduler#getPendingJobReasons` and `getPendingJobReasonsHistory`
- Diagnosing "my background sync just stopped" with `adb shell dumpsys jobscheduler` (STOP_REASON_QUOTA / TIMEOUT / DEVICE_STATE) and Battery Historian
- Standby-bucket sanity check with `adb shell am get-standby-bucket` / `set-standby-bucket`
- Predictive back-gesture compatibility (Android 14 opt-in, Android 15 Pixel fix) as a related modern-OS quirk
- Building a `/diagnose-background-restriction` skill that takes logcat + dumpsys and identifies which restriction policy fired
- Migration playbook: when to drop FGS in favor of WorkManager (boot resume, periodic backup) vs when to keep it (mediaPlayback, location, phoneCall, mediaProcessing with onTimeout())
- Closing exercise: simulate the BOOT_COMPLETED restriction with `adb shell am compat enable`, diagnose with the new skill, migrate to WorkManager, then repeat the loop for the 6-hour timeout
