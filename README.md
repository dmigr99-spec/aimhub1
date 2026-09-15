# AimHub Public Distribution

This repository is the public distribution surface for AimHub.

The canonical development source lives in the private repository `dmigr99-spec/Aim-Hub`. Normal feature development, backend code, tests, and unreleased source changes should not be authored directly here.

## Current production compatibility

- `aimhub 2` - current public production artifact/path.
- `aimhub1` - legacy duplicate retained during migration.

These existing paths are intentionally preserved until a new loader/release-manifest flow is tested in parallel. Do not rename or delete them just to make the repository look cleaner.

## Planned distribution layout

- `loader.lua` - permanent entry point after compatibility testing.
- `channels/` - small stable/beta channel manifests.
- `releases/<version>/` - immutable published artifacts.
- `docs/` - public distribution and migration documentation.

Published artifacts should be generated from a known, tested commit in the private source repository. The public artifact should record its source revision and release version so rollback is deterministic.

## Versioning

AimHub uses semantic release versions and prereleases instead of numbered filenames. Examples: `v1.2.3`, `v1.3.0-beta.1`.

## Important

The current raw URL remains supported throughout the migration. A replacement becomes the stable path only after it is built, tested, and verified against the public raw endpoint.
