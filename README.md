# SpilledCinema Default Connectors

This directory is the seed content for the default connector repository.

Host `spilled-connectors.json` at the root of a GitHub repository. In the app,
users can paste either the GitHub repository URL or the raw JSON URL in
Settings -> Sources -> Connector repositories.

The current runtime supports these built-in adapter ids:

- `svetserialu`
- `bombuj`
- `synova`

Each module can include a `runtime.entry` that points at an ESM file in this
repository. The local SpilledCinema runtime fetches that file and calls:

- `getFeed({ moduleId, feedId, cursor, limit })`
- `search({ moduleId, query })`

Both functions should return the same JSON shapes used by SpilledCinema provider
feed/search endpoints. Repository runtime code is used before bundled fallback
adapters when the repository URL is configured in the app.
