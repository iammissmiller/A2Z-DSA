# Ordered Map (`std::map`) — C++ STL Notes

## 1. What is an Ordered Map?

* `map` is an **associative container** in STL.
* Stores data in **key–value pairs**.
* **Keys are unique**.
* Elements are stored in **sorted (ordered) manner by key**.

---

## 2. Header File

```cpp
#include <map>
```

---

## 3. Syntax

```cpp
map<key_datatype, value_datatype> mp;
```

### Example:

```cpp
map<int, int> mp;
map<char, int> mp;
```

---

## 4. Why is it called an *Ordered* Map?

* Internally implemented using a **balanced BST (Red-Black Tree)**.
* Keys are **always sorted** automatically.
* While iterating, elements come in **increasing order of keys**.

---

## 5. Use Case: Frequency Counting

Example array:

```cpp
arr = {1, 2, 3, 1, 3, 2}
```

### Meaning:

* **Key** → element
* **Value** → frequency (how many times it appears)

---

## 6. Frequency Count Code

```cpp
map<int, int> mp;

for(int i = 0; i < n; i++) {
    mp[arr[i]]++;
}
```

### Internal Representation:

```
1 → 2
2 → 2
3 → 2
```

---

## 7. Accessing Elements

```cpp
mp[key]        // returns value
```

### Example:

```cpp
cout << mp[2];   // output: 2
```

---

## 8. Iterating Over a Map

```cpp
for(auto it : mp) {
    cout << it.first << " -> " << it.second << endl;
}
```

### Output (sorted order):

```
1 -> 2
2 -> 2
3 -> 2
```

---

## 9. Important Properties

* Stores **unique keys only**
* Automatically sorts keys
* Slower than unordered_map, but predictable order
* Useful when **sorted output is required**

---

## 10. Time Complexity of Ordered Map

| Operation            | Time Complexity |
| -------------------- | --------------- |
| Insertion            | O(log N)        |
| Deletion             | O(log N)        |
| Searching / Fetching | O(log N)        |

> Best, Average, and Worst cases are **all O(log N)**

---

## 11. When to Use Ordered Map?

* When **sorted data** is required
* When **order matters**
* When predictable performance is needed
* When time limit is not extremely strict

---

## 12. Map with Characters (Example)

```cpp
map<char, int> mp;
```

Example mapping:

```
a → 2
b → 1
c → 1
```

---

## 13. Ordered Map vs Unordered Map (Quick View)

| Feature        | map            | unordered_map |
| -------------- | -------------- | ------------- |
| Order          | Sorted         | Not sorted    |
| Implementation | Red-Black Tree | Hash Table    |
| Time           | O(log N)       | O(1) avg      |
| Worst Case     | O(log N)       | O(N)          |

---

#include <iostream>
#include <map>
#include <vector>
using namespace std;

int main() {

    int n;
    cin >> n;

    vector<int> arr(n);   // standard C++ array replacement
    for(int i = 0; i < n; i++) {
        cin >> arr[i];
    }

    // precompute
    map<int, int> mpp;
    for(int i = 0; i < n; i++) {
        mpp[arr[i]]++;
    }

    int q;
    cin >> q;
    while(q--) {
        int number;
        cin >> number;
        // fetch
        cout << mpp[number] << endl;
    }

    return 0;
}
