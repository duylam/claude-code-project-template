# claude-code-project-template

A starter `.claude/` config for Claude Code projects — includes curated plugins, rules, and settings to hit the ground running.

## How to use

### Install

Copy the `.claude/` directory into your repo root:

```bash
cp -r .claude/ /path/to/your-project/
```

Then follow the environment setup below to install the required plugin dependencies.

### Environment setup

#### Caveman plugin

The [caveman](https://github.com/JuliusBrussee/caveman) plugin reduces output tokens ~75% while keeping full technical accuracy.

Install for all agents on your machine (macOS / Linux / WSL):

```bash
curl -fsSL https://raw.githubusercontent.com/JuliusBrussee/caveman/main/install.sh | bash
```

Windows (PowerShell 5.1+):

```powershell
irm https://raw.githubusercontent.com/JuliusBrussee/caveman/main/install.ps1 | iex
```

Requires Node ≥18. Safe to re-run. Takes ~30 seconds.

**Trigger:** type `/caveman` or say "talk like caveman". Stop with "normal mode".

#### TypeScript LSP plugin

The `typescript-lsp` plugin gives Claude real-time TypeScript/JavaScript code intelligence (diagnostics, go-to-definition, find references).

Requires `typescript-language-server` binary:

```bash
npm install -g typescript-language-server typescript
```

Then install the plugin inside Claude Code:

```
/plugin install typescript-lsp@claude-plugins-official
```

After installing, run `/reload-plugins` to activate.

## Customization

### Settings

Refer to the [Claude Code CLI reference](https://code.claude.com/docs/en/cli-reference) to customize `.claude/settings.json` — model, permissions, env vars, hooks, and more.

### Plugins

The included `settings.json` declares additional plugin marketplaces under `extraKnownMarketplaces`. To add or swap plugins, edit that section and reference the marketplace GitHub repos:

| Marketplace key | GitHub repo |
|---|---|
| `claude-code-workflows` | [wshobson/agents](https://github.com/wshobson/agents/blob/main/docs/plugins.md) |
| `knowledge-work-plugins` | [anthropics/knowledge-work-plugins](https://github.com/anthropics/knowledge-work-plugins#plugin-marketplace) |

Official Anthropic plugins (like `typescript-lsp`, `commit-commands`, `feature-dev`) live in the [claude-plugins-official](https://github.com/anthropics/claude-plugins-official) marketplace which is built into Claude Code — no extra marketplace config needed.
