---
layout: guide
title: "Choosing a Voice for Your AI Agent"
summary: "A practical framework for selecting the right TTS provider and voice for conversational AI — covering latency, naturalness, cost, and the cases where open-source beats cloud."
updated: 2026-03-01
tags: [voice-agents, comparison, beginner]
---

Picking a voice for an AI agent sounds simple until you try. There are hundreds of options across a dozen providers, benchmarks that contradict each other, and pricing models that only make sense at specific scale points. This guide cuts through the noise.

## The Three Axes That Actually Matter

Every voice selection decision comes down to three things:

**1. Latency** — Does your agent need to respond in real-time?

If you're building a phone-based assistant or a live conversation UI, latency is your first filter. You need sub-200ms time-to-first-audio. That rules out most open-source models running on commodity hardware and narrows you to Cartesia (sub-80ms), ElevenLabs Flash (sub-100ms), and Deepgram Aura-2 (sub-200ms).

If your use case is async — generating narration, processing documents, creating content — latency is irrelevant. Open-source becomes viable.

**2. Voice Character** — Does the voice need to feel like a person?

Some agents can sound functional: clear, neutral, slightly robotic. Phone IVRs and appointment reminders have always sounded like this and users accept it. Others need to pass for human — therapy assistants, personal finance advisors, educational tutors. The gap in naturalness between providers is significant.

For high-naturalness requirements: ElevenLabs (widest voice range), Cartesia (best for dialog), OpenAI (best consistency). For functional quality at lower cost: AWS Polly Neural, Azure Neural, Google WaveNet.

**3. Scale and Cost** — What does your usage look like at 1M+ characters/month?

| Provider | $/1K chars | Good At |
|----------|-----------|---------|
| Cartesia | ~$0.015–0.030 | Real-time agents |
| ElevenLabs | ~$0.030–0.300 | High-quality narration |
| OpenAI TTS | ~$0.015 | Consistency, simplicity |
| Google WaveNet | ~$0.016 | Multilingual |
| AWS Polly Neural | ~$0.016 | AWS-native apps |
| Deepgram Aura-2 | ~$0.030 | Domain-specific |
| Open-source | $0 | Volume, privacy |

At low volume (<500K chars/month) the cost difference is negligible. At high volume the math changes dramatically — and open-source models become the only economically rational choice.

## Decision Tree

**Is latency under 200ms required?**

→ **Yes:** Use Cartesia (Sonic 3) for best-in-class, ElevenLabs Flash for highest voice quality, Deepgram Aura-2 for domain-specific accuracy.

→ **No:** Proceed.

**Does the content require expressive, emotional delivery?**

→ **Yes:** ElevenLabs (studio models) or Cartesia (Sonic 3 emotional range).

→ **No:** Proceed.

**Is this a conversational back-and-forth exchange?**

→ **Yes:** Cartesia Sonic 3 or Sesame CSM (open-source, specifically built for dialog).

→ **No:** Proceed.

**Is the content in a specialized domain (medical, legal, finance)?**

→ **Yes:** Deepgram Aura-2.

→ **No:** Proceed.

**What's your monthly volume?**

→ **<500K chars:** OpenAI TTS-1-HD or Google WaveNet — simple, high quality, manageable cost.

→ **500K–5M chars:** AWS Polly Neural or Azure Neural — enterprise pricing, reliability, native cloud integrations.

→ **>5M chars:** Open-source (Kokoro, Orpheus, F5-TTS) — zero per-character cost.

## The Case for Open-Source

Open-source TTS has crossed a quality threshold that makes it genuinely viable for production. Key models:

- **Kokoro 82M** — 82M parameters, Apache 2.0, very fast, good quality for its size. Best for edge deployment or volume workloads where cost is primary.
- **F5-TTS** — Flow-matching architecture, MIT license, fast inference, high quality. Best middle-tier option.
- **Orpheus** — 3B parameters, Apache 2.0, 8 named voices, highest open-source quality. Best for high-quality async workloads.
- **Sesame CSM** — 1B parameters, Apache 2.0, specifically built for conversation. Best for dialog-heavy applications.

The cost case is straightforward: a deployment generating 10M characters/month at $0.015/1K chars = $150/month. Run Orpheus on a $40/month GPU instance = $40/month at unlimited volume.

The privacy case is equally clear: audio content often contains sensitive information (personal data, proprietary content). Open-source models deployed locally keep that data entirely within your infrastructure.

## Testing Before Committing

Most providers offer free tiers or credits. Before committing to a voice at scale:

1. Generate 20-30 samples covering your actual content domain (not generic demo text)
2. Test with native speakers if you're deploying multilingual voices
3. Listen for mispronunciations of domain-specific terminology
4. Test emotional range if your content requires it
5. Benchmark latency under realistic network conditions, not ideal lab conditions

[Browse and audition voices on Vokda →](https://vokda.iknsae.com)
