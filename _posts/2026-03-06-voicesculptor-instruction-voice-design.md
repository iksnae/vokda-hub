---
layout: post
title: "VoiceSculptor: Design a Voice With Words, Not Sliders"
date: 2026-03-06
tags: [research, open-source, voice-design, instruction-following]
summary: "Northwestern Polytechnical University releases VoiceSculptor — an open-source system combining instruction-following voice design (describe pitch, age, emotion, style in plain language) with high-fidelity voice cloning in a single framework."
---

The standard TTS workflow has a narrow voice selection step: pick from a list, upload a reference clip, or accept whatever the API gives you. **VoiceSculptor** from Northwestern Polytechnical University's ASLP group takes a different approach — describe the voice you want in natural language, and the system builds it.

The paper ([arXiv:2601.10629](https://arxiv.org/abs/2601.10629)) was published in January 2026 and the code and pretrained models are fully open-sourced.

## The Problem It Solves

Fine-grained voice control has been a gap in open-source TTS for a long time. Commercial systems like ElevenLabs' audio tags (`[excited]`, `[whispers]`) and Qwen3-TTS's voice design feature offer varying degrees of natural-language control, but they're either closed-source or limited to a small attribute set.

What's missing in open-source: a system that lets you specify attributes like **pitch, speaking rate, age, emotion, and style** in free-form text and get predictable, high-quality results. VoiceSculptor is the first open-source system to address this coherently.

## How It Works

VoiceSculptor is a two-stage pipeline:

**Stage 1: Voice Design**  
You provide a natural-language description of the voice you want:

> "A calm, middle-aged man with a slight Southern American accent. Deep voice, measured pace, sounds trustworthy."

The system uses a language model to interpret this description and generate a **speaker embedding** — a compact vector representation capturing the described vocal characteristics. Crucially, this uses **Retrieval-Augmented Generation (RAG)**: the model retrieves similar voice descriptions and their corresponding embeddings from a reference database, then synthesizes a new embedding that fits your description.

This RAG approach enables iterative refinement — if the output isn't right, you can describe what to adjust:

> "A bit younger, more energetic, less Southern."

The system retrieves updated references and adjusts the embedding accordingly.

**Stage 2: Voice Cloning**  
The designed speaker embedding is rendered into a reference waveform, which is then fed into a high-fidelity voice cloning model. The cloning model uses that reference to condition synthesis of your actual text.

The two-stage separation matters: voice design and voice rendering are decoupled, which means either stage can be improved independently.

## What You Can Control

- **Pitch** — high, low, conversational, dramatic
- **Speaking rate** — measured, fast, casual
- **Age** — young, middle-aged, elderly
- **Emotion** — calm, warm, authoritative, energetic
- **Style** — podcast host, newscaster, character, narrator
- **Accent/dialect** — with reasonable latitude
- **Multi-attribute combinations** — all of the above simultaneously

## Benchmark Results

VoiceSculptor achieves open-source state-of-the-art on **InstructTTSEval-Zh**, the primary benchmark for instruction-controlled TTS. The evaluation measures how well synthesized speech matches the described attributes — not just audio quality, but attribute fidelity.

## Why It Matters

The Qwen3-TTS voice design feature covers similar ground (describe a voice, get it), but it's tied to the Qwen3 model family and requires its specific architecture. VoiceSculptor is architecture-agnostic — the voice design frontend can in principle be paired with different cloning backends.

For developers building products that need custom voices without a recording session — branded assistants, character voices, personalized narration — VoiceSculptor provides a path that's never been available in open-source before.

Paper: [arxiv.org/abs/2601.10629](https://arxiv.org/abs/2601.10629)  
Code + models: Northwestern Polytechnical University ASLP / WeNet Open Source Community

[Explore open models on Vokda →](https://vokda.iknsae.com)
