# BasaltOS Repo Manifests

Release channel metadata, package repository manifests, and public promotion records.

This repo should stay free of signing keys, deploy credentials, runner secrets, and private infrastructure details.

## Owns

- `basalt.db`
- `basalt.files`
- package signatures as published to channels
- release manifests
- checksums
- repository promotion records

## Planned Layout

```text
repo-manifests/
|-- channels/
|   |-- staging/
|   |   `-- x86_64/
|   `-- stable/
|       `-- x86_64/
`-- manifests/
```

Operational publishing scripts and signing-adjacent runbooks belong in the private `release-ops` repo.

## Contracts

- Consumes signed packages from `packages/`.
- Emits repo metadata consumed by pacman, `iso/`, release tooling, and docs.
- No hand edits to generated channel metadata.

## Validation

For now, keep validation to repository shape:

```sh
test -d channels/stable/x86_64
test -d channels/staging/x86_64
test -d manifests
```
