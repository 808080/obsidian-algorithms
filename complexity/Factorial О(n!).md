---
tags:
  - factorial
  - recursion
---
The fastest growing complexity.

```typescript
function permutations(arr: any[], perm: any[] = [], result: any[][] = []) {
	if (arr.length === 0) {
		result.push(perm);
	} else {
		for (let i = 0; i < arr.length; i++) {
			const copy = arr.slice();
			const elem = copy.splice(i, 1);
			permutations(copy, perm.concat(elem), result);
		}
	}
	
	return result;
}
```