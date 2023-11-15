---
tags:
  - linear
  - fibonacci
  - dp
---
Complexity grows proportionally with input.

##### Examples:
1. Looks for the smallest and the biggest number in an array.
```typescript
function minMax(numbers: number[]) {
	let min = numbers[0];
	let max = numbers[0];
	
	for (let i = 1; i < numbers.length; i++) {
		const n = numbers[i];
		if (n < min) min = n;
		if (n > max) max = n;
	}
	return { min, max };
}
```
Cycles are considered to have linear time complexity.

2. Calculating Fibonacci with dynamic programming approach
```typescript
function fibonacciDP(n: number) {
	if (n <= 1) return n;

	const fibArray = new Array<number>(n + 1);
	fibArray[0] = 0;
	fibArray[1] = 1;
	for (let i = 2; i <= n; i++) {
		fibArray[i] = fibArray[i - 1] + fibArray[i - 2];
	}
	return fibArray[n];
}
```

^ee19cc

3. Linear search. Simple but slower than [[Binary search]]
```typescript
function linearSearch(haystack: number[], needle: number) {
	for (let i = 0; i < haystack.length; i++) {
		if(needle === haystack[i]) return true;
	}
	return false;
}
```