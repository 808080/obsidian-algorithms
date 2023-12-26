Data structure that associates a key-value pair with a hash. 

```javascript
class HashTable {
	constructor(size) {
		if (!size || size < 0) {
			throw new Error('Size cannot be negative');
		}
		
		this.size = size;
		this.memory = new Array();
	}
	
	set(key, value) {
		const hash = this.getHash(key);
		
		if (!this.memory[hash]) {
			this.memory[hash] = new Array();
			this.memory[hash].push([key, value]);
			return;
		}
		
		const pair = this.getPair(key);

		if (pair) {
			pair[1] = value;
		} else {
			this.memory[hash].push([key, value]);
		}
	}
	
	get(key) {
		const hash = this.getHash(key);
	
		if (!this.memory[hash]) {
			return undefined;
		}
	
		const pair = this.getPair(key);
		return pair && pair[1];
	}
	
	remove(key) {
		const hash = this.getHash(key);

		if (!this.memory[hash]) {
			return;
		}
		
		const valIndex = this.memory[hash].findIndex((item) => item[0] === key);
		
		if (valIndex === -1) {
			return;
		}

		this.memory[hash].splice(valIndex, 1);

		if (!this.memory[hash].length) {
			delete this.memory[hash];
		}
	}
	
	getHash(key) {
		return hash(key, this.size);
	}
	
	getPair(key) {
		return this.memory[this.getHash(key)].find((item) => item[0] === key);
	}
}


function hash(key, size) {
	const MAX_LENGTH = 200;
	const start = key.length > MAX_LENGTH ?
		Math.floor((key.length % MAX_LENGTH) / 2) : 0;
	const end = Math.min(key.length, MAX_LENGTH);

	let total = 0;

	for (let i = 0; i < end; i++) {
		const charCode = key.charCodeAt(start + i);
		total = (total + charCode * (i + 1)) % size;
	}
	
	return total;
}
```

##### Methods complexity
- set - [[Linear О(n)|O(n)]], Θ(1)
- get - [[Linear О(n)|O(n)]], Θ(1)
- remove - [[Linear О(n)|O(n)]], Θ(1)
- getHash - [[Linear О(n)|O(n)]], Θ(1)
- getPair - [[Linear О(n)|O(n)]], Θ(1)

#constant #linear 