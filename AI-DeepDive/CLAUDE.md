# How AI Really Works: The Deep Dive

## Project Description
An HTML guide in English for developers who completed "How AI Actually Works" (AI-Intro) and want to go deeper. The target audience is experienced developers (especially Android/mobile) who now understand the WHAT of AI and want to understand the HOW — with real numbers, step-by-step walkthroughs, and simplified math.

This is the companion "deep dive" to AI-Intro's 10-chapter overview. The 10 original topics expand to **13 chapters** where dense topics (neural networks, transformers) get split into two chapters each, and one new topic (training at scale) is added.

The style is **"For Dummies" with numbers** — still friendly and approachable, still heavy on analogies, but now we actually show the computations. No calculus, no scary notation, no proofs. The reader traces through operations with pencil and paper and walks away understanding HOW things work, not just WHAT they do.

**Content approach (A+B):**
- **Level A** — Name the actual operations (dot product, softmax, matrix multiply) and explain what they do intuitively
- **Level B** — Show simplified numeric examples with small friendly numbers, step by step
- Every major concept gets BOTH layers: intuition first, then numbers, then takeaway

## AI-Intro Chapter Mapping

| AI-Intro Chapter | Deep Dive Chapter(s) |
|---|---|
| Ch 1: What Is AI, Really? | Ch 1: The AI Family Tree |
| Ch 2: Neural Networks Without the Math | Ch 2: Inside a Neuron + Ch 3: Layers & Signals |
| Ch 3: How AI Learns | Ch 4: Training Step by Step |
| Ch 4: Tokens | Ch 5: Tokenization Deep Dive |
| Ch 5: The Transformer | Ch 6: Attention + Ch 7: Full Transformer |
| Ch 6: Text Generation | Ch 8: From Prediction to Conversation |
| Ch 7: Temperature & Friends | Ch 9: Sampling Strategies |
| Ch 8: Context Windows | Ch 10: Context & KV Cache |
| Ch 9: Embeddings | Ch 11: Embeddings Geometry |
| Ch 10: Models & Industry | Ch 12: Training at Scale (new) + Ch 13: Architectures |

## Language Rules
- All content is in **English**
- Tone: friendly, conversational, like AI-Intro but one level deeper — "I promised no math, but these numbers are actually fun"
- Every numeric example must use small, friendly numbers (single digits where possible, max 2 decimal places)
- Always show the intuition BEFORE the numbers, and the takeaway AFTER
- Use tables liberally for showing step-by-step computations
- Address: second person singular (you)
- When showing a numeric walkthrough, use the pattern: "Here's what we're doing" → "Here are the numbers" → "Here's what that means"
- Light humor welcome — especially when math turns out to be simpler than expected
- Cross-reference AI-Intro chapters where appropriate: "In AI-Intro Chapter N, we used an analogy. Now let's see the actual numbers."
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
- Target chapter length: **~600 lines HTML** — do NOT cut content if the chapter is under 1000 lines. Quality and completeness matter more than a hard line limit.

## Content Generation Rules
- All generated chapters MUST meet the 400-line minimum on the FIRST attempt. Count lines before finalizing. If under 400 lines, expand sections with examples, diagrams, tips, and detailed explanations before presenting.
- Never pad content incrementally — produce complete, full-length content in one pass.
- Target ~600 lines, but do NOT cut content that's already generated if it's under 1000 lines.

## HTML Validation Rules
- Always close tip-box divs with `</div>`, never `</tip>`.
- Validate all HTML tags are properly closed before completing a chapter.

## Project Structure Rules
- Always check the current working directory and respect the explicit project path provided by the user. Do NOT search parent directories or sibling projects unless explicitly asked.

## Cross-Reference Rules
- When generating multi-file series, ensure all cross-reference links between chapters are consistent. Use relative paths and verify link targets exist before finishing.

