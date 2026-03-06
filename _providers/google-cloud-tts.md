---
layout: profile
title: "Google Cloud TTS"
providerId: google-cloud-tts
type: cloud_provider
tier: startup
website: https://cloud.google.com/text-to-speech
docs: https://cloud.google.com/text-to-speech/docs
pricing: "$0.000004/char (Standard), $0.000016/char (WaveNet), $0.000016/char (Neural2), free: 1M chars/month Standard, 1M chars/month WaveNet"
languages: "40+"
voices: "380+"
latency: "~250ms"
summary: "Google's TTS service with the strongest free tier in the category and high-quality WaveNet and Neural2 voices. Consistent, reliable, and deep Google Cloud integration for GCP-native stacks."
tags: [gcp-native, wavenet, multilingual, free-tier, neural]
---

Google Cloud TTS has been quietly reliable for years. WaveNet voices — released back in 2018 — still hold up well, and the Neural2 voices added more recently are among the best in the standard cloud tier. The pricing and free tier make it hard to beat for most production applications.

## Voice Technology Tiers

- **Standard** — Concatenative synthesis, $4/1M chars. Functional, not impressive.
- **WaveNet** — DeepMind's neural architecture, $16/1M chars. Natural, expressive, high quality.
- **Neural2** — Next-generation neural, $16/1M chars. Slightly more natural than WaveNet.
- **Studio** — Highest quality, $160/1M chars. Comparable to ElevenLabs for specific voices.

For most use cases, **Neural2** at $16/1M chars is the right choice.

## Free Tier

Google has the most generous free tier of any TTS provider:
- 1M chars/month — Standard voices
- 1M chars/month — WaveNet voices
- 1M chars/month — Neural2 voices

This is enough for low-to-medium production use at zero cost.

## Language and Voice Coverage

380+ voices across 40+ languages. Not as broad as Azure (140 languages), but Google's voice quality in covered languages is consistently high. The multilingual voices are particularly good — able to handle mixed-language input naturally.

## SSML

Full SSML support with Google-specific extensions for say-as (dates, numbers, currencies), audio file embedding, and paragraph/sentence structure hints.

## GCP Integration

Native integration with Google Cloud ecosystem: Cloud Storage, Cloud Functions, Pub/Sub, and Dialogflow (Google's conversational AI platform). If your stack is GCP-native, adding TTS is a single client library away.

## When to Use Google Cloud TTS

- GCP-native architectures
- You want the most generous free tier
- Neural2 quality meets requirements and cost efficiency matters
- Mixed-language input (multilingual voices handle this well)
- You're building on Dialogflow or other Google AI services
