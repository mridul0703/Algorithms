# Knuth-Morris-Pratt (KMP) Algorithm

## Introduction
The **Knuth-Morris-Pratt (KMP) algorithm** is an efficient string-searching algorithm used to find the first occurrence of a pattern within a text. Unlike the brute-force method, KMP preprocesses the pattern to avoid redundant comparisons, making it significantly faster for large texts.

## Algorithm Steps
### 1. Compute the LPS (Longest Prefix Suffix) Array:
   - The LPS array is crucial in reducing redundant comparisons.
   - It stores the length of the longest proper prefix which is also a suffix for each prefix of the pattern.
   - This helps determine how much the pattern should be shifted when a mismatch occurs.

### 2. Use the LPS Array to Search the Pattern in the Text:
   - Compare characters of the pattern with the text.
   - If characters match, move both pointers forward.
   - If a mismatch occurs, use the LPS array to determine the next comparison point, avoiding unnecessary resets.

---

## C++ Implementation
```cpp
#include <iostream>
#include <vector>
using namespace std;

// Function to compute the LPS array
vector<int> computeLPS(const string& pattern) {
    int m = pattern.length();
    vector<int> lps(m, 0);
    int len = 0;
    int i = 1;

    while (i < m) {
        if (pattern[i] == pattern[len]) {
            len++;
            lps[i] = len;
            i++;
        } else {
            if (len != 0) {
                len = lps[len - 1];
            } else {
                lps[i] = 0;
                i++;
            }
        }
    }
    return lps;
}

// KMP Algorithm for pattern searching
void KMPSearch(const string& text, const string& pattern) {
    int n = text.length();
    int m = pattern.length();
    vector<int> lps = computeLPS(pattern);

    int i = 0, j = 0;
    while (i < n) {
        if (text[i] == pattern[j]) {
            i++;
            j++;
        }
        if (j == m) {
            cout << "Pattern found at index " << i - j << endl;
            j = lps[j - 1];
        } else if (i < n && text[i] != pattern[j]) {
            if (j != 0) {
                j = lps[j - 1];
            } else {
                i++;
            }
        }
    }
}

int main() {
    string text = "ababcababcabc";
    string pattern = "abc";
    KMPSearch(text, pattern);
    return 0;
}
```

---

## Complexity Analysis
- **Preprocessing LPS Array:** \(O(m)\)
- **Pattern Searching:** \(O(n)\)
- **Overall Time Complexity:** \(O(n + m)\)
- **Space Complexity:** \(O(m)\) (for LPS array)

## Why is KMP Efficient?
- Unlike brute force methods (\(O(nm)\)), KMP does not backtrack the text pointer after a mismatch.
- Utilizes the LPS array to determine the next position for comparison, making it significantly faster.

## Advantages of KMP
- **Eliminates unnecessary comparisons**, improving efficiency.
- **Works well for long texts** where multiple pattern matches might occur.
- **Optimized for multiple pattern searches**, especially in real-time applications.

## Applications
- **Text Searching**: Searching for words in documents, search engines.
- **Plagiarism Detection**: Comparing documents for similarities.
- **DNA Sequence Matching**: Identifying gene patterns in biological sequences.
- **Spam Filtering**: Detecting spam phrases in messages and emails.
- **Intrusion Detection Systems**: Pattern matching in cybersecurity to detect malicious activities.
- **Data Mining**: Identifying recurring patterns in large datasets.
