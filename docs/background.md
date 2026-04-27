# Background & Context

## Origin

This skill was developed in the [wanw-forge](https://github.com/fang-lin/wanw-forge) private workspace as part of a personal AI agent toolkit. It was extracted into a standalone public repository for community use.

## Design Decisions

### Why RSS + public APIs instead of paid search APIs
- Free, structured, reliable data
- No API key required for basic operation
- RSS feeds cover most major news outlets
- Parallel/Tavily/etc. reserved for deep search use cases, not daily aggregation

### Why agent-composed briefings instead of template-only output
- Agent can summarize, translate, analyze trends
- Scripts handle deterministic work (fetch, dedup, rank)
- Agent handles intelligence (composition, trend insights, user interaction)

### Why multi-turn onboarding
- Single-question-at-a-time prevents information overload
- Each step has numbered options for quick reply
- 0 = skip (keep defaults) for fast setup
- Review summary before applying

### Why no i18n files
- Agent translates SKILL.md templates at runtime
- One SKILL.md serves all languages
- Locale-specific sources auto-suggested based on user language

## Known Limitations

- Some RSS sources are unreliable (see sources-catalog.md for status)
- Science category has no working free RSS sources currently
- Streak detection uses simple title similarity, not semantic matching
- User feedback (👍/👎) is Phase 1 (text reply), inline buttons planned for Phase 2

## Related

- [consistent-portrait-set](https://github.com/fang-lin/consistent-portrait-set) — companion skill for photo generation
