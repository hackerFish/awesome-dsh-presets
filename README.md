# 🐋 awesome-dsh-presets — Tested Presets & Rules for DeepSeek Harness

**4 presets (2 derived from official shipped presets with attribution, 2 original) and 4 AGENTS.md rule packs. Every preset passes YAML/`!!js`-dialect parsing, structure checks, and package-existence validation against a real harness install.**

[中文](README.zh.md) · Siblings: [dsh-lab](https://github.com/hackerFish/dsh-lab) · [awesome-dsh-skills](https://github.com/hackerFish/awesome-dsh-skills) · [dsh-video-studio](https://github.com/hackerFish/dsh-video-studio)

## What's inside

- **Presets** (`agent.cordis.yml` + `preset.yml`): drop a directory into `~/.dsh/.agent-presets/` and pick it in new sessions (mechanism per official `@deepseek-ai/dsh-agent-presets`).
- **Rules** (`rules/*.md`): append to `~/.dsh/AGENTS.md`.

## Install

```bash
git clone https://github.com/hackerFish/awesome-dsh-presets ~/dsh-presets
mkdir -p ~/.dsh/.agent-presets
cp -r ~/dsh-presets/presets/minimal-zh ~/.dsh/.agent-presets/   # pick what you need
cat ~/dsh-presets/rules/code-quality.md >> ~/.dsh/AGENTS.md
```

## Presets

| Preset | Type | Notes |
|---|---|---|
| standard-zh | Derived (official standard, MIT, Chinese persona) | Full coding agent |
| minimal-zh | Derived (official minimal, Chinese persona) | Two-tool minimal |
| writer | Original | Chinese technical writing combo |
| researcher | Original | Research combo |
| web-dev | Original | Web-dev pretexts: 23 companion skills, stack choice to deploy |

## Rules

code-quality · commit-discipline · pr-review · safety-guardrails

## Quality gates

`node tools/validate-presets.mjs --harness <node_modules root>` — YAML (incl. `!!js` dialect) parses, top-level list of `{id,name}` rows, nested `cordis:group` recursion, every referenced `@deepseek-ai/*` package must exist in the harness install.

## License

[MIT](LICENSE)
