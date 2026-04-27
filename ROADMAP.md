# Roadmap

## consistent-portrait-set

### Current: v0.8.0
- Grid Mode (2x2 grid, crop into 4 images)
- Chain Mode (sequential generation, unlimited count)
- Face-locking via model card
- Optional reference images (environment, outfit, accessories)
- 512 / 1K / 2K / 4K resolution support
- 9:16 default aspect ratio, 14 ratios supported
- Optional upscale step
- Three approval gates

### Planned
- [ ] Improve hand/finger quality in generated images
- [ ] Better face consistency across different poses and angles
- [ ] Automatic quality scoring before presenting to user
- [ ] Batch mode — generate multiple sets with different themes
- [ ] Template system — save and reuse creative briefs
- [ ] Support additional image generation APIs beyond Gemini

## top-news

### Current: v0.4.1
- Multi-turn onboarding (7 questions, numbered options, review gate)
- RSS + Hacker News API data fetching (20+ sources)
- Smart ranking with dedup and 7-day streak tracking
- 3 output formats (headlines, summary, deep analysis)
- i18n via agent runtime translation
- Locale-specific sources (EN, ZH, DE)
- Cron-based scheduled delivery
- User feedback tracking (👍/👎 text reply)

### Planned
- [ ] Phase 2 feedback: Telegram inline keyboard buttons (👍/👎)
- [ ] Find replacement sources for broken RSS feeds (Science, 机器之心, Reuters, etc.)
- [ ] Expand locale sources (JA, FR, ES, KO)
- [ ] Weekly/monthly digest generation
- [ ] Multi-user support (per-user profiles in group chats)
- [ ] Source health monitoring (auto-detect broken feeds)

## General

- [ ] HermesHub listing (PR submitted: amanning3390/hermeshub#62)
- [ ] Skills.sh SKILL.md rendering (currently shows "No SKILL.md available")
