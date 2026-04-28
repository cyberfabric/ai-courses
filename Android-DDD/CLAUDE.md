# Domain-Driven Design For Android Engineers

## Project Description
An HTML guide in English for **senior Android engineers** who want to genuinely understand Domain-Driven Design (DDD) and apply it to real Android codebases. The reader has shipped non-trivial apps, knows Kotlin and the AndroidX stack, and has hit the wall of anemic models, god-ViewModels, and `:common` modules turning into `:everything`.

The bulk of the course teaches DDD itself — the Eric Evans / Vaughn Vernon canon — pitched at someone who already writes Android code daily. The last two chapters show how to use Claude Code (and AI in general) to introduce DDD into an existing Android codebase, including building a custom `/ubiquitous-language` slash command that emits a `UBIQUITOUS_LANGUAGE.md` file.

The style is **"For Dummies"** — friendly, approachable, heavy on analogies and worked examples. The reader is a strong engineer, but DDD has a reputation for being abstract; every chapter must produce at least one "oh, *that's* what they meant" moment by grounding the concept in a concrete Android scenario.

## Language Rules
- All content is in **English**
- Tone: friendly, peer-to-peer, like a colleague pair-programming with you
- Address: second person singular (you)
- Use Android-specific examples wherever possible: Gradle modules, Room, Retrofit, MVI, MVVM, coroutines, Flow, Hilt
- Whenever a DDD term first appears, give the canonical definition AND a one-sentence "what this looks like in Android"
- When introducing a pattern, include a **before/after** code snippet showing the improvement (use `.comparison` or two `.domain-box` blocks side by side)
- Light humor is welcome — DDD has a stuffy reputation; we're trying to make it feel useful, not academic
- Use short paragraphs — walls of text kill understanding
- Quote primary sources when relevant (Evans' "Blue Book," Vernon's "Red Book"), but never assume the reader has read them

## HTML Conventions
- Each chapter is a separate HTML file in `chapters/`
- Shared CSS: `assets/style.css` (relative path from chapters/)
- Each page includes:
  - `<nav class="top-nav">` with links to prev/next chapter, contents, and theme toggle button
  - `<header class="chapter-header">` with chapter number and title
  - `<main>` with content
  - `<footer>` with prev/next navigation
  - `<script>` at the end of body for theme toggle (localStorage)
- Encoding: UTF-8
- HTML5 doctype
- Meta viewport for responsive
- Target chapter length: **400-600 lines HTML**

## Content Generation Rules
- All generated chapters MUST meet the 400-line minimum on the FIRST attempt. Draft the FULL content in one pass targeting ~10% above the minimum (~440-460 lines). Verify with `wc -l` before finalizing.
- If under 400 lines, expand with substantive sections (worked examples, additional `.domain-box` snippets, a deeper Android case study, an exercise variation) — not filler, not line-by-line padding.
- If you end up within 10–15% above the minimum, LEAVE IT ALONE. Do not trim to fit a tighter range. Only trim if you're significantly over (e.g., >25% above), and then cut whole sections, not individual lines.
- Never pad content incrementally — produce complete, full-length content in one pass.

## HTML Validation Rules
- Always close `<div>` elements with `</div>` — never invent custom closing tags like `</tip>`, `</domain>`, `</context>`, etc.
- Validate all HTML tags are properly closed before completing a chapter (grep for unmatched/custom closing tags).

## Project Structure Rules
- Always check the current working directory and respect the explicit project path provided by the user. Do NOT search parent directories or sibling courses unless explicitly asked.

## Cross-Reference Rules
- When a chapter references another chapter, use a relative link to that chapter's filename (e.g., `<a href="03-bounded-contexts.html">Chapter 3</a>`).
- Verify link targets exist before finishing a chapter.
- The chapter footer's prev/next navigation must match the order in `chapters/index.html` exactly.

