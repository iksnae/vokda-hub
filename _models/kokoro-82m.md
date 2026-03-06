---
layout: profile
title: "Kokoro 82M"
type: open_model
license: "Apache 2.0"
parameters: "82M"
huggingface: https://huggingface.co/hexgrad/Kokoro-82M
website: https://github.com/hexgrad/kokoro
pricing: "Free (self-hosted)"
languages: "English (US, UK), French, Korean, Japanese, Mandarin Chinese, Spanish, Hindi, Italian, Brazilian Portuguese"
summary: "The most efficient open-source TTS model available. 82M parameters, Apache 2.0, very fast inference on modest hardware — the go-to choice for edge deployment and high-volume async workloads."
tags: [edge, fast, efficient, multilingual, self-hosted]
---

Kokoro 82M punches significantly above its weight class. At 82 million parameters it's a tiny model by modern standards, but the output quality is remarkably good — good enough that it's become a default recommendation for developers who need self-hosted TTS without renting a GPU.

## Why It Matters

The TTS model landscape has a gap problem: most open-source models that produce genuinely good audio are large (1B+), requiring significant compute. Kokoro 82M breaks that correlation. The training approach prioritizes output naturalness per parameter rather than raw scale.

The result: you can run Kokoro on a CPU-only server, a laptop, or a Raspberry Pi-class device and get audio quality that would have required a cloud API two years ago.

## Technical Details

- **Parameters:** 82 million
- **License:** Apache 2.0 (commercial use, modification, redistribution — all free)
- **Architecture:** Lightweight neural TTS
- **Inference:** CPU-viable, very fast on Apple Silicon via CoreML/MLX
- **HuggingFace:** `hexgrad/Kokoro-82M`

## Language Support

9 languages: English (US and UK accents), French, Korean, Japanese, Mandarin Chinese, Spanish, Hindi, Italian, and Brazilian Portuguese. Language quality varies — English is best, others are solid.

## Voices

Multiple voice styles available through the model configuration. Voices have distinct tonal characteristics — different enough to be useful for multi-character applications.

## Use Cases

**Best for:**
- Edge deployment (IoT devices, mobile, local-first apps)
- High-volume batch generation where per-character cost matters
- Development/testing workflows where cloud API billing is wasteful
- Privacy-sensitive applications (medical, legal, personal data)
- Applications in the 9 supported languages at modest quality requirements

**Not ideal for:**
- Real-time latency-critical applications (Cartesia wins here)
- Highest expressiveness requirements (Orpheus or cloud providers)
- Languages outside the 9 supported

## Getting Started

```python
# via the kokoro Python package
pip install kokoro

from kokoro import KPipeline
pipeline = KPipeline(lang_code='a')  # 'a' = American English
audio, _ = pipeline("Your text here", voice='af_heart')
```

[Browse Kokoro voices on Vokda →](https://vokda.iknsae.com)
