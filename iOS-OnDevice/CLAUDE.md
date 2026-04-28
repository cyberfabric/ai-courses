# On-Device AI for iOS

## Project Description
An HTML course for iOS developers who want to run ML and AI models directly on the device — no cloud APIs, no server costs, no latency. The reader knows Swift, SwiftUI, and iOS fundamentals, but has never trained, optimized, or deployed a machine learning model. They want to ship real AI features — image classification, object detection, text recognition, speech-to-text, and even generative AI — all running on the user's iPhone.

The course covers Core ML, Vision, Natural Language, Foundation Models, SpeechAnalyzer, Create ML, MLX Swift, Metal 4, hardware acceleration (Neural Engine, GPU), model optimization (quantization, palettization, pruning), and production deployment. It is **tool-agnostic** — focusing on Apple's ML frameworks, not on any specific AI coding tool.

The style is **"For Dummies"** — friendly, approachable, like a senior iOS dev who just shipped an on-device AI feature showing you how they did it. Heavy on practical examples with real Swift code, real Xcode configs, and real model files.

## Language Rules
- All content is in **English**
- Tone: friendly, conversational, like a colleague who's excited about on-device AI
- Use real iOS examples: Swift code, SPM dependencies, actual Apple API calls, real model files
- Address: second person singular (you)
- When introducing a concept, always answer: "OK, but how do I actually use this in my app?"
- Light humor is welcome — keep it engaging, not dry
- Use short paragraphs — walls of text kill understanding
- Use analogies from everyday life and iOS development to explain ML concepts

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
iOS-OnDevice/
  CLAUDE.md                                — This file
  .claude/
    commands/
      generate-next-chapter.md             — Skill for chapter generation
      create-memory-map.md                 — Skill for visual chapter summary generation
  chapters/
    index.html                             — Landing page with navigation
    assets/
      style.css                            — Shared CSS with dark/light theme
    01-on-device-revolution.html           — The On-Device AI Revolution
    02-ml-models-apple-silicon.html        — How ML Models Work on Apple Silicon
    03-first-core-ml-model.html            — Your First Core ML Model
    04-vision-framework.html               — Vision Framework — See Like an iPhone
    05-nlp-speech-sound.html               — Natural Language, Speech, and Sound
    06-foundation-models.html              — Foundation Models and Apple Intelligence
    07-hardware-acceleration.html          — Hardware Acceleration — Neural Engine and Metal
    08-model-optimization.html             — Model Optimization — Making Models iPhone-Ready
    09-create-ml.html                      — Create ML — Training Your Own Models
    10-mlx-swift.html                      — MLX Swift and Open-Source Models
    11-production-deployment.html          — Model Management and Production Deployment
    12-ai-toolkit.html                     — Building Your On-Device AI Toolkit
    maps/                                  — Visual memory maps (generated on demand)
