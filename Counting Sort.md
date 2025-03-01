# Counting Sort Algorithm

## Definition
Counting Sort is a non-comparison-based sorting algorithm that sorts elements by counting the number of occurrences of each unique element. It works efficiently for a limited range of integer values.

---

## Pseudocode
```plaintext
CountingSort(arr, n, maxVal):
    Create count array of size maxVal + 1 and initialize to 0
    for each element in arr:
        count[element] += 1
    
    index = 0
    for i from 0 to maxVal:
        while count[i] > 0:
            arr[index] = i
            index += 1
            count[i] -= 1
```

---

## C++ Implementation
```cpp
#include <iostream>
#include <vector>
using namespace std;

void countingSort(int arr[], int n) {
    int maxVal = *max_element(arr, arr + n);
    vector<int> count(maxVal + 1, 0);

    for (int i = 0; i < n; i++)
        count[arr[i]]++;

    int index = 0;
    for (int i = 0; i <= maxVal; i++) {
        while (count[i] > 0) {
            arr[index++] = i;
            count[i]--;
        }
    }
}

void printArray(int arr[], int size) {
    for (int i = 0; i < size; i++)
        cout << arr[i] << " ";
    cout << endl;
}

int main() {
    int arr[] = {4, 2, 2, 8, 3, 3, 1};
    int n = sizeof(arr) / sizeof(arr[0]);
    countingSort(arr, n);
    cout << "Sorted array: ";
    printArray(arr, n);
    return 0;
}
```

---

## Step-by-Step Explanation
### Given array:
```plaintext
arr[] = {4, 2, 2, 8, 3, 3, 1}
```
1. Find the maximum value: `maxVal = 8`
2. Create a count array: `[0, 1, 2, 0, 1, 0, 0, 0, 1]`
3. Reconstruct sorted array: `{1, 2, 2, 3, 3, 4, 8}`

Final sorted array: `{1, 2, 2, 3, 3, 4, 8}`

---

## Time and Space Complexity
| Case       | Time Complexity |
|------------|----------------|
| Best Case  | O(n + k) |
| Worst Case | O(n + k) |
| Average Case | O(n + k) |
| Space Complexity | O(k) |

where `k` is the range of input values.

---

## Applications and Uses
1. **Sorting Small Range Values** - Best for cases where `k` is not significantly larger than `n`.
2. **Used in Radix Sort** - As a subroutine for sorting digits.
3. **Histogram-based Sorting** - Useful in scenarios like age grouping or frequency analysis.
4. **DNA Sequencing** - Used where values have a limited range.

---

## Specific Problems Where Counting Sort is Useful
1. **Sort Characters in a String** - Problems like "Sort Characters by Frequency" (LeetCode 451).
2. **Sort Elements with Limited Range** - Works well for problems involving small-range integers.
3. **Finding the K-th Most Frequent Element** - Useful in problems requiring frequency analysis.

---

## Conclusion
Counting Sort is a fast and efficient algorithm when `k` is small relative to `n`. However, it is not suitable for sorting large-range values due to its O(k) space complexity.
