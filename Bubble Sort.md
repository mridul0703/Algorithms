# Bubble Sort

## Introduction
Bubble Sort is a simple sorting algorithm that repeatedly steps through the list, compares adjacent elements, and swaps them if they are in the wrong order. The process repeats until the list is sorted. It is named "Bubble Sort" because smaller elements "bubble" to the top of the list.

## Algorithm Steps
1. Start at the beginning of the array.
2. Compare adjacent elements and swap them if needed.
3. Continue this process for the entire array.
4. Repeat until no swaps are needed.

## Pseudo-code
```plaintext
BubbleSort(arr, n):
    for i from 0 to n-1:
        swapped = false
        for j from 0 to n-i-1:
            if arr[j] > arr[j+1]:
                swap(arr[j], arr[j+1])
                swapped = true
        if swapped == false:
            break
```

## C++ Implementation
```cpp
#include <iostream>
using namespace std;

void bubbleSort(int arr[], int n) {
    for (int i = 0; i < n - 1; i++) {
        bool swapped = false;
        for (int j = 0; j < n - i - 1; j++) {
            if (arr[j] > arr[j + 1]) {
                swap(arr[j], arr[j + 1]);
                swapped = true;
            }
        }
        if (!swapped) break;
    }
}

void printArray(int arr[], int n) {
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;
}

int main() {
    int arr[] = {64, 34, 25, 12, 22, 11, 90};
    int n = sizeof(arr) / sizeof(arr[0]);
    cout << "Unsorted array: ";
    printArray(arr, n);
    
    bubbleSort(arr, n);
    
    cout << "Sorted array: ";
    printArray(arr, n);
    return 0;
}
```

## Time Complexity Analysis
| Case        | Complexity |
|------------|-----------|
| Best Case  | O(n) (Already Sorted) |
| Average Case | O(n²) |
| Worst Case  | O(n²) (Reverse Sorted) |

## Space Complexity
- O(1) (In-Place Sorting Algorithm)

## Applications of Bubble Sort
1. **Educational Purpose**: Helps beginners understand the basics of sorting.
2. **Small Datasets**: Works well for small lists where efficiency is not critical.
3. **Detecting Nearly Sorted Data**: The optimized version (with swap check) efficiently detects if an array is already sorted.
4. **Computer Graphics**: Sometimes used in simple animation techniques.
5. **Network Packet Sorting**: Used in scenarios where small sets of data packets need to be sorted.

## Advantages
- Simple and easy to implement.
- Requires no additional memory (in-place sorting).

## Disadvantages
- Inefficient for large datasets.
- O(n²) complexity makes it slower than advanced sorting algorithms.

## Conclusion
Bubble Sort is a fundamental sorting algorithm primarily used for teaching and understanding basic sorting principles. However, for practical applications, more efficient algorithms like Merge Sort, Quick Sort, or Heap Sort are preferred.

---

> **Note:** You can run the provided C++ code to test Bubble Sort and see how it works with different input arrays.
