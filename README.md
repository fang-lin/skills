# skills

> Open agent skills by fang-lin.

A collection of agent skills for [Hermes Agent](https://hermes-agent.nousresearch.com/) and other platforms supporting the [agentskills.io](https://agentskills.io) open standard.

## Skills

| Skill | Description | Version |
|-------|-------------|---------|
| [consistent-portrait-set](skills/consistent-portrait-set/) | Generate consistent multi-photo portrait sets with face-locked model cards | v0.8.0 |
| [top-news](skills/top-news/) | Personalized top news briefing with trend insights and preference learning | v0.4.1 |

## Installation

**Hermes Agent:**
```bash
hermes skills tap add fang-lin/skills
hermes skills install consistent-portrait-set --force
hermes skills install top-news --force
```

**npx skills (Claude Code, Cursor, etc.):**
```bash
npx skills add fang-lin/skills
```

**Manual:**
```bash
cp -r skills/<skill-name> ~/.hermes/skills/
```

## License

MIT
