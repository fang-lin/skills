# consistent-portrait-set — Background & Context

## Origin

Developed in [wanw-forge](https://github.com/fang-lin/wanw-forge) private workspace as `photo-suite`, then extracted and published as `consistent-portrait-set`.

## Design Decisions

- **Gemini API via google-genai SDK** — not raw HTTP. SDK handles imageConfig (resolution, aspect ratio) correctly.
- **4K default for Grid, 2K for Chain** — Grid gets cropped (4K → ~2K per image), Chain is used as-is.
- **Three approval gates** — creative brief, prompt, and generated image must all be approved before proceeding.
- **Scripts handle execution, agent handles intelligence** — generate_suite.py does API calls/cropping/file management, the agent decides prompts and flow.

## Known Limitations

- Gemini's face consistency is approximate, not pixel-perfect
- Four-grid layout sometimes uneven despite explicit prompting
- Vercel AI Gateway doesn't support image input for DeepSeek models (vision must use a different model)
