<div align="center">

# claude-plugins

**Public marketplace for Claude Code plugins by [@atj393](https://github.com/atj393).**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Plugins](https://img.shields.io/badge/plugins-1-blue)](#plugins)
[![Marketplace](https://img.shields.io/badge/marketplace-atj393--plugins-6E4AFF)](.claude-plugin/marketplace.json)

</div>

---

A Claude Code plugin marketplace is a single JSON manifest listing plugins and where to fetch
them from. This repository holds that manifest and nothing else. Each plugin lives in its own
repository.

## Project status

- **Source:** open source under **MIT**.
- **Marketplace name:** `atj393-plugins`, defined in [`.claude-plugin/marketplace.json`](.claude-plugin/marketplace.json).
- **Plugins listed:** 1.
- **Requirements:** Claude Code (CLI, desktop app, or a supported IDE).

## Install

From any Claude Code session:

```
/plugin marketplace add atj393/claude-plugins
/plugin install code-cleanup
```

Then confirm:

```
/plugin
/help
```

## Plugins

| Plugin | Description | Source |
|---|---|---|
| `code-cleanup` | Careful, low-risk codebase cleanup pass with a lead agent and seven specialist workers. | [atj393/claude-plugin-code-cleanup](https://github.com/atj393/claude-plugin-code-cleanup) |

## How pinning works

Every entry in the manifest carries a `sha`. Claude Code fetches that exact commit rather than
the plugin repository's current tip, so a plugin cannot change under an installed user without
this repository changing first.

The trade-off is that pushing a fix to a plugin repository is not enough on its own. The
manifest entry has to be bumped to the new commit as well, and users then run:

```
/plugin update code-cleanup
```

## Uninstall

```
/plugin uninstall code-cleanup
/plugin marketplace remove atj393-plugins
```

The marketplace is removed by its name, `atj393-plugins`, not by the repository name.

## Adding a plugin

Add an object to the `plugins` array in
[`.claude-plugin/marketplace.json`](.claude-plugin/marketplace.json) with a `name`, a
`source` block naming the GitHub repository, the `sha` to pin, and a one-line `description`.

## License

[MIT](LICENSE).
