# Rewriting Apps With AI For Dummies

## Project Description
An HTML guide in English for experienced developers who want to use AI to transform an existing monolith into a clean, well-architected codebase. The running case study is a recipes Android app: starting as a classic monolith (single module, God Activities, raw SQL, no DI, no tests) and ending as a production-grade Clean Architecture app (10 modules, MVI, Room, Hilt, Compose).

The target audience is developers who ALREADY know Clean Architecture, MVI, dependency injection, and testing. They don't need the patterns explained — they need to learn how to orchestrate AI to execute the transformation efficiently, using architecture rules as AI constraints.

The style is **"For Dummies"** — friendly and approachable, but respecting the reader's existing expertise.

## Language Rules
- All content is in **English**
- Tone: surgical, transformation-focused — like a senior architect leading a migration
- Assume the reader already knows: Clean Architecture, MVI/MVVM, Room, Hilt, Compose, Coroutines
- NEVER explain what Clean Architecture is, how MVI works, or why dependency injection matters
- Focus on: how to prompt AI, what context to provide, what rules to set, how to review AI output
- Use analogies from renovation/remodeling to explain the rewrite process
- Reference other courses inline: "For more on [topic], see [Course Name] Chapter N"

## HTML Conventions
- Each chapter is a separate HTML file in `chapters/`
- Shared CSS: `assets/style.css`
- Target chapter length: **400-600 lines HTML**
- UTF-8, HTML5 doctype, meta viewport

## Content Generation Rules
- All generated chapters MUST meet the 400-line minimum on the FIRST attempt.
- Never pad content incrementally — produce complete, full-length content in one pass.

## HTML Validation Rules
- Always close tip-box divs with `</div>`, never `</tip>`.
- Validate all HTML tags are properly closed before completing a chapter.

## Project Structure Rules
- Always check the current working directory. Do NOT search parent directories or sibling projects unless explicitly asked.

## Cross-Reference Rules
- Ensure all cross-reference links between chapters use relative paths and point to valid targets.

## File Structure
```
AI-Rewrite/
  CLAUDE.md
  .claude/
    commands/
      generate-next-chapter.md
      create-memory-map.md
  chapters/
    index.html
    assets/
      style.css                          — Shared CSS (fuchsia + cyan scheme)
    01-rewrite-decision.html             — The Rewrite Decision
    02-teaching-ai-standards.html        — Teaching AI Your Standards
    03-ai-driven-rewrite-setup.html      — Setting Up the AI-Driven Rewrite
    04-monolith-to-multimodule.html      — From Monolith to Multi-Module
    05-domain-layer.html                 — Extracting the Domain Layer
    06-data-layer.html                   — Building the Data Layer With AI
    07-presentation-layer.html           — The Presentation Layer: MVI With AI
    08-dependency-injection.html         — Dependency Injection: Hilt Modules With AI
    09-navigation-errors.html            — Navigation, Errors, and Cross-Cutting Concerns
    10-testing-rewrite.html              — Testing the Rewrite
    11-integration-sprint.html           — The Integration Sprint
    12-lessons-playbook.html             — Lessons From the Rewrite: Your Playbook
    maps/
```

## Progress Tracking
- [x] Chapter 1: The Rewrite Decision
- [x] Chapter 2: Teaching AI Your Standards
- [x] Chapter 3: Setting Up the AI-Driven Rewrite
- [x] Chapter 4: From Monolith to Multi-Module
- [x] Chapter 5: Extracting the Domain Layer
- [x] Chapter 6: Building the Data Layer With AI
- [x] Chapter 7: The Presentation Layer: MVI With AI
- [x] Chapter 8: Dependency Injection: Hilt Modules With AI
- [x] Chapter 9: Navigation, Errors, and Cross-Cutting Concerns
- [x] Chapter 10: Testing the Rewrite
- [x] Chapter 11: The Integration Sprint
- [x] Chapter 12: Lessons From the Rewrite: Your Playbook

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
- `.migration-step` — before/after code transformation (fuchsia accent, `.before-code` + `.after-code` children)
- `.rule-callout` — architecture rule reference with rule ID (indigo accent)
- `.module-map` — module dependency graph visualization (teal accent)
- `.ai-review-box` — AI reviewing code against rules with pass/fail (green/red accent)
- `.prompt-example.good` / `.prompt-example.bad`
- `.comparison`, `.tip-box`, `.warning-box`, `.exercise-box`
- `.checklist`, `.highlight-box`, `.stats-grid`, `.stat-card`
- `.tool-card`, `.workflow-steps`

## Content Guidelines
- **At least 1 `.migration-step`** per chapter with before/after code
- **At least 1 `.rule-callout`** per chapter referencing a specific architecture rule
- **At least 1 `.exercise-box`** per chapter where the reader applies the technique
- Code examples reference the actual recipes app (`:feature:recipe`, `:core:domain`, etc.)
- Never explain Clean Architecture or MVI basics
- Focus on the AI interaction: what prompt, what context, what review

