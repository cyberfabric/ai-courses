# Building AI-Powered Features for iOS

## Project Description
An HTML course for iOS developers who want to ship user-facing AI features that users actually love. The reader knows Swift, SwiftUI, and iOS fundamentals, and has some awareness of AI tools — but hasn't shipped a production AI feature yet. They want to know **what** to build, **how** users should interact with it, and **how** to implement it properly.

This course is **product-focused** — it covers the full lifecycle from choosing the right AI approach, through UX design, to implementation, testing, and safe production deployment. It bridges the gap between "I can call an API" and "I shipped a feature that delights users."

The style is **"For Dummies"** — friendly, approachable, like a senior iOS dev who's shipped several AI features walking you through their playbook. Heavy on real user scenarios, UX patterns, and practical Swift/SwiftUI implementations.

**Companion course:** [iOS-OnDevice](../iOS-OnDevice/) covers the ML infrastructure (Core ML internals, model optimization, hardware acceleration, Create ML training). This course focuses on the **feature-building** angle. Cross-references are included where relevant.

## Language Rules
- All content is in **English**
- Tone: friendly, conversational, product-minded — like a colleague who's obsessed with building great user experiences
- Use real iOS examples: Swift code, SwiftUI views, API integrations, SPM packages
- Address: second person singular (you)
- When introducing a concept, always answer: "OK, but what does the user actually see?"
- Light humor is welcome — keep it engaging, not dry
- Use short paragraphs — walls of text kill understanding
- Use analogies from everyday apps and user experiences to explain AI patterns

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
- Where relevant, add cross-references to iOS-OnDevice chapters for deeper infrastructure topics.

## File Structure
```
iOS-AIFeatures/
  CLAUDE.md                                    — This file
  .claude/
    commands/
      generate-next-chapter.md                 — Skill for chapter generation
      create-memory-map.md                     — Skill for visual chapter summary generation
  chapters/
    index.html                                 — Landing page with navigation
    assets/
      style.css                                — Shared CSS with dark/light theme
    01-ai-ios-mindset.html                     — The AI-Powered iOS Mindset
    02-choosing-ai-stack.html                  — Choosing Your AI Stack on iOS
    03-ai-ux-trust.html                        — Designing AI UX That iOS Users Trust
    04-smart-text.html                         — Smart Text with Foundation Models
    05-chat-conversational.html                — In-App Chat & Conversational AI
    06-smart-search.html                       — Smart Search & Content Generation
    07-image-document.html                     — Image Understanding & Document Intelligence
    08-image-generation.html                   — Image Generation & Creative AI
    09-voice-audio.html                        — Voice & Audio Intelligence
    10-siri-app-intents.html                   — Siri, App Intents & System Integration
    11-personalization.html                    — Smart Personalization & Recommendations
    12-shipping-safely.html                    — Shipping AI Features on the App Store
```

## Progress Tracking
- [x] Chapter 1: The AI-Powered iOS Mindset
- [x] Chapter 2: Choosing Your AI Stack on iOS
- [x] Chapter 3: Designing AI UX That iOS Users Trust
- [x] Chapter 4: Smart Text with Foundation Models
- [x] Chapter 5: In-App Chat & Conversational AI
- [x] Chapter 6: Smart Search & Content Generation
- [x] Chapter 7: Image Understanding & Document Intelligence
- [x] Chapter 8: Image Generation & Creative AI
- [x] Chapter 9: Voice & Audio Intelligence
- [x] Chapter 10: Siri, App Intents & System Integration
- [x] Chapter 11: Smart Personalization & Recommendations
- [x] Chapter 12: Shipping AI Features on the App Store

## Instructions for /generate-next-chapter
When the user invokes `/generate-next-chapter`:
1. Read this CLAUDE.md and find the first chapter marked with `[ ]` in Progress Tracking
2. Read the "Chapter Details" section below for that chapter's topics
3. Read `chapters/assets/style.css` for available CSS classes
4. Read `chapters/index.html` for navigation template
5. Read the previous chapter (if any) for context and smooth transition
6. **Use WebSearch** to find the latest information about the iOS frameworks and APIs relevant to this chapter
7. Generate the HTML file in `chapters/` with full content (400-600 lines)
8. Update CLAUDE.md — mark the chapter as `[x]`
9. Update `chapters/index.html` — remove `pending` class from that chapter's card
10. Update navigation on the previous chapter if needed

