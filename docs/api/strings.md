# strings

String manipulation utilities.

```typescript
import { strings } from '@cl3m/corekit';
// or
import { capitalize, slugify, ... } from '@cl3m/corekit/strings';
```

---

## capitalize

```typescript
capitalize(str: string): string
```

Capitalize the first letter of a string.

```typescript
capitalize('hello world')  // "Hello world"
capitalize('')             // ""
```

---

## toCamelCase

```typescript
toCamelCase(str: string): string
```

Convert a string to camelCase. Handles hyphens, underscores, and spaces.

```typescript
toCamelCase('hello-world')   // "helloWorld"
toCamelCase('foo_bar_baz')   // "fooBarBaz"
toCamelCase('hello world')   // "helloWorld"
```

---

## toKebabCase

```typescript
toKebabCase(str: string): string
```

Convert a string to kebab-case.

```typescript
toKebabCase('helloWorld')  // "hello-world"
toKebabCase('foo_bar')     // "foo-bar"
```

---

## toSnakeCase

```typescript
toSnakeCase(str: string): string
```

Convert a string to snake_case.

```typescript
toSnakeCase('helloWorld')   // "hello_world"
toSnakeCase('hello-world')  // "hello_world"
```

---

## truncate

```typescript
truncate(str: string, maxLength: number, ellipsis?: string): string
```

Truncate a string to a max length, appending an ellipsis if needed. Default ellipsis is `"..."`.

```typescript
truncate('Hello, world!', 8)         // "Hello..."
truncate('Hi', 8)                    // "Hi"
truncate('Long text here', 7, '…')  // "Long t…"
```

---

## slugify

```typescript
slugify(str: string): string
```

Convert a string to a URL-safe slug. Normalizes unicode and removes special characters.

```typescript
slugify('Hello World!')   // "hello-world"
slugify('Héllo Wörld')   // "hello-world"
slugify('  Foo  Bar  ')  // "foo-bar"
```

---

## countOccurrences

```typescript
countOccurrences(str: string, sub: string): number
```

Count non-overlapping occurrences of a substring within a string.

```typescript
countOccurrences('banana', 'an')  // 2
countOccurrences('hello', '')     // 0
```

---

## centerPad

```typescript
centerPad(str: string, width: number, char?: string): string
```

Pad a string on both sides to center it within a given width. Default pad character is `" "`.

```typescript
centerPad('hi', 8)       // "   hi   "
centerPad('hi', 8, '-')  // "---hi---"
```

---

## isEmail

```typescript
isEmail(str: string): boolean
```

Check if a string is a valid email address format.

```typescript
isEmail('user@example.com')  // true
isEmail('not-an-email')      // false
```

---

## stripWhitespace

```typescript
stripWhitespace(str: string): string
```

Remove all whitespace characters from a string.

```typescript
stripWhitespace('hello world')  // "helloworld"
stripWhitespace('  h e l  ')   // "hel"
```

---

## reverseString

```typescript
reverseString(str: string): string
```

Reverse a string. Unicode-safe — handles emoji and multi-byte characters correctly.

```typescript
reverseString('hello')    // "olleh"
reverseString('racecar')  // "racecar"
```

---

## Function reference

| Function | Signature | Returns |
|----------|-----------|---------|
| `capitalize` | `(str: string)` | `string` |
| `toCamelCase` | `(str: string)` | `string` |
| `toKebabCase` | `(str: string)` | `string` |
| `toSnakeCase` | `(str: string)` | `string` |
| `truncate` | `(str, maxLength, ellipsis?)` | `string` |
| `slugify` | `(str: string)` | `string` |
| `countOccurrences` | `(str, sub)` | `number` |
| `centerPad` | `(str, width, char?)` | `string` |
| `isEmail` | `(str: string)` | `boolean` |
| `stripWhitespace` | `(str: string)` | `string` |
| `reverseString` | `(str: string)` | `string` |
