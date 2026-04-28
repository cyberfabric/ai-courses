# AI Economics & Cost Engineering For Dummies

## Project Description
An HTML guide in English for developers who build and ship production AI features. Every production AI feature lives or dies by unit economics — token pricing, prompt caching, batch APIs, context compression, and model cascading are now first-class engineering concerns. This course treats cost as an engineering discipline, not an afterthought.

The primary audience is developers who already use AI APIs (Claude, OpenAI, Gemini) and have been surprised at least once by a bigger-than-expected bill. They know how to call the API — they need to learn the economics of calling it efficiently.

The style is **"For Dummies"** — friendly, analogy-heavy, approachable. Every chapter should produce at least one "so *that's* why my bill is so high" or "I had no idea I could save that much" moment.

## Language Rules
- All content is in **English**
- Tone: friendly, conversational, like a colleague who just finished optimizing a painful bill
- Use analogies from everyday life (grocery bills, gym memberships, bulk shipping, electricity tariffs) to explain cost concepts
- Address: second person singular (you)
- When introducing an optimization, always include a **before/after** cost example with real numbers
- Every number must be dated ("as of April 2026") — models and pricing drift fast
- Light humor is welcome — keep it engaging, not dry
- Use short paragraphs — walls of text kill understanding

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

## Data Freshness Rules — REQUIRED
This course's subject matter ages in weeks, not months. Generating any chapter from stale training data will produce wrong pricing, dead tools, and bad advice. Therefore:

- **Every chapter that cites specific pricing, model names, tool availability, GPU rates, or market-share figures MUST use WebSearch to verify each fact at the moment of generation.** Do not rely on training data for any number.
- **Before finalizing a chapter, run at least one WebSearch per external fact cluster** (e.g., one for Anthropic pricing, one for OpenAI pricing, one for Gemini pricing, one per named tool). Cite the source URL in an HTML comment immediately above the fact (e.g., `<!-- source: https://... as of 2026-04 -->`) or as a small footnote link at the end of the chapter.
- **If a search returns results older than 6 months for a volatile topic** (pricing, GPU rates, tool status), search again with a tighter date filter (e.g., append "April 2026" or "2026") before using the number.
- **Cascade stale facts across chapters.** When a WebSearch confirms a fact has changed since an earlier chapter was generated, also update any earlier chapter that referenced the stale fact — not just the new chapter.
- **Explicit 2026-sensitive topics that MUST be re-searched on every chapter run:**
  - Model pricing tables (Anthropic, OpenAI, Google, and any named model)
  - Cache TTLs, cache-write/read multipliers, and caching discounts
  - Batch API terms, discounts, and SLAs
  - Rate-limit structures and tiering (e.g., Perplexity T0–T5, Together AI dynamic tiering)
  - GPU hourly rates (H100/H200/B200/GB200) on-demand and spot
  - Observability tool status — **Helicone is in maintenance mode after the Mintlify acquisition in March 2026; verify current state before recommending it.**
  - OSS model availability (Llama 4 Scout/Behemoth, DeepSeek V3.2/R2, Qwen 4, Mistral)
- **When a fact cannot be verified within 3 WebSearch attempts**, omit it or mark it with a clearly-flagged "as of <date>, source unconfirmed" caveat rather than fabricating.

## HTML Validation Rules
- Always close tip-box divs with `</div>`, never `</tip>`.
- Validate all HTML tags are properly closed before completing a chapter.

## Project Structure Rules
- Always check the current working directory and respect the explicit project path provided by the user. Do NOT search parent directories or sibling projects unless explicitly asked.

## Cross-Reference Rules
- When generating multi-file series, ensure all cross-reference links between chapters are consistent. Use relative paths and verify link targets exist before finishing.

