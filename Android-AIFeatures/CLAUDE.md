# Building AI-Powered Features for Android

## Project Description
An HTML course for Android developers who want to ship user-facing AI features that users actually love. The reader knows Kotlin, Compose, and Android fundamentals, and has some awareness of AI tools — but hasn't shipped a production AI feature yet. They want to know **what** to build, **how** users should interact with it, and **how** to implement it properly.

This course is **product-focused** — it covers the full lifecycle from choosing the right AI approach, through UX design, to implementation, testing, and safe production deployment. It bridges the gap between "I can call an API" and "I shipped a feature that delights users."

The style is **"For Dummies"** — friendly, approachable, like a senior Android dev who's shipped several AI features walking you through their playbook. Heavy on real user scenarios, UX patterns, and practical Kotlin/Compose implementations.

## Language Rules
- All content is in **English**
- Tone: friendly, conversational, product-minded — like a colleague who's obsessed with building great user experiences
- Use real Android examples: Kotlin code, Compose UI, API integrations, Gradle configs
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

## File Structure
```
Android-AIFeatures/
  CLAUDE.md                                    — This file
  .claude/
    commands/
      generate-next-chapter.md                 — Skill for chapter generation
  chapters/
    index.html                                 — Landing page with navigation
    assets/
      style.css                                — Shared CSS with dark/light theme
    01-ai-app-mindset.html                     — The AI-Powered App Mindset
    02-choosing-ai-approach.html               — Choosing the Right AI Approach
    03-ai-ux-trust.html                        — Designing AI UX That Users Trust
    04-smart-search.html                       — Smart Search & Autocomplete
    05-summarization.html                      — Summarization & Content Generation
    06-chat-conversational.html                — In-App Chat & Conversational UI
    07-image-understanding.html                — Image Understanding & Visual Search
    08-smart-camera.html                       — Smart Camera & Real-Time Processing
    09-notifications-recommendations.html      — Intelligent Notifications & Recommendations
    10-smart-forms.html                        — Smart Forms & Data Extraction
    11-ab-testing-metrics.html                 — A/B Testing & Measuring AI Features
    12-shipping-safely.html                    — Shipping AI Features Safely
```

## Progress Tracking
- [x] Chapter 1: The AI-Powered App Mindset
- [x] Chapter 2: Choosing the Right AI Approach
- [x] Chapter 3: Designing AI UX That Users Trust
- [x] Chapter 4: Smart Search & Autocomplete
- [x] Chapter 5: Summarization & Content Generation
- [x] Chapter 6: In-App Chat & Conversational UI
- [x] Chapter 7: Image Understanding & Visual Search
- [x] Chapter 8: Smart Camera & Real-Time Processing
- [x] Chapter 9: Intelligent Notifications & Recommendations
- [x] Chapter 10: Smart Forms & Data Extraction
- [x] Chapter 11: A/B Testing & Measuring AI Features
- [x] Chapter 12: Shipping AI Features Safely

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
- `.product-pattern` — proven UX/product pattern for AI features (blue accent, unique to this course)
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
- Keep code examples practical (Kotlin, Compose, API calls — max 20-30 lines per snippet)
- Each chapter should end with a preview of how it connects to the next chapter
- Balance technical implementation with UX/product thinking — this is not just an API tutorial
- Every feature discussion should cover: what the user sees, how it works under the hood, and what can go wrong
- Use analogies from apps the reader uses daily (Google Maps, Gmail, YouTube, Instagram)

## Chapter Details

### Chapter 1: The AI-Powered App Mindset
**File:** `01-ai-app-mindset.html`
**Goal:** Shift the reader's thinking from deterministic features (button click → predictable result) to probabilistic features (input → AI inference → "best guess" result) and why this changes everything about how you design, build, and test.

