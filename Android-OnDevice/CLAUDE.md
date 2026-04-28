# On-Device AI for Android

## Project Description
An HTML course for Android developers who want to run ML and AI models directly on the device — no cloud APIs, no server costs, no latency. The reader knows Kotlin, Compose, and Android fundamentals, but has never trained, optimized, or deployed a machine learning model. They want to ship real AI features — image classification, object detection, text recognition, speech-to-text, and even generative AI — all running on the user's phone.

The course covers TensorFlow Lite, MediaPipe, ML Kit, Gemini Nano, hardware acceleration (NPU, GPU, DSP), model optimization (quantization, pruning), and production deployment. It is **tool-agnostic** — focusing on Android ML frameworks, not on any specific AI coding tool.

The style is **"For Dummies"** — friendly, approachable, like a senior Android dev who just shipped an on-device AI feature showing you how they did it. Heavy on practical examples with real Kotlin code, real Gradle configs, and real model files.

## Language Rules
- All content is in **English**
- Tone: friendly, conversational, like a colleague who's excited about on-device AI
- Use real Android examples: Kotlin code, Gradle dependencies, actual API calls, real model files
- Address: second person singular (you)
- When introducing a concept, always answer: "OK, but how do I actually use this in my app?"
- Light humor is welcome — keep it engaging, not dry
- Use short paragraphs — walls of text kill understanding
- Use analogies from everyday life and Android development to explain ML concepts

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
Android-OnDevice/
  CLAUDE.md                                — This file
  .claude/
    commands/
      generate-next-chapter.md             — Skill for chapter generation
  chapters/
    index.html                             — Landing page with navigation
    assets/
      style.css                            — Shared CSS with dark/light theme
    01-on-device-revolution.html           — The On-Device AI Revolution
    02-ml-models-explained.html            — How ML Models Work (Just Enough Theory)
    03-first-model.html                    — Your First On-Device Model
    04-mediapipe.html                      — MediaPipe — Production-Ready AI Features
    05-ml-kit.html                         — ML Kit — Google's Plug-and-Play AI
    06-gemini-nano.html                    — Gemini Nano — On-Device Generative AI
    07-hardware-acceleration.html          — Hardware Acceleration — NPU, GPU, and DSP
    08-model-optimization.html             — Model Optimization — Making Models Mobile-Ready
    09-computer-vision.html                — Computer Vision Features
    10-nlp-audio.html                      — NLP and Audio On-Device
    11-production-deployment.html          — Model Management and Production Deployment
    12-ai-toolkit.html                     — Building Your On-Device AI Toolkit
