# Multiple Recursion – Fibonacci Example

## 1. What is Multiple Recursion?

A **recursive function** is said to use **multiple recursion** when it calls itself **more than once** in a single function call.

In simple words:
**One function call → multiple recursive calls**

---

## 2. Fibonacci Series (Problem Used)

### Fibonacci Series:

[
0, 1, 1, 2, 3, 5, 8, 13, 21, 34 ...
]

### Definition:

Each number is the **sum of the previous two numbers**.

[
F(n) = F(n-1) + F(n-2)
]

---

## 3. Mathematical Definition of Fibonacci Function

### Base Cases:

* (F(0) = 0)
* (F(1) = 1)

### Recursive Case:

[
F(n) = F(n-1) + F(n-2), \quad \text{for } n \ge 2
]

This formula itself shows **multiple recursion** because:

* `F(n)` calls `F(n-1)`
* `F(n)` also calls `F(n-2)`

---

## 4. Recursive Function Structure (Logic)

### Pseudocode:

```
fib(n):
    if n <= 1:
        return n
    return fib(n-1) + fib(n-2)
```

Here:

* `fib(n-1)` → last element
* `fib(n-2)` → second last element

---

## 5. Recursive Tree (Example: fib(4))

```
fib(4)
 ├── fib(3)
 │    ├── fib(2)
 │    │    ├── fib(1)
 │    │    └── fib(0)
 │    └── fib(1)
 └── fib(2)
      ├── fib(1)
      └── fib(0)
```

### Observation:

* Same values (`fib(2)`, `fib(1)`) are computed **multiple times**
* This causes **extra recursive calls**

---

## 6. C++ Implementation (Multiple Recursion)

```cpp

#include <bits/stdc++.h>
using namespace std;

int fib(int n) {
    if (n <= 1)
        return n;

    int last = fib(n - 1);
    int secondLast = fib(n - 2);

    return last + secondLast;
}

int main() {
    cout << fib(4);
    return 0;
}
```

---

## 7. Why This is Multiple Recursion?

Because:

* `fib(n)` calls **two recursive functions**
* More than one recursive call inside the same function

✔ Hence, Fibonacci recursion is a **classic example of multiple recursion**

---

## 8. Time Complexity

### Time Complexity:

[
O(2^n)
]

### Reason:

* Each call branches into **two more calls**
* Number of calls grows **exponentially**

This is why recursive Fibonacci is **inefficient** for large `n`.

---

## 9. Key Exam Points (Very Important)

* Fibonacci recursion uses **multiple recursion**
* Base cases prevent infinite recursion
* Repeated function calls cause inefficiency
* Recursive tree grows exponentially
* Time Complexity: **O(2ⁿ)**
* Space Complexity: **O(n)** (due to recursion stack)

---

## 10. One-Line Definition (For Exams)

> **Multiple recursion** is a type of recursion in which a function makes more than one recursive call within its body.
