# Newtake Marketplace

The Codex plugin directory for **Newtake**, served from `https://mcp.newtake.ai/mcp`.
It carries one plugin: [`newtake`](plugins/newtake).

| Install name | Display name | Endpoint | Version |
| --- | --- | --- | --- |
| `newtake` | Newtake | `https://mcp.newtake.ai/mcp` | `0.3.5` |

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
| `plugins/newtake/` | The package itself: `.codex-plugin/plugin.json`, `.mcp.json`, `assets/newtake-icon.svg`, `skills/` |

Three rules come from the Codex plugin contract and must stay true:

- Directory name = `plugin.json` `name` = marketplace entry `name` = MCP server key = `newtake`.
- Each plugin needs its own MCP server key; two packages sharing one key fight over
  `mcp_servers.<key>` and overwrite each other.
- A package is self-contained: nothing is generated, shared or downloaded at publish time.

`assets/newtake-icon.svg` is the official Newtake mark, byte-identical to
`https://www.newtake.ai/newtake-favicon.svg`. Note that this icon only reaches the plugin card,
detail page, install modal and composer; the icon on MCP tool-call rows comes from the server's
`initialize` response instead.

## Skills

The package ships three workflow Skills under `plugins/newtake/skills/`:

| Skill | What it does |
| --- | --- |
| `newtake-to-treatment` | Turns the finished work on a canvas — images, video, audio, script, storyboard — into a paginated 16:9 director treatment, delivered as `index.html` plus an assets folder and a ZIP |
| `newtake-blender-live-action` | Script and scene references → canvas images → Blender white-model previs with deliberate camera choreography → Seedance 2.5 live-action video |
| `music-driven-product-ad` | A Zen Piano soundtrack plus a 20-second one-take product ad that moves right through connected spaces, with the verified WAV composited in post |

One thing to know before relying on them:

- **They exercise paths the service does not serve yet** — generation submit, task status, export,
  download, upload and media analysis. Run end to end only after the release gates below open; today
  they stop at the first withheld tool.

## Licensing of bundled score assets

`plugins/newtake/skills/music-driven-product-ad/assets/scores/` carries piano scores. All of them are
public domain except `mendelssohn-wedding-march`, whose Mutopia edition and the derived
`mendelssohn-wedding-march.score.json` are **CC BY-SA 4.0** (typeset © 2017 Alexander Brock, based on
the Dubois transcription published by Durand & Cie., plate D. & F. 9516). Keep that attribution and
license notice when redistributing the source or any derived wedding score. Per-piece metadata,
sources and MIDI hashes live in `assets/scores/catalog.json` and `references/repertoire.md`.

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

- Everything shipped here is English: the manifest, this README, the composer prompts and the three
  Skills, which now produce English deliverables. The only non-English strings left are the
  interface tokens and the external preset name listed under "Skills".
- The Skills take their tool and authentication rules from the MCP connection's instructions rather
  than from cross-Skill references, so a Skill can be read on its own.
