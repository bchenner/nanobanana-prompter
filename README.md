# nanobanana-prompter

A Claude agent — project instructions (`CLAUDE.md`) — that writes image prompts
for AI image generation (Gemini via the Nanobanana API), tuned for **realistic
UGC, commercial, and lo-fi content** — the kind that doesn't read as AI at a
glance.

It's an opinionated playbook, not a template filler: mixed imperfect lighting,
off-center propped-phone framing, narrative clutter, natural skin texture, and a
long list of AI-tell anti-patterns to avoid. Every rule exists because something
specific failed without it.

Originally one agent in a multi-agent content pipeline; it stands alone —
everything it needs is in `CLAUDE.md` and `reference/prompt-examples.md`.

## What's inside

- **Three prompt modes** — plain text for quick iterations, JSON (compact and
  full analytical scene-graph) for consistency and object de-entanglement, and a
  modification mode that applies small deltas to an existing base image.
- **Core principles** — the realism stack: 4 candidates per generation, no
  hyphens, mandatory natural-texture skin line, flat neutral light as default,
  2+ mixed light sources for UGC, imperfect framing, no visible windows indoors.
- **Per-scenario tuning** — indoor talking head, outdoor, car selfie, mirror
  selfie, kitchen demos, handheld props, full body, older demographics, deeper
  skin tones, and more.
- **Character consistency** — reference-sheet protocol, a from-scratch ref
  sheet template, and a setting-swap master prompt for placing an existing
  avatar into new locations.
- **Image-to-JSON** — reverse-engineer any image back into a reusable prompt.
- `reference/prompt-examples.md` — the full example library (compact and full
  analytical) the agent matches tone and detail against.

## Use it

**Claude Code:** copy `CLAUDE.md` and `reference/` into a folder and open that
folder as your project — the instructions load automatically.

**Claude Projects (claude.ai):** paste `CLAUDE.md` into the project
instructions and upload `reference/prompt-examples.md` to the project
knowledge.

## License

MIT — see [LICENSE](LICENSE).
