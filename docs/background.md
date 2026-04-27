# Background & Context

## Origin

Both skills were developed in the [wanw-forge](https://github.com/fang-lin/wanw-forge) private workspace, then extracted and merged into this unified public repository for community use.

Previously each skill had its own repo (`fang-lin/consistent-portrait-set`, `fang-lin/top-news`). They were merged into `fang-lin/skills` for cleaner identifiers and easier maintenance.

## consistent-portrait-set

### What it does
Generates consistent multi-photo portrait sets using a model card (face reference image) via Google Gemini API. Two modes: Grid (2x2, fast) and Chain (sequential, precise).

### Design Decisions
- **Gemini API via google-genai SDK** — not raw HTTP. SDK handles imageConfig (resolution, aspect ratio) correctly.
- **4K default for Grid, 2K for Chain** — Grid gets cropped (4K → ~2K per image), Chain is used as-is.
- **Three approval gates** — creative brief, prompt, and generated image must all be approved before proceeding.
- **Scripts handle execution, agent handles intelligence** — generate_suite.py does API calls/cropping/file management, the agent decides prompts and flow.

### Known Limitations
- Gemini's face consistency is approximate, not pixel-perfect
- Four-grid layout sometimes uneven despite explicit prompting
- Vercel AI Gateway doesn't support image input for DeepSeek models (vision must use a different model)

## top-news

### What it does
Delivers personalized top news briefings from free RSS feeds and public APIs. Supports topic selection, scheduled delivery, streak tracking, trend analysis, and user feedback learning.

### Design Decisions
- **RSS + Hacker News API instead of paid search APIs** — free, structured, no API key required.
- **Agent-composed briefings** — scripts fetch and rank data, agent writes summaries and trend analysis.
- **Multi-turn onboarding** — one question at a time, numbered options, skip with 0, review before applying.
- **i18n via agent runtime translation** — one SKILL.md for all languages, agent translates at runtime.
- **Locale-specific sources** — auto-suggested based on user language (EN, ZH, DE verified).

### Known Limitations
- 6 RSS sources broken as of 2026-04-27 (机器之心, Reuters, 华尔街见闻, 澎湃, Nature, Science)
- Science category has no reliable free RSS sources
- Streak detection uses simple title similarity, not semantic matching
- User feedback is Phase 1 (text reply), inline buttons planned for Phase 2
