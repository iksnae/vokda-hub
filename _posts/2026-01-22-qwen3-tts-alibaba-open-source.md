---
layout: post
title: "Qwen3-TTS: Alibaba Releases Open-Source TTS Trained on 5 Million Hours"
date: 2026-01-22
tags: [release, open-source, alibaba, multilingual]
summary: "Alibaba Cloud's Qwen team releases Qwen3-TTS — two model sizes (0.6B and 1.7B), 10 languages, voice cloning, free-form voice design via natural language, and streaming support. Apache 2.0."
---

Alibaba's Qwen team released Qwen3-TTS on January 22nd — a series of open-source TTS models with two size variants (0.6B and 1.7B), covering 10 languages with voice cloning, streaming, and a capability that stands out: **voice design via natural language instructions**.

## What Qwen3-TTS Does Differently

Most TTS models give you a set of pre-defined voices to choose from. Qwen3-TTS adds **voice design** — you describe the voice you want in natural language and the model generates it:

```python
# Instead of choosing "voice_id: en_us_001"
# You write:
voice_prompt = "A warm, mid-30s American woman with a slightly husky voice. 
                Measured pace, sounds like a podcast host."
```

The model interprets that description and synthesizes a voice matching those characteristics. Combined with traditional voice cloning (provide reference audio), this gives developers two paths to custom voice creation: describe it from scratch, or clone from an existing recording.

This is a genuinely novel capability for an open-source model. Cloud providers have offered similar features at enterprise pricing tiers. Getting it in an Apache 2.0 model changes the access equation significantly.

## Scale of Training

Qwen3-TTS was trained on over **5 million hours of speech data** across its 10 covered languages. For context, most open-source TTS models train on thousands to tens of thousands of hours. Five million hours means the model has heard vastly more linguistic variety, accent diversity, and prosodic patterns — which shows up in the output's naturalness across languages.

## Languages

10 languages with full feature support: **Chinese, English, Japanese, Korean, German, French, Russian, Portuguese, Spanish, and Italian**, plus multiple dialectal voice profiles within supported languages.

The Chinese and Japanese coverage in particular is stronger than most Western-developed TTS models, which tend to treat East Asian languages as afterthoughts.

## Architecture

The core innovation is the **Qwen3-TTS-Tokenizer-12Hz** — a custom neural codec running at 12Hz that converts audio to discrete tokens. The architecture:

1. Text input → semantic tokens via the language model backbone
2. Semantic tokens → acoustic tokens via the 12Hz tokenizer  
3. Acoustic tokens → 24kHz waveform via the decoder

Running at 12Hz means 12 acoustic frames per second, which enables streaming output — you start hearing audio before the full generation is complete.

## Model Sizes

**Qwen3-TTS-0.6B** — 600M parameters. Faster inference, smaller memory footprint. Good for edge deployment and lower-latency applications where full model quality isn't needed.

**Qwen3-TTS-1.7B** — 1.7B parameters. Higher quality, better voice cloning fidelity, stronger multilingual output. The recommended choice for production quality.

HuggingFace: `Qwen/Qwen3-TTS-0.6B` and `Qwen/Qwen3-TTS-1.7B`  
Paper: [arxiv.org/abs/2601.15621](https://arxiv.org/abs/2601.15621)

## API Access

Beyond self-hosting, Qwen3-TTS is available via Alibaba Cloud's DashScope API for developers who want model quality without infrastructure overhead. vLLM support is included for high-throughput deployments.

## Who It's For

Qwen3-TTS lands hardest for:

- **Asian language applications** — the Chinese and Japanese quality is meaningfully better than other open-source alternatives
- **Multilingual products** needing consistent voice quality across 10 languages
- **Developers wanting custom voice creation** without enterprise cloud API costs
- **Privacy-sensitive applications** — fully self-hostable with no external API dependency
- **Researchers** — the pretraining framework is available for fine-tuning on custom languages and domains

The voice design capability alone makes it worth evaluating for any project where "pick from a list of 6 pre-made voices" isn't good enough.

[Explore open models on Vokda →](https://vokda.iknsae.com/models)
