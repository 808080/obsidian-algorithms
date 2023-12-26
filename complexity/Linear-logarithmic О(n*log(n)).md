---
tags:
  - linear-logarithmic
  - merge-sort
  - recursion
  - swap
---
Grows faster than linear complexity but slower than quadratic one.

##### Examples:
1. Merge sort
```typescript
function mergeSort(arr: number[], start = 0, end = arr.length - 1, buffer: number[]) {
	if (end <= start) return arr;

	buffer = buffer || [...arr];

	const mid = Math.floor((start + end) / 2);

	mergeSort(arr, start, mid, buffer);
	mergeSort(arr, mid + 1, end, buffer);

	merge(arr, buffer, start, mid, end);

	return arr;
}

function merge(arr: number[], buffer: number[], start: number, mid: number, end: number) {
	for (let i = start; i <= end; i++) {
		buffer[i] = arr[i];
	}

	let l = start;
	let r = mid + 1;
	let i = start;

	while (l < mid + 1 && r < end + 1) {
		if (buffer[l] <= buffer[r]) {
			arr[i] = buffer[l];
			l++
		} else {
			arr[i] = buffer[r];
			r++
		}
		i++;
	}
	
	while (l < mid + 1) {
		arr[i] = buffer[l];
		l++;
		i++;
	}
	
	while (r < end + 1) {
		arr[i] = buffer[r];
		r++;
		i++;
	}
}
```

2. Quick sort
```typescript
function quickSort(arr: number[], start = 0, end = arr.length - 1) {
	if (end <= start) {
		return arr;
	}

	const pivotIndex = partition(arr, start, end);

	quickSort(arr, start, pivotIndex - 1);
	quickSort(arr, pivotIndex + 1, end);

	return arr;
}

function partition(arr: number[], start = 0, end = arr.length - 1) {
	const pivotValue = arr[end];

	let pivotIndex = start;

	for (let i = start; i < end; i++) {
		if (arr[i] <= pivotValue) {
			swap(arr, i, pivotIndex);
			pivotIndex++;
		}
	}
	
	swap(arr, pivotIndex, end);
	
	return pivotIndex;
}

function swap(arr: number[], i: number, j: number) {
	const tmp = arr[i];
	arr[i] = arr[j];
	arr[j] = tmp;
}
```

3. Javascript **Array.sort()** method also has O(n\*log(n)) complexity (used algorithm may vary depending on a browser).