## File Structure
```
Android-DDD/
  CLAUDE.md                                              — This file
  .claude/
    commands/
      generate-next-chapter.md                           — Skill for chapter generation
      create-memory-map.md                               — Skill for visual chapter summary generation
  chapters/
    index.html                                           — Landing page with navigation
    assets/
      style.css                                          — Shared CSS with dark/light theme
    01-why-ddd-for-android.html                          — Why DDD for Android?
    02-ubiquitous-language.html                          — Ubiquitous Language
    03-bounded-contexts.html                             — Bounded Contexts
    04-context-mapping.html                              — Context Mapping
    05-subdomains.html                                   — Subdomains: Core, Supporting, Generic
    06-domain-events.html                                — Domain Events
    07-entities-and-value-objects.html                   — Entities and Value Objects
    08-aggregates.html                                   — Aggregates
    09-repositories-and-services.html                    — Repositories and Domain Services
    10-ddd-on-android-architecture.html                  — DDD on Android Architecture
    11-ubiquitous-language-skill.html                    — The /ubiquitous-language Skill
    12-refactoring-toward-ddd-with-ai.html               — Refactoring Toward DDD with AI
    maps/                                                — Visual memory maps (generated on demand)
```

## Progress Tracking
- [x] Chapter 1: Why DDD for Android?
- [x] Chapter 2: Ubiquitous Language
- [x] Chapter 3: Bounded Contexts
- [x] Chapter 4: Context Mapping
- [x] Chapter 5: Subdomains: Core, Supporting, Generic
- [x] Chapter 6: Domain Events
- [x] Chapter 7: Entities and Value Objects
- [x] Chapter 8: Aggregates
- [x] Chapter 9: Repositories and Domain Services
- [x] Chapter 10: DDD on Android Architecture
- [x] Chapter 11: The /ubiquitous-language Skill
- [x] Chapter 12: Refactoring Toward DDD with AI

## Instructions for /generate-next-chapter
When the user invokes `/generate-next-chapter`:
1. Read this CLAUDE.md and find the first chapter marked with `[ ]` in Progress Tracking
2. Read the "Chapter Details" section below for that chapter's topics
3. Read `chapters/assets/style.css` for available CSS classes
4. Read `chapters/index.html` for navigation template
5. Read the previous chapter (if any) for context and smooth transition
6. Generate the HTML file in `chapters/` with full content (400-600 lines, target ~440-460 on the first pass)
7. Update CLAUDE.md — mark the chapter as `[x]`
8. Update `chapters/index.html` — remove the `pending` class from that chapter's card
9. Update navigation on the previous chapter (add "next chapter" link if missing)

## CSS Classes for Content

### Course-specific boxes (use these regularly)
- `.domain-box` — domain-modeling examples (aggregate sketches, invariants, Kotlin model snippets); inner `.model-text` for monospace code
- `.language-box` — ubiquitous-language term definitions; use `.term` for the term, `.do-not-say` for "don't call it X" notes
- `.context-box` — bounded-context callouts (e.g., "in the Billing context, `Order` means..."); use `.context-name` for the context label
- `.android-box` — Android-specific notes (Gradle layout, Room/Retrofit mapping, MVI/MVVM hookup, coroutines/Flow); inner `.android-code` for monospace code

### Shared callouts
- `.tip-box` — tips and advice (blue accent)
- `.warning-box` — warnings, anti-patterns, common mistakes (red accent)
- `.exercise-box` — hands-on exercises the reader should do (bronze accent)
- `.highlight-box` — key takeaway / "the big idea" (gradient bronze background)

### Shared structures
- `.prompt-example.good` / `.prompt-example.bad` — labeled "good"/"bad" examples (use sparingly here; prefer `.comparison`)
- `.comparison` — side-by-side 2-column grid (use to show before/after refactors)
- `.checklist` — checklists with checkmarks (use `.checked` on completed items)
- `.stats-grid` + `.stat-card` — three-up stats display
- `.tool-card` — tool description cards (icon + name + description)
- `.workflow-steps` + `.step` + `.step-arrow` — visual workflow pipeline

### Theme
- `.theme-toggle` — theme switch button (in nav)

