# CLI

corekit ships with a built-in CLI so you can run utility functions directly from your terminal.

## Installation

=== "Global"
    ```bash
    npm install -g @cl3m/corekit
    corekit --help
    ```

=== "npx (no install)"
    ```bash
    npx @cl3m/corekit --help
    ```

---

## String commands

### `capitalize`
```bash
corekit capitalize "hello world"
# Hello world
```

### `slugify`
```bash
corekit slugify "Hello World! Foo"
# hello-world-foo
```

### `camel`
```bash
corekit camel "hello-world"
# helloWorld
```

### `kebab`
```bash
corekit kebab "helloWorldFoo"
# hello-world-foo
```

---

## Array commands

### `chunk`
```bash
corekit chunk 3 a b c d e f
# [["a","b","c"],["d","e","f"]]
```

### `unique`
```bash
corekit unique a b a c b d
# ["a","b","c","d"]
```

### `range`
```bash
corekit range 1 10
# [1,2,3,4,5,6,7,8,9,10]

corekit range 0 20 5
# [0,5,10,15,20]
```

---

## Date commands

### `format`
```bash
corekit format 2024-03-15 YYYY/MM/DD
# 2024/03/15

corekit format 2024-03-15 DD-MM-YYYY
# 15-03-2024
```

### `timeago`
```bash
corekit timeago 2024-01-01
# 14 months ago

corekit timeago 2030-01-01
# in 3 years
```

---

## All commands

| Command | Args | Description |
|---------|------|-------------|
| `capitalize` | `<text>` | Capitalize first letter |
| `slugify` | `<text>` | Convert to URL slug |
| `camel` | `<text>` | Convert to camelCase |
| `kebab` | `<text>` | Convert to kebab-case |
| `chunk` | `<size> <items...>` | Chunk items into groups |
| `unique` | `<items...>` | Remove duplicates |
| `range` | `<start> <end> [step]` | Generate number range |
| `format` | `<date> <template>` | Format a date |
| `timeago` | `<date>` | Get relative time string |
