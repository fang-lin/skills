# top-news — Background & Context

## Origin

Developed in [wanw-forge](https://github.com/fang-lin/wanw-forge) private workspace, then extracted and published.

## Design Decisions

- **RSS + Hacker News API instead of paid search APIs** — free, structured, no API key required.
- **Agent-composed briefings** — scripts fetch and rank data, agent writes summaries and trend analysis.
- **Multi-turn onboarding** — one question at a time, numbered options, skip with 0, review before applying.
- **i18n via agent runtime translation** — one SKILL.md for all languages, agent translates at runtime.
- **Locale-specific sources** — auto-suggested based on user language (EN, ZH, DE verified).

## Changes (2026-04-28)

- **Timezone-aware scheduling** — onboarding now asks timezone (Question 6), cron jobs convert user's local time to UTC. Config stores `timezone` field.
- **HN ranking weight fix** — HN upvote score multiplier reduced from 0.5 to 0.05 (cap 100→20) to prevent HN dominating top results.
- **Source diversity cap** — max 5 articles per source in top N, ensures RSS sources aren't squeezed out by HN.
- **Frontmatter standardized** — `env` replaced with `required_environment_variables` (with prompt/help/required_for), added `metadata.hermes.config` for default preferences, added `platforms: [macos, linux, windows]`.
- **Template moved** — `briefing-template.md` moved from `references/` to `templates/` per Hermes skill directory standard.
- **Pitfalls & Verification sections added** — documents known failure modes and post-action checks.
- **Anti-self-patch rule** — CRITICAL RULES #8: agent should not edit skill files, suggest `hermes skills update` instead.

## Known Limitations

- 6 RSS sources broken as of 2026-04-27 (机器之心, Reuters, 华尔街见闻, 澎湃, Nature, Science)
- Science category has no reliable free RSS sources
- Streak detection uses simple title similarity, not semantic matching
- User feedback is Phase 1 (text reply), inline buttons planned for Phase 2
