# Contributing

Thanks for your interest in contributing to the Andersen EV Home Assistant integration!

## Branch model

This repository uses a two-branch model:

* **`develop`** — the beta/staging trunk. Merges here publish `-beta.N` prereleases (release
  automation coming soon).
* **`main`** — the stable trunk. Releases are promoted here from `develop`.

Both branches are protected and PR-only — there are no direct pushes to either.

Contributor flow: fork the repo -> create a feature branch -> open a PR into `develop`. Maintainers
promote `develop -> main` for stable releases. Everyday feature/fix PRs should target `develop`,
**not** `main`.

## Commit messages

[Conventional Commits](https://www.conventionalcommits.org/) are required. Common types used in
this repo:

* `feat` — a new feature
* `fix` — a bug fix
* `docs` — documentation-only changes
* `ci` — changes to CI configuration or workflows
* `chore` — maintenance work that isn't a fix or feature (tooling, deps, config)
* `build` — changes to the build/packaging process
* `test` — adding or correcting tests
* `refactor` — code changes that neither fix a bug nor add a feature

Examples:

```
fix: resolve userLock desync when Andersen omits lock state
feat: add sensor for charger fault code
```

These commit types drive automated version bumps and changelog generation, so please use them
accurately.

## Local development

See the README's [Development](README.md#development) section for full details. In short:

* The repo ships a devcontainer (VS Code "Reopen in Container") for a full Linux test suite
  matching CI.
* Run tests with `pytest` from the repo root; lint/format with `ruff` (config at
  `custom_components/andersen_ev/ruff.toml`, line length 120).
* Enable pre-commit hooks with `pre-commit install` — see the README "Development" section for
  details.

## Releases & versioning

This project follows [Semantic Versioning](https://semver.org/). The intended flow is: merges to
`develop` cut `-beta.N` prereleases, and promotion to `main` cuts the stable release — both
produced automatically by `release-please` (landing in an upcoming PR). Until that automation is
in place, versions are bumped manually in `custom_components/andersen_ev/manifest.json`.