## File Structure
```
AI-Economics/
  CLAUDE.md                                — This file
  .claude/
    commands/
      generate-next-chapter.md             — Skill for chapter generation
      create-memory-map.md                 — Skill for visual chapter summary generation
  chapters/
    index.html                             — Landing page with navigation
    assets/
      style.css                            — Shared CSS with dark/light theme (emerald palette)
    01-why-cost-engineering-matters.html   — Why Cost Engineering Makes or Breaks AI Features
    02-tokens-as-money.html                — Tokens Are Money: The Cost Equation
    03-2026-pricing-landscape.html         — The 2026 Pricing Landscape
    04-prompt-caching.html                 — Prompt Caching: The 90% Discount You're Not Using
    05-batch-apis.html                     — Batch APIs: Half Price for Patient Workloads
    06-context-compression.html            — Context Compression: Spend Less by Sending Less
    07-model-cascading-routing.html        — Model Cascading & Routing: Right Model, Right Job
    08-rate-limits-capacity.html           — Rate Limits, Tiering & Capacity Planning
    09-cost-observability.html             — Cost Observability
    10-self-hosting-math.html              — Self-Hosting Math: When OSS + GPUs Beat APIs
    11-fine-tuning-roi.html                — Fine-Tuning ROI
    12-finops-for-ai.html                  — FinOps for AI: Budgets, Forecasts & the 2026 Playbook
```

## Progress Tracking
- [x] Chapter 1: Why Cost Engineering Makes or Breaks AI Features
- [x] Chapter 2: Tokens Are Money: The Cost Equation
- [x] Chapter 3: The 2026 Pricing Landscape
- [x] Chapter 4: Prompt Caching: The 90% Discount You're Not Using
- [x] Chapter 5: Batch APIs: Half Price for Patient Workloads
- [x] Chapter 6: Context Compression: Spend Less by Sending Less
- [x] Chapter 7: Model Cascading & Routing: Right Model, Right Job
- [x] Chapter 8: Rate Limits, Tiering & Capacity Planning
- [x] Chapter 9: Cost Observability: You Can't Optimize What You Can't See
- [x] Chapter 10: Self-Hosting Math: When OSS + GPUs Beat APIs
- [x] Chapter 11: Fine-Tuning ROI: When Custom Pays Off
- [x] Chapter 12: FinOps for AI: Budgets, Forecasts & the 2026 Playbook

## Instructions for /generate-next-chapter
When the user invokes `/generate-next-chapter`:
1. Read this CLAUDE.md and find the first chapter marked with `[ ]` in Progress Tracking
2. Read the "Chapter Details" section below for that chapter's topics
3. Read `chapters/assets/style.css` for available CSS classes
4. Read `chapters/index.html` for navigation template
5. Read the previous chapter (if any) for context and smooth transition
6. **Run WebSearch for every external fact** the chapter will cite (see Data Freshness Rules). Record each verified number and its source URL.
7. Generate the HTML file in `chapters/` with full content (400-600 lines), citing sources as HTML comments or footnote links
8. Update CLAUDE.md — mark the chapter as `[x]`
9. Update `chapters/index.html` — remove `pending` class from that chapter's card
10. Update navigation on the previous chapter if needed
11. If any searched fact contradicts a number used in an earlier chapter, update that earlier chapter too

## CSS Classes for Content
- `.cost-breakdown-box` — itemized line-by-line cost math ("100k prompts × $3/M = $300"); gold accent, unique to this course
- `.pricing-table-box` — wrapper for dense provider-comparison tables with highlighted columns; unique to this course
- `.roi-box` — two-column break-even / ROI scenarios (A vs B) with a verdict strip; unique to this course
- `.savings-callout` — pill-shaped inline highlight for "→ saves 60%" moments; also supports `.banner` modifier for full-width callouts; unique to this course
- `.prompt-example.good` / `.prompt-example.bad` — labeled good/bad examples
- `.comparison` — side-by-side comparison grid
- `.tip-box` — tips and advice
- `.warning-box` — warnings and cautions
- `.exercise-box` — hands-on exercises (emerald accent)
- `.checklist` — checklists with checkmarks
- `.highlight-box` — key messages (gradient emerald background)
- `.stats-grid` + `.stat-card` — statistics display
- `.tool-card` — tool description cards (icon + name + description)
- `.workflow-steps` + `.step` + `.step-arrow` — visual workflow pipeline
- `.theme-toggle` — theme switch button (in nav)

## Content Guidelines
- **At least one `.cost-breakdown-box`** per chapter showing itemized cost math with real 2026 numbers
- **At least one `.savings-callout`** per chapter highlighting a concrete % or $ savings
- **At least one `.roi-box`** per chapter OR one `.pricing-table-box`, depending on whether the chapter is comparing scenarios (ROI) or listing provider specs (pricing)
- **At least one `.exercise-box`** per chapter with a hands-on cost exercise (estimate, compute, compare)
- **At least one `.tip-box`** and **at least one `.warning-box`** per chapter
- Every cost/price claim must cite a 2026 source (WebSearch-verified) either inline or as a footnote
- Include concrete dollar numbers, not just percentages — developers think in dollars, not ratios
- Connect techniques to real API calls the reader has probably made
- Each chapter should end with a brief preview of how this connects to the next chapter

