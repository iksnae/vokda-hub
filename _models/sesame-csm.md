---
layout: profile
title: "Sesame CSM-1B"
type: open_model
license: "Apache 2.0"
parameters: "1B"
huggingface: https://huggingface.co/sesame/csm-1b
pricing: "Free (self-hosted)"
languages: "English"
summary: "Sesame's Conversational Speech Model — 1B parameters, Apache 2.0, specifically designed for dialog and turn-taking. The first open-source TTS model built for conversation rather than narration."
tags: [conversational, dialog, voice-agents, self-hosted, open-source]
---

The TTS model landscape is built around a monologue assumption: generate audio for text that one speaker says uninterrupted. Sesame CSM was designed around a different assumption — that TTS needs to fit into conversation.

## What CSM Gets Right

Training CSM on conversational data changes the acoustic character of the output in specific ways:

**Turn-taking patterns** — Phrases trail off appropriately, sentence endings signal completion vs. continuation differently. The model has learned how conversation sounds from both sides.

**Natural back-channels** — "Yeah," "mm-hm," "right," "got it" — the short acknowledgments that make dialog feel alive. In narration-trained models these sound forced. CSM produces them naturally because it trained on them naturally.

**Dialog pacing** — The rhythm of speech in conversation is different from narration. Sentences are shorter, there are more mid-utterance pauses, energy patterns shift more frequently. CSM reflects this.

## Technical Details

- **Parameters:** 1 billion
- **License:** Apache 2.0
- **HuggingFace:** `sesame/csm-1b`
- **MLX port:** `mlx-community/csm-1b` — optimized for Apple Silicon inference
- **Release:** February 2025 (Sesame)

The MLX port is ready for immediate use on Apple Silicon. Local inference on M2/M3 hardware is fast enough for batch generation and viable for lower-latency real-time use.

## Use Cases

**Best for:**
- **Voice AI assistants** — conversational style that matches the mode of interaction
- **Telephony bots** — call center, IVR, conversational phone applications
- **Educational tools** — tutoring, Q&A interfaces, interactive learning
- **Game dialog** — NPC conversations, interactive narrative with back-and-forth
- **Any application where the TTS voice is in dialog, not monologue**

**Not ideal for:**
- Audiobook narration (Orpheus or cloud providers optimized for that)
- Long-form content generation (monologue-optimized models are better)
- Non-English content (CSM-1B is English-only)

## Running Locally

```python
# Using the HuggingFace transformers library
from huggingface_hub import hf_hub_download
# or via mlx-community/csm-1b for Apple Silicon
```

Or via the MLX port for Apple Silicon:
```bash
pip install mlx-audio
mlx_audio generate --model mlx-community/csm-1b --text "Your text here"
```

[Explore open models on Vokda →](https://vokda.iknsae.com)
