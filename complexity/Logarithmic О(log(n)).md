---
tags:
  - logarithmic
  - binary-search
---
Complexity grows in logarithmic progression. The amount of data to process decreases in multiple times with each iteration.

##### Example:
[[Binary search]]. Number of cases to check decreases in half with each iteration.
```typescript
function binarySearch(haystack: number[], needle: number) {
	let start = 0;
	let end = haystack.length;

	while (start < end) {
		const mid = Math.floor((start + end) / 2);
		if (haystack[mid] === needle) return true;
		if (haystack[mid] > needle) end = mid;
		else start = mid + 1;
	}
	return false;
}
```
