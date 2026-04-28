# AI-Driven Debugging & Performance for iOS

## Project Description
An HTML course for iOS developers who want to use AI to debug faster and optimize performance. The reader already knows Swift and Xcode but hasn't applied AI systematically to debugging — crash analysis, profiling, memory leaks, hangs, SwiftUI performance, build times, and production monitoring.

**Tool focus: Xcode 26 AI features AND Claude Code.** This course covers both Xcode's native AI integration (ChatGPT, Anthropic API keys, Swift Assist, local models on Apple silicon) and Claude Code as external AI tools for iOS debugging. It also covers XcodeBuildMCP for AI agent control of Xcode.

The style is **"For Dummies"** — friendly, approachable, like a senior iOS dev showing you debugging tricks over coffee. Heavy on practical examples with real crash reports, Instruments output, and hands-on exercises.

## Language Rules
- All content is in **English**
- Tone: friendly, conversational, like a colleague who's seen every crash pattern
- Use real iOS debugging scenarios (actual crash patterns, real Instruments output, genuine Xcode build issues)
- Address: second person singular (you)
- When introducing a debugging technique, always show: "Here's the raw output" → "Here's what AI finds" → "Here's the fix"
- Light humor is welcome — debugging is painful enough without dry writing
- Use short paragraphs — walls of text kill understanding
- **Cover both Xcode 26 AI features AND Claude Code** — show when each tool is the better choice for the debugging task at hand
- Reference XcodeBuildMCP where relevant for AI agent integration with Xcode

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
- All generated chapters MUST meet the 400-line minimum on the FIRST attempt. Count lines before finalizing. If under 400 lines, expand sections with examples, diagrams, tips, and detailed explanations before presenting.
- Never pad content incrementally — produce complete, full-length content in one pass.

## HTML Validation Rules
- Always close tip-box divs with `</div>`, never `</tip>`.
- Validate all HTML tags are properly closed before completing a chapter.

## Project Structure Rules
- Always check the current working directory and respect the explicit project path provided by the user. Do NOT search parent directories or sibling projects unless explicitly asked.

## Cross-Reference Rules
- When generating multi-file series, ensure all cross-reference links between chapters are consistent. Use relative paths and verify link targets exist before finishing.

## File Structure
```
iOS-Debug/
  CLAUDE.md                                — This file
  .claude/
    commands/
      generate-next-chapter.md             — Skill for chapter generation
      create-memory-map.md                 — Skill for visual chapter summary generation
  chapters/
    index.html                             — Landing page with navigation
    assets/
      style.css                            — Shared CSS with dark/light theme
    01-ai-debugger-mindset.html            — The AI-Powered iOS Debugger Mindset
    02-crash-reports-symbolication.html    — Crash Reports, Logs & Symbolication
    03-hangs-responsiveness.html           — Hangs & Responsiveness Diagnosis
    04-memory-leaks.html                   — Memory Leak Detection with AI
    05-swiftui-rendering.html              — SwiftUI Rendering Performance
    06-network-urlsession.html             — Network & URLSession Debugging
    07-xcode-build-performance.html        — Xcode Build Performance
    08-energy-thermal.html                 — Energy & Thermal Optimization
    09-ai-assisted-instruments.html        — AI-Assisted Instruments Profiling
    10-flaky-tests.html                    — Flaky Test Diagnosis
    11-production-monitoring.html          — Production Monitoring & Crash Reporting
    12-performance-playbook.html           — Performance Budgets & Your Debugging Playbook
    maps/                                  — Visual memory maps (generated on demand)
```

