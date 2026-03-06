---
layout: profile
title: "OpenAI TTS"
providerId: openai
type: cloud_provider
tier: startup
website: https://platform.openai.com/docs/guides/text-to-speech
docs: https://platform.openai.com/docs/api-reference/audio/createSpeech
pricing: "$0.015/1K chars (TTS-1), $0.030/1K chars (TTS-1-HD)"
languages: "Afrikaans, Arabic, Armenian, Azerbaijani, Belarusian, Bosnian, Bulgarian, Catalan, Chinese, Croatian, Czech, Danish, Dutch, English, Estonian, Finnish, French, Galician, German, Greek, Hebrew, Hindi, Hungarian, Icelandic, Indonesian, Italian, Japanese, Kannada, Kazakh, Korean, Latvian, Lithuanian, Macedonian, Malay, Marathi, Maori, Nepali, Norwegian, Persian, Polish, Portuguese, Romanian, Russian, Serbian, Slovak, Slovenian, Spanish, Swahili, Swedish, Tagalog, Tamil, Thai, Turkish, Ukrainian, Urdu, Vietnamese, and Welsh"
voices: "6 built-in voices"
latency: "~200ms"
summary: "Simple, consistent, and already in your stack if you're using OpenAI for the LLM layer. Six high-quality built-in voices with broad language support and the simplest API in the category."
tags: [simple, consistent, multilingual, openai-native]
---

OpenAI TTS is the path of least resistance for teams already using the OpenAI API. One SDK, one billing account, voices that are consistently good without being exceptional. For many applications that's exactly the right tradeoff.

## Models

Two model tiers:
- **TTS-1** — $0.015/1K chars. Optimized for real-time use. Lower latency, slightly less natural.
- **TTS-1-HD** — $0.030/1K chars. Highest quality. Best for final-output content where you're not running under latency constraints.

## Voices

Six built-in voices: **alloy, echo, fable, onyx, nova, shimmer**. The variety covers male/female and different tonal registers (warm, neutral, crisp, deep). What they lack in character depth they make up for in consistency — these voices never sound bad, even on unusual input.

## API

```
POST https://api.openai.com/v1/audio/speech
{
  "model": "tts-1-hd",
  "input": "Your text here",
  "voice": "nova"
}
```

Response is a binary audio stream. It's the simplest TTS API in the industry.

## Language Support

OpenAI TTS inherits language coverage from the Whisper training corpus — it supports a remarkable 50+ languages, many of which smaller providers don't cover at all.

## When to Use OpenAI TTS

- You're already using OpenAI for the LLM layer and want a single vendor
- You need broad language coverage without evaluating alternatives
- Content is general-purpose and doesn't require expressive/emotional range
- Volume is moderate (the per-character cost stacks up at high volume)
- Developer productivity matters more than voice selection depth
