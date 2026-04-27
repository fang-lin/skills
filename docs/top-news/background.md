# top-news — Background & Context

## Origin

Developed in [wanw-forge](https://github.com/fang-lin/wanw-forge) private workspace, then extracted and published.

## Design Decisions

- **RSS + Hacker News API instead of paid search APIs** — free, structured, no API key required.
- **Agent-composed briefings** — scripts fetch and rank data, agent writes summaries and trend analysis.
- **Multi-turn onboarding** — one question at a time, numbered options, skip with 0, review before applying.
- **i18n via agent runtime translation** — one SKILL.md for all languages, agent translates at runtime.
- **Locale-specific sources** — auto-suggested based on user language (EN, ZH, DE verified).

## Known Limitations

- 6 RSS sources broken as of 2026-04-27 (机器之心, Reuters, 华尔街见闻, 澎湃, Nature, Science)
- Science category has no reliable free RSS sources
- Streak detection uses simple title similarity, not semantic matching
- User feedback is Phase 1 (text reply), inline buttons planned for Phase 2
