# objects

Object inspection and manipulation utilities.

```typescript
import { objects } from '@cl3m/corekit';
// or
import { pick, omit, deepMerge, ... } from '@cl3m/corekit/objects';
```

---

## deepClone

```typescript
deepClone<T>(obj: T): T
```

Deep clone a plain object or array via JSON serialization. The clone is fully independent — mutations do not affect the original.

!!! warning "Limitations"
    Does not handle `Date` objects, functions, `undefined` values, or circular references. Use a dedicated library like `structuredClone` for those cases.

```typescript
const original = { a: { b: 1 } };
const clone = deepClone(original);
clone.a.b = 99;
original.a.b;  // 1 — unchanged
```

---

## deepMerge

```typescript
deepMerge<T extends Record<string, unknown>>(target: T, source: Partial<T>): T
```

Recursively merge `source` into `target`. Nested plain objects are merged; arrays and primitives from `source` replace those in `target`. Returns a new object — does not mutate `target`.

```typescript
deepMerge(
  { x: 1, y: { z: 2, w: 3 } },
  { y: { z: 99 } }
)
// { x: 1, y: { z: 99, w: 3 } }
```

---

## pick

```typescript
pick<T extends Record<string, unknown>, K extends keyof T>(obj: T, keys: K[]): Pick<T, K>
```

Create a new object containing only the specified keys. Fully type-safe — the return type reflects exactly which keys were picked.

```typescript
pick({ a: 1, b: 2, c: 3 }, ['a', 'c'])  // { a: 1, c: 3 }
```

---

## omit

```typescript
omit<T extends Record<string, unknown>, K extends keyof T>(obj: T, keys: K[]): Omit<T, K>
```

Create a new object excluding the specified keys. The complement of `pick`.

```typescript
omit({ a: 1, b: 2, c: 3 }, ['b'])  // { a: 1, c: 3 }
```

---

## flattenObject

```typescript
flattenObject(obj: Record<string, unknown>, prefix?: string): Record<string, unknown>
```

Flatten a deeply nested object using dot-notation keys.

```typescript
flattenObject({ a: { b: { c: 1 }, d: 2 } })
// { 'a.b.c': 1, 'a.d': 2 }
```

---

## isPlainObject

```typescript
isPlainObject(val: unknown): val is Record<string, unknown>
```

Type guard that returns `true` if the value is a plain object — not an array, not `null`, not a class instance.

```typescript
isPlainObject({})          // true
isPlainObject([])          // false
isPlainObject(null)        // false
isPlainObject(new Date())  // false
```

---

## isEmpty

```typescript
isEmpty(obj: Record<string, unknown>): boolean
```

Check if an object has no own enumerable keys.

```typescript
isEmpty({})        // true
isEmpty({ a: 1 }) // false
```

---

## invertObject

```typescript
invertObject(obj: Record<string, string>): Record<string, string>
```

Swap all keys and values of an object.

```typescript
invertObject({ a: '1', b: '2' })  // { '1': 'a', '2': 'b' }
```

---

## getByPath

```typescript
getByPath(obj: Record<string, unknown>, path: string): unknown
```

Safely retrieve a nested value using a dot-notation path string. Returns `undefined` if any segment of the path doesn't exist — never throws.

```typescript
getByPath({ a: { b: 42 } }, 'a.b')   // 42
getByPath({ a: {} }, 'a.b.c')        // undefined
```

---

## Function reference

| Function | Signature | Returns |
|----------|-----------|---------|
| `deepClone` | `<T>(obj: T)` | `T` |
| `deepMerge` | `<T>(target, source)` | `T` |
| `pick` | `<T, K>(obj, keys)` | `Pick<T, K>` |
| `omit` | `<T, K>(obj, keys)` | `Omit<T, K>` |
| `flattenObject` | `(obj, prefix?)` | `Record<string, unknown>` |
| `isPlainObject` | `(val: unknown)` | `val is Record<string, unknown>` |
| `isEmpty` | `(obj)` | `boolean` |
| `invertObject` | `(obj)` | `Record<string, string>` |
| `getByPath` | `(obj, path)` | `unknown` |
