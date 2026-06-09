# Parameterized Recursion and Functional Recursion

## Problem: Sum of First N Natural Numbers

This can be solved using recursion in **two ways**:

1. Parameterized recursion
2. Functional recursion

---

## 1. Parameterized Recursion

### Logic

* Keep decreasing `i`
* Add `i` to `sum`
* When `i < 1`, print the result

### Pseudocode

```
f(i, sum):
    if i < 1:
        print sum
        return
    f(i - 1, sum + i)
```

### Function Call

```
f(n, 0)
```

### Key Points

* Result is **not returned**, it is **printed**
* Extra parameter is used to store the answer
* Tail-recursive in nature

---

## 2. Functional Recursion

### Logic

* If `n == 0`, return 0
* Otherwise return:

  ```
  n + f(n - 1)
  ```

### Pseudocode

```
f(n):
    if n == 0:
        return 0
    return n + f(n - 1)
```

---

## C++ Code (Functional Recursion)

```cpp
#include <bits/stdc++.h>
using namespace std;

int sum(int n)
{
    if (n == 0)
        return 0;

    return n + sum(n - 1);
}

int main()
{
    int n = 3;
    cout << sum(n);
    return 0;
}
```

### Output

```
6
```

---

## Difference Between Parameterized and Functional Recursion

| Parameterized           | Functional         |
| ----------------------- | ------------------ |
| Uses extra parameter    | No extra parameter |
| Prints result           | Returns result     |
| Tail recursion          | Non-tail recursion |
| More control over state | Cleaner logic      |


