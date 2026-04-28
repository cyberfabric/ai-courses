# How AI Actually Works: A No-BS Guide for Developers

## Project Description
An HTML guide in English for developers who use AI tools daily but want to understand how AI actually works under the hood. The target audience is experienced developers (especially Android/mobile) who use Claude Code, Cursor, ChatGPT etc. but don't understand tokens, transformers, embeddings, or how models generate text.

The style is **"For Dummies"** — friendly, approachable, heavy on analogies and everyday examples. The reader is smart (they're a developer) but has zero background in ML/AI theory. No math formulas. Explain everything through intuition, analogies, and clear examples. Each chapter should produce at least one "aha moment" where something clicks.

## Language Rules
- All content is in **English**
- Tone: friendly, conversational, like a patient friend explaining things over coffee
- Use analogies from everyday life and software development to explain AI concepts
- **No math formulas** — use intuition, diagrams described in words, and analogies instead
- Address: second person singular (you)
- When introducing a concept, always answer: "OK, but what does this actually mean in practice?"
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

## File Structure
```
AI-Intro/
  CLAUDE.md                              — This file
  .claude/
    commands/
      generate-next-chapter.md           — Skill for chapter generation
  chapters/
    index.html                           — Landing page with navigation
    assets/
      style.css                          — Shared CSS with dark/light theme
    01-what-is-ai.html                   — What Is AI, Really?
    02-neural-networks.html              — Neural Networks Without the Math
    03-how-ai-learns.html                — How AI Learns
    04-tokens.html                       — Tokens: The Language AI Speaks
    05-transformer.html                  — The Transformer
    06-text-generation.html              — How Text Generation Actually Works
    07-temperature-and-friends.html      — Temperature, Top-p & Friends
    08-context-windows.html              — Context Windows & How Conversations Work
    09-embeddings.html                   — Embeddings: How AI Understands Meaning
    10-models-and-industry.html          — Types of AI Models & The Industry Map
```

## Progress Tracking
- [x] Chapter 1: What Is AI, Really?
- [x] Chapter 2: Neural Networks Without the Math
- [x] Chapter 3: How AI Learns
- [x] Chapter 4: Tokens: The Language AI Speaks
- [x] Chapter 5: The Transformer
- [x] Chapter 6: How Text Generation Actually Works
- [x] Chapter 7: Temperature, Top-p & Friends
- [x] Chapter 8: Context Windows & How Conversations Work
- [x] Chapter 9: Embeddings: How AI Understands Meaning
- [x] Chapter 10: Types of AI Models & The Industry Map

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
- `.analogy-box` — analogy/metaphor explanation (purple accent, unique to this course)
- `.aha-box` — "aha moment" insight (amber accent, unique to this course)
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
- **At least one analogy per major concept** — use `.analogy-box` for the best ones
- **At least one "aha moment" per chapter** — use `.aha-box` when something clicks
- **At least one concrete example** showing how the concept affects the reader's daily AI tool usage
- **No profession-tag needed** — this is conceptual, not role-based
- Keep code examples minimal and illustrative (Python snippets if needed, max 10-15 lines)
- When possible, connect concepts to tools the reader already uses (ChatGPT, Claude, Cursor)
- Each chapter should end with a brief preview of how this concept connects to the next chapter

## Chapter Details

### Chapter 1: What Is AI, Really?
**File:** `01-what-is-ai.html`
**Goal:** Clear the fog — define AI, ML, deep learning, and LLMs so the reader stops confusing them.
**Topics:**
- The buzzword soup: AI vs Machine Learning vs Deep Learning vs LLMs — nested circles
- A brief history: from rule-based systems to neural networks to transformers (timeline, not textbook)
- Why "AI" is a terrible name — it's really sophisticated pattern matching
- The three types of ML: supervised, unsupervised, reinforcement — with everyday examples
- Where LLMs fit in the bigger picture
- Why this matters to you: every tool you use (Claude Code, Cursor, ChatGPT) is built on these concepts
- The "AI is not thinking" realization — it's autocomplete on steroids
- Analogy: AI is like a chef who has read every cookbook but never tasted food
- Exercise: Map the AI tools you use daily to the concepts from this chapter

### Chapter 2: Neural Networks Without the Math
**File:** `02-neural-networks.html`
**Goal:** Build intuition for how neural networks work without a single equation.
**Topics:**
- The biological inspiration: real neurons vs artificial neurons (and why the analogy breaks down)
- A single neuron: inputs, weights, bias, activation — explained as a voting system
- Layers: why stacking neurons creates magic — the "abstraction ladder"
- What "deep" in deep learning means — it's just lots of layers
- Visualizing what layers learn: edges → shapes → concepts → meaning
- The "universal approximator" idea in plain language
- Why size matters: parameters, from thousands to billions
- GPT-4 has ~1.8 trillion parameters — what does that even mean?
- Analogy: a neural network is like a massive phone tree where each person makes tiny yes/no decisions
- How this connects to the LLMs you use: your prompt enters one end, text comes out the other
- Exercise: Draw (on paper) a tiny 3-layer network and trace how a simple input flows through it

### Chapter 3: How AI Learns
**File:** `03-how-ai-learns.html`
**Goal:** Explain training without math — how AI goes from random to useful.
**Topics:**
- The starting point: random weights — the AI knows literally nothing
- The training loop: predict → compare → adjust → repeat (millions of times)
- Loss functions: the "how wrong am I?" score — like a grade on an exam
- Gradient descent: walking downhill blindfolded — finding the lowest point
- Backpropagation: the blame game — which weights caused the error?
- Learning rate: too big = overshoot, too small = takes forever
- Overfitting: memorizing the exam vs understanding the subject
- Training data: garbage in, garbage out — why data quality matters more than model size
- Pre-training vs fine-tuning: learning to read vs learning to be a lawyer
- How long training takes: GPT-4 took months on thousands of GPUs (and millions of dollars)
- Why you can't just "retrain" when AI says something wrong
- Analogy: training an AI is like teaching someone to paint by showing them millions of paintings and saying "more like this, less like that"
- Exercise: Identify 3 things ChatGPT/Claude does well and 3 things it does poorly — explain why based on training

### Chapter 4: Tokens: The Language AI Speaks
**File:** `04-tokens.html`
**Goal:** Demystify tokenization — the reader should understand why token limits exist and what they mean.
**Topics:**
- AI doesn't read words — it reads tokens (and tokens aren't always words)
- What tokenization is: breaking text into chunks the model can process
- BPE (Byte Pair Encoding) explained simply: the most common patterns become tokens
- Why "strawberry" counting is hard: tokens split words in unexpected ways
- Token vocabularies: GPT uses ~100K tokens, each is a number
- Seeing tokens: tools to visualize how your text gets tokenized
- Why tokens matter for cost: you pay per token, not per word
- Context window = max tokens in a conversation (input + output combined)
- The token budget: how providers charge (input tokens are cheaper than output tokens)
- Why longer prompts cost more and take longer
- Tokens in different languages: English is efficient, other languages use more tokens
- Code tokenization: why code uses more tokens than you'd expect
- Analogy: tokenization is like how you read "don't" — you see one word, but it's actually two concepts (do + not)
- Exercise: Use a tokenizer tool to count tokens in 5 different prompts — find which uses more tokens and why

