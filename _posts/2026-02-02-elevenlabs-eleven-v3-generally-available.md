---
layout: post
title: "ElevenLabs Eleven v3 Is Now Generally Available"
date: 2026-02-02
tags: [release, elevenlabs]
summary: "Eleven v3 exits alpha and goes GA — bringing audio tags, multi-speaker dialogue, and 70+ language support. The most expressive TTS model ElevenLabs has shipped."
providerId: elevenlabs
---

After several months in alpha, ElevenLabs shipped Eleven v3 as generally available on February 2nd. It's a meaningful generational step from Multilingual v2 — not just incremental quality improvements, but a fundamentally different approach to how you direct voice output.

## What's New

**Audio tags** are the headline feature. Instead of relying entirely on the model to interpret emotional tone from text, v3 lets you annotate inline:

```
[excited] We just closed the deal — [whispers] don't tell anyone yet.
[sighs] I've been waiting for this for months.
[laughs] You actually said that?
```

Tags can be applied to any span of text and stack with each other. The model interprets them relative to context — an `[excited]` tag on routine text reads differently than the same tag on a punchline. ElevenLabs describes the prompt engineering as more demanding than v2 but says the ceiling is significantly higher.

**Multi-speaker dialogue mode** is the other major addition. You can specify multiple voices in a single generation with natural pacing and interruptions between them — which eliminates the need to stitch together multiple API calls and manually line up timing for podcast scripts, audiobooks, or interactive narratives.

**70+ languages** — expanded from v2's 29. Coverage now includes many high-demand markets that were missing or in low-quality tiers before.

**68% reduction in errors** on complex text: chemical formulas, phone numbers, addresses, technical jargon. This matters more than it sounds — one garbled email address or wrong phone number in an IVR system undermines the entire deployment.

## What It's Best For

ElevenLabs is direct about the intended use case: v3 is built for **video, audiobooks, and media tools** — non-real-time creative applications where audio quality and expressiveness are the product.

For real-time and conversational agents they explicitly recommend staying with v2.5 Turbo or Flash. A real-time version of v3 is in development, but not yet available.

## Prompting v3

The audio tag system requires a bit of adjustment if you're used to just passing clean prose to the API. ElevenLabs' guidance is to treat v3 more like directing a voice actor — think about pacing, where emphasis should fall, which moments need emotional color.

A few patterns that work well:

```
# Emphasis
The answer is [emphatically] no.

# Non-verbal reactions  
[laughs softly] I can't believe that worked.

# Dialogue dynamics
— [confidently] I think we should ship it.
— [skeptical pause] And the tests?
— [hesitates] Most of them pass.
```

## API Access

Eleven v3 is available via `eleven_v3` in the API and through the ElevenLabs Studio interface. Pricing is higher than v2.5 — consult their pricing page for current rates.

## The Bottom Line

If you're generating audio for creative content — trailers, audiobooks, explainer videos, game dialog — v3 is the version to be on. The audio tag system gives you the kind of fine-grained control that used to require a voice acting session and post-production. Multi-speaker dialogue alone saves significant time for anyone producing scripted content.

For voice agents and real-time applications, hold off until the conversational v3 variant ships.

[Explore ElevenLabs voices on Vokda →](https://vokda.iknsae.com)
