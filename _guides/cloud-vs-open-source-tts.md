---
layout: guide
title: "Cloud TTS vs Open-Source: An Honest Comparison"
summary: "A no-spin comparison of cloud provider TTS and self-hosted open-source models — quality gaps, cost curves, operational overhead, and when each makes sense."
updated: 2026-03-01
tags: [comparison, open-source, infrastructure]
---

The "cloud vs open-source" debate in TTS is different from the same debate in LLMs, databases, or web frameworks. The quality gap used to be enormous. It's much smaller now — and shrinking fast.

Here's an honest breakdown.

## The State of the Gap

Two years ago, open-source TTS sounded robotic. The good models were giant, slow, and expensive to run. Cloud providers had years of training data, tuned acoustic models, and the engineering resources to build fast inference infrastructure.

Today, models like **Kokoro** (82M params), **F5-TTS**, and **Orpheus** (3B) have closed a significant portion of that gap. They're not equal to ElevenLabs' top studio voices, but they're better than AWS Polly Standard, better than most Azure Standard voices, and comparable to Google WaveNet in naturalness evaluations.

The remaining gap shows up most clearly in:
- **Expressive/emotional range** — Cloud providers still lead
- **Voice cloning** — ElevenLabs and Cartesia are meaningfully ahead
- **Real-time latency** — Cloud APIs with dedicated infrastructure win

For everything else — basic narration, functional assistant voices, content generation — open-source is production-viable.

## The Cost Curve

Cloud pricing is pay-per-character. That's invisible at low volume and brutal at scale.

**Monthly cost at different volumes (using $0.015/1K chars as benchmark):**

| Monthly chars | Cloud cost | Self-hosted (Orpheus on $40 GPU) |
|--------------|-----------|----------------------------------|
| 100K | $1.50 | $40.00 |
| 1M | $15 | $40.00 |
| 5M | $75 | $40.00 |
| 20M | $300 | $40.00 |
| 100M | $1,500 | $80 (need bigger instance) |

The crossover point is roughly **3–5M characters/month**. Below that, cloud is cheaper (or comparable) when you factor in zero operational overhead. Above it, self-hosted wins decisively.

For bursty workloads — infrequent high-volume generation — cloud is better: you pay only for what you use, no idle infrastructure.

## Operational Overhead

Self-hosting has costs beyond compute:

**You own:**
- Model updates (cloud providers push these automatically)
- Scaling (cloud handles this)
- Reliability and uptime SLAs
- Hardware failure response
- Initial setup and ongoing maintenance

For a solo developer or small team, this overhead is often underestimated. Cloud TTS is genuinely "call an API and it works." Self-hosted requires infrastructure work.

**Mitigation:** Services like Replicate, HuggingFace Inference API, and Modal let you run open-source models via API with someone else handling the infrastructure. You get open-source models at cloud pricing — a middle path that's underused.

## Privacy and Data Control

This dimension is underweighted in most comparisons.

When you call a cloud TTS API, your text goes to a third-party server. For most content this is fine. For sensitive content it's not:

- Medical records being read back to patients
- Legal documents being narrated for review
- Internal financial documents
- Personal user data of any kind under GDPR/CCPA

With self-hosted open-source, nothing leaves your infrastructure. This is a compliance requirement for regulated industries, not a preference.

## Quality Decisions in Practice

**Use cloud when:**
- You need voice cloning (ElevenLabs, Cartesia)
- Real-time latency is critical (Cartesia, ElevenLabs Flash)
- Emotional/expressive range is a product requirement
- Volume is below ~3M chars/month
- Engineering bandwidth is limited

**Use open-source when:**
- Volume exceeds ~5M chars/month
- Content is privacy-sensitive
- You need consistent voices you own and control
- Latency requirements are relaxed (async workloads)
- You want to avoid per-character billing entirely

**Use hosted open-source (Replicate/HF) when:**
- You want open-source quality without infrastructure overhead
- Volume is moderate and predictable
- Vendor lock-in to proprietary voice APIs is a concern

## The Hybrid Approach

Most mature deployments end up hybrid:
- Cloud API for real-time interactive use (chat, phone)
- Self-hosted for batch/async generation (content, notifications, documents)
- Development uses cloud (fast iteration, no setup)
- Production large-volume uses self-hosted (cost)

Start with cloud. Migrate async workloads when the cost math justifies it.

[Browse and compare voices on Vokda →](https://vokda.iknsae.com)
