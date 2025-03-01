# Merge Sort Algorithm

## Definition
Merge Sort is a divide-and-conquer sorting algorithm that splits an array into smaller subarrays, recursively sorts them, and then merges them back together in sorted order.

---

## Pseudocode
```plaintext
MergeSort(arr, left, right):
    if left < right:
        mid = (left + right) / 2
        MergeSort(arr, left, mid)
        MergeSort(arr, mid + 1, right)
        Merge(arr, left, mid, right)

Merge(arr, left, mid, right):
    Create leftSubArray and rightSubArray
    Merge the two subarrays in sorted order
```

---

## C++ Implementation
```cpp
#include <iostream>
using namespace std;

void merge(int arr[], int left, int mid, int right) {
    int n1 = mid - left + 1;
    int n2 = right - mid;

    int leftArr[n1], rightArr[n2];
    for (int i = 0; i < n1; i++)
        leftArr[i] = arr[left + i];
    for (int i = 0; i < n2; i++)
        rightArr[i] = arr[mid + 1 + i];

    int i = 0, j = 0, k = left;
    while (i < n1 && j < n2) {
        if (leftArr[i] <= rightArr[j]) {
            arr[k] = leftArr[i];
            i++;
        } else {
            arr[k] = rightArr[j];
            j++;
        }
        k++;
    }

    while (i < n1) {
        arr[k] = leftArr[i];
        i++;
        k++;
    }

    while (j < n2) {
        arr[k] = rightArr[j];
        j++;
        k++;
    }
}

void mergeSort(int arr[], int left, int right) {
    if (left < right) {
        int mid = left + (right - left) / 2;

        mergeSort(arr, left, mid);
        mergeSort(arr, mid + 1, right);
        merge(arr, left, mid, right);
    }
}

void printArray(int arr[], int n) {
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;
}

int main() {
    int arr[] = {12, 11, 13, 5, 6, 7};
    int n = sizeof(arr) / sizeof(arr[0]);

    cout << "Original Array: ";
    printArray(arr, n);
    
    mergeSort(arr, 0, n - 1);
    
    cout << "Sorted Array: ";
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
### **Step 1: Divide the Array**
- Split into `{12, 11, 13}` and `{5, 6, 7}`
- Further split into `{12}`, `{11, 13}`, `{5}`, `{6, 7}`
- Continue until single elements remain

### **Step 2: Merge and Sort**
- Merge `{11, 13}` into `{11, 12, 13}`
- Merge `{6, 7}` into `{5, 6, 7}`
- Finally, merge `{11, 12, 13}` and `{5, 6, 7}` into `{5, 6, 7, 11, 12, 13}`

Final sorted array: `{5, 6, 7, 11, 12, 13}`

---

## Time and Space Complexity
| Case       | Time Complexity |
|------------|----------------|
| Best Case  | O(n log n) |
| Worst Case | O(n log n) |
| Average Case | O(n log n) |
| Space Complexity | O(n) |

---

## Applications and Uses
1. **Sorting Large Data Sets** - Merge Sort is used when dealing with massive amounts of data.
2. **External Sorting** - Used in scenarios where data does not fit into memory.
3. **Used in Linked Lists** - Merge Sort performs efficiently on linked lists as it minimizes movement.
4. **Parallel Processing** - Suitable for multi-threaded implementations due to divide-and-conquer nature.

---

## Specific Problems Where Merge Sort is Useful
1. **Sorting Large Files** - Used in external sorting where data is too big to fit into RAM.
2. **Counting Inversions in an Array** - Helps find the number of inversions in an array in O(n log n) time.
3. **Sorting Linked Lists** - Efficient for linked list sorting since it does not require random access.
4. **TimSort (Hybrid Algorithm)** - TimSort (used in Python and Java) is a hybrid of Merge Sort and Insertion Sort.

---

## Conclusion
Merge Sort is a highly efficient and stable sorting algorithm with O(n log n) time complexity. It is particularly useful for large datasets and external sorting but requires additional memory for merging.
