# top-news — Background & Context

## Origin

Developed in [wanw-forge](https://github.com/fang-lin/wanw-forge) private workspace, then extracted and published.

## Design Decisions

- **Google News RSS as sole aggregator** — free, no API key, covers all topics/languages/regions via query parameters. Replaced 20+ individual RSS sources that required manual maintenance.
- **Agent-composed briefings** — scripts fetch and rank data, agent writes summaries and trend analysis.
- **Multi-turn onboarding** — one question at a time, numbered options, skip with 0, review before applying.
- **i18n via agent runtime translation** — one SKILL.md for all languages, agent translates at runtime.
- **Custom RSS support** — users can add any RSS/Atom feed alongside Google News queries.

## Changes (2026-04-28)

- **Source system rewrite** — replaced 20+ individual RSS sources and Hacker News API with Google News RSS as the sole aggregator. Each user topic becomes a Google News query (`?q=topic&hl=lang&gl=region`). Users can still add custom RSS/Atom feeds. Bing News was evaluated but its RSS endpoint is defunct.
- **HN code removed** — `fetch_hackernews()` deleted from fetch_news.py, HN score weighting removed from ranking. Ranking now uses recency + streak only.
- **Source diversity cap** — max 5 articles per source in top N.
- **Timezone-aware scheduling** — onboarding now asks timezone (Question 6), cron jobs convert user's local time to UTC. Config stores `timezone` field.
- **Frontmatter standardized** — `env` replaced with `required_environment_variables` (with prompt/help/required_for), added `metadata.hermes.config` for default preferences, added `platforms: [macos, linux, windows]`.
- **Template moved** — `briefing-template.md` moved from `references/` to `templates/` per Hermes skill directory standard.
- **Pitfalls & Verification sections added** — documents known failure modes and post-action checks.
- **Anti-self-patch rule** — CRITICAL RULES #8: agent should not edit skill files, suggest `hermes skills update` instead.

## Known Limitations

- Google News RSS is the single point of failure — if it goes down, no news (custom RSS feeds still work)
- Bing News RSS was evaluated as fallback but its endpoint no longer returns RSS
- Streak detection uses simple title similarity, not semantic matching
- User feedback is Phase 1 (text reply), inline buttons planned for Phase 2
