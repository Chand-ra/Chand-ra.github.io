---
title: "KittenCast: A local, lightweight document to audiobook compiler"
date: 2026-03-22
---

### **KittenCast: A local, lightweight document-to-audiobook compiler**

I’m excited to share a project I’ve been working on: [KittenCast](https://github.com/Chand-ra/KittenCast), a lightweight CLI tool that converts EPUBs, PDFs, Word docs, and plain text files into audiobooks.

The core requirement was strict: **100% local operation.** No data leaks to cloud APIs, no unexpected usage costs: just your personal library and your CPU. 

### Why I Built It

There are plenty of cloud-based TTS APIs, but for long-form content like books, they become incredibly expensive. Furthermore, many readers prioritize privacy for their personal document libraries.

I chose to build this around [**KittenTTS**](https://github.com/KittenML/KittenTTS) because it offers an incredible balance of quality and efficiency. When the entire synthesis model fits in under 25MB (Nano model), true decentralized audiobook creation becomes viable on standard hardware.

### How It Works

The architecture is designed to be modular and resilient:

1.  **Format Extraction (`EbookLib`, `pypdf`, `python-docx`):** The tool automatically routes files based on extension to the correct parsing logic.
2.  **Intelligent Sentence Tokenization (NLTK):** TTS models have limited context windows and struggle with very long strings. Instead of naive cutting (which chops words in half), I integrated NLTK’s `sent_tokenize` to split the text logically at sentence boundaries.
3.  **Synthesis (KittenTTS):** These safe chunks are fed sequentially to the model, generating audio arrays for each.
4.  **Assembly (`NumPy`, `Soundfile`):** We concatenate the resulting arrays, injecting calculated 0.4-second silences between sentence chunks to create natural-sounding pacing and breaks.

### Features

I focused on making this a tool someone would actually want to use:

* **CLI First:** Full support for argument parsing (voices, model sizes, output paths).
* **Progress Tracking:** Integrated `tqdm` progress bars for granular synthesis tracking.
* **Diagnostic Text Dumping:** Use the `--dump-text` flag to save the *extracted* text *before* synthesis. This is crucial for verifying if a glitch is an extraction issue or a model issue.

### Performance Profiling: Speed and Resource Efficiency

Before diving into the qualitative analysis, I profiled the three KittenTTS models to see how they actually handle resource allocation during local inference. 

| Model Size | Init Time | Model RAM | Peak RAM | Inference Time | RTF (Lower is better) |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **nano** | 6.37s | 88.1 MB | 142.2 MB | 1.48s | 0.078x |
| **micro** | 7.83s | 90.6 MB | 145.8 MB | 6.18s | 0.306x |
| **mini** | 8.54s | 99.9 MB | 206.9 MB | 10.84s | 0.630x |

The efficiency here is fantastic. Even the highest-fidelity `mini` model peaks at just over 200 MB of RAM and maintains a Real-Time Factor (RTF) of 0.630x. The `nano` model, however, is the clear winner for rapid CLI deployment, generating audio more than 10 times faster than real-time (0.078x) with a microscopic memory footprint.

### Model Analysis: Where KittenTTS Fails

This brings me to the core engineering analysis required for model improvement. While the speed and voice fidelity of the three KittenTTS models are impressive for their size, my tests revealed distinct edge cases in a production scenario.

*(Note: The exact text snippets and documents used to isolate all of the following failure cases are available in the `tests/fixtures` directory of the repository so you can easily reproduce them locally.)*

#### A. The Complex Formatting (pdf) Challenge
Raw math notation or LaTeX (e.g., \(E=mc^2)\) is synthesized as absolute gibberish by the TTS engine. Even with a layout-aware parser, listening to a TTS read out raw equations character-by-character is a terrible user experience.

#### B. Lexical Normalization & Symbolic Data
The models misinterpret non-standard English formats.

* **Phone Numbers & Identifiers:** The model consistently attempts to read contiguous numerical blocks as standard integers. A phone number like `7782934627` is synthesized as "seven billion, seven hundred eighty-two million...", rather than a sequence of discrete digits. It also stumbles on regional formatting like `+49 30 1234567` or `(800) 555-1234`, where parentheses and plus signs cause unnatural pauses or are ignored entirely.
* **Email Addresses:** Complex strings like `alex.jones_dev@demo.net` expose the model's inability to handle special characters gracefully. Underscores are entirely ignored, while dots are treated as full stops, causing unnatural pauses mid-address. Furthermore, numbers preceding domains (`chandrapratap376`) are read as hundreds or thousands rather than individual characters, breaking the flow of contact information.
* **Acronyms vs. Initialisms:** The model struggles to differentiate between acronyms read as words (like ZIP) and initialisms read as letters (like WHO or S.W.A.L.K.). It tends to default to phonetic pronunciation, resulting in "WHO" being read as the interrogative pronoun ("who") rather than "W-H-O."

#### C. Semantic Lookahead & Phonetic Mapping
The models struggle when pronunciation requires deep contextual understanding.

* **Heteronyms (Context-Dependent Pronunciation):** The models fail on sentences like *"The nurse wound the bandage around the wound"* or *"A single tear fell when she saw the tear in her dress."* Without sufficient lookahead, the most statistically common pronunciation for the spelling is applied, destroying the grammatical meaning of the sentence.
* **Loanwords & Irregular Orthography:** Words with non-English phonetic roots entirely break the G2P rules. Terms like *Chiaroscuro*, *Synecdoche*, *Bologna*, *Victual*, and *Boatswain* are synthesized with brute-force phonetic English rules, rendering them completely unrecognizable. 

#### D. Prosody, Pacing, and Contextual Emotion
The models struggle to generate dynamic, human-like pacing when the text deviates from standard declarative prose.

* **Dialogue & Rapid Exchanges:** When fed complex dialogue (like excerpts from Oscar Wilde featuring rapid back-and-forths, internal quotes, em-dashes, and exclamations), the prosody flattens. The model does not modulate its pitch to differentiate between speakers, nor does it recognize the em-dash (`—`) as a cue for a dramatic pause or interruption, leading to a robotic, run-on delivery of highly emotional text.
* **The "Long Sentence" Exhaustion:** When presented with a 250+ word run-on sentence lacking standard punctuation boundaries (periods, commas, semicolons), the audio generation degrades. Because the NLTK chunker relies on punctuation to split inputs, massive unbroken text blocks force the model to hold too much in its context window. This results in unnatural mid-sentence pauses and incorrect pronunciations for otherwise common words (like "shadow").

#### E. Multimodal & Multilingual Contamination
Real-world texts are rarely perfectly clean, single-language ASCII.

* **Emojis & Unicode Symbols:** In modern texts like travel itineraries, the inclusion of emojis (📅, ✈️, 🥂) causes unpredictable behavior. The underlying text normalizer attempts to read the literal alt-text descriptions ("smiling face with sunglasses"), which destroys the narrative immersion. Similarly, standard units are often misread. For instance, **15°C** is pronounced literally as "fifteen degree see".
* **Code-Switching & Non-Latin Scripts:** When encountering foreign phrases like *Chère Renée-Louise*, *Amicalement*, or Devanagari script, the models apply a heavy, broken English accent to the words, completely losing the intended phonetics.

### Next Steps

KittenCast is a powerful proof of concept for local audiobook generation. The next architectural pivot would be addressing the academic paper issue, likely building a pre-processing agent to "clean" raw math from text before synthesis.

**You can check out the repository and start building your own local audiobook library [here](https://github.com/Chand-ra/KittenCast).**

Feedback, issues, and PRs are all very welcome!
