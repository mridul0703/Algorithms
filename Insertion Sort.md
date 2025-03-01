# Insertion Sort Algorithm

## Definition
Insertion Sort is a simple and efficient comparison-based sorting algorithm that builds the final sorted array one item at a time by inserting each element into its correct position.

---

## Pseudocode
```plaintext
InsertionSort(arr, n):
    for i from 1 to n-1:
        key = arr[i]
        j = i - 1
        while j >= 0 and arr[j] > key:
            arr[j + 1] = arr[j]
            j = j - 1
        arr[j + 1] = key
```

---

## C++ Implementation
```cpp
#include <iostream>
using namespace std;

void insertionSort(int arr[], int n) {
    for (int i = 1; i < n; i++) {
        int key = arr[i];
        int j = i - 1;
        while (j >= 0 && arr[j] > key) {
            arr[j + 1] = arr[j];
            j = j - 1;
        }
        arr[j + 1] = key;
    }
}

void printArray(int arr[], int n) {
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;
}

int main() {
    int arr[] = {12, 11, 13, 5, 6};
    int n = sizeof(arr) / sizeof(arr[0]);
    
    cout << "Original Array: ";
    printArray(arr, n);
    
    insertionSort(arr, n);
    
    cout << "Sorted Array: ";
    printArray(arr, n);
    return 0;
}
```

---

## Step-by-Step Explanation
Let's take an example array:
```plaintext
arr[] = {12, 11, 13, 5, 6}
```
### **Pass 1:**
- Compare **11** with **12**, insert 11 before 12 → `{11, 12, 13, 5, 6}`

### **Pass 2:**
- Compare **13** with 12, no change → `{11, 12, 13, 5, 6}`

### **Pass 3:**
- Compare **5** with 13, 12, and 11, insert before 11 → `{5, 11, 12, 13, 6}`

### **Pass 4:**
- Compare **6** with 13, 12, and 11, insert before 11 → `{5, 6, 11, 12, 13}`

Final sorted array: `{5, 6, 11, 12, 13}`

---

## Time and Space Complexity
| Case       | Time Complexity |
|------------|----------------|
| Best Case  | O(n) (Already sorted) |
| Worst Case | O(n²) (Reversed order) |
| Average Case | O(n²) |
| Space Complexity | O(1) (In-place sorting) |

---

## Applications and Uses
1. **Efficient for Small Data Sets** - Works well for small and nearly sorted datasets.
2. **Stable Sort** - Preserves the relative order of equal elements.
3. **Used in Online Sorting** - Suitable for situations where elements arrive one by one and need to be sorted dynamically.
4. **Sorting Playing Cards** - Similar to how people sort playing cards in hand.

---

## Specific Problems Where Insertion Sort is Useful
1. **Sorting Partially Sorted Arrays** - If an array is nearly sorted, Insertion Sort performs in O(n) time.
2. **Sorting Small Lists in Hybrid Algorithms** - Often used in Timsort and IntroSort for small subarrays.
3. **Maintaining Order in a Stream of Data** - Used in online algorithms where new elements are continuously added.
4. **Minimal Memory Overhead** - Used in memory-constrained applications where in-place sorting is required.

---

## Conclusion
Insertion Sort is an easy-to-implement algorithm that works well for small or nearly sorted datasets. However, it is inefficient for large datasets due to its O(n²) complexity.