## CSS Classes for Content
- `.product-pattern` — proven UX/product pattern for AI features (coral accent, unique to this course)
- `.user-story-box` — scenario from the user's perspective showing how a feature feels (amber accent, unique to this course)
- `.api-recipe` — step-by-step API integration recipe with code (green accent, unique to this course)
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
- **At least one `.product-pattern`** per chapter showing a proven UX pattern for AI features
- **At least one `.user-story-box`** per chapter showing how the feature feels from the user's perspective
- **At least one `.api-recipe`** per chapter with a step-by-step API integration
- **At least one `.exercise-box`** per chapter where the reader builds something tangible
- Keep code examples practical (Swift, SwiftUI, API calls — max 20-30 lines per snippet)
- Each chapter should end with a preview of how it connects to the next chapter
- Balance technical implementation with UX/product thinking — this is not just an API tutorial
- Every feature discussion should cover: what the user sees, how it works under the hood, and what can go wrong
- Use analogies from apps the reader uses daily (Photos, Mail, Safari, Maps, Messages)
- Where relevant, add cross-references to iOS-OnDevice chapters for deeper infrastructure topics

## Chapter Details

### Chapter 1: The AI-Powered iOS Mindset
**File:** `01-ai-ios-mindset.html`
**Goal:** Shift the reader's thinking from deterministic features (button tap → predictable result) to probabilistic features (input → AI inference → "best guess" result) and why this changes everything about how you design, build, and test — framed through Apple's privacy-first AI ecosystem.

**Topics:**
- The fundamental shift: traditional features are deterministic (2 + 2 = 4 every time), AI features are probabilistic (this photo is "probably" a cat with 94% confidence) — why this matters for your entire development approach
- Apple Intelligence as the platform: privacy-first, on-device, free inference — how Apple's approach shapes what you can build differently than other platforms
- What makes a great AI feature: invisible intelligence (Siri suggestions), augmented capability (Live Text), reduced friction (QuickType), proactive assistance (Maps ETA) — the four patterns
- The AI feature spectrum: from simple (autocomplete) to ambitious (conversational AI) — where to start and how to grow
- User expectations in 2026: iPhone users expect AI to be private, instant, and seamless — they've been trained by Apple Intelligence — the bar is high and the patience is low
- The "magic vs. useful" trap: impressive demos don't equal useful features — a 95%-accurate classifier that solves a real pain point beats a flashy chatbot nobody needs
- Privacy as competitive advantage: on-device processing means you can offer AI features that cloud-dependent competitors can't — health data, financial data, personal photos
- The build-vs-buy decision at a glance: Foundation Models (free, on-device, Apple-only), Core ML (custom models, on-device), Cloud APIs (powerful, costs money) — a preview of Chapter 2
- AI feature lifecycle on iOS: idea → prototype → TestFlight → iterate → ship → monitor → improve — how App Store review adds a unique dimension
- Common anti-patterns: "AI for AI's sake" (adding AI where a picker would work), "the black box" (no explanation for AI decisions), "set and forget" (shipping AI without monitoring), "the over-promise" (marketing says "AI-powered" but the feature is a keyword match)
- Real-world case studies: how iOS apps use AI — Siri, Photos Memories, Live Text, Mail suggestions, Safari summaries, third-party apps like Signeasy (contract insights), Dark Noise (AI soundscapes), and Capture (smart categorization)
- Exercise: audit 5 apps on your iPhone, identify their AI features, rate each on usefulness (1-5) and trustworthiness (1-5), and identify what UX patterns make the good ones work

### Chapter 2: Choosing Your AI Stack on iOS
**File:** `02-choosing-ai-stack.html`
**Goal:** Give the reader a clear decision framework for choosing between Foundation Models, Core ML, Vision, Cloud APIs, and hybrid approaches — covering cost, latency, privacy, capability, and device support.

