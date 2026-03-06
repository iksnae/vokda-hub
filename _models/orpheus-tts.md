---
layout: profile
title: "Orpheus TTS"
type: open_model
license: "Apache 2.0"
parameters: "~3B"
huggingface: https://huggingface.co/canopylabs/orpheus-tts-0.1-pretrain-prod
pricing: "Free (self-hosted)"
languages: "English"
voices: "8 named voices"
summary: "Canopy Labs' 3-billion-parameter open TTS model with 8 distinct named voices. Highest quality open-source English TTS available — comparable to top cloud providers for narration and content generation."
tags: [high-quality, narration, self-hosted, expressive]
---

Orpheus is the highest-quality openly available English TTS model. At 3 billion parameters it requires real compute to run, but the output quality justifies it for applications where audio quality is a product differentiator.

## Background

Canopy Labs released Orpheus as a genuine research contribution — Apache 2.0 licensed, no enterprise gating, no "community edition" restrictions. The model is the model.

The design philosophy prioritizes voice character: the 8 named voices have distinct personalities, not just tonal variations. They were designed to feel like a voice cast rather than parameter variations.

## Technical Details

- **Parameters:** ~3 billion
- **License:** Apache 2.0
- **HuggingFace:** `canopylabs/orpheus-tts-0.1-pretrain-prod`
- **Language:** English
- **Inference:** Requires GPU for reasonable speed; M-series Mac viable via MLX at reduced throughput

## Quality Comparison

At its best, Orpheus output is competitive with ElevenLabs standard voices and significantly better than AWS Polly Neural or Google WaveNet. The gap shows most clearly in:
- Long-form narration (naturalness over multiple paragraphs)
- Voices with strong character (the model doesn't flatten into neutrality)
- Edge cases (unusual words, mixed formatting, unconventional punctuation)

## 8 Named Voices

The voice catalog covers: `tara`, `leah`, `jess`, `leo`, `dan`, `mia`, `zac`, `zoe`. Each has distinct gender presentation, age impression, and tonal style — sufficient for applications that need multiple distinct characters.

## Deployment Considerations

**Local (Mac with Apple Silicon):**
- M2/M3 Pro: ~3–5 RTF (3–5 seconds to generate 1 second of audio) — viable for async workloads, not real-time
- M3 Max/Ultra: faster, more viable for moderate throughput

**Cloud GPU:**
- A10G (24GB VRAM): ~0.3 RTF — fast enough for near-real-time at moderate quality settings
- A100: fastest, production-scale throughput

## Use Cases

**Best for:**
- Audiobook and long-form narration production
- Podcast voice generation
- High-quality content audio at scale (where cloud API cost is prohibitive)
- Applications that need owned, controlled voices
- When cloud API data privacy is a concern

[Browse Orpheus voices on Vokda →](https://vokda.iknsae.com)