## Progress Tracking
- [x] Chapter 1: The AI-Powered iOS Debugger Mindset
- [x] Chapter 2: Crash Reports, Logs & Symbolication
- [x] Chapter 3: Hangs & Responsiveness Diagnosis
- [x] Chapter 4: Memory Leak Detection with AI
- [x] Chapter 5: SwiftUI Rendering Performance
- [x] Chapter 6: Network & URLSession Debugging
- [x] Chapter 7: Xcode Build Performance
- [x] Chapter 8: Energy & Thermal Optimization
- [x] Chapter 9: AI-Assisted Instruments Profiling
- [x] Chapter 10: Flaky Test Diagnosis
- [x] Chapter 11: Production Monitoring & Crash Reporting
- [x] Chapter 12: Performance Budgets & Your Debugging Playbook

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
- `.debug-trace` — crash report, LLDB output, Instruments data, or os_log output with AI analysis (Apple Blue accent, unique to this course)
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
- **At least one `.debug-trace`** per chapter with a crash report, LLDB output, Instruments data, or os_log output with AI analysis
- **At least one `.root-cause`** per chapter with a root cause analysis finding
- **At least one `.fix-pattern`** per chapter showing a common fix pattern or solution
- **At least one `.performance-metric`** per chapter (where applicable) showing before/after metrics
- **At least one `.exercise-box`** per chapter where the reader debugs or profiles something real
- **Show both Xcode 26 AI features AND Claude Code** — demonstrate when each is the better choice
- Keep code examples practical and real (Swift, LLDB output, crash reports, Instruments data, Xcode build settings, MetricKit payloads)
- Each chapter should end with a preview of how it connects to the next chapter
- Every chapter should teach the reader to build at least one reusable Claude Code skill (/command)

## Chapter Details

### Chapter 1: The AI-Powered iOS Debugger Mindset
**File:** `01-ai-debugger-mindset.html`
**Goal:** Shift the reader from print-statement debugging to systematic AI-assisted debugging with LLDB, Xcode 26, and Claude Code.

**Topics:**
- Why debugging is still the biggest time sink for iOS devs — real numbers and developer surveys
- The traditional debugging cycle (print → rebuild → reproduce) vs. the AI-augmented cycle (observe → AI hypothesize → verify → fix)
- How AI reads Swift stacktraces differently than you do — pattern matching across millions of known issues
- The new AI landscape for iOS: Xcode 26 native AI (ChatGPT integration, Anthropic API keys, Swift Assist, local models on Apple silicon) vs. Claude Code as external tool — when to use each
- XcodeBuildMCP: giving AI agents full Xcode control (build, test, debug via LLDB, simulator interaction)
- Setting up Claude Code for iOS debugging — CLAUDE.md rules, project context, relevant file patterns for Swift/Xcode projects
- Your first AI-assisted debug session: feeding an `EXC_BAD_ACCESS` crash to Claude Code and Xcode AI
- Building a `/debug` skill — a reusable command that takes a crash log or stacktrace and returns structured analysis
- The "5 Whys" technique with AI — using follow-up prompts to drill past symptoms to root causes
- When AI is wrong — recognizing hallucinated fixes and validating AI suggestions in Swift context
- The debugging journal — using Claude Code to maintain a log of bugs, root causes, and fixes for your iOS project

### Chapter 2: Crash Reports, Logs & Symbolication
**File:** `02-crash-reports-symbolication.html`
**Goal:** Master iOS crash report analysis, dSYM symbolication, and structured logging with AI assistance.

**Topics:**
- Anatomy of an iOS crash report (.ips files) — what each section means (exception type, thread backtrace, binary images) and what AI needs to see
- dSYM symbolication: why unsymbolicated reports are useless, how to locate dSYMs, using `atos` and `symbolicatecrash` tools
- Console.app log filtering — navigating the firehose of system logs to find your app's messages
- os_log structured logging — OSLogStore, log categories, subsystems, signposts — giving AI structured data to analyze
- Reading exception types with AI: `EXC_BAD_ACCESS (SIGBUS)`, `EXC_BAD_ACCESS (SIGSEGV)`, `EXC_CRASH (SIGABRT)`, `EXC_BREAKPOINT` — what each means
- Building an `/analyze-crash` skill that takes raw .ips crash report content and returns: crash type, faulting thread, likely root cause, affected component, and suggested fix
- Multi-device crashes — using AI to compare stacktraces across different iOS versions, device models, and architectures
- Third-party framework crashes — when the stacktrace points into UIKit, SwiftUI, Core Data, or Combine internals
- Common crash patterns AI recognizes instantly: force-unwrap nil optionals, out-of-bounds array access, unrecognized selector, keypath crashes, Swift concurrency precondition failures
- Exercise: capture a real crash from Xcode organizer or simulator, paste the full crash report into Claude Code, walk through the AI analysis

