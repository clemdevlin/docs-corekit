# dates

Date formatting, arithmetic, and comparison utilities.

```typescript
import { dates } from '@cl3m/corekit';
// or
import { formatDate, timeAgo, ... } from '@cl3m/corekit/dates';
```

---

## formatDate

```typescript
formatDate(date: Date, template: string): string
```

Format a `Date` using a template string. Supported tokens:

| Token | Value | Example |
|-------|-------|---------|
| `YYYY` | 4-digit year | `2024` |
| `MM` | 2-digit month | `03` |
| `DD` | 2-digit day | `05` |
| `HH` | 2-digit hours (24h) | `14` |
| `mm` | 2-digit minutes | `30` |
| `ss` | 2-digit seconds | `00` |

```typescript
const d = new Date('2024-03-15T09:05:00');
formatDate(d, 'YYYY-MM-DD')  // "2024-03-15"
formatDate(d, 'DD/MM/YYYY')  // "15/03/2024"
formatDate(d, 'HH:mm:ss')    // "09:05:00"
```

---

## addToDate

```typescript
addToDate(date: Date, amount: number, unit: 'days' | 'months' | 'years'): Date
```

Add a duration to a date. Returns a **new Date** — does not mutate the original.

```typescript
const d = new Date('2024-01-15');
addToDate(d, 10, 'days')    // 2024-01-25
addToDate(d, 2, 'months')   // 2024-03-15
addToDate(d, 1, 'years')    // 2025-01-15
```

---

## diffDates

```typescript
diffDates(
  a: Date,
  b: Date,
  unit: 'milliseconds' | 'seconds' | 'minutes' | 'hours' | 'days'
): number
```

Get the difference between two dates in the specified unit. The result is `b - a`, and can be negative if `b` is before `a`.

```typescript
const a = new Date('2024-01-01');
const b = new Date('2024-01-11');
diffDates(a, b, 'days')   // 10
diffDates(a, b, 'hours')  // 240
diffDates(b, a, 'days')   // -10
```

---

## timeAgo

```typescript
timeAgo(date: Date, now?: Date): string
```

Return a human-readable relative time string. Handles both past and future dates. The optional `now` parameter defaults to the current time.

```typescript
timeAgo(new Date(Date.now() - 30_000))    // "just now"
timeAgo(new Date(Date.now() - 3_600_000)) // "1 hour ago"
timeAgo(new Date('2024-01-01'))           // "14 months ago"
timeAgo(new Date(Date.now() + 86_400_000)) // "in 1 day"
timeAgo(new Date('2030-01-01'))            // "in 3 years"
```

---

## isBetween

```typescript
isBetween(date: Date, start: Date, end: Date): boolean
```

Check if a date falls within a range (inclusive of both endpoints).

```typescript
isBetween(
  new Date('2024-06-15'),
  new Date('2024-01-01'),
  new Date('2024-12-31')
)
// true
```

---

## isSameDay

```typescript
isSameDay(a: Date, b: Date): boolean
```

Check if two dates fall on the same calendar day, regardless of time.

```typescript
isSameDay(new Date('2024-03-15'), new Date('2024-03-15'))  // true
isSameDay(new Date('2024-03-15'), new Date('2024-03-16'))  // false
```

---

## startOf

```typescript
startOf(date: Date, unit: 'day' | 'month' | 'year'): Date
```

Get the start of a day, month, or year for a given date. Returns a new Date with time set to `00:00:00.000`.

```typescript
const d = new Date('2024-03-15T14:30:00');
startOf(d, 'day')    // 2024-03-15 00:00:00
startOf(d, 'month')  // 2024-03-01 00:00:00
startOf(d, 'year')   // 2024-01-01 00:00:00
```

---

## isValidDate

```typescript
isValidDate(val: unknown): val is Date
```

Type guard that returns `true` if the value is a `Date` instance with a valid (non-NaN) time.

```typescript
isValidDate(new Date())            // true
isValidDate(new Date('invalid'))   // false
isValidDate('2024-01-01')         // false
isValidDate(null)                  // false
```

---

## Function reference

| Function | Signature | Returns |
|----------|-----------|---------|
| `formatDate` | `(date, template)` | `string` |
| `addToDate` | `(date, amount, unit)` | `Date` |
| `diffDates` | `(a, b, unit)` | `number` |
| `timeAgo` | `(date, now?)` | `string` |
| `isBetween` | `(date, start, end)` | `boolean` |
| `isSameDay` | `(a, b)` | `boolean` |
| `startOf` | `(date, unit)` | `Date` |
| `isValidDate` | `(val: unknown)` | `val is Date` |