## Chapter Details

### Chapter 1: The Rewrite Decision
**File:** `01-rewrite-decision.html`
**Goal:** When to rewrite vs refactor, and how AI changes the calculus.
**Topics:**
- The rewrite vs refactor decision framework: when each makes sense
- How AI changes the time/risk equation: rewrites are now feasible that weren't before
- The recipes app monolith: the "before" state (single module, God Activities, database-in-UI, no DI, no tests)
- The target: 10-module Clean Architecture with MVI, Room, Hilt, Compose, 128+ tests
- Using AI to audit existing code quality: the "AI codebase health check"
- Estimating rewrite scope with AI assistance
- The rewrite manifesto: what changes, what stays, what gets deleted
- Risk assessment: identifying the highest-risk transformations
- Cross-reference: "AI-Engineering covers the project setup you'll need. This course applies it to a real rewrite."

### Chapter 2: Teaching AI Your Standards
**File:** `02-teaching-ai-standards.html`
**Goal:** Write the dual-format architecture rules BEFORE touching code.
**Topics:**
- Why rules before code: preventing AI from introducing violations during the rewrite
- The 10 architecture rule areas: package structure, presentation, domain, data, error handling, network, testing, DI, Gradle, navigation
- Writing review checklists: MUST/SHOULD/PREFER severity, concrete examples, anti-patterns
- Condensing to `.ctx` files: the 25-line constraint, one-line summaries, cross-references
- Walkthrough: the actual rules from `/app/generic-app-cheks-and-rules/`
- Loading rules into your rewrite project's CLAUDE.md
- Testing that AI follows your rules: the "rule compliance test"
- The rule evolution cycle: update rules as you learn during the rewrite
- Cross-reference: "AI-Engineering Chapter 7 covers the architecture rules pattern in depth. Here we apply it."

### Chapter 3: Setting Up the AI-Driven Rewrite
**File:** `03-ai-driven-rewrite-setup.html`
**Goal:** CLAUDE.md, skills, and hooks configured for a rewrite project.
**Topics:**
- The rewrite CLAUDE.md: architecture rules, module boundaries, naming conventions, forbidden patterns
- Rewrite-specific skills: `/migrate-to-module`, `/extract-domain`, `/add-di`, `/generate-tests-for-migration`
- Quality gate hooks: preventing new code in the monolith module
- The migration tracking system: tracking which files have been migrated
- Branch strategy for AI-driven rewrites: feature branches per module extraction
- The "rewrite dashboard": knowing what's done, what's in progress, what's remaining
- Cross-reference: "AI-Engineering Chapters 2-5 cover the general configuration. This chapter applies it to rewrite scenarios."

### Chapter 4: From Monolith to Multi-Module
**File:** `04-monolith-to-multimodule.html`
**Goal:** AI creates the 10-module Gradle structure from the monolith.
**Topics:**
- Using AI to analyze monolith dependencies: the "dependency graph prompt"
- Generating the Gradle module structure: settings.gradle.kts, build.gradle.kts for each module
- The 10-module target: app, core/common, core/design-system, core/domain, core/testing, data/local, data/repository, feature/recipe, feature/books, feature/grocery
- Dependency rules (what depends on what): using the package-structure rules as constraints
- The dependency inversion principle as AI context: making sure AI wires modules correctly
- Validating the module graph: AI-assisted dependency verification
- The first compile: making the empty multi-module project build successfully
- Common AI mistakes: circular dependencies, wrong visibility modifiers, missing module declarations

### Chapter 5: Extracting the Domain Layer
**File:** `05-domain-layer.html`
**Goal:** AI extracts pure Kotlin domain models, repository interfaces, and use cases.
**Topics:**
- Identifying domain concepts in monolith code: AI-assisted "code archaeology"
- The domain layer rules as AI constraints: pure Kotlin, no Android dependencies, Result pattern
- Extracting data classes and sealed types from Activities and Fragments
- Defining repository interfaces: the contract between domain and data
- Creating use cases: the "one public method" pattern (operator fun invoke)
- The Result sealed class: standardizing error handling across the domain
- Generating domain tests: AI-written tests for extracted logic
- Common AI mistakes: leaking Android dependencies into domain, creating anemic use cases

### Chapter 6: Building the Data Layer With AI
**File:** `06-data-layer.html`
**Goal:** Room entities, DAOs, mappers, and repository implementations.
**Topics:**
- The data layer rules as AI constraints: explicit @ColumnInfo, enums as String, @Transaction on @Relation
- AI-generated Room entities and DAOs: from raw SQLite to Room
- Repository implementation: the bridge between domain interfaces and Room DAOs
- Data mappers: entity ↔ domain model conversion at the boundary
- Error handling at the data boundary: catching exceptions, returning Result
- Room migration with AI: generating migration scripts
- Testing with fakes: AI-generated fake repository implementations
- Common AI mistakes: exposing Room entities to UI, missing @Transaction, wrong error handling

