# Contributing

Thanks for your interest in contributing!

## Repository Structure

```
skills/
├── consistent-portrait-set/
│   ├── SKILL.md
│   ├── scripts/
│   │   ├── generate_suite.py
│   │   └── test_generate_suite.py
│   └── references/
│       └── prompt-guide.md
└── top-news/
    ├── SKILL.md
    ├── scripts/
    │   ├── fetch_news.py
    │   ├── rank_and_dedup.py
    │   └── test_top_news.py
    └── references/
        ├── briefing-template.md
        └── sources-catalog.md
```

## SKILL.md Format

Each skill uses YAML frontmatter:

```yaml
---
name: skill-name
description: What this skill does and when to trigger it.
version: "1.0.0"
requires_toolsets:
  - code_execution
  - skills
env:
  - API_KEY_NAME
---
```

- `name`: Must match the directory name
- `description`: Used by the agent to decide when to activate this skill
- `requires_toolsets`: Hermes toolsets needed at runtime
- `env`: Required environment variables

## Development Setup

1. Clone the repo:
   ```bash
   git clone https://github.com/fang-lin/skills.git
   ```

2. Install Python dependencies:
   ```bash
   pip install google-genai Pillow  # for consistent-portrait-set
   ```

3. Run tests:
   ```bash
   cd skills/<skill-name>/scripts
   python -m pytest -v
   ```

## Making Changes

### General principles

- Scripts handle deterministic work (API calls, file I/O, data processing)
- SKILL.md guides agent behavior (workflow, prompts, user interaction)
- Keep CLI interfaces stable when modifying scripts
- All file I/O through script's directory management, no hardcoded paths
- Add tests for new functionality

### consistent-portrait-set

- Maintain the three approval gates (creative brief, prompt, generated image)
- All generation must go through `generate_suite.py`, not direct API calls
- Use `MEDIA:` prefix for image delivery

### top-news

- Maintain multi-turn onboarding with numbered options
- All data fetching through `fetch_news.py`, ranking through `rank_and_dedup.py`
- Keep sources-catalog.md updated with source status

## Pull Requests

1. Fork the repo and create a feature branch
2. Make your changes with clear commit messages
3. Ensure tests pass
4. Submit a PR with a description of what changed and why

## Reporting Issues

Open an issue on GitHub with:
- What you expected to happen
- What actually happened
- Steps to reproduce
- Hermes version and environment details
