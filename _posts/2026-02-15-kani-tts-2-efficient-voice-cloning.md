---
layout: post
title: "Kani-TTS-2: 400M Parameters, 3GB VRAM, Voice Cloning — Trained in 6 Hours"
date: 2026-02-15
tags: [release, open-source, kani, efficiency]
summary: "nineninesix.ai releases Kani-TTS-2 — a 400M parameter model using LiquidAI's LFM2 architecture and NVIDIA NanoCodec. Zero-shot voice cloning on 3GB VRAM, with a Real-Time Factor of 0.2. Apache 2.0."
---

Kani-TTS-2 is a new open-source TTS model from nineninesix.ai that makes an interesting argument about where the efficiency ceiling is in 2026: 400 million parameters, 3GB VRAM, zero-shot voice cloning, real-time capable — and trained on 10,000 hours of speech data in six hours.

That training time is the thing worth pausing on.

## The Architecture: LFM2 + NanoCodec

Kani-TTS-2 is built on two components that aren't the usual open-source TTS stack:

**LFM2 (LiquidAI Liquid Foundation Model 2)** — a 350M parameter language backbone from LiquidAI designed for efficiency. LFMs use a different architecture from standard transformers — specifically designed to run fast on constrained hardware without sacrificing output quality. The Kani team uses LFM2 as the "audio intent" predictor: it generates sequences of audio tokens that represent what should be said.

**NVIDIA NanoCodec** — converts those audio tokens into 22kHz waveforms. NanoCodec is a neural audio codec specifically built for efficiency — it achieves high-fidelity reconstruction at low bitrates, which keeps memory requirements down.

The combination: **Audio-as-Language**. The model never works with mel-spectrograms or raw waveforms during inference — everything is discrete tokens until the final NanoCodec decode step. This is what enables the 3GB VRAM footprint.

## Training Efficiency

The numbers are striking. The English model was trained on 10,000 hours of high-quality speech data using 8 NVIDIA H100 GPUs — total training time: **6 hours**.

To put that in context: training a comparable-scale TTS model on traditional architectures with similar data would typically take days to a week on the same hardware. The LFM2 architecture's training efficiency is a meaningful part of the story here — it suggests that the model family can be extended, fine-tuned, and adapted to new languages or domains cheaply.

## Zero-Shot Voice Cloning

Voice cloning works via **speaker embeddings** — no fine-tuning required. The workflow:

1. Provide a short reference audio clip (a few seconds)
2. The model extracts speaker characteristics as an embedding
3. Inference uses that embedding to condition all output

This is standard zero-shot cloning architecture, but Kani-TTS-2 runs it at 400M parameters and 3GB VRAM — which means it fits on consumer GPUs like the RTX 3060 or 4050. Previously this quality of zero-shot cloning required hardware that most developers don't have locally.

## Performance

- **Real-Time Factor: 0.2** — generates 10 seconds of audio in ~2 seconds. Faster than real-time, but not fast enough for sub-200ms conversational use without optimization.
- **VRAM:** 3GB — runs on consumer GPUs, not just research clusters
- **Sampling rate:** 22kHz
- **License:** Apache 2.0

## Languages

Currently available in **English** (`nineninesix/kani-tts-2-en`) and **Portuguese** (`nineninesix/kani-tts-2-pt`). The team describes language expansion as ongoing — the pretraining framework is released publicly, which means community-contributed language fine-tunes are likely.

## The Open Pretraining Framework

Beyond the model weights, nineninesix.ai released the complete pretraining code. This is the part that matters most for researchers and teams building specialized applications:

- Train a new language variant from scratch using the same architecture
- Fine-tune for a specific accent, domain, or speaker style
- Adapt the codec to different audio characteristics

This positions Kani-TTS-2 less as a finished product and more as a platform for building custom TTS — which is genuinely different from most open releases that ship weights only.

## Bottom Line

For developers who need voice cloning on consumer hardware, Kani-TTS-2 is the most accessible option currently available. The LFM2 architecture is worth watching — if training efficiency compounds across larger model sizes, the team at nineninesix.ai may have more to release.

HuggingFace: `nineninesix/kani-tts-2-en` | `nineninesix/kani-tts-2-pt`

[Explore open models on Vokda →](https://vokda.iknsae.com/models)
