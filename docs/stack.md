# God's Eye View in the Innotel Platform Stack

**Role: SecurityOps** — A real-time intelligence console for planet Earth, from public data.

Part of the [Innotel Platform Stack](https://github.com/innotelinc/innotel-platform-stack).
The canonical definition of the stack, its shared layers and their owners lives
there; this file records only what God's Eye View does inside it.

## Boundaries

### Owns

- the 3D globe and its layers
- the live feed adapters
- the voice-control surface

### Consumes

- public aircraft, ship, satellite, earthquake and camera feeds
- an OpenAI-compatible realtime model
- Cerulean (Authentik SSO, if deployed)

### Does not own

- the underlying data sources
- the model provider
- identity (Cerulean)

## Service map

| Component | Technology | Job |
| --- | --- | --- |
| God's Eye View | Node.js / TypeScript | A real-time intelligence console for planet Earth, from public data. |
| Identity | Cerulean Authentik | Sign-in and role claims, where the repo has a UI |
| Secrets | Cerulean Vault (KV v2) | Production credentials, referenced as `vault://` |
| Trust | Cerulean | DNS, TLS and the public hostname |
| Edge | NPM Edge | The public route in front of the service |

## In the ecosystem

- **Identity** comes from Cerulean Authentik; this repo holds no second account
  table and no password of its own.
- **Secrets** come from Cerulean Vault. `.env` is local only and is never
  committed; a `vault://` reference is resolved by the deployment.
- **Trust and edge** are Cerulean's and NPM Edge's. This repo does not write DNS
  records or call the NPM API directly.
- **Storage, billing and telephony** belong to ONYX, Magnate and Zeus
  respectively; God's Eye View consumes them only where the boundaries above say
  so.

## See also

- [README](../README.md)
- [Innotel Platform Stack](https://github.com/innotelinc/innotel-platform-stack)
