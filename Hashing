# Hashing (Video 13)

## 1. What is Hashing?

**Hashing** is a technique used to **store and fetch data efficiently** using an index.

 Instead of searching every time, we:

* **Pre-store** information
* **Fetch** it in constant time

---

## 2. Problem with Naive Approach

### Example:

Count how many times a number appears in an array.

```cpp
int f(int number, int arr[], int n) {
    int cnt = 0;
    for(int i = 0; i < n; i++) {
        if(arr[i] == number)
            cnt++;
    }
    return cnt;
}
```

### Time Complexity:

* One query → **O(n)**
* `Q` queries → **O(Q × n)**

Example:

* `n = 10^5`
* `Q = 10^5`

[
O(10^5 \times 10^5) = O(10^{10})
]

 **Too slow (≈ 100 seconds)**

---

## 3. Idea of Hashing (Pre-Storing + Fetching)

### Key Concept:

* **Precompute once**
* **Answer queries fast**

Two phases:

1. **Pre-storing (Precomputation)**
2. **Fetching (Query answering)**

---

## 4. Frequency Array / Hash Array

A **hash array** stores:

* **Index → number**
* **Value → frequency of that number**

Also called:

* Frequency Array
* Counting Array

---

## 5. Example

### Given Array:

```
arr = [1, 2, 1, 3, 2]
```

### Maximum element = 3

So size of hash array = `max + 1 = 4`

### Hash Array Representation:

| Index | 0 | 1 | 2 | 3 |
| ----- | - | - | - | - |
| hash  | 0 | 2 | 2 | 1 |

Meaning:

* `1` appears 2 times
* `2` appears 2 times
* `3` appears 1 time

---

## 6. Precomputation Logic

### Steps:

1. Initialize hash array with 0
2. Traverse original array
3. Increment frequency

```cpp
int hash[13] = {0};   // assuming max value ≤ 12

for(int i = 0; i < n; i++) {
    hash[arr[i]]++;
}
```

---

## 7. Fetching / Query Answering

Once hash array is ready:

```cpp
cout << hash[number] << endl;
```

### Time Complexity:

* **O(1)** per query

---

## 8. Complete C++ Program (As in Notes)

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cin >> n;

    int arr[n];
    for(int i = 0; i < n; i++) {
        cin >> arr[i];
    }

    // Precompute
    int hash[100005] = {0};
    for(int i = 0; i < n; i++) {
        hash[arr[i]]++;
    }

    int q;
    cin >> q;
    while(q--) {
        int number;
        cin >> number;
        cout << hash[number] << endl;
    }

    return 0;
}
```

---

## 9. Time & Space Complexity

### Precomputation:

* **O(n)**

### Each Query:

* **O(1)**

### Total:

[
O(n + q)
]

### Space Complexity:

* **O(maxElement)**

---

## 10. Important Constraints (Very Important)

### Inside `main()`:

* Max array size ≈ **10⁶**

### Globally:

```cpp
int hash[10000000];
```

 Can go up to **10⁷**

 Not possible inside `main()` due to stack overflow

---

## 11. When to Use Hashing?

Use hashing when:

* Repeated frequency queries
* Large input size
* Need fast lookup
* Elements are within a **known range**

---

## 12. Key Points (One-Liners)

* Hashing uses **index-based storage**
* Frequency array stores **count of elements**
* Query time reduces from **O(n) to O(1)**
* Precomputation is required
* Space–time tradeoff is involved

---

## 13. One-Mark Definition

> **Hashing** is a technique used to store data in a way that allows fast insertion, deletion, and searching.

---
