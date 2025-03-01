# Analysis of Sorting Algorithms

## Introduction
Sorting algorithms are fundamental in computer science and are used in various applications such as database management, searching, and data organization. Each sorting algorithm has its own advantages, use cases, and efficiency based on the dataset and problem constraints.

---

## Brief Working of Sorting Algorithms

| Algorithm | Working Mechanism |
|-----------|------------------|
| **Bubble Sort** | Repeatedly swaps adjacent elements if they are in the wrong order, moving the largest element to the end in each pass. |
| **Selection Sort** | Selects the smallest element in each iteration and swaps it with the first unsorted element. |
| **Insertion Sort** | Inserts each element in its correct position by shifting larger elements to the right. |
| **Merge Sort** | Recursively divides the array into halves, sorts each half, and merges them in sorted order. |
| **Quick Sort** | Selects a pivot, partitions the array around it, and recursively sorts the subarrays. |
| **Heap Sort** | Converts the array into a heap and repeatedly extracts the maximum (or minimum) element. |
| **Counting Sort** | Uses a frequency array to count occurrences and place elements directly into the sorted array. |
| **Radix Sort** | Sorts numbers digit by digit using counting sort as a subroutine. |
| **Bucket Sort** | Divides the elements into buckets, sorts each bucket, and combines them. |
| **Shell Sort** | Uses a decreasing sequence of gaps to perform insertion sort on elements spaced apart, reducing swaps. |

---

## Comparison of Sorting Algorithms

| Algorithm       | Best Case  | Average Case | Worst Case  | Space Complexity | Stable | Use Cases |
|---------------|------------|-------------|------------|----------------|--------|-----------|
| **Bubble Sort** | O(n)       | O(n²)       | O(n²)       | O(1)           | Yes    | Small datasets, teaching purposes |
| **Selection Sort** | O(n²)    | O(n²)       | O(n²)       | O(1)           | No     | Small datasets, when swaps are expensive |
| **Insertion Sort** | O(n)    | O(n²)       | O(n²)       | O(1)           | Yes    | Nearly sorted arrays, small datasets |
| **Merge Sort** | O(n log n)  | O(n log n)  | O(n log n)  | O(n)           | Yes    | Large datasets, linked lists |
| **Quick Sort** | O(n log n)  | O(n log n)  | O(n²)       | O(log n)       | No     | General-purpose sorting, quick execution |
| **Heap Sort** | O(n log n)  | O(n log n)  | O(n log n)  | O(1)           | No     | Priority queues, large datasets |
| **Counting Sort** | O(n + k) | O(n + k)    | O(n + k)    | O(k)           | Yes    | Sorting integers with a limited range |
| **Radix Sort** | O(nk)      | O(nk)       | O(nk)       | O(n + k)       | Yes    | Sorting numbers, words, or fixed-length strings |
| **Bucket Sort** | O(n + k)  | O(n + k)    | O(n²)       | O(n + k)       | Yes    | Floating-point numbers, uniform distribution |
| **Shell Sort** | O(n log n) | O(n log n)  | O(n²)       | O(1)           | No     | Medium-sized datasets, optimized insertion sort |

---
