---
layout: post
title: "CosyVoice 2: Alibaba's Streaming TTS Hits Human-Parity Naturalness"
date: 2026-03-06
tags: [research, open-source, alibaba, streaming]
summary: "CosyVoice 2 achieves human-parity naturalness in streaming mode by combining a pre-trained LLM backbone with chunk-aware causal flow matching — single model handles both streaming and non-streaming synthesis."
---

Alibaba's FunAudioLLM team released CosyVoice 2, an improved streaming speech synthesis model that claims human-parity naturalness with minimal response latency. The paper and weights are available at [github.com/FunAudioLLM/CosyVoice](https://github.com/FunAudioLLM/CosyVoice).

The original CosyVoice was already strong — multilingual, high prosody naturalness, solid speaker similarity in zero-shot settings. CosyVoice 2 is a systematic overhaul focused on one thing the original didn't nail: **making streaming work without quality loss**.

## The Core Problem With Streaming TTS

Most TTS models are built for offline (non-streaming) generation: process the full text, generate the full audio, deliver it. Streaming requires the model to produce audio chunks incrementally while more text is still being processed — which creates a tension between latency (start delivering audio quickly) and quality (the model has less context when generating each chunk).

The standard approaches either sacrifice quality for speed or require separate models for streaming and non-streaming use cases. CosyVoice 2 takes a different approach.

## What's New

**Finite-scalar quantization (FSQ)** replaces the original residual vector quantization for speech tokens. FSQ improves codebook utilization — more of the learned codebook gets used in practice, which means the model's representations are richer and less wasteful. Better codebook utilization translates directly to higher-quality reconstructed audio.

**LLM backbone** — rather than training a custom text-speech language model from scratch, CosyVoice 2 uses a pre-trained LLM directly as the backbone for the text-to-speech token prediction step. This is architecturally significant: pre-trained LLMs have better text understanding, better handling of rare words and unusual syntax, and better prosody modeling from the sheer scale of their pre-training. Plugging one in rather than training a smaller custom model is both cheaper and better.

**Chunk-aware causal flow matching** is the key innovation for streaming. Flow matching generates audio by learning a continuous transformation from noise to speech signal. The "chunk-aware causal" variant divides the generation into chunks that can be processed sequentially while respecting causal constraints — each chunk depends only on previously processed context, not future text. This enables streaming delivery without a separate streaming model:

- **Streaming mode:** Generate and deliver audio chunks incrementally as text arrives
- **Non-streaming mode:** Same model, same weights — process full context for maximum quality
- **Virtually lossless** quality in streaming vs. non-streaming mode

## Why This Matters for Voice Agents

The practical implication: a single CosyVoice 2 deployment handles both use cases — real-time conversational applications *and* high-quality batch generation — without running two separate models or maintaining two serving pipelines. For teams building mixed-use voice infrastructure, that simplification has real operational value.

The latency numbers (from their demo page at [funaudiollm.github.io/cosyvoice2](https://funaudiollm.github.io/cosyvoice2)) show response latency competitive with commercial streaming APIs while maintaining naturalness that evaluators rated on par with human speech.

## Open Source

Code and pretrained models: `github.com/FunAudioLLM/CosyVoice`  
Paper: [arxiv.org/abs/2412.10117](https://arxiv.org/abs/2412.10117)

Alibaba has been on a run with open audio models — CosyVoice 2 follows Qwen3-TTS (released January 22nd) and continues to show the FunAudioLLM team as one of the most productive groups in open-source speech synthesis.

[Explore open models on Vokda →](https://vokda.iknsae.com)
