# arrays

Array transformation and query utilities.

```typescript
import { arrays } from '@cl3m/corekit';
// or
import { chunk, groupBy, ... } from '@cl3m/corekit/arrays';
```

---

## unique

```typescript
unique<T>(arr: T[]): T[]
```

Remove duplicate values from an array. Uses `Set` internally — preserves insertion order.

```typescript
unique([1, 2, 2, 3, 3])          // [1, 2, 3]
unique(['a', 'b', 'a', 'c'])     // ["a", "b", "c"]
```

---

## chunk

```typescript
chunk<T>(arr: T[], size: number): T[][]
```

Split an array into chunks of a given size. The last chunk may be smaller than `size`.

!!! note
    Throws a `RangeError` if `size <= 0`.

```typescript
chunk([1, 2, 3, 4, 5], 2)  // [[1,2],[3,4],[5]]
chunk([1, 2, 3], 3)         // [[1,2,3]]
```

---

## flatten

```typescript
flatten<T>(arr: (T | T[])[], deep?: boolean): T[]
```

Flatten a nested array by one level. Pass `deep: true` to flatten all levels.

```typescript
flatten([[1, 2], [3, [4]]])        // [1, 2, 3, [4]]
flatten([[1, 2], [3, [4]]], true)  // [1, 2, 3, 4]
```

---

## intersection

```typescript
intersection<T>(a: T[], b: T[]): T[]
```

Return elements that appear in both arrays.

```typescript
intersection([1, 2, 3], [2, 3, 4])  // [2, 3]
```

---

## difference

```typescript
difference<T>(a: T[], b: T[]): T[]
```

Return elements in `a` that are not in `b`.

```typescript
difference([1, 2, 3], [2, 3, 4])  // [1]
```

---

## shuffle

```typescript
shuffle<T>(arr: T[]): T[]
```

Shuffle an array using the Fisher-Yates algorithm. Returns a **new array** — does not mutate the original.

```typescript
shuffle([1, 2, 3, 4, 5])  // [3, 1, 5, 2, 4] (random order)
```

---

## groupBy

```typescript
groupBy<T>(arr: T[], keyFn: (item: T) => string): Record<string, T[]>
```

Group array elements into an object keyed by the return value of `keyFn`.

```typescript
const users = [
  { name: 'Alice', role: 'admin' },
  { name: 'Bob',   role: 'user'  },
  { name: 'Carol', role: 'admin' },
];

groupBy(users, u => u.role);
// {
//   admin: [{ name: 'Alice', ... }, { name: 'Carol', ... }],
//   user:  [{ name: 'Bob', ... }]
// }
```

---

## sum

```typescript
sum(arr: number[]): number
```

Sum all numbers in an array. Returns `0` for an empty array.

```typescript
sum([1, 2, 3, 4])  // 10
sum([])            // 0
```

---

## minMax

```typescript
minMax(arr: number[]): { min: number; max: number }
```

Get the minimum and maximum values of a numeric array in a single pass.

!!! note
    Throws an `Error` if the array is empty.

```typescript
minMax([3, 1, 4, 1, 5, 9])  // { min: 1, max: 9 }
```

---

## sample

```typescript
sample<T>(arr: T[]): T
```

Pick a random element from an array.

!!! note
    Throws an `Error` if the array is empty.

```typescript
sample([1, 2, 3, 4, 5])  // 3 (random)
```

---

## range

```typescript
range(start: number, end: number, step?: number): number[]
```

Generate an array of numbers from `start` to `end` (inclusive), with an optional `step`. Default step is `1`.

```typescript
range(1, 5)      // [1, 2, 3, 4, 5]
range(0, 10, 2)  // [0, 2, 4, 6, 8, 10]
```

---

## Function reference

| Function | Signature | Returns |
|----------|-----------|---------|
| `unique` | `<T>(arr: T[])` | `T[]` |
| `chunk` | `<T>(arr: T[], size: number)` | `T[][]` |
| `flatten` | `<T>(arr, deep?)` | `T[]` |
| `intersection` | `<T>(a: T[], b: T[])` | `T[]` |
| `difference` | `<T>(a: T[], b: T[])` | `T[]` |
| `shuffle` | `<T>(arr: T[])` | `T[]` |
| `groupBy` | `<T>(arr, keyFn)` | `Record<string, T[]>` |
| `sum` | `(arr: number[])` | `number` |
| `minMax` | `(arr: number[])` | `{ min, max }` |
| `sample` | `<T>(arr: T[])` | `T` |
| `range` | `(start, end, step?)` | `number[]` |