```

## Progress Tracking
- [x] Chapter 1: The On-Device AI Revolution
- [x] Chapter 2: How ML Models Work (Just Enough Theory)
- [x] Chapter 3: Your First On-Device Model
- [x] Chapter 4: MediaPipe — Production-Ready AI Features
- [x] Chapter 5: ML Kit — Google's Plug-and-Play AI
- [x] Chapter 6: Gemini Nano — On-Device Generative AI
- [x] Chapter 7: Hardware Acceleration — NPU, GPU, and DSP
- [x] Chapter 8: Model Optimization — Making Models Mobile-Ready
- [x] Chapter 9: Computer Vision Features
- [x] Chapter 10: NLP and Audio On-Device
- [x] Chapter 11: Model Management and Production Deployment
- [x] Chapter 12: Building Your On-Device AI Toolkit

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
- `.device-benchmark` — on-device performance benchmark results (copper accent, unique to this course)
- `.model-pipeline` — ML data flow visualization: input → preprocess → inference → postprocess → output (steel-blue accent, unique to this course)
- `.hardware-note` — hardware/chipset compatibility and capability info (gray accent, unique to this course)
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
- **At least one `.device-benchmark`** per chapter showing model performance metrics (inference time, memory, model size)
- **At least one `.model-pipeline`** per chapter showing data flow through the ML pipeline
- **At least one `.hardware-note`** per chapter with device/chipset compatibility information
- **At least one `.exercise-box`** per chapter where the reader builds or measures something real
- Keep code examples practical and real (Kotlin, Gradle config, Android API calls — max 20-30 lines per snippet)
- Each chapter should end with a preview of how it connects to the next chapter
- Every chapter should produce something tangible: a working feature, a benchmark, or a deployed model
- Use analogies to bridge from Android concepts the reader knows to ML concepts they don't

## Chapter Details

### Chapter 1: The On-Device AI Revolution
**File:** `01-on-device-revolution.html`
**Goal:** Convince the reader that on-device AI is the next frontier for Android apps and give them a mental map of the landscape.

**Topics:**
- Why on-device AI matters in 2026: privacy (data never leaves the device), latency (no network round-trip), offline capability, cost savings (no cloud API fees per request)
- Cloud AI vs on-device AI: a side-by-side comparison — latency (200ms cloud vs 10ms on-device), privacy (data sent to server vs stays on device), cost (per-request billing vs free after model download), capability (GPT-4 vs MobileNet)
- The on-device AI stack: hardware (NPU, GPU, DSP, CPU) → runtime (TFLite, ONNX, MediaPipe) → framework (ML Kit, Gemini Nano) → your app
- What Android devices can do today: real examples — Google Photos (image search), Google Translate (offline mode), Gboard (smart compose), Samsung Galaxy AI (on-device summarization)
- The hardware landscape in 2026: Google Tensor G-series (on-device Gemini Nano), Qualcomm Snapdragon (Hexagon NPU), Samsung Exynos, MediaTek Dimensity — what each brings
- The three categories of on-device AI: classical ML (classification, detection), task-specific models (MediaPipe face/hand/pose), and on-device generative AI (Gemini Nano)
- The "good enough" principle: on-device models are smaller but surprisingly capable for focused, narrow tasks
- What you will build in this course: preview of features — image classifier, hand gesture recognizer, OCR scanner, offline translator, on-device text rewriter, optimized real-time object detector
- Prerequisites check: what the reader needs (Kotlin, Compose, Android Studio, a physical device) and what they do NOT need (ML theory, Python, training infrastructure)
- Exercise: audit your current app (or a favorite app) for 3 features that could benefit from on-device AI — estimate the user impact of each

### Chapter 2: How ML Models Work (Just Enough Theory)
**File:** `02-ml-models-explained.html`
**Goal:** Give the reader just enough ML understanding to be dangerous — what a model is, what inference means, and what inputs/outputs look like, without becoming ML engineers.

**Topics:**
- What an ML model actually is: a file containing learned numerical weights that transforms inputs into outputs — analogy: a compiled function you didn't write, it takes inputs and returns outputs, but you can't read the source code
- The inference loop: load model → preprocess input → run inference → postprocess output → display result — the core pattern you'll use in every chapter
- Model formats you'll encounter: TensorFlow Lite (.tflite), ONNX (.onnx), MediaPipe task bundles (.task), PyTorch Mobile (.ptl) — what each is and when you'll see it
- Tensors explained for Android devs: multi-dimensional arrays — a Bitmap is a 3D tensor (height × width × RGB channels), a sentence is a 2D tensor (tokens × embedding dimensions)
- Input preprocessing: why you can't just throw a Bitmap at a model — resizing to expected dimensions (224×224), normalizing pixel values (0-255 → 0.0-1.0), channel ordering (RGB vs BGR)
- Output postprocessing: raw model output is numbers (logits, probabilities) — you need to interpret them: find the highest probability, map index to label, apply threshold
- Model metadata: labels file, input/output tensor specs, normalization parameters — the "README" inside the model file that tells you how to use it
- Common model architectures Android devs encounter: MobileNet (image classification, small and fast), SSD/YOLO (object detection with bounding boxes), DeepLab (image segmentation), MobileBERT (text classification)
- The size-accuracy tradeoff: MobileNetV3-Small (2MB, 68% accuracy) vs EfficientNet-B7 (66MB, 84% accuracy) — choosing the right model for mobile constraints
- Where to find pre-trained models: TensorFlow Hub, ONNX Model Zoo, Hugging Face, MediaPipe Solutions, Kaggle Models — the model "app stores"
- Exercise: download a MobileNetV3 .tflite model from TensorFlow Hub, open it in Netron (the model visualizer), and identify its input shape, output shape, and file size

### Chapter 3: Your First On-Device Model
**File:** `03-first-model.html`
**Goal:** Get the reader running a real ML model on their Android device — an image classifier that identifies objects from the camera in real time.

**Topics:**
- Setting up the project: Gradle dependencies for TensorFlow Lite — `org.tensorflow:tensorflow-lite`, `tensorflow-lite-support`, `tensorflow-lite-metadata`, and `tensorflow-lite-gpu`
- Adding the model to your project: placing the .tflite file in `assets/`, configuring `aaptOptions { noCompress "tflite" }` to prevent compression
- Loading the model: creating a `TFLite Interpreter` with options, memory-mapping the model file for performance, configuring thread count
- The `TensorImage` and `ImageProcessor` helper classes: simplifying image preprocessing — resize, normalize, and convert Bitmap to tensor in a few lines
- Building the inference pipeline step by step: capture frame → resize to 224×224 → normalize pixels to [0,1] → run inference → read top-5 predictions with confidence scores
- CameraX integration: capturing frames from the camera using `ImageAnalysis` use case, converting `ImageProxy` to `Bitmap`, handling rotation
- Displaying results in Compose: overlaying classification labels and confidence percentages on the camera preview using a `Box` composable
- Threading strategy: running inference on `Dispatchers.Default`, never blocking the UI thread, using `StateFlow` to push results to the UI
- Performance baseline: measuring inference time with `System.nanoTime()` — establishing the CPU benchmark (typically 50-100ms on mid-range devices)
- Common pitfalls and fixes: model not found crash (wrong asset path), wrong input dimensions (model expects 224×224 but got 640×480), forgetting to normalize (garbage output), running on main thread (ANR)
- Exercise: build a working image classifier that runs on your phone — photograph 10 different objects, record the top prediction and confidence for each, note which ones it gets right vs wrong and hypothesize why

### Chapter 4: MediaPipe — Production-Ready AI Features
**File:** `04-mediapipe.html`
**Goal:** Use Google's MediaPipe to add polished, production-ready AI features without training any models — face detection, hand tracking, pose estimation, and object detection.

**Topics:**
- What MediaPipe is: Google's cross-platform framework with pre-built ML solutions optimized for mobile — "batteries included" AI features you can add in an afternoon
- MediaPipe Tasks API: the high-level Android SDK — `ObjectDetector`, `FaceLandmarker`, `HandLandmarker`, `PoseLandmarker`, `ImageClassifier`, `TextClassifier`
- Setting up MediaPipe: Gradle dependency `com.google.mediapipe:tasks-vision`, downloading model bundle files (.task), initialization with `BaseOptions`
- Building a real-time object detector: camera feed → MediaPipe `ObjectDetector` → bounding boxes with labels drawn on Compose Canvas
- Face mesh and landmarks: detecting 468 face landmarks in real time — building an AR-style face overlay (glasses, masks, face paint) using `FaceLandmarker`
- Hand tracking: detecting 21 hand landmarks per hand — building a gesture recognizer that maps hand poses to actions (thumbs up = like, peace = screenshot, open palm = pause)
- Pose estimation: full-body skeletal tracking with 33 landmarks — practical uses in fitness apps (rep counting), physical therapy (range of motion), gaming (body-controlled input)
- MediaPipe configuration: `RunningMode` (IMAGE for photos, VIDEO for recorded, LIVE_STREAM for camera), delegate selection (CPU or GPU), max results, confidence thresholds
- Performance tuning: choosing the right model variant (lite vs full vs heavy), adjusting detection frequency, frame skipping to maintain smooth UI
- Combining multiple MediaPipe tasks: running face detection AND hand tracking simultaneously — managing multiple pipeline instances, memory considerations
- MediaPipe vs raw TFLite: developer experience (hours vs days), accuracy (MediaPipe models are optimized), performance (MediaPipe handles threading), flexibility (TFLite lets you use any model)
- Exercise: build a hand gesture recognizer that detects 3 different hand poses and triggers 3 different app actions — measure the detection latency and accuracy for each gesture

### Chapter 5: ML Kit — Google's Plug-and-Play AI
**File:** `05-ml-kit.html`
**Goal:** Master Google's ML Kit for common AI tasks that require zero ML expertise — text recognition, barcode scanning, translation, smart replies, entity extraction, and custom model deployment.

**Topics:**
- ML Kit vs MediaPipe vs TFLite: when to use which — ML Kit for "I just want it to work" (highest level), MediaPipe for real-time tracking (optimized pipelines), TFLite for custom models (most flexible)
- On-device vs cloud APIs in ML Kit: which features work offline (text recognition, barcode, face detection, translation) vs which need network (document AI, cloud vision)
- Text recognition (OCR): building a receipt scanner — point the camera at a receipt, extract all text lines, group by blocks, display structured results in Compose
- Barcode and QR code scanning: fast, reliable scanning with `BarcodeScanning` — building a product lookup feature, handling multiple barcode formats (QR, EAN, Code128)
- On-device translation: `Translation` API — building an offline translator supporting 50+ language pairs, downloading language models on demand (2-5MB each), managing storage
- Smart Reply: generating contextual reply suggestions for messaging — feeding conversation history with `TextMessage` objects, getting 1-3 relevant reply suggestions back
- Entity extraction: identifying dates, addresses, phone numbers, flight numbers, tracking numbers in text — building a "smart clipboard" that detects actionable items in copied text
- Digital ink recognition: handwriting to text in 300+ languages — building a handwriting input for a note-taking feature, handling stroke data from Compose Canvas touch events
- Custom model deployment with ML Kit: using `CustomRemoteModel` (Firebase-hosted, OTA updates) and `CustomLocalModel` (bundled in APK) to run your own TFLite models through ML Kit's infrastructure
- Model download management: checking availability, downloading on Wi-Fi only, tracking download progress, handling storage constraints, updating models without app updates via Firebase
- Exercise: build a "smart scanner" that combines text recognition + barcode scanning + entity extraction — scan a receipt, extract items/prices, detect any phone numbers or dates, and display a structured summary

### Chapter 6: Gemini Nano — On-Device Generative AI
**File:** `06-gemini-nano.html`
**Goal:** Harness Google's Gemini Nano for on-device generative AI — summarization, smart replies, rewriting, and contextual suggestions without any cloud API calls.

**Topics:**
- What Gemini Nano is: a small but capable LLM designed to run directly on Android — the first practical on-device generative AI for mobile apps
- Device compatibility: which phones support Gemini Nano (Pixel 8 Pro+, Samsung Galaxy S24+, and expanding list), runtime feature detection with `GenerativeModel.isAvailable()`
- The AICore system service: how Android manages the on-device model — the model is shared across apps, downloaded/updated by the system, managed by AICore, lifecycle handled by Android
- Setting up Gemini Nano: Gradle dependency (`com.google.ai.edge.aicore`), declaring `AICore` capability in manifest, initialization with `GenerativeModel`, availability checks
- Text generation: building a "rewrite this" feature — transform user text to formal/casual/shorter/longer tone entirely on-device, streaming token output for responsive UX
- Summarization: condensing long text into key points — building a "TL;DR" button for an article reader, handling input length limits gracefully
- Smart reply generation: context-aware reply suggestions that understand conversation flow — building smart replies for a messaging feature with conversational context
- The MediaPipe LLM Inference API: an alternative path for running on-device LLMs — supports Gemma, Phi, StableLM, and other compatible models beyond Gemini Nano
- Prompt engineering for tiny models: why prompts that work on GPT-4 fail on Nano — use shorter prompts, simpler instructions, single focused tasks, avoid complex reasoning chains
- Limitations and guardrails: what Gemini Nano cannot do (long-form generation, complex reasoning, large context windows, image generation) — setting realistic user expectations
- Fallback strategies: on-device first, cloud second — detecting when the device can't handle a request, gracefully upgrading to Gemini Pro/Flash via the Generative AI API
- Exercise: build an "AI Writing Assistant" that offers 4 text transformations (summarize, formalize, simplify, expand) running entirely on-device, with a cloud fallback for unsupported devices — compare the quality and latency of on-device vs cloud results

### Chapter 7: Hardware Acceleration — NPU, GPU, and DSP
**File:** `07-hardware-acceleration.html`
**Goal:** Move beyond CPU inference and unlock the full power of the device's AI hardware — making models run 5-20x faster using GPU delegates, NNAPI, and chipset-specific acceleration.

**Topics:**
- The hardware zoo inside your phone: CPU (general purpose, slowest for ML), GPU (massively parallel, great for large models), NPU/TPU (purpose-built for tensor operations, fastest), DSP (specialized signal processing, efficient for audio)
- Why CPU inference is leaving performance on the table: benchmark showing MobileNetV2 on Pixel 8 — CPU: 25ms, GPU: 8ms, NNAPI (Tensor TPU): 3ms — same model, same accuracy, 8x faster
- TFLite GPU Delegate: setup with `GpuDelegate()`, `Interpreter.Options().addDelegate()`, supported operations (conv2d, matmul — yes; custom ops — no), automatic fallback for unsupported ops
- NNAPI Delegate: Android's hardware abstraction layer for ML — routes operations to the best available hardware automatically, setup with `NnApiDelegate()`, controlling accelerator selection
- Qualcomm QNN Delegate: direct access to the Hexagon NPU on Snapdragon chips — maximum performance on Qualcomm devices, setup and configuration, model compatibility requirements
- Google Tensor TPU: how Pixel phones use their custom ML accelerator — accessing via NNAPI, performance characteristics, supported model architectures
- Samsung Eden / Exynos NPU: ML acceleration on Galaxy devices — accessing through NNAPI or Samsung's Neural SDK, device-specific optimizations
- Delegate selection strategy: how to pick the right delegate at runtime — check device capabilities, benchmark each delegate on first run, cache the best delegate choice, implement fallback chain (NPU → GPU → CPU)
- Benchmarking methodology: measuring latency (p50, p95, p99 — not just average), throughput (inferences per second), memory consumption, power draw, and thermal throttling over sustained usage
- Warm-up runs: why the first inference is always slow (JIT compilation, shader compilation, NPU initialization) — running 3-5 warm-up inferences before measuring or showing results to users
- Handling delegate failures gracefully: some operations aren't supported on all delegates — catching delegate init failures, falling back to CPU without crashing, logging which delegate was used
- Exercise: take the image classifier from Chapter 3, run it on CPU, GPU delegate, and NNAPI — measure the p50 latency on your device for each, then build a dynamic delegate selector that picks the fastest available option at runtime

### Chapter 8: Model Optimization — Making Models Mobile-Ready
**File:** `08-model-optimization.html`
**Goal:** Transform models that are too big or too slow for mobile into optimized versions — quantization, pruning, and distillation explained through hands-on practice.

**Topics:**
- Why optimization matters: a 100MB float32 model with 50ms CPU inference is unusable on mobile — target benchmarks for shipping: under 20MB model size, under 15ms inference on NPU, under 50MB runtime memory
- Quantization explained: reducing numerical precision from 32-bit floats to 16-bit or 8-bit integers — same learned patterns, 2-4x smaller file, 2-3x faster inference, usually <2% accuracy loss
- Post-training quantization with TFLite: the easiest optimization — use the TFLite Converter Python script to quantize an existing model, no retraining needed, three variants available
- Dynamic range quantization: quantize weights only (smallest code change, 2x smaller, minor speedup) — when to use: quick win, models where most time is in weight-heavy ops
- Full integer quantization: quantize both weights and activations (4x smaller, 2-4x faster, requires representative dataset) — when to use: production models where performance matters
- Float16 quantization: reduce to half precision (2x smaller, GPU-friendly, almost no accuracy loss) — when to use: models targeting GPU delegate
- Quantization-aware training (QAT): simulating quantization during training for better accuracy — when post-training quantization drops accuracy below acceptable threshold (common in small models)
- Pruning: removing weights that contribute little to accuracy — structured pruning (remove entire channels) vs unstructured pruning (zero individual weights), achieving 50-90% sparsity
- Knowledge distillation: training a small "student" model to mimic a large "teacher" — how MobileNet-style models are created, when to use: you need a model much smaller than anything available
- Model format conversion: PyTorch → ONNX → TFLite pipeline, TensorFlow SavedModel → TFLite, common conversion pitfalls (unsupported ops, dynamic shapes)
- ONNX Runtime Mobile: an alternative to TFLite — when to choose ONNX (model originates from PyTorch, need cross-platform with iOS, specific op support)
- The optimization decision tree: start with post-training quantization (int8) → if accuracy drops too much, try float16 → if still too large, try pruning → if still not good enough, consider distillation or a different base model
- Exercise: take a standard MobileNetV2 float32 model (14MB), apply int8 post-training quantization, measure size reduction and accuracy impact on 20 test images, then run the quantized model with GPU delegate and measure combined speedup vs original CPU baseline

### Chapter 9: Computer Vision Features
**File:** `09-computer-vision.html`
**Goal:** Build production-quality computer vision features — object detection with bounding boxes, image segmentation, custom model training, and real-time video processing at 30fps.

**Topics:**
- Beyond classification: the CV task taxonomy — classification (what is it?), detection (where is it? → bounding boxes), segmentation (pixel-perfect outline → masks), tracking (follow it across frames → IDs)
- Object detection with SSD-MobileNet: building a real-time detector that draws bounding boxes around objects with class labels and confidence scores on the camera feed
- Image segmentation with DeepLab: separating foreground from background — building a portrait mode / background blur feature using on-device semantic segmentation
- Non-maximum suppression (NMS): why your detector returns 50 overlapping boxes for one object — IoU (intersection over union) threshold, filtering duplicates, the algorithm explained simply
- Custom model training for your domain: using TensorFlow Model Maker to train a custom object detector with your own images — collecting data, labeling with LabelImg, training in Colab, exporting to TFLite
- Transfer learning in practice: fine-tuning a pre-trained model on 100-500 images of your specific objects — the minimal viable dataset, data augmentation tricks, when 100 images is enough
- Video processing pipeline: handling continuous frames efficiently — frame skipping (process every 3rd frame), async inference with coroutines, ring buffer pattern, avoiding memory pressure from Bitmap allocations
- Drawing results on Compose Canvas: bounding boxes with labels using `Canvas` and `DrawScope`, segmentation mask overlay with alpha blending, scaling detection coordinates to match screen dimensions
- Real-world camera handling: sensor rotation vs display rotation, scaling detection coordinates from model input size to preview size, handling different aspect ratios (4:3 sensor, 16:9 display)
- Performance patterns for 30fps: the producer-consumer pattern — camera produces frames, inference consumes them asynchronously, UI updates with latest results without blocking either pipeline
- Testing vision features: building a test suite with sample images, asserting expected detections (object class, bounding box region, confidence threshold), regression testing when changing models
- Exercise: build a real-time object detector with SSD-MobileNet that draws labeled bounding boxes on live camera, apply int8 quantization + GPU delegate, and verify it maintains 30fps on your device

### Chapter 10: NLP and Audio On-Device
**File:** `10-nlp-audio.html`
**Goal:** Bring language understanding and audio processing to your app without cloud APIs — text classification, sentiment analysis, speech-to-text, and keyword spotting running entirely on-device.

**Topics:**
- On-device NLP landscape: what's practical in 2026 — text classification, sentiment analysis, entity extraction, language detection, basic QA — all run well on mobile; complex reasoning still needs the cloud
- Text classification with TFLite: building a content categorizer using a fine-tuned MobileBERT — spam/ham filter, support ticket router, or content moderation filter, the full pipeline from text input to category output
- Sentiment analysis on-device: analyzing user reviews, chat messages, or feedback for positive/negative/neutral sentiment — building a real-time sentiment indicator for a messaging feature
- Tokenization for on-device NLP: BPE vs WordPiece vs SentencePiece — loading the tokenizer vocabulary file, encoding text to token IDs, keeping tokenizer in sync with model's expected vocabulary
- On-device speech-to-text: Android's `SpeechRecognizer` with offline language packs (download specific languages for offline use), Whisper.cpp for high-accuracy offline transcription, Vosk for lightweight always-on recognition
- Keyword spotting and wake word detection: building an always-listening feature that detects specific phrases — using a tiny audio classification model (< 1MB), processing audio in a background service with minimal battery impact
- Audio classification: identifying sounds (applause, siren, dog bark, music genre) using YAMNet — extracting audio features (mel spectrograms), running classification, practical uses in accessibility and smart home apps
- Text embeddings on-device: computing semantic similarity without a server — running a small all-MiniLM sentence transformer for on-device search, recommendations, or duplicate detection
- Combining NLP with generative AI: use traditional NLP models for classification tasks (fast, reliable, cheap) and Gemini Nano for generation tasks (rewriting, summarization) — picking the right tool for each job
- Multilingual considerations: single multilingual model (larger but simpler) vs per-language specialists (smaller but manage multiple downloads), on-demand language model downloading strategies
- Exercise: build a "smart inbox" feature that classifies incoming messages by category (urgent, informational, social, spam) and shows per-message sentiment, running entirely on-device with a fine-tuned MobileBERT

### Chapter 11: Model Management and Production Deployment
**File:** `11-production-deployment.html`
**Goal:** Ship on-device AI features to production with confidence — model packaging, versioning, OTA updates, A/B testing, monitoring, error handling, and graceful degradation across thousands of device configurations.

**Topics:**
- The production gap: "it works on my Pixel" is not enough — the fragmented reality: 24,000+ distinct Android devices, 8+ chipset families, 512MB to 16GB RAM, Android 8 to 16, with and without NPUs
- Model packaging strategies: bundled in APK/AAB (instant availability, increases download size by model size), downloaded on first use (smaller APK, requires download UI and error handling), Firebase ML custom model hosting (OTA updates, A/B testing)
- APK size impact: a 15MB model adds 15MB to your APK — using Android App Bundles to deliver models only to supported devices, compressing models, asset delivery API for large models
- Model versioning: semantic versioning for models (v1.2.3), tracking which version runs on which devices, embedding version metadata in the model file, rollback strategy when a new model performs worse
- A/B testing models: running two model versions on different user segments — Firebase Remote Config to assign model variants, comparing accuracy, latency, and user engagement metrics in production
- Firebase ML Model Management: hosting TFLite models on Firebase, triggering downloads with `FirebaseModelDownloader`, conditional delivery based on device capability or user segment
- OTA model updates: pushing improved models without an app update — the workflow from training → validation → upload to Firebase → gradual rollout → monitoring → full deployment
- Error handling and graceful degradation: model loading failure (corrupt download, out of memory), inference crash (unexpected input), garbage output (model mismatch) — fallback UIs, error telemetry, disabling features on incapable devices
- Device capability detection at runtime: checking available RAM (`ActivityManager.getMemoryInfo()`), NPU presence (NNAPI device list), API level, and deciding which model variant to load — or whether to disable the AI feature entirely
- Memory management in production: model lifecycle (load on screen enter, unload on screen exit), lazy loading, avoiding keeping large models in memory during background, handling `onTrimMemory` callbacks
- Performance monitoring: tracking p50/p95 inference latency, success rate, crash rate, model download completion rate using Firebase Analytics custom events — alerting on regressions after model updates
- Privacy and compliance: on-device processing as a GDPR advantage — data never leaves the device, no consent needed for on-device inference, communicating "processed locally" to users, audit logging
- Exercise: take any feature from earlier chapters and add production hardening — device capability check, model download with progress UI, error handling with fallback, performance telemetry, and graceful degradation on unsupported devices

### Chapter 12: Building Your On-Device AI Toolkit
**File:** `12-ai-toolkit.html`
**Goal:** Consolidate everything into a reusable decision framework, build a toolkit abstraction, and chart a roadmap for staying current as on-device AI evolves.

**Topics:**
- The on-device AI decision framework: given a feature requirement, how to choose — ML Kit (easiest, limited customization), MediaPipe (best real-time tracking, pre-built solutions), TFLite/ONNX (any custom model, most flexible), Gemini Nano (generative tasks, limited devices)
- Building a reusable inference wrapper: a Kotlin class that handles model loading, delegate selection, warm-up, preprocessing, inference, postprocessing, error handling, and performance measurement — the pattern for every future on-device AI feature
- The model evaluation checklist: 6 metrics to measure before shipping — accuracy (does it get the right answer?), latency (fast enough for real-time?), model size (fits the APK budget?), memory (runs without OOM?), power (drains battery?), device coverage (what % of users can run it?)
- Multi-model architectures: running several models as a pipeline — detect faces → crop → classify emotion → generate response — pipeline design, memory budgets, scheduling inference across models
- Edge cases and failure modes: adversarial inputs (unusual angles, extreme lighting), out-of-distribution data (objects the model never saw), environmental factors (motion blur, occlusion) — building robust features that fail gracefully with confidence thresholds
- The complete capstone architecture: designing an app that combines vision (object detection), language (text classification), generative AI (Gemini Nano summarization), and audio (keyword spotting) — demonstrating how all pieces work together in a single app
- Keeping up with the landscape: key resources — Android ML documentation, TensorFlow blog, MediaPipe releases, Google AI Edge updates, Android Dev Summit talks, arXiv papers (just the abstracts)
- What's coming next: on-device multimodal models (image + text), LoRA adapters for user-personalized models, federated learning for privacy-preserving improvement, always-on ambient AI features, on-device fine-tuning
- Cross-platform considerations: sharing models between Android and iOS — TFLite and ONNX work on both, Kotlin Multiplatform strategies for shared ML preprocessing/postprocessing logic
- Your 30-day action plan: week 1 pick a feature and prototype with ML Kit or MediaPipe, week 2 optimize and benchmark on target devices, week 3 add hardware acceleration and production hardening, week 4 ship to beta users and monitor metrics
- Exercise: design an on-device AI feature for your own app — write a technical design document covering: problem statement, model selection (with rationale), optimization strategy, hardware acceleration plan, fallback behavior for unsupported devices, production monitoring metrics, and estimated timeline
