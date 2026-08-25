# Calliope AI plugin marketplace

A curated index of Calliope AI plugins, installable from the **Plugins** view in
Calliope AI IDE. Agents, skills, instructions, hooks, and MCP server
definitions.

## What this repo is, and is not

This is an **index**, not a container. `marketplace.json` lists plugins and says
where each one lives; the plugins themselves stay in their own repositories and
keep their own release cadence. Nothing is vendored here.

That shape is deliberate. A marketplace that bundled its plugins would make
every content change a change to this repo, and would put the skills catalogue
and the IDE's plugin list in the same release train. They are different things
with different audiences.

## Adding a plugin

One entry in `marketplace.json`:

```json
{
  "name": "some-plugin",
  "description": "What it gives you, in one line.",
  "version": "0.1.0",
  "source": { "source": "github", "repo": "calliopeai/some-plugin" }
}
```

`source` may also be a relative path (a plugin living inside this repo), a git
URL, or an npm/pip package. Omitting it entirely means *this repository is the
plugin*, which is the single-plugin form and not what this index uses.

A plugin repository needs a manifest at its root — `.plugin/plugin.json`,
`.claude-plugin/plugin.json`, or `plugin.json` — and any of `commands/`,
`skills/<name>/SKILL.md`, `agents/*.md`, `hooks.json`, or `.mcp.json`.

## Using it

Add this repository to `chat.plugins.marketplaces`:

```json
"chat.plugins.marketplaces": ["calliopeai/calliope-marketplace"]
```

While this repository is private, that only resolves for users whose GitHub
account can read it. It is not wired into the shipped build's defaults yet, and
should not be until the repository is public — a default pointing at a
repository most users cannot read would show them an empty Plugins list with no
explanation.

## License

MIT. Each listed plugin carries its own license in its own repository.
