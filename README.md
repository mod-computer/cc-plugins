# cc-plugins

Claude Code plugin marketplace for Mod.

## Adding as a Marketplace

Add this repository as a plugin marketplace in Claude Code:

```bash
claude plugins:add-marketplace /path/to/cc-plugins
```

Or add to your Claude Code settings (`~/.claude/settings.json`):

```json
{
  "pluginMarketplaces": [
    "/path/to/cc-plugins"
  ]
}
```

## Available Plugins

| Plugin | Description |
|--------|-------------|
| [spec-plugin](./plugins/spec-plugin) | Skills for writing specs, adding traces, and reviewing requirements |

## Installing Plugins

After adding the marketplace, install plugins with:

```bash
claude plugins:install spec-plugin
```

Or use `/plugin` in Claude Code to browse and install.

## Structure

```
cc-plugins/
├── .claude-plugin/
│   └── marketplace.json    # Plugin registry
└── plugins/
    └── spec-plugin/        # Individual plugins
```
