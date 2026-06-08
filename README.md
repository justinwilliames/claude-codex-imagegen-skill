# claude-codex-imagegen-skill

A self-contained Claude Code skill that lets Claude generate and edit images by delegating the actual image work to OpenAI Codex.

## What it does

This repo packages a Claude skill plus a tiny wrapper script:

- `SKILL.md` teaches Claude when to route image requests through Codex
- `scripts/codex-imagegen.sh` launches Codex non-interactively, passes prompts and optional image attachments, and returns the final result cleanly

The skill does not depend on any other Claude skill.

## Requirements

- Claude Code
- Codex CLI installed locally
- Codex already authenticated on the machine

The skill is self-contained at the Claude-skill level, but it still needs a working Codex installation to do the actual generation.

## Install

Clone the repo directly into your Claude skills directory under the skill name `codex-imagegen`:

```bash
git clone https://github.com/justinwilliames/claude-codex-imagegen-skill.git \
  ~/.claude/skills/codex-imagegen
chmod +x ~/.claude/skills/codex-imagegen/scripts/codex-imagegen.sh
```

If you already cloned it elsewhere, copy or symlink the folder into `~/.claude/skills/codex-imagegen`.

## Use

Example trigger phrases:

- "Use Codex to make an image of a plumber fixing a sink"
- "Generate this via Codex"
- "Edit this image in Codex"
- "Make a hero image with Codex"
- "Create a PNG with Codex"

Claude will use the skill, call the wrapper script, and let Codex handle the image generation or edit.

## Repo layout

```text
claude-codex-imagegen-skill/
├── SKILL.md
├── LICENSE
├── README.md
└── scripts/
    └── codex-imagegen.sh
```

## Notes

- Project-bound outputs should be copied into a real destination directory rather than left only under `~/.codex/generated_images/...`.
- The wrapper supports repeatable `--image` arguments for reference images or edit targets.

## Credits

The Codex wrapper (`scripts/codex-imagegen.sh`) is adapted from [tomc98/claude-code-codex-skill](https://github.com/tomc98/claude-code-codex-skill) by Thomas Csere (MIT).

## License

MIT — see [LICENSE](LICENSE).
