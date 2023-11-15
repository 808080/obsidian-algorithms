---
tags:
  - exponential
  - recursion
  - fibonacci
---
Exponential complexity grows really fast but factorial complexity still grows faster.

```typescript
function fibonacci(n: number): number {
	if (n <= 1) return n;
	return fibonacci(n - 2) + fibonacci(n - 1);
}
```

In this example exponential growth is achieved with two recursive calls.  It's recommended to avoid exponential algorithms. Here are some alternatives to Fibonacci function ([[Constant O(1)#^817de1]], [[Linear О(n)#^ee19cc]]).