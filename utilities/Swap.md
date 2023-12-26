---
tags:
  - swap
---
Used to interchange values for certain array indices.

```typescript
function swap(arr: number[], i: number, j: number) {
	const tmp = arr[i];
	arr[i] = arr[j];
	arr[j] = tmp;
}
```