**Topics:**
- The fundamental shift: traditional features are deterministic (2 + 2 = 4 every time), AI features are probabilistic (this photo is "probably" a cat with 94% confidence) — why this matters for your entire development approach
- What makes a great AI feature: invisible intelligence (Gmail Smart Compose), augmented capability (Google Photos search), reduced friction (autofill), proactive assistance (Google Maps arrival prediction) — the four patterns
- The AI feature spectrum: from simple (autocomplete) to ambitious (conversational AI) — where to start and how to grow
- User expectations in 2026: users expect AI features to "just work" — they've been trained by Google, Apple, and Samsung — the bar is high and the patience is low
- The "magic vs. useful" trap: impressive demos don't equal useful features — a 95%-accurate classifier that solves a real pain point beats a flashy chatbot nobody needs
- Probabilistic UX: designing for uncertainty — what happens when the AI is wrong? (it will be wrong) — the core UX challenge unique to AI features
- The build-vs-buy decision at a glance: cloud AI APIs (fast to ship, ongoing cost), on-device models (free at scale, limited capability), hybrid (best of both, most complex) — a preview of Chapter 2
- AI feature lifecycle: idea → prototype → user research → iterate → ship → monitor → improve — how this differs from traditional feature development (hint: the "improve" step never ends)
- Common anti-patterns: "AI for AI's sake" (adding AI where a dropdown would work), "the black box" (no explanation for AI decisions), "set and forget" (shipping AI without monitoring), "the over-promise" (marketing says "AI-powered" but the feature is a keyword match)
- Real-world case studies: how popular Android apps use AI — Google Keyboard predictions, YouTube recommendations, Google Photos memories, Spotify Discover Weekly — what makes each one great (or annoying)
- Exercise: audit 5 apps on your phone, identify their AI features, rate each on usefulness (1-5) and trustworthiness (1-5), and identify what UX patterns make the good ones work

### Chapter 2: Choosing the Right AI Approach
**File:** `02-choosing-ai-approach.html`
**Goal:** Give the reader a clear decision framework for choosing between cloud APIs, on-device inference, and hybrid approaches — covering cost, latency, privacy, capability, and maintenance tradeoffs.

**Topics:**
- The three paths: cloud AI APIs (send data to a server, get results back), on-device models (run inference locally on the phone), hybrid (use on-device for speed/privacy, cloud for heavy lifting) — each has a sweet spot
- Cloud AI APIs in 2026: Gemini API, OpenAI API, Claude API, Azure AI, AWS Bedrock — the major players, pricing models (per-token, per-request, per-image), and what each does best
- On-device inference in 2026: TFLite, MediaPipe, ML Kit, Gemini Nano, Core ML (for cross-platform context) — when to go local
- The decision matrix: latency requirements (real-time camera = on-device, batch summarization = cloud), privacy sensitivity (health data = on-device, public content = cloud), cost at scale (1M users × $0.01/request = $10K/month vs free on-device), offline requirements
- Cost modeling for Android apps: calculating real API costs — a note-taking app with 100K DAU, each user summarizes 3 notes/day = 300K API calls/day — how to estimate and control costs
- Latency budgets: what users tolerate — autocomplete needs <100ms (on-device only), search results can take 500ms (cloud OK), document summarization can take 2-3 seconds (cloud fine with loading UI)
- Privacy and compliance: GDPR implications of sending user data to cloud APIs, App Store privacy labels, data processing agreements — when on-device is the only legal option
- The hybrid architecture: on-device for fast/private tasks (text classification, image preprocessing), cloud for heavy tasks (long-form generation, complex reasoning) — how to build the routing layer
- API key management on Android: why hardcoding API keys in the APK is a security disaster — using your own backend as a proxy, Firebase App Check for abuse prevention, token-based auth patterns
- Vendor lock-in considerations: abstracting the AI provider behind an interface — switching from OpenAI to Gemini shouldn't require rewriting your feature
- Fallback strategies: what happens when the cloud API is down, when the device can't run the model, when the user is offline — graceful degradation patterns
- Exercise: pick an AI feature you want to build, create a decision matrix comparing cloud vs on-device vs hybrid — estimate cost, latency, privacy impact, and offline capability for each approach, then pick the winner and justify your choice

### Chapter 3: Designing AI UX That Users Trust
**File:** `03-ai-ux-trust.html`
**Goal:** Master the UX patterns that make AI features feel trustworthy, transparent, and delightful — covering loading states, confidence communication, error handling, and user control.

