# 03 · Rendering strategies: CSR, SSR, SSG, ISR, streaming

| Strategy | HTML produced | Best for | Watch out for |
|---|---|---|---|
| CSR | In the browser | Authenticated apps behind login, dashboards | Slow first paint on weak devices, no SEO for public content |
| SSG | At build | Docs, marketing, blogs | Build time grows with page count; stale until rebuild |
| ISR / stale-while-revalidate | Build, then regenerated on demand | Catalogues that change hourly | Cache invalidation semantics; per-user data cannot be cached |
| SSR | Per request | Personalised or fresh public pages, SEO | Server cost and TTFB; hydration cost; need to avoid request waterfalls |
| Streaming SSR + Suspense | Shell first, slow parts later | Pages with one slow data dependency | Error handling inside streamed boundaries; layout shift if fallbacks are the wrong size |

## Decision procedure

1. Is the content public and does it need to be indexed? If no, **CSR** is usually enough (the reference app).
2. Is it identical for all users? **SSG/ISR**.
3. Does it depend on the user or request? **SSR**, and stream slow parts.
4. Within any of these, hydrate as little as possible: islands, server components, or lazy hydration for below-the-fold widgets.

## Costs that are easy to miss

- **Hydration** re-runs component code on the client; a server-rendered page can look ready but not respond (affects INP).
- **Waterfalls**: server-render → hydrate → client fetch. Move data fetching to the server or the route loader.
- **Caching layers** (CDN, framework cache, query cache) must agree on invalidation; document who owns each.
