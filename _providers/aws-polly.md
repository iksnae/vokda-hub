---
layout: profile
title: "AWS Polly"
providerId: aws-polly
type: cloud_provider
tier: enterprise
website: https://aws.amazon.com/polly/
docs: https://docs.aws.amazon.com/polly/
pricing: "$0.004/1K chars (Standard), $0.016/1K chars (Neural)"
languages: "30+"
voices: "60+"
latency: "~300ms (Neural)"
summary: "Amazon's mature TTS service with neural voices across 30+ languages and tight AWS ecosystem integration. Best for AWS-native architectures where you're already in the ecosystem."
tags: [aws-native, enterprise, multilingual, neural, ssml]
---

AWS Polly is the veteran of the cloud TTS market. It's not the most exciting option in 2026, but it's reliable, well-documented, deeply integrated into the AWS ecosystem, and economically attractive at scale.

## Voice Tiers

- **Standard voices** — $0.004/1K chars. Concatenative synthesis, older technology, robotic-ish. Mostly useful for cost-sensitive applications where quality is secondary.
- **Neural voices** — $0.016/1K chars. Neural TTS, significantly more natural. The voices you actually want to use.

Neural Polly voices are competitive with general-purpose cloud TTS — they're not as expressive as ElevenLabs or as fast as Cartesia, but they're solid, consistent, and cheap relative to premium providers.

## SSML Support

Polly has among the best SSML support in the industry — breathing, whispering, speaking rate, volume, emphasis, and even Amazon-specific extensions for pronunciation dictionaries and phonemes. For applications that need fine-grained control over delivery, Polly's SSML depth is genuinely useful.

## AWS Integration

The native integration with the AWS ecosystem is Polly's strongest card:
- **Lambda** — generate audio inline with serverless functions
- **S3** — stream generated audio directly to buckets
- **CloudFront** — serve cached audio from CDN
- **Lex** — built-in TTS for AWS chatbots

If your stack is already AWS-native, adding Polly is one SDK call away.

## Lexicons and Pronunciation

Custom lexicons let you define pronunciation for domain-specific terms, acronyms, and brand names. This is essential for applications with specialized vocabulary — healthcare and finance deployments in particular.

## When to Use AWS Polly

- Your architecture is AWS-native and you want minimal vendor sprawl
- You need deep SSML control
- Custom pronunciation lexicons are a requirement
- Volume is high and cost is primary (Neural at $0.016/1K is competitive)
- You need a mature, enterprise-supported service