## Content Guidelines (per chapter)
- **At least one `.domain-box`** showing a real Kotlin domain model snippet
- **At least one `.language-box`** introducing a key term and "do not say" alternatives
- **At least one `.context-box` OR `.android-box`** anchoring the concept in either bounded-context or Android-specific terms
- **At least one `.exercise-box`** with a hands-on action the reader can take in their own codebase today
- **At least one `.tip-box` and one `.warning-box`** — DDD has subtle traps; flag them
- Worked code examples in **Kotlin**, idiomatic for modern Android (coroutines, Flow, sealed classes, value classes)
- Reference the Android stack the reader actually uses: Gradle modules, Room, Retrofit, Hilt, MVI/MVVM, Compose
- Each chapter ends with a brief "What's Next" preview connecting to the following chapter

## Chapter Details

### Chapter 1: Why DDD for Android?
**File:** `01-why-ddd-for-android.html`
**Goal:** Convince a senior Android dev that DDD is worth their time — by naming the pain they already feel and showing how DDD addresses it.
**Topics:**
- The pain: anemic data classes, business logic scattered across ViewModels, use cases, and "helper" objects
- Why mobile teams especially feel it: feature flags pile up, each feature owner picks their own model shape, the `:common` module turns into a god-module
- Eric Evans' core insight: software should mirror the *domain*, not the database or the screen layout
- The "Blue Book" (Evans) and the "Red Book" (Vernon): one-paragraph orientation to where DDD comes from
- Strategic vs tactical DDD — what each is, and what this course covers (both)
- When DDD is overkill: simple CRUD apps, prototypes, throwaway code, single-developer projects
- When DDD pays off: regulated domains (fintech, health), long-lived apps, multi-team codebases
- A real Android scenario: a "ride request" feature that ended up with six different `Order`-like types because nobody named the domain
- The 80/20 of DDD: ubiquitous language + bounded contexts give 80% of the value with 20% of the ceremony
- A roadmap of what you'll be able to do by chapter 12: extract aggregates, draw a context map, run `/ubiquitous-language` on your own repo
- Exercise: list three terms in your current codebase that mean different things to different people on your team

### Chapter 2: Ubiquitous Language
**File:** `02-ubiquitous-language.html`
**Goal:** Teach the single most valuable DDD practice and make it actionable today, with a concrete `UBIQUITOUS_LANGUAGE.md` template.
**Topics:**
- The translation tax: every meeting where the PM says "user," the dev says "account," QA says "profile," and the DB says "subscriber"
- What "ubiquitous" actually means: same word, same meaning, in chat, code, tickets, screens, the database, and the analytics events
- How to build one: pair a domain expert with an engineer, write down terms as they come up, refine on every PR
- Where it lives: a `UBIQUITOUS_LANGUAGE.md` at the repo root (alongside `CLAUDE.md`)
- What goes in it: the term, its definition, illustrative examples, "do not say" alternatives, related terms
- The naming compass: nouns become classes, verbs become methods, adjectives become flags or value objects
- Code smells that reveal a missing language: helper-class names like `UserManager`, `OrderProcessor`, `PaymentHelper`, `*Util`
- Refactoring exercise: rename one ambiguous class in your codebase using a domain term
- How language drift happens — and the rituals (PR templates, design docs) that prevent it
- Common Android-specific traps: "screen", "view", "fragment", "activity" leaking into domain code
- Worked example: a glossary entry for a `RidePickupRequest` term (with `.language-box`)
- A preview of how Claude Code reads `UBIQUITOUS_LANGUAGE.md` (full chapter on this in Part V)

