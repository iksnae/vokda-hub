---
layout: post
title: "Inworld TTS-1.5 Claims Top Quality Benchmark at $10/1M Chars — 25x Cheaper Than Alternatives"
date: 2026-01-21
tags: [release, inworld, pricing]
summary: "Inworld AI enters the TTS market with TTS-1.5 — claiming ELO 1,160 benchmark performance (highest rated) at $5–10 per million characters. If the numbers hold, it's the most significant pricing disruption the TTS market has seen."
providerId: inworld
---

Inworld AI launched TTS-1.5 on January 21st with a provocative claim: best quality *and* cheapest price. Those two things don't usually go together, and the TTS industry noticed.

## The Numbers

- **Pricing:** $5–10 per million characters (TTS-1.5 Mini at $5, TTS-1.5 Max at $10)
- **Benchmark:** ELO score of 1,160 — which Inworld claims is #1 in quality evaluations for real-time TTS
- **Latency:** Sub-250ms time-to-first-audio for TTS-1.5 Max
- **Comparison:** ElevenLabs Multilingual v2 at $206/1M characters for their #6-ranked model

If accurate, TTS-1.5 Max is 20x cheaper than ElevenLabs at higher ranked quality. Even against the cheapest commodity providers (AWS Polly Neural at $16/1M, Google Neural2 at $16/1M), Inworld is 1.6x cheaper.

## Why the Price Gap Is Possible

Inworld built their TTS infrastructure from scratch rather than adapting existing models. They've been running voice AI for game characters at scale since 2021 — processing enormous volumes of TTS for NPC dialog in games. That operational scale allowed them to build infrastructure optimized for cost efficiency in a way that general-purpose providers haven't.

The result, according to their announcement, is a fundamentally different cost structure — not a temporary introductory price designed to acquire customers.

## What You Actually Get

Two model variants:

**TTS-1.5 Mini** — $5/1M chars. Optimized for minimal latency. Best when time-to-first-audio is the absolute priority and cost is the binding constraint.

**TTS-1.5 Max** — $10/1M chars. Best quality, sub-250ms latency. Their recommended default for most production applications.

Enterprise plans include data sovereignty options — audio processing stays within your infrastructure. This is meaningful for regulated industries and privacy-sensitive applications.

## The Benchmark Skepticism

Inworld's ELO benchmark is self-reported, based on their own evaluation framework. They claim #1 ranking with a score of 1,160. The Vokda position: treat benchmark rankings from providers about their own products with appropriate skepticism.

That said, the pricing story doesn't depend on the benchmark being accurate. At $10/1M chars, TTS-1.5 Max is worth evaluating on its own terms regardless of where it ranks. Independent evaluations from developers on Reddit and the HuggingFace community put it in the top tier for naturalness, though not unanimously ahead of Cartesia Sonic 3 for real-time feel.

## Practical Implications

If you're currently paying ElevenLabs rates for a non-creative-content use case (an assistant voice, notifications, documentation readback), Inworld TTS-1.5 is worth a direct comparison. The quality ceiling might be lower for highly expressive content, but for utility voice applications, the cost savings at scale are significant.

At 10M characters/month:
- ElevenLabs Multilingual v2: ~$2,060
- Google Neural2: ~$160
- AWS Polly Neural: ~$160
- **Inworld TTS-1.5 Max: ~$100**

That delta compounds fast.

[Browse voices on Vokda →](https://vokda.iknsae.com)
