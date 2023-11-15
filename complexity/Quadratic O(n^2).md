---
tags:
  - quadratic
---
Grows faster than linear-logarithmic complexity and slower than exponential one.

```typescript
function combinations(arr1: number[], arr2: number[]) {
	const result = [];

	for (let i = 0; i < arr1.length; i++) {
		for (let j = 0; j < arr2.length; j++) {
			result.push([arr1[i], arr2[j]]);
		}
	}
	
	return result;
}
```

Nested loops is a classic example of quadratic complexity.