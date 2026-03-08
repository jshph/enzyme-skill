# Enzyme — Agent Skill

An [Agent Skill](https://agentskills.io) for exploring Obsidian vaults with [Enzyme](https://enzyme.garden). Works with any agent that supports the Agent Skills format.

Enzyme turns your vault into something you can converse with — surfacing connections between ideas by concept, not keyword.

## Supported Agents

Any agent implementing the [Agent Skills spec](https://agentskills.io/specification), including Claude Code, Cursor, Gemini CLI, OpenCode, Goose, Roo Code, and [many others](https://agentskills.io/home).

## Self-contained

The binary (macOS arm64, Linux x86_64, Linux arm64) and embedding model are bundled — no separate install step needed. The skill's setup script copies the right binary for the current platform to `~/.cache/enzyme/` and puts `enzyme` on PATH.

## Installation

Copy or symlink the `enzyme/` directory into your agent's skills location. For example, with Claude Code:

```bash
cp -r enzyme/ ~/.claude/skills/enzyme
```

Refer to your agent's documentation for where skills are loaded from.

## Skill Structure

```
enzyme/
├── SKILL.md                  # Main skill instructions
├── bin/                      # Platform binaries
│   ├── enzyme-macos-arm64
│   ├── enzyme-linux-x86_64
│   └── enzyme-linux-arm64
├── models/                   # Embedding model (~23 MB)
│   ├── model.onnx
│   └── tokenizer.json
├── scripts/
│   └── setup.sh              # Bootstrap script (no network needed)
└── references/
    ├── petri-guide.md        # How to present vault overview results
    └── search-guide.md       # How to present search results
```

## Usage

Once installed, invoke the skill when you want to explore your Obsidian vault by concept. The skill teaches agents how to use the `enzyme` CLI to:

- **`enzyme petri`** — See trending entities, active themes, and catalyst questions
- **`enzyme catalyze "query"`** — Search by concept/theme, not keyword
- **`enzyme refresh`** — Update the index after vault changes
- **`enzyme apply <dir>`** — Project vault catalysts onto external content

## License

MIT
