A fixed-sized data structure. Requires predefined length which cannot be changed. 

```typescript
class Array<T> {
	private memory: Record<number, T | undefined>;
	private capacity: number;


	constructor(capacity: number) {
		this.capacity = capacity;
		this.memory = allocate<T>(capacity);
	}

	set(item: T, idx: number): void {
		if (idx >= this.capacity) throw new Error('Out of length');
		this.memory[idx] = item;
	}
	
	get(idx: number): T | undefined {
		if (idx >= this.capacity) throw new Error('Out of length');
		return this.memory[idx];
	}

	remove(idx: number): T | undefined {
		if (idx >= this.capacity) throw new Error('Out of length');
		
		const temp = this.memory[idx];
		this.memory[idx] = undefined;

		return temp;
	}

	size() {
		return this.capacity;
	}
}
```

##### Methods complexity
- set - [[Constant O(1)|O(1)]]
- get - [[Constant O(1)|O(1)]]
- remove - [[Constant O(1)|O(1)]]
- size - [[Constant O(1)|O(1)]]