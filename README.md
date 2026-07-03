# Metis Registry

The community package registry and live catalog for [Metis Orchestrator](https://github.com/lachydotmcg/metis-orchestrator) — the local-first AI orchestration desktop app.

No server, no accounts. This repo is the registry: the app fetches raw JSON from here over HTTPS, and publishing is a pull request.

## What lives here

```
packages/            one folder per published package
  <publisher>.<id>/
    manifest.json    metadata: name, kind, tags, permissions, source_url, sha256
    (payload files)  optionally, small payloads live right here in the registry
catalog/
  models.json        the live model catalog — the app's model picker updates
                     from this file, so new models reach every install the day
                     they're merged (no app release needed)
featured.json        the Pulse feed: community creations, changelog, AI news
docs/
  manifest-schema.md manifest field reference
```

## Publishing a package

1. Build your skill / preset / pipeline / MCP config. Host the payload in your own repo, or (for small text payloads like a single skill file) directly in your package folder here.
2. Add `packages/<your-github-username>.<package-id>/manifest.json` — see [docs/manifest-schema.md](docs/manifest-schema.md) and the example package.
3. Set `sha256` to the SHA-256 hex of your payload file so installs can verify integrity.
4. Open a pull request. Merged = published. Your GitHub username is your publisher identity.

## Installing

Use the Marketplace inside Metis Orchestrator. Installs fetch from `source_url`, verify the `sha256`, and show `permissions_requested` before anything is written.

## Package kinds

`skill` · `preset` · `pipeline` · `mcp` · `template`

## Trust model

- Manifests are human-reviewed via PR before they appear.
- Payloads are pinned by SHA-256 — the file you reviewed is the file users get.
- Every permission a package wants is declared in the manifest and surfaced at install time by the app's permission ceremony.
