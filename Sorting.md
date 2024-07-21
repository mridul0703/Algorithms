# Sorting Algorithms Documentation

This file provides a comprehensive overview of common sorting algorithms, including their explanations, time and space complexities, pseudocode, and implementation in C++. Sorting algorithms are fundamental in computer science and are used to arrange data in a particular order. This document covers the following algorithms:

1. [Bubble Sort](#Bubble-sort)
2. [Selection Sort](#selection-sort)
3. [Insertion Sort](#insertion-sort)
4. [Merge Sort](#merge-sort)
5. [Quick Sort](#quick-sort)
6. [Heap Sort](#heap-sort)
7. [Counting Sort](#counting-sort)

---

## Bubble Sort

**Explanation:**  
Bubble Sort repeatedly steps through the list, compares adjacent elements, and swaps them if they are in the wrong order. This process continues until the list is sorted. It is named for the way smaller elements "bubble" to the top of the list.

- **Time Complexity:**
  - Best Case: \(O(n)\) (when the list is already sorted)
  - Average Case: \(O(n^2)\)
  - Worst Case: \(O(n^2)\)
- **Space Complexity:** \(O(1)\) (in-place)

### Pseudocode

```plaintext
function bubbleSort(arr):
    n = length of arr
    for i from 0 to n-1:
        for j from 0 to n-i-2:
            if arr[j] > arr[j+1]:
                swap arr[j] and arr[j+1]
```

### C++ Code

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

int main() {
    int arr[] = {64, 34, 25, 12, 22, 11, 90};
    int n = sizeof(arr) / sizeof(arr[0]);
    bubbleSort(arr, n);
    cout << "Sorted array: ";
    for (int i = 0; i < n; i++)
        cout << arr[i] << " ";
    return 0;
}
```

---

## Selection Sort

**Explanation:**  
Selection Sort divides the array into a sorted and an unsorted region. It repeatedly selects the smallest (or largest) element from the unsorted region and moves it to the end of the sorted region. This continues until the entire array is sorted.

- **Time Complexity:**
  - Best Case: \(O(n^2)\)
  - Average Case: \(O(n^2)\)
  - Worst Case: \(O(n^2)\)
- **Space Complexity:** \(O(1)\) (in-place)

### Pseudocode

```plaintext
function selectionSort(arr):
    n = length of arr
    for i from 0 to n-1:
        minIndex = i
        for j from i+1 to n:
            if arr[j] < arr[minIndex]:
                minIndex = j
        swap arr[i] and arr[minIndex]
```

### C++ Code

```cpp
#include <iostream>
using namespace std;

void selectionSort(int arr[], int n) {
    for (int i = 0; i < n - 1; i++) {
        int minIndex = i;
        for (int j = i + 1; j < n; j++) {
            if (arr[j] < arr[minIndex]) {
                minIndex = j;
            }
        }
        swap(arr[i], arr[minIndex]);
    }
}

int main() {
    int arr[] = {64, 34, 25, 12, 22, 11, 90};
    int n = sizeof(arr) / sizeof(arr[0]);
    selectionSort(arr, n);
    cout << "Sorted array: ";
    for (int i = 0; i < n; i++)
        cout << arr[i] << " ";
    return 0;
}
```

---

## Insertion Sort

**Explanation:**  
Insertion Sort builds the final sorted array one item at a time. It takes each element from the unsorted part and inserts it into the correct position within the sorted part. This is similar to sorting playing cards in your hand.

- **Time Complexity:**
  - Best Case: \(O(n)\) (when the list is already sorted)
  - Average Case: \(O(n^2)\)
  - Worst Case: \(O(n^2)\)
- **Space Complexity:** \(O(1)\) (in-place)

### Pseudocode

```plaintext
function insertionSort(arr):
    n = length of arr
    for i from 1 to n-1:
        key = arr[i]
        j = i - 1
        while j >= 0 and arr[j] > key:
            arr[j + 1] = arr[j]
            j = j - 1
        arr[j + 1] = key
```

### C++ Code

```cpp
#include <iostream>
using namespace std;

void insertionSort(int arr[], int n) {
    for (int i = 1; i < n; i++) {
        int key = arr[i];
        int j = i - 1;
        while (j >= 0 && arr[j] > key) {
            arr[j + 1] = arr[j];
            j--;
        }
        arr[j + 1] = key;
    }
}

int main() {
    int arr[] = {64, 34, 25, 12, 22, 11, 90};
    int n = sizeof(arr) / sizeof(arr[0]);
    insertionSort(arr, n);
    cout << "Sorted array: ";
    for (int i = 0; i < n; i++)
        cout << arr[i] << " ";
    return 0;
}
```

---

## Merge Sort

**Explanation:**  
Merge Sort is a Divide and Conquer algorithm. It divides the array into two halves, recursively sorts each half, and then merges the two sorted halves to produce the final sorted array. It ensures \(O(n \log n)\) performance.

- **Time Complexity:**
  - Best Case: \(O(n \log n)\)
  - Average Case: \(O(n \log n)\)
  - Worst Case: \(O(n \log n)\)
- **Space Complexity:** \(O(n)\) (not in-place)

### Pseudocode

```plaintext
function mergeSort(arr, l, r):
    if l < r:
        m = (l + r) / 2
        mergeSort(arr, l, m)
        mergeSort(arr, m + 1, r)
        merge(arr, l, m, r)

function merge(arr, l, m, r):
    n1 = m - l + 1
    n2 = r - m
    L = array of size n1
    R = array of size n2
    for i from 0 to n1-1:
        L[i] = arr[l + i]
    for j from 0 to n2-1:
        R[j] = arr[m + 1 + j]
    i = 0
    j = 0
    k = l
    while i < n1 and j < n2:
        if L[i] <= R[j]:
            arr[k] = L[i]
            i++
        else:
            arr[k] = R[j]
            j++
        k++
    while i < n1:
        arr[k] = L[i]
        i++
        k++
    while j < n2:
        arr[k] = R[j]
        j++
        k++
```

### C++ Code

```cpp
#include <iostream>
using namespace std;

void merge(int arr[], int l, int m, int r) {
    int n1 = m - l + 1;
    int n2 = r - m;
    int *L = new int[n1];
    int *R = new int[n2];
    for (int i = 0; i < n1; i++)
        L[i] = arr[l + i];
    for (int j = 0; j < n2; j++)
        R[j] = arr[m + 1 + j];
    int i = 0, j = 0, k = l;
    while (i < n1 && j < n2) {
        if (L[i] <= R[j]) {
            arr[k] = L[i];
            i++;
        } else {
            arr[k] = R[j];
            j++;
        }
        k++;
    }
    while (i < n1) {
        arr[k] = L[i];
        i++;
        k++;
    }
    while (j < n2) {
        arr[k] = R[j];
        j++;
        k++;
    }
    delete[] L;
    delete[] R;
}

void mergeSort(int arr[], int l, int r) {
    if (l < r) {
        int m = l + (r - l) / 2;
        mergeSort(arr, l, m);
        mergeSort(arr, m + 1, r);
        merge(arr, l, m, r);
    }
}

int main() {
    int arr[] = {64, 34, 25, 12, 22, 11, 90};
    int n = sizeof(arr) / sizeof(arr[0]);
    mergeSort(arr, 0, n - 1);
    cout << "Sorted array: ";
    for (int i = 0; i < n; i++)
        cout << arr[i] << " ";
    return 0;
}
```

---

## Quick Sort

**Explanation:**  
Quick Sort is a Divide and Conquer algorithm that selects a 'pivot' element, partitions the array into elements less than and

 greater than the pivot, and recursively sorts the subarrays. It has a good average-case performance.

- **Time Complexity:**
  - Best Case: \(O(n \log n)\)
  - Average Case: \(O(n \log n)\)
  - Worst Case: \(O(n^2)\) (when the pivot is the smallest or largest element)
- **Space Complexity:** \(O(\log n)\) (in-place)

### Pseudocode

```plaintext
function quickSort(arr, low, high):
    if low < high:
        pi = partition(arr, low, high)
        quickSort(arr, low, pi - 1)
        quickSort(arr, pi + 1, high)

function partition(arr, low, high):
    pivot = arr[high]
    i = low - 1
    for j from low to high-1:
        if arr[j] <= pivot:
            i++
            swap arr[i] and arr[j]
    swap arr[i + 1] and arr[high]
    return i + 1
```

### C++ Code

```cpp
#include <iostream>
using namespace std;

int partition(int arr[], int low, int high) {
    int pivot = arr[high];
    int i = low - 1;
    for (int j = low; j < high; j++) {
        if (arr[j] <= pivot) {
            i++;
            swap(arr[i], arr[j]);
        }
    }
    swap(arr[i + 1], arr[high]);
    return i + 1;
}

void quickSort(int arr[], int low, int high) {
    if (low < high) {
        int pi = partition(arr, low, high);
        quickSort(arr, low, pi - 1);
        quickSort(arr, pi + 1, high);
    }
}

int main() {
    int arr[] = {64, 34, 25, 12, 22, 11, 90};
    int n = sizeof(arr) / sizeof(arr[0]);
    quickSort(arr, 0, n - 1);
    cout << "Sorted array: ";
    for (int i = 0; i < n; i++)
        cout << arr[i] << " ";
    return 0;
}
```

---

## Heap Sort

**Explanation:**  
Heap Sort is a comparison-based sorting algorithm that uses a binary heap data structure. It builds a max heap from the input data, repeatedly extracts the maximum element from the heap, and rebuilds the heap until the array is sorted.

- **Time Complexity:**
  - Best Case: \(O(n \log n)\)
  - Average Case: \(O(n \log n)\)
  - Worst Case: \(O(n \log n)\)
- **Space Complexity:** \(O(1)\) (in-place)

### Pseudocode

```plaintext
function heapSort(arr):
    n = length of arr
    buildMaxHeap(arr, n)
    for i from n-1 down to 1:
        swap arr[0] and arr[i]
        heapify(arr, 0, i)

function buildMaxHeap(arr, n):
    for i from n/2-1 down to 0:
        heapify(arr, i, n)

function heapify(arr, i, n):
    largest = i
    l = 2*i + 1
    r = 2*i + 2
    if l < n and arr[l] > arr[largest]:
        largest = l
    if r < n and arr[r] > arr[largest]:
        largest = r
    if largest != i:
        swap arr[i] and arr[largest]
        heapify(arr, largest, n)
```

### C++ Code

```cpp
#include <iostream>
using namespace std;

void heapify(int arr[], int n, int i) {
    int largest = i;
    int l = 2 * i + 1;
    int r = 2 * i + 2;
    if (l < n && arr[l] > arr[largest])
        largest = l;
    if (r < n && arr[r] > arr[largest])
        largest = r;
    if (largest != i) {
        swap(arr[i], arr[largest]);
        heapify(arr, n, largest);
    }
}

void buildMaxHeap(int arr[], int n) {
    for (int i = n / 2 - 1; i >= 0; i--)
        heapify(arr, n, i);
}

void heapSort(int arr[], int n) {
    buildMaxHeap(arr, n);
    for (int i = n - 1; i >= 1; i--) {
        swap(arr[0], arr[i]);
        heapify(arr, i, 0);
    }
}

int main() {
    int arr[] = {64, 34, 25, 12, 22, 11, 90};
    int n = sizeof(arr) / sizeof(arr[0]);
    heapSort(arr, n);
    cout << "Sorted array: ";
    for (int i = 0; i < n; i++)
        cout << arr[i] << " ";
    return 0;
}
```

---

## Counting Sort

**Explanation:**  
Counting Sort is a non-comparison-based sorting algorithm. It counts the number of occurrences of each distinct element and uses this information to place elements in the correct position in the output array. It's efficient for sorting integers within a small range.

- **Time Complexity:**
  - Best Case: \(O(n + k)\)
  - Average Case: \(O(n + k)\)
  - Worst Case: \(O(n + k)\)
- **Space Complexity:** \(O(k)\) (where \(k\) is the range of input values)

### Pseudocode

```plaintext
function countingSort(arr):
    maxVal = findMax(arr)
    count = array of size maxVal+1 with all values 0
    for each element in arr:
        count[element]++
    index = 0
    for i from 0 to maxVal:
        while count[i] > 0:
            arr[index] = i
            index++
            count[i]--
```

### C++ Code

```cpp
#include <iostream>
using namespace std;

void countingSort(int arr[], int n) {
    int maxVal = arr[0];
    for (int i = 1; i < n; i++)
        if (arr[i] > maxVal)
            maxVal = arr[i];
    int *count = new int[maxVal + 1]();
    for (int i = 0; i < n; i++)
        count[arr[i]]++;
    int index = 0;
    for (int i = 0; i <= maxVal; i++) {
        while (count[i] > 0) {
            arr[index] = i;
            index++;
            count[i]--;
        }
    }
    delete[] count;
}

int main() {
    int arr[] = {64, 34, 25, 12, 22, 11, 90};
    int n = sizeof(arr) / sizeof(arr[0]);
    countingSort(arr, n);
    cout << "Sorted array: ";
    for (int i = 0; i < n; i++)
        cout << arr[i] << " ";
    return 0;
}
```

---

Feel free to use this improved version for your documentation or GitHub repository. Let me know if there's anything else you need!