**Topics:**
- The trust equation: AI features start with zero trust — users need to see correct results consistently before they rely on the feature — how to earn trust fast and how to lose it in one bad interaction
- Loading states for AI: the three phases — initiating ("Analyzing your photo..."), processing (streaming dots, progress percentage, skeleton screens), and completing (smooth result reveal with animation) — never leave users staring at a spinner with no context
- Streaming responses in Compose: building a token-by-token text reveal for LLM outputs — the ChatGPT-style typing effect that sets user expectations for generation time
- Confidence communication: when and how to show confidence — high confidence (just show the result), medium confidence (show with a subtle "AI suggested" badge), low confidence (show multiple options and let the user pick)
- The "AI suggested" pattern: labeling AI-generated content so users know what came from AI vs what they created — Gmail's "Smart Compose" subtle gray text, Google Photos' "AI-organized" albums
- User control and override: every AI feature needs an escape hatch — dismiss, edit, undo, "not helpful" feedback, manual fallback — users must always feel in control
- Error communication: "I'm not sure" is better than a wrong answer — when the AI should refuse, ask for clarification, or show "no results" instead of hallucinating garbage
- Feedback loops: thumbs up/down, "was this helpful?", implicit signals (did the user accept the suggestion or dismiss it?) — collecting data to improve without annoying the user
- Accessibility for AI features: screen reader announcements for dynamic AI content, motion reduction for streaming animations, alternative text for AI-generated images, focus management after AI results load
- Progressive disclosure: start simple (one-tap AI action) → offer more (customize the AI's behavior) → power user (advanced settings) — don't overwhelm with options on day one
- Dark patterns to avoid: AI features that manipulate (fake urgency from AI), deceive (presenting AI opinions as facts), or trap (no way to turn off AI suggestions)
- Exercise: design the complete UX flow for an "AI email reply" feature — sketch (or describe) every state: empty, loading, results, error, user edit, and feedback — include confidence indicators and override options

### Chapter 4: Smart Search & Autocomplete
**File:** `04-smart-search.html`
**Goal:** Build intelligent search features that understand user intent, not just keywords — semantic search, typo tolerance, query suggestions, and AI-powered result ranking.

**Topics:**
- Beyond keyword matching: why traditional search fails — user types "that blue jacket from last week" and gets zero results because no item is literally named "that blue jacket from last week" — semantic search understands intent
- Text embeddings 101: turning words into numbers (vectors) that capture meaning — "happy" and "joyful" have similar vectors, "happy" and "socket wrench" don't — the foundation of semantic search
- Building a local search index: embedding your app's content (product names, article titles, user notes) into vectors, storing them in a local SQLite database, and searching by vector similarity
- On-device embedding models: running a small sentence transformer (all-MiniLM, 22MB) on-device with TFLite for instant semantic search without API calls — the complete setup
- Cloud-powered semantic search: using Gemini Embedding API or OpenAI Embeddings for higher-quality search when on-device isn't enough — batch-embed content, search in real time
- Autocomplete that predicts intent: showing suggestions as the user types — combining prefix matching (fast, local) with semantic prediction (AI-powered, understands context) — the two-tier approach
- Typo tolerance and fuzzy matching: integrating Levenshtein distance with semantic understanding — "receipe" should find "recipes," "kotlin coroutenes" should find "Kotlin Coroutines"
- Search result ranking with AI: re-ranking keyword search results using an AI model that considers user history, recency, popularity, and semantic relevance — the hybrid ranking pattern
- Building the search UI in Compose: SearchBar with real-time suggestions, result cards with highlighted matches, empty states, loading states, "no results — try these" fallback suggestions
- Personalized search: learning from what the user clicks and searches for — building a lightweight preference model that improves ranking over time without sending data to the cloud
- Performance optimization: debouncing search queries, caching embeddings, pre-computing popular query results, lazy loading result details — keeping search fast on mid-range devices
- Exercise: build a semantic search feature for a recipe app with 100 recipes — embed all recipe titles and ingredients, implement real-time search that finds "something spicy with chicken" even though no recipe title contains those exact words

### Chapter 5: Summarization & Content Generation
**File:** `05-summarization.html`
**Goal:** Add AI-powered text summarization and content generation to your app — from TL;DR buttons to smart drafts, with proper UX for generated content.

**Topics:**
- Summarization use cases in Android apps: article TL;DR, email thread summary, meeting notes condensation, review highlights, notification batching ("5 messages from Anna about the project deadline")
- The summarization stack: on-device (Gemini Nano — fast, free, limited quality), cloud (Gemini Flash/Pro — higher quality, costs money), hybrid (on-device for short text, cloud for long documents)
- Building a "TL;DR" button: the complete flow — user taps button → show loading animation → call summarization API → stream response → display with "AI Summary" badge → allow expand to full text
- Prompt engineering for summarization: crafting prompts that produce consistent, useful summaries — "Summarize in 2-3 bullet points, focus on action items" vs "Summarize this" — the difference is night and day
- Content generation: drafting emails, writing replies, generating descriptions — the "AI Draft" pattern where AI creates a starting point the user can edit, not a final product
- Template-based generation: combining AI with structured templates — "Generate a product description" with fields (name, category, key features) that constrain the AI's output for consistency
- Streaming text in Compose: building a `LazyColumn`-based text renderer that displays tokens as they arrive — smooth scrolling, proper text wrapping, and handling markdown in streamed output
- Token limits and chunking: handling long documents that exceed the model's context window — splitting into chunks, summarizing each chunk, then summarizing the summaries (map-reduce pattern)
- Content quality control: detecting and filtering hallucinated content, adding source attribution, implementing "regenerate" for when the output isn't great, A/B testing different prompts
- Caching generated content: storing summaries and drafts locally so the AI doesn't regenerate the same content repeatedly — cache invalidation when source content changes
- Cost management: batching summarization requests, caching aggressively, using smaller models for simple tasks — keeping cloud API costs under control as your user base grows
- Exercise: build an "AI Notes" feature — the user writes a long note, taps "Summarize," and sees a 3-bullet-point summary with a streaming animation — implement with both Gemini Nano (on-device) and Gemini Flash (cloud) and compare quality and latency

### Chapter 6: In-App Chat & Conversational UI
**File:** `06-chat-conversational.html`
**Goal:** Build a conversational AI interface in your Android app — chat UI in Compose, conversation management, streaming responses, and making the chatbot actually useful.

**Topics:**
- When a chatbot makes sense: customer support, product discovery, guided workflows, learning/tutoring, data exploration — vs when it doesn't (simple settings, binary choices, anything a form does better)
- The anatomy of a chat UI in Compose: `LazyColumn` for message history, input field with send button, message bubbles (user vs AI), typing indicator, scroll-to-bottom behavior, keyboard handling
- Building chat message models: data classes for `ChatMessage` (role, content, timestamp, status), conversation state management with `ViewModel`, persisting chat history with Room
- Streaming responses with Kotlin Flow: calling the Gemini API or OpenAI API with streaming enabled, collecting tokens as they arrive, updating the UI message in real time — the complete coroutine pipeline
- Conversation memory: maintaining context across messages — sending conversation history with each request, managing the context window limit, summarizing old messages to fit more context
- System prompts that work: defining your chatbot's personality, knowledge boundaries, and response format — "You are a helpful recipe assistant. Only answer cooking questions. If asked about anything else, politely redirect." — making the AI stay in its lane
- Tool use / function calling: letting the AI trigger app actions — "Show me nearby restaurants" → AI calls a function that queries your database → returns results in chat — bridging conversation with app functionality
- Rich messages beyond text: rendering images, cards, buttons, carousels, and action chips in chat — `ChatMessage` with sealed class variants for different content types
- Handling edge cases: empty conversations (greeting/onboarding), very long conversations (performance with 500+ messages), network errors mid-stream (retry with partial response), offensive input (content filtering)
- Rate limiting and cost control: limiting messages per minute/hour, showing usage indicators, implementing free tiers with upgrade prompts — preventing a chatbot from bankrupting your API budget
- Offline chat: queuing messages when offline, syncing when back online, or using Gemini Nano for a limited offline chat experience
- Exercise: build a complete chat interface with Compose — user sends messages, AI responds with streaming text, conversation persists across app restarts, and the AI has a defined personality and knowledge boundary via system prompt

### Chapter 7: Image Understanding & Visual Search
**File:** `07-image-understanding.html`
**Goal:** Build features that understand images — automatic categorization, visual search ("find photos like this"), scene description, and AI-powered OCR that extracts structured data.

**Topics:**
- Image understanding use cases: photo organization (Google Photos), product visual search (Google Lens), accessibility (image descriptions for screen readers), content moderation, document digitization
- Image classification on-device: using ML Kit or a custom TFLite model to categorize photos — "food," "landscape," "document," "pet" — building an auto-tagging gallery feature
- Multimodal AI for image understanding: sending images to Gemini Pro Vision or GPT-4 Vision — "Describe this image," "What product is this?," "Extract the text from this receipt" — the most capable but most expensive approach
- Building visual search: embedding images into vectors (CLIP model), storing embeddings locally, and finding visually similar images — "find more photos like this one" without cloud APIs
- Scene description for accessibility: generating natural-language descriptions of photos for visually impaired users — on-device with ML Kit image labeling (basic) or cloud with Gemini Vision (detailed)
- Smart OCR beyond raw text: ML Kit text recognition extracts text, but AI can structure it — "This is a receipt from Starbucks, total $5.40, 2 items" — combining OCR with LLM parsing for structured data extraction
- Image preprocessing for AI: resizing, compression, format conversion (HEIC → JPEG), and orientation correction before sending to APIs — handling Android's image format zoo
- Building a "point and search" feature: user takes a photo → AI identifies the object → app searches for related products/information — the Google Lens pattern implemented in your app
- Batch processing photos: analyzing a photo library in the background — scheduling with WorkManager, processing in batches to avoid memory pressure, storing results in a local database
- Privacy considerations for image AI: photos are deeply personal — on-device processing for categorization (never send photos to cloud without consent), clear opt-in for cloud analysis, data retention policies
- Cost of image APIs: image analysis is expensive ($0.01-0.05 per image) — caching results, processing only new photos, using on-device for simple tasks and cloud only for complex ones
- Exercise: build a "photo organizer" that automatically categorizes photos from the gallery into groups (food, nature, people, documents, screenshots) using on-device ML Kit image labeling — display categories in a Compose grid with photo counts

### Chapter 8: Smart Camera & Real-Time Processing
**File:** `08-smart-camera.html`
**Goal:** Build real-time camera features — live object detection overlays, document scanning with edge detection, AR-style annotations, and barcode/QR scanning with contextual actions.

**Topics:**
- Real-time vs batch: camera features need <50ms per frame for smooth 20fps+ experience — this limits you to on-device models (cloud round-trip is too slow for live camera)
- CameraX + AI pipeline: setting up `ImageAnalysis` use case, converting `ImageProxy` to model input, running inference on a background thread, drawing results on a Compose `Canvas` overlay
- Live object detection: using MediaPipe Object Detector or ML Kit Object Detection for real-time bounding boxes — building a "point your camera and identify" feature with labeled overlays
- Document scanning with AI: edge detection to find document boundaries, perspective correction (crop and dewarp), ML Kit text recognition on the corrected image — building a clean document scanner
- Barcode and QR scanning: ML Kit BarcodeScanning for instant recognition — adding contextual actions (open URL, add contact, connect to Wi-Fi, show product info) based on barcode content type
- AR-style annotations: drawing labels, arrows, and info cards anchored to detected objects in the camera feed — coordinate transformation from model space to screen space in Compose
- Smart viewfinder features: auto-zoom on detected text (too small to read), highlight detected faces for photo framing, show grid overlay when document edges are detected
- Frame rate management: not every frame needs analysis — strategies for frame skipping (analyze every 3rd frame), async inference (process frame N while camera captures frame N+1), and adaptive rate (slow down analysis when results are stable)
- Camera permission UX: requesting camera permission with context ("We need your camera to scan documents"), handling permanent denial, showing preview even before AI model loads — the complete permission flow
- Memory and thermal management: continuous camera + ML inference generates heat — monitoring thermal state, throttling inference frequency when hot, releasing camera when app goes to background
- Testing camera features: testing without a physical camera — using `FakeCamera` in unit tests, pre-recorded video for integration tests, screenshot testing for overlay rendering
- Exercise: build a "smart scanner" camera feature — open the camera, detect documents in real-time with edge highlighting, capture on tap, dewarp the image, extract text with OCR, and display the structured result

### Chapter 9: Intelligent Notifications & Recommendations
**File:** `09-notifications-recommendations.html`
**Goal:** Build AI-driven notification timing, content recommendations, and behavior prediction — features that proactively help users rather than annoying them.

**Topics:**
- The notification paradox: notifications are powerful (direct user engagement) but dangerous (annoying users → uninstall) — AI can make notifications smarter by sending the right message at the right time to the right user
- Smart notification timing: using on-device behavior signals (when the user typically opens the app, their active hours, current context from Activity Recognition API) to schedule notifications at optimal times
- Notification content personalization: varying notification text based on user preferences — A/B testing "New recipes available" vs "3 chicken recipes you might like" vs "Your friend Anna shared a recipe" — AI-optimized copy
- Content recommendation engines: collaborative filtering (users like you also liked X), content-based (similar to what you've liked before), and hybrid — building a simple recommendation system for your app's content
- On-device recommendation: building a lightweight TFLite recommendation model that runs locally — training on anonymized aggregate data, personalizing with on-device user history, no data leaves the device
- Cloud recommendation APIs: using Vertex AI Recommendations, Firebase A/B Testing, or building your own with Gemini — when the recommendation problem is too complex for on-device
- Behavior prediction: predicting what the user wants next based on patterns — "You usually check weather at 7am" → proactive weather card, "You order coffee every Monday" → pre-fill the order — using simple ML or rule-based systems
- The "proactive assistant" pattern: surfacing relevant information before the user asks — travel app shows boarding pass at airport, fitness app suggests workout at usual time, news app highlights topics you follow
- Engagement metrics that matter: open rate, dismissal rate, action rate, time-to-action, opt-out rate — measuring notification and recommendation quality, not just volume
- Notification grouping and summarization: bundling 10 messages into "5 messages from Anna, 3 from project chat, 2 from news" — using AI to summarize grouped notifications into useful previews
- Avoiding the filter bubble: recommendation systems that only show what users already like create echo chambers — diversification strategies, serendipity injection, user control over recommendation intensity
- Exercise: build a "smart digest" notification feature — analyze the user's content consumption patterns (time of day, content categories), batch the day's updates into a single well-timed summary notification with AI-generated preview text

### Chapter 10: Smart Forms & Data Extraction
**File:** `10-smart-forms.html`
**Goal:** Build AI-powered form features — autofill from photos, receipt/document parsing, structured data extraction from unstructured input, and intelligent input validation.

**Topics:**
- The form problem: users hate filling out forms — AI can reduce friction by pre-filling, extracting data from photos, and intelligently validating input — every field the AI fills is a field the user doesn't type
- Photo-to-form: point the camera at a document (receipt, business card, ID, invoice) → AI extracts all fields → pre-fill the form — the "snap and done" pattern that eliminates manual data entry
- Receipt parsing pipeline: capture image → ML Kit OCR → raw text → LLM structured extraction → JSON with merchant, date, items, amounts, tax, total → populate expense form — the complete pipeline with code
- Business card scanning: extract name, title, company, phone, email, address from a photo — combining ML Kit text recognition with entity extraction or LLM parsing for structured output
- Intelligent autofill: going beyond Android's built-in autofill — using context (what screen the user is on, what they're doing) to suggest values — "You're adding a meeting → here are your recent contacts and usual meeting rooms"
- Natural language to structured data: user types "lunch with Anna tomorrow at noon at the Italian place" → AI extracts {event: "lunch", person: "Anna", date: "2026-03-31", time: "12:00", location: "Italian restaurant"} → pre-fill calendar event
- AI-powered input validation: going beyond regex — "Is this a valid address?" (AI geocoding check), "Does this email look right?" (pattern + domain check), "Is this description appropriate?" (content moderation)
- Form field suggestions: as the user fills one field, AI predicts others — entering "Starbucks" as merchant auto-suggests category "Coffee/Dining", entering a date auto-suggests the day of the week
- Handling extraction errors: AI will misread text and extract wrong values — UX patterns for showing extracted data with easy correction (tap to edit, swipe to reject), confidence highlighting (low-confidence fields highlighted in yellow)
- Offline form intelligence: caching extraction models and templates locally for offline use — expense tracking and document scanning that works on a plane or in areas with no signal
- Data privacy for extracted data: receipts and documents contain sensitive information — processing on-device when possible, encrypting extracted data, clear data retention policies
- Exercise: build an "expense capture" feature — user photographs a receipt, AI extracts merchant, date, total, and line items, displays in an editable form with confidence indicators on each field, and saves to a local Room database

### Chapter 11: A/B Testing & Measuring AI Features
**File:** `11-ab-testing-metrics.html`
**Goal:** Learn how to measure whether your AI features actually work — defining success metrics, A/B testing AI quality, monitoring costs, and making data-driven decisions about AI feature development.

**Topics:**
- Why AI features need different metrics: traditional features have binary success (button works or doesn't), AI features have quality gradients (the suggestion was helpful / somewhat helpful / useless / harmful) — you need new measurement approaches
- Defining success metrics for AI: task completion rate (did the user finish faster with AI?), acceptance rate (did the user use the AI suggestion?), edit distance (how much did the user change the AI output?), satisfaction (explicit feedback scores)
- The AI quality scorecard: accuracy (how often is the AI right?), latency (how fast?), cost (how much per user per month?), user satisfaction (NPS/CSAT for AI features), coverage (what % of requests get a useful response?)
- A/B testing AI features: randomly assigning users to AI-enabled vs AI-disabled groups — measuring task completion time, error rate, feature engagement, and retention — the controlled experiment approach
- A/B testing AI models: same feature, different models or prompts — testing Gemini Flash vs GPT-4o-mini for summarization, comparing prompt variants, measuring quality differences at scale
- Firebase A/B Testing setup: creating experiments, defining audiences, setting success events, running tests with statistical significance — the practical Firebase workflow for Android
- Prompt A/B testing: testing different system prompts or instruction variants — "You are a helpful assistant" vs "You are a concise, professional assistant" — measuring which produces better user outcomes
- Cost monitoring and budgeting: tracking API spend per feature, per user segment, per day — setting up alerts when costs exceed thresholds, implementing usage caps, forecasting costs at scale
- Quality monitoring in production: logging AI inputs/outputs (with privacy controls), sampling responses for human review, automated quality checks (response length, format compliance, toxicity scoring)
- User feedback systems: thumbs up/down buttons, "was this helpful?" prompts, implicit signals (accepted vs dismissed, edited vs used as-is) — building a feedback flywheel without survey fatigue
- When to kill an AI feature: feature costs too much, users don't engage, quality is too low, maintenance burden is too high — the honest assessment framework and how to sunset gracefully
- Exercise: design a measurement plan for one AI feature from a previous chapter — define 3 success metrics, design an A/B test with control and treatment groups, specify what Firebase events to log, and set cost alert thresholds

### Chapter 12: Shipping AI Features Safely
**File:** `12-shipping-safely.html`
**Goal:** Ship AI features to production with confidence — rate limiting, content filtering, abuse prevention, privacy compliance, feature flags, and incident response for when things go wrong.

**Topics:**
- The AI safety checklist: before shipping any AI feature, validate — content safety (can the AI produce harmful output?), cost safety (can a single user bankrupt your API budget?), privacy safety (does user data stay where it should?), abuse safety (can bad actors exploit the feature?)
- Rate limiting for AI features: per-user limits (50 AI requests/day), per-session limits (10 requests/minute), global limits (circuit breaker when API costs spike) — implementing in your backend and showing friendly limit-reached UI
- Content filtering: checking AI inputs and outputs for harmful content — using Gemini's built-in safety filters, implementing your own keyword and pattern checks, handling edge cases (medical content that looks harmful but isn't)
- Prompt injection defense: users sending "Ignore your instructions and..." — input sanitization, instruction/data separation, output validation, monitoring for unusual responses — the security model for user-facing AI
- Abuse prevention: detecting and blocking users who try to exploit AI features for spam generation, content farming, or data extraction — behavioral signals, rate patterns, and response to detected abuse
- Feature flags for AI: rolling out AI features gradually with Firebase Remote Config — 1% → 10% → 50% → 100% rollout, instant kill switch, device-capability targeting (only enable for devices with NPU)
- Privacy compliance for AI features: GDPR data processing for AI inputs, user consent for cloud processing, data retention policies, right to deletion, privacy labels in the Play Store — the legal checklist
- App Store compliance: Google Play policies on AI-generated content, disclosing AI usage to users, content policies for generative features, age-appropriate AI (COPPA considerations)
- Incident response: what to do when your AI feature goes wrong — the AI produces harmful content, costs spike unexpectedly, users report bad experiences — the response playbook with kill switches and communication templates
- Model and API versioning: handling API deprecations (OpenAI, Gemini version changes), model updates that change behavior, backward compatibility strategies, version pinning
- Monitoring and alerting: Crashlytics for AI-related crashes, custom Firebase events for quality metrics, cost dashboards, anomaly detection for unusual usage patterns — the production monitoring stack
- Exercise: create a complete safety plan for one AI feature — rate limiting rules, content filter configuration, privacy audit, feature flag strategy, incident response checklist, and monitoring dashboard design — ready to present to your team lead before shipping
