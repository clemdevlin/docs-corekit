# Getting Started

## Installation

Install corekit from npm:

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

---

## Importing

corekit supports three import styles depending on your needs.

### Namespace import (recommended)

Import all four modules as namespaces:

```typescript
import { strings, arrays, objects, dates } from '@cl3m/corekit';

strings.capitalize('hello');   // "Hello"
arrays.unique([1, 1, 2, 3]);  // [1, 2, 3]
```

### Subpath imports (best for tree-shaking)

Import only the module you need. Bundlers will exclude unused code:

```typescript
import { slugify, toCamelCase } from '@cl3m/corekit/strings';
import { chunk, groupBy }       from '@cl3m/corekit/arrays';
import { pick, omit }           from '@cl3m/corekit/objects';
import { formatDate, timeAgo }  from '@cl3m/corekit/dates';
```

### CommonJS

```javascript
const { strings, arrays } = require('@cl3m/corekit');
// or
const { slugify } = require('@cl3m/corekit/strings');
```

---

## TypeScript

corekit is written in TypeScript and ships declaration files. No `@types` package needed.

```typescript
import { arrays } from '@cl3m/corekit';

// Fully typed — T is inferred
const result = arrays.chunk([1, 2, 3, 4, 5], 2);
//    ^? number[][]

const grouped = arrays.groupBy(
  [{ name: 'Alice', role: 'admin' }],
  u => u.role
);
// ^? Record<string, { name: string; role: string }[]>
```

!!! note "Minimum TypeScript version"
    corekit targets TypeScript `5.0+`. It uses modern features like `exactOptionalPropertyTypes` and `noUncheckedIndexedAccess`.

---

## Requirements

| Environment | Version |
|-------------|---------|
| Node.js | `>= 18.0.0` |
| TypeScript | `>= 5.0` (optional) |
| Browser | ES2017+ (Chrome 67+, Firefox 60+, Safari 11+) |

---

## Next steps

- Explore the [API Reference](api/strings.md) for all 39 functions
- Set up the [CLI](cli.md) for terminal usage
- Learn about [Browser Support](browser.md) for frontend projects
