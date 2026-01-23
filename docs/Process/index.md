# Release Process

This document defines how to cut an official **AtlanticWave-SDX platform release**
from the `sdx-release` repository.

## Definition

An AtlanticWave-SDX release is a **Git tag in this repository** (for example,
`v2026.1.0`) that:

- Pins the exact versions of all platform components via Git submodules
- Corresponds to published container images for those components
- Defines a reproducible deployment using `docker-compose.yml`

The Git tag is the single source of truth for a platform release.

## Scope

This repository does **not** build application code.
It aggregates and pins component repositories and documents how to run them
together as a platform.

## High-level release steps

1. **Select component versions**
   - Identify the exact commits or tags to use for each component repository.

2. **Update submodule pointers**
   - Update this repository so each submodule points to the selected version.
   - Verify with `git submodule status --recursive`.

3. **Validate the platform**
   - Ensure container images exist for the intended release version.
   - Validate the stack using `docker compose` and the `SDX_VERSION` variable.

4. **Create the platform tag**
   - Tag the repository using the year-based scheme (for example, `v2026.1.0`).
   - Push the tag to the remote repository.

5. **Publish documentation**
   - Add or update release notes under `docs/releases/`.
   - Ensure operator and developer usage instructions are documented.
   - Publish documentation via GitHub Pages from the `docs/` directory.

## Notes

- Platform releases are immutable once tagged.
- Documentation may evolve on `main`, but tags represent fixed, reproducible states.
- Development work should never occur directly on release tags.