### Chapter 3: Bounded Contexts
**File:** `03-bounded-contexts.html`
**Goal:** Teach the reader to spot, name, and draw bounded-context boundaries — the single most strategic DDD move.
**Topics:**
- What a bounded context is: a model + its language + its team + its boundary
- Why "one big model" fails at scale (Conway's law strikes again)
- The classic example: same word, two meanings — `Customer` in Sales is a lead; `Customer` in Support is a ticket-holder
- Identifying bounded contexts: linguistic boundaries, team boundaries, deployment boundaries
- The context map as a one-page diagram every engineer should be able to draw from memory
- Bounded contexts on Android: Gradle modules, feature modules, dynamic feature modules, KMP shared modules
- What lives inside a context vs at the edges
- Translation between contexts: ACLs (introduced here, full treatment in chapter 4)
- The "shared module" anti-pattern: how a `:common` module quietly turns into `:everything`
- Worked example: splitting a fintech app into Onboarding, Transactions, Investments, and Statements contexts
- Tools: a paper context map vs a Miro vs an automated context map from your build graph
- How to recognize you've drawn a boundary in the wrong place (signals: cross-context chatter, types ping-ponging through ACLs)
- Exercise: draw a context map of your current app on one page

### Chapter 4: Context Mapping
**File:** `04-context-mapping.html`
**Goal:** Equip the reader with the canonical context-relationship vocabulary so they can describe and design integrations precisely.
**Topics:**
- Why bounded contexts must talk: real apps cross context boundaries on every screen
- The Evans-canonical relationships and what each actually means in code
- **Anti-Corruption Layer (ACL):** the "Google Translate" between two contexts (your favorite weapon against legacy)
- **Shared Kernel:** a tiny shared model between two contexts (use sparingly — high coupling cost)
- **Customer-Supplier:** upstream team supports downstream team (most healthy default for inter-team work)
- **Conformist:** downstream team must accept upstream's model as-is (when you're the small guy)
- **Open Host Service & Published Language:** an API designed for other contexts to consume
- **Separate Ways:** when integrating costs more than duplicating
- **Big Ball of Mud:** the elephant — and what to do when you inherit one
- Drawing a context map: arrows, U/D labels, what those labels actually mean
- Android example: building an ACL between your domain layer and a third-party SDK that returns ugly DTOs
- When to redraw the map: signals your context relationships are stale (cross-team escalations, recurring outages, types ping-ponging through ACLs)
- Exercise: classify each cross-context dependency in your app

### Chapter 5: Subdomains: Core, Supporting, Generic
**File:** `05-subdomains.html`
**Goal:** Teach the reader to make strategic investment decisions — what to build, what to outsource, what to buy — using DDD's subdomain lens.
**Topics:**
- The strategic question: where does your team add the most value?
- **Core domain:** your competitive advantage, the part nobody else can copy
- **Supporting subdomain:** needed but not differentiating (e.g., reporting, admin tools)
- **Generic subdomain:** needed but completely undifferentiated (auth, email, payments rails)
- Why this matters: where to invest your senior engineers, what to outsource, what to buy off the shelf
- The trap of treating everything as core (everyone wants their feature to be core)
- A simple test: "if a competitor copied this exactly, would we lose?"
- Mapping subdomains to bounded contexts: not 1:1, but related
- Android example: a fitness app — workout planning is core; user profiles are supporting; auth and payments are generic
- How subdomain identification reshapes hiring, prioritization, and tech choices
- Common mistakes: choosing the most "interesting" domain instead of the most differentiating one; treating generic stuff as bespoke
- Exercise: classify each module in your `settings.gradle` as core, supporting, or generic

### Chapter 6: Domain Events
**File:** `06-domain-events.html`
**Goal:** Introduce domain events as a modeling tool — and event storming as the workshop format that produces them.
**Topics:**
- The shift in perspective: from "what *is*" (entities and tables) to "what *happens*" (events)
- Event storming: a 3-hour workshop that produces a domain map for an entire team
- The orange-sticky-note method: events first, then commands, then aggregates
- Events vs commands: tense matters (`OrderPlaced` is an event; `PlaceOrder` is a command)
- Events as first-class citizens in code: sealed Kotlin classes, immutable, named in past tense
- Event-driven on Android: lightweight in-process events using Flow / SharedFlow — no need for Kafka
- Persistence and replay: when domain events become your audit log
- Events crossing context boundaries: events as a "Published Language"
- Common pitfalls: events that are really CRUD updates in disguise; events with too much payload
- Worked example: modeling a checkout flow with events (`CartItemAdded`, `OrderPlaced`, `PaymentCaptured`, `OrderShipped`)
- Tools: domain event publishers, in-memory dispatchers; when (rarely) you need a real broker
- When NOT to use domain events: simple flows where direct method calls are clearer
- Exercise: pick one feature and list every domain event in past tense