### Chapter 3: Hangs & Responsiveness Diagnosis
**File:** `03-hangs-responsiveness.html`
**Goal:** Use AI to diagnose main thread hangs, watchdog terminations, and responsiveness issues — among the hardest iOS bugs.

**Topics:**
- What hangs are and why they are worse than crashes — UX impact, App Store review rejection, user retention damage
- The watchdog: `0x8BADF00D` termination code — what triggers it, timeout thresholds for different app states (launch, background, foreground)
- MetricKit MXHangDiagnostic — receiving hang diagnostic payloads in production, the hang call stack format
- Thread Checker: detecting main-thread violations at development time — Xcode runtime warnings
- Reading hang reports with AI — feeding the call tree to Claude Code to identify the blocking operation
- Building an `/analyze-hang` skill that identifies: blocked thread, blocking operation, call chain, and suggested async alternative
- Common hang patterns: synchronous network on main thread, heavy Core Data fetches, synchronous keychain access, large image decoding on main thread, excessive Auto Layout recalculation
- Swift concurrency and hangs: detecting `MainActor` misuse, finding blocking calls inside async contexts, Task priority inversion
- Instruments Time Profiler for hang analysis — recording a hang, finding the heavy main-thread sample, AI interpreting the call tree
- Using `os_signpost` to measure and identify hang-prone code sections
- Exercise: introduce a deliberate `Thread.sleep(6)` on the main thread, capture the hang diagnostic, use Claude Code to diagnose and refactor to async

### Chapter 4: Memory Leak Detection with AI
**File:** `04-memory-leaks.html`
**Goal:** Combine Memory Graph Debugger output and Instruments data with AI to find and fix retain cycles and memory leaks.

**Topics:**
- Why memory leaks matter on iOS — OOM jetsam terminations, the `EXC_RESOURCE` exception, reduced multitasking priority
- Memory Graph Debugger: capturing a memory graph in Xcode, reading the visual retain graph, exporting memory graph data
- Instruments Leaks template and Allocations instrument — recording allocations, identifying persistent growth, leak detection
- Feeding Memory Graph Debugger output to Claude Code — the retain cycle chain is structured data that AI analyzes well
- Building an `/analyze-leak` skill that returns: leaking object, GC root, retention chain explanation, and fix options (weak, unowned, capture lists)
- The classic iOS memory leaks: strong delegate references, closure capture of `self` without `[weak self]`, `NotificationCenter` observer leaks, `Timer` retain cycles, `CADisplayLink` strong targets
- `weak` vs `unowned` — when each is correct, the crash risk of `unowned`, AI auditing for misuse
- SwiftUI memory considerations: `@StateObject` vs `@ObservedObject` lifetime, `@Observable` class retention, `NavigationStack` view lifecycle
- Combine memory leaks: `AnyCancellable` storage, `sink` closures capturing self, `store(in:)` patterns
- Building a `/scan-for-leaks` skill that reviews Swift source files for known leak patterns
- Exercise: create a deliberate retain cycle with a closure capturing self strongly, use Memory Graph Debugger to visualize it, use Claude Code to suggest the fix

### Chapter 5: SwiftUI Rendering Performance
**File:** `05-swiftui-rendering.html`
**Goal:** Diagnose and fix SwiftUI performance issues using AI to analyze view body evaluations, identity, and rendering overhead.