```

## Progress Tracking
- [x] Chapter 1: The On-Device AI Revolution
- [x] Chapter 2: How ML Models Work on Apple Silicon
- [x] Chapter 3: Your First Core ML Model
- [x] Chapter 4: Vision Framework — See Like an iPhone
- [x] Chapter 5: Natural Language, Speech, and Sound
- [x] Chapter 6: Foundation Models and Apple Intelligence
- [x] Chapter 7: Hardware Acceleration — Neural Engine and Metal
- [x] Chapter 8: Model Optimization — Making Models iPhone-Ready
- [x] Chapter 9: Create ML — Training Your Own Models
- [x] Chapter 10: MLX Swift and Open-Source Models
- [x] Chapter 11: Model Management and Production Deployment
- [x] Chapter 12: Building Your On-Device AI Toolkit

## Instructions for /generate-next-chapter
When the user invokes `/generate-next-chapter`:
1. Read this CLAUDE.md and find the first chapter marked with `[ ]` in Progress Tracking
2. Read the "Chapter Details" section below for that chapter's topics
3. Read `chapters/assets/style.css` for available CSS classes
4. Read `chapters/index.html` for navigation template
5. Read the previous chapter (if any) for context and smooth transition
6. **Use WebSearch** to find the latest iOS/Apple documentation and developer resources for this chapter's topics
7. Generate the HTML file in `chapters/` with full content (400-600 lines)
8. Update CLAUDE.md — mark the chapter as `[x]`
9. Update `chapters/index.html` — remove `pending` class from that chapter's card
10. Update navigation on the previous chapter if needed

## CSS Classes for Content
- `.device-benchmark` — on-device performance benchmark results (sapphire blue accent, unique to this course)
- `.model-pipeline` — ML data flow visualization: input → preprocess → inference → postprocess → output (teal accent, unique to this course)
- `.apple-framework` — Apple framework/API spotlight and compatibility info (gray accent, unique to this course)
- `.prompt-example.good` — good examples (green accent)
- `.prompt-example.bad` — bad examples (red accent)
- `.comparison` — side-by-side comparisons
- `.tip-box` — tips and advice
- `.warning-box` — warnings and cautions
- `.exercise-box` — hands-on exercises (teal accent)
- `.checklist` — checklists with checkmarks
- `.highlight-box` — key messages (gradient background)
- `.stats-grid` + `.stat-card` — statistics display
- `.tool-card` — tool description cards (icon + name + description)
- `.workflow-steps` + `.step` + `.step-arrow` — visual workflow pipeline
- `.theme-toggle` — theme switch button (in nav)

## Content Guidelines
- **At least one `.device-benchmark`** per chapter showing model performance metrics (inference time, memory, model size)
- **At least one `.model-pipeline`** per chapter showing data flow through the ML pipeline
- **At least one `.apple-framework`** per chapter with Apple framework/API information
- **At least one `.exercise-box`** per chapter where the reader builds or measures something real
- Keep code examples practical and real (Swift, Xcode config, Apple API calls — max 20-30 lines per snippet)
- Each chapter should end with a preview of how it connects to the next chapter
- Every chapter should produce something tangible: a working feature, a benchmark, or a deployed model
- Use analogies to bridge from iOS concepts the reader knows to ML concepts they don't

## Chapter Details

### Chapter 1: The On-Device AI Revolution
**File:** `01-on-device-revolution.html`
**Goal:** Convince the reader that on-device AI is the next frontier for iOS apps and give them a mental map of the Apple AI landscape.

**Topics:**
- Why on-device AI matters in 2026: privacy (data never leaves the device), latency (no network round-trip), offline capability, cost savings (no cloud API fees) — Apple's privacy-first philosophy makes this a differentiator, not just a feature
- Cloud AI vs on-device AI: a side-by-side comparison — latency (200ms cloud vs 10ms on-device), privacy (data sent to server vs stays on device), cost (per-request billing vs free after model download), capability (GPT-4 vs on-device Foundation Models)
- The Apple on-device AI stack: hardware (Neural Engine, GPU, CPU) → runtime (Core ML, Metal) → frameworks (Vision, NaturalLanguage, Speech, SoundAnalysis, Foundation Models) → your app
- What iOS does with on-device AI today: real examples — Siri (voice recognition), Photos (scene classification, Visual Look Up), Live Text (OCR), Spotlight search, on-device keyboard predictions, Journal suggestions
- Neural Engine progression: A11 (first Neural Engine, 2 cores, 600B ops/s) through A19 — each generation's capability jump, how Apple Silicon enabled on-device AI at scale
- The three categories of on-device AI on iOS: classical ML via Core ML (classification, detection), built-in intelligence frameworks (Vision, NaturalLanguage, Speech), and on-device generative AI (Foundation Models, Apple Intelligence)
- The "good enough" principle: on-device models are smaller but surprisingly capable for focused, narrow tasks — Apple's approach of specialized models over one giant model
- What you will build in this course: preview of features — image classifier with Core ML, document scanner with Vision, on-device text generation with Foundation Models, Metal-accelerated inference, custom model training with Create ML
- Prerequisites check: what the reader needs (Swift, SwiftUI, Xcode, a physical iPhone 15 Pro or newer) and what they do NOT need (ML theory, Python expertise, training infrastructure)
- Exercise: audit your current app (or a favorite App Store app) for 3 features that could benefit from on-device AI — estimate the user impact of each

### Chapter 2: How ML Models Work on Apple Silicon
**File:** `02-ml-models-apple-silicon.html`
**Goal:** Give the reader just enough ML understanding to be dangerous — what a model is, how Core ML works, and how Apple Silicon changes the game, without becoming ML engineers.

**Topics:**
- What an ML model actually is: a file containing learned numerical weights that transforms inputs into outputs — analogy: a compiled function you didn't write, it takes inputs and returns outputs, but you can't read the source code
- The inference loop on iOS: load MLModel → preprocess input → run prediction → postprocess output → display result — the core pattern you'll use in every chapter
- Core ML model formats: .mlmodel (compiled, single file) vs .mlpackage (directory bundle, supports larger models) — when you see each and why .mlpackage is becoming the default
- Tensors explained for iOS devs: multi-dimensional arrays — a UIImage is a 3D tensor (height × width × RGB channels), a sentence is a 2D tensor (tokens × embedding dimensions), MLMultiArray is how Core ML represents tensors
- Input preprocessing on iOS: why you can't just throw a UIImage at a model — CGImage conversion, pixel buffer creation with CVPixelBuffer, resizing to expected dimensions (224×224), normalizing pixel values, VNImageRequestHandler as the bridge
- Output postprocessing: raw model output is numbers (logits, probabilities stored in MLMultiArray) — you need to interpret them: find the highest probability, map index to label, apply confidence threshold
- Model metadata in Core ML: Xcode's model viewer shows input/output specs, class labels, author, license — the built-in "README" that tells you how to use the model
- Common model architectures iOS devs encounter: MobileNet (image classification, small and fast), YOLOv8 (object detection with bounding boxes), DeepLab (image segmentation), BERT variants (text tasks) — all available as .mlmodel
- The size-accuracy tradeoff on iOS: MobileNetV3 (2MB, fast, less accurate) vs EfficientNet (larger, more accurate) — choosing the right model for mobile constraints with Core ML's model size preview in Xcode
- Where to find pre-trained models: Apple's ML Gallery (curated, ready-to-use .mlmodel files), Hugging Face (exportable to Core ML via coremltools), TensorFlow Hub (convertible), Create ML (train your own)
- Exercise: download MobileNetV2 from Apple's ML Gallery, drag it into an Xcode project, inspect it in Xcode's model viewer — identify input shape, output shape, class labels, and file size

### Chapter 3: Your First Core ML Model
**File:** `03-first-core-ml-model.html`
**Goal:** Get the reader running a real ML model on their iPhone — converting a model with coremltools, integrating with Xcode, and running live camera inference in SwiftUI.

**Topics:**
- Setting up the project: creating a new Xcode project with SwiftUI, adding a Core ML model by dragging .mlmodel into the project navigator — Xcode auto-generates the Swift class
- Converting a PyTorch model with coremltools: installing coremltools via pip, writing the Python conversion script (ct.convert), specifying input type as ImageType, adding class labels, saving as .mlpackage
- Loading the model: the auto-generated Swift class (e.g., MobileNetV2), creating an instance with MobileNetV2(configuration:), understanding MLModelConfiguration for compute unit selection
- The VNCoreMLRequest workflow: wrapping your Core ML model in VNCoreMLModel, creating VNCoreMLRequest, feeding images through VNImageRequestHandler, reading VNClassificationObservation results
- Building the inference pipeline step by step: capture frame → convert to CVPixelBuffer → create VNImageRequestHandler → perform VNCoreMLRequest → read top-5 predictions with confidence scores
- Camera integration with AVFoundation: setting up AVCaptureSession, configuring AVCaptureVideoDataOutput, implementing AVCaptureVideoDataOutputSampleBufferDelegate, converting CMSampleBuffer to CVPixelBuffer
- Displaying results in SwiftUI: building a camera preview with UIViewRepresentable, overlaying classification labels and confidence percentages using ZStack and Text views, updating via @Published properties
- Threading strategy: running inference off the main thread with Swift concurrency (async/await), using @MainActor to push results to the UI, never blocking the camera pipeline
- Performance baseline: measuring inference time with CFAbsoluteTimeGetCurrent() — establishing benchmarks on iPhone 15 Pro (typically 5-15ms on Neural Engine, 30-80ms on CPU)
- Common pitfalls and fixes: model not found crash (not added to target), wrong input dimensions (model expects 224×224 but got 1920×1080), forgetting orientation handling (rotated results), running on main thread (dropped frames)
- Exercise: build a working image classifier that runs on your iPhone — photograph 10 different objects, record the top prediction and confidence for each, note which ones it gets right vs wrong and hypothesize why

### Chapter 4: Vision Framework — See Like an iPhone
**File:** `04-vision-framework.html`
**Goal:** Master Apple's Vision framework for production-ready computer vision features — text recognition, face detection, body pose, document scanning, and barcode scanning without any custom models.

**Topics:**
- What Vision is: Apple's high-level computer vision framework — pre-trained models maintained by Apple, optimized for each device, updated with every iOS release, zero model management on your part
- VNClassifyImageRequest: on-device image classification with Apple's built-in taxonomy — identifying scenes (beach, forest, office), objects (dog, car, food), activities (running, cooking) with confidence scores
- VNRecognizeTextRequest (OCR): extracting text from images with world-class accuracy — building a receipt scanner that reads text blocks, supports 18+ languages, fast vs accurate recognition levels, handling revision levels
- VNDetectHumanBodyPoseRequest: full-body skeletal tracking with 19 joint points — practical uses in fitness apps (rep counting, form correction), physical therapy (range of motion measurement), and interactive features
- VNDetectFaceRectanglesRequest and VNDetectFaceLandmarksRequest: face detection with 76 landmark points — building face-based features (AR overlays, face crop for profile photos, attention tracking)
- RecognizeDocumentsRequest (iOS 26): the new document intelligence API — automatically detecting, cropping, and classifying documents (receipts, IDs, business cards) with structured data extraction
- Barcode and QR scanning with VNDetectBarcodesRequest: fast, reliable scanning supporting 16+ symbologies (QR, EAN-13, Code 128, PDF417) — building a product lookup or ticket scanner feature
- Person segmentation with VNGeneratePersonSegmentationRequest: separating people from backgrounds at pixel level — building portrait mode, background replacement, and video effects in real time
- Combining multiple Vision requests: running text recognition + barcode detection + face detection in a single VNImageRequestHandler pass — performance implications and request ordering strategies
- Vision request configuration: VNImageRequestHandler vs VNSequenceRequestHandler (single image vs video frames), revision selection for backward compatibility, regionOfInterest for focused detection
- Exercise: build a "smart scanner" that combines VNRecognizeTextRequest + VNDetectBarcodesRequest — scan a receipt, extract all text lines and any barcodes, display structured results in SwiftUI

### Chapter 5: Natural Language, Speech, and Sound
**File:** `05-nlp-speech-sound.html`
**Goal:** Bring language understanding, speech processing, and sound classification to your app without cloud APIs — NLTagger, SpeechAnalyzer, SpeechTranscriber, and SoundAnalysis running entirely on-device.

**Topics:**
- NLTagger for named entity recognition: identifying people, places, organizations, and dates in text — building a "smart clipboard" that detects actionable entities in copied text, with support for 50+ languages
- Sentiment analysis with NLTagger: analyzing user reviews, messages, or feedback for sentiment scores (-1.0 to 1.0) — building a real-time sentiment indicator for a messaging or review feature
- NLEmbedding for semantic similarity: computing word and sentence embeddings on-device — building semantic search, finding similar items, duplicate detection, and recommendation features without a server
- SpeechAnalyzer (iOS 26): the new speech analysis API for real-time voice metrics — pitch, rate, jitter, shimmer, voicing probability, providing structured vocal quality data for health, accessibility, and communication apps
- SpeechTranscriber (iOS 26): the modern successor to SFSpeechRecognizer — streaming on-device speech-to-text with improved accuracy, language detection, and long-form audio support (lectures, meetings, conversations)
- Sound Analysis with SNClassifySoundRequest: identifying 300+ sound categories (applause, siren, dog bark, music genre, coughing) using Apple's built-in sound classifier — practical uses in accessibility, health monitoring, and smart home
- Building an audio classification pipeline: configuring AVAudioEngine to capture microphone input, feeding audio buffers to SNAudioStreamAnalyzer, processing SNClassificationResult with confidence thresholds
- Combining NLP and speech: using SpeechTranscriber for voice-to-text and then NLTagger for entity extraction and sentiment analysis on the transcript — a complete voice-to-intelligence pipeline running entirely on-device
- Multilingual considerations: NLLanguageRecognizer for automatic language detection, per-language model availability, handling mixed-language content gracefully
- Performance characteristics: NLTagger runs in microseconds (essentially free), Speech recognition uses ~50-100MB memory, Sound Analysis runs continuously with minimal battery impact — designing for sustained use
- Exercise: build an "AI Listener" that captures microphone input, transcribes speech with SpeechTranscriber, extracts entities with NLTagger, and classifies background sounds with SoundAnalysis — display all three streams simultaneously in SwiftUI

### Chapter 6: Foundation Models and Apple Intelligence
**File:** `06-foundation-models.html`
**Goal:** Harness Apple's on-device Foundation Models for text generation, guided output, tool calling, and integration with Apple Intelligence features — all running locally with zero cloud dependency.

**Topics:**
- What Foundation Models framework is: Apple's on-device generative AI API (iOS 26+) — a ~3B parameter language model running entirely on the Neural Engine, private by design, no data leaves the device, no API keys needed
- Device compatibility: which devices support Foundation Models (iPhone 15 Pro+, M1+ iPads and Macs), runtime capability detection with SystemLanguageModel.default availability check, graceful degradation for unsupported devices
- The @Generable macro: defining Swift structs that the model outputs conform to — guided generation that guarantees valid, typed output instead of raw text, eliminating parsing errors and hallucination of structure
- Guided generation with Swift types: constraining model output to your exact data shape — @Generable struct with String, Int, Bool, enum, and optional fields, the model fills in values that match your schema
- Tool calling: giving the model access to app functions — defining tools with parameter schemas, the model decides when to call which tool, executing tool results and feeding them back into the conversation
- Multi-turn sessions: maintaining conversation context across multiple prompts — LanguageModelSession management, context window considerations, when to start fresh vs continue
- Streaming responses: receiving tokens as they are generated — building responsive UI with AsyncSequence, showing partial results for better perceived performance
- Writing Tools API integration: hooking into the system-wide Writing Tools feature — making your app's text fields support Rewrite, Proofread, and Summarize without any model management
- Image Playground and Genmoji: programmatic access to on-device image generation — generating custom images and emoji within your app using the ImagePlayground framework
- On-device vs Private Cloud Compute: understanding when requests stay on-device vs when they route to Apple's secure cloud — transparency, user controls, and how to design features that work in both modes
- Prompt engineering for on-device models: why prompts that work on GPT-4 may need adjustment for smaller on-device models — shorter instructions, focused tasks, leveraging guided generation over free-form output
- Exercise: build an "AI Writing Assistant" that uses Foundation Models with @Generable to offer 4 text transformations (summarize, formalize, simplify, expand) — use guided generation to return structured results with confidence scores, streaming the output in real time

### Chapter 7: Hardware Acceleration — Neural Engine and Metal
**File:** `07-hardware-acceleration.html`
**Goal:** Understand and leverage the full power of Apple Silicon for ML — Neural Engine dispatch, Metal 4 tensor operations, GPU vs CPU vs ANE benchmarking, and thermal management.

**Topics:**
- The hardware inside your iPhone: CPU (general purpose, slowest for ML), GPU (massively parallel via Metal, great for custom kernels), Neural Engine / ANE (purpose-built for tensor operations, fastest for supported models) — how Apple Silicon unifies all three
- A-series Neural Engine progression: A11 (2 cores, 600B ops/s) through A19 — core count growth, TOPS (trillion operations per second) increase per generation, how each generation enables new on-device capabilities
- M-series comparison: how M1/M2/M3/M4/M5 chips relate to A-series — larger Neural Engines, more GPU cores, shared memory architecture advantage, why the same Core ML model runs differently on iPhone vs iPad vs Mac
- MLComputeUnits dispatch: controlling where your model runs — .all (let Core ML decide), .cpuAndGPU (skip Neural Engine), .cpuAndNeuralEngine, .cpuOnly — when to use each and why .all is usually best
- Metal 4 tensor operations: the new Metal API for direct GPU tensor math — native tensor support as first-class citizens, ML inference embedded in shader code, MetalPerformanceShaders for common operations
- GPU vs CPU vs Neural Engine benchmarking: measuring real inference time on each compute unit — building a benchmark harness with CFAbsoluteTimeGetCurrent(), measuring p50/p95/p99 latency, memory footprint per backend
- Warm-up runs: why the first inference is always slow (model compilation, shader compilation, Neural Engine initialization) — running 3-5 warm-up inferences before measuring or showing results to users
- Thermal management: sustained workload behavior — how iPhone throttles Neural Engine and GPU under thermal pressure, measuring performance degradation over 60 seconds of continuous inference, designing for thermal budgets
- Real device benchmarks: comparison table of MobileNetV2 inference across iPhone 15, 15 Pro, 16, 16 Pro, SE — showing CPU, GPU, and Neural Engine times for each, demonstrating the device diversity your app must handle
- Profiling with Instruments: using the Core ML Instrument, Metal System Trace, and Neural Engine Activity trace to identify bottlenecks — finding which operations fall back to CPU, measuring memory bandwidth
- Exercise: take the image classifier from Chapter 3, run it with .cpuOnly, .cpuAndGPU, .cpuAndNeuralEngine, and .all — measure the p50 latency on your device for each, plot the results, identify which compute unit wins and by how much

### Chapter 8: Model Optimization — Making Models iPhone-Ready
**File:** `08-model-optimization.html`
**Goal:** Transform models that are too big or too slow for iPhone into optimized versions — quantization, palettization, pruning, and the coremltools optimization pipeline.

**Topics:**
- Why optimization matters: a 500MB float32 model is unusable on iPhone — target benchmarks for shipping: model size under 50MB (ideally under 20MB), inference under 30ms on Neural Engine, runtime memory under 200MB
- Quantization explained: reducing numerical precision from float32 to float16, int8, or int4 — same learned patterns, 2-4x smaller file, 2-3x faster inference, typically less than 2% accuracy loss
- Post-training quantization with coremltools: the Python pipeline — ct.optimize.coreml.linear_quantize_weights() for weight-only quantization, choosing between int8 and int4, measuring accuracy impact
- Palettization (Apple's unique approach): clustering weights into a palette of 2^N values — 6-bit (64 values), 4-bit (16 values), 3-bit (8 values) palettization, often better accuracy-size tradeoff than pure quantization for Core ML models
- Joint compression: combining palettization with pruning for maximum compression — the coremltools pipeline for applying multiple compression techniques in sequence, measuring cumulative impact
- Pruning: removing weights that contribute little to accuracy — magnitude pruning with coremltools, achieving 50-90% sparsity, how the Neural Engine handles sparse models efficiently
- PyTorch to Core ML conversion pipeline: the complete workflow — torch model → torch.jit.trace or torch.export → ct.convert() → ct.optimize → validate → deploy, handling common conversion errors (unsupported ops, dynamic shapes)
- Size-accuracy tradeoff measurement: building a test harness that measures accuracy on a validation set before and after each optimization — establishing your "accuracy budget" (how much can you lose before users notice?)
- Hugging Face to Core ML: converting popular open-source models — using exporters and coremltools together, handling tokenizer conversion, verifying output equivalence between PyTorch and Core ML versions
- Model format considerations: .mlmodel vs .mlpackage, compiled .mlmodelc for faster loading, on-device compilation with MLModel.compileModel(at:), when to pre-compile vs compile on first launch
- Exercise: take a standard MobileNetV3 float32 model, apply int8 quantization, 6-bit palettization, and 4-bit palettization separately — measure size reduction and accuracy impact for each on 20 test images, then compare Neural Engine inference speed for each variant

### Chapter 9: Create ML — Training Your Own Models
**File:** `09-create-ml.html`
**Goal:** Train custom ML models entirely within the Apple ecosystem — using the Create ML app GUI and Create ML Components in Swift for image, text, sound classification, object detection, and on-device personalization.

**Topics:**
- Create ML app: Apple's no-code model training GUI — drag in labeled data, choose a model type, train, evaluate, and export .mlmodel — building an image classifier in under 10 minutes without writing Python
- Create ML model types: image classification, object detection, sound classification, text classification, word tagging, tabular classification/regression, recommendation, action classification, hand pose classification, body pose classification
- Image classification with Create ML: preparing a labeled image dataset (folder-per-class structure), configuring augmentations (crop, rotate, flip, blur, noise), training with transfer learning from Apple's base models, evaluating with confusion matrix
- Object detection training: annotating images with bounding boxes using Create ML's built-in annotation tool or importing from JSON/CSV, training a YOLO-based detector, evaluating with IoU and mAP metrics
- Create ML Components framework: the Swift API for building custom training pipelines in code — composable transformers, estimators, and feature extractors that run in your app
- On-device personalization with MLUpdateTask: updating a model on the user's device with their data — the privacy-preserving way to improve models without collecting user data, practical for personalized recommendations and user-specific classifiers
- Transfer learning in practice: fine-tuning Apple's base feature extractors on 50-200 images of your specific objects — the minimal viable dataset, when 100 images is enough, strategies for collecting training data
- Sound classification training: recording or collecting audio samples per category, configuring feature extraction parameters, training and evaluating — building a custom sound detector (e.g., specific machine sounds, pet sounds, accessibility alerts)
- Text classification training: preparing labeled text datasets, choosing between maximum entropy and transfer learning backends, handling imbalanced classes, evaluating precision/recall/F1
- Exporting and integrating: the trained model output is a standard .mlmodel file — drag into Xcode, use the same Core ML inference code from Chapter 3, no special integration needed
- Exercise: build a custom image classifier for 5 objects on your desk using Create ML — collect 30 photos per object, train with augmentation, evaluate accuracy, export to .mlmodel, and integrate into the SwiftUI camera app from Chapter 3

### Chapter 10: MLX Swift and Open-Source Models
**File:** `10-mlx-swift.html`
**Goal:** Run open-source language models on Apple Silicon with MLX Swift, llama.cpp, and ExecuTorch — choosing between Apple's Foundation Models and the open-source ecosystem.

**Topics:**
- What MLX is: Apple's open-source array framework for machine learning on Apple Silicon — designed for unified memory, lazy evaluation, composable transformations, and GPU acceleration via Metal
- MLX Swift (mlx-swift package): the Swift bindings for MLX — adding via Swift Package Manager, basic tensor operations (creation, arithmetic, matmul), how it maps to the Metal GPU automatically
- Running Llama/Mistral/Gemma with MLX Swift: downloading quantized models from Hugging Face, loading with MLX's model loading API, generating text with streaming output, managing memory for multi-billion parameter models
- llama.cpp on iOS: the C/C++ inference engine compiled for iPhone — adding via Swift Package Manager or as an Xcode framework, loading GGUF model files, configuring context length and batch size, Metal GPU acceleration
- ExecuTorch: Meta's on-device inference framework for PyTorch models — the alternative to Core ML for PyTorch-native workflows, supported backends (XNNPACK for CPU, Core ML delegate, MPS delegate)
- Model quantization formats: GGUF (llama.cpp's format with Q4_K_M, Q5_K_M, Q8_0 variants), MLX quantized formats, Core ML int4/int8 — choosing the right format for your runtime
- Memory management for large models: a 7B parameter model at 4-bit quantization needs ~4GB — device RAM constraints (iPhone 15 Pro has 8GB, SE has 4GB), mmap for lazy loading, unloading when backgrounded
- Choosing Apple Foundation Models vs open-source: Foundation Models (zero setup, guaranteed availability on supported devices, guided generation, tool calling) vs open-source (model choice, fine-tuning, larger context windows, runs on more device classes)
- Performance comparison: benchmarking tokens-per-second for Foundation Models vs Llama 3.2 3B (MLX) vs Mistral 7B (llama.cpp) on iPhone 16 Pro — latency, memory, thermal behavior, quality differences
- Building a model selection layer: runtime detection of device capability, choosing the best available model (Foundation Models if available, fall back to smaller open-source model, fall back to cloud API), unified Swift interface
- Exercise: set up MLX Swift in a new project, download a quantized Llama 3.2 1B model, build a simple chat interface in SwiftUI with streaming token output — measure tokens/second and memory usage on your device

### Chapter 11: Model Management and Production Deployment
**File:** `11-production-deployment.html`
**Goal:** Ship on-device AI features to production with confidence — model packaging, App Store guidelines, device capability detection, error handling, and performance monitoring.

**Topics:**
- The production gap: "it works on my iPhone 16 Pro" is not enough — the device diversity reality: iPhone SE (4GB RAM, A15) to iPhone 16 Pro Max (8GB RAM, A18 Pro), different Neural Engine capabilities, different iOS versions
- Model bundling strategies: embedded in app bundle (instant availability, increases download size), on-demand resource tags (downloaded after install, Apple manages storage), Background Assets framework for large models
- App Store guidelines for AI: Apple's review guidelines on model size (binary size limits, on-demand resources for large models), privacy requirements (App Privacy Report disclosures), and content policy (generated content must comply with guidelines)
- CloudKit for model distribution: hosting model files on CloudKit for dynamic delivery — versioning, conditional downloads based on device capability, background downloading, retry logic
- Device capability detection at runtime: checking Neural Engine availability with MLModel.availableComputeDevices, reading ProcessInfo.physicalMemory for RAM checks, using UIDevice for model identification — deciding which model variant to load
- A/B testing models: running two model versions on different user segments — using Firebase Remote Config or your own feature flag system to assign model variants, measuring accuracy, latency, and user engagement
- Error handling and graceful degradation: model loading failure (corrupt download, insufficient memory), inference crash (unexpected input shape), low-quality output — fallback UIs, disabling features on incapable devices, logging errors with OSLog
- Memory management in production: model lifecycle (load on view appear, unload on view disappear), responding to memory warnings with didReceiveMemoryWarning, using autoreleasepool for batch inference, monitoring with Xcode Memory Graph
- Performance monitoring: tracking p50/p95 inference latency, success rate, model load time using MetricKit and os_signpost — custom metrics with Firebase Analytics or your analytics platform, alerting on regressions
- Privacy compliance: on-device processing as an App Store and regulatory advantage — Apple's App Tracking Transparency, no data leaving the device means simplified GDPR/CCPA compliance, communicating "processed on your device" to users
- Update strategy: when to update models (new iOS version, accuracy improvements, bug fixes), staged rollouts, rollback mechanism, ensuring backward compatibility with older model versions still cached on user devices
- Exercise: take any feature from earlier chapters and add production hardening — device capability check with graceful fallback, error handling for model load and inference failures, performance telemetry with os_signpost, and memory management with proper lifecycle

### Chapter 12: Building Your On-Device AI Toolkit
**File:** `12-ai-toolkit.html`
**Goal:** Consolidate everything into a reusable decision framework, build a toolkit abstraction, and chart a roadmap for staying current as on-device AI evolves.

**Topics:**
- The on-device AI decision framework: given a feature requirement, how to choose — Vision framework (easiest for CV tasks, zero model management), Core ML with custom models (any model, most flexible), Foundation Models (generative tasks, iOS 26+), MLX Swift (open-source models, maximum control)
- Building a reusable inference wrapper: a Swift protocol and class that handles model loading, compute unit selection, warm-up, preprocessing, inference, postprocessing, error handling, and performance measurement — the pattern for every future on-device AI feature
- Multi-model pipelines: running several models as a pipeline — detect face with Vision → crop → classify emotion with Core ML → generate response with Foundation Models — pipeline design, memory budgets, async scheduling with Swift concurrency
- Edge cases and failure modes: adversarial inputs (unusual angles, extreme lighting), out-of-distribution data (objects the model never saw), environmental factors (motion blur, occlusion, low light) — building robust features with confidence thresholds and fallback behavior
- The model evaluation checklist: 6 metrics to measure before shipping — accuracy (does it get the right answer?), latency (fast enough for real-time?), model size (fits the download budget?), memory (runs without jetsam termination?), power (drains battery?), device coverage (what % of your users can run it?)
- The complete capstone architecture: designing an app that combines Vision (document scanning), NaturalLanguage (entity extraction), Foundation Models (summarization), and Sound Analysis (ambient classification) — demonstrating how all pieces work together
- Device diversity as a design constraint: building a capability matrix (iPhone SE can run Vision + NaturalLanguage, iPhone 15 Pro can add Foundation Models, iPad with M-series can add MLX models) — progressive enhancement, not lowest common denominator
- Privacy as a competitive advantage: Apple's end-to-end privacy story — on-device processing, differential privacy in Create ML, Private Cloud Compute transparency, App Privacy Report — positioning your app's AI features as trustworthy
- Keeping up with the landscape: key resources — Apple ML documentation, WWDC sessions, Apple ML Research blog, Hugging Face Core ML community, MLX GitHub repository, coremltools release notes
- What is coming next: predictions for Core AI at WWDC 2026, on-device multimodal models, LoRA adapters for user-personalized Foundation Models, larger context windows, MLX expansion across all Apple platforms
- Exercise: design an on-device AI feature for your own app — write a technical design document covering: problem statement, framework selection (with rationale), optimization strategy, device coverage matrix, fallback behavior, privacy considerations, and estimated timeline