### Chapter 7: Entities and Value Objects
**File:** `07-entities-and-value-objects.html`
**Goal:** Teach the central tactical-DDD distinction with deeply Kotlin-idiomatic examples — including why `data class` is a trap.
**Topics:**
- Identity vs equality: the central distinction in tactical DDD
- **Entity:** identity persists across changes (a `User`, an `Order`, a `RidePickupRequest`)
- **Value Object:** defined only by its attributes (a `Money(amount, currency)`, an `Address`, an `EmailAddress`)
- Why Kotlin `data class` is *not* automatically a value object: equality semantics are right, but mutability via `copy(...)` and uncontrolled construction are not
- Making true value objects in Kotlin: immutability, no IDs, side-effect-free methods, validation in the constructor
- Self-validation: throw on invalid construction (don't let invalid value objects exist)
- Why primitives obscure the model: `String email` vs `EmailAddress`, `Long userId` vs `UserId`
- Inline value classes (`@JvmInline value class`) for zero-allocation type safety
- Entity equality by ID, not by content; how to override `equals` and `hashCode` correctly for entities
- Common Android mistakes: passing primitives across screens, putting domain logic in DTOs, using `data class` for entities
- Worked example: refactoring `User(name: String, email: String)` toward `User(id: UserId, name: FullName, email: EmailAddress)` with validation
- When to keep things as primitives — and when not to
- Exercise: pick one anemic data class in your code and lift one of its fields to a value object

### Chapter 8: Aggregates
**File:** `08-aggregates.html`
**Goal:** Make the aggregate concept concrete and unscary — and arm the reader with rules of thumb for sizing them on a real app.
**Topics:**
- The aggregate: a cluster of entities + value objects with a *consistency boundary*
- The aggregate root: the only entry point; outsiders only hold a reference to the root
- The transaction rule: one aggregate per transaction (mostly — and why "mostly")
- Why this rule exists: avoiding N-way locking, scaling out, eventual consistency between aggregates
- Sizing aggregates: small is usually right (Vernon's "Effective Aggregate Design" rules)
- How to find aggregates: invariants tell you where the boundary is
- Cross-aggregate consistency: eventual via domain events
- Worked example: an `Order` aggregate with `LineItem` value objects (and why `LineItem` isn't its own aggregate)
- Loading aggregates: don't lazy-load across boundaries (a known footgun on Android with Room relations)
- Anti-patterns: huge aggregates, aggregates that span half the schema, lazy collections everywhere
- Aggregates and Room/SQLite: what the persistence model can and can't do; transactions in Room
- The Law of Demeter connection: only talk to the aggregate root, never reach inside
- Exercise: take one feature in your app and identify the aggregate root + boundary

### Chapter 9: Repositories and Domain Services
**File:** `09-repositories-and-services.html`
**Goal:** Clarify two of the most-misused DDD building blocks — repositories and domain services — with idiomatic Android implementations.
**Topics:**
- The repository: a collection-like interface for a single aggregate type (NOT a per-table DAO)
- What a repository hides: the persistence mechanism (Room, Retrofit, in-memory, KMP SQLDelight)
- Repository methods: `add`, `findById`, `save`, `remove` — and very few queries
- The "specification" pattern for complex queries that don't belong as named methods
- Why repositories return aggregates (not DTOs, not partial entities)
- **Domain services:** stateless operations that don't fit cleanly inside an entity or value object
- Examples: a `PriceCalculationService`, a `RouteFinderService`
- The difference between domain services, application services, and infrastructure services (and why the distinction matters)
- Anti-patterns: repository as DAO ("`OrderRepository.getOrdersByStatusAndDate(...)`"), domain service as god-object
- On Android: repository *interfaces* live in `:domain`; *implementations* live in `:data`; mock with fakes, not Mockito, in tests
- Worked example: an `OrderRepository` interface in `:domain` module, a Room-backed implementation in `:data`
- When you don't need a repository (small finite set of aggregates loaded once, like a settings store)
- Exercise: rewrite one of your existing DAO interfaces as a proper repository

### Chapter 10: DDD on Android Architecture
**File:** `10-ddd-on-android-architecture.html`
**Goal:** Show how the entire DDD vocabulary maps onto a modern multi-module Android codebase, end-to-end.
**Topics:**
- The big-picture layout: `:domain` (pure Kotlin/JVM, no Android), `:data`, `:feature-*`, `:app`
- Why `:domain` must not depend on Android: testability, reuse on Wear/Auto/desktop, KMP-readiness
- Mapping bounded contexts to Gradle modules (one module per context for the cleanest enforcement)
- DDD inside Clean Architecture: where entities, repos, and use cases sit
- DDD with MVI: state machines as transitions over a domain
- DDD with MVVM: ViewModels as application services orchestrating the domain — never as the domain itself
- Coroutines and Flow: domain methods returning `Flow<T>` vs returning values; threading rules
- Room as a persistence backend for aggregates: how to handle aggregate-internal relationships
- Retrofit and DTOs: the ACL pattern between API and domain (where mappers live)
- Kotlin Multiplatform: a sneak peek at when DDD really pays off (shared `:domain` across iOS/Android)
- The build-graph view: enforcing context boundaries with module dependencies (and detekt rules)
- Anti-patterns specific to Android: domain logic in Activities, business rules in `RecyclerView.Adapter`s, validation in `TextWatcher`s
- Exercise: sketch the module graph for your app and label each module with its DDD role

### Chapter 11: The /ubiquitous-language Skill
**File:** `11-ubiquitous-language-skill.html`
**Goal:** Teach the reader to build a custom Claude Code slash command that produces (and maintains) `UBIQUITOUS_LANGUAGE.md` for a real codebase.
**Topics:**
- The motivation: Claude Code reads a `UBIQUITOUS_LANGUAGE.md` at the repo root automatically (just like `CLAUDE.md`), and uses it on every task
- What a Claude Code "skill" really is: a slash command stored at `.claude/commands/ubiquitous-language.md`
- Anatomy of a skill: name, description, prompt body, optional frontmatter
- Designing the skill: input is a domain description or codebase scan; output is a structured `UBIQUITOUS_LANGUAGE.md`
- The output format: term, definition, examples, "do not say" alternatives, related concepts
- Hooking the skill into your workflow: invoke it once per bounded context; commit the result
- Sharing the skill across the team: commit `.claude/commands/ubiquitous-language.md` to the repo so every teammate gets the same skill
- How Claude Code uses `UBIQUITOUS_LANGUAGE.md` once it exists: memory loading, automatic context injection
- Keeping it in sync: a `/sync-ubiquitous-language` companion skill that reconciles the doc with the code on demand
- Demonstration: running the skill on a small Android project (a sample fintech app)
- Common mistakes: skill prompts that are too generic, not anchoring on real code, not committing the output
- Worked example: the actual file structure of `.claude/commands/ubiquitous-language.md` and a sample run

### Chapter 12: Refactoring Toward DDD with AI
**File:** `12-refactoring-toward-ddd-with-ai.html`
**Goal:** Walk through a realistic, end-to-end AI-assisted refactor of a legacy Android codebase toward a DDD-shaped architecture.
**Topics:**
- The starting point: a typical Android codebase with anemic data classes, god-ViewModels, and a `:common` module that shouldn't exist
- Step 1: Have Claude Code scan the repo and produce a context map (one prompt, structured output)
- Step 2: Generate a `UBIQUITOUS_LANGUAGE.md` per bounded context using the skill from chapter 11
- Step 3: Identify aggregates — prompt Claude to suggest where consistency boundaries should be, based on invariants in the code
- Step 4: Extract value objects — rename `String email` → `EmailAddress`, `Long userId` → `UserId` across the codebase, with Claude doing the find/rename
- Step 5: Move logic from ViewModels into the domain layer (and pull domain types into `:domain`)
- Step 6: Introduce repository interfaces; move Room/Retrofit code to `:data` implementations
- Verifying the refactor: existing tests as the safety net, Claude as the assistant generating new tests
- Limits of AI-driven DDD: humans still own the strategic decisions (subdomains, bounded-context boundaries)
- Pitfalls: blindly applying patterns, refactoring without tests, ignoring legacy constraints
- Workflow tactics: small commits, one aggregate at a time, review every diff, never let Claude touch two contexts in one PR
- Closing thoughts: why DDD + AI is more powerful than either alone — DDD gives you the vocabulary; AI gives you the throughput
