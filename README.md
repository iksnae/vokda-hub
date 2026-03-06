# Vokda Hub

The editorial layer of [Vokda](https://vokda.iknsae.com) — TTS news, model tracking, provider profiles, and guides for builders.

**Live:** https://hub.vokda.iknsae.com  
**App:** https://vokda.iknsae.com

---

## What's Here

| Section | Path | Purpose |
|---------|------|---------|
| News | `_posts/` | Date-stamped articles — model releases, provider updates |
| Guides | `_guides/` | Long-form how-to and comparison guides |
| Providers | `_providers/` | One profile per cloud TTS provider |
| Models | `_models/` | Open-source model registry |
| Data | `_data/` | YAML data files (providers, models feature matrix) |
| API | `api/` | Generated JSON endpoints consumed by the Vokda app |

---

## Local Development

Requires Ruby 3.x and Bundler.

```bash
bundle install
bundle exec jekyll serve
# open http://localhost:4000
```

---

## Adding Content

### News Post

Create `_posts/YYYY-MM-DD-slug.md`:

```yaml
---
layout: post
title: "Your Title"
date: YYYY-MM-DD
tags: [release, provider-name]
summary: "One sentence summary shown in feed."
providerId: provider-slug   # optional — links to provider profile
---

Your content here.
```

### Provider Profile

Create `_providers/provider-slug.md`:

```yaml
---
layout: profile
title: "Provider Name"
providerId: provider-slug
type: cloud_provider
tier: free | startup | enterprise
website: https://...
docs: https://...
pricing: "..."
languages: "N"
voices: "N+"
latency: "~Xms"
summary: "One-paragraph summary."
tags: [tag1, tag2]
---

Full profile content.
```

### Open Model

Create `_models/model-slug.md`:

```yaml
---
layout: profile
title: "Model Name"
type: open_model
license: "Apache 2.0"
parameters: "82M"
huggingface: org/model-name
pricing: "Free (self-hosted)"
languages: "en"
summary: "..."
tags: [fast, edge, open-source]
---
```

### Guide

Create `_guides/guide-slug.md`:

```yaml
---
layout: guide
title: "Guide Title"
summary: "What you'll learn."
updated: YYYY-MM-DD
tags: [beginner, comparison]
---
```

---

## JSON API

Jekyll generates JSON endpoints at build time, consumed by the Vokda SvelteKit app:

| Endpoint | Description |
|----------|-------------|
| `/api/news.json` | Latest 20 news posts |
| `/api/providers.json` | All provider profiles |
| `/api/models.json` | All open model profiles |
| `/api/feed.xml` | RSS/Atom feed |

---

## Architecture

This repo is one half of the Vokda content architecture:

- **`vokda-hub`** (this repo) — Editorial content, Jekyll, GitHub Pages
- **`vokda`** — SvelteKit app, voice discovery, collections, auth

The app's `/hub` route fetches `news.json` from this site and renders a lightweight in-app teaser. Full content lives here.

See [hub-architecture.md](https://github.com/iksnae/vokda/blob/main/docs/specs/hub-architecture.md) for the full spec.