## File Structure
```
AI-DeepDive/
  CLAUDE.md                                  — This file
  .claude/
    commands/
      generate-next-chapter.md               — Skill for chapter generation
      create-memory-map.md                   — Skill for visual chapter summary generation
  chapters/
    index.html                               — Landing page with navigation
    assets/
      style.css                              — Shared CSS with dark/light theme
    01-ai-family-tree.html                   — The AI Family Tree — A Deeper Look
    02-inside-a-neuron.html                  — Inside a Neuron — The Math That Isn't Scary
    03-layers-and-signals.html               — How Networks Think — Layers, Weights & Signals
    04-training-step-by-step.html            — Training Step by Step — Forward, Loss, Backward
    05-tokenization-deep-dive.html           — Tokenization Deep Dive
    06-attention-mechanism.html              — Attention Is All You Need
    07-full-transformer.html                 — The Full Transformer Architecture
    08-prediction-to-conversation.html       — From Prediction to Conversation
    09-sampling-strategies.html              — Sampling Strategies — The Numbers Behind Creativity
    10-context-and-kv-cache.html             — Context, Memory & the KV Cache
    11-embeddings-geometry.html              — Embeddings — From Words to Geometry
    12-training-at-scale.html                — How Models Are Actually Trained at Scale
    13-architectures-compared.html           — Model Architectures Compared
    maps/                                    — Visual memory maps (generated on demand)
```

## Progress Tracking
- [x] Chapter 1: The AI Family Tree — A Deeper Look
- [x] Chapter 2: Inside a Neuron — The Math That Isn't Scary
- [x] Chapter 3: How Networks Think — Layers, Weights & Signals
- [x] Chapter 4: Training Step by Step — Forward, Loss, Backward
- [x] Chapter 5: Tokenization Deep Dive
- [x] Chapter 6: Attention Is All You Need
- [x] Chapter 7: The Full Transformer Architecture
- [x] Chapter 8: From Prediction to Conversation
- [x] Chapter 9: Sampling Strategies — The Numbers Behind Creativity
- [x] Chapter 10: Context, Memory & the KV Cache
- [x] Chapter 11: Embeddings — From Words to Geometry
- [x] Chapter 12: How Models Are Actually Trained at Scale
- [x] Chapter 13: Model Architectures Compared

