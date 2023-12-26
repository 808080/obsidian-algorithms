Similar to [[Singly Linked list]] but additionally each node has a reference to its previous node.

```typescript
type Node<T> = {
	value: T,
	next: Node<T>,
	prev: Node<T>
} | null;


class DoublyLinkedList<T> {
	public length: number;
	private head: Node<T>;
	private tail: Node<T>;

	constructor() {
		this.length = 0;
		this.head = null;
		this.tail = null;
	}

	prepend(item: T): void {
		const newItem: Node<T> = {
			value: item,
			next: this.head,
			prev: null
		};

		this.head = newItem;
		if (!this.tail) this.tail = this.head;
		this.length++;
	}
	
	insertAt(item: T, idx: number): void {
		if (idx < 0) throw new Error('Index cannot be negative');
		if (idx > this.length) throw new Error('Index exceeds length');

		if (idx === 0) {
			this.prepend(item);
			return;
		}
	
		if (idx === this.length) {
			this.append(item);
			return;
		}
		
		const prevNode = this.getNodeAt(idx - 1)!;
		const newItem: Node<T> = {
			value: item,
			next: prevNode.next?.next || null,
			prev: prevNode
		};

		prevNode.next = newItem;
		this.length++;
	}
	
	append(item: T): void {
		const newItem: Node<T> = {
			value: item,
			next: null,
			prev: this.tail
		};
		
		if (!this.tail) {
			this.head = this.tail = newItem;
		} else {
			this.tail.next = newItem;
			this.tail = newItem;
		}
		this.length++;
	}
	
	remove(item: T): T | undefined {
		if (!this.head) return;
		
		let target: Node<T> = this.head;
		let prev: Node<T> = null;
		let found = false;

		while (target) {
			if (item === target.value) {
				found = true;
				break;
			}
		
			prev = target;
			target = target.next;
		}
		
		if (!found) return;

		if (target === this.head) {
			this.head = this.head.next;
		}
		
		if (target === this.tail) {
			this.tail = prev;
		}
		
		if (prev) prev.next = target!.next;
		this.length--;

		return target ? target.value : undefined;
	}
	
	get(idx: number): T | undefined {
		if (idx < 0) throw new Error('Index cannot be negative');
		if (idx > this.length - 1) throw new Error('Index exceeds length');
		return this.getNodeAt(idx)?.value;
	}
	
	removeAt(idx: number): T | undefined {
		if (idx < 0) throw new Error('Index cannot be negative');
		if (idx > this.length - 1) throw new Error('Index exceeds length');
		
		if (idx === 0) {
			const h = this.head;
			this.head = this.head!.next;
			this.length--;
			
			return h?.value;
		}

		const prevNode = this.getNodeAt(idx - 1)!;
		const target = prevNode.next!;

		prevNode.next = target.next;
		if (idx === this.length - 1) this.tail = prevNode;

		this.length--;
		return target.value;
	}

	getHead() {
		return this.head?.value;
	}

	getTail() {
		return this.tail?.value;
	}

	private getNodeAt(idx: number): Node<T> {
		let i = 0;
		let current = this.head;

		while (current) {
			if (idx === i) return current;
			current = current.next;
			i++;
		}
		
		return null;
	}
}
```

##### Methods complexity
- prepend - [[Constant O(1)|O(1)]]
- insertAt - [[Linear О(n)|O(n)]]
- append - [[Constant O(1)|O(1)]]
- remove - [[Linear О(n)|O(n)]]
- get - [[Linear О(n)|O(n)]]
- removeAt - [[Linear О(n)|O(n)]]
- getHead - [[Constant O(1)|O(1)]]
- getTail - [[Constant O(1)|O(1)]]