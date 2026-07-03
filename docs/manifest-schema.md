# manifest.json schema (v0.1.0)

Every package folder contains a `manifest.json` with these fields. The shape mirrors the
`RegistryPackage` type inside Metis Orchestrator (`src/shared/runtime-contracts.ts`).

| Field | Required | Description |
| --- | --- | --- |
| `schema_version` | yes | Always `"0.1.0"` for now. |
| `id` | yes | Globally unique, `<publisher>.<package-id>` (lowercase, dots/dashes). Must match the folder name. |
| `kind` | yes | `skill` \| `preset` \| `pipeline` \| `mcp` \| `template` |
| `name` | yes | Human display name. |
| `version` | yes | Semver, bumped via PR to publish an update. |
| `publisher` | yes | Your GitHub username. |
| `description` | yes | One or two sentences shown in the Marketplace. |
| `tags` | yes | Lowercase search tags, e.g. `["design", "frontend"]`. |
| `permissions_requested` | yes | Array of Metis permission scopes the package needs, e.g. `["filesystem.read"]`. Empty array if none. |
| `source_url` | yes | HTTPS URL of the payload file (raw GitHub URL — either in your own repo or in this package folder). |
| `sha256` | yes | SHA-256 hex digest of the payload at `source_url`. Installs verify this. |
| `ascii_art` | no | Small monospace art shown on the package card (array of strings, ≤ 12 lines × 40 cols). |
| `images` | no | Array of image paths relative to the package folder. |
| `policy_compat` | no | Minimum Metis Policy version, if the package depends on routing behavior. |

Compute the digest on Windows with:

```powershell
Get-FileHash payload-file -Algorithm SHA256
```
