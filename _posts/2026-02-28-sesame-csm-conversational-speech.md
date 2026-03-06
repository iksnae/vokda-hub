---
layout: post
title: "Sesame CSM-1B: The First TTS Model Built Specifically for Conversation"
date: 2026-02-28
tags: [open-source, release, sesame]
summary: "Sesame's Conversational Speech Model is a 1B-parameter open-source model designed from the ground up for dialog — realistic turn-taking, natural back-channels, and Apache 2.0 licensing."
providerId: sesame
---

Most text-to-speech models are built for monologue: they're optimized for narration, announcements, audiobooks — content where one voice speaks continuously and nothing speaks back. Conversations don't work that way.

**Sesame's CSM-1B** is the first openly available TTS model designed specifically for the conversational case, and the difference in output is immediately noticeable.

## What Makes It Different

The core insight behind CSM is that natural-sounding dialog requires different training objectives than natural-sounding narration. Sesame trained on conversation data specifically, teaching the model:

- **Realistic turn-taking patterns** — knowing when to trail off, when to pick up energy, how the end of a phrase signals completion
- **Natural back-channels** — the "mm-hm," "right," "got it" acknowledgments that make a voice sound engaged rather than automated
- **Dialog pacing** — speaking rhythm that fits interruption-style exchanges rather than extended monologue

The result sounds right in voice agent applications in a way that even high-quality narration-tuned models don't. Something about the timing feels responsive rather than robotic.

## Technical Details

- **Parameters:** 1 billion
- **License:** Apache 2.0 — production use, modification, redistribution, commercial deployment, all unrestricted
- **HuggingFace:** `sesame/csm-1b`
- **MLX port:** `mlx-community/csm-1b` — ready to run locally on Apple Silicon today

The MLX port is worth highlighting: CSM can run on a MacBook or Mac mini at reasonable speed via mlx-audio, making it viable for local development and privacy-sensitive deployments without a cloud API dependency.

## Who It's For

CSM shines in applications where the TTS voice is one side of a two-way conversation:

- Voice AI assistants (real-time call center, support bots)
- Interactive educational tools with back-and-forth dialog
- Game NPCs and interactive narrative
- Accessibility tools that need to feel responsive, not broadcast-y

For straight narration (audiobooks, articles, podcasts) you'd still reach for Kokoro or Orpheus — they're optimized for that delivery style. But for anything where your TTS voice is in a dialog, CSM is now the first thing worth trying.

## Bottom Line

Sesame didn't just release another TTS model — they identified a gap in the existing model landscape (conversational AI specifically) and built directly into it. Apache 2.0 licensing means there's no friction to building on it, and the MLX port makes local experimentation frictionless on Apple Silicon.

[Explore open models on Vokda →](https://vokda.iknsae.com)
