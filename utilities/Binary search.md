---
tags:
  - logarithmic
---
Relatively fast way of finding position of a value in a sorted array. Returns '-1' if the searched value doesn't exist in array.

```typescript
function binarySearch(haystack: number[], needle: number) {
	let start = 0;
	let end = haystack.length;

	while (start < end) {
		const mid = Math.floor((start + end) / 2);
		if (haystack[mid] === needle) return mid;
		if (haystack[mid] > needle) end = mid;
		else start = mid + 1;
	}
	return -1;
}
```