**Topics:**
- The SwiftUI rendering mental model: view body evaluation, diffing, and rendering — what triggers re-evaluation and why excessive evaluation kills performance
- `Self._printChanges()` — the key debugging tool: adding it to view bodies to see exactly what changed and why a view re-evaluated
- Instruments View Body track — recording view body evaluations, identifying hot views, Count and Avg Duration metrics
- Feeding `_printChanges()` output and Instruments data to Claude Code — "This view body evaluates 47 times during a scroll"
- `@Observable` (Observation framework) vs `@ObservedObject` / `@StateObject` — the granularity difference and performance implications
- Common SwiftUI performance traps AI catches: reading too many properties in a view body, unstable view identity, creating objects inside body, missing `@State` for local state, heavy computation in body
- Building an `/analyze-rendering` skill that identifies the cause of excessive re-evaluation and suggests a fix
- Structural identity vs explicit identity (`id()` modifier) — how identity drives view lifetime and animation performance
- `EquatableView`, custom `Equatable` conformance, and `@State` optimization patterns
- LazyVStack/LazyHStack performance — missing explicit `id`, heavy row views, prefetching considerations
- Exercise: build a deliberately inefficient SwiftUI List with excessive re-rendering, measure with `_printChanges()`, use Claude Code to optimize step by step

### Chapter 6: Network & URLSession Debugging
**File:** `06-network-urlsession.html`
**Goal:** Use AI to diagnose network-layer issues in URLSession-based iOS apps, including async/await patterns and security.

**Topics:**
- The network debugging challenge on iOS: SSL, ATS, timeouts, retries, Codable serialization, async/await threading
- URLSession logging: `URLSessionTaskMetrics`, custom logging delegates, capturing request/response pairs programmatically
- Charles Proxy and Proxyman — setting up HTTPS interception, reading captured traffic, feeding session exports to AI
- Feeding network logs to Claude Code — request/response pairs, timing data, error descriptions for analysis
- Building an `/analyze-network` skill that identifies: failed requests, slow responses, retry storms, certificate issues, and unnecessary calls
- SSL pinning failures: `NSURLAuthenticationChallenge`, `SecTrust` evaluation, App Transport Security exceptions — AI diagnosing `NSURLErrorSecureConnectionFailed`
- async/await networking patterns with AI review — structured concurrency pitfalls, `TaskGroup` for parallel requests, cancellation handling
- Combine networking: `URLSession.DataTaskPublisher`, error handling chains, AI reviewing `flatMap`/`retry` operator chains
- Timeout and retry strategies — AI analyzing `URLSessionConfiguration` settings and suggesting optimal values
- Caching strategy review — `URLCache`, HTTP caching headers, AI auditing cache policy configuration
- Exercise: capture a failing API flow using Proxyman or URLSession logging, paste the data into Claude Code, get step-by-step diagnosis

### Chapter 7: Xcode Build Performance
**File:** `07-xcode-build-performance.html`
**Goal:** Use AI to analyze Xcode build timelines and optimize build times for Swift projects.

**Topics:**
- Why build speed matters — developer flow state, CI costs, iteration speed on large Swift projects
- Xcode build timeline: enabling the build timeline view, reading task durations, identifying serialized bottlenecks
- Swift compilation time flags: `-Xfrontend -warn-long-function-bodies`, `-Xfrontend -warn-long-expression-type-checking` — finding slow-to-compile expressions
- Feeding build timing data to Claude Code — task names, durations, dependencies, and parallel execution analysis
- Building an `/analyze-build` skill that identifies: slowest compilation units, serialized bottlenecks, cache misses, and configuration issues
- SPM (Swift Package Manager) resolution performance — package graph complexity, version resolution time, binary target usage
- Module stability and framework builds — when to use `BUILD_LIBRARY_FOR_DISTRIBUTION`, the ABI stability trade-off
- Build settings optimization: `SWIFT_COMPILATION_MODE` (whole module vs incremental), `EAGER_LINKING`, `SWIFT_ENABLE_BATCH_MODE`, `DEBUG_INFORMATION_FORMAT`
- Modularization for build speed — AI suggesting module boundaries, reducing recompilation cascades
- CI-specific optimizations: Xcode Cloud considerations, derived data caching, parallel destination testing
- Exercise: examine your project's build timeline, extract timing data, use Claude Code to recommend the top 3 optimizations

