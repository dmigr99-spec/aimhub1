# Distribution Contract

## Repository purpose

This public repository publishes client artifacts. It is not the canonical development source and must not contain production backend secrets or private service code.

## Target layout

### Permanent loader

`loader.lua` becomes the long-lived entry point only after runtime compatibility and the authenticated delivery path are verified. It should resolve a release through controlled release metadata rather than depending on filenames such as `aimhub 2`.

### Channel manifests

Planned examples:

- `channels/stable.json`
- `channels/beta.json`

A channel manifest should identify a semantic version, immutable release artifact identifier/path, artifact hash, and source commit SHA. Do not publish private repository credentials or backend secrets in manifests.

### Immutable releases

Published artifacts live under `releases/<version>/` only when publication is intentionally part of the delivery design. Once a stable version is published, its artifact must not be edited in place. Fixes produce a new version.

## Rollback

Rollback changes the stable channel pointer to a previously verified immutable release. This keeps rollback fast and auditable.

## Legacy compatibility

The current `aimhub 2` path remains available until the replacement loader/delivery flow is verified and existing consumers have a migration path. `aimhub1` is also retained during this phase because it is an existing public path.

During migration, CI pins both legacy files to their current Git blob hashes:

- `aimhub 2`: `3312b23367acd7ed3044dd564033b358c44739b6`
- `aimhub1`: `0337693716feffb94bc5c622cef5b939c04dfeb4`

An intentional migration that changes either legacy artifact must therefore update this contract and its CI fingerprints in the same reviewed change. This prevents an unrelated PR from silently changing a live raw path.

## Publication rule

A stable artifact must originate from a specific tested commit in `dmigr99-spec/Aim-Hub`, pass release checks, and have its hash recorded before any stable channel or delivery pointer is updated.
