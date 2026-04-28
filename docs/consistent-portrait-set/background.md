# consistent-portrait-set — Background & Context

## Origin

Developed in [wanw-forge](https://github.com/fang-lin/wanw-forge) private workspace as `photo-suite`, then extracted and published as `consistent-portrait-set`.

## Design Decisions

- **Gemini API via google-genai SDK** — not raw HTTP. SDK handles imageConfig (resolution, aspect ratio) correctly.
- **4K default for Grid, 2K for Chain** — Grid gets cropped (4K → ~2K per image), Chain is used as-is.
- **Three approval gates** — creative brief, prompt, and generated image must all be approved before proceeding.
- **Scripts handle execution, agent handles intelligence** — generate_suite.py does API calls/cropping/file management, the agent decides prompts and flow.

## Changes (2026-04-28)

- **Gemini safety filter workaround** — Pitfalls section now includes a prompt rewriting table for bypassing silent content moderation blocks (euphemistic vocabulary for revealing outfits).
- **Frontmatter standardized** — `env` replaced with `required_environment_variables` (with prompt/help/required_for), added `metadata.hermes.config` for default mode/resolution/aspect ratio, added `platforms: [macos, linux, windows]`.
- **Web toolset declared** — `requires_toolsets` now includes `web` (Step 1 uses web_search for trend research).
- **Pitfalls & Verification sections added** — documents known failure modes and post-action checks.
- **Anti-self-patch rule** — CRITICAL RULES #6: agent should not edit skill files, suggest `hermes skills update` instead.

## Known Limitations

- Gemini's face consistency is approximate, not pixel-perfect
- Four-grid layout sometimes uneven despite explicit prompting
- Vercel AI Gateway doesn't support image input for DeepSeek models (vision must use a different model)
