# Character Hashing (Frequency Counting)

## Problem Motivation

When we need to answer multiple queries like:

* How many times does a character appear in a string?

A **naive approach** is inefficient.

---

## Naive Approach (Brute Force)

### Idea

For every query character, traverse the whole string and count.

### Pseudocode

```cpp
int f(char c, string s) {
    int cnt = 0;
    for(int i = 0; i < s.length(); i++) {
        if(s[i] == c)
            cnt++;
    }
    return cnt;
}
```

### Time Complexity

* For each query: **O(N)**
* For Q queries: **O(Q × N)**

This is slow for large inputs.

---

## Optimized Approach: Character Hashing

### Key Idea

* Precompute frequencies of all characters once
* Answer each query in **O(1)** time

---

## Assumptions

* Characters are **lowercase English letters** (`a` to `z`)
* Total lowercase letters = **26**

---

## ASCII Concept (Important)

* Characters have integer ASCII values

  * `'a'` → 97
  * `'z'` → 122

### Character to Index Mapping

```cpp
index = ch - 'a'
```

Examples:

* `'a' - 'a' = 0`
* `'f' - 'a' = 5`
* `'z' - 'a' = 25`

---

## Hash Array Representation

```
Index:  0  1  2  ...  25
Char:   a  b  c  ...  z
```

Each index stores frequency of that character.

---

## Precomputation Step

### Code

```cpp
int hash[26] = {0};

for(int i = 0; i < s.size(); i++) {
    hash[s[i] - 'a']++;
}
```

### Time Complexity

* **O(N)** (single traversal of string)

---

## Query Handling

### Code

```cpp
char c;
cin >> c;
cout << hash[c - 'a'] << endl;
```

### Time Complexity

* **O(1)** per query

---

## Full Optimized Code (Lowercase Only)

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    string s;
    cin >> s;

    // Precompute frequencies
    int hash[26] = {0};
    for(int i = 0; i < s.size(); i++) {
        hash[s[i] - 'a']++;
    }

    int q;
    cin >> q;
    while(q--) {
        char c;
        cin >> c;
        cout << hash[c - 'a'] << endl;
    }

    return 0;
}
```

---

## Handling All Characters (Extended ASCII)

If input may contain **uppercase, lowercase, digits, symbols**, use size **256**.

### Code

```cpp
int hash[256] = {0};

for(int i = 0; i < s.size(); i++) {
    hash[s[i]]++;
}
```

Query:

```cpp
cout << hash[c] << endl;
```

---

## Time & Space Complexity (Optimized)

| Step       | Complexity      |
| ---------- | --------------- |
| Precompute | O(N)            |
| Each Query | O(1)            |
| Total      | O(N + Q)        |
| Space      | O(26) or O(256) |

---

## Key Takeaways (Exam Points)

* Hashing avoids repeated traversal
* Use ASCII arithmetic for indexing
* `'ch' - 'a'` is valid only for lowercase letters
* Preferred for frequency/counting problems
* Very common in **DSA, competitive programming, interviews**

---