## Instructions for /generate-next-chapter
When the user invokes `/generate-next-chapter`:
1. Read this CLAUDE.md and find the first chapter marked with `[ ]` in Progress Tracking
2. Read the "Chapter Details" section below for that chapter's topics
3. Read `chapters/assets/style.css` for available CSS classes
4. Read `chapters/index.html` for navigation template
5. Read the previous chapter (if any) for context and smooth transition
6. Generate the HTML file in `chapters/` with full content (~600 lines, don't cut under 1000)
7. Update CLAUDE.md — mark the chapter as `[x]`
8. Update `chapters/index.html` — remove `pending` class from that chapter's card
9. Update navigation on the previous chapter if needed

## CSS Classes for Content
- `.math-walkthrough` — step-by-step numeric examples (steel blue accent, unique to this course)
- `.operation-box` — explain a single operation conceptually (amber accent, unique to this course)
- `.intuition-box` — plain-English meaning after showing numbers (teal accent, unique to this course)
- `.checkpoint-box` — quick "can you follow?" self-test (green accent, unique to this course)
- `.prompt-example.good` — good examples (green accent)
- `.prompt-example.bad` — bad examples (red accent)
- `.comparison` — side-by-side comparisons
- `.tip-box` — tips and advice
- `.warning-box` — warnings and cautions
- `.exercise-box` — hands-on exercises (amber accent)
- `.checklist` — checklists with checkmarks
- `.highlight-box` — key messages (gradient background)
- `.stats-grid` + `.stat-card` — statistics display
- `.tool-card` — tool description cards (icon + name + description)
- `.workflow-steps` + `.step` + `.step-arrow` — visual workflow pipeline
- `.theme-toggle` — theme switch button (in nav)

## Content Guidelines
- **At least one `.math-walkthrough`** per chapter — complete numeric example
- **At least one `.operation-box`** per chapter — explaining a core operation
- **At least one `.intuition-box`** per chapter — connecting numbers back to plain English
- **At least one `.checkpoint-box`** per chapter — quick self-test
- **At least one `.exercise-box`** per chapter — hands-on computation the reader does
- Cross-references to AI-Intro use: `<div class="tip-box"><strong>Companion:</strong> This expands on <a href="../../AI-Intro/chapters/NN-slug.html">AI-Intro Ch N: Title</a>.</div>`
- Numbers should use `<code>` or monospace styling for clarity
- Use HTML tables (not ASCII art) for matrices and grids
- When possible, connect concepts to tools the reader already uses (ChatGPT, Claude, Cursor)
- Each chapter should end with a brief preview of how this concept connects to the next chapter

## Chapter Details

### Chapter 1: The AI Family Tree — A Deeper Look
**File:** `01-ai-family-tree.html`
**Goal:** Go beyond buzzword definitions to show what mathematically distinguishes each ML approach.
**Companion:** AI-Intro Ch 1 (01-what-is-ai.html)
**Topics:**
- Quick recap: AI > ML > DL > LLMs hierarchy (link back to AI-Intro Ch 1 for basics)
- Decision boundaries: what a classifier actually learns — draw the line between cats and dogs in "feature space"
- Feature engineering vs. learned features: classical ML needs you to pick features, deep learning finds them automatically
- Supervised learning with numbers: a tiny 2-feature, 3-sample dataset classified by hand
- Unsupervised learning: k-means clustering traced step by step with 6 data points
- Reinforcement learning: the reward signal loop with a simple grid-world example
- What makes neural networks "deep": stacking layers composes simple features into complex ones
- Why LLMs are a specific type of deep learning: sequence-to-sequence, trained on text, autoregressive
- The "feature hierarchy" idea: pixels → edges → shapes → objects → concepts
- Numeric walkthrough: classify a 2D point using a simple linear boundary (weights, bias, threshold)
- Analogy: classical ML is like giving someone a recipe and ingredients; deep learning is like giving them thousands of dishes and saying "figure out the recipes yourself"
- Exercise: given 4 data points on a 2D plane, draw a decision boundary by hand

### Chapter 2: Inside a Neuron — The Math That Isn't Scary
**File:** `02-inside-a-neuron.html`
**Goal:** Fully trace how a single artificial neuron computes its output with real numbers.
**Companion:** AI-Intro Ch 2 (02-neural-networks.html)
**Topics:**
- The single neuron: 3 inputs, 3 weights, 1 bias — the complete formula: output = activation(w1×x1 + w2×x2 + w3×x3 + b)
- Numeric walkthrough: inputs [0.5, 0.8, 0.2], weights [0.4, -0.3, 0.7], bias 0.1 — compute the weighted sum step by step
- What the weighted sum means: some inputs matter more (higher weight), some are suppressed (negative weight)
- The activation function problem: without it, stacking layers is useless (it collapses to a single linear function)
- ReLU explained: if positive keep it, if negative make it zero. Walkthrough with 5 different inputs
- Sigmoid explained: squash any number into 0–1 range. Walkthrough with the same 5 inputs
- Tanh explained briefly: like sigmoid but -1 to 1
- Why non-linearity matters: without it, 100 layers = 1 layer. With it, each layer can carve a new decision surface
- Visualizing activation functions: what happens as input goes from -5 to +5
- The bias as a "shift": it moves the activation threshold left or right
- How a single neuron is already a tiny classifier: it draws one line through feature space
- Analogy: a neuron is like a judge scoring a talent show — each act (input) gets a weighted score, the bias is the judge's baseline mood, and the activation function is the judge deciding "yes" or "no"
- Exercise: compute the output of a neuron with given weights and inputs, using ReLU and then sigmoid

### Chapter 3: How Networks Think — Layers, Weights & Signals
**File:** `03-layers-and-signals.html`
**Goal:** Trace a complete forward pass through a small multi-layer network with real numbers.
**Companion:** AI-Intro Ch 2 (02-neural-networks.html)
**Topics:**
- From one neuron to a layer: 3 inputs, 4 neurons, each with its own weights — that's a layer
- Matrix representation: why a layer's weights form a matrix (inputs × neurons), and why that matters for computation
- Numeric walkthrough: 3 inputs through a 4-neuron hidden layer, step by step (12 multiplications, 4 sums, 4 activations)
- Matrix multiplication explained: the "row times column" rule traced on a 3×4 example
- The forward pass: input layer → hidden layer 1 → hidden layer 2 → output — each layer transforms the data
- What each layer "sees": early layers detect simple patterns, later layers detect complex ones
- Feature hierarchies in practice: a text model's layers go from character patterns to words to grammar to meaning
- Numeric walkthrough: full forward pass through a 2-layer network (3 inputs, 4 hidden, 2 output) with all numbers shown
- Why depth matters more than width: two narrow layers can represent things one wide layer cannot
- The output layer: for classification, softmax turns raw scores into probabilities (preview — full softmax in Ch 6)
- How parameter count is calculated: (inputs × neurons + biases) per layer, summed across all layers
- Scaling up: your 2-layer toy network has ~20 parameters; GPT-4 has ~1.8 trillion. Same math, different scale
- Analogy: a multi-layer network is like a factory assembly line — raw materials enter, each station (layer) refines them, and the finished product comes out the other end
- Exercise: given a 2-layer network with provided weights, compute the full forward pass for a given input

### Chapter 4: Training Step by Step — Forward, Loss, Backward
**File:** `04-training-step-by-step.html`
**Goal:** Walk through one complete training iteration with numbers: forward pass, loss calculation, gradient, weight update.
**Companion:** AI-Intro Ch 3 (03-how-ai-learns.html)
**Topics:**
- Recap: the network starts with random weights — it knows nothing
- The training loop in 4 steps: forward pass, compute loss, backward pass, update weights
- Step 1 — Forward pass: use the network from Chapter 3, feed in a training example, get the (wrong) output
- Step 2 — Loss function: Mean Squared Error with numbers (predicted 0.7, actual 1.0, loss = 0.09)
- Cross-entropy loss: briefly, for classification tasks (more intuitive explanation than MSE for probabilities)
- Step 3 — The backward pass (backpropagation): the chain rule idea WITHOUT calculus — "how much did each weight contribute to the error?"
- The "blame game" analogy: if the output is wrong, trace backward — which weights pushed it the wrong way?
- Numeric walkthrough: for a tiny 2-weight network, show how the gradient tells you "increase this weight, decrease that one"
- Step 4 — Weight update: new_weight = old_weight - learning_rate × gradient, with actual numbers
- Learning rate: too big (0.5) overshoots, too small (0.0001) crawls — show the same update with different rates
- One epoch: running through ALL training examples once
- Batch size: why you don't update after every single example (noise vs. efficiency tradeoff)
- The loss curve: how loss decreases over epochs — what a healthy training run looks like vs. overfitting
- Overfitting with numbers: training loss drops to 0.01 but validation loss stays at 0.5 — the model memorized
- Analogy: training is like adjusting the dials on a mixing board while listening to music — each dial (weight) changes the sound a little, and you keep tweaking until the output sounds right
- Exercise: given a predicted output, actual output, and learning rate, compute the weight update for a single weight

### Chapter 5: Tokenization Deep Dive
**File:** `05-tokenization-deep-dive.html`
**Goal:** Trace the BPE algorithm step by step on actual text to show how a vocabulary is built.
**Companion:** AI-Intro Ch 4 (04-tokens.html)
**Topics:**
- Quick recap: AI reads tokens, not words (link to AI-Intro Ch 4)
- Character-level vs. word-level vs. subword: the tradeoffs that led to BPE
- BPE algorithm step by step: start with characters, count pairs, merge the most frequent, repeat
- Numeric walkthrough: take the text "low lower newest" — show the full merge table across 5 iterations
- The vocabulary that emerges: common words stay whole, rare words get split into known subwords
- Merge rules as a priority list: the tokenizer stores which merges to apply and in what order
- Encoding new text: given a trained vocabulary, how "lower" gets tokenized (apply merges in order)
- Why "strawberry" is hard: show the actual token splits and why letter-counting breaks
- Token IDs: each token maps to a number — "hello" might be token 15339. The model only sees numbers
- Special tokens: BOS, EOS, PAD, and their roles
- Vocabulary size tradeoffs: small vocab (more tokens per text, slower) vs. large vocab (fewer tokens, bigger embedding table)
- Multilingual tokenization: why Japanese text uses 2-3× more tokens than English for the same meaning
- Analogy: BPE is like creating shorthand — if you keep writing "artificial intelligence," you'd eventually abbreviate it to "AI." BPE does this automatically for the most common patterns
- Exercise: given a small corpus and merge table, apply BPE encoding by hand to a new sentence

### Chapter 6: Attention Is All You Need
**File:** `06-attention-mechanism.html`
**Goal:** Compute Q, K, V, attention scores, and weighted values with actual numbers for a 3-token sequence.
**Companion:** AI-Intro Ch 5 (05-transformer.html)
**Topics:**
- The core question attention answers: "when processing this word, how much should I pay attention to each other word?"
- Queries, Keys, Values — the search engine analogy: Q = what I'm looking for, K = what each word offers, V = the actual content
- Where Q, K, V come from: each is the input embedding multiplied by a learned weight matrix
- Numeric walkthrough: 3 tokens, embedding dimension 4, Q/K/V dimension 3 — show all three matrix multiplications
- The attention score: dot product of Q and K — why this measures "how relevant is word j to word i?"
- Numeric walkthrough: compute the 3×3 attention score matrix from Q and K
- Scaling: divide by sqrt(d_k) — why, and what happens if you skip this step (gradients explode)
- Softmax: turning raw scores into probabilities that sum to 1
- Numeric walkthrough: apply softmax to one row of the attention matrix, showing the exponentiation and normalization
- The weighted sum: multiply attention weights by V to get the output
- Numeric walkthrough: compute the final attention output for each token
- The full picture: from input embeddings to attention output, all numbers visible
- Self-attention: when Q, K, V all come from the same sequence (which is what happens in a transformer)
- Multi-head attention: running attention N times in parallel with different weight matrices, concatenating results
- Analogy: attention is like being at a party and deciding who to listen to — each person (token) asks "who here has information relevant to me?" (Q×K), then blends what they hear (weighted V)
- Exercise: given Q, K, V matrices (3×3), compute the full attention output step by step

### Chapter 7: The Full Transformer Architecture
**File:** `07-full-transformer.html`
**Goal:** Show how attention is just one piece — layer norm, residual connections, FFN, and positional encoding complete the picture.
**Companion:** AI-Intro Ch 5 (05-transformer.html)
**Topics:**
- The transformer block: attention is only 1 of 4 operations in each "layer"
- Residual connections: add the input back to the output — why "skip connections" prevent vanishing gradients
- Numeric walkthrough: input vector [0.5, 0.3, 0.8, 0.1] + attention output [0.2, -0.1, 0.3, 0.4] = residual output
- Layer normalization: normalize each vector to have mean 0 and variance 1 — keeps numbers from exploding
- Numeric walkthrough: normalize a 4-element vector step by step (compute mean, subtract, compute variance, divide)
- The feed-forward network (FFN): two linear layers with ReLU in between — what it adds beyond attention
- Numeric walkthrough: a tiny FFN (4 inputs, 8 hidden, 4 output) processing one token
- Positional encoding: the model sees all tokens at once, so it needs to know word ORDER
- Sinusoidal encoding explained intuitively: each position gets a unique "fingerprint" of numbers
- Numeric example: what the positional encoding vectors look like for positions 0, 1, 2, 3
- How position information mixes with token meaning: just add the two vectors together
- Encoder vs. decoder: encoder sees all tokens (bidirectional), decoder only sees previous tokens (causal mask)
- The causal mask with numbers: a 4×4 attention matrix where future positions are -infinity (then softmax makes them 0)
- Stacking layers: GPT-3 has 96 transformer blocks. Each one refines the representation further
- Analogy: a transformer block is like a round of editing — attention finds relevant context (research), FFN processes and enriches it (rewriting), residual connections preserve the original draft, layer norm keeps formatting consistent
- Exercise: given an input vector and attention output, apply residual connection and layer normalization by hand

### Chapter 8: From Prediction to Conversation
**File:** `08-prediction-to-conversation.html`
**Goal:** Trace autoregressive generation token by token through the full pipeline, showing how a sentence forms.
**Companion:** AI-Intro Ch 6 (06-text-generation.html)
**Topics:**
- The fundamental loop: predict next token, append, repeat — traced with actual token IDs and probabilities
- Numeric walkthrough: start with prompt tokens [The, cat, sat], show the probability distribution for the next token, pick "on", append, show next distribution, pick "the", etc.
- Greedy decoding: always pick the highest probability token — fast but boring
- Numeric walkthrough: show greedy decoding for 5 steps with probability distributions
- Beam search: keep the top-N sequences at each step, prune the rest
- Numeric walkthrough: beam search with beam width 2 over 3 steps — show how beams branch and get pruned
- Why beam search is expensive: N beams means N forward passes per token
- Sampling revisited: random selection weighted by probabilities (preview of Chapter 9's deeper dive)
- The stop condition: when does generation end? EOS token, max length, or stop sequence
- How chat works: the system prompt + conversation history + user message are concatenated into one long sequence
- The attention mask in chat: the model attends to everything before the current token, including system prompt and prior turns
- Why "memory" is an illusion: every turn resends the full history
- Token-by-token streaming: the model generates one token and sends it immediately — that's why you see text appear gradually
- Latency breakdown: time-to-first-token (process the prompt) vs. tokens-per-second (generation speed)
- Analogy: autoregressive generation is like writing a story by committee where each committee member only gets to add one word, but they can see everything written so far
- Exercise: given a 5-token vocabulary and a probability distribution at each step, trace greedy and sample decoding for 4 tokens

### Chapter 9: Sampling Strategies — The Numbers Behind Creativity
**File:** `09-sampling-strategies.html`
**Goal:** Show with actual probability distributions how temperature, top-k, and top-p reshape the output.
**Companion:** AI-Intro Ch 7 (07-temperature-and-friends.html)
**Topics:**
- Starting point: the raw logits from the model — just big/small numbers, not yet probabilities
- Softmax recap: turning logits into probabilities (with numbers: logits [2.0, 1.0, 0.5, -1.0, -3.0] → probabilities)
- Temperature scaling: divide logits by T BEFORE softmax
- Numeric walkthrough: same 5 logits at temperature 0.5, 1.0, and 2.0 — show how the distribution sharpens and flattens
- Temperature 0 (or near-zero): the distribution becomes a spike at the top token — deterministic
- Temperature >1: the tail gets fatter, rare tokens become viable
- Top-k sampling: sort by probability, keep only the top K, renormalize
- Numeric walkthrough: 10 tokens, apply top-k with k=3 — show which tokens survive and the renormalized probabilities
- Top-p (nucleus) sampling: sort by probability, keep tokens until cumulative probability exceeds P
- Numeric walkthrough: same 10 tokens, apply top-p with p=0.9 — show the cumulative sum and the cutoff point
- Top-k vs. top-p: why top-p adapts to confidence level (sometimes keeps 2 tokens, sometimes 8)
- Combining strategies: temperature first, then top-p, then sample
- Frequency penalty: subtract a value for each time a token has appeared — reduces repetition
- Presence penalty: binary — if the token appeared at all, subtract a fixed value
- Numeric walkthrough: a 5-token distribution with frequency penalty applied — show how repeated tokens get suppressed
- Practical settings table: best configs for code, creative writing, factual Q&A, brainstorming
- Analogy: temperature is like the volume knob on a stereo equalizer — low volume makes only the loudest frequencies audible (top tokens dominate), high volume brings out the quiet frequencies too (rare tokens get a chance)
- Exercise: given logits for 8 tokens, apply temperature=0.7, then top-p=0.9, then sample — show all intermediate steps

### Chapter 10: Context, Memory & the KV Cache
**File:** `10-context-and-kv-cache.html`
**Goal:** Explain mechanically how the KV cache works and why context windows have hard limits.
**Companion:** AI-Intro Ch 8 (08-context-windows.html)
**Topics:**
- The problem with autoregressive generation: each new token needs to attend to ALL previous tokens
- Without KV cache: regenerate Q, K, V for every token at every step — O(n²) compute per token
- The insight: K and V for already-processed tokens don't change — cache them
- Numeric walkthrough: generating tokens 1–5, show what gets computed vs. what gets reused from cache
- KV cache memory: each layer stores K and V for every token. For a 96-layer model with 128-dim heads, that's a LOT of memory
- Memory calculation: tokens × layers × 2 (K+V) × head_dim × num_heads × bytes — plug in GPT-3 numbers
- Why context windows have a hard limit: the KV cache must fit in GPU memory
- The quadratic attention problem: attention is O(n²) where n = sequence length — double the context, quadruple the compute
- Sliding window attention: only attend to the last W tokens — reduces memory from O(n) to O(W)
- Numeric example: with a window of 4, show the attention mask for an 8-token sequence
- Grouped Query Attention (GQA): share K/V across multiple Q heads to reduce cache size
- Numeric example: 8 Q heads, 2 KV heads — show the sharing pattern
- RoPE (Rotary Position Embedding) briefly: how modern models encode position for extrapolation
- Context window evolution: 2K → 4K → 32K → 128K → 1M — what changed
- Why "longer context" doesn't mean "better": lost-in-the-middle problem, attention dilution
- Analogy: the KV cache is like taking notes during a meeting — instead of re-listening to the entire meeting every time someone asks a question, you check your notes. The notes grow with meeting length, and eventually you run out of notebook pages (GPU memory)
- Exercise: for a 4-layer, 2-head model with head_dim=3, calculate the KV cache size for a 10-token sequence

### Chapter 11: Embeddings — From Words to Geometry
**File:** `11-embeddings-geometry.html`
**Goal:** Train a tiny embedding from scratch (skip-gram idea) and compute cosine similarity with real vectors.
**Companion:** AI-Intro Ch 9 (09-embeddings.html)
**Topics:**
- Quick recap: embeddings turn discrete tokens into continuous vectors (link to AI-Intro Ch 9)
- The training idea (skip-gram): predict context words from a center word — the weights become the embeddings
- Simplified walkthrough: a 5-word vocabulary, 3-dimensional embeddings, one training step shown
- The co-occurrence intuition: words appearing in similar contexts get similar embeddings
- Numeric walkthrough: two 4-dimensional embedding vectors, compute cosine similarity step by step
  - Step 1: dot product (multiply element-wise, sum)
  - Step 2: magnitude of each vector (square elements, sum, square root)
  - Step 3: divide dot product by product of magnitudes
- Interpreting the result: 0.95 means very similar, 0.3 means not related
- Distance vs. similarity: cosine similarity vs. Euclidean distance — when to use which
- The king-queen analogy with actual vectors: show 4D vectors where king - man + woman ≈ queen
- Embedding dimensions: why more dimensions capture more nuance (3D vs. 768D vs. 3072D)
- Sentence embeddings: how to go from word embeddings to a single vector for a whole paragraph
- Practical use: semantic search — embed the query, embed all documents, find the closest
- Numeric walkthrough: 3 document embeddings and 1 query embedding, rank by cosine similarity
- Vector databases: specialized storage that makes nearest-neighbor search fast (HNSW, IVF briefly)
- Analogy: training embeddings is like asking thousands of people "who do you hang out with?" and then placing people who have similar friend groups near each other on a map
- Exercise: given 4 word embeddings (3D vectors), compute all pairwise cosine similarities and identify the most/least similar pair

### Chapter 12: How Models Are Actually Trained at Scale
**File:** `12-training-at-scale.html`
**Goal:** Explain the full training pipeline from raw internet text to a useful assistant.
**Companion:** New topic (no direct AI-Intro equivalent)
**Topics:**
- The three stages: pre-training, supervised fine-tuning (SFT), and RLHF/RLAIF
- Pre-training: predict the next token on trillions of tokens from the internet
- Data pipelines: web scraping, deduplication, filtering, quality scoring — what the training data actually looks like
- The compute requirements: petaflops-days, thousands of GPUs, months of training
- Numeric perspective: GPT-3 used ~3.14 × 10²³ FLOPS. How long would that take on your laptop? (~800,000 years)
- Data parallelism vs. model parallelism vs. pipeline parallelism: splitting the work across GPUs
- Mixed precision training: using float16 instead of float32 to halve memory and double speed
- The loss curve during pre-training: what it looks like, scaling laws (more data + more compute = lower loss, predictably)
- Chinchilla scaling laws: the optimal ratio of model size to training data
- Supervised fine-tuning (SFT): take the pre-trained model and train it on instruction-response pairs
- How SFT changes behavior: from "predict next token" to "follow instructions"
- RLHF: train a reward model on human preferences, then use PPO to optimize the language model
- Simplified RLHF walkthrough: two responses, human picks the better one, reward model learns, policy improves
- DPO as a simpler alternative to RLHF: skip the reward model, optimize directly on preference pairs
- Constitutional AI (RLAIF): using AI feedback instead of human feedback
- Why training is expensive: a table of estimated costs for training various model sizes
- Analogy: pre-training is like getting a general education (reading everything), SFT is like vocational training (learning a specific job), RLHF is like an internship with feedback (a mentor corrects your behavior)
- Exercise: given a model's parameter count and a training dataset size, estimate whether it's compute-optimal using Chinchilla ratios

### Chapter 13: Model Architectures Compared
**File:** `13-architectures-compared.html`
**Goal:** Map the landscape of model architectures so the reader understands what's behind each type of AI.
**Companion:** AI-Intro Ch 10 (10-models-and-industry.html)
**Topics:**
- Encoder-only models (BERT): bidirectional, great for understanding, used for classification and embeddings
- How BERT's masked language model works: hide a word, predict it from context — numeric example with a 5-token sentence
- Decoder-only models (GPT, Claude, Llama): autoregressive, great for generation
- Why decoder-only won: simpler to scale, more general, generation is the universal interface
- Encoder-decoder models (T5, original Transformer): best for translation and summarization — why they're less common now
- Mixture of Experts (MoE): only activate a subset of parameters per token — more total parameters, same compute
- Numeric example: 8 experts, router picks top-2 for each token — show the gating mechanism
- Why MoE matters: Mixtral 8x7B has 47B parameters but only uses ~13B per token
- Diffusion models: start with noise, gradually denoise to create images
- The diffusion process: forward (add noise in T steps) and reverse (remove noise in T steps)
- Simplified numeric walkthrough: a 4-pixel "image" going through 3 denoising steps
- Vision Transformers (ViT): split an image into patches, treat each patch as a token, apply standard transformer
- Multimodal models: how vision and text are combined — project image embeddings into the same space as text tokens
- State-space models (Mamba) briefly: linear-time alternatives to transformers for very long sequences
- Where the field is heading: scaling laws, emergent abilities, efficiency improvements
- Analogy: model architectures are like different types of vehicles — encoder-only is a scanner (analyzes), decoder-only is a printer (generates), encoder-decoder is a translator (reads then writes), MoE is a team of specialists (only the relevant experts work on each task)
- Exercise: given a use case (chatbot, search, translation, image generation), pick the right architecture and justify why
