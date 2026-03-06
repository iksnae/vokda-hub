---
layout: profile
title: "Cartesia"
providerId: cartesia
type: cloud_provider
tier: enterprise
website: https://cartesia.ai
docs: https://docs.cartesia.ai
pricing: "Pay-per-character, free tier available"
languages: "40+"
voices: "Named + custom clones"
latency: "Sub-80ms streaming"
summary: "The fastest real-time TTS API available. Cartesia Sonic 3 delivers sub-80ms streaming latency with real emotional expression, instant voice cloning, and enterprise compliance (SOC 2, HIPAA, PCI)."
tags: [real-time, voice-cloning, emotion, enterprise, multilingual]
---

Cartesia has become the benchmark provider for real-time voice agent applications. If you're building a conversational AI and evaluating TTS providers, Sonic 3 is the thing everyone else is being compared against.

## What Makes Cartesia Different

The headline advantage is **latency**. Sub-80ms time-to-first-audio via WebSocket streaming is fast enough that it's no longer the bottleneck in a voice agent stack — the LLM inference is. For live conversational UI, this matters enormously.

The second differentiator is **real emotional expression**. Sonic 3's emotional range — laughter, warmth, urgency, hesitation — is learned, not post-processed via SSML tags. The difference is audible in side-by-side comparisons. Other providers' "emotional" voices still sound like someone who was told to sound emotional. Sonic 3 sounds like it.

## Voice Catalog

Cartesia offers a set of named character voices plus two cloning tiers:

- **Instant Voice Cloning** — 10 seconds of reference audio, cloned voice available immediately
- **Pro Voice Cloning** — fine-tuned for enterprise deployments, consistent on-brand voice identity

The cloning capability makes Cartesia a natural fit for applications that need custom branded voices without the months-long engagement that custom voice recording used to require.

## API

Cartesia offers both REST and WebSocket endpoints:

```
POST https://api.cartesia.ai/tts/bytes          # Non-streaming
POST https://api.cartesia.ai/tts/sse            # Server-sent events streaming
WebSocket wss://api.cartesia.ai/tts/ws           # WebSocket streaming
```

The WebSocket endpoint is the one to use for real-time applications. SSE is a good middle ground for streaming without persistent connections.

## Compliance

SOC 2 Type II, HIPAA, and PCI Level 1 certifications make Cartesia viable for regulated industries where most other providers aren't yet certified.

## Pricing

Free tier available at cartesia.ai. Paid tiers are pay-per-character. No minimum commitment for standard access.

## When to Use Cartesia

- Real-time voice agents (phone, live chat, in-app assistant)
- Anything where emotional range is a product requirement
- When you need branded voice clones
- Healthcare, finance, or legal deployments requiring compliance certifications
