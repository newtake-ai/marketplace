# Newtake Marketplace

The Codex plugin directory for **Newtake**, served from `https://mcp.newtake.ai/mcp`.
It carries one plugin: [`newtake`](plugins/newtake).

| Install name | Display name | Endpoint | Version |
| --- | --- | --- | --- |
| `newtake` | Newtake | `https://mcp.newtake.ai/mcp` | `0.1.0` |

The plugin is a Codex-native HTTP remote MCP: it ships no client ID, redirect URI, credential or
local server. The client registers and signs in through the server's own OAuth metadata.

## Install

This repository is public — no GitHub authorization is needed, only working Git access to GitHub.

```bash
codex plugin marketplace add https://github.com/newtake-ai/marketplace.git --ref main
codex plugin add newtake@newtake
```

Reload plugins or start a new Codex task, then complete the Newtake sign-in on the `newtake` MCP
connection. Every tester signs in with their own Newtake account.

## Update

```bash
codex plugin marketplace upgrade newtake
codex plugin add newtake@newtake
```

Verify in a new Codex task. Before you sign in, `POST /mcp` answers `401` with
`WWW-Authenticate: Bearer` while both OAuth well-known endpoints answer `200`; that is the expected
state, not a broken install.

## Layout

| Path | Contents |
| --- | --- |
| `.agents/plugins/marketplace.json` | Catalog: one entry, `newtake`, category `Creativity`, installation `AVAILABLE`, authentication `ON_INSTALL` |
| `plugins/newtake/` | The package itself: `.codex-plugin/plugin.json`, `.mcp.json`, `assets/newtake-icon.svg` |

Three rules come from the Codex plugin contract and must stay true:

- Directory name = `plugin.json` `name` = marketplace entry `name` = MCP server key = `newtake`.
- Each plugin needs its own MCP server key; two packages sharing one key fight over
  `mcp_servers.<key>` and overwrite each other.
- A package is self-contained: nothing is generated, shared or downloaded at publish time.

`assets/newtake-icon.svg` is the official Newtake mark, byte-identical to
`https://www.newtake.ai/newtake-favicon.svg`. Note that this icon only reaches the plugin card,
detail page, install modal and composer; the icon on MCP tool-call rows comes from the server's
`initialize` response instead.

## Release status

The package is a thin client: what a user can actually do is decided by the gateway behind
`mcp.newtake.ai`. That gateway serves the overseas Newtake profile (`environment=intl-prod`,
English-only) and withholds every tool group whose backend is not deployed overseas yet — the
remote task chain (generation submit / task status / export / download), media analysis, uploads,
and canvas inline execution. Tool availability is one reviewable list in the gateway code, and the
conclusive release state lives in the gateway repository's `deploy/intl-prod/rollout.yaml`
(`release_gates`); this README only points at it.

Until those gates declare the overseas service released, treat this directory as **staged**:
installing it to verify a build is fine, announcing it to users is not.

## Source of truth

This repository is the source of truth for the `newtake` package — edit `plugins/newtake/` here.
Any content change bumps `version` in `plugins/newtake/.codex-plugin/plugin.json` by
`MAJOR.MINOR.PATCH`; never reuse a version already published for this package, and keep the version
in the table above in step with it.

Before pushing, validate the package manifest:

```bash
python3 ~/.codex/skills/.system/plugin-creator/scripts/validate_plugin.py plugins/newtake
```

Changes to the gateway itself (tool gating, branding, OAuth) belong in the gateway repository, not
here.

## Notes

- Skills for advanced workflows (Blender live action, music-driven ads, treatment decks) are not
  part of this package yet; the first release covers sign-in → projects and canvases → model
  discovery → generation → result on the canvas.
- The product is English-only: the plugin manifest, prompts and every future Skill in this package
  are written in English.