**Topics:**
- The four paths on iOS: Foundation Models (free ~3B LLM, on-device), Apple frameworks (Vision, NLP, Speech — free, on-device), Core ML (custom models, on-device), Cloud APIs (Gemini, OpenAI, Claude — powerful, costs money) — each has a sweet spot
- Foundation Models framework deep look: what it can do (text generation, classification, summarization, structured output), device requirements (iPhone 15 Pro+, M1+), the free inference advantage that changes the economics
- Apple's built-in intelligence: Vision (OCR, document understanding, face detection), Natural Language (entities, sentiment, embeddings), SpeechAnalyzer (speech-to-text), Sound Analysis — free, on-device, no model management
- Cloud APIs in 2026: OpenAI, Gemini, Claude — pricing models, capabilities, when on-device isn't enough (complex reasoning, large context windows, photorealistic image generation)
- The decision matrix: latency requirements (autocomplete <100ms = on-device only), privacy sensitivity (health data = on-device only), cost at scale (Foundation Models = $0 per inference vs Cloud at $0.01/request), device coverage (Foundation Models needs A17 Pro or later)
- Cost modeling for iOS apps: Foundation Models = $0 per inference — the economics are transformative compared to cloud APIs at 100K DAU × 3 requests/day
- Device compatibility reality: Foundation Models needs iPhone 15 Pro or later — what about older devices? Graceful degradation strategies, fallback to Vision/NLP frameworks, or cloud API fallback
- Private Cloud Compute: when Foundation Models can't handle a task on-device, Apple routes to its secure cloud infrastructure — same privacy guarantees, larger models, transparent and auditable
- The hybrid architecture: on-device for fast/private tasks (text classification, image preprocessing), cloud for heavy tasks (complex reasoning, large-context generation) — how to build the routing layer in Swift
- API key security on iOS: why hardcoding API keys in the IPA is a security disaster — using your own backend as a proxy, App Attest for abuse prevention, Keychain storage patterns
- Cross-reference: for deeper Core ML model deployment and optimization, see iOS-OnDevice Chapters 3, 8, and 11
- Exercise: pick an AI feature you want to build, create a decision matrix comparing Foundation Models vs Vision framework vs Cloud API — estimate cost, latency, privacy impact, and device coverage for each approach, then pick the winner and justify your choice

### Chapter 3: Designing AI UX That iOS Users Trust
**File:** `03-ai-ux-trust.html`
**Goal:** Master the iOS-specific UX patterns that make AI features feel trustworthy, transparent, and delightful — covering SwiftUI streaming, Apple HIG alignment, trust signals, progressive disclosure, and accessibility.

