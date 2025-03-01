# Bubble Sort Algorithm

## Definition
Bubble Sort is a simple sorting algorithm that repeatedly swaps adjacent elements if they are in the wrong order. It is named for the way smaller elements "bubble" to the top of the array.

---

## Pseudocode
```plaintext
BubbleSort(arr, n):
    for i from 0 to n-1:
        for j from 0 to n-i-1:
            if arr[j] > arr[j+1]:
                swap(arr[j], arr[j+1])
```

---

## C++ Implementation
```cpp
#include <iostream>
using namespace std;

void bubbleSort(int arr[], int n) {
    for (int i = 0; i < n - 1; i++) {
        for (int j = 0; j < n - i - 1; j++) {
            if (arr[j] > arr[j + 1]) {
                swap(arr[j], arr[j + 1]);
            }
        }
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
    
    cout << "Original Array: ";
    printArray(arr, n);
    
    bubbleSort(arr, n);
    
    cout << "Sorted Array: ";
    printArray(arr, n);
    return 0;
}
```

---

## Step-by-Step Explanation
Let's take an example array:
```plaintext
arr[] = {64, 34, 25, 12, 22, 11, 90}
```
### **Pass 1:**
```plaintext
(64 34) 25 12 22 11 90 → Swap → (34 64) 25 12 22 11 90
34 (64 25) 12 22 11 90 → Swap → 34 (25 64) 12 22 11 90
34 25 (64 12) 22 11 90 → Swap → 34 25 (12 64) 22 11 90
34 25 12 (64 22) 11 90 → Swap → 34 25 12 (22 64) 11 90
34 25 12 22 (64 11) 90 → Swap → 34 25 12 22 (11 64) 90
34 25 12 22 11 (64 90) → No swap
```
### **Pass 2:**
```plaintext
(34 25) 12 22 11 64 90 → Swap → (25 34) 12 22 11 64 90
25 (34 12) 22 11 64 90 → Swap → 25 (12 34) 22 11 64 90
25 12 (34 22) 11 64 90 → Swap → 25 12 (22 34) 11 64 90
25 12 22 (34 11) 64 90 → Swap → 25 12 22 (11 34) 64 90
```
Repeating this process, we get:
```plaintext
Final Sorted Array: {11, 12, 22, 25, 34, 64, 90}
```

---

## Time and Space Complexity
| Case       | Time Complexity |
|------------|----------------|
| Best Case  | O(n) (Already sorted) |
| Worst Case | O(n²) (Reversed order) |
| Average Case | O(n²) |
| Space Complexity | O(1) (In-place sort) |

---

## Applications and Uses
1. **Educational Purposes** - Used to teach sorting concepts due to its simplicity.
2. **Small Data Sets** - Works well for small arrays where performance is not a concern.
3. **Step-by-Step Visualization** - Used in animations and debugging for learning sorting concepts.
4. **Detecting Sorted Data** - If no swaps occur in a pass, the array is already sorted.

---

## Specific Problems Where Bubble Sort is Useful
1. **Detecting Nearly Sorted Data** - If the input array is almost sorted, Bubble Sort performs efficiently in O(n) time.
2. **Sorting Small Lists** - In small datasets, where simplicity matters more than efficiency, Bubble Sort can be useful.
3. **Sorting Student Roll Numbers** - When working with small numbers of records in an educational system.
4. **Checking Array Sortedness** - Bubble Sort can be used to verify whether an array is sorted by checking for swaps in one pass.
5. **Bubble Down Effect in Simulations** - Used in some simulations where elements need to settle in order, like particle sorting.

---

## Conclusion
Bubble Sort is easy to implement but inefficient for large datasets due to its O(n²) complexity. It is useful in teaching, debugging, and handling small datasets efficiently.
