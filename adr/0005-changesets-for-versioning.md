# ADR-0005: Changesets for library versioning

**Status:** Accepted

## Decision

Every PR touching a published package includes a changeset describing the change and bump type. CI opens a "Version packages" PR; merging it publishes.

## Consequences

Breaking changes are explicit and reviewable; changelogs are generated. Cost: contributor discipline, mitigated by a CI check for missing changesets.