### Chapter 7: The Presentation Layer: MVI With AI
**File:** `07-presentation-layer.html`
**Goal:** ViewModels with Contract pattern, Compose screens, reducer pattern.
**Topics:**
- The presentation layer rules: single immutable State, sealed Event interface, Channel for effects
- The MVI Contract pattern: State data class, Event sealed interface, Effect sealed interface
- AI-generated ViewModels: loading the presentation rules as context
- The reducer as a pure function: telling AI about the reduce(state, event) → state + effects pattern
- Compose screens from AI: converting Activities/Fragments to Composables
- State management: single source of truth, no scattered StateFlows
- The presentation rules checklist: 50+ rules covering state, events, reducers, effects, ViewModels
- Reviewing AI-generated presentation code against the checklist
- Common AI mistakes: mutable state, shared effects, business logic in Composables

### Chapter 8: Dependency Injection: Hilt Modules With AI
**File:** `08-dependency-injection.html`
**Goal:** Hilt setup across all modules with AI.
**Topics:**
- The DI rules as constraints: per-module Hilt @Module, scope matching, @Binds vs @Provides
- AI-generated Hilt modules: one @Module per Gradle module in `di/` package
- Scoping rules: Singleton for data/core, ViewModelScoped for features
- @Binds vs @Provides: when AI should use each (prefer @Binds)
- Multi-module DI: making sure all bindings are discoverable across modules
- Qualifier placement: in the module that defines the type
- Testing DI configuration: verifying all bindings resolve correctly
- Common AI mistakes: wrong scope, missing @InstallIn, placing modules in wrong Gradle module

### Chapter 9: Navigation, Errors, and Cross-Cutting Concerns
**File:** `09-navigation-errors.html`
**Goal:** Type-safe navigation, error handling, and other cross-cutting concerns.
**Topics:**
- The navigation rules: route constants in owning feature, type-safe routes, no raw strings
- AI-generated navigation: route definitions, NavHost setup, inter-feature navigation via :app
- Error handling rules: three-tier hierarchy (ApiResult → AppResult → feature-specific → UiError)
- AI-generated error transformation: at each layer boundary
- The network layer rules: CallAdapter for ApiResult, dual OkHttpClient, token authentication
- Package structure validation: AI checking that no forbidden dependencies exist
- Gradle rules: convention plugins, version catalog, KSP-only
- Cross-reference: "AI-Engineering Chapter 7 covers the full set of architecture rules. This chapter applies them to cross-cutting concerns."

### Chapter 10: Testing the Rewrite
**File:** `10-testing-rewrite.html`
**Goal:** Comprehensive testing using AI, following the testing rules.
**Topics:**
- The testing rules: unit tests dominate, fakes over mocks, JUnit 5, performance targets
- AI-generated test strategy: what to test first (domain → data → presentation → integration)
- ViewModel contract tests: testing state transitions and effects
- Repository tests with fakes: AI-generated fake implementations
- Domain use case tests: pure function testing
- Compose UI tests: screenshot tests with golden images
- The 128+ test target: how the recipes app achieved comprehensive coverage
- Test quality review: are AI-generated tests testing behavior or implementation?
- Cross-reference: "AI-Advanced Chapter 8 covers TDD with AI. AI-CodeReview Chapter 3 covers reviewing AI-generated tests."

### Chapter 11: The Integration Sprint
**File:** `11-integration-sprint.html`
**Goal:** Connecting all layers, resolving issues, and validating the rewrite.
**Topics:**
- Layer integration checklist: connecting domain → data → presentation → navigation
- Resolving cross-module dependency issues: AI-assisted compile error resolution
- Full test suite execution: running all 128+ tests and fixing failures
- Behavior comparison: original monolith vs rewritten app (feature parity verification)
- Performance comparison: is the rewritten app faster, slower, or the same?
- The integration sprint workflow: daily cycle of integrate → test → fix → repeat
- Handling edge cases AI missed: the "manual review" pass
- The final build: ProGuard, release mode, APK size comparison

### Chapter 12: Lessons From the Rewrite: Your Playbook
**File:** `12-lessons-playbook.html`
**Goal:** Retrospective and reusable playbook.
**Topics:**
- Rewrite retrospective: what worked, what didn't, what surprised you
- The reusable rewrite playbook: step-by-step guide for any app
- Rules library as a team asset: sharing architecture rules across projects
- Before/after code comparison: monolith vs clean architecture side by side
- Metrics: lines migrated, tests generated, review iterations, time saved
- Applying the playbook to other apps: customizing for iOS, web, backend
- Connecting to AI-Factory: "You've transformed an existing app. Now build one from zero."
- Your rewrite confidence score: what you can tackle now that you couldn't before
