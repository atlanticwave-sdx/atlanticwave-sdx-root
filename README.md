# AtlanticWave-SDX Release Repository

## Purpose

This repository is the **system-level release and orchestration repository**
for the AtlanticWave-SDX platform.

It does **not** contain application code.

---

## What This Repository Does

- Aggregates AtlanticWave-SDX component repositories using Git submodules
- Pins exact component versions for each platform release
- Defines platform deployment via Docker Compose
- Serves as the **single source of truth** for AtlanticWave-SDX platform releases
- Enables reproducible deployments and rollbacks via Git tags

---

## What This Repository Does NOT Do

- Does not build application code
- Does not modify component repositories
- Does not define development workflows for individual components
- Does not publish container images

---

## Repository Structure

```
sdx-release/
├── services/            # Git submodules (pinned component repositories)
├── docker-compose.yml   # Platform orchestration
├── docs/                # Human-facing documentation (GitHub Pages)
│   ├── index.md
│   ├── release-process
│       ├── index.md
│   └── releases
│       ├── v2022.1.0
│           ├── index.md
│       ├── v2026.1.0
│           ├── index.md
├── .gitmodules
└── README.md
```

---

## Documentation

Human-facing documentation lives under `docs/` and is published via GitHub Pages.

- Overview and usage: `docs/index.md`
- Release process: `docs/release-process.md`
- Platform releases: `docs/releases/`

---

## Cloning the Repository

You must clone with submodules:

```bash
git clone --recurse-submodules https://github.com/atlanticwave-sdx/sdx-release.git
```

If already cloned without submodules:

```bash
git submodule update --init --recursive
```

---

## Using a Platform Release (Operators)

A platform release is defined by a **Git tag** in this repository
(for example: `v2026.1.0`).

```bash
git fetch --tags
git checkout v2026.1.0

git submodule sync --recursive
git submodule update --init --recursive

export SDX_VERSION=v2026.1.0
docker compose pull
docker compose up -d
```

Stop the platform:

```bash
docker compose down
```

---

## Platform Releases

- Platform releases use a **year-based versioning scheme**
  (for example: `v2026.1.0`)
- Each tag pins:
  - Exact submodule commits
  - Corresponding published container images
  - A reproducible Docker Compose deployment

Release notes and instructions are documented under:

```
docs/releases/
```

---

## Updating Component Versions (Maintainers)

To update a component for a future release:

```bash
cd services/<component>
git fetch
git checkout <desired-commit-or-tag>
```

Then update the pointer in this repository:

```bash
cd ../../
git add services/<component>
git commit -m "Update <component> submodule for next release"
git push
```

This **does not** affect existing platform release tags.

---

## Creating a New Platform Release

Creating a release means tagging this repository **after validation**:

```bash
git tag v2026.1.1
git push origin v2026.1.1
```

See `docs/release-process.md` for the authoritative release procedure.

---

## Why This Is Safe and Reversible

This repository uses Git submodules.

That means:
- Component repositories remain independent
- No history is rewritten
- No files are moved
- Existing releases are immutable once tagged

Worst case scenario:
**Delete this repository.**
Nothing else is affected.

---

## Final Note

This repository exists to make AtlanticWave-SDX **deployable, reproducible,
and auditable** at the platform level.

It is intentionally minimal.

