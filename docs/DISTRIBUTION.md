# Distribution Contract

## Repository purpose

This public repository publishes client artifacts. It is not the canonical development source and must not contain production backend secrets or private service code.

## Target layout

### Permanent loader

`loader.lua` becomes the long-lived entry point only after executor/runtime compatibility is verified. It should resolve a release from a small channel manifest rather than depending on filenames such as `aimhub 2`.

### Channel manifests

Planned examples:

- `channels/stable.json`
- `channels/beta.json`

A channel manifest should identify a semantic version, immutable release artifact path, artifact hash, and source commit SHA.

### Immutable releases

Published artifacts live under `releases/<version>/`. Once a stable version is published, its artifact should not be edited in place. Fixes produce a new version.

## Rollback

Rollback changes the stable channel pointer to a previously verified immutable release. This keeps rollback fast and auditable.

## Legacy compatibility

The current `aimhub 2` path remains available until the new loader/channel flow is verified and existing consumers have a migration path. `aimhub1` is also retained during this phase because it is an existing public path.

## Publication rule

A stable artifact must originate from a specific tested commit in `dmigr99-spec/Aim-Hub`, pass release checks, and have its hash recorded before the stable channel is updated.
