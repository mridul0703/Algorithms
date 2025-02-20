# Kadane's Algorithm

## Introduction
Kadane's Algorithm is a famous algorithm used to find the maximum sum of a contiguous subarray within a one-dimensional numeric array. It runs in **O(n)** time complexity, making it an efficient solution for the **Maximum Subarray Sum** problem.

## Problem Statement
Given an array `arr[]` of size `n`, find the **maximum sum of a contiguous subarray**.

### Example:
#### Input:
```cpp
arr[] = {-2, 1, -3, 4, -1, 2, 1, -5, 4}
```
#### Output:
```
Maximum contiguous sum is 6
```
#### Explanation:
The subarray `[4, -1, 2, 1]` has the maximum sum `6`.

---

## Approach
1. Initialize two variables:
   - `maxSum` to store the maximum sum found so far.
   - `currentSum` to store the sum of the current subarray.
2. Iterate through the array:
   - Add the current element to `currentSum`.
   - If `currentSum` exceeds `maxSum`, update `maxSum`.
   - If `currentSum` becomes negative, reset it to `0`.
3. Return `maxSum` as the result.

---

## Pseudo Code
```
function kadaneAlgorithm(arr, n):
    maxSum = -∞  // Initialize max sum as negative infinity
    currentSum = 0
    
    for i from 0 to n-1:
        currentSum = currentSum + arr[i]
        if currentSum > maxSum:
            maxSum = currentSum
        if currentSum < 0:
            currentSum = 0
    
    return maxSum
```

---

## C++ Implementation
```cpp
#include <iostream>
#include <climits>
using namespace std;

int kadane(int arr[], int n) {
    int maxSum = INT_MIN, currentSum = 0;

    for (int i = 0; i < n; i++) {
        currentSum += arr[i];
        if (currentSum > maxSum)
            maxSum = currentSum;
        if (currentSum < 0)
            currentSum = 0;
    }
    return maxSum;
}

int main() {
    int arr[] = {-2, 1, -3, 4, -1, 2, 1, -5, 4};
    int n = sizeof(arr) / sizeof(arr[0]);
    cout << "Maximum contiguous sum is " << kadane(arr, n) << endl;
    return 0;
}
```

---

## Complexity Analysis
- **Time Complexity:** `O(n)`, since we traverse the array once.
- **Space Complexity:** `O(1)`, as we use only a few extra variables.

---

## Edge Cases Considered
- All negative elements (choose the largest element as the max sum).
- A mix of positive and negative numbers.
- An already sorted increasing or decreasing array.
- Single-element arrays.

---

## Variants of Kadane's Algorithm
1. **Finding the subarray itself**:
   - Maintain `start`, `end`, and `tempStart` indices.
2. **2D Kadane's Algorithm**:
   - Used for finding the maximum sum submatrix in a 2D array.

---

## Conclusion
Kadane’s Algorithm efficiently finds the maximum contiguous subarray sum in linear time, making it a fundamental algorithm in competitive programming and interviews.
