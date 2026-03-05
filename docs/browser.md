# Browser Support

All core modules (`strings`, `arrays`, `objects`, `dates`) are fully browser-compatible. The CLI is Node.js only.

---

## CDN — Script tag (no bundler)

The simplest way to use corekit in a browser. Exposes a global `corekit` object:

```html
<script src="https://cdn.jsdelivr.net/npm/@cl3m/corekit/dist/browser.global.js"></script>
<script>
  console.log(corekit.strings.slugify('Hello World!'));      // "hello-world"
  console.log(corekit.arrays.chunk([1,2,3,4,5], 2));        // [[1,2],[3,4],[5]]
  console.log(corekit.dates.timeAgo(new Date('2024-01-01'))); // "14 months ago"
</script>
```

---

## ESM — Modern browser (no bundler)

Use native ES module imports directly in the browser:

```html
<script type="module">
  import { strings, arrays } from
    'https://cdn.jsdelivr.net/npm/@cl3m/corekit/dist/browser.esm.js';

  console.log(strings.toCamelCase('hello-world')); // "helloWorld"
  console.log(arrays.range(1, 5));                 // [1, 2, 3, 4, 5]
</script>
```

---

## Bundler — Vite, Webpack, Rollup

Use the dedicated browser subpath for bundler builds. This excludes all Node.js-specific code:

```typescript
import { strings, arrays, objects, dates } from '@cl3m/corekit/browser';
```

!!! tip "Prefer subpath imports for tree-shaking"
    If you only need one module, import it directly to keep your bundle smaller:
    ```typescript
    import { slugify } from '@cl3m/corekit/strings';
    ```

---

## Compatibility

| Browser | Minimum version |
|---------|-----------------|
| Chrome | 67+ |
| Firefox | 60+ |
| Safari | 11+ |
| Edge | 18+ |
| Node.js | 18+ |

The browser build targets **ES2017**, which covers all modern browsers without requiring polyfills.

---

## What's excluded from browser builds

| Feature | Available in browser? |
|---------|----------------------|
| `strings` module | ✅ Yes |
| `arrays` module | ✅ Yes |
| `objects` module | ✅ Yes |
| `dates` module | ✅ Yes |
| `cli` | ❌ Node.js only |
