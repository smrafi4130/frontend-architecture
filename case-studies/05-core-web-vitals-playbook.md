# 05 · Core Web Vitals playbook

Targets (75th percentile of real users): **LCP ≤ 2.5 s, INP ≤ 200 ms, CLS ≤ 0.1.**

## Method

1. **Measure in the field first** (RUM via `web-vitals`), then reproduce in the lab (Lighthouse, Performance panel). Lab numbers on a fast laptop mislead.
2. Find the metric that fails for the page/segment that matters.
3. Change one thing, re-measure, record the result.
4. Add a **budget** to CI so it does not regress.

## LCP

| Cause | Fix |
|---|---|
| Slow server/TTFB | cache at CDN, SSG/ISR, reduce redirects |
| Late discovery of hero image | `<img fetchpriority="high">`, preload, no lazy-load on LCP image |
| Large images | AVIF/WebP, `srcset`/`sizes`, correct dimensions |
| Render-blocking CSS/JS | inline critical CSS, defer scripts, split bundles |
| Client-side fetch waterfall | move data to server/loader |

## INP

- Break up long tasks (>50 ms): `scheduler.yield()` / chunking.
- Reduce hydration work and re-render scope: memoise expensive subtrees, colocate state, avoid context values that change on every render.
- Debounce or defer non-urgent updates (`useDeferredValue`, `startTransition`).
- Virtualise long lists.

## CLS

- Reserve space (`width`/`height` or `aspect-ratio`) for images, embeds, ads.
- Skeletons the same size as final content.
- `font-display` strategy plus metric-matched fallback fonts.

## Bundle hygiene

Route-level code splitting, analyse with a bundle visualiser, avoid whole-library imports, set per-route budgets.

## Status

This is a playbook. A measured before/after performance project is on the portfolio roadmap; no numbers are claimed here.