## Chapter Details

### Chapter 1: Why Cost Engineering Makes or Breaks AI Features
**File:** `01-why-cost-engineering-matters.html`
**Goal:** Convince the reader that cost is now a first-class engineering concern, and set up the mental model for the rest of the course.
**Topics:**
- Open with "the $10k surprise bill" story — a team that shipped a hit AI feature and then got a nasty invoice
- The gap between "using AI" and "using AI profitably"
- Why unit economics matter: a feature that costs $0.05/request can be viable; $5/request usually isn't, no matter how good it is
- What "FinOps for AI" is and why it's different from traditional cloud FinOps (latency tradeoffs, quality tradeoffs, stochastic costs)
- The five levers that control AI cost: model choice, caching, batching, compression, routing (the rest of the course maps to these)
- Why 2026 is a special moment: cost deflation is real but bills are still exploding because usage grows faster
- Who this course is for and what you'll be able to do after
- The mental model: treat every API call as a small purchase order — it has a price, a quality, and an alternative
- The three "cost discovery" questions to ask on day one of any AI feature: "what's the cost per request?", "what's the cost per user per month?", "what's the cost at 10x scale?"
- Course structure: 4 parts (foundations → levers → production → strategy), 12 chapters
- Exercise: Estimate the monthly cost of one AI feature you've built or used — input tokens, output tokens, requests/day. Compare to what you've been paying.