### Chapter 8: Energy & Thermal Optimization
**File:** `08-energy-thermal.html`
**Goal:** Use AI to identify and fix battery-draining and thermal-throttling behaviors in your iOS app.

**Topics:**
- Why energy optimization matters on iOS — battery complaints in App Store reviews, Apple's energy debugging guidance, thermal throttling impact on performance
- Energy Instruments: the Energy Impact gauge in Xcode, Energy Log instrument, recording energy usage by subsystem
- MetricKit energy metrics: `MXMetricPayload` energy data, `MXCPUMetric`, `MXGPUMetric`, `MXDiskIOMetric`, `MXNetworkTransferMetric`
- Feeding energy profiling data to Claude Code — subsystem breakdown, CPU wake frequency, network transfer patterns
- Building an `/analyze-energy` skill that identifies: excessive CPU usage, inefficient scheduling, background abuse, location drain
- BGTaskScheduler: `BGAppRefreshTask` vs `BGProcessingTask`, efficient background work scheduling, AI reviewing task registration
- Core Location energy impact: `desiredAccuracy` levels, `allowsBackgroundLocationUpdates`, significant location changes vs continuous monitoring — AI auditing location configuration
- Thermal state monitoring: `ProcessInfo.thermalState`, responding to thermal pressure, throttling features gracefully
- Audio and media session energy: `AVAudioSession` configuration, background audio patterns, video playback energy
- Network energy optimization: `waitsForConnectivity`, background URL session configuration, batching network requests
- Power Profiler (Xcode 26): the new Instruments tool for system power usage visualization — AI interpreting subsystem-level power attribution
- Exercise: profile your app's energy usage during a typical user session, extract the data, use Claude Code to identify the top 3 energy drains

### Chapter 9: AI-Assisted Instruments Profiling
**File:** `09-ai-assisted-instruments.html`
**Goal:** Learn to extract profiler data from Xcode Instruments and use AI to interpret CPU, memory, and system traces.

**Topics:**
- The profiler data gap: Instruments shows beautiful graphs, AI explains what they mean in your code's context
- Time Profiler deep dive: recording, reading the call tree, heaviest stack trace, understanding sample counts and weight
- Allocations instrument: heap growth analysis, transient vs persistent allocations, generation analysis
- Building a `/profile-cpu` skill that takes hot methods with call counts and durations, identifies CPU bottlenecks and suggests optimizations
- System Trace: thread scheduling, context switches, priority inversions — when your code is waiting vs running
- Power Profiler (Xcode 26): subsystem-level power attribution, correlating code execution with energy impact
- Combining profiler data with code context: feeding both Instruments output AND Swift source to AI for a complete picture
- AI interpretation patterns: "This method accounts for 40% of main thread CPU during scroll — here is the allocation it triggers and the fix"
- Xcode 26 AI integration for profiling: using native AI to explain Instruments results directly in Xcode
- Instruments automation: `xctrace` command-line tool for CI profiling, exporting trace data for AI analysis
- Exercise: profile a screen transition with Time Profiler, export the call tree data, use Claude Code to explain the 3 most expensive operations and suggest fixes

### Chapter 10: Flaky Test Diagnosis
**File:** `10-flaky-tests.html`
**Goal:** Use AI to systematically diagnose and fix XCTest and XCUITest flakiness.

