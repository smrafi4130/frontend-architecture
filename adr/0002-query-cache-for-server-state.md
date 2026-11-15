# ADR-0002: Query cache for server state

**Status:** Accepted. Implemented in [enterprise-react-app](https://github.com/smrafi4130/enterprise-react-app).

## Decision

TanStack Query owns server state; a small Zustand store owns client state (session). Mutations invalidate keys; high-intent actions are optimistic with rollback.

## Alternatives considered

Redux Toolkit + RTK Query (more ceremony at this size); normalised graph cache (schema coupling not justified).

## Consequences

No hand-written loading/error state. Risk: forgetting to invalidate related keys. Mitigation: co-locate keys with queries and cover cross-key invalidation in integration tests.
