# ADR-0001: Modular monolith before micro-frontends

**Status:** Accepted

## Context

Several teams will contribute to one product surface. Micro-frontends offer independent deploys but add runtime and operational cost (see [case study 02](../case-studies/02-micro-frontends-vs-modular-monolith.md)).

## Decision

Use a single deployable with lint-enforced module boundaries and a versioned design-system package. Revisit if teams are blocked by a shared release train.

## Alternatives considered

Module Federation from day one: independence, but duplicate runtime risk and contract overhead without a demonstrated need.

## Consequences

Simpler tooling and consistent UX; releases are coordinated. Trigger to revisit: measurable cross-team release blocking.
