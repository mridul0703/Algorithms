# Quick Sort Algorithm

## Definition
Quick Sort is a divide-and-conquer algorithm that selects a pivot element, partitions the array around the pivot, and recursively sorts the partitions.

---

## Pseudocode
```plaintext
QuickSort(arr, low, high):
    if low < high:
        pivotIndex = Partition(arr, low, high)
        QuickSort(arr, low, pivotIndex - 1)
        QuickSort(arr, pivotIndex + 1, high)

Partition(arr, low, high):
    pivot = arr[high]
    i = low - 1
    for j from low to high - 1:
        if arr[j] < pivot:
            i++
            swap(arr[i], arr[j])
    swap(arr[i + 1], arr[high])
    return i + 1
```

---

## C++ Implementation
```cpp
#include <iostream>
using namespace std;

int partition(int arr[], int low, int high) {
    int pivot = arr[high];
    int i = (low - 1);
    for (int j = low; j < high; j++) {
        if (arr[j] < pivot) {
            i++;
            swap(arr[i], arr[j]);
        }
    }
    swap(arr[i + 1], arr[high]);
    return (i + 1);
}

void quickSort(int arr[], int low, int high) {
    if (low < high) {
        int pi = partition(arr, low, high);
        quickSort(arr, low, pi - 1);
        quickSort(arr, pi + 1, high);
    }
}

void printArray(int arr[], int size) {
    for (int i = 0; i < size; i++)
        cout << arr[i] << " ";
    cout << endl;
}

int main() {
    int arr[] = {10, 7, 8, 9, 1, 5};
    int n = sizeof(arr) / sizeof(arr[0]);
    quickSort(arr, 0, n - 1);
    cout << "Sorted array: ";
    printArray(arr, n);
    return 0;
}
```

---

## Step-by-Step Explanation
### Given array:
```plaintext
arr[] = {10, 7, 8, 9, 1, 5}
```
1. Choose pivot (e.g., last element `5`)
2. Partition array into elements `< 5` and `>= 5`
3. Recursively apply Quick Sort on partitions

Final sorted array: `{1, 5, 7, 8, 9, 10}`

---

## Time and Space Complexity
| Case       | Time Complexity |
|------------|----------------|
| Best Case  | O(n log n) |
| Worst Case | O(n^2) |
| Average Case | O(n log n) |
| Space Complexity | O(log n) |

---

## Applications and Uses
1. **Efficient Sorting** - Quick Sort is widely used in sorting algorithms due to its average O(n log n) complexity.
2. **Divide-and-Conquer Algorithms** - Forms a base for other recursive solutions.
3. **Database Sorting** - Used in indexing and searching operations.
4. **Competitive Programming** - Preferred for fast in-memory sorting.

---

## Specific Problems Where Quick Sort is Useful
1. **Sorting Large Arrays in Competitive Programming** - Quick Sort is often the fastest approach.
2. **Sorting in Database Queries** - Used for optimizing query operations.
3. **Median Finding Algorithms** - Quick Sort helps in efficiently finding medians.
4. **External Sorting** - Used in cases where memory efficiency is critical.

---

## Conclusion
Quick Sort is one of the fastest sorting algorithms, widely used in practice, but it can have O(n²) worst-case complexity if pivot selection is poor. Choosing a good pivot (e.g., median of three) helps improve efficiency.
