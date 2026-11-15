# ADR-0004: Two-tier design tokens

**Status:** Accepted. Implemented in [react-design-system](https://github.com/smrafi4130/react-design-system).

## Decision

Primitive tokens hold raw values; semantic tokens (`accent.default`) alias primitives per theme. Components use only semantic tokens. A small in-repo transform resolves aliases and fails on unknown references or cycles.

## Alternatives considered

Style Dictionary: powerful, but a large config surface for a 64-token set.

## Consequences

Dark mode required no component changes. Cost: maintaining a tiny build script; migrate to Style Dictionary if multi-platform output (iOS/Android) becomes a requirement.
