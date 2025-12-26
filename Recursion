# Recursion

## Definition

Recursion is a programming technique in which a function calls itself until a specified stopping condition is met.

---

## Basic Structure of a Recursive Function

A recursive function generally has two parts:

1. Base Condition – the condition used to stop recursion.
2. Recursive Call – the function calling itself.

### Example (Conceptual)

```cpp
void fun() {
    print();
    fun();
}
```

If no base condition is present, the function will keep calling itself infinitely.

---

## Base Condition

Base condition is the condition used to stop recursion.

Without a base condition:

* Infinite recursive calls occur
* Stack memory keeps getting filled
* Results in stack overflow or segmentation fault

---
## Stack Space 

Stack space in recursion is the memory used to store each recursive function call until the base condition is reached.

### Why is stack space important?

* Stack space is limited

* If recursion:
  Has no base condition, or
  Has too many recursive calls
  → stack memory fills up

This causes stack overflow (program crash).

### What happens in recursion?

* Every time a recursive function is called:
* A new stack frame is created
* It stores:
    * Local variables
    * Function parameters
    * Return address

These stack frames are stored in stack memory

### Example
void fun(int n) {
    if (n == 0)
        return;      // base condition
    fun(n - 1);      // recursive call
}

-----

Call sequence:

fun(3)
fun(2)
fun(1)
fun(0)  ← base condition

--------

Stack frames in memory:

| fun(3) |
| fun(2) |
| fun(1) |
| fun(0) |

----------------

## Stack Overflow & Segmentation Fault

* Each function call occupies stack memory
* Stack space is limited
* If recursive calls exceed available stack space, stack overflow occurs
* This may lead to a segmentation fault

### Stack Representation (Conceptual)

```
fun(), L2
fun(), L2
fun(), L2
fun(), L2
```

Stack space gets filled before previous calls complete execution.

---

## Example of Recursive Code with Base Condition

```cpp
#include <bits/stdc++.h>
using namespace std;

int cnt = 0;

void print() {
    if (cnt == 3)
        return;   // base condition

    cout << cnt << endl;
    cnt++;
    print();     // recursive call
}

int main() {
    print();
    return 0;
}
```

### Explanation

* Function prints values of `cnt`
* Stops recursion when `cnt == 3`
* Prevents infinite recursion

---

## Recursion Tree

A recursion tree represents how recursive calls are made and returned.

### Example Representation

```
fun()
 ↓
fun()
 ↓
fun()
 ↓
fun()
```

* Downward arrows represent recursive calls
* Upward return happens after base condition is met

---
