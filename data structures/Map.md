In comparison with arrays, has an associated key for each value.  Simplified JavaScript [Map](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map) implementation.

```typescript
class Map<T extends (string | number), V> {

	private length: number;
	private data: { [key in T]?: V };
	
	constructor() {
		this.length = 0;
		this.data = {};
	}

	get(key: T): V | undefined {
		return this.data[key];
	}
	
	set(key: T, value: V): void {
		this.data[key] = value;
		this.length++;
	}

	has(key: T): boolean {
		return this.data.hasOwnProperty(key);
	}
	
	delete(key: T): V | undefined {
		const v = this.data[key];
		if (this.data.hasOwnProperty(key)) {
			this.length--;
			delete this.data[key];
		}
		return v;
	}
	
	size(): number {
		return this.length;
	}
}
```

##### Methods complexity
- get - [[Constant O(1)|O(1)]]
- set - [[Constant O(1)|O(1)]]
- has - [[Constant O(1)|O(1)]]
- delete - [[Constant O(1)|O(1)]]
- size - [[Constant O(1)|O(1)]]