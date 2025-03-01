# Bucket Sort Algorithm

## Definition
Bucket Sort is a sorting algorithm that divides elements into multiple buckets and sorts each bucket individually using another sorting technique, such as Insertion Sort.

---

## Pseudocode
```plaintext
BucketSort(arr, n):
    Create empty buckets
    Distribute elements into buckets based on range
    Sort each bucket using insertion sort
    Merge sorted buckets back into the array
```

---

## C++ Implementation
```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

void bucketSort(float arr[], int n) {
    vector<float> buckets[n];
    
    for (int i = 0; i < n; i++) {
        int bucketIndex = n * arr[i];
        buckets[bucketIndex].push_back(arr[i]);
    }
    
    for (int i = 0; i < n; i++)
        sort(buckets[i].begin(), buckets[i].end());
    
    int index = 0;
    for (int i = 0; i < n; i++)
        for (float num : buckets[i])
            arr[index++] = num;
}

void printArray(float arr[], int size) {
    for (int i = 0; i < size; i++)
        cout << arr[i] << " ";
    cout << endl;
}

int main() {
    float arr[] = {0.42, 0.32, 0.33, 0.52, 0.37, 0.47, 0.51};
    int n = sizeof(arr) / sizeof(arr[0]);
    bucketSort(arr, n);
    cout << "Sorted array: ";
    printArray(arr, n);
    return 0;
}
```

---

## Step-by-Step Explanation
### Given array:
```plaintext
arr[] = {0.42, 0.32, 0.33, 0.52, 0.37, 0.47, 0.51}
```
1. Create `n` empty buckets.
2. Distribute elements into buckets based on their value:
    - `0.42 → bucket[4]`
    - `0.32 → bucket[3]`
    - `0.33 → bucket[3]`
    - `0.52 → bucket[5]`
    - `0.37 → bucket[3]`
    - `0.47 → bucket[4]`
    - `0.51 → bucket[5]`
3. Sort individual buckets.
4. Merge all sorted buckets into the final array.

Final sorted array: `{0.32, 0.33, 0.37, 0.42, 0.47, 0.51, 0.52}`

---

## Time and Space Complexity
| Case       | Time Complexity |
|------------|----------------|
| Best Case  | O(n + k) |
| Worst Case | O(n²) |
| Average Case | O(n + k) |
| Space Complexity | O(n) |

where `k` is the number of buckets.

---

## Applications and Uses
1. **Sorting Floating-Point Numbers** - Best suited for numbers uniformly distributed over a range.
2. **Histogram Sorting** - Efficient when sorting elements within a fixed range.
3. **Data Clustering** - Used for clustering large datasets before further analysis.

---

## Specific Problems Where Bucket Sort is Useful
1. **Sorting Fractions or Floating-Point Numbers** - Sorting decimal values efficiently.
2. **Visualizing Data for Machine Learning** - Sorting datasets before further processing.
3. **Sorting in Computational Geometry** - Used in nearest neighbor problems and convex hull algorithms.

---

## Conclusion
Bucket Sort is a powerful algorithm when working with uniformly distributed data, but its efficiency depends on the proper selection of bucket sizes and the sorting technique used inside the buckets.