**Topics:**
- The trust equation on iOS: Apple users expect premium, polished AI experiences — errors feel worse on a $1000 device — how to earn trust fast and how to lose it in one bad interaction
- Loading states for AI in SwiftUI: the three phases — initiating (ProgressView with contextual text), processing (streaming tokens with smooth animation), completing (result reveal with transition) — never leave users staring at a spinner with no context
- Streaming responses in SwiftUI: building a token-by-token text reveal using AsyncSequence — the ChatGPT-style typing effect adapted for SwiftUI's declarative model with proper state management
- Apple HIG for AI: how Apple designs AI interactions (subtle, integrated, user-controlled) — Writing Tools as the gold standard of AI UX, how to match that quality in your own features
- Confidence communication: when and how to show confidence — high confidence (just show the result), medium confidence (show with a subtle "AI suggested" badge), low confidence (show multiple options and let the user pick) — following Apple's pattern from Siri suggestions
- The "AI suggested" pattern: labeling AI-generated content so users know what came from AI vs what they created — Mail's suggested replies, Safari's suggested searches
- User control and override: every AI feature needs an escape hatch — dismiss, edit, undo, "not helpful" feedback, manual fallback — users must always feel in control
- Error communication: "I'm not sure" is better than a wrong answer — when the AI should refuse, ask for clarification, or show "no results" instead of hallucinating garbage
- Feedback loops: thumbs up/down, "was this helpful?", implicit signals (did the user accept the suggestion or dismiss it?) — collecting data to improve without annoying the user
- Accessibility for AI features: VoiceOver announcements for dynamic AI content, reduce motion for streaming animations, Dynamic Type support for AI-generated text, focus management after AI results load
- Progressive disclosure: start simple (one-tap AI action) → offer more (customize the AI's behavior) → power user (advanced settings) — don't overwhelm with options on day one
- Dark patterns to avoid: AI features that manipulate (fake urgency from AI), deceive (presenting AI opinions as facts), or trap (no way to turn off AI suggestions) — Apple's App Store review will reject these
- Exercise: design the complete UX flow for an "AI email reply" feature in SwiftUI — sketch (or describe) every state: empty, loading, streaming, results, error, user edit, and feedback — include confidence indicators and override options

### Chapter 4: Smart Text with Foundation Models
**File:** `04-smart-text.html`
**Goal:** Build text intelligence features using Apple's Foundation Models framework — structured output with @Generable, Writing Tools integration, classification, and summarization.

**Topics:**
- Foundation Models 101: importing the framework, creating a LanguageModelSession, generating your first text response — the "hello world" of on-device AI on iOS
- The @Generable macro: defining Swift structs that the model fills — turn unstructured text into typed data (extract meeting details, classify support tickets, parse recipes into ingredients) — constrained decoding guarantees structural correctness
- @Guide constraints: restricting output values — rating must be "PG"/"PG-13"/"R", category must be from your enum — the model can only produce values you've allowed
- Building a "TL;DR" feature: user taps button → show loading animation → Foundation Models summarizes → stream response → display with "AI Summary" badge → allow expand to full text — the complete flow
- Writing Tools integration: how your app gets Apple's Rewrite/Proofread/Summarize for free by adopting standard text views — customizing with App Intents for app-specific writing actions
- Text classification in-app: sentiment analysis, content tagging, priority detection — @Generable with an enum output for reliable, type-safe categorization that never produces invalid values
- Prompt engineering for device-scale models: the ~3B parameter model is capable but not GPT-4 — writing prompts that work within its limits, being specific, providing examples in-prompt, keeping instructions clear
- Streaming text in SwiftUI: building a view that displays tokens as they arrive via AsyncSequence — smooth animation, proper text wrapping, handling markdown in streamed output
- Content quality control: the model may produce weak results for complex tasks — implementing "regenerate," prompt fallback strategies, escalating to cloud API for hard cases
- Caching generated content: storing summaries and classifications locally (SwiftData or UserDefaults) so the model doesn't re-process the same content — cache invalidation when source text changes
- Real-world examples: how Signeasy extracts contract insights, how Zoho summarizes notebooks, how Capture categorizes entries — all using Foundation Models on-device
- Exercise: build a "Smart Notes" feature — user writes a note, taps "Analyze," and sees: a 3-bullet summary, detected entities (people, dates, places), and a priority classification (high/medium/low) — all using @Generable with typed Swift structs

### Chapter 5: In-App Chat & Conversational AI
**File:** `05-chat-conversational.html`
**Goal:** Build a conversational AI interface in your iOS app — SwiftUI chat UI, multi-turn sessions with Foundation Models, tool calling, streaming responses, and making the chatbot actually useful.

**Topics:**
- When a chatbot makes sense: customer support, product discovery, guided workflows, learning/tutoring, data exploration — vs when it doesn't (simple settings, binary choices, anything a form does better)
- The anatomy of a chat UI in SwiftUI: ScrollView with LazyVStack for message history, TextField with send button, message bubbles (user vs AI with distinct styles), typing indicator, scroll-to-bottom behavior, keyboard avoidance
- Building chat message models: Swift structs for ChatMessage (role, content, timestamp, status), @Observable ViewModel for conversation state, persisting chat history with SwiftData
- Multi-turn sessions with Foundation Models: LanguageModelSession maintains conversation context automatically — no need to resend history manually, the framework handles the context window
- Streaming responses with AsyncSequence: LanguageModelSession returns partial responses as an AsyncSequence — collecting tokens as they arrive, updating the UI message bubble in real time with SwiftUI animations
- Tool calling: implementing the Tool protocol — let the model call your app code ("Show me nearby restaurants" → model calls your search function → returns results in chat) — bridging conversation with app functionality
- System prompts (instructions): defining your chatbot's personality, knowledge boundaries, and response format — "You are a helpful recipe assistant. Only answer cooking questions." — making the AI stay in its lane
- Rich messages beyond text: rendering images, cards, buttons, and action chips in chat — using Swift enums with associated values for different content types in your message model
- On-device vs cloud chat: Foundation Models for private, free, offline chat; cloud APIs (OpenAI, Claude) for complex reasoning and larger context windows — the hybrid chat architecture with automatic routing
- Handling edge cases: empty conversations (greeting/onboarding message), very long conversations (session context limits), network errors for cloud mode (retry with partial response), offensive input (content filtering)
- Rate limiting and cost control: on-device is free but cloud fallback costs money — limiting cloud messages per session, showing usage indicators, implementing an offline-first approach
- Exercise: build a complete chat interface in SwiftUI — user sends messages, AI responds with streaming text via Foundation Models, conversation persists with SwiftData, and the AI has tool calling capability to check weather or search recipes

### Chapter 6: Smart Search & Content Generation
**File:** `06-smart-search.html`
**Goal:** Build intelligent search features and AI-powered content generation — semantic search with embeddings, autocomplete, content drafting, and template-based generation.

**Topics:**
- Beyond keyword matching: why traditional search fails — user types "that blue jacket from last week" and gets zero results because no item is literally named "that blue jacket from last week" — semantic search understands intent
- Text embeddings on iOS: using NLEmbedding for semantic similarity — "happy" and "joyful" have similar vectors, "happy" and "socket wrench" don't — the foundation of semantic search on Apple platforms
- Building a local search index: embedding your app's content (product names, article titles, user notes) with NLEmbedding, storing vectors locally, and searching by cosine similarity — no cloud APIs needed
- Cloud-powered semantic search: using OpenAI Embeddings or Gemini Embedding API when NLEmbedding isn't enough — batch-embed content on your server, search in real time from the app
- Autocomplete that predicts intent: showing suggestions as the user types — combining prefix matching (fast, local) with Foundation Models prediction (AI-powered, understands context) — the two-tier approach
- Search UI in SwiftUI: the .searchable modifier with real-time suggestions, result cards with highlighted matches, empty states, loading states, "no results — try these" fallback suggestions
- Content generation with Foundation Models: drafting emails, writing replies, generating descriptions — the "AI Draft" pattern where AI creates a starting point the user can edit, not a final product
- Template-based generation: combining Foundation Models with @Generable structured templates — "Generate a product description" with typed fields (name, category, key features) that constrain the AI's output for consistency
- Token limits and chunking: handling long documents that exceed the model's context window — splitting into chunks, summarizing each chunk, then summarizing the summaries (map-reduce pattern)
- Personalized search: learning from what the user taps and searches for — building a lightweight on-device preference model that improves ranking over time without sending data to the cloud
- Cross-reference: for deeper NLEmbedding implementation and semantic similarity details, see iOS-OnDevice Chapter 5
- Exercise: build a semantic search feature for a recipe app with 100 recipes — embed all recipe titles and ingredients with NLEmbedding, implement real-time search that finds "something spicy with chicken" even though no recipe title contains those exact words

### Chapter 7: Image Understanding & Document Intelligence
**File:** `07-image-document.html`
**Goal:** Build features that understand images and documents — Vision framework OCR, RecognizeDocumentsRequest, visual search, photo library intelligence, and structured data extraction with Foundation Models.

**Topics:**
- Image understanding use cases on iOS: photo organization (Photos app), document scanning (Notes), accessibility (image descriptions for VoiceOver), content moderation, receipt parsing, business card scanning
- VNRecognizeTextRequest: extracting text from images — supports 26+ languages, handwriting recognition, confidence scores per character — building a smart OCR feature step by step
- RecognizeDocumentsRequest (iOS 26): structured document understanding — not just raw text but tables, lists, paragraphs, QR codes, emails, phone numbers, URLs — the next-generation document intelligence API
- Building a document scanner: camera capture → Vision for text extraction → Foundation Models for structured parsing → typed Swift data via @Generable — the "snap and understand" pipeline
- Smart OCR beyond raw text: Vision extracts text, Foundation Models structures it — "This is a receipt from Starbucks, total $5.40, 2 items" — combining OCR with @Generable for typed output (merchant, date, total, items array)
- Photo library intelligence: VNClassifyImageRequest for auto-categorization, VNGeneratePersonSegmentationRequest for portrait features, VNDetectFaceRectanglesRequest for people detection — building a smart gallery
- Visual search patterns: "find more photos like this" — using image features from Vision to group and search photos by visual similarity within the user's library
- Image preprocessing: handling HEIC format, Live Photos, orientation metadata, resizing for API input — iOS image format considerations before AI processing
- Batch processing photos: analyzing a photo library in the background — using Swift concurrency with TaskGroup, processing in batches to avoid memory pressure, storing results in SwiftData
- Privacy considerations: photos are deeply personal — on-device processing for everything (Vision + Foundation Models are both on-device), clear opt-in for any cloud analysis, never upload without explicit consent
- Accessibility: generating VoiceOver descriptions for images using Foundation Models — making photo features accessible to visually impaired users
- Cross-reference: for deeper Vision framework internals and request configuration, see iOS-OnDevice Chapter 4
- Exercise: build a "receipt organizer" feature — user photographs receipts, Vision extracts text, Foundation Models parses into structured data (merchant, date, total, items) via @Generable, display in an editable SwiftUI form with confidence indicators on each field

### Chapter 8: Image Generation & Creative AI
**File:** `08-image-generation.html`
**Goal:** Build creative AI features using Image Playground, Genmoji, and the ImageCreator API — programmatic image generation, creative workflows, and user-facing creative tools.

**Topics:**
- The creative AI landscape on iOS: Image Playground (on-device image generation), Genmoji (custom emoji), ImageCreator API (programmatic generation without system UI) — all free, all on-device, all private
- ImagePlaygroundSheet: presenting Apple's system image generation UI in your app — the simplest integration path, users create images with Apple's familiar interface in your app's context
- ImageCreator API: programmatic image generation without showing the system UI — generate images from text descriptions in your own custom workflow, control the generation parameters
- Image styles: animation, sketch, and the new ChatGPT-powered styles in iOS 26 — when to let users choose the style vs picking the right style for them based on context
- Genmoji integration: custom emoji that users create — automatically available in apps using standard text views, APIs for custom text engines, mixing multiple emoji with custom expressions
- Building a creative feature: "Generate a cover image for your note" — text description → Image Playground generates options → user picks → save to note — the complete creative workflow in SwiftUI
- Prompt design for image generation: how to guide the on-device model effectively — what descriptions work well and what doesn't with Apple's image generation models
- Combining text + image AI: Foundation Models generates a creative description → Image Playground creates an image from it — multi-model pipelines for creative features
- UX patterns for generative images: loading states (generation takes seconds, not milliseconds), presenting multiple options, editing/regenerating, attribution labels ("Created with Image Playground")
- Content safety: Apple's built-in safety filters for Image Playground — no harmful or explicit content generation possible — how this affects your feature design and what to communicate to users
- When Image Playground isn't enough: limitations (no photorealistic images, no specific real people or brands), when to consider cloud image APIs (DALL-E, Stability AI) as alternatives, and the privacy/cost tradeoffs
- Exercise: build an "AI Mood Board" feature — user describes a project theme in natural language, Foundation Models expands the description into 4 variations, Image Playground generates concept images for each, display in a SwiftUI grid with save/share functionality

### Chapter 9: Voice & Audio Intelligence
**File:** `09-voice-audio.html`
**Goal:** Build voice and audio AI features using SpeechAnalyzer, Sound Analysis, and Foundation Models — speech-to-text, voice-driven UX, sound classification, and multi-modal audio intelligence.

**Topics:**
- Voice AI on iOS in 2026: SpeechAnalyzer (WWDC 2025) replaces the old SFSpeechRecognizer — faster, more flexible, entirely on-device, supports long-form audio and distant microphone input
- SpeechAnalyzer setup: configuring capabilities per use case — close-mic dictation vs distant audio (meeting recording) vs long-form transcription — the modular approach with minimal boilerplate
- Real-time transcription UX: live speech-to-text with streaming partial results — building a transcription view in SwiftUI with visual waveform feedback, partial result highlighting, and final text display
- Voice-to-action pipeline: speech → SpeechAnalyzer transcription → Foundation Models structured extraction → app action — "Schedule lunch with Anna tomorrow at noon" → extracted calendar event via @Generable
- Sound classification: SNClassifySoundRequest for ambient awareness — 300+ sound categories (applause, sirens, dog barks, music) — building contextual features that react to the user's environment
- Audio pipeline architecture: AVAudioEngine → tap → buffer → SNAudioStreamAnalyzer — handling microphone permissions, background audio sessions, interruptions from phone calls
- Building a voice assistant: tap-to-speak button → SpeechAnalyzer transcribes → Foundation Models processes with tool calling → execute app actions → speak result with AVSpeechSynthesizer — the complete voice interaction loop
- Speech + text combo: transcribe a meeting → Foundation Models summarizes → extract action items with @Generable — the voice notes feature everyone wants to build
- Multilingual support: SpeechAnalyzer with automatic language detection, Foundation Models for translation between languages — building features that work across the user's languages
- Privacy and permissions: microphone is the most sensitive permission on iOS — providing clear context for the permission dialog, handling denial gracefully, emphasizing on-device processing for maximum privacy
- Battery and performance: continuous audio processing drains battery — strategies for power-efficient audio features (sampling rate, buffer size, when to stop listening)
- Cross-reference: for deeper SpeechAnalyzer and Sound Analysis framework internals, see iOS-OnDevice Chapter 5
- Exercise: build a "Voice Notes" feature — tap to record → live transcription displayed in real time → when done, Foundation Models generates a 3-bullet summary + extracts key topics + suggests a title — all processed on-device

### Chapter 10: Siri, App Intents & System Integration
**File:** `10-siri-app-intents.html`
**Goal:** Make your AI features discoverable and accessible system-wide through Siri, App Intents, Shortcuts, and Apple Intelligence integration — so users can access your features from anywhere.

**Topics:**
- Why system integration matters: your AI feature is most useful when users can access it from anywhere — Siri, Shortcuts, Spotlight, Lock Screen widgets, Action button — not just when your app is open
- App Intents framework 101: defining intents that expose your app's AI features to the system — the modern replacement for SiriKit with a much simpler API
- Making AI features Siri-accessible: "Hey Siri, summarize my notes in [YourApp]" — defining the AppIntent, handling parameters, returning results — voice-first design for AI features
- Shortcuts integration: letting users chain your AI features with other apps — "When I arrive at office → summarize unread emails → show in widget" — powerful automation with zero extra code once you define the intent
- The 12 App Intent domains: where your feature fits — Books, Camera, Spreadsheets, Mail, and more — choosing the right domain for maximum discoverability in Siri and Spotlight
- Writing Tools integration: your app gets Apple's Rewrite/Proofread/Summarize for free with standard text views — customizing with App Intents for app-specific writing actions beyond the defaults
- Spotlight integration: indexing your app's AI-generated content (summaries, classifications, extracted data) so it appears in system-wide search — making your AI work discoverable
- Widget intelligence: building widgets that show AI-generated insights — "Today's summary," "Smart suggestions," "Recent AI actions" — WidgetKit with on-device Foundation Models processing
- Focus modes and smart notifications: delivering AI-generated insights at the right time — using Focus filters to customize AI behavior per context (work mode shows project summaries, personal mode shows recipe suggestions)
- Live Activities for AI: showing real-time AI processing status on Lock Screen and Dynamic Island — "Analyzing your photos... 47/120 done" — the premium iOS touch that makes long AI tasks feel polished
- The "Use Model" Shortcuts action: a built-in Shortcuts action that lets users tap directly into Apple Intelligence models — how your app can participate in this ecosystem
- Exercise: add Siri and Shortcuts support to the "Smart Notes" feature from Chapter 4 — "Hey Siri, summarize my latest note in [YourApp]" and a Shortcut that auto-summarizes new notes and displays the result in a Home Screen widget

### Chapter 11: Smart Personalization & Recommendations
**File:** `11-personalization.html`
**Goal:** Build personalization features that learn from user behavior — custom LoRA adapters, on-device learning, recommendation engines, smart notifications, and proactive features that anticipate user needs.

**Topics:**
- Personalization on iOS: learning from the user's behavior to make AI features better over time — all on-device, all private, the Apple way — no user data ever leaves the phone
- Custom LoRA adapters: training specialized adapters for Foundation Models — when prompt engineering isn't enough, fine-tune the model for your specific domain (medical terminology, legal language, brand voice, specialized jargon)
- Adapter training toolkit: Apple's tools for creating ~160MB LoRA adapters — the PEFT (Parameter-Efficient Fine-Tuning) approach, training data requirements, evaluation metrics, deploying adapters to devices
- On-device learning with Create ML: using MLUpdateTask for personalizing classification models with user data — the model improves from individual usage without data leaving the device
- Recommendation engines: collaborative filtering (users like you also liked X), content-based (similar to what you've liked before), hybrid — building a simple but effective recommendation system for your app's content
- Smart notification timing: using user behavior patterns (when they typically open the app, their active hours, current context) to schedule notifications at optimal times — on-device behavior analysis
- The "proactive assistant" pattern: surfacing relevant information before the user asks — travel app shows boarding pass at airport, fitness app suggests workout at usual time, news app highlights followed topics at reading time
- Notification content personalization: varying notification text based on user preferences — Foundation Models for generating personalized notification copy that resonates with each user
- Behavior prediction: predicting what the user wants next based on patterns — "You usually check news at 8am" → proactive content card, "You order coffee every Monday" → pre-fill the order
- Engagement metrics that matter: open rate, dismissal rate, action rate, time-to-action, opt-out rate — measuring personalization quality, not just volume
- Avoiding the filter bubble: recommendation systems that only show what users already like create echo chambers — diversification strategies, serendipity injection, user control over recommendation intensity
- Cross-reference: for deeper adapter training and Create ML personalization details, see iOS-OnDevice Chapters 6 and 9
- Exercise: build a "Smart Feed" feature — track which content categories the user engages with (taps, time spent, saves), build a simple on-device preference model, rank content by predicted interest, show personalized recommendations with "Why this was recommended" explainers

### Chapter 12: Shipping AI Features on the App Store
**File:** `12-shipping-safely.html`
**Goal:** Ship AI features to production with confidence — App Store review, safety, privacy compliance, A/B testing, feature flags, metrics, and incident response for when things go wrong.

**Topics:**
- The AI safety checklist: before shipping any AI feature, validate five dimensions — content safety (can the AI produce harmful output?), cost safety (can a single user bankrupt your cloud API budget?), privacy safety (does user data stay where it should?), abuse safety (can bad actors exploit the feature?), App Store compliance (will Apple approve it?)
- App Store Review for AI features: Apple's policies on AI-generated content, requirements for disclosing AI usage to users, content policies for generative features, the review team's known focus areas — what gets rejected and why, with real examples
- Rate limiting for AI features: on-device is free but cloud fallback costs money — per-user limits (50 cloud requests/day), per-session limits (10/minute), global circuit breakers (pause when costs spike) — implementing limits and showing friendly limit-reached UI
- Content filtering: checking AI inputs and outputs for harmful content — Foundation Models' built-in safety filters, additional filtering for cloud APIs, handling edge cases (medical content that looks harmful but isn't)
- Prompt injection defense: users sending "Ignore your instructions and..." — input sanitization, instruction/data separation, output validation, monitoring for unusual AI responses — the security model for user-facing AI
- Feature flags for AI: rolling out AI features gradually with Firebase Remote Config or CloudKit — 1% → 10% → 50% → 100% rollout, instant kill switch, device-capability targeting (only enable Foundation Models features for iPhone 15 Pro+)
- A/B testing AI features: randomly assigning users to AI-enabled vs AI-disabled groups — measuring task completion time, error rate, feature engagement, and retention — also testing different prompts and model variants
- Defining success metrics for AI: task completion rate (did the user finish faster with AI?), acceptance rate (did the user use the AI suggestion?), edit distance (how much did the user change the AI output?), satisfaction (explicit feedback scores) — the AI quality scorecard
- Privacy compliance on iOS: Apple's privacy nutrition labels for AI features, App Tracking Transparency implications, GDPR/CCPA for any cloud AI processing, on-device as the ultimate privacy shield — the legal checklist
- Cost monitoring for cloud features: tracking API spend per feature, per user segment, per day — setting up alerts when costs exceed thresholds, implementing usage caps, forecasting costs at scale
- Incident response: what to do when your AI feature goes wrong — the AI produces harmful content, costs spike unexpectedly, users report bad experiences — the response playbook with kill switches and communication templates
- Model and API versioning: handling Foundation Models updates across iOS versions (26, 26.1, 27), cloud API deprecations (OpenAI, Gemini version changes), backward compatibility strategies, version pinning
- Exercise: create a complete shipping plan for one AI feature from a previous chapter — App Store review checklist, safety configuration, feature flag strategy, A/B test design with success metrics, monitoring dashboard specification, and incident response playbook — ready to present to your team lead before submitting to the App Store
