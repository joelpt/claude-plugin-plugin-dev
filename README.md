# plugin-dev

Claude Code plugin-development skills, agents, and commands — slim wrappers over the upstream
`anthropics/claude-plugins-public` plugin-dev surface (hook, command, skill, agent, MCP,
settings, structure).

## Architecture

The wrapper files (`skills/`, `agents/`, `commands/`) are thin: each `Read`s the corresponding
file from the pinned upstream, vendored here as a git **submodule** at `upstream/`. Wrapper
bodies reference it via `${CLAUDE_PLUGIN_ROOT}/upstream/...` so they resolve wherever the plugin
is installed.

Upstream is pinned to a specific commit (`edb2c52`). To bump: update the submodule, re-pin,
bump `.claude-plugin/plugin.json` `version`.

## Install

```bash
claude plugin marketplace add joelpt/joelpt-claude-plugins
claude plugin install plugin-dev@joelpt-claude-plugins
```

Then restart Claude Code. Requires read access to the private marketplace repo.

## Clone for development

```bash
git clone --recurse-submodules https://github.com/joelpt/claude-plugin-plugin-dev.git
```

Distributed via the [`joelpt-claude-plugins`](https://github.com/joelpt/joelpt-claude-plugins)
marketplace. Bump `version` (patch minimum) on any change — the marketplace cache is keyed by version.

## License

MIT (wrapper). Upstream submodule retains its own license.
