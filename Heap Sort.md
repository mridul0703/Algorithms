# Heap Sort Algorithm

## Definition
Heap Sort is a comparison-based sorting technique based on Binary Heap data structure. It works by building a max heap and extracting the largest element repeatedly.

---

## Pseudocode
```plaintext
HeapSort(arr):
    BuildMaxHeap(arr)
    for i from n-1 to 1:
        swap(arr[0], arr[i])
        Heapify(arr, 0, i)

BuildMaxHeap(arr):
    for i from n/2 down to 0:
        Heapify(arr, i, n)

Heapify(arr, i, n):
    largest = i
    left = 2 * i + 1
    right = 2 * i + 2
    if left < n and arr[left] > arr[largest]:
        largest = left
    if right < n and arr[right] > arr[largest]:
        largest = right
    if largest != i:
        swap(arr[i], arr[largest])
        Heapify(arr, largest, n)
```

---

## C++ Implementation
```cpp
#include <iostream>
using namespace std;

void heapify(int arr[], int n, int i) {
    int largest = i;
    int left = 2 * i + 1;
    int right = 2 * i + 2;

    if (left < n && arr[left] > arr[largest])
        largest = left;

    if (right < n && arr[right] > arr[largest])
        largest = right;

    if (largest != i) {
        swap(arr[i], arr[largest]);
        heapify(arr, n, largest);
    }
}

void heapSort(int arr[], int n) {
    for (int i = n / 2 - 1; i >= 0; i--)
        heapify(arr, n, i);

    for (int i = n - 1; i > 0; i--) {
        swap(arr[0], arr[i]);
        heapify(arr, i, 0);
    }
}

void printArray(int arr[], int size) {
    for (int i = 0; i < size; i++)
        cout << arr[i] << " ";
    cout << endl;
}

int main() {
    int arr[] = {12, 11, 13, 5, 6, 7};
    int n = sizeof(arr) / sizeof(arr[0]);
    heapSort(arr, n);
    cout << "Sorted array: ";
    printArray(arr, n);
    return 0;
}
```

---

## Step-by-Step Explanation
### Given array:
```plaintext
arr[] = {12, 11, 13, 5, 6, 7}
```
1. Build max heap from input array.
2. Extract maximum element and place it at the end.
3. Heapify the remaining heap.
4. Repeat until the array is sorted.

Final sorted array: `{5, 6, 7, 11, 12, 13}`

---

## Time and Space Complexity
| Case       | Time Complexity |
|------------|----------------|
| Best Case  | O(n log n) |
| Worst Case | O(n log n) |
| Average Case | O(n log n) |
| Space Complexity | O(1) |

---

## Applications and Uses
1. **Priority Queues** - Heap Sort is useful in applications requiring priority-based operations.
2. **Graph Algorithms** - Used in Dijkstra’s and Prim’s algorithms.
3. **Real-Time Processing** - Used where consistent O(n log n) performance is required.
4. **Operating Systems** - Used for scheduling processes.

---

## Specific Problems Where Heap Sort is Useful
1. **Finding the k-th Largest/Smallest Element** - Efficient in problems like "Kth Largest Element in an Array" (LeetCode 215).
2. **Sorting Almost Sorted Arrays** - Ideal for problems where elements are close to their sorted positions.
3. **Merging k Sorted Lists** - Used in problems like "Merge k Sorted Lists" (LeetCode 23).

---

## Conclusion
Heap Sort is an in-place sorting algorithm with O(n log n) complexity, making it efficient for large datasets where stable sorting is not required.
