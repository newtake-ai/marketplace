# Newtake for Codex

Newtake is an AI visual canvas: start from an idea, a script or a reference image and build the
result on a canvas you keep editing. This repository is the Codex plugin marketplace that carries
the official `newtake` plugin, which connects Codex to the Newtake remote MCP server at
`https://mcp.newtake.ai/mcp`.

| Install name | Display name | Endpoint | Version |
| --- | --- | --- | --- |
| `newtake` | Newtake | `https://mcp.newtake.ai/mcp` | `1.0.0` |

## Install

This repository is public — no GitHub authorization is needed, only working Git access to GitHub.

```bash
codex plugin marketplace add https://github.com/newtake-ai/marketplace.git --ref main
codex plugin add newtake@newtake
```

Reload plugins or start a new Codex task, then complete the Newtake sign-in on the `newtake` MCP
connection. You sign in with your own Newtake account.

## Update

```bash
codex plugin marketplace upgrade newtake
codex plugin add newtake@newtake
```

## What you can do

- Sign in with your Newtake account and work inside your own projects.
- List and open your projects and canvases.
- Discover the image and video models available to you.
- Create and arrange nodes, write and edit scripts, and read the timelines, groups and media already
  on a canvas.
- Set up image and video generation with the model you choose, and follow what the canvas produced.

Everything lands in your own Newtake account, so you can pick the work up again in the Newtake canvas
at any time.

## Signing in

Before you sign in, `POST /mcp` answers `401` with `WWW-Authenticate: Bearer` while both OAuth
well-known endpoints answer `200`. That is the expected state, not a broken install.

## Skills

The plugin ships three workflow Skills that Codex can run for you:

| Skill | What it does |
| --- | --- |
| `newtake-to-treatment` | Turns the finished work on a canvas — images, video, audio, script, storyboard — into a paginated 16:9 director treatment, delivered as `index.html` plus an assets folder and a ZIP |
| `newtake-blender-live-action` | Script and scene references → canvas images → Blender white-model previs with deliberate camera choreography → Seedance 2.5 live-action video |
| `music-driven-product-ad` | A Zen Piano soundtrack plus a 20-second one-take product ad that moves right through connected spaces, with the verified WAV composited in post |

These three are previews: they lean on generation paths that are still being completed on the hosted
service, so check the result before you rely on it.

## Bundled score assets

`music-driven-product-ad` bundles piano scores. All of them are public domain except
`mendelssohn-wedding-march`, whose Mutopia edition and the derived
`mendelssohn-wedding-march.score.json` are **CC BY-SA 4.0** (typeset © 2017 Alexander Brock, based on
the Dubois transcription published by Durand & Cie., plate D. & F. 9516). Keep that attribution and
license notice when redistributing the source or any derived wedding score.
