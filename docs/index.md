# @cl3m/corekit

<div style="margin: 1.5rem 0 2rem">
  <span class="badge badge-blue">TypeScript-first</span>&nbsp;
  <span class="badge badge-green">Zero dependencies</span>&nbsp;
  <span class="badge badge-purple">ESM + CJS</span>&nbsp;
  <span class="badge badge-yellow">Browser + Node</span>
</div>

**corekit** is a general-purpose utility library for JavaScript and TypeScript projects. It covers the four domains you reach for in almost every project — strings, arrays, objects, and dates — with a clean, consistent API and zero runtime dependencies.

```bash
npm install @cl3m/corekit
```

---

## Quick example

```typescript
import { strings, arrays, objects, dates } from '@cl3m/corekit';

strings.slugify('Hello World!');            // "hello-world"
strings.toCamelCase('hello-world');         // "helloWorld"

arrays.chunk([1, 2, 3, 4, 5], 2);          // [[1,2],[3,4],[5]]
arrays.groupBy(users, u => u.role);        // { admin: [...], user: [...] }

objects.pick({ a:1, b:2, c:3 }, ['a','c']); // { a:1, c:3 }
objects.deepMerge(defaults, overrides);     // deep merged object

dates.timeAgo(new Date('2024-01-01'));      // "14 months ago"
dates.formatDate(new Date(), 'YYYY-MM-DD'); // "2026-03-05"
```

---

## Modules

| Module | Description | Functions |
|--------|-------------|-----------|
| [`strings`](api/strings.md) | String manipulation utilities | 11 |
| [`arrays`](api/arrays.md) | Array transformation utilities | 11 |
| [`objects`](api/objects.md) | Object inspection & manipulation | 9 |
| [`dates`](api/dates.md) | Date formatting & arithmetic | 8 |

---

## Why corekit?

- **TypeScript-first** — every function is fully typed with generics where applicable
- **Zero dependencies** — no transitive bloat, ever
- **Dual output** — ships both ESM and CJS, with subpath exports for tree-shaking
- **Browser ready** — core modules work in any modern browser via CDN or bundler
- **CLI included** — run utilities directly from your terminal with `npx @cl3m/corekit`

---

## Installation

=== "npm"
    ```bash
    npm install @cl3m/corekit
    ```

=== "yarn"
    ```bash
    yarn add @cl3m/corekit
    ```

=== "pnpm"
    ```bash
    pnpm add @cl3m/corekit
    ```

=== "CDN"
    ```html
    <script src="https://cdn.jsdelivr.net/npm/@cl3m/corekit/dist/browser.global.js"></script>
    ```

---

## License

MIT © Clement
