# Documentation of Quick Sort

## Quick Sort Algorithm

### Code Implementation

```javascript
function swap(array, firstIndex, secondIndex) {
    let temp = array[firstIndex];
    array[firstIndex] = array[secondIndex];
    array[secondIndex] = temp;
}

function pivot(array, pivotIndex = 0, endIndex = array.length - 1) {
    let swapIndex = pivotIndex;

    for(let i = pivotIndex + 1; i <= endIndex; i++) {
        if(array[i] < array[pivotIndex]) {
            swapIndex++;
            swap(array, swapIndex, i);
        }
    }

    swap(array, pivotIndex, swapIndex);
    return swapIndex;
}

function quickSort(array, left = 0, right = array.length - 1) {
    let pivotIndex = pivot(array, left, right);
    if(left < right) {
        quickSort(array, left, pivotIndex - 1);
        quickSort(array, pivotIndex + 1, right);
    }
    return array;
}

let array = [4, 6, 1, 7, 3, 2, 5];
quickSort(array);
```

### Explanation

- **Swap function**: Swaps two elements in the array.
- **Pivot function**: Selects a pivot, places it in its correct position, and ensures elements smaller than the pivot are to the left, and larger elements are to the right.
- **QuickSort function**: Recursively sorts the array by partitioning it around a pivot.

### Time Complexity

- **Average case**: `O(n log n)`. On average, the algorithm iterates through `n` items and performs `log n` partitioning steps.
- **Worst case**: `O(n^2)`. If the array is already sorted or nearly sorted, each partition creates one large subarray, leading to quadratic time complexity.

### Space Complexity

- **Space complexity**: `O(1)` since the algorithm manipulates the array in place without needing additional space (apart from recursive stack calls).