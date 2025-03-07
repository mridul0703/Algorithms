# Sieve of Eratosthenes

## Introduction
The **Sieve of Eratosthenes** is an efficient algorithm for finding all prime numbers up to a given limit. It works by iteratively marking the multiples of each prime number starting from 2.

## Algorithm
1. Create a boolean array `isPrime[]` and initialize all entries as `true`.
2. Start from the first prime number, 2.
3. Mark all multiples of 2 (except 2 itself) as `false`.
4. Move to the next unmarked number (which is the next prime) and repeat the process.
5. Continue until all numbers up to the given limit are processed.

## Pseudocode
```plaintext
SieveOfEratosthenes(n):
    Create an array isPrime of size n+1 and set all elements to true
    Set isPrime[0] and isPrime[1] to false (0 and 1 are not prime)
    
    For i from 2 to sqrt(n):
        If isPrime[i] is true:
            For j from i*i to n with step i:
                Set isPrime[j] to false
    
    Print all numbers where isPrime[i] is true
```

## Implementation in C++
```cpp
#include <iostream>
#include <vector>
using namespace std;

void sieveOfEratosthenes(int n) {
    vector<bool> isPrime(n + 1, true);
    isPrime[0] = isPrime[1] = false;

    for (int i = 2; i * i <= n; i++) {
        if (isPrime[i]) {
            for (int j = i * i; j <= n; j += i) {
                isPrime[j] = false;
            }
        }
    }

    cout << "Prime numbers up to " << n << ": ";
    for (int i = 2; i <= n; i++) {
        if (isPrime[i]) {
            cout << i << " ";
        }
    }
    cout << endl;
}

int main() {
    int n;
    cout << "Enter the limit: ";
    cin >> n;
    sieveOfEratosthenes(n);
    return 0;
}
```

## Complexity Analysis
- **Time Complexity**: **O(n log log n)** (Highly efficient for large `n`)
- **Space Complexity**: **O(n)** (Stores a boolean array of size `n`)

## Example Output
```
Enter the limit: 30
Prime numbers up to 30: 2 3 5 7 11 13 17 19 23 29
```

## Applications
- Finding prime numbers efficiently.
- Cryptography and security algorithms.
- Generating prime numbers for mathematical problems.

## References
- [Wikipedia: Sieve of Eratosthenes](https://en.wikipedia.org/wiki/Sieve_of_Eratosthenes)
- [GeeksforGeeks Explanation](https://www.geeksforgeeks.org/sieve-of-eratosthenes/)

---

This repository contains a simple and efficient implementation of the **Sieve of Eratosthenes** algorithm in C++. Feel free to contribute and improve the code!
