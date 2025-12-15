# AtlanticWave-SDX Root Repository

## Purpose

This repository is the system-level orchestration and release repository for the AtlanticWave-SDX platform.

It does not contain application code.

---

## What This Repository Does

- Aggregates SDX repositories using Git submodules
- Defines system-wide deployment via Docker Compose
- Provides a single authoritative SDX release
- Enables reproducible deployments and rollbacks

---

## Repository Structure

atlanticwave-sdx-root/
├── services/           # Git submodules
├── docker-compose.yml  # Platform orchestration
├── .gitmodules
└── README.md

---

## Cloning the Repository

You must clone with submodules:

git clone --recurse-submodules https://github.com/atlanticwave-sdx/atlanticwave-sdx-root.git

---

## Adding a New SDX Component

If a new SDX repository is created:

git submodule add https://github.com/atlanticwave-sdx/<new-repo>.git services/<new-repo>
git add .gitmodules services/<new-repo>
git commit -m "Add <new-repo> as SDX component"
git push

Optionally update docker-compose.yml.

---

## Why This Is Reversible

This repository uses Git submodules.

That means:
- Existing repositories remain unchanged
- No history is rewritten
- No files are moved
- No tags or branches are modified

This repository stores only:
- Repository URLs
- Pointers to exact commits

Nothing else.

---

## What Was Created

- This root repository
- .gitmodules
- services/ placeholders
- Docker Compose
- Root-level tags only

---

## What Was NOT Changed

- No commits added to component repositories
- No tags added automatically
- No releases overwritten
- No dependencies introduced

Each repository still works standalone.

---

## Reversal Scenarios

### Delete Everything
Delete this repository. Full rollback.

### Remove a Component
git submodule deinit -f services/<repo>
git rm -f services/<repo>
rm -rf .git/modules/services/<repo>
git commit -m "Remove <repo>"
git push

### Undo a Tag
git tag -d vX.Y.Z
git push origin :refs/tags/vX.Y.Z

### Add a New Component
Follow the procedure above. Existing releases are unaffected.

---

## Final Note

Worst case scenario:
Delete this repository.

Nothing else is affected.
