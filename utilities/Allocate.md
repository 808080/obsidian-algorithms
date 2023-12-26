Provides additional memory for a data structure.

```typescript
function allocate<T>(size: number) {
	const memory: Record<number, T | undefined> = {};
	
	for (let i = 0; i < size; i++) {
		memory[i] = undefined;
	}
	
	return memory;
}
```