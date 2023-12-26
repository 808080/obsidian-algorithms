Similar to [[Array|array]] but without predefined length. Therefore it can have various insertion and removal methods.

```typescript
class ArrayList<T> {
	public length: number;
	private memory: Record<number, T | undefined>;
	private capacity: number;
	

	constructor(capacity: number) {
		this.length = 0;
		this.capacity = capacity;
		this.memory = allocate<T>(capacity);
	}

	prepend(item: T): void {
		for (let i = this.length; i > 0; i--) {
			this.memory[i] = this.memory[i - 1];
		}

		this.memory[0] = item;
		this.length++;

		if (this.capacity === this.length) this.resize();
	}
	
	insertAt(item: T, idx: number): void {
		if (idx >= this.length) throw new Error('Out of length');

		const temp = Object.assign({}, this.memory);
		this.memory[idx] = item;
		for (let i = idx + 1; i <= this.length; i++) {
			this.memory[i] = temp[i - 1];
		}

		this.length++;

		if (this.capacity === this.length) this.resize();
	}
	
	append(item: T): void {
		this.memory[this.length] = item;
		this.length++;

		if (this.capacity === this.length) this.resize();
	}
	
	remove(item: T): T | undefined {
		let temp: T | undefined;
		for (let i = 0; i < this.length; i++) {
			if (this.memory[i] === item) {
				temp = this.memory[i];
		
				for (; i < this.length; i++) {
					this.memory[i] = this.memory[i + 1];
				}
				
				this.length--;
				this.memory[this.length] = undefined;
			}
		}
		
		return temp;
	}
	
	get(idx: number): T | undefined {
		if (idx >= this.length) throw new Error('Out of length');
		return this.memory[idx];
	}
	
	removeAt(idx: number): T | undefined {
		if (idx >= this.length) throw new Error('Out of length');

		let temp: T | undefined;
		for (let i = 0; i < this.length; i++) {
			if (i === idx) {
				temp = this.memory[i];

				for (; i < this.length; i++) {
					this.memory[i] = this.memory[i + 1];
				}
				
				this.length--;
				this.memory[this.length] = undefined;
			}
		}
		
		return temp;
	}
	
	private resize() {
		const newSize = this.capacity * 2;
		const newMemory = allocate<T>(newSize);

		for (let i = 0; i < this.capacity; i++) {
			newMemory[i] = this.memory[i];
		}

		this.capacity = newSize;
		this.memory = newMemory;
	}
}
```

##### Methods complexity
- prepend - [[Linear О(n)|O(n)]]
- insertAt - [[Linear О(n)|O(n)]]
- append - [[Constant O(1)|O(1)]]
- remove - [[Linear О(n)|O(n)]]
- get - [[Constant O(1)|O(1)]]
- removeAt - [[Linear О(n)|O(n)]]