**Topics:**
- Why flaky tests erode trust: the "retry and ignore" culture and its cost to team velocity
- Categorizing flaky tests: timing-dependent, order-dependent, environment-dependent, resource-dependent
- Feeding test failure logs to Claude Code: test name, assertion failure, stacktrace, XCTest output, recent code changes
- Building a `/diagnose-flaky` skill that returns: flakiness category, likely root cause, fix strategy
- XCTest async patterns: `XCTestExpectation` vs `async/await` tests, `fulfillment(of:)` timeout tuning, `Task` testing with `withCheckedThrowingContinuation`
- XCUITest synchronization: `waitForExistence(timeout:)`, custom expectations, animation completion, handling system alerts and permission dialogs
- Test plan configuration: parallel vs sequential execution, test repetition modes (until failure, retry on failure), randomized order for detecting state coupling
- Swift concurrency testing: testing `@MainActor` code, `Task` cancellation, actor isolation in test targets (Swift 6.2 improvements)
- CI simulator issues: simulator boot time, CoreSimulator reliability, Xcode version mismatches, running tests on Apple silicon CI (GitHub Actions, Xcode Cloud)
- Shared mutable state: singletons in tests, Core Data in-memory stores, UserDefaults suite isolation, keychain test cleanup
- Exercise: take your team's most notorious flaky test, collect failure logs across multiple runs, use Claude Code to find the root cause

### Chapter 11: Production Monitoring & Crash Reporting
**File:** `11-production-monitoring.html`
**Goal:** Use AI to analyze production crash data from Crashlytics, MetricKit, and Xcode Organizer to prioritize and fix production issues.

**Topics:**
- The production debugging challenge: no debugger, no LLDB, only telemetry and crash reports
- Firebase Crashlytics for iOS: integration, crash clusters, non-fatal exceptions, breadcrumbs, custom keys
- Feeding Crashlytics crash reports to Claude Code: crash summary, affected iOS versions, device distribution, reproduction frequency
- Building a `/triage-crash` skill that returns: severity assessment, user impact estimate, root cause hypothesis, fix priority
- MetricKit production diagnostics: `MXMetricPayload` and `MXDiagnosticPayload`, receiving diagnostic data in-app, the 24-hour reporting cadence
- Xcode Organizer insights: the Crashes, Energy, Hangs, Disk Writes, and Launch tabs — extracting data for AI analysis
- TestFlight beta feedback: linking beta tester crash reports with feedback, using AI to correlate crash patterns with user-reported issues
- On-device crash logs: retrieving `.ips` files from Settings > Privacy > Analytics, parsing them without Xcode Organizer
- Non-fatal exception analysis: caught errors that indicate problems (excessive retries, fallback code paths, degraded experiences)
- Crash trends and regression detection: AI comparing crash rates across app versions to find regressions introduced by specific builds
- Exercise: export top 3 crash clusters from Crashlytics or Xcode Organizer, feed to Claude Code, produce a prioritized fix plan with estimated user impact

### Chapter 12: Performance Budgets & Your Debugging Playbook
**File:** `12-performance-playbook.html`
**Goal:** Establish measurable performance budgets and build a personal AI-debugging playbook for ongoing use.

**Topics:**
- What performance budgets are: concrete thresholds for launch time, frame rate, memory footprint, app size, network payload
- Setting budgets for your iOS app: AI helping choose realistic targets based on app category and Apple's recommendations
- XCTest performance metrics: `measure {}` blocks, baselines, standard deviation thresholds, CI enforcement
- MetricKit launch time: `MXAppLaunchMetric`, cold vs warm vs hot launch, measuring time-to-interactive
- App size management: App Thinning (slicing, bitcode, on-demand resources), asset catalog optimization, AI identifying the largest size contributors
- Building a `/check-budgets` skill that compares current metrics against budgets and flags violations
- The debugging decision tree: a flowchart for "my app is slow / crashing / draining battery / hanging" routing to the right tool (LLDB, Instruments, Memory Graph, MetricKit, Crashlytics)
- Building your personal debugging toolkit: curating and organizing the 12 skills built throughout this course into a cohesive system
- Team debugging culture: sharing Claude Code skills across the team, consistent CLAUDE.md practices, knowledge base of past bugs
- Continuous performance monitoring: automated XCTest performance tests in CI, MetricKit dashboards, regression alerts
- The 30-day debugging challenge: week 1 crash analysis, week 2 profiling and Instruments, week 3 memory and energy, week 4 test stability and production monitoring
