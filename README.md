# claude-code-project-template

A starter `.claude/` config for Claude Code projects — includes curated plugins, rules, and settings to hit the ground running.

## Install to your project

### Copy the config

1. Copy the `.claude/` directory into your repo root:

```bash
cp -r .claude/ /path/to/your-project/
```

2. Open this repo's `.gitignore` and copy the lines marked `# COPY to your .gitignore` into your project's `.gitignore`.

### Install Node.js (for the caveman plugin)

The [caveman](https://github.com/JuliusBrussee/caveman) plugin is already enabled via the copied `settings.json` and reduces output tokens ~75% while keeping full technical accuracy. It just needs Node ≥18 on your machine to run.

If you don't have Node installed, the quickest way is via [nvm](https://github.com/nvm-sh/nvm):

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash
nvm install --lts
```

(Check the [nvm releases](https://github.com/nvm-sh/nvm/releases) for the latest install script version.)

**Trigger:** type `/caveman` or say "talk like caveman". Stop with "normal mode".

### Customize the hooks

Hooks ship **disabled by default** (`disableAllHooks: true` in `.claude/settings.json`).

To opt in, remove or set `"disableAllHooks": false` in `.claude/settings.json`.

## Reference

### Git submodules

**Initialize submodules after cloning without `--recurse-submodules`:**

```bash
git submodule update --init --recursive
```

**Pull latest changes (repo + all submodules):**

```bash
git pull --recurse-submodules
```

**Update all submodules to their latest remote commit:**

```bash
git submodule update --remote --checkout
```

### Marketplaces

The included `settings.json` declares additional plugin marketplaces under `extraKnownMarketplaces`. To add or swap plugins, edit that section and reference the marketplace GitHub repos:

| Marketplace key | GitHub repo |
|---|---|
| `claude-code-workflows` | [wshobson/agents](https://github.com/wshobson/agents/blob/main/docs/plugins.md) |
| `knowledge-work-plugins` | [anthropics/knowledge-work-plugins](https://github.com/anthropics/knowledge-work-plugins#plugin-marketplace) |

Official Anthropic plugins (like `typescript-lsp`, `commit-commands`, `feature-dev`) live in the [claude-plugins-official](https://github.com/anthropics/claude-plugins-official) marketplace which is built into Claude Code — no extra marketplace config needed.

### Settings

Refer to the [Claude Code CLI reference](https://code.claude.com/docs/en/cli-reference) to customize `.claude/settings.json` — model, permissions, env vars, hooks, and more.
