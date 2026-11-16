# frontend-architecture

[![CI](https://github.com/smrafi4130/frontend-architecture/actions/workflows/docs.yml/badge.svg)](https://github.com/smrafi4130/frontend-architecture/actions/workflows/docs.yml)

Case studies and decision records on designing, scaling and operating frontend systems.
Each document states the question, the options with their trade-offs, a decision rule, and, where it exists, a link to code that implements it.

> **Honest scope:** these are design analyses written from study and from building the reference projects below. They are not retrospectives of systems I operated at scale, and each study marks whether it is implemented in code or analysis only.

## Case studies

| # | Topic | Implemented in code? |
|---|---|---|
| [01](case-studies/01-large-scale-app-architecture.md) | Large-scale application architecture | Yes, `enterprise-react-app` |
| [02](case-studies/02-micro-frontends-vs-modular-monolith.md) | Micro-frontends vs modular monolith | Monolith side only |
| [03](case-studies/03-rendering-strategies.md) | CSR / SSR / SSG / ISR / streaming | CSR only |
| [04](case-studies/04-data-fetching-and-caching.md) | Data fetching and caching | Yes, `enterprise-react-app` |
| [05](case-studies/05-core-web-vitals-playbook.md) | Core Web Vitals playbook | Analysis only (perf lab on roadmap) |
| [06](case-studies/06-auth-and-frontend-security.md) | Authentication and frontend security | Partly, `enterprise-react-app` |
| [07](case-studies/07-real-time-architecture.md) | Real-time architecture | Analysis only |
| [08](case-studies/08-observability-and-error-handling.md) | Observability and error handling | Seam + boundaries, `enterprise-react-app` |

## Architecture decision records

Template: [adr/0000-template.md](adr/0000-template.md)

| ADR | Decision |
|---|---|
| [0001](adr/0001-modular-monolith-before-micro-frontends.md) | Modular monolith before micro-frontends |
| [0002](adr/0002-query-cache-for-server-state.md) | Query cache for server state |
| [0003](adr/0003-httponly-refresh-cookie-in-production.md) | httpOnly refresh cookie in production |
| [0004](adr/0004-tokens-as-source-of-truth-for-theming.md) | Two-tier design tokens |
| [0005](adr/0005-changesets-for-versioning.md) | Changesets for versioning |

## Companion repositories

- [`enterprise-react-app`](https://github.com/smrafi4130/enterprise-react-app): feature-based React/TypeScript app, RBAC, three test layers
- [`react-design-system`](https://github.com/smrafi4130/react-design-system): tokens + accessible primitives, Storybook, visual regression

## Contributing to these notes

Corrections welcome via issues. Docs are linted with markdownlint and links are checked in CI.

License: MIT
