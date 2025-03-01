# Radix Sort Algorithm

## Definition
Radix Sort is a non-comparative integer sorting algorithm that sorts numbers digit by digit, from the least significant to the most significant digit, using a stable sorting algorithm like Counting Sort.

---

## Pseudocode
```plaintext
RadixSort(arr, n):
    Find the maximum number to determine the number of digits
    for each digit position (1s, 10s, 100s, ...):
        Perform Counting Sort based on the current digit
```

---

## C++ Implementation
```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

int getMax(int arr[], int n) {
    int maxVal = arr[0];
    for (int i = 1; i < n; i++)
        if (arr[i] > maxVal)
            maxVal = arr[i];
    return maxVal;
}

void countingSort(int arr[], int n, int exp) {
    vector<int> output(n);
    vector<int> count(10, 0);

    for (int i = 0; i < n; i++)
        count[(arr[i] / exp) % 10]++;

    for (int i = 1; i < 10; i++)
        count[i] += count[i - 1];

    for (int i = n - 1; i >= 0; i--) {
        output[count[(arr[i] / exp) % 10] - 1] = arr[i];
        count[(arr[i] / exp) % 10]--;
    }

    for (int i = 0; i < n; i++)
        arr[i] = output[i];
}

void radixSort(int arr[], int n) {
    int maxVal = getMax(arr, n);
    for (int exp = 1; maxVal / exp > 0; exp *= 10)
        countingSort(arr, n, exp);
}

void printArray(int arr[], int size) {
    for (int i = 0; i < size; i++)
        cout << arr[i] << " ";
    cout << endl;
}

int main() {
    int arr[] = {170, 45, 75, 90, 802, 24, 2, 66};
    int n = sizeof(arr) / sizeof(arr[0]);
    radixSort(arr, n);
    cout << "Sorted array: ";
    printArray(arr, n);
    return 0;
}
```

---

## Step-by-Step Explanation
### Given array:
```plaintext
arr[] = {170, 45, 75, 90, 802, 24, 2, 66}
```
1. Find the maximum number (802) to determine the number of digit passes.
2. Sort numbers based on each digit position using Counting Sort:
    - **1st pass (1s place):** `{170, 90, 802, 2, 24, 45, 75, 66}`
    - **2nd pass (10s place):** `{802, 2, 24, 45, 66, 170, 75, 90}`
    - **3rd pass (100s place):** `{2, 24, 45, 66, 75, 90, 170, 802}`
3. The final sorted array: `{2, 24, 45, 66, 75, 90, 170, 802}`

---

## Time and Space Complexity
| Case       | Time Complexity |
|------------|----------------|
| Best Case  | O(nk) |
| Worst Case | O(nk) |
| Average Case | O(nk) |
| Space Complexity | O(n + k) |

where `k` is the number of digits in the maximum number.

---

## Applications and Uses
1. **Large Numbers Sorting** - Used when sorting large integers efficiently.
2. **Sorting Strings** - Used in fixed-length string sorting.
3. **Used in DNA Sequencing** - Efficient for sorting large datasets in bioinformatics.
4. **Post Office Sorting** - Used for sorting postal codes.

---

## Specific Problems Where Radix Sort is Useful
1. **Sorting Phone Numbers** - Since phone numbers have fixed digits, Radix Sort is efficient.
2. **Sorting Large Data Without Comparisons** - Useful for scenarios where comparison-based sorting is inefficient.
3. **LSD vs. MSD Sorting Problems** - Used in problems requiring sorting based on different digit significance.

---

## Conclusion
Radix Sort is a powerful non-comparative sorting algorithm that excels in sorting fixed-length numbers or strings. However, it is not ideal when dealing with a large range of values due to its auxiliary space usage.
