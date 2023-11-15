---
tags:
  - constant
  - fibonacci
---
Algorithm's complexity doesn't depend on input.

```typescript
function fibonacciBinet(n: number) {
	const phi = (1 + Math.sqrt(5)) / 2;
	const fibonacci = Math.round((Math.pow(phi, n) - Math.pow(-phi, -n)) / Math.sqrt(5));
	return fibonacci;
}
```

^817de1

Binet's formula calculates n-th Fibonacci number directly. Algebraic operations are performed with constant time.