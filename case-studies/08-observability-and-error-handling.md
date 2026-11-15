# 08 · Frontend observability and error handling

## What to capture

1. **Errors:** uncaught exceptions, unhandled rejections, React render errors (error boundaries), failed network calls, schema/contract violations.
2. **Performance (RUM):** Core Web Vitals with page, device and connection dimensions.
3. **Behavioural breadcrumbs:** route changes, key actions, last N API calls, to make an error reproducible.
4. **Release tagging:** attach the build version/commit; upload source maps privately.

## Error taxonomy (drives UI and alerting)

| Class | Example | User sees | Reported? |
|---|---|---|---|
| Expected, user-fixable | 422 validation | inline field error | no |
| Permission | 403 | "no access" state | no (maybe metric) |
| Transient | network, 5xx | retry affordance | sample |
| Contract | response fails schema | generic error | **yes, high priority** |
| Programming | render exception | boundary fallback | **yes** |

## Layers of defence

Error boundaries per route (a broken page should not take down the shell), query-level `onError`, a global `unhandledrejection` handler, and a single `reportError()` seam so the vendor (Sentry, Datadog) is swappable.

## Alerting

Alert on error-rate regression per release and on Web Vitals p75 regressions, not on individual exceptions. Scrub PII from breadcrumbs and URLs.

## Example

`enterprise-react-app/src/shared/lib/observability.ts` is the reporter seam; `ErrorBoundary` and the global rejection handler both route through it.
