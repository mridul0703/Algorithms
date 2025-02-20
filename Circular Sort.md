# Cycle Sort (Circular Sort)

## Introduction
Cycle Sort is an in-place, non-comparative sorting algorithm that minimizes the number of writes to the array. It is optimal when writes are costly, such as in EEPROMs or flash memory, where the number of writes affects the lifespan of the memory.

### **Key Features:**
- In-place sorting (O(1) extra space)
- Runs in O(n²) time complexity in the worst case
- Minimizes the number of swaps (optimal for cases where write operations are costly)

---

## **Algorithm Explanation**
Cycle Sort works by identifying **cycles** in the permutation and rotating them into the correct position.

1. **Start from the first element** and determine where it should be in a sorted array.
2. **Place the element at its correct position** by swapping.
3. **Continue shifting displaced elements until the cycle completes.**
4. **Repeat the process for the remaining elements.**

---

## **Pseudocode**
```plaintext
Function cycleSort(arr, n):
    for cycle_start from 0 to n-2:
        item = arr[cycle_start]
        pos = cycle_start
        
        // Find the correct position of the item
        for i from cycle_start+1 to n-1:
            if arr[i] < item:
                pos += 1
        
        // If item is already in the correct position, continue
        if pos == cycle_start:
            continue
        
        // Skip duplicate elements
        while item == arr[pos]:
            pos += 1
        
        // Swap the item into its correct position
        swap(item, arr[pos])
        
        // Rotate the rest of the cycle
        while pos != cycle_start:
            pos = cycle_start
            for i from cycle_start+1 to n-1:
                if arr[i] < item:
                    pos += 1
            
            while item == arr[pos]:
                pos += 1
            
            swap(item, arr[pos])
```

---

## **C++ Implementation**
```cpp
#include <iostream>
#include <vector>
using namespace std;

void cycleSort(vector<int>& arr, int n) {
    for (int cycle_start = 0; cycle_start < n - 1; cycle_start++) {
        int item = arr[cycle_start];
        int pos = cycle_start;
        
        // Find the position where we put the current item
        for (int i = cycle_start + 1; i < n; i++) {
            if (arr[i] < item) pos++;
        }
        
        // If item is already in the correct position, continue
        if (pos == cycle_start) continue;
        
        // Skip duplicate elements
        while (item == arr[pos]) pos++;
        swap(item, arr[pos]);
        
        // Rotate the rest of the cycle
        while (pos != cycle_start) {
            pos = cycle_start;
            for (int i = cycle_start + 1; i < n; i++) {
                if (arr[i] < item) pos++;
            }
            
            while (item == arr[pos]) pos++;
            swap(item, arr[pos]);
        }
    }
}

int main() {
    vector<int> arr = {4, 3, 2, 1, 5};
    int n = arr.size();
    
    cycleSort(arr, n);
    
    cout << "Sorted array: ";
    for (int num : arr) {
        cout << num << " ";
    }
    cout << endl;
    return 0;
}
```

---

## **Complexity Analysis**
- **Best Case:** `O(n log n)` (rare but possible)
- **Average Case:** `O(n²)`
- **Worst Case:** `O(n²)`
- **Space Complexity:** `O(1)` (in-place sorting)
- **Number of Writes:** `O(n)` (optimal when minimizing writes)

---

## **Edge Cases**
✅ Already sorted array (no swaps needed)  
✅ Reverse sorted array (max swaps needed)  
✅ Array with duplicate elements  
✅ Array with all elements the same (no swaps needed)  

---

## **Conclusion**
Cycle Sort is efficient when minimizing write operations is crucial, but it is not the best general-purpose sorting algorithm due to its `O(n²)` time complexity. However, it remains an important sorting technique in scenarios where write operations are expensive, such as EEPROM memory devices.

🚀 **Happy Coding!**
