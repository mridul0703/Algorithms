# Selection Sort Algorithm

## Definition
Selection Sort is a simple comparison-based sorting algorithm that repeatedly selects the smallest (or largest) element from the unsorted portion and places it in the correct position.

---

## Pseudocode
```plaintext
SelectionSort(arr, n):
    for i from 0 to n-1:
        min_index = i
        for j from i+1 to n:
            if arr[j] < arr[min_index]:
                min_index = j
        swap(arr[i], arr[min_index])
```

---

## C++ Implementation
```cpp
#include <iostream>
using namespace std;

void selectionSort(int arr[], int n) {
    for (int i = 0; i < n - 1; i++) {
        int min_index = i;
        for (int j = i + 1; j < n; j++) {
            if (arr[j] < arr[min_index]) {
                min_index = j;
            }
        }
        swap(arr[i], arr[min_index]);
    }
}

void printArray(int arr[], int n) {
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;
}

int main() {
    int arr[] = {64, 25, 12, 22, 11};
    int n = sizeof(arr) / sizeof(arr[0]);
    
    cout << "Original Array: ";
    printArray(arr, n);
    
    selectionSort(arr, n);
    
    cout << "Sorted Array: ";
    printArray(arr, n);
    return 0;
}
```

---

## Step-by-Step Explanation
Let's take an example array:
```plaintext
arr[] = {64, 25, 12, 22, 11}
```
### **Pass 1:**
- Find the smallest element in `{64, 25, 12, 22, 11}` → **11**
- Swap 11 with 64 → `{11, 25, 12, 22, 64}`

### **Pass 2:**
- Find the smallest element in `{25, 12, 22, 64}` → **12**
- Swap 12 with 25 → `{11, 12, 25, 22, 64}`

### **Pass 3:**
- Find the smallest element in `{25, 22, 64}` → **22**
- Swap 22 with 25 → `{11, 12, 22, 25, 64}`

### **Pass 4:**
- Find the smallest element in `{25, 64}` → **25** (no swap needed)
- Final sorted array: `{11, 12, 22, 25, 64}`

---

## Time and Space Complexity
| Case       | Time Complexity |
|------------|----------------|
| Best Case  | O(n²) |
| Worst Case | O(n²) |
| Average Case | O(n²) |
| Space Complexity | O(1) (In-place sort) |

---

## Applications and Uses
1. **Small Data Sets** - Efficient for small datasets where simplicity is preferred.
2. **No Extra Space Needed** - Works in O(1) extra space (in-place sorting).
3. **Easy to Implement** - Simple algorithm for teaching sorting concepts.
4. **Not Stable** - Doesn't preserve the relative order of equal elements.
5. **Used in Embedded Systems** - Works well in environments with memory constraints.

---

## Specific Problems Where Selection Sort is Useful
1. **Sorting Students by Marks** - If the dataset is small, Selection Sort can be used to arrange students' scores in ascending order.
2. **Finding the Kth Smallest/Largest Element** - Instead of sorting the entire array, we can run Selection Sort for the first K iterations to find the Kth smallest/largest element efficiently.
3. **Arranging Players in a Tournament** - When ranking a small number of players based on their scores.
4. **Selection in Hardware Implementation** - Used where simple, minimal memory sorting is required in embedded systems.

---

## Conclusion
Selection Sort is an easy-to-understand sorting algorithm but inefficient for large datasets due to its O(n²) complexity. It is useful for teaching and small-scale applications where memory is a concern.