### Chapter 2: Tokens Are Money: The Cost Equation
**File:** `02-tokens-as-money.html`
**Goal:** Build intuition about tokens as the unit of cost, and expose the non-obvious asymmetries.
**Topics:**
- What a token is (practical definition, not deep dive — cross-reference AI-Intro if needed)
- The cost equation: `cost = input_tokens × input_price + output_tokens × output_price` (per request)
- Why input and output are priced separately — and why output is almost always more expensive (typically 4–5x)
- Reasoning tokens and "internal thinking" — the new 2026 budget variable for o-series and reasoning models
- Test-time compute pricing: reasoning models can use 2–10x more "internal" tokens than they output
- Why long context costs more than you think: attention scales quadratically in some ops, though providers mostly hide this behind flat per-token pricing
- The 200K vs 1M context pricing multiplier — some providers charge extra above a threshold, some don't
- Tokenization quirks: why "hello world" is ~2 tokens but a long URL might be 50
- Cheap ways to count tokens before calling the API (tiktoken, Anthropic's tokenizer endpoint, Gemini counter)
- The "token budget" mindset: deciding up-front how many tokens a feature is allowed to spend per call
- A worked example: a chat feature with 4000-token system prompt, 500-token user message, 800-token response — compute the per-call cost on three providers
- Exercise: Tokenize a real prompt you wrote this week. Compute the exact cost under current 2026 prices for three providers.

### Chapter 3: The 2026 Pricing Landscape
**File:** `03-2026-pricing-landscape.html`
**Goal:** Give the reader a mental map of the April 2026 pricing landscape across the three major providers, and teach them to read a price sheet.
**Topics:**
- **WebSearch required:** fetch current Anthropic, OpenAI, and Google pricing pages at generation time and put exact numbers in the chapter, dated
- Anthropic Claude family (April 2026): Opus 4.7, Sonnet 4.6, Haiku 4.5 — per-million input/output rates, cache rates, 1M context behavior
- OpenAI family (April 2026): GPT-5.4, GPT-5.4 Mini, GPT-5.1, GPT-4.1, o3, o4-mini — rates and positioning
- Google Gemini family (April 2026): Gemini 3 Pro (≤200K and >200K tiers), Gemini 2.5 Pro stable, Flash tiers — rates and context caching discounts
- The "cost per 1M tokens" mental shortcut — everyone prices per 1M, so learn to think in those units
- Reading a price sheet: seven things to always check (input rate, output rate, cache read/write rates, batch discount, context-size surcharge, rate limits, reasoning-token billing)
- How rates have deflated: GPT-4-level quality is now available at $0.05–$0.20 per 1M input tokens via small models
- Regional processing surcharges (+10% for data residency in some cases)
- The "cheapest credible model" for most tasks in 2026 and why it's usually enough
- Exercise: Pick a real API call from your logs. Price it on all three providers using current 2026 rates. Which is cheapest? Which would you actually use and why?
- Pricing table box showing all three providers side-by-side

### Chapter 4: Prompt Caching: The 90% Discount You're Not Using
**File:** `04-prompt-caching.html`
**Goal:** Teach the reader what prompt caching is, how each major provider implements it, and how to do the break-even math.
**Topics:**
- **WebSearch required:** confirm current cache TTLs, write multipliers, and read discounts for all three providers
- What prompt caching is: prefix-matching to skip recomputing the KV-cache for repeated context
- Anthropic: explicit `cache_control` markers, 5-minute default TTL and 1-hour extended TTL; cache-write costs ~1.25x (5-min) or 2x (1-hour) base input; cache-read costs ~0.1x base input
- OpenAI: automatic prefix caching (no markers), cache-write +25% on input, cache-read 90% discount; 5-minute TTL only (as of April 2026)
- Gemini: explicit context caching, 90% input discount on Gemini 2.5+; 75% on Gemini 2.0; minimum 1,024 tokens (Flash) or 4,096 tokens (Pro)
- The break-even math: for Anthropic 5-min TTL, one cache read already pays for the write; for 1-hour TTL, you need at least two reads
- What to cache: long system prompts, few-shot examples, retrieved documents, conversation history
- What NOT to cache: things that change per-request (user IDs, timestamps, randomized content)
- The cache-order rule: cached prefix MUST be identical — including whitespace — so put dynamic content last
- Semantic caching as a 2026 complement: embedding-similarity lookup to reuse responses across similar queries (Redis, Upstash, LangChain cache). Conservative threshold 0.85+, lower with monitoring
- Real numbers: a 20K-token system prompt called 1000 times per hour on Anthropic Sonnet — uncached cost vs cached cost
- Workspace-level isolation (Anthropic, since Feb 2026) — caches don't leak across workspaces
- Common bugs: near-misses where a space or newline invalidates the cache; forgetting to mark cache_control on a repeat prompt
- Exercise: Pick a prompt you call repeatedly. Compute uncached vs cached monthly cost. Estimate the break-even frequency for Anthropic 5-min vs 1-hour TTL.

### Chapter 5: Batch APIs: Half Price for Patient Workloads
**File:** `05-batch-apis.html`
**Goal:** Teach the reader when batch API fits, how to use it on each provider, and how to stack batch with caching.
**Topics:**
- **WebSearch required:** confirm current batch discount percentages and SLAs across providers
- What batch API is: submit many requests, get results within 24 hours, pay ~half price
- Anthropic Message Batches API: 50% discount, 24h SLA, one JSONL file in, one file out
- OpenAI Batch API: 50% discount, 24h SLA, JSONL upload via Files API
- Google Gemini Batch: 50% async discount, same pattern
- The "flat 50%" rule is industry standard across all three providers in 2026 — nobody is cheaper than anyone on batch
- When batch fits: overnight evaluation runs, backfills, embedding generation, daily reports, synthetic data generation, dataset labeling
- When batch does NOT fit: anything user-facing that needs sub-minute latency, anything with strict ordering requirements, anything with tight error-retry loops
- **Stacking batch + caching** — the crown jewel: combining 50% batch discount with 90% cached-read discount yields effective rates around 5% of list price on repeated-prefix workloads
- Architecture patterns: batch queues, status polling, result reconciliation, idempotency keys
- Operational gotchas: partial batch failures, rate-limit interactions, JSONL format edge cases, result ordering
- Cost-per-eval example: running 100K prompts through a classifier once per day — real-time vs batch vs batch+cached
- When a batch job has to become real-time: graceful fallback patterns
- Exercise: Identify one workload in your system that could move to batch. Compute the savings at current real-time cost. Add caching on top and recompute.

### Chapter 6: Context Compression: Spend Less by Sending Less
**File:** `06-context-compression.html`
**Goal:** Teach techniques for shrinking prompt size without losing quality.
**Topics:**
- **WebSearch required:** verify LLMLingua-2 status, recursive summarization tools, any 2026 entrants
- The insight: in most production prompts, 40–80% of the tokens contribute little to the answer
- LLMLingua-2 (2026): token-level compression with 3–6x speed over v1, 20x compression with <2% quality loss on many tasks; labels each token "keep" vs "drop"
- Recursive summarization: hierarchical summaries (summary-of-summaries) for long documents and long conversations
- "Living summaries" for chat: maintain an evolving summary instead of keeping full history, trigger re-summarization when over threshold
- DTCRS (Dynamic Topic-Cluster Recursive Summarization): query-aware chunk grouping for RAG
- Semantic chunking: break documents at topic boundaries, not fixed sizes
- Summarization + keyphrase extraction + semantic chunking combined → 5–20x compression, 70–94% cost savings in practice
- What you lose: verbatim recall (cite exact text), specific numbers, formatting fidelity — so choose compression level based on downstream task
- Where NOT to compress: contract review, code review for exact syntax, legal docs with clause-level semantics
- Measuring compression quality: before/after embedding similarity, human-rated sampling, downstream task accuracy
- Real savings example: a 50K-token RAG context compressed to 10K at Sonnet rates — monthly cost delta
- Tooling landscape: LLMLingua, LangChain/LlamaIndex built-in compressors, Pinecone's context-compression plugins
- Exercise: Take a long prompt you've built (>5K tokens). Apply a compression technique. Measure quality delta on 5 sample queries. Compute savings if you deployed it.

### Chapter 7: Model Cascading & Routing: Right Model, Right Job
**File:** `07-model-cascading-routing.html`
**Goal:** Teach the two core patterns for using cheaper models when they're enough, and premium models only when needed.
**Topics:**
- **WebSearch required:** verify OpenRouter, Martian, Not Diamond, RouteLLM, Unify status — anyone acquired/shut down
- Cascading: try a cheap model first, fall back to a premium model if the cheap one isn't good enough (confidence threshold, explicit self-eval, or downstream check)
- Routing: classify the request up-front and send to the right model based on task type (Haiku for extraction, Sonnet for reasoning, Opus for rare hard cases)
- OpenRouter (2026): unified endpoint to 500+ models from 60+ providers; billed at selected model rate; built-in auto-router (Not Diamond-powered)
- Martian: dynamic prompt-based routing; picks best model per request
- Not Diamond: routing/optimization SDK that integrates into your stack
- RouteLLM: academic/research framework for serving and evaluating routers
- The cascade decision: when the "router/cascade overhead" (classification call) is smaller than the savings from cheaper inference — typical break-even is 10–50x input/output asymmetry
- The 60–80% savings claim: where it's real (classification, extraction, FAQ, simple Q&A) and where it isn't (deep reasoning, agentic workflows)
- Cascading vs routing vs ensembling: when each wins
- Writing a simple classifier-router by hand — small LLM call to tag request → route based on tag
- Cascade failure modes: quality degradation you didn't notice, silently routing everything to the cheap model, confidence calibration drift
- Real example: a customer-support bot where 80% of tickets are FAQ-routable to Haiku, 20% need Sonnet — monthly bill before/after
- ROI box: Opus-everything vs Haiku-with-Sonnet-fallback scenario
- Exercise: Profile your app's request distribution. What % could be served by a cheaper model? Estimate savings.

### Chapter 8: Rate Limits, Tiering & Capacity Planning
**File:** `08-rate-limits-capacity.html`
**Goal:** Teach the reader how rate limits work in 2026 and how to plan capacity for production.
**Topics:**
- **WebSearch required:** confirm Anthropic/OpenAI/Google current tier structures and token-based limit norms
- Token-based vs request-based rate limits — 2026 has standardized on tokens because tokens reflect true compute
- The anatomy of a rate limit: requests per minute (RPM), input TPM, output TPM, all three matter
- Anthropic, OpenAI, Google usage tiers: spend-based progression, what unlocks at each level
- **Perplexity** T0–T5 leaky-bucket tiers based on cumulative spend
- **Together AI** dynamic rate limits (since Jan 2026): limits grow with sustained usage
- Why agents are the 2026 capacity wildcard: one agent iteration can do 30+ model calls behind a single "user action"
- Capacity planning: forecasting peak requests/second from user growth + agent multipliers
- Graceful degradation: when you hit the ceiling, shed load to a smaller model or a cached response
- Backoff strategies: exponential backoff, jittered retry, concurrency caps
- Handling 429s and 529s (Anthropic "overloaded"): what each means, how to react differently
- Requesting tier bumps: what providers look at, typical approval timelines
- Multi-provider redundancy for capacity: when it's worth the complexity
- Exercise: Pick one API endpoint in your app. Compute peak RPS today and at 10x growth. Check whether your current tier would hold.

### Chapter 9: Cost Observability: You Can't Optimize What You Can't See
**File:** `09-cost-observability.html`
**Goal:** Teach the reader which observability tools matter in 2026 and how to set up per-feature cost attribution.
**Topics:**
- **WebSearch required:** verify tool status — **Helicone is in maintenance mode after Mintlify acquired it in March 2026** — confirm current state; check Langfuse, Braintrust, Phoenix, TruLens, Langsmith, Portkey
- What to instrument: per-request cost, per-user cost, per-feature cost, cache hit rate, p50/p95/p99 latency, token counts, model used
- Langfuse (MIT open-source): hobby free (50K units/mo, 30-day retention), Core $29/mo (100K units, 90-day); customizable dashboards
- Helicone: **in maintenance after Mintlify acquisition March 2026** — verify state before recommending
- Braintrust: cloud-native, per-request cost breakdowns, tag-based attribution, strong for evals
- Phoenix (Arize): open-source, tracing + evals
- TruLens: open-source tracing + evaluation
- OpenLLMetry, Weave: additional tracing options
- Portkey: gateway pattern — logs + routing + retries in one hop
- **The gateway + eval-tool pattern** (2026 best practice): Portkey or Helicone in front for routing/logging, Langfuse or Phoenix for cost+latency+quality tracing
- Per-feature cost attribution via tags/metadata: tag every request with `feature=X`, group in dashboards
- Per-user cost attribution for B2B SaaS: tagging with `user_id`, alerting on outliers
- Cost alerts that don't wake you up: anomaly detection vs threshold alerts
- Cost dashboards that matter: weekly trendline, per-feature breakdown, cache hit rate, top-10 most expensive requests
- Instrumenting in code: the 5-line SDK wrapper pattern
- Exercise: Pick one AI feature. Add per-request logging that captures cost + latency + model + cache hit. Ship it, watch a week, identify the top 3 cost drivers.

### Chapter 10: Self-Hosting Math: When OSS + GPUs Beat APIs
**File:** `10-self-hosting-math.html`
**Goal:** Teach the reader the break-even analysis for self-hosting vs API use in 2026.
**Topics:**
- **WebSearch required:** confirm current GPU hourly rates (H100, H200, B200, GB200), OSS model lineup (Llama 4 Scout/Behemoth, DeepSeek V3.2, Qwen 4, Mistral Large 3)
- The self-hosting decision tree: privacy, latency, cost, control — which dimension is driving
- 2026 GPU pricing: H100 SXM5 ~$2.50/hr on-demand; H200 $3.50–$6/hr on-demand, $4.54/hr spot; B200 $6–$8.50/hr on-demand, $2.90/hr spot; GB200 NVL2 $10–$14/hr on-demand; RTX 4090 $0.55/hr
- OSS models you'd actually deploy in 2026: Llama 4 Scout (fits single H100, ~71GB VRAM), Llama 4 Behemoth (rumored 2T+ params, Q2 2026), DeepSeek V3.2 (aggressive pricing via API too), DeepSeek R2 (reasoning), Qwen 4
- Mixture-of-Experts cost advantage: DeepSeek V3 activates 37B of 671B params → ~85% compute reduction; factor this into capacity math
- Break-even calculation: fixed cost (GPU hours + ops overhead) / cost per 1M tokens vs API price per 1M
- The surprising 2026 conclusion: **because API prices have deflated so aggressively, self-hosting rarely wins on pure cost unless you're doing billions of tokens/month or have non-cost drivers**
- When self-hosting still wins: PII/privacy constraints, latency-critical on-prem, specialized fine-tuned models, guaranteed throughput
- Ops overhead you forget: GPU reliability, failover, batching infrastructure, quantization (GGUF/AWQ), serving frameworks (vLLM, SGLang, TensorRT-LLM, Ollama), on-call rotation
- Hybrid architectures: cheap OSS for the 90%, API for the hard 10%
- Speculative decoding (vLLM/SGLang/TensorRT-LLM 2026 default): 2–3x speed improvement; DeepSeek V3 ships native multi-token prediction
- Exercise: Pick your largest AI workload. Size the GPU cluster required. Compute monthly cost (GPUs + ops). Compare to current API bill. At what volume does self-hosting win?

### Chapter 11: Fine-Tuning ROI: When Custom Pays Off
**File:** `11-fine-tuning-roi.html`
**Goal:** Teach the reader the prompt → RAG → fine-tune decision tree and the cost math for each approach.
**Topics:**
- **WebSearch required:** verify current fine-tuning costs (LoRA, QLoRA, full fine-tune), provider-hosted fine-tuning prices, typical ROI benchmarks
- The three levers from cheapest to most expensive: prompt engineering → retrieval (RAG) → fine-tuning; try in that order
- When to fine-tune: narrow task, hundreds+ good examples, already hit quality ceiling with prompting + RAG, stable output format needed
- **When NOT to fine-tune: before product-market fit** — you'll re-train every time the task scope shifts
- LoRA on consumer GPU: 100–500 examples, 1–3 hrs, $0–$10 local or $20–$100 cloud
- QLoRA on H100: $10–$16 for 8–12 hours
- Full fine-tune on 8x H100s: $250–$510 for 24–48 hours
- Total project cost (data prep + training + eval): typically $20–$50 for optimized flows, $500+ for serious ones
- Provider-hosted fine-tuning: OpenAI and Google offer FT for specific models; Anthropic does not currently (verify)
- The 3.7x average ROI figure (top performers 10x+) — what drives the difference
- Runtime savings from fine-tuned small models: 10–100x cheaper inference per task than calling a premium API
- Eval infrastructure is the bottleneck — you can't know if fine-tuning worked without evals
- The "distill-from-Opus" pattern: use a big model to generate training data, fine-tune a small model
- Roi-box comparison: "always Opus" vs "fine-tuned Haiku/Llama 3.2 8B" for a classification task
- Exercise: Pick one task where you're using a premium model. Compute cost of generating 1K training examples + LoRA + ongoing inference. Compare to current monthly spend.

### Chapter 12: FinOps for AI: Budgets, Forecasts & the 2026 Playbook
**File:** `12-finops-for-ai.html`
**Goal:** Wrap the course with a practical playbook for managing AI spend as a discipline.
**Topics:**
- **WebSearch required:** verify current state of AI FinOps frameworks, any new 2026 pricing primitives (e.g., reasoning-token tiers, test-time compute pricing)
- Setting per-feature budgets: dollar cap per feature per month, alert at 80%, cut off or degrade at 100%
- Forecasting under cost deflation: if prices drop 50% per year, how do you plan? (Answer: usage grows faster than prices drop — usually)
- Unit economics discipline: cost per request, cost per user per month, cost per transaction vs revenue per those
- The 2026 structural tailwinds: MoE commoditization, speculative decoding as default (vLLM/SGLang/TensorRT-LLM), continuous cost deflation from competition
- The 2026 structural headwinds: agent traffic multiplication, reasoning-token growth, test-time compute premiums
- A 10-item production cost checklist (recap of the course):
  1. Per-request cost logged
  2. Per-feature tags applied
  3. Prompt caching enabled where applicable
  4. Batch API used for async workloads
  5. Context compressed where quality allows
  6. Model cascaded/routed by difficulty
  7. Rate-limit ceiling & capacity plan documented
  8. Cost dashboard with weekly trendline
  9. Budget alerts wired to Slack/PagerDuty
  10. Fine-tuning / self-hosting evaluated against API costs
- Organizational patterns: who owns AI cost (platform? each team?), how to do showback/chargeback in a B2B SaaS, how to run "cost reviews" quarterly
- Where AI pricing is headed (speculative, dated): reasoning-token tiers standardizing, streaming-price differentiation, compute-unit abstractions
- Final exercise: Run the 10-item checklist against one AI feature you own. For every item not in place, write a one-line action and a dollar estimate of the savings.
- Close the course: the mindset shift from "call the API and hope" to "engineer the economics"