### Chapter 5: The Transformer
**File:** `05-transformer.html`
**Goal:** Explain the transformer architecture at an intuitive level — why it changed everything.
**Topics:**
- Before transformers: RNNs and their fatal flaw (they read one word at a time, forgetting earlier words)
- The 2017 paper: "Attention Is All You Need" — the title says it all
- Attention in plain English: "when processing each word, look at ALL other words to understand context"
- Self-attention: how "bank" means different things in "river bank" vs "bank account"
- The "queries, keys, values" concept: like a search engine inside the model
- Multi-head attention: looking at text from multiple perspectives simultaneously
- Positional encoding: how the model knows word order (since it sees all words at once)
- Why transformers are fast: they process all tokens in parallel (unlike RNNs that go one by one)
- Encoder vs decoder: understanding vs generating (BERT vs GPT)
- Why this matters: transformers made large language models possible
- Scaling: why bigger transformers get disproportionately better
- Analogy: reading a book with an RNN is like reading through a keyhole, moving one word at a time. A transformer reads the whole page at once and draws connections between every pair of words
- Exercise: Take a sentence with an ambiguous word and explain how attention helps resolve the ambiguity

### Chapter 6: How Text Generation Actually Works
**File:** `06-text-generation.html`
**Goal:** The reader should fully understand the next-token prediction loop — the core of how ChatGPT/Claude works.
**Topics:**
- The fundamental truth: LLMs predict ONE token at a time
- Autoregressive generation: generate token → append → repeat
- The probability distribution: for each position, the model scores EVERY possible next token
- Why it's not just "pick the most likely": that would be boring and repetitive
- Sampling: randomly picking from the top candidates (weighted by probability)
- The full loop: prompt → tokenize → feed through transformer → get probabilities → sample → repeat
- Why responses feel "creative": randomness is a feature, not a bug
- Why the same prompt gives different answers: sampling is random
- Why AI "hallucinates": it generates plausible-sounding tokens even when it doesn't "know" the answer
- The speed question: why generation is slower than understanding (it's sequential)
- Streaming: why you see text appear word by word (each token is generated one at a time)
- Analogy: imagine autocomplete on your phone, but instead of 3 suggestions, it has 100,000 — and it picks one randomly (favoring the more likely ones), then uses that to generate the next suggestion
- Exercise: Open ChatGPT, send the exact same prompt 3 times, compare the outputs — explain why they differ

### Chapter 7: Temperature, Top-p & Friends
**File:** `07-temperature-and-friends.html`
**Goal:** Demystify the generation parameters — the reader should know what to adjust and when.
**Topics:**
- Temperature: the "creativity dial" — low = predictable, high = wild
- How temperature works: it sharpens or flattens the probability distribution
- Temperature 0: always pick the most likely token (deterministic, boring, but reliable)
- Temperature 1: use the probabilities as-is
- Temperature >1: even unlikely tokens get a chance (creative but risky)
- Top-p (nucleus sampling): "only consider tokens that make up the top X% of probability"
- Top-k: "only consider the top K most likely tokens"
- Temperature vs top-p: which to use when (practical advice)
- Max tokens: setting output length limits
- Stop sequences: telling the model when to shut up
- Frequency penalty and presence penalty: reducing repetition
- Practical guide: best settings for code generation, creative writing, factual answers, brainstorming
- Why coding tools use low temperature: you want predictable, correct code
- Analogy: temperature is like the "adventure level" on a GPS — low means "fastest route," high means "surprise me with scenic detours"
- Exercise: If your AI tool allows it, try the same coding prompt with temperature 0 vs 1 — observe the difference

### Chapter 8: Context Windows & How Conversations Work
**File:** `08-context-windows.html`
**Goal:** Explain how chat-based AI maintains "conversation" — and why it's an illusion.
**Topics:**
- The fundamental truth: AI has NO memory between requests. None. Zero.
- How "conversations" work: the app sends the ENTIRE conversation history with each request
- System prompts: hidden instructions that come before your message
- The conversation stack: system prompt + conversation history + your latest message
- Context window sizes: 4K → 32K → 128K → 200K → 1M tokens — the evolution
- What happens when you hit the limit: summarization, truncation, or error
- Why AI "forgets" in long conversations: older messages get dropped
- The context window is like RAM, not a hard drive
- How coding tools manage context: file contents, project structure, CLAUDE.md
- Why "just make it bigger" isn't the answer: cost, speed, and attention degradation
- Long context vs good context: 1M tokens doesn't mean you should use 1M tokens
- KV cache: why long conversations use more GPU memory (simplified)
- Analogy: imagine you have amnesia and your friend texts you the ENTIRE conversation history every time they send a message. That's exactly how ChatGPT works
- Exercise: In a long chat, reference something from the very beginning — does the AI remember? Why or why not?

### Chapter 9: Embeddings: How AI Understands Meaning
**File:** `09-embeddings.html`
**Goal:** Explain embeddings intuitively — this is the bridge chapter to RAG and the AI Ecosystem course.
**Topics:**
- The problem: computers can't understand "similar" — "dog" and "puppy" are completely different strings
- The solution: turn words into lists of numbers (vectors) that capture meaning
- What an embedding looks like: a list of 768-3072 numbers
- The magic: similar meanings → similar numbers → close in "vector space"
- The classic example: king - man + woman ≈ queen (and why this blew people's minds)
- Visualizing high dimensions: imagine a 3D room but with 1000+ dimensions
- Sentence embeddings: same idea, but for entire paragraphs
- Cosine similarity: how to measure "how close are these two embeddings?" (the concept, not the formula)
- Practical use: semantic search (search by meaning, not keywords)
- Vector databases: databases designed to store and search embeddings fast
- Why this matters: embeddings are the foundation of RAG (Retrieval-Augmented Generation)
- The connection: this is HOW you'll teach AI about your specific data (covered in AI-Ecosystem)
- Analogy: embeddings are like GPS coordinates for meaning. "Dog" and "puppy" have similar coordinates. "Dog" and "democracy" are on different continents
- Exercise: Think of 5 word pairs that are semantically similar and 5 that aren't — would a keyword search find the similar ones?

### Chapter 10: Types of AI Models & The Industry Map
**File:** `10-models-and-industry.html`
**Goal:** Give the reader a complete mental map of the AI landscape — models, companies, open vs closed.
**Topics:**
- Text models (LLMs): GPT, Claude, Gemini, Llama, Mistral — what makes each different
- Image generation models: DALL-E, Midjourney, Stable Diffusion, Flux — how diffusion works (very simplified)
- Multimodal models: models that see, hear, AND write (GPT-4o, Gemini, Claude)
- Code models: Codex, CodeLlama, DeepSeek Coder — specialized vs general
- Speech models: Whisper (speech-to-text), TTS models (text-to-speech)
- Open source vs closed source: the great divide
  - Closed: OpenAI (GPT), Anthropic (Claude), Google (Gemini)
  - Open: Meta (Llama), Mistral, DeepSeek, Stability AI
  - What "open" really means: open weights ≠ open source ≠ open training data
- Model sizes: 7B, 13B, 70B, 405B — what the "B" means and why size matters
- The cost curve: how model size affects speed and price
- Running models locally vs in the cloud: tradeoffs
- The business of AI: APIs, subscriptions, enterprise contracts
- Who uses what: why startups love open source, enterprises love closed
- Analogy: think of AI models like cars — there are economy cars (7B), sedans (70B), and supercars (1T+). Some are proprietary (Tesla), some are open-source (Linux of cars). You pick based on your needs and budget
- Exercise: For 3 different project ideas, pick which model type and size you'd use and why
