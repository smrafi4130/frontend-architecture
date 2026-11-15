# ADR-0003: Refresh token in an httpOnly cookie for production

**Status:** Accepted as the target design; the reference app uses `sessionStorage` as a documented stand-in.

## Decision

Access token in memory, refresh token in `httpOnly; Secure; SameSite=Lax/Strict` cookie, CSRF-protected refresh endpoint, single-flight refresh on the client.

## Consequences

Removes the long-lived credential from script reach. Requires backend cooperation and a same-site deployment (or BFF).
