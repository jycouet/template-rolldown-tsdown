# template-rolldown-tsdown

This demo project demonstrates how different bundlers (rolldown vs tsdown) handle template literals containing `</script>` tags when using tagged template literal syntax vs function call syntax.

## Setup

```bash
pnpm install
```

## Run the Demo

```bash
# Compare the outputs
pnpm test
```

## What You'll See

### in `1.0.0-beta.1` [dist-rolldown/index.js](dist-rolldown/index.js#L13)

```js
<script lang="ts">console.log('Hello');</script>
```

### in `1.0.0-beta.46` [dist-rolldown/index.js](dist-rolldown/index.js#L13)

```js
<script lang="ts">
	console.log('Hello');
<\/script>
```

### in [dist-tsdown/index.js](dist-tsdown/index.js#L12)

```js
<script lang="ts">
	console.log('Hello');
<\/script>
```

## Issue

The issue is that the `</script>` tag is being escaped to `<\/script>` in the source code with `tsdown`, but not with `rolldown`.
